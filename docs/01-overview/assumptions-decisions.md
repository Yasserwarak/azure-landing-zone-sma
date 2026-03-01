# Assumptions & Architectural Decisions

This document captures the key assumptions and decisions made for the Azure Landing Zone design.

---

## 1. Business Assumptions

| Category | Decision |
|-----------|----------|
| Company Size | 20 employees (initial) |
| Growth Plan | Potential scale to 50–100 users |
| Location | Düsseldorf, Germany |
| Budget | ~$170/month (initial learning phase) |
| Work Model | On-site only (no remote access required) |

---

## 2. Identity & Access

| Area | Decision |
|------|----------|
| Identity Provider | Microsoft Entra ID (Cloud-only) |
| On-Prem AD | Not used |
| Authentication Method | SSO via Entra ID |
| Access Control | Azure RBAC |

---

## 3. Networking

| Area | Decision |
|------|----------|
| VPN | Not implemented (cost saving) |
| Connectivity | Public Internet (HTTPS) |
| Azure Network | Single VNet |
| Segmentation | One shared subnet (Phase 1) |

---

## 4. Backup & DR

| Area | Decision |
|------|----------|
| Backup Type | Full Volume Snapshots |
| Backup Target | Azure Blob Storage |
| Encryption | Default encryption at rest |
| DR Strategy | Restore to temporary Azure VM |

---

## 5. Monitoring & Security

| Area | Decision |
|------|----------|
| Logging | Log Analytics Workspace |
| SIEM | Microsoft Sentinel (Future) |
| Data Sensitivity | High (customer media & CRM data) |
| Future Hardening | Private Endpoints, Immutable Blob |

---

## 6. Governance

| Area | Decision |
|------|----------|
| Subscription Model | Single subscription |
| Future Plan | Separate Dev/Prod subscriptions |
| Policy Strategy | To be defined in later phase |
| Tagging | Will follow CAF best practices |

---

## Architectural Philosophy

This landing zone is designed as:

- Lightweight
- Cost-optimized
- Learning-focused
- Expandable for future enterprise hardening
