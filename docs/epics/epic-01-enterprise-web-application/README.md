# Epic 01 — Enterprise Web Application

| Property | Value |
|----------|-------|
| Epic | 01 |
| Status | In Progress |
| Project | GnSyS |
| Objective | Build an enterprise-style web application on Oracle Cloud Infrastructure |

---

# Epic Goal

Build and evolve a functional web application running on Oracle Cloud Infrastructure.

The application will integrate compute, networking, database, storage, security, and application services while following documented engineering standards.

---

# Scope

This epic includes:

- OCI networking and compute infrastructure
- Oracle Linux virtual machine
- Apache HTTP Server
- Flask web application
- systemd service management
- Oracle Autonomous Database
- OCI Object Storage
- Application health indicators
- Graceful dependency failure handling

---

# Sprints

| Sprint | Objective | Status |
|--------|-----------|:------:|
| Sprint 01 | OCI Foundations and Enterprise Web Application | ✅ |
| Sprint 02 | Object Storage Integration | 🚧 |

---

# Current Architecture

```text
                        Internet
                            │
                     Internet Gateway
                            │
                    OCI Public Subnet
                            │
                    VM-GnSyS-WEB-01
                            │
                 Apache Reverse Proxy
                            │
                    Flask Application
                     ┌──────┴──────┐
                     │             │
                     ▼             ▼
          Autonomous Database   Object Storage
