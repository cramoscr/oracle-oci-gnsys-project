# Epic 01 — Enterprise Web Application

| Property | Value |
|----------|-------|
| Epic | 01 |
| Status | ✅ Completed |
| Project | GnSys |
| Objective | Build a production-style enterprise web application on Oracle Cloud Infrastructure |

---

# Vision

Design, build, and validate an enterprise-style cloud application using Oracle Cloud Infrastructure while applying production-inspired engineering practices, documentation standards, and separation between infrastructure and application components.

Epic 01 establishes the functional application foundation later extended by the distributed architecture implemented in Epic 02.

---

# Business Objective

Transform GnSys from an infrastructure learning environment into a functional cloud application demonstrating:

- Cloud Networking
- Compute
- Web Services
- Reverse Proxy Architecture
- Object Storage
- Autonomous Database Integration
- Runtime Configuration
- Application Health Monitoring
- Operational Resilience

---

# Epic Roadmap

| Sprint | Name | Status |
|---------|------|:------:|
| Sprint 01 | OCI Foundations & Enterprise Web Application | ✅ |
| Sprint 02 | Autonomous Database Integration | ✅ |
| Sprint 03 | Object Storage Integration | ✅ |

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
                     ┌──────┴──────┐
                     │             │
                     ▼             ▼
          Autonomous Database   Object Storage
                     │             │
              GNSYS_APP Schema   Cloud Objects
```

This working single-server application architecture became the baseline later extended by Epic 02 into a multi-server, load-balanced deployment.

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

## Object Storage

- ✅ OCI Object Storage resources created and configured
- ✅ Application server access to Object Storage
- ✅ Object Storage connectivity validated from the VM
- ✅ Bucket/object content enumeration validated through SSH
- ✅ Cloud-hosted content accessible from the compute environment

## Autonomous Database

- ✅ Oracle Autonomous Database
- ✅ Oracle Wallet configuration
- ✅ python-oracledb driver
- ✅ Dedicated application schema
- ✅ Database connectivity validation
- ✅ Application database connectivity
- ✅ Application configuration retrieved from the database

## Application Resilience

- ✅ Application health indicator
- ✅ Database health detection
- ✅ Database outage detection
- ✅ Graceful degradation during database connectivity failures
- ✅ Web tier remains reachable during database failure conditions

---

# Key Validation Performed

The application stack was validated incrementally:

1. SSH connectivity to the OCI Compute instance.
2. Apache HTTP service availability.
3. Flask application availability on its local application port.
4. Apache-to-Flask reverse proxy connectivity.
5. Object Storage access from the application server.
6. Object Storage bucket/object enumeration from SSH.
7. Autonomous Database connectivity using the Oracle Wallet.
8. Database access using the application Python virtual environment.
9. Retrieval of application information from the dedicated database schema.
10. Application behavior during database connectivity failures.
11. Recovery after database connectivity was restored.

These tests demonstrated the complete application environment and integration with multiple OCI services.

---

# Deliverables

- ✅ Enterprise OCI networking
- ✅ Oracle Linux Compute
- ✅ Apache Reverse Proxy
- ✅ Flask Web Application
- ✅ OCI Object Storage integration and connectivity validation
- ✅ Oracle Autonomous Database integration
- ✅ Oracle Wallet connectivity
- ✅ Dedicated application database schema
- ✅ Runtime application configuration
- ✅ systemd service management
- ✅ Application health monitoring
- ✅ Database health monitoring
- ✅ Graceful database failure handling
- ✅ Technical documentation

---

# Definition of Done

Epic 01 is considered complete because:

- The application is fully operational on OCI. ✅
- The application is accessible through Apache Reverse Proxy. ✅
- Object Storage connectivity from the compute environment was validated. ✅
- Object Storage content enumeration was validated. ✅
- Application data and configuration are retrieved from Oracle Autonomous Database. ✅
- Database authentication and connectivity are operational. ✅
- The application detects database availability. ✅
- The application handles database outages without losing the web tier. ✅
- The implementation is documented in the project repository. ✅

---

# Relationship with Epic 02

Epic 01 created the working single-server application stack and integrated the core OCI services used by GnSys.

Epic 02 subsequently extended this architecture by introducing:

- A second web server
- Application synchronization
- OCI Load Balancer
- Backend health checks
- Traffic distribution
- Application-tier High Availability

```text
Epic 01
Enterprise Web Application
      ✅ Completed
          │
          ▼
Epic 02
Distributed Architecture
      ✅ Completed
```

---

# Result

Epic 01 successfully established the production-style application foundation for GnSys.

The resulting environment demonstrates practical OCI experience across networking, compute, Linux administration, web services, Object Storage, Python application hosting, Oracle Autonomous Database connectivity, security configuration, service management, and application resilience.

This working application became the foundation for the distributed architecture implemented in Epic 02.

---

# Status

**EPIC 01 — COMPLETED ✅**
