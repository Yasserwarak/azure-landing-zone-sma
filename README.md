# Azure Landing Zone – Social Media Agency (Learning/Trial)

Azure landing zone architecture and operational standards for a **20-person EU-based social media agency learning environment**.

## 🏢 Business Context
- **20 employees**, Germany-based (Neuss, NRW)
- **Hybrid setup**: On-prem Ugreen DXP4800 NAS (EspoCRM) + Azure for backups, web apps, DR
- **Trial/learning environment** following Microsoft Cloud Adoption Framework (CAF)

## 🏠 On-Prem Infrastructure (Ugreen NASync DXP4800 Plus)

| Component | Specs |
|-----------|-------|
| **Model** | Ugreen NASync DXP4800 Plus |
| **CPU** | Intel Pentium Gold 8505 (5 cores, 6 threads, 4.4GHz max) |
| **RAM** | 16GB DDR5 |
| **HDD** | 2x 12TB RAID 1 |
| **SSD** | 2TB cache + 4TB storage |
| **Network** | 10GbE + 2.5GbE |
| **OS** | UGOS Pro (Linux-based, Docker support) |
| **Workloads** | EspoCRM (Docker + MySQL on SSD) |

## 🏗️ Architecture Summary

On-Prem (Ugreen DXP4800 NAS)
├── EspoCRM (Docker + MySQL on SSD)
└── Daily backup → Azure Blob Storage

Azure Landing Zone (Single Subscription - "Start Small")
├── Static Web Apps (Content Tracker app)
├── Blob Storage (EspoCRM backups)
├── Log Analytics (monitoring)
└── Entra ID SSO (employee access)

text

## 📋 Documentation Index

### 01 Overview
- [Architecture Overview](docs/01-overview/overview.md)
- [Architecture Diagram](docs/01-overview/architecture-diagram.md)

### 02 Design Areas (Microsoft CAF)
- [Identity & Access Management](docs/02-design-areas/identity-access.md)
- [Resource Organization](docs/02-design-areas/resource-organization.md)
- [Network Topology](docs/02-design-areas/network-topology.md)
- [Security](docs/02-design-areas/security.md)
- [Governance](docs/02-design-areas/governance.md)
- [Management](docs/02-design-areas/management.md)
- [Platform Automation & DevOps](docs/02-design-areas/platform-automation-devops.md)
- [Billing & Tenant](docs/02-design-areas/billing-tenant.md)

### 04 Standards
- [Naming & Tagging](docs/04-standards/naming-tagging.md)
- [RACI Matrix](docs/04-standards/raci.md)
- [Azure Policies](docs/04-standards/policies-baseline.md)

### 05 Applications
- [Content Tracker App](docs/05-apps/content-tracker-app.md)
- [EspoCRM Integration](docs/05-apps/crm-integration.md)

## 🚀 Quick Status

| Component | Status | Owner |
|-----------|--------|-------|
| Landing Zone Design | ✅ Documented | Cloud Admin |
| Ugreen NAS Setup | ✅ Live | Head of Operations |
| EspoCRM (Docker) | ✅ Running | Head of Operations |
| NAS→Azure Backup | ⏳ Script ready | Cloud Admin |
| Content Tracker App | ⏳ Deploy pending | Cloud Admin |

## 🔗 Key Resources
- [Microsoft Cloud Adoption Framework](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/)
- [Azure Landing Zone Design Areas](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/design-areas)
NOW copy ALL of this → paste into README.md → Commit → Tell me "README fixed" → I'll give you the next 3 files!
