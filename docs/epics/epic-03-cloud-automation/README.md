# Epic 03 — Cloud Automation

| Property | Value |
|----------|-------|
| Epic | 03 |
| Status | Planned |
| Project | GnSyS |
| Objective | Automate infrastructure provisioning, application deployment and cloud operations |

---

# Vision

After building a resilient multi-server architecture, the next logical step is to eliminate manual deployment and operational tasks.

This epic introduces Infrastructure as Code (IaC), Continuous Integration / Continuous Deployment (CI/CD), monitoring, observability and operational automation.

The goal is to evolve the project into a modern cloud platform that can be deployed repeatedly, consistently and reliably.

---

# Business Motivation

Manual deployments are error-prone, slow and difficult to reproduce.

Automation provides:

- Consistency
- Repeatability
- Faster deployments
- Reduced operational risk
- Better documentation
- Easier disaster recovery

---

# Architecture Evolution

## Current

```
Internet
    │
Load Balancer
    │
 ┌──┴────────┐
 │           │
 ▼           ▼
WEB-01    WEB-02
 │           │
 └────┬──────┘
      ▼
Autonomous Database

Object Storage
```

---

## Future

```
                GitHub Repository
                        │
                        ▼
               OCI DevOps Pipeline
                        │
        ┌───────────────┴───────────────┐
        ▼                               ▼
 Terraform                     Application Deployment
        │                               │
        └───────────────┬───────────────┘
                        ▼
                Oracle Cloud Infrastructure
```

---

# Planned Sprints

| Sprint | Objective | Status |
|---------|-----------|:------:|
| Sprint 05 | Infrastructure as Code | ⏳ |
| Sprint 06 | CI/CD Pipeline | ⏳ |
| Sprint 07 | Monitoring & Observability | ⏳ |
| Sprint 08 | Disaster Recovery | ⏳ |

---

# Planned User Stories

## US-501 — Terraform

Provision OCI infrastructure using Infrastructure as Code.

---

## US-502 — OCI DevOps

Automate application deployment.

---

## US-503 — GitHub Integration

Connect the repository with OCI DevOps.

---

## US-504 — Monitoring

Collect metrics, logs and application health information.

---

## US-505 — Alarms & Notifications

Generate operational alerts.

---

## US-506 — Disaster Recovery

Document and validate recovery procedures.

---

# Deliverables

- Terraform modules
- OCI DevOps Pipeline
- CI/CD automation
- Monitoring dashboards
- Alarms
- Notifications
- Disaster Recovery documentation

---

# Definition of Done

Epic 03 will be considered complete when:

- Infrastructure can be recreated using Terraform.
- Application deployment is automated.
- Monitoring and alerts are operational.
- Disaster Recovery procedures are documented and validated.
- Operational documentation is complete.

---

# Success Criteria

- Zero manual infrastructure provisioning.
- Repeatable deployments.
- Automated application updates.
- Operational visibility through monitoring.
- Reproducible cloud environment.
