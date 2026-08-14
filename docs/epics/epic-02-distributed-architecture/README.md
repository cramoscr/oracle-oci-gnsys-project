# Epic 02 — Distributed Architecture

| Property | Value |
|----------|-------|
| Epic | 02 |
| Status | ✅ Completed |
| Project | GnSys |
| Objective | Transform the application into a resilient multi-server cloud solution |

---

# Vision

Epic 02 evolves GnSys from a single-server application into a distributed OCI architecture with multiple application servers and load-balanced HTTP traffic.

The implementation follows a progressive engineering approach, introducing and validating each component separately to understand its role in scalability, resilience, and availability.

---

# Business Motivation

A single application server represents a Single Point of Failure (SPOF).

This epic removes that limitation at the application-server layer by introducing a second compute instance and OCI Load Balancer, allowing HTTP traffic to be distributed across healthy backends.

---

# Architecture Evolution

## Before

```text
                Internet
                    │
                Apache
                    │
             GnSys-VM-WEB-01
                    │
                    ▼
        Oracle Autonomous Database
```

---

## Implemented Architecture

```text
                     Internet
                         │
                 OCI Load Balancer
                         │
            ┌────────────┴────────────┐
            │                         │
            ▼                         ▼
    GnSys-VM-WEB-01          GnSys-VM-WEB-02
            │                         │
       Apache / Flask            Apache / Flask
            │                         │
            └────────────┬────────────┘
                         │
                         ▼
             Oracle Autonomous Database
```

The OCI Load Balancer distributes incoming HTTP requests between the two application servers.

Testing confirmed that requests can be served by either VM-WEB-01 or VM-WEB-02 and that traffic continues to be served when only one healthy backend remains available.

---

# Sprint Status

| Sprint | Objective | Status |
|---------|-----------|:------:|
| Sprint 03 | Multi-Server Deployment | ✅ |
| Sprint 04 | High Availability | ✅ |

---

# User Stories

## US-301 — Second Compute Instance

Deploy a second application server to introduce compute redundancy.

**Status:** ✅ Completed

---

## US-302 — Application Synchronization

Synchronize application code and configuration between both application servers.

**Status:** ✅ Completed

---

## US-303 — Shared Cloud Resources

Ensure both application servers can operate against the common application architecture and shared backend resources.

**Status:** ✅ Completed

---

## US-304 — Health Checks

Configure Load Balancer health checks to identify healthy and unhealthy application backends.

**Status:** ✅ Completed

---

## US-305 — Load Balancer

Distribute incoming HTTP traffic across both application servers.

**Status:** ✅ Completed

---

## US-306 — Failure Simulation

Validate that the application continues serving traffic when one application backend is unavailable.

**Status:** ✅ Completed

---

# Deliverables

- ✅ Multi-server deployment
- ✅ Two operational application servers
- ✅ Application synchronization
- ✅ OCI Load Balancer
- ✅ Backend health checks
- ✅ HTTP traffic distribution
- ✅ Backend failure validation
- ✅ Basic High Availability at the web/application tier

---

# Validation Performed

The distributed architecture was validated through direct observation of application responses.

With both backends healthy, repeated browser requests demonstrated traffic distribution between:

- `GnSys-VM-WEB-01`
- `GnSys-VM-WEB-02`

A backend availability test also confirmed that the Load Balancer continued routing requests to the remaining healthy server when the other backend was unavailable.

This demonstrated the fundamental behavior expected from the implemented high-availability web tier.

---

# Definition of Done

Epic 02 is considered complete because:

- Two application servers are operational. ✅
- Both servers serve the application. ✅
- Application deployment was synchronized between servers. ✅
- OCI Load Balancer distributes incoming traffic. ✅
- Backend health checks are operational. ✅
- Traffic distribution between both servers was validated. ✅
- Service continuity with a single healthy backend was validated. ✅
- GitHub documentation reflects the distributed topology. ✅

---

# Result

Epic 02 successfully transformed GnSys from a single-server deployment into a load-balanced, multi-server OCI application architecture.

The project now demonstrates several core cloud infrastructure concepts in practice:

- Compute redundancy
- Load balancing
- Backend health monitoring
- Traffic distribution
- Failure handling
- Basic application-tier High Availability

These capabilities provide a practical complement to the concepts covered in OCI Foundations certification preparation.

---

# Status

**EPIC 02 — COMPLETED ✅**
