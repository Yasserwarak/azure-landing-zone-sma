# Subscription Foundation

## Overview

After implementing the identity architecture, the next step in the Azure Landing Zone deployment is defining the **subscription structure**.

The Azure subscription acts as the **primary billing, governance, and access boundary** for Azure resources.

All Azure resources within the landing zone are deployed inside this subscription.

For the purposes of this landing zone architecture, a **single subscription model** was selected.

This decision aligns with the architectural goals of the fictional organization:

- simplicity
- cost efficiency
- low operational complexity
- small team size

---

# Organization Context

The fictional organization is a **20-person social media agency based in Germany**.

The company operates a hybrid environment consisting of:

- On-prem NAS infrastructure
- Azure resources for applications and backup
- Cloud-hosted web services
- Monitoring and analytics services

Because the organization is relatively small and currently operates a limited number of workloads, a **single Azure subscription** provides sufficient governance and operational control.

---

# Subscription Model

The landing zone currently uses **one Azure subscription**.

The subscription contains all resources required for the environment, including:

- networking
- storage
- applications
- monitoring
- backup services

This approach is commonly referred to as a **Start-Small Landing Zone model**.

---

# Reasons for Choosing a Single Subscription

Several factors influenced the decision to start with a single subscription.

### Organizational Size

The organization currently has only **20 internal users**, which does not require complex multi-subscription governance.

### Operational Simplicity

Managing a single subscription reduces operational overhead and simplifies administration.

### Cost Management

A single subscription makes it easier to monitor spending and enforce budget controls.

### Learning Environment

Because this landing zone is also designed as a **learning and experimentation environment**, a simplified structure is appropriate.

---

# Subscription Governance Boundary

The Azure subscription serves several important governance roles.

### Billing Boundary

All Azure resource consumption is billed through the subscription.

Cost monitoring and budgeting are applied at this level.

### Access Control Boundary

RBAC roles are assigned at the subscription scope for administrative roles such as:

- Cloud Administrators
- Read-Only Users

These permissions cascade down to resources within the subscription.

### Resource Containment

All resource groups and resources are contained within the subscription.

---

# Relationship to Microsoft Entra ID

The subscription is connected to the organization's **Microsoft Entra ID tenant**.

Microsoft Entra ID provides:

- authentication
- identity governance
- role-based access control

User identities and security groups defined earlier are used to assign permissions to the subscription.

This integration ensures centralized identity and access management.

---

# Current Subscription Access Model

Subscription access is controlled using **Azure Role-Based Access Control (RBAC)**.

Initial role assignments include:

| Security Group | Role | Scope |
|----------------|------|-------|
| SG-LZ-CloudAdmins | Contributor | Subscription |
| SG-LZ-Readers | Reader | Subscription |

These assignments ensure that:

- platform administrators can manage infrastructure
- observers can view resources without modifying them

---

# Future Subscription Evolution

Although the current architecture uses a single subscription, the design allows future expansion.

If the organization grows, the environment can evolve into a **multi-subscription architecture**.

Possible future subscriptions include:

- Production
- Development
- Security
- Shared Services

This approach aligns with the **Azure Enterprise Landing Zone model** used by larger organizations.

---

# Alignment with Cloud Adoption Framework

The subscription structure aligns with the **Microsoft Cloud Adoption Framework (CAF)** guidance for small and medium organizations.

CAF recommends starting with a simplified architecture and expanding governance structures as the environment grows.

The landing zone therefore follows the principle:

"Start simple, design for scale."

---

# Implementation Outcome

After completing the subscription foundation phase:

- an Azure subscription acts as the primary governance boundary
- identity access is controlled through Microsoft Entra ID
- RBAC roles are applied at the subscription scope
- the environment is prepared for resource organization

---

# Next Phase

The next step in the landing zone implementation is **Resource Organization**.

This phase defines:

- resource group structure
- naming conventions
- tagging standards
- governance policies

These elements determine how resources are structured within the subscription.

This will be documented in:

02-resource-groups.md
