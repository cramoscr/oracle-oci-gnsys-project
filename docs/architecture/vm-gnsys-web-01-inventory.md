# vm-gnsys-web-01 — Technical Inventory

**Captured:** 2026-09-08  
**Purpose:** Preserve the current technical characteristics and runtime state of the OCI VM created during the GnSys OCI certification lab.

## Executive Summary

`vm-gnsys-web-01` is an ARM64 Oracle Linux virtual machine currently active in OCI. It is **not an unused VM**: it is still running the GnSys Flask web application behind Apache HTTP Server.

The VM remains suitable for lightweight development and lab workloads, but should not be repurposed without first deciding whether the existing GnSys workload is still needed.

## Compute

| Attribute | Value |
|---|---|
| Hostname | `vm-gnsys-web-01` |
| Virtualization | KVM |
| Architecture | ARM64 / `aarch64` |
| CPU | ARM Neoverse-N1 |
| vCPU / OCPU visible to OS | 1 |
| Cores | 1 |
| Threads per core | 1 |
| NUMA nodes | 1 |

## Operating System

| Attribute | Value |
|---|---|
| Distribution | Oracle Linux Server |
| Version | 9.8 |
| Kernel | `6.12.0-204.92.4.3.el9uek.aarch64` |
| Platform | `el9` |

## Memory

| Metric | Value |
|---|---:|
| Total RAM | 5.5 GiB |
| Used RAM | 3.6 GiB |
| Free RAM | 417 MiB |
| Buff/cache | 1.8 GiB |
| Available RAM | 1.9 GiB |
| Swap | 4.0 GiB |
| Swap used | 379 MiB |

## Storage

### Root filesystem

| Metric | Value |
|---|---:|
| Root filesystem | `/dev/mapper/ocivolume-root` |
| Size | 30 GiB |
| Used | 13 GiB |
| Available | 17 GiB |
| Utilization | 44% |

### Other filesystems

| Mount | Size | Used | Available |
|---|---:|---:|---:|
| `/boot` | 2.0 GiB | 763 MiB | 1.2 GiB |
| `/var/oled` | 15 GiB | 264 MiB | 15 GiB |
| `/boot/efi` | 100 MiB | 7.9 MiB | 92 MiB |

## Networking

| Interface | State | Address |
|---|---|---|
| `lo` | UNKNOWN | `127.0.0.1/8`, `::1/128` |
| `enp0s6` | UP | `10.0.1.47/24` |

The observed VM address is therefore:

```text
10.0.1.47/24
```

This is a private OCI VCN address. Public IP, subnet OCID, NSGs, security lists and load-balancer attachment were not captured in this inventory session and should be documented separately if needed.

## Runtime State

At inspection time the VM had approximately **26 days and 23 hours of uptime** with negligible CPU load:

```text
load average: 0.00, 0.01, 0.00
```

## Important Running Services

The machine currently runs both the GnSys application and its web front end:

| Service | Role | State |
|---|---|---|
| `gnsys-app.service` | GnSys Flask Web Application | running |
| `httpd.service` | Apache HTTP Server | running |
| `sshd.service` | SSH access | running |
| `firewalld.service` | Host firewall | running |
| `auditd.service` | Security auditing | running |
| `oracle-cloud-agent.service` | OCI management agent | running |
| `oracle-cloud-agent-updater.service` | OCI agent updater | running |
| `unified-monitoring-agent.service` | OCI monitoring / Fluentd collector | running |
| `chronyd.service` | Time synchronization | running |
| `NetworkManager.service` | Network management | running |

Other standard Oracle Linux services such as `crond`, `rsyslog`, `rpcbind`, `tuned`, PCP monitoring services and systemd user/session services were also active.

## Current Assessment

### Status

**In use — do not repurpose blindly.**

The presence of both:

```text
gnsys-app.service
httpd.service
```

confirms that this VM still hosts the GnSys web workload created during the OCI certification lab.

### Capacity observation

For lightweight development tooling, source-code analysis, Git, Node/Sass compilation and similar tasks, the VM's approximately 5.5 GiB RAM and 17 GiB free root storage would be technically usable.

However, because it already has an active application workload, a separate unused VM is preferable for experiments such as the Material APEX Revival Lab.

## Follow-up Inventory Items

The following OCI-level properties were not captured from the guest OS and may be added later:

- OCI compute shape name
- Compartment
- Availability domain / fault domain
- Instance OCID
- Public IPv4 address
- VCN and subnet
- Network Security Groups
- Security Lists
- Boot volume configuration
- Load Balancer backend membership
- OCI Free Tier / Always Free eligibility

---

This document records the VM state observed directly from the operating system on 2026-09-08 and should be treated as a point-in-time infrastructure inventory.