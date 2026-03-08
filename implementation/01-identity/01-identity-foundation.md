# Identity Foundation

## Overview

Identity is the core security boundary of the Azure Landing Zone.  
All authentication and authorization across the environment are handled through **Microsoft Entra ID**.

The landing zone uses **Microsoft Entra ID as the central identity provider** for:

- Azure platform administration  
- Application authentication  
- Access to Azure resources  
- Monitoring and operational services  

This identity-first approach ensures that **every action in the environment is traceable to an authenticated identity**.

---

# Identity Architecture Model

The landing zone follows a **cloud-only identity architecture**.

This means:

- No on-premises Active Directory
- No domain controllers
- No Azure AD Connect
- No hybrid identity synchronization

All identities exist directly inside **Microsoft Entra ID**.

This design was chosen because the fictional company:

- has **20 employees**
- operates from **a single office**
- has **no legacy infrastructure**
- wants **low operational complexity**

---

# Identity Platform

The identity platform is based on:

**Microsoft Entra ID (Azure Active Directory)**

The tenant acts as the **central authority for authentication and authorization**.

The Entra ID tenant provides identity services for:

| Platform Component | Identity Usage |
|---|---|
| Azure Subscription | Administrative access |
| Resource Groups | Resource management permissions |
| Azure Storage | Backup access |
| Web Applications | Application authentication |
| Monitoring | Log access |
| Future automation | DevOps identities |

---

# Licensing Model

The tenant uses **Microsoft Entra ID Plan 2 (P2)**.

This license tier enables advanced identity security and governance features.

Key capabilities available include:

- Privileged Identity Management (PIM)
- Conditional Access
- Access Reviews
- Identity Protection
- Risk-based sign-in detection

Although not all capabilities are immediately configured, the architecture is designed to **support these controls in later security hardening phases**.

---

# Identity Design Principles

The identity architecture follows several core principles based on **Microsoft Cloud Adoption Framework (CAF)** recommendations.

## 1. Cloud-First Identity

Identity services are provided directly by Microsoft Entra ID without dependency on local infrastructure.

---

## 2. Centralized Identity Control

All authentication decisions originate from the Entra ID tenant.

This ensures:

- consistent authentication policies  
- centralized identity governance  
- simplified security monitoring

---

## 3. Least Privilege

Users receive **only the permissions required to perform their roles**.

Administrative privileges are minimized wherever possible.

---

## 4. Group-Based Access Control

Permissions are assigned to **security groups rather than individual users**.

Access therefore follows this structure:

User  
↓  
Security Group  
↓  
Azure RBAC Role  
↓  
Resource Scope  

This approach improves:

- scalability
- auditing
- operational simplicity

---

## 5. Separation of Duties

Administrative responsibilities are distributed across multiple roles.

This reduces the risk of excessive privilege concentration.

Examples include:

- cloud platform administration  
- application administration  
- backup operations  
- monitoring access

---

## 6. Expandable Governance

The identity architecture is designed to support future governance features such as:

- privileged access elevation
- automated access reviews
- identity risk monitoring
- conditional access policies

---

# Tenant Preparation

Before implementing identity access control, the following baseline configuration tasks were performed:

1. Verified the Microsoft Entra tenant configuration  
2. Confirmed Entra ID P2 licensing availability  
3. Established initial administrative identities  
4. Prepared the directory for user provisioning  
5. Defined the identity architecture principles  

These steps ensure the tenant is prepared to support **secure identity management and RBAC implementation**.

---

# Security Considerations

Identity security is critical to the overall landing zone architecture.

The identity system is designed to support:

- multi-factor authentication enforcement  
- identity monitoring  
- privileged access auditing  
- secure administrative operations  

Advanced controls will be introduced gradually as the landing zone evolves.

---

# Alignment with Microsoft Cloud Adoption Framework

The identity design aligns with the **Identity Design Area** of the Microsoft Cloud Adoption Framework.

CAF recommends:

- centralized identity management  
- group-based RBAC  
- minimal privileged access  
- governance-ready identity architecture  

The implemented identity foundation follows these principles.

---

# Implementation Outcome

After completing the identity foundation phase:

- Microsoft Entra ID is established as the **central identity provider**
- The identity platform supports **cloud-only authentication**
- Entra ID P2 licensing enables **advanced governance capabilities**
- The environment is prepared for **user provisioning and access control implementation**

---

# Next Phase

The next step in the identity implementation is:

**User Provisioning**

This includes:

- creating executive identities  
- creating employee accounts  
- bulk provisioning users via CSV  

This will be documented in: 02-identity-users
