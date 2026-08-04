# Epic 01 — Enterprise Web Application

| Property | Value |
|----------|-------|
| Epic | 01 |
| Status | In Progress |
| Project | GnSyS |
| Objective | Build a production-style enterprise web application on Oracle Cloud Infrastructure |

---

# Vision

Design, build and evolve an enterprise-style cloud application using Oracle Cloud Infrastructure Always Free resources.

This epic focuses on establishing a complete application stack while applying engineering best practices, documentation standards and production-inspired architecture.

---

# Business Objective

Transform the project from an infrastructure learning repository into a fully functional cloud application demonstrating:

- Cloud Networking
- Compute
- Web Services
- Database Integration
- Cloud Storage
- Operational Resilience

---

# Epic Roadmap

| Sprint | Name | Status |
|---------|-------------------------------|:------:|
| Sprint 01 | OCI Foundations & Enterprise Web Application | ✅ |
| Sprint 02 | Object Storage Integration | 🚧 |

---

# Architecture Evolution

## Sprint 01

```
Internet
    │
Apache
    │
Flask
    │
Oracle Autonomous Database
```

---

## Sprint 02 (Current)

```
Internet
    │
Apache
    │
Flask
 ┌──┴─────────────┐
 │                │
 ▼                ▼
ADB       Object Storage
```

---

## Future

```
                 Internet
                     │
              OCI Load Balancer
                     │
          ┌──────────┴──────────┐
          │                     │
          ▼                     ▼
   VM-GnSyS-WEB-01      VM-GnSyS-WEB-02
          │                     │
          └──────────┬──────────┘
                     ▼
            Oracle Autonomous DB

               Object Storage
```

---

# Deliverables

- Enterprise OCI networking
- Apache Reverse Proxy
- Flask Web Application
- Oracle Autonomous Database
- OCI Object Storage
- Runtime Configuration
- High Availability (future)

---

# Success Criteria

Epic 01 will be complete when:

- The application is fully operational.
- Application data resides in Oracle Autonomous Database.
- Static assets and documents reside in Object Storage.
- The application gracefully handles service outages.
- Documentation is complete.
