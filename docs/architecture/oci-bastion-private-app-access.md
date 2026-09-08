# OCI Bastion Access to GnSys Private Application VM

## Purpose

Document the secure administrative access path established for `GnSys-VM-APP-01`, while preserving the VM as a private resource with no public IPv4 address.

This configuration was validated on 2026-09-08.

## Architecture

```text
Administrator PC
      |
      | SSH / local port forwarding
      v
OCI Bastion: GnSysBastion01
Private endpoint: 10.0.2.132
      |
      | TCP/22
      v
GnSys-VM-APP-01
Private IP: 10.0.2.86
Subnet: GnSys-SNET-PRV-01 (10.0.2.0/24)
      |
      | outbound Internet traffic
      v
GnSys-RT-PRV-01
0.0.0.0/0 -> GnSys-NATGW-01
      |
      v
Internet
```

## Existing private network design

`GnSys-VM-APP-01` remains in the private subnet:

- VM: `GnSys-VM-APP-01`
- Shape: `VM.Standard.A1.Flex`
- Architecture: ARM64 / Ampere A1
- OCPU: 1
- Memory: 6 GB allocated (approximately 5.5 GiB visible to Linux)
- Private IPv4: `10.0.2.86`
- Public IPv4: none
- Subnet: `GnSys-SNET-PRV-01`
- Subnet CIDR: `10.0.2.0/24`
- Subnet access: Private Subnet
- Route table: `GnSys-RT-PRV-01`
- Network Security Group: `GnSys-NSG-APP-01`

The private route table contains:

```text
Destination: 0.0.0.0/0
Target type: NAT Gateway
Target: GnSys-NATGW-01
```

This allows resources in the private subnet to initiate outbound Internet connections without assigning them public IP addresses. The NAT Gateway does not provide inbound Internet access to the VM.

## OCI Bastion

A managed OCI Bastion was created instead of converting the application VM to a public subnet or using the web server as an improvised jump host.

Configuration:

- Bastion: `GnSysBastion01`
- VCN: `GnSys-VCN-01`
- Target subnet: `GnSys-SNET-PRV-01`
- Bastion type: Standard
- Private endpoint IP: `10.0.2.132`
- Maximum session TTL configured: 3 hours
- FQDN support: Disabled
- SOCKS5 support: Disabled

The administrator CIDR allowlist is intentionally restricted to a single external `/32` address. The actual public administrator IP is not recorded in this repository because it is operational and may change.

## NSG change

Before Bastion was introduced, `GnSys-NSG-APP-01` allowed SSH only from `GnSys-NSG-WEB-01`:

```text
GnSys-NSG-WEB-01 -> TCP/22 -> APP tier
```

This represented deliberate tier-to-tier segmentation and was preserved.

A second stateful ingress rule was added specifically for OCI Bastion:

```text
Source:      10.0.2.132/32
Protocol:    TCP
Destination: port 22
Purpose:     Allow SSH from GnSys Bastion
```

Using `/32` limits SSH access to the Bastion private endpoint rather than permitting the entire `10.0.2.0/24` subnet.

The resulting policy is conceptually:

```text
GnSys-NSG-WEB-01  ---- TCP/22 ---> GnSys-VM-APP-01
10.0.2.132/32      ---- TCP/22 ---> GnSys-VM-APP-01
```

## Client connection model

OCI Bastion uses an SSH port-forwarding session targeting:

```text
Target IP:   10.0.2.86
Target port: 22
```

A local tunnel can be established from the administrator workstation using the OCI-generated Bastion session command. A local port such as `2222` is forwarded to `10.0.2.86:22` through the managed Bastion.

Conceptually:

```text
localhost:2222
     |
     | encrypted SSH tunnel
     v
OCI Bastion
     |
     v
10.0.2.86:22
```

The second SSH connection is then made to `opc@localhost` on the chosen local forwarded port.

Private keys, session OCIDs, ephemeral session commands, and administrator public IP addresses must not be committed to this repository.

## Validation

Successful login to the application VM was confirmed. The Linux login record reported the source as:

```text
10.0.2.132
```

which matches the OCI Bastion private endpoint and therefore validates the intended path:

```text
Administrator -> OCI Bastion -> GnSys-VM-APP-01
```

## Troubleshooting performed

Initial port-forward attempts reached the local tunnel but failed before SSH key exchange with the target VM.

The cause was identified by following the connection path layer by layer. `GnSys-NSG-APP-01` allowed TCP/22 only from the Web-tier NSG, so the new Bastion endpoint was not an authorized SSH source.

After adding the Bastion-specific `/32` ingress rule and reconnecting the tunnel, SSH access succeeded.

This provides a useful troubleshooting pattern:

1. Verify the local SSH connection reaches the forwarded local port.
2. Verify the OCI Bastion session is Active.
3. Verify the target private IP and port.
4. Verify subnet and VNIC security rules.
5. Verify the target operating system SSH service and firewall if network rules are correct.
6. Only then troubleshoot SSH user/key authentication.

## Pre-desktop recovery checkpoint

Before installing a graphical desktop, XRDP, development tools, or otherwise repurposing `GnSys-VM-APP-01`, a recoverable OCI Custom Image was created.

```text
Custom image:
GnSys-VM-APP-01-PRE-DESKTOP-2026-09-08

Status at validation:
Available

Original image family:
Oracle Linux 9.8 aarch64
```

The VM was stopped before image creation to favor a consistent filesystem state.

This image represents the known-good pre-workstation baseline:

```text
GnSys-VM-APP-01
      |
      +-- Oracle Linux 9.8 / ARM64
      +-- 1 OCPU / 6 GB RAM
      +-- private subnet
      +-- NAT outbound connectivity
      +-- OCI Bastion SSH access validated
      +-- no graphical desktop installed
      |
      +--> PRE-DESKTOP CUSTOM IMAGE
```

If the workstation experiment causes an unrecoverable configuration problem, a replacement VM can be created from this image rather than attempting to reverse every package or configuration change manually.

The image is a recovery checkpoint, not a substitute for backing up application data that may be created after the checkpoint.

## Workstation feasibility discovery

Before changing the VM, the Oracle Linux Developer EPEL repository for aarch64 was enabled and package availability was verified.

Native ARM64 packages were found for the proposed lightweight graphical stack, including:

- XFCE components
- `xrdp.aarch64`
- `xorgxrdp.aarch64`
- `xrdp-selinux.aarch64`

At the pre-desktop checkpoint, Linux reported approximately:

- 5.5 GiB RAM total
- 4.8 GiB RAM available
- 4 GiB swap
- 30 GB root filesystem
- approximately 20 GB free on `/`
- default boot target: `multi-user.target`

The primary expected performance constraint for desktop use is the single OCPU rather than memory.

## Architectural decision

`GnSys-VM-APP-01` will remain private.

Rejected alternatives for this use case:

- Moving the VM to a public subnet.
- Assigning a public IPv4 address directly to the application VM.
- Opening TCP/22 broadly to the Internet.
- Reusing `GnSys-VM-WEB-01` as a permanent jump host and mixing web workload and administrative access responsibilities.

OCI Bastion provides the cleaner separation of responsibilities while retaining outbound Internet access through the existing NAT Gateway.

## Potential new role

`GnSys-VM-APP-01` is being evaluated as a private cloud development workstation and isolated development/research host for the Material APEX Revival experiment.

The intended experiment is to add a lightweight graphical environment and development tooling while preserving the private-network architecture. The pre-desktop custom image provides the rollback boundary before those changes begin.
