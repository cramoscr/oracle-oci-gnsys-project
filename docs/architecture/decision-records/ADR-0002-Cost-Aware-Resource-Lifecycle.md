# ADR-0002 — Cost-Aware Resource Lifecycle

| Property | Value |
|---|---|
| **ADR ID** | ADR-0002 |
| **Project** | GnSyS |
| **Title** | Cost-Aware Resource Lifecycle |
| **Status** | Accepted |
| **Version** | 1.0 |
| **Date** | July 2026 |
| **Author** | Carlos R.G. |
| **Decision Owner** | Project GnSyS |

---

## Table of Contents

1. Context
2. Problem Statement
3. Decision
4. Resource Lifecycle Classes
5. End-of-Lab Requirements
6. Cost-Control Principles
7. Consequences
8. Alternatives Considered
9. Implementation Guidance
10. Review Triggers
11. Related Documents

---

## 1. Context

Project **GnSyS** is a long-term Oracle Cloud Infrastructure learning environment built inside an existing OCI tenancy.

The tenancy may contain other personal projects and workloads. GnSyS must therefore remain logically isolated, operationally manageable, and financially controlled.

Some OCI resources can remain provisioned with little or no ongoing cost, while others may continue generating charges even when they are not actively being used. Stopping a resource does not always eliminate all associated costs because storage, reserved capacity, networking services, logging, backups, or other dependent resources may continue to be billed.

Project GnSyS requires a lifecycle strategy that preserves the learning environment without creating uncontrolled recurring expenses.

---

## 2. Problem Statement

Completely deleting the environment after every laboratory would:

- remove useful architecture and configuration;
- make future laboratories slower to begin;
- reduce continuity between learning phases;
- require repeated manual reconstruction;
- make the final environment less useful as a technical portfolio.

Keeping every resource continuously active would:

- create unnecessary recurring costs;
- increase the risk of forgotten billable resources;
- make cost attribution more difficult;
- create operational clutter;
- increase the possibility of affecting unrelated projects in the tenancy.

A balanced lifecycle model is required.

---

## 3. Decision

Project GnSyS adopts a **cost-aware resource lifecycle model**.

Every resource created by a laboratory must be assigned one of the following lifecycle classifications:

1. **Permanent**
2. **Hibernate**
3. **Disposable**

The classification determines what happens to the resource after the laboratory is completed.

The default policy is:

> Preserve architecture and configuration when the ongoing cost is acceptable, stop resources when doing so materially reduces cost, and delete resources that provide no continuing value or cannot be retained economically.

No resource may be assumed to become free merely because it has been stopped.

Actual billing behavior must be verified before assigning a lifecycle classification.

---

## 4. Resource Lifecycle Classes

### 4.1 Permanent

Permanent resources remain provisioned after the laboratory.

This classification is appropriate when the resource:

- forms part of the reusable GnSyS architecture;
- has no material recurring cost under the current OCI pricing model;
- provides governance, organization, or documentation value;
- is difficult or unnecessary to reconstruct repeatedly;
- does not create an unacceptable security risk.

Possible examples include:

- compartments;
- IAM groups and policies;
- Virtual Cloud Networks;
- subnets;
- route tables;
- security lists;
- Network Security Groups;
- defined tags;
- budgets and selected alarms;
- small quantities of retained documentation or test data.

The word **Permanent** does not mean that the resource can never be removed. It means that retention is the expected end-of-lab action.

---

### 4.2 Hibernate

Hibernate resources are retained but placed in the lowest practical cost state when not being used.

This classification is appropriate when the resource:

- is useful in future laboratories;
- is expensive or time-consuming to reconstruct;
- supports a start-and-stop operating model;
- can be made significantly less expensive while inactive.

Possible examples include:

- Compute instances that support stopping without losing required state;
- database services that provide an appropriate stop or pause capability;
- reusable application environments;
- selected development services.

A Hibernate classification requires verification of all associated costs.

For example, stopping a Compute instance may reduce compute charges while attached boot volumes, block volumes, backups, public IP arrangements, or other dependent resources may still incur charges.

---

### 4.3 Disposable

Disposable resources must be removed after the laboratory or experiment.

This classification is appropriate when the resource:

- exists only to demonstrate a specific concept;
- duplicates an existing reusable resource;
- creates an unnecessary recurring cost;
- has no expected value after validation;
- can be recreated easily;
- increases exposure or operational complexity when retained.

Possible examples include:

- temporary test instances;
- experimental storage volumes;
- short-lived buckets;
- test public IP addresses;
- temporary load balancers;
- duplicated network components;
- proof-of-concept databases;
- temporary logs or backups.

Deletion must include dependent resources when applicable.

---

## 5. End-of-Lab Requirements

Every GnSyS laboratory must contain an **End-of-Lab State** section.

The section must identify:

- every created resource;
- its OCI name;
- its lifecycle classification;
- the required end-of-lab action;
- any residual cost consideration;
- whether the action was validated.

