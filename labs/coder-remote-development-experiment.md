# Coder Remote Development Experiment — Failed Path

**Date:** 2026-09-08  
**Host:** `gnsys-vm-app-01`  
**Platform:** OCI / Oracle Linux 9.8 / ARM64  
**Result:** **Experiment aborted — excessive setup friction for the intended goal**

## Objective

Evaluate whether **Coder** could provide a practical remote development environment on the existing GnSys OCI VM, especially for a workflow centered on:

```text
Personal PC -> Coder workspace -> GitHub -> AI agent / Codex -> code
```

The expected benefit was to reduce dependency on the local development machine and improve development velocity with AI-assisted tooling.

The experiment was explicitly about **reducing friction and time-to-market**, not proving that the infrastructure could eventually be made to work.

## Starting point

`gnsys-vm-app-01` already existed from a previous remote desktop/XRDP experiment.

Observed resources:

```text
OS:       Oracle Linux Server 9.8
CPU:      1 OCPU
RAM:      5.5 GiB total (~4.6 GiB available)
Swap:     4 GiB
Disk:     30 GiB root volume (~19 GiB free)
Arch:     ARM64 / aarch64
```

Residual packages from the previous graphical lab included XRDP, xorgxrdp, XFCE components, and TigerVNC components. They were deliberately **not removed**, because they were not preventing the Coder experiment and cleanup would have added unnecessary work.

## Step 1 — Docker

Docker was installed successfully on Oracle Linux 9.8.

Verified versions:

```text
Docker version 29.8.0
Docker Compose version v5.5.1
```

Validation:

```bash
docker run --rm hello-world
```

Result:

```text
Hello from Docker!
```

Docker successfully pulled and executed the ARM64 image (`arm64v8`).

**Status: SUCCESS**

## Step 2 — Coder installation

Coder installed successfully.

```text
Coder v2.37.1+22f4284
```

The binary supported the self-hosted `server` command.

**Status: SUCCESS**

## Step 3 — Start Coder server

Coder was launched interactively:

```bash
coder server
```

Coder successfully started:

```text
HTTP listener:  http://127.0.0.1:3000
Database:       built-in PostgreSQL
```

Because the server was listening only on localhost, Coder automatically established a temporary `try.coder.app` tunnel and presented an external Web UI URL.

No OCI NSG or firewall port was opened.

**Status: SUCCESS**

## Step 4 — Web UI and GitHub authentication

The Web UI loaded correctly through the temporary tunnel.

The administrator account was configured using GitHub device authentication.

GitHub reported:

```text
Congratulations, you're all set!
Your device is now connected.
```

**Status: SUCCESS**

## Step 5 — Docker workspace template

A new Coder template was configured using:

```text
Base template: Docker Containers
Image:         codercom/example-base:ubuntu
```

The lightweight base image was intentionally selected instead of the larger universal image because the OCI VM has only 1 OCPU.

The following modules were selected:

```text
Codex CLI
VS Code Web
Git Clone
```

The Git Clone module was configured against a real project repository so the experiment could eventually test actual development rather than a synthetic demo.

The intended architecture had now become:

```text
Windows PC / Browser
        |
        v
      Coder
        |
        v
OCI gnsys-vm-app-01
        |
      Docker
        |
        v
+-----------------------+
| Coder Workspace       |
|                       |
| VS Code Web           |
| Git repository        |
| Codex CLI             |
+-----------------------+
```

### Codex authentication observation

The Coder Codex CLI module indicated that an `openai_api_key` would be collected from developers when creating the workspace.

This introduced an additional concern: the experiment did not want to assume API-key-based billing/authentication when the developer already had access to ChatGPT/Codex through other mechanisms.

This was recorded as **product friction**, not investigated further during this lab.

## Step 6 — Failure

At the final template creation stage, the browser stopped communicating reliably with the Coder instance through the temporary tunnel.

The Web UI returned:

```json
{"message":"Failed to dial peer.","detail":"context deadline exceeded"}
```

Refreshing the browser (`F5`) produced the same result.

Inspection of the `coder server` terminal showed that the Coder process itself was still alive and processing activity. There was no corresponding fatal server failure visible in the log.

The likely failing component was therefore the temporary `try.coder.app` connectivity path rather than Docker or the local Coder process.

## Possible workaround considered

A direct SSH port-forward was considered:

```text
Browser -> localhost:3000
             |
          SSH tunnel
             |
             v
gnsys-vm-app-01:3000
```

Technically, this was a reasonable next diagnostic step.

**It was deliberately rejected.**

The experiment had reached the point where continuing would contradict its original purpose.

## Decision

**ABORT THE EXPERIMENT.**

No attempt was made to:

- open port 3000 in OCI;
- create additional NSG/firewall rules;
- configure nginx or another reverse proxy;
- create a permanent Coder service;
- configure a custom Coder access URL;
- add an SSH tunnel;
- debug the `try.coder.app` tunnel further;
- remove the previous XRDP/XFCE environment.

Docker and Coder were left installed for possible future investigation.

## What worked

| Component | Result |
|---|---|
| Oracle Linux ARM64 host | OK |
| Docker installation | OK |
| ARM64 Docker image execution | OK |
| Coder installation | OK |
| Coder local server | OK |
| Built-in PostgreSQL | OK |
| Initial `try.coder.app` access | OK |
| GitHub authentication | OK |
| Template builder | OK until final creation |
| Docker workspace design | Configured |
| Codex CLI module | Configured, API-key concern noted |
| Persistent Web access | FAILED / unreliable |

## Engineering conclusion

The important result is **not that Coder cannot work**.

The result is that, for this particular objective and environment, the path accumulated too much operational ceremony before producing usable application code.

The actual path became approximately:

```text
OCI VM
 -> Linux administration
 -> Docker
 -> Coder server
 -> temporary external tunnel
 -> GitHub authentication
 -> Terraform-based template
 -> Docker workspace template
 -> modules
 -> Git clone configuration
 -> Codex authentication concern
 -> tunnel failure
 -> proposed SSH tunnel
 -> finally, development
```

That is incompatible with the experiment's desired experience:

```text
repository -> AI agent -> code
```

A technically solvable infrastructure problem is not automatically a worthwhile problem to solve.

For GnSys and the broader AI-assisted development effort, **developer-environment infrastructure must justify itself by removing more friction than it introduces**.

## Lesson learned

> Do not optimize for proving that a tool can be made to work. Optimize for whether the tool materially improves the development workflow.

The experiment therefore produced useful evidence despite being aborted: **Coder, in this self-hosted OCI configuration, did not yet demonstrate enough reduction in development friction to justify further setup effort.**
