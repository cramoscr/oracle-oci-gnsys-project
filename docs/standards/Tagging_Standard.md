# Tagging Standard

| Property | Value |
|----------|-------|
| **Document ID** | STD-002 |
| **Project** | GnSyS |
| **Document** | Tagging Standard |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Carlos R.G. |
| **Last Updated** | July 2026 |

---

# Table of Contents

1. Purpose
2. Objectives
3. Tagging Strategy
4. Mandatory Tags
5. Optional Tags
6. Tag Definitions
7. Examples
8. Best Practices
9. Anti-Patterns
10. Future Evolution

---

# 1. Purpose

This document defines the tagging strategy adopted by **Project GnSyS**.

A consistent tagging strategy improves governance, operational management, reporting, automation, and cost visibility across Oracle Cloud Infrastructure resources.

Every resource deployed within Project GnSyS should include the mandatory tags defined in this document whenever OCI supports tagging.

---

# 2. Objectives

The tagging strategy is designed to achieve the following goals:

- Identify resource ownership.
- Group resources by project.
- Distinguish environments.
- Improve operational visibility.
- Simplify automation.
- Facilitate cost reporting.
- Support future Infrastructure as Code deployments.

---

# 3. Tagging Strategy

Project GnSyS adopts a simple and consistent tagging model.

Mandatory tags describe:

- Ownership
- Project
- Environment
- Resource lifecycle

Optional tags provide additional operational information when appropriate.

---

# 4. Mandatory Tags

| Tag | Example | Description |
|------|---------|-------------|
| Project | GnSyS | Project identifier |
| Environment | LAB | Deployment environment |
| Owner | Carlos | Resource owner |
| ManagedBy | Manual | Deployment method |
| Version | 1.0 | Current project version |

---

# 5. Optional Tags

| Tag | Example | Description |
|------|---------|-------------|
| Purpose | Public Web Server | Business purpose |
| CostCenter | TRAINING | Cost allocation |
| Department | Engineering | Organizational unit |
| Criticality | Low | Operational importance |
| Notes | OCI Foundations Lab | Additional comments |

---

# 6. Tag Definitions

## Project

Identifies the project that owns the resource.

Example:

```
Project = GnSyS
```

---

## Environment

Defines where the resource belongs.

Possible values:

```
LAB
DEV
TEST
QA
UAT
PROD
```

Current project value:

```
LAB
```

---

## Owner

Identifies the individual responsible for the resource.

Example:

```
Carlos
```

---

## ManagedBy

Indicates how the resource was created.

Possible values:

```
Manual

Terraform

OCI Resource Manager

Ansible
```

Current value:

```
Manual
```

---

## Version

Represents the current project release.

Example:

```
1.0
```

---

# 7. Examples

Example tags applied to a Compute Instance:

| Tag | Value |
|------|-------|
| Project | GnSyS |
| Environment | LAB |
| Owner | Carlos |
| ManagedBy | Manual |
| Version | 1.0 |

---

Example tags applied to an Object Storage Bucket:

| Tag | Value |
|------|-------|
| Project | GnSyS |
| Environment | LAB |
| Owner | Carlos |
| ManagedBy | Manual |
| Purpose | Architecture Diagrams |

---

# 8. Best Practices

- Apply tags during resource creation whenever possible.
- Keep tag values short and consistent.
- Avoid abbreviations unless officially defined.
- Reuse existing tag values.
- Review tags periodically as the environment evolves.

---

# 9. Anti-Patterns

Avoid tags such as:

```
Test

CarlosVM

Misc

Unknown

New

Temporary
```

Avoid inconsistent values such as:

```
Prod

Production

production

PRODUCTION
```

Choose one value and use it consistently.

---

# 10. Future Evolution

Future project phases may introduce additional tags for:

- Terraform Workspaces
- Kubernetes Clusters
- Multi-Region Deployments
- Disaster Recovery
- Cost Optimization
- Compliance
- Security Classification

The tagging strategy should remain backward compatible whenever possible.

---

> **Engineering Principle #3**

> *If a resource has no owner, no purpose, and no context, it should not exist.*
