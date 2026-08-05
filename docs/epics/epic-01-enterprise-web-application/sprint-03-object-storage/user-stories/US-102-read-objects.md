# US-102 — Read Objects from Object Storage

| Property | Value |
|----------|-------|
| Sprint | 03 |
| Epic | Enterprise Web Application |
| Status | Planned |
| Priority | High |

---

## User Story

**As a** cloud application

**I want** to retrieve files from OCI Object Storage

**So that** application content can be managed outside the virtual machine.

---

## Acceptance Criteria

- [ ] Read `documents/release_notes.txt`
- [ ] Read `documents/welcome.txt`
- [ ] Read `config/application_config.json`
- [ ] Display the downloaded content in a test script
- [ ] Handle missing objects gracefully

---

## Technical Tasks

- [ ] Connect to bucket `OBJ-GnSyS-LABS-01`
- [ ] Download a text object
- [ ] Decode its contents
- [ ] Parse the JSON configuration file
- [ ] Validate error handling

---

## Definition of Done

- Required objects are retrieved successfully
- Text and JSON contents are readable
- Download failures are controlled
- Evidence is documented
