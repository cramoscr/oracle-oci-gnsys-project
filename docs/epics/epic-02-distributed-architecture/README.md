# Epic 02 — Distributed Architecture

| Property | Value |
|----------|-------|
| Epic | 02 |
| Status | In Progress |
| Project | GnSys |
| Objective | Transform the application into a resilient multi-server cloud solution |

---

# Vision

Epic 02 evolves GnSys from a single-server application into a distributed OCI architecture with multiple application servers and load-balanced HTTP traffic.

The implementation follows a progressive engineering approach so that each infrastructure component can be deployed, tested, and understood independently.

---

# Architecture Evolution

## Before

```text
Internet
   │
GnSys-VM-WEB-01
   │
Apache Reverse Proxy
   │
Flask Application
   │
Oracle Autonomous Database
```

## Current Architecture

```text
                         Internet
                            │
                    OCI Load Balancer
                            │
                 ┌──────────┴──────────┐
                 │                     │
                 ▼                     ▼
        GnSys-VM-WEB-01       GnSys-VM-WEB-02
                 │                     │
                 ▼                     ▼
        Apache / Flask         Apache / Flask
                 │                     │
                 └──────────┬──────────┘
                            │
                            ▼
                Oracle Autonomous Database
```

The Load Balancer distributes requests between both web servers. Browser refresh testing confirmed that requests can be served by VM-WEB-01 and VM-WEB-02.

---

# Implementation Status

| Capability | Status |
|------------|:------:|
| Second Compute Instance | ✅ |
| Multi-server application deployment | ✅ |
| Application synchronization | ✅ |
| Load Balancer | ✅ |
| Backend health checks | ✅ |
| Traffic distribution validation | ✅ |
| Failure simulation / HA validation | ⏳ |
| Object Storage integration | ⏳ |

---

# User Stories

## US-301 — Second Compute Instance

Deploy a second application server to introduce compute redundancy.

**Status:** ✅ Completed

## US-302 — Application Synchronization

Deploy the same application configuration to both web servers.

**Status:** ✅ Completed

## US-303 — Shared Cloud Resources

Allow both application servers to consume common OCI services such as Autonomous Database.

**Status:** 🚧 In Progress

## US-304 — Health Checks

Configure health checks so that unhealthy backends can be detected by the Load Balancer.

**Status:** ✅ Completed

## US-305 — Load Balancer

Distribute incoming HTTP traffic across both application servers.

**Status:** ✅ Completed

## US-306 — Failure Simulation

Validate application availability when one backend server becomes unavailable.

**Status:** ⏳ Pending

---

# Deliverables

- ✅ Multi-server deployment
- ✅ Two application backends
- ✅ Manual application synchronization
- ✅ OCI Load Balancer
- ✅ Backend health checks
- ✅ Traffic distribution validation
- ⏳ Failure simulation and HA validation
- ⏳ Object Storage integration

---

# Definition of Done

Epic 02 will be considered complete when:

- Two application servers are operational. ✅
- Both servers serve the same application version. ✅
- Traffic is distributed through OCI Load Balancer. ✅
- Load Balancer health checks validate backend availability. ✅
- Shared application resources are documented and validated. 🚧
- The application remains available after intentionally removing one server. ⏳

---

# Current Result

GnSys now demonstrates a real multi-server OCI deployment rather than a single-instance application.

The remaining work for this epic is controlled backend failure testing and completion of the remaining shared-resource work.
