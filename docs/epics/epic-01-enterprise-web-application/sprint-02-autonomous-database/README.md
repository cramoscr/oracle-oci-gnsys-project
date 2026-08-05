# Sprint 02 — Oracle Autonomous Database Integration

| Property | Value |
|----------|-------|
| Sprint | 02 |
| Epic | Enterprise Web Application |
| Status | Completed |
| Duration | July – August 2026 |

---

# Sprint Goal

Integrate Oracle Autonomous Database into the GnSyS application, replacing static application behavior with dynamic data retrieved from Oracle Cloud Infrastructure.

The application will establish secure connectivity using Oracle Wallet and the Python Oracle Database driver while implementing resilient database health monitoring.

---

# Business Motivation

Modern enterprise applications rely on managed cloud databases instead of local storage.

This sprint introduces Oracle Autonomous Database as the application's primary data platform while ensuring that temporary database outages do not affect application availability.

---

# Architecture Before

```text
                    Internet
                        │
                 Apache Reverse Proxy
                        │
                 Flask Application
```

---

# Architecture After

```text
                    Internet
                        │
                 Apache Reverse Proxy
                        │
                 Flask Application
                        │
                python-oracledb Driver
                        │
                  Oracle Wallet
                        │
        Oracle Autonomous Database (Always Free)
                        │
                 GNSYS_APP Schema
```

---

# User Stories

## US-101 — Provision Oracle Autonomous Database

Provision an Oracle Autonomous Database instance using the OCI Always Free tier.

Status:

✅ Completed

---

## US-102 — Secure Database Connectivity

Configure secure connectivity using Oracle Wallet and python-oracledb.

Status:

✅ Completed

---

## US-103 — Application Database Integration

Connect the Flask application to Oracle Autonomous Database.

Status:

✅ Completed

---

## US-104 — Database Health Monitoring

Implement runtime database connectivity validation and display database status within the application.

Status:

✅ Completed

---

## US-105 — Graceful Database Failure Handling

Ensure the application remains available even when Oracle Autonomous Database is offline.

Status:

✅ Completed

---

# Technical Tasks

- [x] Create Oracle Autonomous Database
- [x] Download Wallet
- [x] Install Wallet on VM
- [x] Install python-oracledb
- [x] Test secure connectivity
- [x] Create GNSYS_APP schema
- [x] Create application configuration table
- [x] Configure environment variables
- [x] Integrate Flask with Oracle Database
- [x] Display database information
- [x] Implement Database ONLINE/OFFLINE indicator
- [x] Handle database connection failures gracefully
- [x] Update documentation

---

# Deliverables

- Oracle Autonomous Database deployed
- Secure Oracle Wallet configuration
- Dedicated application schema
- Flask database integration
- Dynamic application configuration
- Database health monitoring
- Graceful degradation when the database is unavailable

---

# Definition of Done

Sprint 02 is complete when:

- The Flask application successfully connects to Oracle Autonomous Database.
- Application data is retrieved dynamically from the database.
- Database outages do not interrupt application availability.
- Database status is clearly displayed to users.
- Documentation is complete.

---

# Sprint Outcome

The application successfully demonstrates:

- Secure Oracle Database connectivity
- Runtime configuration retrieval
- Dynamic database integration
- Operational resilience during database outages

---

# Progress

| Story | Status |
|--------|:------:|
| US-101 | ✅ |
| US-102 | ✅ |
| US-103 | ✅ |
| US-104 | ✅ |
| US-105 | ✅ |

---

# Lessons Learned

- Oracle Wallet provides secure connectivity without exposing database credentials.
- The python-oracledb thin driver simplifies OCI database integration.
- Enterprise applications should degrade gracefully when external services become unavailable.

---

# Sprint Retrospective

The integration of Oracle Autonomous Database transformed the project from a static web application into a cloud-native application capable of consuming managed database services while maintaining high application availability during service interruptions.
