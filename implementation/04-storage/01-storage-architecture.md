# Storage Architecture

## Overview

The storage architecture of the landing zone supports **hybrid data storage and backup for the organization's CRM system**.

The company operates an **EspoCRM system hosted on a Ugreen NAS device on-premises**.

The CRM application and its MySQL database remain on-premises, while Azure is used as a **secure off-site backup target**.

This architecture provides:

- reliable off-site backup storage
- disaster recovery capability
- protection against local hardware failure
- scalable long-term storage

---

# Primary Data Location

The **primary operational data** for the organization is stored on the on-premises NAS system.

### On-Prem Infrastructure

The company uses:

**Ugreen NASync DXP4800 Plus**

Key characteristics:

| Component | Description |
|---|---|
| System | Ugreen NASync DXP4800 Plus |
| CPU | Intel Pentium Gold 8505 |
| RAM | 16GB DDR5 |
| Storage | HDD RAID1 + SSD storage |
| OS | UGOS Pro |
| Workload | EspoCRM (Docker container) |
| Database | MySQL running on SSD |

The NAS hosts the following services:

- EspoCRM application
- MySQL database
- internal file storage
- snapshot backups

---

# CRM Application Architecture

The CRM system runs entirely on the NAS.

Architecture:

EspoCRM (Docker container)  
↓  
MySQL Database  
↓  
Stored on NAS SSD storage

The CRM stores important business data including:

- customer records
- communication history
- sales information
- media attachments
- operational data

Because this data is critical for business operations, reliable backup storage is required.

---

# Backup Strategy

The landing zone uses a **hybrid backup architecture**.

The NAS periodically creates **full volume snapshots or database exports**, which are then transferred to Azure.

Backup flow:

On-Prem NAS  
↓  
Snapshot / Database Export  
↓  
Secure HTTPS Transfer  
↓  
Azure Blob Storage

This ensures that a copy of the CRM data is always available outside the local infrastructure.

---

# Azure Storage Role

Azure Storage is used as an **off-site backup repository**.

The landing zone uses:

**Azure Storage Account with Blob Storage**

The storage account is deployed in:

```
RG-Backup
```

This resource group contains backup-related resources only.

Separating backups from application resources improves governance and security.

---

# Blob Container Design

Backup data is organized using Blob Storage containers.

Example container structure:

| Container | Purpose |
|---|---|
| nas-backups | Full NAS snapshots |
| crm-database-backups | MySQL database exports |
| archive | Long-term archived backups |

This separation improves:

- backup management
- restore procedures
- lifecycle policies

---

# Backup Data Types

The backup architecture supports multiple types of data.

### NAS Snapshots

Full NAS snapshots provide recovery for:

- application files
- configuration files
- media assets
- file storage

### Database Backups

MySQL database dumps provide recovery for:

- CRM customer records
- CRM operational data
- CRM system configuration

These backups ensure the CRM system can be reconstructed even if the NAS fails.

---

# Disaster Recovery Scenario

If the on-prem NAS becomes unavailable, the backup data stored in Azure can be used to restore the CRM system.

Example recovery workflow:

Azure Blob Storage  
↓  
Download backup data  
↓  
Deploy temporary Azure VM  
↓  
Install MySQL + EspoCRM  
↓  
Restore database and application files

This process enables temporary cloud-based operation until on-prem infrastructure is restored.

---

# Data Durability

Azure Blob Storage provides extremely high durability.

Backup data is protected through:

- redundant storage infrastructure
- distributed replication
- automated integrity checks

This ensures that backup data remains available even during hardware failures.

---

# Encryption

All data stored in Azure Storage is protected by **encryption at rest**.

Azure automatically encrypts data using Microsoft-managed keys.

This protects CRM backup data from unauthorized access at the storage layer.

Future enhancements may include:

- customer-managed encryption keys
- Azure Key Vault integration

---

# Access Control

Access to the backup storage account is controlled through **Azure RBAC**.

The following access model is used:

| Security Group | Role |
|---|---|
| SG-LZ-BackupOperators | Storage Blob Data Contributor |
| SG-LZ-CloudAdmins | Contributor |
| SG-LZ-Readers | Reader |

This ensures that only authorized users can upload, download, or restore backup files.

---

# Storage Lifecycle Management

To reduce storage costs, lifecycle policies can automatically move older backups to cheaper storage tiers.

Example lifecycle policy:

| Age | Storage Tier |
|---|---|
| 0–30 days | Hot |
| 30–90 days | Cool |
| 90+ days | Archive |

This helps optimize long-term storage costs.

---

# Security Considerations

The storage architecture follows several security principles:

- RBAC-based access control
- encryption at rest
- separation of backup storage from application resources
- limited access for external users

Future improvements may include:

- private endpoints for storage
- immutable blob storage (WORM)
- Microsoft Defender for Storage

---

# Alignment with Landing Zone Architecture

The storage architecture supports the hybrid design of the landing zone.

Key characteristics include:

- CRM system hosted on-prem
- Azure used as backup target
- secure backup transfer via HTTPS
- scalable cloud storage for long-term retention

This approach balances **cost efficiency, operational simplicity, and disaster recovery capability**.

---

# Implementation Outcome

After completing the storage phase:

- CRM data remains operational on-prem
- backup copies are securely stored in Azure
- the organization has off-site backup protection
- the environment supports disaster recovery restoration

---

# Next Phase

The next step in the landing zone implementation is **Compute and Application Deployment**.

This phase includes:

- Azure App Service deployment
- Content Tracker application
- temporary compute resources for disaster recovery

This will be documented in:

05-compute-applications.md
