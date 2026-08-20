# OCI Learning Journey Report

## Executive Summary

This report summarizes the Oracle Cloud Infrastructure (OCI) learning process carried out through the **GnSys** hands-on project and the subsequent preparation for the **OCI Foundations certification exam**.

The learning journey began on **July 3, 2026** and reached its first major completion milestone on **August 20, 2026**, when the certification examination was completed successfully.

The total elapsed calendar time was **48 days** (approximately **6 weeks and 6 days**).

Because the learning sessions were not tracked with a stopwatch, the effort figures in this report are reconstructed estimates based on the recorded sequence of labs, troubleshooting sessions, documentation work, conceptual reviews, and exam-practice sessions.

A reasonable estimate of total active learning effort is:

- **Estimated range:** 36-55 hours
- **Working midpoint estimate:** approximately 45 hours
- **Equivalent midpoint in minutes:** approximately 2,700 minutes
- **Average over the full 48-day period:** approximately 56 minutes per calendar day

These figures should be understood as a documented reconstruction rather than an exact time sheet.

---

## 1. Learning Period

| Item | Value |
|---|---|
| Initial date | July 3, 2026 |
| Final milestone date | August 20, 2026 |
| Calendar duration | 48 days |
| Approximate duration | 6 weeks, 6 days |
| Estimated active effort | 36-55 hours |
| Midpoint estimate | ~45 hours |
| Midpoint in minutes | ~2,700 minutes |

---

## 2. Learning Approach

The process was deliberately practical rather than limited to passive course consumption.

The initial objective was to learn OCI by building and documenting a real cloud environment. The project later evolved into a structured preparation path for the OCI Foundations certification.

The learning process combined:

- OCI conceptual study
- Hands-on infrastructure labs
- Linux administration and SSH access
- Networking design and troubleshooting
- Application deployment
- Database connectivity
- Storage integration
- Load balancing
- Security configuration
- GitHub documentation
- Architecture discussions
- Certification-oriented review
- Repeated multiple-choice exam simulations

This approach made the project both a certification preparation exercise and a small cloud engineering portfolio project.

---

## 3. Timeline and Major Milestones

### Phase 1 - Project Definition and OCI Foundation Setup
**Early July 2026**

The project started with the definition of the GnSys learning environment and its basic governance model.

Activities included:

- Definition of the project purpose and learning objectives
- Creation and organization of the OCI compartment structure
- Naming conventions using the `GnSys-` prefix
- Tagging strategy
- Initial architecture decisions
- Documentation-first approach using GitHub

This phase established the organizational structure used throughout the rest of the project.

---

### Phase 2 - Networking and Compute
**July 2026**

The first major hands-on infrastructure phase focused on OCI networking and compute.

Key activities included:

- Creation of the GnSys VCN
- Public subnet configuration
- Internet Gateway configuration
- Route table configuration
- Security List review
- Network Security Group (NSG) implementation
- Inbound SSH and HTTP access
- Creation of Oracle Linux compute instances
- SSH connectivity from a Windows workstation
- Validation of network paths and public access

This phase provided practical exposure to several OCI Foundations networking concepts, including VCNs, subnets, gateways, routes, and NSGs.

---

### Phase 3 - Web Application Deployment
**Mid to late July 2026**

The infrastructure was extended into an application platform.

The deployed stack included:

- Oracle Linux
- Apache HTTP Server
- Python
- Flask
- systemd
- Reverse proxy configuration

The application was installed under `/opt/gnsys-app` and exposed through Apache on HTTP port 80.

The process included troubleshooting HTTP errors, service configuration, proxy behavior, Linux service management, and application connectivity.

This made the project substantially more practical than a typical entry-level cloud certification lab.

---

### Phase 4 - Storage and Database Integration
**Late July 2026**

Additional OCI services were incorporated into the project.

#### Object Storage

Object Storage integration was implemented and tested from the compute environment.

#### Autonomous Database

An Autonomous Database was created and connected to the application environment.

Activities included:

- Wallet preparation
- TNS service configuration
- Python `oracledb` connectivity tests
- Database schema and table creation
- Application-to-database integration
- Troubleshooting Oracle authentication errors

The application successfully retrieved information from the database during testing.

---

### Phase 5 - High Availability and Load Balancing
**Late July to early August 2026**

The architecture was expanded to include multiple web instances and OCI Load Balancing.

The environment demonstrated:

- Multiple compute instances
- HTTP traffic distribution
- Backend health concepts
- Load balancer behavior
- Instance identification through the web application

