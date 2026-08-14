# Product Backlog

| Property | Value |
|----------|-------|
| Project | GnSys |
| Document | Product Backlog |
| Version | 1.1 |
| Status | Active |
| Last Updated | August 2026 |

---

# Purpose

The Product Backlog defines the high-level capabilities planned for the GnSys project.

Unlike Sprint Backlogs, which contain implementation tasks for a specific iteration, the Product Backlog represents the long-term evolution of the project.

Features are grouped into Epics and prioritized according to their architectural value.

---

# Product Vision

Build a production-style enterprise application on Oracle Cloud Infrastructure while documenting engineering decisions, implementation steps, and lessons learned.

The project evolves progressively from a single virtual machine into a distributed and increasingly automated cloud application following enterprise engineering practices.

---

# Product Backlog

| ID | Feature | Epic | Priority | Status |
|----|---------|------|:--------:|:------:|
| PB-001 | Enterprise Web Application | Epic 01 | High | ✅ |
| PB-002 | Distributed Architecture | Epic 02 | High | 🚧 |
| PB-003 | Cloud Automation | Epic 03 | Medium | ⏳ |
| PB-004 | Monitoring & Observability | Epic 03 | Medium | ⏳ |
| PB-005 | Disaster Recovery | Epic 03 | Low | ⏳ |

---

# Epic Overview

## Epic 01 — Enterprise Web Application

Objective:

Build the first production-style application running on Oracle Cloud Infrastructure.

Implemented capabilities include:

- OCI Networking
- Compute
- Apache
- Flask
- Oracle Autonomous Database
- Application and database health handling

**Status:** ✅ Core implementation completed

---

## Epic 02 — Distributed Architecture

Objective:

Transform the application into a distributed system capable of running on multiple compute instances.

Current deliverables:

- ✅ Second Compute Instance
- ✅ Multi-server application deployment
- ✅ Manual synchronization
- ✅ OCI Load Balancer
- ✅ Backend Health Checks
- ✅ Traffic distribution validation
- ⏳ Controlled backend failure simulation
- ⏳ Object Storage integration

**Status:** 🚧 In Progress

---

## Epic 03 — Cloud Automation

Objective:

Automate infrastructure provisioning and application deployment.

Planned deliverables:

- Terraform
- OCI DevOps
- CI/CD Pipelines
- Infrastructure as Code
- Advanced Monitoring
- Disaster Recovery

**Status:** ⏳ Planned

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
   ✅ Core Complete
        │
        ▼
Epic 02
Distributed Architecture
   🚧 In Progress
        │
        ▼
Epic 03
Cloud Automation
   ⏳ Planned
```

---

# Current Milestone

The project has progressed from a single-server OCI application to a load-balanced, two-server web architecture.

The immediate remaining objectives are:

- Validate behavior when one backend becomes unavailable.
- Complete any remaining shared-resource integration work.
- Continue OCI Foundations practice exams and certification preparation.

---

# Success Criteria

The product vision will be considered achieved when:

- The application runs entirely on Oracle Cloud Infrastructure.
- Multiple OCI services are integrated.
- High availability has been implemented and validated.
- Infrastructure provisioning is automated.
- Documentation is complete and reproducible.

---

# Related Documents

- Project Charter
- Architecture Decision Records
- Naming Standard
- Epic Documentation
- Sprint Documentation
