# Resource Group Architecture

## Overview

After defining the subscription structure, the next step in the Azure Landing Zone implementation is organizing resources using **Azure Resource Groups**.

Resource Groups provide a logical container for Azure resources and allow administrators to manage:

- deployment scope
- access control
- lifecycle management
- resource organization

Resource groups help structure the Azure environment in a way that is clear, manageable, and aligned with operational responsibilities.

---

# Resource Group Strategy

The landing zone uses **function-based resource grouping**.

Resources are grouped according to their operational purpose rather than by application.

This approach simplifies:

- administration
- RBAC assignment
- monitoring
- governance

Each resource group represents a **functional component of the platform**.

---

# Resource Groups Implemented

The following resource groups were created as part of the landing zone deployment.

| Resource Group | Purpose |
|---|---|
| RG-Network | Networking infrastructure |
| RG-Apps | Application workloads |
| RG-Backup | Backup storage and recovery resources |
| RG-Monitoring | Logging, monitoring, and observability |
| RG-Compute | Virtual machines used for recovery scenarios |

---

# RG-Network

## Purpose

The **RG-Network** resource group contains networking components used by the landing zone.

Typical resources include:

- Virtual Network (VNet)
- Subnets
- Network Security Groups
- Private endpoints (future phase)

Networking resources are centralized in this resource group to simplify management and security configuration.

---

# RG-Apps

## Purpose

The **RG-Apps** resource group hosts application workloads deployed in Azure.

This includes:

- web applications
- static web apps
- application services
- supporting application components

Application administrators manage resources in this group.

---

# RG-Backup

## Purpose

The **RG-Backup** resource group stores backup-related resources.

This is particularly important for the organization's **NAS-to-Azure backup architecture**.

Typical resources include:

- Azure Storage Accounts
- Blob containers used for backup storage

Backups from the on-premises NAS are uploaded to this storage.

This resource group ensures backup resources are logically separated from application resources.

---

# RG-Monitoring

## Purpose

The **RG-Monitoring** resource group contains monitoring and logging components.

Typical resources include:

- Log Analytics Workspace
- Azure Monitor components
- Alert rules
- monitoring dashboards

Centralizing monitoring resources simplifies visibility and troubleshooting across the environment.

---

# RG-Compute

## Purpose

The **RG-Compute** resource group contains compute resources.

For this landing zone, compute resources are primarily used for:

- temporary virtual machines
- disaster recovery restore scenarios
- administrative troubleshooting environments

In the event that backups must be restored, a temporary Azure VM can be deployed in this resource group.

---

# Benefits of Resource Group Organization

Organizing resources using functional resource groups provides several advantages.

## Operational Clarity

Administrators can easily identify where specific resources belong.

## RBAC Scope Control

RBAC roles can be assigned at the resource group level for specific teams.

For example:

- Application administrators → RG-Apps
- Monitoring readers → RG-Monitoring

## Lifecycle Management

Entire resource groups can be managed or removed together if necessary.

## Governance

Resource groups provide a clear structure for applying:

- policies
- monitoring
- security controls

---

# Alignment with Landing Zone Architecture

The resource group structure aligns with the landing zone design principles:

- modular architecture
- separation of responsibilities
- simplified governance

Each resource group represents a logical layer of the platform.

This modular structure also allows future expansion of the environment.

---

# Implementation Outcome

After completing the resource organization phase:

- resource groups are defined
- infrastructure components are logically separated
- RBAC can be applied at appropriate scopes
- monitoring and backup resources are isolated

The environment is now prepared for **network deployment and core infrastructure services**.

---

# Next Phase

The next step in the landing zone implementation is **Networking Architecture**.

This phase includes:

- Virtual Network deployment
- subnet configuration
- network security groups
- connectivity design

This will be documented in:

03-networking.md