Browser refresh tests visibly demonstrated requests being served by different backend instances.

This became one of the clearest practical demonstrations of OCI infrastructure behavior within the project.

---

### Phase 6 - Certification-Focused Study
**Late July through August 2026**

After the core hands-on architecture was functional, the learning process shifted progressively toward OCI Foundations certification preparation.

The review covered the major exam domains, including:

- OCI regions and availability domains
- Compartments and resource organization
- IAM users, groups, policies, authentication, and authorization
- Virtual Cloud Networks
- Public and private subnets
- Routing
- Internet Gateway, NAT Gateway, and Service Gateway concepts
- Local and Remote Peering
- FastConnect and VPN/IPsec concepts
- Compute services
- Autoscaling concepts
- Oracle Kubernetes Engine overview
- Functions and serverless concepts
- Object Storage
- Archive Storage
- Block Volumes
- File Storage
- Load Balancing
- Autonomous Database concepts
- Cloud Guard
- Security Zones
- Vault and encryption
- Pricing and cost management

Several areas received additional review because they were initially less intuitive, particularly:

- Networking connectivity models
- IAM scope and global versus regional resources
- Block Volume behavior
- Load Balancer scope
- Private Load Balancers

---

## 4. Exam Practice

A significant portion of the final preparation consisted of repeated multiple-choice simulations.

The practice evolved from relatively straightforward questions toward intentionally difficult and less predictable questions.

The focus was not only on selecting the correct answer, but also on explaining why competing options were incorrect.

This stage was especially useful for identifying subtle gaps in:

- Networking
- Storage
- IAM
- Availability and resilience concepts
- Resource scope

The final review sessions closely resembled the style and subject coverage of the Oracle University practice material.

---

## 5. Estimated Effort by Activity

The following distribution is an approximation reconstructed from the recorded learning sessions.

| Activity | Estimated effort |
|---|---:|
| Hands-on GnSys infrastructure | 12-18 hours |
| OCI concepts, course review, and theory | 8-12 hours |
| Practice questions and exam preparation | 8-12 hours |
| Troubleshooting and architecture discussions | 5-8 hours |
| Documentation and GitHub maintenance | 3-5 hours |
| **Estimated total** | **36-55 hours** |

The midpoint estimate is approximately **45 hours**.

This midpoint corresponds to approximately **2,700 minutes** of active work.

---

## 6. Nature of the Effort

The total effort should not be interpreted as 45 hours of certification video study.

A large portion of the time involved practical engineering work, including:

- Designing cloud infrastructure
- Configuring networks
- Deploying compute instances
- Working with Linux
- Troubleshooting SSH and HTTP connectivity
- Configuring Apache
- Deploying a Python/Flask application
- Creating and consuming OCI storage services
- Connecting applications to an Oracle Autonomous Database
- Configuring load balancing
- Testing distributed request handling
- Reviewing security boundaries
- Documenting technical decisions

As a result, the GnSys project represents both a learning exercise and demonstrable hands-on OCI experience.

---

## 7. Final Outcome

By August 20, 2026, the learning process had progressed through three distinct levels:

1. **Conceptual understanding** of OCI Foundations topics
2. **Hands-on implementation** of a functioning OCI application environment
3. **Certification-oriented validation** through structured exam practice

The certification examination was completed successfully on **August 20, 2026**.

The project therefore reached its original learning objective while also producing a documented OCI portfolio that includes networking, compute, security, storage, database integration, load balancing, application deployment, and technical documentation.

---

## 8. Measurement Notes

The effort estimates in this document are based on reconstructed activity rather than a formal time-tracking system.

The conversation history contains many short study sessions, several extended lab and debugging sessions, architecture discussions, and repeated exam-practice sessions, but not every interaction contains explicit start and end timestamps.

For this reason:

- **48 days** is a precise calendar-duration figure.
- **36-55 hours** is an estimated active-effort range.
- **~45 hours** is the recommended working estimate.

Future learning projects could improve measurement accuracy by recording the start time, end time, topic, and outcome of each study session.

---

## Conclusion

The GnSys OCI learning journey lasted approximately seven calendar weeks and required an estimated **45 hours of active effort**.

More importantly, the process moved beyond certification preparation into practical cloud implementation. The resulting project demonstrates the ability to understand OCI concepts, translate them into working infrastructure, troubleshoot real configuration issues, document technical decisions, and validate knowledge through formal certification preparation.

The project can therefore be presented not merely as exam study, but as a structured hands-on OCI learning project with measurable technical outcomes.
