# Identity – Azure Role-Based Access Control (RBAC)

## Overview

After defining the identity structure and creating security groups, the next step in the Azure Landing Zone implementation is **Azure Role-Based Access Control (RBAC)**.

RBAC defines **who can access Azure resources and what actions they are allowed to perform**.

RBAC assignments are applied to **security groups rather than individual users**, following the group-based access control model defined earlier.

This ensures:

- scalable permission management
- simplified onboarding
- consistent security governance
- alignment with Microsoft best practices

---

# RBAC Access Model

Access in the landing zone follows the structure:

User  
↓  
Security Group  
↓  
Azure RBAC Role  
↓  
Resource Scope

Users are added to **security groups**, and groups are assigned **RBAC roles** at the appropriate scope.

This approach prevents direct user-to-role assignments and improves long-term maintainability.

---

# RBAC Scope Hierarchy

Azure RBAC roles can be assigned at different scopes within the Azure hierarchy.

The hierarchy follows this structure:

Management Group  
↓  
Subscription  
↓  
Resource Group  
↓  
Resource

For this landing zone implementation, RBAC assignments are applied primarily at the following scopes:

- Subscription
- Resource Group
- Individual Resource (when required)

---

# Subscription-Level Role Assignments

The following RBAC roles were assigned at the **subscription level**.

| Security Group | Azure Role | Scope |
|---|---|---|
| SG-LZ-CloudAdmins | Contributor | Subscription |
| SG-LZ-Readers | Reader | Subscription |

### Cloud Administrators

Group:

SG-LZ-CloudAdmins

Role:

Contributor

Scope:

Subscription

Members of this group can:

- deploy Azure resources
- configure networking
- manage storage
- manage resource groups
- manage monitoring configuration

The **Contributor role** allows full management of Azure resources but **does not allow granting access to others**.

---

### Read-Only Users

Group:

SG-LZ-Readers

Role:

Reader

Scope:

Subscription

Members of this group can:

- view Azure resources
- inspect configurations
- review monitoring data

They **cannot modify resources**.

This role is useful for:

- executives
- auditors
- external observers

---

# Resource Group Level Role Assignments

Some permissions are applied at the **resource group level** rather than the entire subscription.

This ensures **least privilege access**.

---

## Application Administrators

Group:

SG-LZ-AppAdmins

Role:

Contributor

Scope:

RG-Apps

Members of this group can manage application resources including:

- web apps
- static web apps
- application configuration
- deployment settings

This allows application management without granting full platform administration privileges.

---

## Monitoring Access

Group:

SG-LZ-MonitoringReaders

Role:

Log Analytics Reader

Scope:

RG-Monitoring / Log Analytics Workspace

Members of this group can:

- view monitoring dashboards
- analyze logs
- review alerts
- access Log Analytics queries

They cannot modify monitoring configuration.

---

# Resource-Level Role Assignments

Certain permissions are applied directly at the **resource level**.

---

## Backup Storage Access

Group:

SG-LZ-BackupOperators

Role:

Storage Blob Data Contributor

Scope:

Backup Storage Account

Members of this group can:

- upload backup files
- download backup files
- manage backup containers
- restore backup data

This role supports the organization's **NAS-to-Azure Blob Storage backup architecture**.

---

# Security Administrator Access

Group:

SG-LZ-SecurityAdmins

Role assignments for this group will focus on security-related governance and monitoring.

Typical responsibilities include:

- reviewing RBAC assignments
- supporting identity governance
- reviewing security alerts
- assisting with security policy enforcement

This group may later receive additional roles related to:

- Microsoft Defender for Cloud
- Microsoft Sentinel
- security monitoring resources

---

# External Partner Access

External guest users, such as **Hiba Almsouti**, may receive permissions through security groups when required.

Guest accounts are never assigned roles directly.

Instead:

Guest User  
↓  
Security Group  
↓  
RBAC Role

This ensures consistent access governance for both internal and external identities.

---

# Least Privilege Strategy

The RBAC model follows the **principle of least privilege**.

Permissions are assigned based on the minimum access required for each role.

Examples include:

- application administrators receive access only to application resource groups
- monitoring users receive read-only monitoring access
- backup operators receive storage access only

This reduces the risk of accidental misconfiguration or unauthorized changes.

---

# RBAC Implementation Outcome

After completing this phase:

- security groups are mapped to Azure RBAC roles
- access control is centralized through Entra ID groups
- permissions follow least privilege principles
- operational roles are clearly separated

This RBAC model provides the foundation for secure resource management within the landing zone.

---

# Next Phase

The next step in the identity implementation is **Identity Governance**.

Identity governance includes:

- Privileged Identity Management (PIM)
- Conditional Access
- Access Reviews
- Identity security monitoring

This will be documented in:

05-identity-governance.md
