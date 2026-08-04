# Epic 02 — Distributed Architecture

| Property | Value |
|----------|-------|
| Epic | 02 |
| Status | Planned |
| Project | GnSyS |
| Objective | Transform the application into a resilient multi-server cloud solution |

---

# Vision

The current application runs on a single virtual machine.

This epic introduces a distributed architecture by deploying multiple application servers across different Availability Domains, improving scalability, resilience, and availability.

The implementation intentionally follows a progressive engineering approach, introducing each component separately to understand its purpose before moving to the next layer.

---

# Business Motivation

A single server represents a Single Point of Failure (SPOF).

This epic eliminates that limitation by introducing redundancy and preparing the environment for High Availability.

---

# Architecture Evolution

## Before

```
                Internet
                    │
                Apache
                    │
                VM-GnSyS-WEB-01
                    │
      ┌─────────────┴─────────────┐
      ▼                           ▼
Autonomous Database        Object Storage
```

---

## Target Architecture

```
                     Internet
                         │
                 OCI Load Balancer
                         │
            ┌────────────┴────────────┐
            │                         │
            ▼                         ▼
    VM-GnSyS-WEB-01          VM-GnSyS-WEB-02
            │                         │
            └────────────┬────────────┘
                         ▼
             Oracle Autonomous Database

                  Object Storage
```

---

# Planned Sprints

| Sprint | Objective | Status |
|---------|-----------|:------:|
| Sprint 03 | Multi-Server Deployment | ⏳ |
| Sprint 04 | High Availability | ⏳ |

---

# Planned User Stories

## US-301 — Second Compute Instance

Deploy a second application server in another Availability Domain.

---

## US-302 — Application Synchronization

Synchronize application code and configuration between servers.

---

## US-303 — Shared Storage Strategy

Ensure both servers consume the same cloud resources.

---

## US-304 — Health Checks

Implement application health endpoints.

---

## US-305 — Load Balancer

Distribute incoming traffic across multiple servers.

---

## US-306 — Failure Simulation

Validate that the application continues operating after losing one server.

---

# Deliverables

- Multi-server deployment
- Cross-Availability Domain architecture
- Manual synchronization
- Health checks
- OCI Load Balancer
- Basic High Availability

---

# Definition of Done

Epic 02 will be considered complete when:

- Two application servers are operational.
- Both servers serve the same application version.
- Object Storage and Autonomous Database are shared.
- Traffic is distributed through OCI Load Balancer.
- The application remains available after shutting down one server.

---

# Success Criteria

- No single application server is a single point of failure.
- Deployment process is documented.
- Architecture diagrams are updated.
- GitHub documentation reflects the new topology.
