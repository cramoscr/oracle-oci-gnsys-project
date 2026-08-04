# 🚀 Project GnSys
## Building a Production-Style Oracle Cloud Application using OCI Always Free

<p align="center">

![Oracle Cloud](https://img.shields.io/badge/Oracle-Cloud-red)
![OCI](https://img.shields.io/badge/Learning-OCI%20Foundations-orange)
![Progress](https://img.shields.io/badge/Progress-98%25-brightgreen)
![Application](https://img.shields.io/badge/Application-ONLINE-success)
![Database](https://img.shields.io/badge/Database-Health%20Monitoring-blue)
![License](https://img.shields.io/badge/License-MIT-green)

</p>

---

> **"Build first. Document always. Understand everything."**

Project **GnSys** is an enterprise-style Oracle Cloud Infrastructure learning repository documenting every lab, architectural decision, and lesson learned while building a production-style cloud application from scratch using Oracle Cloud Infrastructure Always Free resources.

Unlike repositories that simply collect notes, this project follows engineering practices used in real enterprise environments.

---

# 📑 Table of Contents

- Project Overview
- Learning Dashboard
- High-Level Architecture
- Repository Structure
- Completed Labs
- Enterprise Features
- Architecture Decision Records
- Learning Roadmap
- Future Enhancements
- References

---

# 🎯 Project Objectives

- Learn Oracle Cloud Infrastructure through hands-on implementation
- Build a complete cloud-hosted enterprise application
- Understand enterprise architecture patterns
- Document every engineering decision
- Create a professional cloud engineering portfolio
- Prepare for Oracle OCI certifications

---

# 📊 Learning Dashboard

```text
Overall Progress

██████████████████████████████░ 98%
```

| Domain | Status |
|-------------------------------|:---:|
| Governance & IAM | ✅ |
| Networking | ✅ |
| Compute | ✅ |
| Storage Fundamentals | ✅ |
| Autonomous Database | ✅ |
| Enterprise Web Application | ✅ |
| Monitoring | ✅ |
| Cost Management | ✅ |
| Practice Exams | 🟡 |
| OCI Foundations Certification | ⏳ |

---

# 🏛️ High-Level Architecture

```text
                          Internet
                              │
                       Internet Gateway
                              │
                    OCI Public Subnet
                              │
                      GnSys-VM-WEB-01
                    Oracle Linux 9.8
                              │
                      Apache HTTP Server
                              │
                       Reverse Proxy
                              │
                        Flask Application
                              │
                     python-oracledb Driver
                              │
                        Oracle Wallet
                              │
          Oracle Autonomous Database 26ai (Always Free)
                              │
                      GNSYS_APP Schema
                              │
                  APPLICATION_INFO Table

                     Planned Next Phase
              ├── Object Storage
              ├── Second VM (AD-2)
              ├── Manual Synchronization
              └── Load Balancer
```

---

# 📂 Repository Structure

```text
docs/
 ├── architecture/
 ├── decisions/
 ├── roadmap/
 ├── standards/

labs/
diagrams/
screenshots/
scripts/
terraform/        (future)
```

---

# 🧪 Completed Labs

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

## Compute

- ✅ Oracle Linux Virtual Machine
- ✅ SSH Key Authentication
- ✅ Apache HTTP Server
- ✅ Reverse Proxy Configuration
- ✅ systemd Service Management

## Database

- ✅ Oracle Autonomous Database 26ai
- ✅ Wallet Configuration
- ✅ python-oracledb Driver
- ✅ Dedicated Application Schema
- ✅ Database Connectivity Validation

## Application

- ✅ Python Virtual Environment
- ✅ Flask Web Application
- ✅ Runtime Environment Variables
- ✅ Application Configuration Table
- ✅ Dynamic Configuration Loading
- ✅ Database Health Detection
- ✅ Graceful Database Failure Handling

## Observability

- ✅ Monitoring Overview
- ✅ Notifications
- ✅ Cost Analysis

---

# 💼 Enterprise Features

The current implementation already includes several enterprise-grade practices.

- ✅ Apache Reverse Proxy
- ✅ Flask Application Server
- ✅ Oracle Wallet Authentication
- ✅ python-oracledb Thin Driver
- ✅ Dedicated Application Database User
- ✅ Environment Variable Configuration
- ✅ systemd Service
- ✅ Application Health Indicator
- ✅ Database Health Indicator
- ✅ Graceful Degradation when Database is Offline
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

# 📸 Screenshots

Every completed lab contains screenshots documenting deployed OCI resources and application behavior.

```text
screenshots/
```

---

# 🛣️ Learning Roadmap

## Phase 1 — OCI Foundations

- ✅ Governance
- ✅ Networking
- ✅ Compute
- ✅ Storage Fundamentals
- ✅ Autonomous Database
- ✅ Enterprise Web Application
- 🟡 Practice Exams
- ⏳ OCI Foundations Certification

---

## Phase 2 — Enterprise Cloud Labs

- ⏳ Object Storage Integration
- ⏳ Read Application Assets from Bucket
- ⏳ Second Compute Instance (Availability Domain)
- ⏳ Manual Synchronization between Servers
- ⏳ Load Balancer
- ⏳ Health Checks
- ⏳ High Availability Simulation

---

## Phase 3 — Professional OCI

- ⏳ Terraform
- ⏳ OCI DevOps
- ⏳ Oracle Kubernetes Engine (OKE)
- ⏳ Monitoring & Logging
- ⏳ Disaster Recovery
- ⏳ Infrastructure as Code

---

# 🎯 Current Application Capabilities

Current application demonstrates:

- Enterprise deployment on Oracle Linux
- Apache acting as Reverse Proxy
- Flask backend
- Oracle Autonomous Database integration
- Oracle Wallet authentication
- Dedicated application schema
- Runtime configuration
- Database connectivity monitoring
- Automatic detection of database outages
- Graceful degradation while keeping the web application available

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
