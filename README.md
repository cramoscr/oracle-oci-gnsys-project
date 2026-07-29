# 🚀 Project GnSys
## Enterprise Oracle Cloud Infrastructure Learning Journey

<p align="center">

![Oracle Cloud](https://img.shields.io/badge/Oracle-Cloud-red)
![OCI](https://img.shields.io/badge/Learning-OCI%20Foundations-orange)
![Progress](https://img.shields.io/badge/Progress-95%25-brightgreen)
![Status](https://img.shields.io/badge/Status-Database%20Review-blue)
![License](https://img.shields.io/badge/License-MIT-green)

</p>

---

> **"Build first. Document always. Understand everything."**

Project **GnSys** is an enterprise-style Oracle Cloud Infrastructure learning repository documenting every lab, architectural decision, and lesson learned while progressing through the OCI Foundations learning path.

Unlike repositories that simply collect notes, this project is organized as if it were documenting a real cloud deployment.

---

# 📑 Table of Contents

- Project Overview
- Learning Dashboard
- Architecture
- Repository Structure
- Completed Labs
- Roadmap
- Standards
- ADRs
- Screenshots
- Learning Path
- Future Work

---

# 🎯 Project Objectives

- Learn OCI through hands-on implementation
- Understand enterprise cloud architecture
- Document every design decision
- Build a professional cloud engineering portfolio
- Prepare for OCI certifications

---

# 📊 Learning Dashboard

```text
Overall Progress

█████████████████████████████░ 95%
```

| Domain | Progress |
|--------------------------|:---:|
| Governance & IAM | ✅ |
| Networking | ✅ |
| Compute | ✅ |
| Storage | ✅ |
| Database Services | 🟡 |
| Monitoring | ✅ |
| Cost Management | ✅ |
| Documentation | ✅ |
| Practice Exams | 🟡 |
| Certification | ⏳ |

---

# 🏛️ High-Level Architecture

```text
                     Internet
                         │
                 Internet Gateway
                         │
          ┌──────── Public Subnet ────────┐
          │                               │
     Oracle Linux VM                 Future LB
          │
     Apache Web Server
          │
      Object Storage

         VCN (Enterprise Design)
```

*A graphical architecture diagram will be maintained under `/diagrams`.*

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
terraform/ (future)
```

---

# 🧪 Completed Labs

## Governance
- ✅ Compartments
- ✅ IAM Policies
- ✅ Tags

## Networking
- ✅ VCN
- ✅ Public Subnet
- ✅ Internet Gateway
- ✅ NAT Gateway
- ✅ Service Gateway
- ✅ Route Tables
- ✅ Security Lists
- ✅ Network Security Groups

## Compute
- ✅ Oracle Linux VM
- ✅ SSH Authentication
- ✅ Apache Deployment

## Storage
- ✅ Object Storage Fundamentals
- ✅ Block Volume Fundamentals

## Observability
- ✅ Monitoring Overview
- ✅ Notifications
- ✅ Cost Management

---

# 🧭 Engineering Standards

- Consistent naming convention
- Tagging strategy
- Documentation-first workflow
- Architecture Decision Records (ADRs)
- Reproducible labs

---

# 📝 Architecture Decision Records

| ADR | Description | Status |
|-----|-------------|:-----:|
| ADR-0001 | Documentation First | ✅ |
| ADR-0002 | Naming Standards | ✅ |
| ADR-0003 | NSG over Security Lists | ✅ |

---

# 📸 Screenshots

Each completed lab includes screenshots showing the deployed OCI resources.

```
screenshots/
```

---

# 🛣️ Learning Roadmap

## Phase 1 — OCI Foundations

- ✅ Core Services
- ✅ Networking
- ✅ Compute
- ✅ Storage
- 🟡 Database Review
- 🟡 Practice Exams
- ⏳ Certification Exam

## Phase 2 — OCI AI Foundations

- ⏳ AI Services
- ⏳ Generative AI
- ⏳ Vector Search

## Phase 3 — Professional OCI

- ⏳ Terraform
- ⏳ DevOps
- ⏳ OKE
- ⏳ High Availability
- ⏳ Disaster Recovery

---

# 📚 References

- Oracle Cloud Documentation
- Oracle University
- OCI Architecture Center

---

# 🤝 Contributing

This repository is maintained as a personal learning and portfolio project.
Suggestions and discussions are always welcome.

---

# 👨‍💻 Author

**Carlos Ramos Gomez**

Costa Rica

---

# 🙏 Acknowledgements

Technical implementation by the author.

Documentation, reviews, study guidance, and architectural discussions were developed with assistance from ChatGPT (OpenAI).

---

# 📄 License

MIT License
