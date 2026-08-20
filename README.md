# 🚀 Project GnSys
## Building a Production-Style Oracle Cloud Application using OCI Always Free

<p align="center">

![Oracle Cloud](https://img.shields.io/badge/Oracle-Cloud-red)
![OCI](https://img.shields.io/badge/OCI-Foundations%20Certified-brightgreen)
![Progress](https://img.shields.io/badge/Progress-100%25-brightgreen)
![Application](https://img.shields.io/badge/Application-ONLINE-success)
![Architecture](https://img.shields.io/badge/Architecture-Load%20Balanced-blue)
![License](https://img.shields.io/badge/License-MIT-green)

</p>

---

> **"Build first. Document always. Understand everything."**

Project **GnSys** is an enterprise-style Oracle Cloud Infrastructure learning repository documenting hands-on labs, architectural decisions, and lessons learned while building a production-style cloud application from scratch using Oracle Cloud Infrastructure Always Free resources.

Unlike repositories that simply collect notes, this project follows engineering practices used in real enterprise environments.

---

# 🎯 Project Objectives

- Learn Oracle Cloud Infrastructure through hands-on implementation
- Build a complete cloud-hosted enterprise application
- Understand enterprise architecture patterns
- Document engineering decisions
- Create a professional cloud engineering portfolio
- Prepare for Oracle OCI certifications

---

# 🏆 Certification Milestone

On **August 20, 2026**, the project reached its original certification goal:

- ✅ **Oracle Cloud Infrastructure Certified Foundations Associate**
- ✅ Exam: **1Z0-1085-26 — Oracle Cloud Infrastructure Foundations Associate**
- ✅ Certification earned after completing the GnSys hands-on learning path, focused conceptual review, and Oracle practice-exam preparation

This milestone validates the OCI fundamentals exercised throughout the project, including governance and IAM, networking, compute, storage, security, cost management, and core OCI architecture concepts.

---

# 📊 Learning Dashboard

```text
Overall Progress

██████████████████████████████ 100%
```

| Domain | Status |
|-------------------------------|:---:|
| Governance & IAM | ✅ |
| Networking | ✅ |
| Compute | ✅ |
| Storage Fundamentals | ✅ |
| Autonomous Database | ✅ |
| Enterprise Web Application | ✅ |
| Distributed Web Architecture | ✅ |
| Load Balancing | ✅ |
| Monitoring | ✅ |
| Cost Management | ✅ |
| Practice Exams | ✅ |
| OCI Foundations Certification | ✅ |

---

# 🏛️ High-Level Architecture

```text
                              Internet
                                  │
                           Internet Gateway
                                  │
                           OCI Load Balancer
                                  │
                     ┌────────────┴────────────┐
                     │                         │
                     ▼                         ▼
             GnSys-VM-WEB-01          GnSys-VM-WEB-02
             Oracle Linux 9.8          Oracle Linux 9.8
                     │                         │
                Apache HTTP               Apache HTTP
                Reverse Proxy             Reverse Proxy
                     │                         │
                Flask App                  Flask App
                     │                         │
                     └────────────┬────────────┘
                                  │
                         python-oracledb
                                  │
                            Oracle Wallet
                                  │
                Oracle Autonomous Database 26ai
                                  │
                           GNSYS_APP Schema
```

The OCI Load Balancer distributes HTTP requests across both web application backends. Testing confirmed that browser requests can be served by either VM-WEB-01 or VM-WEB-02.

---

# 📂 Repository Structure

```text
README.md
docs/
 ├── architecture/
 │    ├── decision-records/
 │    └── project_charter.md
 ├── epics/
 │    ├── epic-01-enterprise-web-application/
 │    ├── epic-02-distributed-architecture/
 │    └── epic-03-cloud-automation/
 ├── project/
 └── standards/
```

---

# 🧪 Completed Labs and Capabilities

## Governance

- ✅ Compartments
- ✅ IAM Policies
- ✅ Resource Tags

## Networking

- ✅ Virtual Cloud Network (VCN)
- ✅ Public Subnet
- ✅ Internet Gateway
- ✅ NAT Gateway
- ✅ Service Gateway
- ✅ Route Tables
- ✅ Security Lists
- ✅ Network Security Groups (NSG)

## Compute & Web Tier

- ✅ Two Oracle Linux Virtual Machines
- ✅ SSH Key Authentication
- ✅ Apache HTTP Server
- ✅ Reverse Proxy Configuration
- ✅ Flask Application
- ✅ systemd Service Management
- ✅ Manual application synchronization

## Database

- ✅ Oracle Autonomous Database 26ai
- ✅ Wallet Configuration
- ✅ python-oracledb Driver
- ✅ Dedicated Application Schema
- ✅ Database Connectivity Validation

## High Availability Foundations

- ✅ OCI Load Balancer
- ✅ Two application backends
- ✅ Backend health checks
- ✅ HTTP traffic distribution validation
- ⏳ Controlled backend failure simulation

## Observability & Cost

- ✅ Monitoring Overview
- ✅ Notifications
- ✅ Cost Analysis

---

# 💼 Enterprise Features

- ✅ Apache Reverse Proxy
- ✅ Flask Application Server
- ✅ Oracle Wallet Authentication
- ✅ python-oracledb Thin Driver
- ✅ Dedicated Application Database User
- ✅ Environment Variable Configuration
- ✅ systemd Service
- ✅ Application Health Indicator
- ✅ Database Health Indicator
- ✅ Graceful Database Failure Handling
- ✅ Multi-server application deployment
- ✅ OCI Load Balancer
- ✅ Backend health monitoring
- ✅ Separation between Infrastructure and Application Configuration

---

# 🧭 Engineering Standards

- Documentation First
- Consistent Naming Convention
- Tagging Strategy
- Infrastructure Documentation
- Architecture Decision Records (ADR)
- Reproducible Labs
- Enterprise Naming Standards

---

# 📝 Architecture Decision Records

| ADR | Description | Status |
|-----|-------------|:-----:|
| ADR-0001 | Documentation First | ✅ |
| ADR-0002 | Naming Standards | ✅ |
| ADR-0003 | Network Security Groups over Security Lists | ✅ |

---

# 🛣️ Learning Roadmap

## Phase 1 — OCI Foundations

- ✅ Governance
- ✅ Networking
- ✅ Compute
- ✅ Storage Fundamentals
- ✅ Autonomous Database
- ✅ Enterprise Web Application
- ✅ Practice Exams
- ✅ OCI Foundations Certification

## Phase 2 — Distributed Cloud Architecture

- ✅ Second Compute Instance
- ✅ Manual Synchronization between Servers
- ✅ Load Balancer
- ✅ Health Checks
- ✅ Traffic Distribution
- ⏳ High Availability Failure Simulation
- ⏳ Object Storage Integration

## Phase 3 — Professional OCI

- ⏳ Terraform
- ⏳ OCI DevOps
- ⏳ Oracle Kubernetes Engine (OKE)
- ⏳ Advanced Monitoring & Logging
- ⏳ Disaster Recovery
- ⏳ Infrastructure as Code

---

# 🎯 Current Application Capabilities

GnSys currently demonstrates:

- Enterprise deployment on Oracle Linux
- Two web application servers
- Apache acting as Reverse Proxy
- Flask backend
- OCI Load Balancer distributing HTTP traffic
- Backend health checks
- Oracle Autonomous Database integration
- Oracle Wallet authentication
- Dedicated application schema
- Runtime configuration
- Database connectivity monitoring
- Graceful degradation when the database is unavailable

---

# 📚 References

- Oracle Cloud Infrastructure Documentation
- Oracle University
- Oracle Architecture Center

---

# 🤝 Contributing

This repository is maintained as a personal learning and portfolio project.

Suggestions, discussions, and architectural feedback are always welcome.

---

# 👨‍💻 Author

**Carlos Ramos Gomez**

Costa Rica

---

# 🙏 Acknowledgements

Technical implementation by the author.

Architecture reviews, engineering discussions, documentation improvements, study planning, and technical mentoring were developed with assistance from ChatGPT (OpenAI).

---

# 📄 License

MIT License