Example:

| Resource | OCI Name | Lifecycle | End-of-Lab Action | Residual Cost Check |
|---|---|---:|---|---|
| Compartment | `CMP-GnSyS` | Permanent | Keep | None expected |
| VCN | `VCN-GnSyS-01` | Permanent | Keep | Verify current pricing |
| Compute instance | `VM-GnSyS-WEB-01` | Hibernate | Stop | Check boot and block volumes |
| Temporary volume | `BV-GnSyS-TEMP-01` | Disposable | Delete | Confirm deletion |
| Test load balancer | `LB-GnSyS-TEST-01` | Disposable | Delete | Confirm billing has stopped |

A laboratory is not complete until its end-of-lab actions have been performed or intentionally deferred and documented.

---

## 6. Cost-Control Principles

Project GnSyS adopts the following cost-control principles.

### Isolate GnSyS resources

GnSyS resources must be placed in their designated compartment structure and must not depend on unrelated personal projects unless an explicit decision record approves the dependency.

### Apply project tags

Resources must follow the Project GnSyS Tagging Standard so that ownership, environment, management method, and purpose can be identified.

### Establish a budget

The project should have an OCI budget and alert thresholds appropriate to the approved learning investment.

### Verify rather than assume

OCI pricing, Free Tier eligibility, and billing behavior must be checked before deploying resources that may create charges.

### Review dependent resources

Stopping or deleting a primary resource does not guarantee that all dependent resources stop generating costs.

### Prefer reversible actions

When practical, choose a reversible low-cost state before deleting a resource that has continuing learning value.

### Eliminate abandoned resources

Resources with no owner, purpose, active laboratory, or documented future use must be reviewed for removal.

---

## 7. Consequences

### Positive consequences

- The completed architecture can remain available for future learning.
- Recurring costs can be reduced without deleting the entire project.
- Laboratories become operationally and financially auditable.
- Resource cleanup becomes part of the learning process.
- GnSyS remains isolated from other OCI projects.
- Cost management becomes a practical cloud-engineering skill.
- Future Terraform automation can implement the same lifecycle model.

### Negative consequences

- Each laboratory requires additional lifecycle analysis.
- OCI prices and service behavior must be reviewed periodically.
- Stopped resources may still create residual charges.
- Some resources may need to be rebuilt after deletion.
- Cost monitoring adds administrative work.
- A permanent environment can accumulate technical debt unless reviewed regularly.

These trade-offs are accepted because cost governance is a core objective of the project.

---

## 8. Alternatives Considered

### Alternative A — Delete everything after every laboratory

**Decision:** Rejected.

**Reason:** This would minimize residual costs but remove architectural continuity, increase reconstruction effort, and reduce the value of the resulting environment.

---

### Alternative B — Keep every resource active

**Decision:** Rejected.

**Reason:** This would create unnecessary recurring expenses and increase the risk of abandoned billable resources.

---

### Alternative C — Rely exclusively on Free Tier resources

**Decision:** Rejected as the only strategy.

**Reason:** Free Tier resources may be useful, but service eligibility, capacity, availability, and pricing can change. The project must remain cost-aware even when free resources are used.

---

### Alternative D — Classify resources as Permanent, Hibernate, or Disposable

**Decision:** Accepted.

**Reason:** This provides a practical balance between architectural continuity, learning value, operational control, and cost management.

---

## 9. Implementation Guidance

Each laboratory must perform the following lifecycle workflow:

```text
Design
  ↓
Estimate cost exposure
  ↓
Create and tag resources
  ↓
Execute the laboratory
  ↓
Validate the result
  ↓
Classify each resource
  ↓
Keep, hibernate, or delete
  ↓
Review remaining costs
  ↓
Update documentation
```

The resource inventory maintained by each laboratory must reference:

- **STD-001 — Naming Standard**
- **STD-002 — Tagging Standard**
- **ADR-0002 — Cost-Aware Resource Lifecycle**

Resources that cannot be clearly classified must not be left running by default.

---

## 10. Review Triggers

This decision must be reviewed when:

- Oracle changes OCI pricing or Free Tier conditions;
- a new laboratory introduces a significant fixed-cost service;
- monthly spending exceeds the approved project budget;
- GnSyS begins supporting a real application;
- Terraform or other automation is introduced;
- the project expands into another OCI region;
- a retained resource has not been used for an extended period;
- the existing tenancy structure changes materially.

A review may result in a new ADR that supersedes this decision.

---

## 11. Related Documents

- [Project Charter](../Project_Charter.md)
- [ADR-0001 — Documentation First](./ADR-0001-Documentation-First.md)
- [Naming Standard](../../standards/Naming_Standard.md)
- [Tagging Standard](../../standards/Tagging_Standard.md)

---

> **Engineering Principle**

> *Cloud resources should remain active because they provide value—not because they were forgotten.*
