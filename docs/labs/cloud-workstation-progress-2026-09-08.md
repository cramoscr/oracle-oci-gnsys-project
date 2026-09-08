# GnSys Cloud Workstation — Progress Log

**Date:** 2026-09-08  
**Status:** EXPERIMENT CONCLUDED — technically feasible, operationally rejected

## Objective

Evaluate whether `GnSys-VM-APP-01` can become a personal cloud development workstation so development environments, source code, agents, and tools do not need to reside on the local work computer.

The first experiment deliberately used a conventional lightweight Linux desktop (`XFCE + XRDP`). The experiment produced enough evidence to make an architectural decision: the approach is technically feasible, but it introduces too much operational friction for a daily personal development environment.

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

The VM remained private throughout the experiment.

```text
Administrator workstation
        |
        | SSH local forwarding
        v
OCI Bastion
10.0.2.132
        |
        v
GnSys-VM-APP-01
10.0.2.86
        |
        | outbound
        v
NAT Gateway -> Internet
```

SSH access through OCI Bastion was validated successfully.

## Recovery checkpoint

Before installing the graphical stack, the VM was stopped and a Custom Image was created:

```text
GnSys-VM-APP-01-PRE-DESKTOP-2026-09-08
```

Status was confirmed as `Available` before proceeding. This remains the rollback boundary for the desktop experiment.

## Repository preparation

The Oracle Linux Developer EPEL repository (`ol9_developer_EPEL`) was enabled because the default Oracle Linux repositories did not expose XFCE or XRDP packages.

Native ARM64 availability was confirmed for both XFCE and XRDP.

## Installed graphical stack

The lightweight XFCE/XRDP stack installed successfully.

Confirmed packages included:

```text
xfce4-session-4.18.3-1.el9.aarch64
xfce4-panel-4.18.4-1.el9.aarch64
xfdesktop-4.18.1-3.el9.aarch64
xfwm4-4.18.0-2.el9.aarch64
xrdp-0.10.6.1-3.el9.aarch64
xorgxrdp-0.10.5-1.el9.aarch64
xrdp-selinux-0.10.6.1-3.el9.aarch64
```

Additional XFCE components installed as part of the minimal desktop included settings, terminal, app finder, notification daemon, and PolicyKit integration.

## Dedicated development identity

A dedicated graphical development user was created:

```text
gnsys-dev
```

Its XFCE session command was configured through:

```text
/home/gnsys-dev/.Xclients
```

with:

```bash
exec startxfce4
```

## XRDP validation

XRDP and its session manager ran successfully:

```text
xrdp.service        active (running)
xrdp-sesman         active (running)
TCP/3389             listening
```

RDP was never exposed directly to the public Internet.

Linux `firewalld` and the OCI NSG were configured to permit TCP/3389 only from the OCI Bastion private endpoint (`10.0.2.132/32`).

An OCI Bastion port-forwarding session targeted:

```text
10.0.2.86:3389
```

A local high port was forwarded through Bastion and Windows Remote Desktop successfully reached the XRDP login screen.

## What worked

The experiment validated the entire access chain:

```text
Windows Remote Desktop
        |
        | local forwarded port
        v
SSH tunnel
        |
        v
OCI Bastion
        |
        v
APP-01:3389
        |
        v
XRDP
        |
        v
Xorg
        |
        v
XFCE session
```

XRDP logs confirmed successful authentication for `gnsys-dev`, session creation on display `:10`, Xorg startup, and channel connection.

Process inspection confirmed that the XFCE desktop stack was actually running, including:

- `xfce4-session`
- `xfwm4`
- `xfsettingsd`
- `xfce4-panel`
- `xfdesktop`
- `xfce4-notifyd`

Therefore the experiment progressed substantially beyond simple network connectivity: the graphical Linux session itself was alive.

## Remaining graphical issue

Despite successful authentication, Xorg startup, and XFCE processes running, the RDP client displayed only a blue background rather than a usable desktop.

Logs contained non-fatal XFCE warnings (missing Thunar and optional panel plugins) plus indications worth investigating in XRDP's graphics path, including GFX/H.264 negotiation and repeated `encoder is nil` messages.

At this point the remaining problem appeared to be in the remote graphics/rendering path rather than OCI networking, Bastion, authentication, Xorg, or basic XFCE startup.

## Architectural finding

The remaining rendering problem was deliberately **not** pursued further.

The reason is more important than the individual XRDP bug: by this stage, the operational workflow itself had demonstrated excessive complexity for the actual requirement.

The daily path had become approximately:

```text
Create/recreate temporary Bastion session
        -> obtain session OCID / SSH command
        -> maintain local SSH key and scripts
        -> start SSH port-forward tunnel
        -> start Windows Remote Desktop
        -> authenticate to XRDP
        -> maintain Linux desktop/Xorg/XRDP compatibility
```

OCI Bastion session TTL also caused previously working local connection scripts to become invalid after the temporary session expired. This behavior is appropriate for controlled, temporary administrative access, but undesirable as the foundation for a daily personal workstation.

## Actual requirement discovered

The experiment clarified that the real requirement is not simply:

> Run a Linux GUI in OCI.

The stronger requirement is:

> Provide a personal development environment accessible from the work computer primarily through a browser, while minimizing or eliminating personal operational artifacts stored on that computer.

Desired local footprint:

```text
Work computer
    |
    +-- Browser / HTTPS only (target)
    |
    X-- no personal SSH private/public keys
    X-- no OCI connection CMD scripts
    X-- no OCI CLI credentials
    X-- no personal Git repositories
    X-- no development toolchain
    X-- no manually initiated SSH tunnels as the normal workflow
```

This does not imply invisibility from corporate endpoint/network monitoring, and any use must remain compatible with employer policy. It means reducing persistent personal development artifacts and operational dependencies on the work machine.

## Decision

**XFCE + XRDP over OCI Bastion is technically feasible but rejected as the preferred daily-access architecture.**

OCI Bastion remains useful for temporary administrative access and recovery. It should not be the normal user-facing gateway to the personal cloud development environment.

The VM itself remains valuable and can be reused for the next architecture experiment.

## Next architecture experiment

Evaluate purpose-built Cloud Development Environment approaches, prioritizing browser-first HTTPS access.

Candidates already identified:

1. Coder (self-hosted Cloud Development Environment)
2. OpenVSCode Server / browser-hosted IDE approach
3. DevPod, if its client-side operational model fits the local-footprint requirement

The next comparison should explicitly score:

- browser-only daily access
- local credential/key footprint
- OCI ARM64 compatibility
- installation/maintenance complexity
- HTTPS and authentication model
- GitHub integration
- terminal access
- Codex / AI-agent support
- OpenSpec support
- persistence and backup
- performance on 1 OCPU / 6 GB
- monthly cost
- recovery/admin path

## Historical note

This was a small engineering failure in the useful sense: a plausible architecture was implemented far enough to expose its real operational cost before more effort was invested in polishing it.

Or, in the project's Costa Rican vocabulary:

> **Otra raya más que le sale al tigre.**

The wheel was made sufficiently round to discover that it was not the wheel we wanted to use.
