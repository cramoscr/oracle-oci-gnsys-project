# GnSys Cloud Workstation — Progress Log

**Date:** 2026-09-08  
**Status:** PAUSED — safe continuation point

## Objective

Evaluate whether `GnSys-VM-APP-01` can become a personal cloud development workstation so development environments, source code, agents, and tools do not need to reside on the local work computer.

The first experiment deliberately uses a conventional lightweight Linux desktop (`XFCE + XRDP`). A later architecture review will compare this approach with Cloud Development Environment alternatives such as Coder and browser-based VS Code solutions.

## VM baseline

`GnSys-VM-APP-01`:

- OCI shape: `VM.Standard.A1.Flex`
- Architecture: ARM64 / Ampere A1 (`Neoverse-N1`)
- OCPU: 1
- RAM: 6 GB allocated (~5.5 GiB visible to Linux)
- Swap: 4 GiB
- Root filesystem: 30 GB
- Free space before desktop installation: ~20 GB
- OS: Oracle Linux 9.8
- Private IP: `10.0.2.86`
- Public IP: none
- Default target before experiment: `multi-user.target`

Observed baseline memory usage was approximately 708 MiB, leaving ~4.8 GiB available.

## Network / administrative access

The VM remains private.

```text
Administrator workstation
        |
        | SSH local forwarding
        v
OCI Bastion
10.0.2.132
        |
        | TCP/22
        v
GnSys-VM-APP-01
10.0.2.86
        |
        | outbound
        v
NAT Gateway -> Internet
```

SSH access through OCI Bastion was validated successfully before the workstation experiment.

## Recovery checkpoint

Before installing the graphical stack, the VM was stopped and a Custom Image was created:

```text
GnSys-VM-APP-01-PRE-DESKTOP-2026-09-08
```

Status was confirmed as `Available` before proceeding.

This is the rollback boundary for the desktop experiment.

## Repository preparation

The Oracle Linux Developer EPEL repository (`ol9_developer_EPEL`) was enabled because the default Oracle Linux repositories did not expose XFCE or XRDP packages.

Native ARM64 availability was then confirmed for both XFCE and XRDP.

## Installed graphical stack

The lightweight XFCE/XRDP stack was installed successfully.

Confirmed packages:

```text
xfce4-session-4.18.3-1.el9.aarch64
xfce4-panel-4.18.4-1.el9.aarch64
xfdesktop-4.18.1-3.el9.aarch64
xfwm4-4.18.0-2.el9.aarch64
xrdp-0.10.6.1-3.el9.aarch64
xorgxrdp-0.10.5-1.el9.aarch64
xrdp-selinux-0.10.6.1-3.el9.aarch64
```

Additional XFCE components installed as part of the minimal desktop include settings, terminal, app finder, notification daemon, and PolicyKit integration.

## XFCE session configuration

For the current `opc` user, the intended XRDP desktop command was configured through:

```text
~/.Xclients
```

with:

```bash
exec startxfce4
```

The file was made executable.

## XRDP status

XRDP was enabled and started successfully:

```text
xrdp.service
Loaded: enabled
Active: active (running)
```

XRDP reported:

```text
address [0.0.0.0] port [3389]
listening to port 3389 on 0.0.0.0
```

Socket validation confirmed:

```text
*:3389 LISTEN xrdp
```

Therefore, at the pause point:

- XFCE is installed: YES
- XRDP is installed: YES
- XRDP service is running: YES
- TCP/3389 is listening locally: YES
- External/public TCP/3389 exposure: NO
- RDP through Bastion validated: NOT YET

## Security principle

Do **not** expose RDP directly to the Internet.

Target design:

```text
Windows Remote Desktop
        |
        | localhost:<local-port>
        v
SSH tunnel / OCI Bastion
        |
        | TCP/3389
        v
GnSys-VM-APP-01
        |
        v
XRDP -> XFCE
```

The application VM should continue to have no public IP.

## Exact continuation point

The next session should resume here rather than repeat installation.

### 1. Validate XRDP session manager

```bash
systemctl status xrdp-sesman --no-pager
```

Expected: `active (running)`.

### 2. Create a dedicated graphical development user

Recommended instead of using `opc` as the permanent desktop identity:

```bash
sudo useradd -m -s /bin/bash dev
sudo passwd dev
```

Do not store the password in Git.

Configure XFCE for that user:

```bash
sudo bash -c 'echo "exec startxfce4" > /home/dev/.Xclients'
sudo chmod +x /home/dev/.Xclients
sudo chown dev:dev /home/dev/.Xclients
```

### 3. Permit RDP only from the Bastion endpoint in Linux firewall

Bastion private endpoint currently documented as `10.0.2.132`.

Proposed rule:

```bash
sudo firewall-cmd --permanent \
  --add-rich-rule='rule family="ipv4" source address="10.0.2.132/32" port protocol="tcp" port="3389" accept'
sudo firewall-cmd --reload
sudo firewall-cmd --list-rich-rules
```

Before applying this in a future session, verify the Bastion private endpoint is still `10.0.2.132`.

### 4. Add OCI NSG ingress rule

On `GnSys-NSG-APP-01`, add a stateful ingress rule only for the Bastion endpoint:

```text
Source type:       CIDR
Source:            10.0.2.132/32
Protocol:          TCP
Destination port:  3389
Description:       Allow RDP from GnSys Bastion
```

Do not create `0.0.0.0/0 -> 3389`.

### 5. Create OCI Bastion RDP port-forwarding session

Suggested session:

```text
Name:        GnSys-APP-01-RDP
Target IP:   10.0.2.86
Target port: 3389
```

Use an unprivileged local port such as `33389` when adapting the OCI-generated SSH tunnel command.

Conceptually:

```text
localhost:33389 -> OCI Bastion -> 10.0.2.86:3389
```

### 6. Test from Windows Remote Desktop

Launch:

```text
mstsc
```

and connect to:

```text
localhost:33389
```

Authenticate using the dedicated graphical Linux user created above.

## Definition of success for this experiment

The experiment is complete when a usable XFCE desktop from `GnSys-VM-APP-01` is displayed through Windows Remote Desktop while:

1. APP-01 remains on the private subnet.
2. APP-01 has no public IP.
3. TCP/3389 is not exposed publicly.
4. RDP traffic reaches APP-01 only through OCI Bastion.
5. Basic desktop responsiveness on 1 OCPU / 6 GB RAM is measured qualitatively.

## Follow-up architecture decision — deliberately deferred

Once the conventional desktop works, compare it against purpose-built Cloud Development Environment approaches rather than assuming a full remote desktop is the final design.

Candidates already identified for evaluation:

- Coder (self-hosted CDE)
- OpenVSCode Server / browser-hosted IDE approach
- DevPod (development environments as code)

Decision question:

> Does the user actually need a remote desktop, or only a secure browser-accessible personal development environment?

Do not mix this decision into completion of the current XFCE/XRDP experiment. Finish and benchmark the current experiment first, then compare alternatives.
