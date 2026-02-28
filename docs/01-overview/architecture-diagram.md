# Architecture Diagram (Target State) — Azure Landing Zone (Learning / AZ-104)

This document describes the **target state architecture** for a fictional 20-person social media agency in Düsseldorf, Germany.

The goal of this project is to:
- Prepare for the **AZ-104: Microsoft Azure Administrator** exam
- Apply Azure Landing Zone best practices
- Build a structured hybrid cloud architecture in a cost-aware way

---

## Key Design Decisions

- **Single Azure Subscription** (cost optimized)
  - Future: split into Dev / Prod subscriptions
- **Identity**: Microsoft Entra ID only (no on-prem AD DS)
- **Connectivity**: No VPN initially (budget constraint: ~$170/month)
  - NAS sends backups via **HTTPS over public internet**
- **Networking**: One simple Azure VNet for learning purposes
- **Security**: CRM data classified as **high sensitivity**
- **Monitoring**: Log Analytics now; Microsoft Sentinel later
- **Disaster Recovery**: Restore backups to a temporary Azure VM if NAS fails

> Note: Azure Blob Storage does not sync a database automatically.
> The NAS generates full volume backups/snapshots and uploads them to Azure Blob Storage.

---

## High-Level Architecture Diagram

```mermaid
flowchart LR

%% ===== On-Prem =====
subgraph ONP[On-Prem (Office Düsseldorf, Germany)]
  NAS[Ugreen NASync DXP4800 Plus]
  CRM[EspoCRM (Docker Container)]
  DB[(MySQL Database on SSD)]
  NAS --> CRM
  CRM --> DB
end

%% ===== Identity =====
subgraph ID[Identity]
  Entra[Microsoft Entra ID (Cloud-only identities)]
end

%% ===== Azure =====
subgraph AZ[Azure (EU Region) - Single Subscription]

  subgraph NET[Networking]
    VNET[Virtual Network (VNet)]
    SUBNET[Subnet (Shared Services)]
    NSG[Network Security Group]
    VNET --- SUBNET
    SUBNET --- NSG
  end

  STORAGE[Azure Storage Account (Blob Storage)]
  LA[Log Analytics Workspace]
  VM[Azure VM (Temporary DR Restore)]
  WEB[Content Tracker Web App (SSO)]
end

%% ===== Flows =====
NAS -->|Full Volume Backup (HTTPS)| STORAGE
STORAGE -->|Diagnostics Logs| LA
WEB -->|SSO Authentication| Entra
VM -->|Restore Backups| STORAGE
```

---

## Component Overview

### On-Prem Infrastructure
- Ugreen NASync DXP4800 Plus
- EspoCRM running in Docker
- MySQL database stored on SSD
- Full volume backup snapshots created regularly

### Azure Components
- Storage Account (Blob Storage) for backup retention
- Log Analytics Workspace for monitoring
- Content Tracker Web App (future expansion possible)
- Temporary Azure VM for disaster recovery restore

---

## Security Considerations (Learning Focus)

- Encryption at rest (default for Azure Storage)
- RBAC-based access control via Entra ID
- Future improvement:
  - Immutable Blob Storage (WORM)
  - Private Endpoints
  - Microsoft Sentinel integration

---

## Planned Future Improvements

- Add Azure Monitor alerts & dashboards
- Introduce Microsoft Sentinel (SIEM)
- Implement Site-to-Site VPN when budget allows
- Separate Dev and Production subscriptions
- Implement Azure Policies and Governance controls
