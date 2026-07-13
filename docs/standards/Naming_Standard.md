# Naming Standard

| Property | Value |
|----------|-------|
| **Project** | GnSyS |
| **Document** | Naming Standard |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Carlos R.G. |
| **Last Updated** | July 2026 |

---

# Table of Contents

1. Purpose
2. Design Principles
3. Naming Convention
4. Naming Grammar
5. Resource Prefixes
6. Examples
7. Reserved Prefixes
8. Best Practices
9. Anti-Patterns
10. Future Evolution

---

# 1. Purpose

This document defines the naming convention adopted by **Project GnSyS**.

The objective is to ensure that every Oracle Cloud Infrastructure (OCI) resource is immediately recognizable, consistently named, and easy to locate within the OCI Console.

A standardized naming convention improves:

- Readability
- Operational consistency
- Troubleshooting
- Resource discovery
- Documentation quality
- Automation readiness

---

# 2. Design Principles

The naming convention follows five engineering principles.

## Consistency

Resources of the same type should always follow the same structure.

---

## Simplicity

Names should be easy to read and understand.

---

## Predictability

Engineers should be able to infer the purpose of a resource simply by reading its name.

---

## Scalability

The naming convention must remain effective as the environment grows.

---

## Automation

Names should be compatible with scripting, Infrastructure as Code, and automation tools.

---

# 3. Naming Convention

Every OCI resource follows the format:

```
<TYPE>-GnSyS-<FUNCTION>-<NN>
```

Where:

| Component | Description |
|-----------|-------------|
| TYPE | OCI resource type |
| GnSyS | Project identifier |
| FUNCTION | Business or technical purpose |
| NN | Sequential identifier |

Example:

```
VM-GnSyS-WEB-01
```

---

# 4. Naming Grammar

Examples:

```
VCN-GnSyS-01

VM-GnSyS-WEB-01

VM-GnSyS-APP-01

LB-GnSyS-PUBLIC-01

OBJ-GnSyS-BACKUP-01

ADB-GnSyS-ATP-01
```

---

# 5. Resource Prefixes

| Resource | Prefix |
|----------|--------|
| Compartment | CMP |
| Virtual Cloud Network | VCN |
| Subnet | SNET |
| Internet Gateway | IGW |
| NAT Gateway | NGW |
| Service Gateway | SGW |
| Route Table | RT |
| Security List | SL |
| Network Security Group | NSG |
| Compute Instance | VM |
| Load Balancer | LB |
| Block Volume | BV |
| Boot Volume | BOOT |
| Object Storage Bucket | OBJ |
| Autonomous Database | ADB |
| Vault | VLT |
| Key | KEY |
| User | USR |
| Group | GRP |
| Policy | POL |
| Notification Topic | TOPIC |
| Alarm | ALARM |
| Budget | BUDGET |

---

# 6. Examples

## Networking

```
VCN-GnSyS-01

SNET-GnSyS-PUB-01

SNET-GnSyS-PRV-01

IGW-GnSyS-01

NGW-GnSyS-01

SGW-GnSyS-01

RT-GnSyS-PUB-01

SL-GnSyS-PUB-01

NSG-GnSyS-WEB-01
```

---

## Compute

```
VM-GnSyS-WEB-01

VM-GnSyS-WEB-02

VM-GnSyS-APP-01
```

---

## Storage

```
OBJ-GnSyS-BACKUP-01

OBJ-GnSyS-LABS-01

BV-GnSyS-WEB-01
```

---

## Database

```
ADB-GnSyS-ATP-01
```

---

# 7. Reserved Prefixes

The following prefixes are reserved for future project phases.

| Prefix | Planned Usage |
|---------|---------------|
| TF | Terraform |
| K8S | Kubernetes |
| DR | Disaster Recovery |
| HA | High Availability |
| DEVOPS | OCI DevOps |
| ADR | Architecture Decision Record |

---

# 8. Best Practices

- Keep names concise.
- Use uppercase prefixes.
- Use hyphens as separators.
- Avoid spaces.
- Avoid special characters.
- Avoid environment-specific abbreviations unless required.
- Follow the standard consistently.

---

# 9. Anti-Patterns

Avoid names such as:

```
MyVM

Server1

CarlosVM

Test

NewVCN

VM123

Machine01
```

These names do not communicate purpose or ownership.

---

# 10. Future Evolution

The naming convention is expected to evolve as Project GnSyS incorporates:

- Terraform modules
- Kubernetes clusters
- OCI DevOps
- Multi-region deployments
- Enterprise networking

Future revisions should preserve backward compatibility whenever practical.

---

> **Engineering Principle #2**

> *If a resource cannot be identified by its name alone, the naming convention has failed.*
