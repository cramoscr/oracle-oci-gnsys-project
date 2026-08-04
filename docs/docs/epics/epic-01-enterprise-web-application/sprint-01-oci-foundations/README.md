# Sprint 01 — OCI Foundations & Enterprise Web Application

| Property | Value |
|----------|-------|
| Sprint | 01 |
| Epic | Enterprise Web Application |
| Status | Completed |
| Duration | July – August 2026 |

---

# Sprint Goal

Build the first functional version of the GnSyS application on Oracle Cloud Infrastructure.

The objective was to deploy a production-style web application integrating networking, compute, Apache, Flask, and Oracle Autonomous Database.

---

# Major Deliverables

- Oracle Cloud networking
- Oracle Linux Compute Instance
- Apache HTTP Server
- Reverse Proxy
- Python Virtual Environment
- Flask Application
- Oracle Autonomous Database
- Oracle Wallet
- python-oracledb
- Dedicated application schema
- Dynamic application configuration
- Database health monitoring
- Graceful database outage handling

---

# Sprint Outcome

The application successfully demonstrates:

- Web application deployment on OCI
- Reverse Proxy architecture
- Secure database connectivity
- Runtime configuration
- Dynamic content retrieval
- Resilience when the database becomes unavailable

---

# Architecture Achieved

```text
Internet
    │
Apache
    │
Flask
    │
 ┌──┴──────────────┐
 │                 │
 ▼                 ▼
Oracle Autonomous Database
```

---

# Status

✅ Completed
