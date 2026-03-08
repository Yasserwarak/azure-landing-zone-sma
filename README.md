# Azure Landing Zone – Social Media Agency (Learning / Trial)

Azure Landing Zone architecture and operational standards for a **20-person EU-based social media agency learning environment**.

This project documents a **hybrid cloud architecture built in Azure following the Microsoft Cloud Adoption Framework (CAF)**.

The repository serves two purposes:

- Azure **architecture learning environment**
- **realistic hybrid cloud platform design** for a digital agency

---

# 🏢 Business Context

The fictional organization is a **social media and digital services agency based in Germany (Neuss / Düsseldorf)**.

The agency provides services such as:

- social media content production
- digital marketing campaigns
- brand development
- content strategy
- customer engagement

Some customers operate in **regulated sectors**, including:

- healthcare organizations
- financial institutions
- critical infrastructure companies

Therefore the architecture must support:

- strong identity governance
- auditability
- monitoring
- regulatory awareness

The environment follows a **Start-Small Azure Landing Zone model** designed for small organizations.

---

# 🏠 On-Prem Infrastructure (Ugreen NASync DXP4800 Plus)

The agency operates a hybrid environment with core workloads running on-premises.

| Component | Specs |
|--------|------|
| Model | Ugreen NASync DXP4800 Plus |
| CPU | Intel Pentium Gold 8505 (5 cores, 6 threads) |
| RAM | 16GB DDR5 |
| HDD | 2x 12TB RAID 1 |
| SSD | 2TB cache + 4TB storage |
| Network | 10GbE + 2.5GbE |
| OS | UGOS Pro (Linux-based) |
| Workloads | EspoCRM (Docker + MySQL) |

### On-Prem Workload

The primary internal system is:

**EspoCRM**

Architecture:

```
EspoCRM (Docker)
        ↓
MySQL Database
        ↓
NAS SSD Storage
```

This CRM manages:

- customer records
- contracts
- communications
- service information
- operational data

Backups of this system are stored in Azure.

---

# ☁️ Azure Landing Zone (Start-Small Architecture)

The Azure platform supports:

- cloud-hosted applications
- off-site backup storage
- monitoring
- automation workflows
- disaster recovery

Architecture overview:

```
On-Prem Infrastructure
│
├── Ugreen NAS (EspoCRM + MySQL)
│
└── Backup Snapshots
      ↓
Azure Blob Storage
```

Azure platform:

```
Azure Landing Zone
│
├── Entra ID (Identity)
├── Azure Storage (Backup)
├── Azure App Services
├── Azure Monitor
├── Azure Functions (PowerShell)
├── Azure Logic Apps
└── Azure AI Foundry
```

---

# 🌐 Cloud Applications

Azure hosts two primary applications.

### Company Website

The agency’s public website is hosted in Azure.

Purpose:

- company information
- service presentation
- contact forms
- marketing content

---

### Customer Portal & Gamification App

The agency also operates a **customer portal application**.

The application was **designed and developed internally by Yasser Warak and Amer Warak**.

Features include:

- contract overview
- service management
- meeting scheduling
- pricing transparency
- campaign tracking
- customer interaction management

The application also includes **gamification features** to increase engagement.

Customers can:

- track campaign progress
- view deliverables
- schedule meetings
- review content proposals

---

# 🤖 AI Content Automation Platform

The landing zone includes an **AI-powered automation system** designed to support internal creative workflows.

The system generates weekly content ideas and scripts for customers.

This automation platform uses **multiple AI agents orchestrated through Azure AI Foundry**.

### Agent roles

Example agents include:

- Idea Generation Agent
- Hook Generation Agent
- Script Writing Agent
- Brand Style Validation Agent
- Compliance Review Agent
- Weekly Packaging Agent

The system uses a **customer style databank** containing:

- brand tone
- target audience
- preferred content formats
- messaging patterns
- campaign preferences
- scheduling requirements

---

# ⚙️ Automation Architecture

Automation workflows are executed using:

| Service | Purpose |
|------|------|
| Azure Functions (PowerShell) | Automation execution |
| Azure Logic Apps | Workflow scheduling and delivery |
| Azure AI Foundry | Multi-agent AI orchestration |
| Azure Storage | Content and style database |
| Entra ID | Secure employee authentication |

Weekly workflow:

```
Customer Style Databank
        ↓
Automation Trigger
        ↓
Idea Generation Agent
        ↓
Hook Generation Agent
        ↓
Script Writing Agent
        ↓
Brand Style Validation
        ↓
Compliance Review
        ↓
Weekly Content Package
        ↓
Customer Delivery
```

---

# 🏗️ Resource Group Structure

Azure resources are organized into functional resource groups.

| Resource Group | Purpose |
|---|---|
| RG-Network | Networking infrastructure |
| RG-Apps | Website and customer application |
| RG-Backup | Backup storage |
| RG-Monitoring | Monitoring and logs |
| RG-Compute | Temporary disaster recovery VM |

---

# 📊 Monitoring and Observability

The platform uses **Azure Monitor and Log Analytics**.

Monitoring covers:

- application health
- automation workflows
- backup operations
- infrastructure status
- security events

Future improvement:

- Microsoft Sentinel (SIEM)

---

# 🛡️ Governance and Compliance

Because some clients operate in regulated sectors, the architecture considers:

- GDPR (EU data protection)
- KRITIS (critical infrastructure in Germany)
- NIS2 cybersecurity directive
- healthcare data protection
- financial sector audit expectations

Security mechanisms include:

- Entra ID identity governance
- RBAC access control
- centralized monitoring
- audit logging

---

# 📋 Documentation Index

## 01 Overview

- Architecture Overview
- Architecture Diagram

## 02 Design Areas (Microsoft CAF)

- Identity & Access Management
- Resource Organization
- Network Topology
- Security
- Governance
- Management
- Platform Automation & DevOps
- Billing & Tenant

## 03 Implementation

- Identity Architecture
- Resource Group Structure
- Networking
- Storage & Backup
- Compute & Applications
- Monitoring
- Governance
- AI Automation Platform
- Operations

---

# 📦 Applications

## Content Tracker App

Internal application used to manage:

- social media content planning
- campaign coordination
- customer engagement

## EspoCRM Integration

EspoCRM remains on-prem but integrates with Azure for:

- backup storage
- disaster recovery
- monitoring support

---

# 🚀 Quick Status

| Component | Status | Owner |
|---|---|---|
| Landing Zone Design | ✅ Documented | Cloud Admin |
| Ugreen NAS Setup | ✅ Live | Head of Operations |
| EspoCRM (Docker) | ✅ Running | Head of Operations |
| NAS → Azure Backup | ⏳ Script Ready | Cloud Admin |
| Website Deployment | ⏳ Pending | Cloud Admin |
| Customer Portal | ⏳ Development | Platform Team |
| AI Automation Platform | ⏳ Design Phase | Platform Team |

---

# 🔗 Key Resources

- Microsoft Cloud Adoption Framework  
- Azure Landing Zone Design Areas  
- Azure Architecture Center  
- Azure AI Foundry Documentation  

---

# 📚 Project Purpose

This repository was created to:

- learn Azure cloud architecture
- prepare for **AZ-104 certification**
- design a realistic hybrid cloud platform
- explore AI-assisted automation workflows
- build a scalable cloud foundation

The architecture follows the principle:

**"Start simple, design for scale."**

---

# 👨‍💻 Authors

**Yasser Warak**  
Cloud Architecture • Automation • Platform Design • Application Development • AI Integration
