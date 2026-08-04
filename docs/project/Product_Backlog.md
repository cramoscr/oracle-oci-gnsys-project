project/Product_Backlog.md
# Product Backlog

| Property | Value |
|----------|-------|
| Project | GnSyS |
| Document | Product Backlog |
| Version | 1.0 |
| Status | Active |
| Last Updated | August 2026 |

---

# Purpose

The Product Backlog defines the high-level capabilities planned for the GnSyS project.

Unlike Sprint Backlogs, which contain implementation tasks for a specific iteration, the Product Backlog represents the long-term evolution of the project.

Features are grouped into Epics and prioritized according to their architectural value.

---

# Product Vision

Build a production-style enterprise application on Oracle Cloud Infrastructure while documenting every engineering decision, implementation step, and lesson learned.

The project is intended to evolve from a single virtual machine into a highly available cloud application following enterprise engineering practices.

---

# Product Backlog

| ID | Feature | Epic | Priority | Status |
|----|---------|------|:--------:|:------:|
| PB-001 | Enterprise Web Application | Epic 01 | High | 🚧 |
| PB-002 | Distributed Architecture | Epic 02 | High | ⏳ |
| PB-003 | Cloud Automation | Epic 03 | Medium | ⏳ |
| PB-004 | Monitoring & Observability | Epic 03 | Medium | ⏳ |
| PB-005 | Disaster Recovery | Epic 03 | Low | ⏳ |

---

# Epic Overview

## Epic 01 — Enterprise Web Application

Objective:

Build the first production-style application running entirely on Oracle Cloud Infrastructure.

Deliverables:

- OCI Networking
- Compute
- Apache
- Flask
- Oracle Autonomous Database
- Object Storage

Status:

🚧 In Progress

---

## Epic 02 — Distributed Architecture

Objective:

Transform the application into a distributed system capable of running on multiple compute instances.

Planned Deliverables:

- Second Compute Instance
- Multi-Availability Domain deployment
- Manual synchronization
- Load Balancer
- Health Checks

Status:

⏳ Planned

---

## Epic 03 — Cloud Automation

Objective:

Automate infrastructure provisioning and application deployment.

Planned Deliverables:

- Terraform
- OCI DevOps
- CI/CD Pipelines
- Infrastructure as Code
- Monitoring
- Disaster Recovery

Status:

⏳ Planned

---

# Prioritization Strategy

Features are prioritized according to the following engineering principles:

1. Build a working application.
2. Improve scalability.
3. Improve resilience.
4. Automate repetitive tasks.
5. Optimize operations.

---

# Product Roadmap

```text
Epic 01
Enterprise Web Application
        │
        ▼
Epic 02
Distributed Architecture
        │
        ▼
Epic 03
Cloud Automation
```

---

# Success Criteria

The product vision will be considered achieved when:

- The application runs entirely on Oracle Cloud Infrastructure.
- Multiple OCI services are integrated.
- High availability has been implemented.
- Infrastructure provisioning is automated.
- Documentation is complete and reproducible.

---

# Related Documents

- Project Charter
- Decision Log
- Naming Standard
- Architecture Diagrams
- Epic Documentation
- Sprint Documentation
