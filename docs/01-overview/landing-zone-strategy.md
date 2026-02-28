# Landing Zone Strategy & Scale Decision

## 1. Objective

This document explains why a **Small-Scale Azure Landing Zone** was chosen instead of an Enterprise-Scale or Platform Landing Zone model.

The goal of this project is:

- AZ-104 preparation
- Hybrid architecture learning
- Cost-aware implementation
- Structured but lightweight design

---

## 2. Available Landing Zone Models

### Enterprise-Scale Landing Zone

Characteristics:
- Management Group hierarchy
- Multiple subscriptions (Platform / Connectivity / Identity / Apps)
- Hub-Spoke network topology
- Centralized security & governance
- Dedicated platform engineering team
- Enterprise-grade policies and blueprints

Best suited for:
- Large enterprises
- Regulated industries
- Multi-business-unit organizations

---

### Platform Landing Zone

Characteristics:
- Shared services subscription
- Centralized networking
- Platform team managing core infrastructure
- Application teams deploying workloads separately

Best suited for:
- Medium-to-large companies
- Organizations with multiple app teams

---

### Start-Small / Application-Focused Landing Zone

Characteristics:
- Single subscription
- Simple Virtual Network
- Minimal but structured governance
- Direct workload deployment
- Cost-optimized
- Expandable design

Best suited for:
- Small companies
- Early cloud adoption
- Learning environments
- Budget-constrained scenarios

---

## 3. Why Start-Small Was Selected

The fictional company has:

- 20 employees
- Single office location (Düsseldorf)
- Limited initial cloud budget (~$170/month)
- No dedicated cloud platform team
- One primary workload (CRM + Web App)
- On-prem NAS with backup integration

Implementing an Enterprise-Scale model would introduce:

- Unnecessary complexity
- Higher operational overhead
- Increased cost
- Governance structures not yet required

Therefore, a **Start-Small Landing Zone** was intentionally selected.

---

## 4. Architectural Philosophy

The design follows this principle:

> "Start simple, design for growth."

The architecture:

- Uses a single subscription
- Implements one VNet
- Applies RBAC via Entra ID
- Introduces monitoring via Log Analytics
- Enables backup to Azure Blob Storage
- Supports temporary DR restore via Azure VM

The structure allows future transition to:

- Multi-subscription model
- Hub-Spoke networking
- Centralized governance
- Platform landing zone model

---

## 5. Future Evolution Path

Phase 2 (Growth):
- Separate Dev and Prod subscriptions
- Introduce tagging & policy enforcement
- Add Microsoft Sentinel

Phase 3 (Enterprise Hardening):
- Implement Management Groups
- Deploy Hub-Spoke topology
- Add Site-to-Site VPN
- Introduce Private Endpoints
- Centralize security operations

---

## Conclusion

The selected landing zone model aligns with:

- Company size
- Budget constraints
- Learning objectives
- Practical hybrid workload requirements

The architecture is intentionally lightweight but designed to scale toward enterprise patterns when needed.
