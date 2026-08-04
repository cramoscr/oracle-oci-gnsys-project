# Sprint 2 — Cloud Storage Integration

| Property | Value |
|----------|-------|
| Sprint | 02 |
| Status | In Progress |
| Estimated Duration | 1–2 weeks |
| Priority | High |
| Objective | Integrate OCI Object Storage into the GnSyS application |

---

# Sprint Goal

Integrate Oracle Object Storage into the existing Flask application so that application resources are dynamically retrieved from OCI instead of the local filesystem.

---

# Current Architecture

```
Internet
    │
Apache
    │
Flask
    │
 ┌──┴──────────────────────┐
 │                         │
 ▼                         ▼
Oracle Autonomous DB   Object Storage
```

---

# User Stories

## US-201 — OCI Authentication

**As a** cloud application

**I want** to authenticate against Oracle Cloud Infrastructure

**So that** I can access Object Storage resources.

### Acceptance Criteria

- [ ] OCI SDK installed
- [ ] Authentication configured
- [ ] Bucket accessible
- [ ] Bucket listing successful

---

## US-202 — Read Text Files

**As a** Flask application

**I want** to download text files from Object Storage

**So that** application content can be managed without redeploying.

### Acceptance Criteria

- [ ] Read release_notes.txt
- [ ] Read welcome.txt
- [ ] Handle download failures gracefully

---

## US-203 — Read Configuration

**As a** Flask application

**I want** to read application_config.json

**So that** configuration can be externalized.

### Acceptance Criteria

- [ ] Download JSON
- [ ] Parse JSON
- [ ] Apply configuration

---

## US-204 — Images from Object Storage

**As a** web application

**I want** to display images stored in Object Storage

**So that** static assets are centralized.

### Acceptance Criteria

- [ ] Download image
- [ ] Display logo
- [ ] Handle missing image

---

## US-205 — Integrate into Web Application

**As a** user

**I want** Release Notes to appear on the home page

**So that** application documentation is always current.

### Acceptance Criteria

- [ ] Release Notes displayed
- [ ] Content loaded dynamically
- [ ] Graceful degradation if Object Storage is unavailable

---

# Technical Tasks

- [ ] Install OCI Python SDK
- [ ] Configure OCI authentication
- [ ] Discover Namespace
- [ ] Access Bucket OBJ-GnSyS-LABS-01
- [ ] Download objects
- [ ] Integrate Object Storage with Flask
- [ ] Improve error handling
- [ ] Update README
- [ ] Update Architecture Diagram

---

# Definition of Done

Sprint 2 is complete when:

- Application retrieves Release Notes from Object Storage.
- Application retrieves configuration from Object Storage.
- Static assets are served from Object Storage.
- The application remains operational when Object Storage is unavailable.
- Documentation has been updated.

---

# Deliverables

- OCI SDK integration
- Dynamic content
- Externalized configuration
- Updated architecture
- Updated GitHub documentation

---

# Lessons Learned

(To be completed at sprint closure.)

---

# Retrospective

(To be completed at sprint closure.)
