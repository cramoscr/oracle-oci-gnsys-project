# Sprint 03 — Object Storage Integration

| Property | Value |
|----------|-------|
| Sprint | 03 |
| Epic | Enterprise Web Application |
| Status | ✅ Completed |
| Project | GnSys |

---

# Sprint Goal

Extend the GnSys environment by integrating Oracle Cloud Infrastructure Object Storage and validating that the OCI Compute instance can access and enumerate cloud-hosted objects.

The sprint introduces Object Storage as an external cloud storage service and demonstrates interaction between Compute and Object Storage.

---

# Business Motivation

Application and project resources should not depend exclusively on local storage inside a virtual machine.

OCI Object Storage provides durable cloud storage that can be accessed independently from the lifecycle of an individual compute instance.

This sprint validates that GnSys can consume cloud-hosted storage resources from its application environment.

---

# Architecture

```text
                     OCI
                      │
          ┌───────────┴───────────┐
          │                       │
          ▼                       ▼
  GnSys Compute VM        OCI Object Storage
          │                       │
          └──── OCI Access ───────┘
```

Object Storage access was tested directly from the Oracle Linux VM through SSH.

---

# Implementation

The sprint established and validated the basic Object Storage integration required for the GnSys learning architecture.

Implemented capabilities include:

- OCI Object Storage resource usage
- Access from the GnSys Compute environment
- Bucket/object visibility from the VM
- Object enumeration from the Linux command line
- Validation of connectivity between Compute and Object Storage

---

# Validation Performed

Object Storage functionality was validated from an SSH session on the OCI Compute instance.

The tests confirmed that the VM could communicate with OCI Object Storage and enumerate the available content.

This provided practical validation of the relationship between:

```text
Compute
   │
   ▼
OCI Authentication / Access
   │
   ▼
Object Storage
   │
   ▼
Bucket Contents
```

---

# Completed Objectives

- [x] Use OCI Object Storage
- [x] Establish access from the Compute environment
- [x] Validate Object Storage connectivity
- [x] Enumerate Object Storage content from SSH
- [x] Confirm that cloud-hosted objects are accessible from the VM
- [x] Document the integration

---

# Deliverables

- ✅ OCI Object Storage environment
- ✅ Compute-to-Object-Storage connectivity
- ✅ Object enumeration validation
- ✅ SSH-based functional testing
- ✅ Documentation of the integration

---

# Definition of Done

Sprint 03 is considered complete because:

- Object Storage is available in the GnSys OCI environment. ✅
- The Compute instance can access Object Storage. ✅
- Bucket/object content can be enumerated from the VM. ✅
- Connectivity was validated through SSH. ✅
- The integration is documented. ✅

---

# Lessons Learned

This sprint demonstrated an important cloud architecture principle: application servers do not need to rely exclusively on local filesystem storage.

OCI Object Storage provides an independent storage layer that can be accessed by compute resources and can later support application assets, documents, configuration files, backups, or other shared content.

The exercise also reinforced the importance of validating cloud-service access directly from the runtime environment rather than assuming that successful resource creation implies successful application connectivity.

---

# Sprint Retrospective

The Object Storage exercise successfully validated communication between the GnSys Compute environment and OCI Object Storage.

The original sprint plan included broader application-level possibilities such as dynamic assets and configuration. The key learning objective actually implemented and validated was Compute-to-Object-Storage access and content enumeration.

Those results are sufficient to close the hands-on Object Storage integration exercise without claiming application features that were not explicitly validated.

---

# Status

**SPRINT 03 — COMPLETED ✅**
