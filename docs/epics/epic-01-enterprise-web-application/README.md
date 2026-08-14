# Epic 01 — Enterprise Web Application

| Property | Value |
|----------|-------|
| Epic | 01 |
| Status | ✅ Core Application Completed |
| Project | GnSys |
| Objective | Build a production-style enterprise web application on Oracle Cloud Infrastructure |

---

# Vision

Design and build an enterprise-style cloud application on Oracle Cloud Infrastructure while applying production-inspired engineering practices, documentation standards, and clear separation between infrastructure and application components.

Epic 01 establishes the functional application foundation used by the later distributed architecture work.

---

# Business Objective

Transform GnSys from an infrastructure learning environment into a functional cloud application demonstrating:

- Cloud Networking
- Compute
- Web Services
- Reverse Proxy Architecture
- Database Integration
- Runtime Configuration
- Application Health Monitoring
- Operational Resilience

---

# Epic Roadmap

| Sprint | Name | Status |
|---------|------|:------:|
| Sprint 01 | OCI Foundations & Enterprise Web Application | ✅ |
| Sprint 02 | Autonomous Database Integration | ✅ |
| Sprint 03 | Object Storage Integration | ⏸ Deferred |

Object Storage experimentation is documented separately under Sprint 03. It is not required for closure of the core Enterprise Web Application because the implemented application is fully operational without it.

---

# Implemented Architecture

```text
                    Internet
                        │
                 Public Subnet
                        │
                GnSys-VM-WEB-01
                        │
                Apache HTTP Server
                        │
                  Reverse Proxy
                        │
                Flask Application
                        │
               python-oracledb
                        │
                  Oracle Wallet
                        │
          Oracle Autonomous Database
                        │
                 GNSYS_APP Schema
                        │
             APPLICATION_INFO Table
```

This architecture became the baseline application stack later extended by Epic 02 into a multi-server, load-balanced deployment.

---

# Implemented Capabilities

## OCI Infrastructure

- ✅ Virtual Cloud Network
- ✅ Public Subnet
- ✅ Internet Gateway and routing
- ✅ Network Security Groups
- ✅ Oracle Linux Compute instance
- ✅ SSH key authentication

## Web Application

- ✅ Apache HTTP Server
- ✅ Apache Reverse Proxy
- ✅ Python virtual environment
- ✅ Flask application
- ✅ systemd application service
- ✅ HTTP application access

## Autonomous Database

- ✅ Oracle Autonomous Database
- ✅ Oracle Wallet configuration
- ✅ python-oracledb driver
- ✅ Dedicated application schema
- ✅ Application database connectivity
- ✅ Application configuration stored in database

## Application Resilience

- ✅ Application health indicator
- ✅ Database health detection
- ✅ Database outage detection
- ✅ Graceful degradation when database connectivity is unavailable
- ✅ Application remains reachable during database failure conditions

---

# Key Validation Performed

The application stack was validated incrementally:

1. SSH connectivity to the OCI Compute instance.
2. Apache HTTP service availability.
3. Flask application availability on its local application port.
4. Apache-to-Flask reverse proxy connectivity.
5. Autonomous Database connectivity using the Oracle Wallet.
6. Database access using the application Python virtual environment.
7. Retrieval of application information from the dedicated database schema.
8. Application behavior during database connectivity failures.
9. Recovery after database connectivity was restored.

These tests demonstrated the complete path from the browser-facing web tier to Oracle Autonomous Database.

---

# Deliverables

- ✅ Enterprise OCI networking
- ✅ Oracle Linux Compute
- ✅ Apache Reverse Proxy
- ✅ Flask Web Application
- ✅ Oracle Autonomous Database integration
- ✅ Oracle Wallet connectivity
- ✅ Dedicated application database schema
- ✅ Runtime application configuration
- ✅ systemd service management
- ✅ Application health monitoring
- ✅ Database health monitoring
- ✅ Graceful database failure handling
- ⏸ Object Storage application integration deferred to a separate enhancement sprint

---

# Definition of Done

The core Epic 01 objective is complete because:

- The application is fully operational on OCI. ✅
- The application is accessible through Apache Reverse Proxy. ✅
- Application data and configuration are retrieved from Oracle Autonomous Database. ✅
- Database authentication and connectivity are operational. ✅
- The application detects database availability. ✅
- The application handles database outages without losing the web tier. ✅
- The implementation is documented in the project repository. ✅

---

# Relationship with Epic 02

Epic 01 created the working single-server application stack.

Epic 02 subsequently extended this architecture by introducing:

- A second web server
- Application synchronization
- OCI Load Balancer
- Backend health checks
- Traffic distribution
- Application-tier High Availability

This separation keeps the project evolution clear:

```text
Epic 01
Working Enterprise Web Application
        │
        ▼
Epic 02
Distributed / High Availability Architecture
```

---

# Object Storage

Object Storage integration was originally included in the Epic 01 roadmap.

The repository contains a dedicated Sprint 03 for that experiment. The sprint remains available as a future enhancement, but it does not block completion of the core enterprise web application.

This distinction reflects the actual implementation state rather than marking unimplemented capabilities as completed.

---

# Result

Epic 01 successfully established the production-style application foundation for GnSys.

The resulting stack demonstrates practical OCI experience across networking, compute, Linux administration, web services, Python application hosting, Oracle Autonomous Database connectivity, security configuration, service management, and application resilience.

This working application became the foundation for the distributed architecture implemented in Epic 02.

---

# Status

**EPIC 01 — CORE APPLICATION COMPLETED ✅**
