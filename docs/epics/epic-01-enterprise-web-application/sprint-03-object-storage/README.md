# Sprint 03 — Object Storage Integration

| Property | Value |
|----------|-------|
| Sprint | 02 |
| Epic | Enterprise Web Application |
| Status | In Progress |
| Estimated Duration | 1–2 Weeks |

---

# Sprint Goal

Extend the GnSyS enterprise application by integrating Oracle Cloud Infrastructure Object Storage.

The application will begin consuming external resources directly from OCI, allowing documents, configuration files and static assets to be managed independently from the application deployment.

---

# Business Motivation

The current application stores all resources locally inside the virtual machine.

This sprint removes that limitation by introducing centralized cloud storage, enabling application content to evolve without modifying the application code.

---

# Architecture Before

```text
Internet
    │
Apache
    │
Flask
    │
Oracle Autonomous Database
```

---

# Architecture After

```text
                          Internet
                              │
                      Apache Reverse Proxy
                              │
                       Flask Application
                     ┌────────┴────────┐
                     │                 │
                     ▼                 ▼
      Oracle Autonomous DB     OCI Object Storage
                     │                 │
          Application Data     Static Assets
                               Configuration
                               Release Notes
                               Images
```

---

# User Stories

## US-201 — OCI Authentication

**Objective**

Authenticate the application against Oracle Cloud Infrastructure.

### Acceptance Criteria

- [ ] OCI SDK installed
- [ ] Authentication configured
- [ ] Namespace discovered
- [ ] Bucket accessible

---

## US-202 — Read Objects

**Objective**

Download text files from Object Storage.

### Acceptance Criteria

- [ ] Read release_notes.txt
- [ ] Read welcome.txt
- [ ] Handle download failures

---

## US-203 — Dynamic Configuration

**Objective**

Read application_config.json from Object Storage.

### Acceptance Criteria

- [ ] JSON downloaded
- [ ] JSON parsed
- [ ] Configuration applied

---

## US-204 — Images

**Objective**

Load static images from Object Storage.

### Acceptance Criteria

- [ ] Logo stored in Bucket
- [ ] Logo displayed by application
- [ ] Graceful fallback if unavailable

---

## US-205 — Flask Integration

**Objective**

Display Object Storage content on the application homepage.

### Acceptance Criteria

- [ ] Release Notes displayed
- [ ] Welcome message displayed
- [ ] Application remains operational if Object Storage is unavailable

---

# Technical Tasks

- [ ] Create Object Storage Bucket
- [x] Upload project documents
- [ ] Install OCI Python SDK
- [ ] Configure OCI Authentication
- [ ] Read Bucket contents
- [ ] Download Objects
- [ ] Integrate with Flask
- [ ] Improve exception handling
- [ ] Update README
- [ ] Update Architecture Diagram

---

# Deliverables

- OCI Object Storage integrated
- Dynamic Release Notes
- Dynamic Welcome Message
- Externalized Application Configuration
- Dynamic Static Assets

---

# Definition of Done

Sprint 02 will be considered complete when:

- Flask retrieves documents from Object Storage.
- Static assets are served from OCI.
- Configuration is externalized.
- The application continues operating when Object Storage is unavailable.
- Project documentation has been updated.

---

# Progress

| Story | Status |
|--------|:------:|
| US-201 | 🚧 |
| US-202 | 🚧 |
| US-203 | ⏳ |
| US-204 | ⏳ |
| US-205 | ⏳ |

---

# Lessons Learned

(To be completed during the sprint.)

---

# Sprint Retrospective

(To be completed at sprint closure.)
