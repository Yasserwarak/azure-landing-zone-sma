# Identity – Security Groups

## Overview

After provisioning user identities, the next step in the identity implementation is the creation of **security groups** in Microsoft Entra ID.

Security groups are used to implement **group-based access control** within the Azure Landing Zone.

Instead of assigning permissions directly to individual users, permissions are assigned to security groups.  
Users are then added to groups based on their responsibilities within the organization.

This model follows Microsoft best practices and provides:

- simplified permission management
- scalable access control
- improved auditing and governance
- alignment with the Microsoft Cloud Adoption Framework

---

# Access Control Architecture

The landing zone uses a layered access control model.

Access flows through the following structure:

User  
↓  
Security Group  
↓  
Azure RBAC Role  
↓  
Resource Scope

Security groups therefore act as the **bridge between identities and Azure permissions**.

---

# Security Groups Implemented

The following Microsoft Entra ID security groups were created to represent operational roles within the organization.

| Security Group | Purpose |
|---|---|
| SG-LZ-CloudAdmins | Azure platform administrators |
| SG-LZ-SecurityAdmins | Security governance administrators |
| SG-LZ-AppAdmins | Application administrators |
| SG-LZ-BackupOperators | Backup and storage operators |
| SG-LZ-MonitoringReaders | Monitoring and observability access |
| SG-LZ-Readers | Read-only access to Azure resources |

These groups represent the operational roles required to manage the landing zone.

---

# Cloud Administrators

Group:

SG-LZ-CloudAdmins

Members of this group are responsible for managing the Azure platform infrastructure.

Typical responsibilities include:

- deploying Azure resources
- managing networking
- configuring storage
- managing resource groups
- maintaining platform configuration

This group represents the **core cloud operations team**.

---

# Security Administrators

Group:

SG-LZ-SecurityAdmins

Members of this group oversee identity governance and platform security.

Responsibilities include:

- reviewing access permissions
- monitoring identity-related security alerts
- implementing security policies
- supporting compliance activities

This group helps maintain the overall security posture of the environment.

---

# Application Administrators

Group:

SG-LZ-AppAdmins

Members of this group manage application-level resources.

Typical responsibilities include:

- deploying web applications
- managing static web apps
- configuring application settings
- supporting application updates

This group allows application management without granting full platform administration privileges.

---

# Backup Operators

Group:

SG-LZ-BackupOperators

Members of this group manage backup-related operations.

Responsibilities include:

- managing backup storage accounts
- verifying backup integrity
- restoring data during recovery scenarios
- monitoring backup jobs

This role is particularly relevant for the organization's **NAS-to-Azure backup architecture**.

---

# Monitoring Readers

Group:

SG-LZ-MonitoringReaders

Members of this group can view monitoring data without modifying resources.

They can access:

- Azure Monitor
- Log Analytics
- monitoring dashboards
- alerts and metrics

This role supports operational visibility without granting administrative permissions.

---

# Read-Only Access

Group:

SG-LZ-Readers

This group provides read-only access to the Azure environment.

Typical users include:

- executives
- auditors
- external reviewers
- stakeholders who require visibility but not modification privileges

Members can inspect resources but cannot make changes.

---

# External Partner Access

External users, such as the IT partner **Hiba Almsouti**, may be added to appropriate security groups when required.

Guest users are managed through **Microsoft Entra B2B collaboration** and are granted only the minimum permissions required to perform their tasks.

This ensures secure collaboration while maintaining strict access control.

---

# Benefits of Group-Based Access Control

Using security groups provides several operational advantages.

## Scalability

Permissions are managed at the group level rather than per user.

## Security

Users only receive permissions associated with their role.

## Simplified Management

New employees can be onboarded by simply adding them to the appropriate group.

## Auditing

Access reviews focus on group membership rather than individual permissions.

---

# Alignment with Landing Zone Architecture

Security groups form the **core access control layer** of the landing zone identity architecture.

They allow Azure roles to be assigned at the correct scope while maintaining clear separation of duties.

These groups will be mapped to **Azure RBAC roles** in the next implementation phase.

---

# Implementation Outcome

After completing this phase:

- security groups are defined
- organizational roles are represented in Entra ID
- identities can be grouped based on responsibilities
- the environment is prepared for RBAC role assignment

---

# Next Phase

The next step in the identity implementation is **Azure Role-Based Access Control (RBAC)**.

RBAC roles will be assigned to the security groups created in this phase to control access to Azure resources.

This will be documented in:

04-identity-rbac.md
