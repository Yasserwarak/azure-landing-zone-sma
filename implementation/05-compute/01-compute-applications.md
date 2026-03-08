# Compute and Application Architecture

## Overview

After defining identity, subscription structure, networking, and storage, the next step in the Azure Landing Zone implementation is the **compute and application architecture**.

This phase defines how workloads are deployed and operated across the hybrid environment.

The landing zone uses a **hybrid workload model**:

- the primary CRM system remains on-premises
- cloud-hosted applications are deployed in Azure
- temporary recovery compute can be deployed in Azure when needed

This approach supports the organization's current operational needs while remaining cost-aware and scalable.

---

# Workload Placement Strategy

The landing zone uses a **split workload architecture**.

Different workloads are placed according to their operational requirements.

| Workload | Location | Purpose |
|---|---|---|
| EspoCRM | On-Prem NAS | Internal CRM system and customer data |
| MySQL Database | On-Prem NAS | Database for EspoCRM |
| Company Website | Azure | Public company website |
| Customer Management App | Azure | Customer portal and gamification platform |
| Disaster Recovery Restore VM | Azure | Temporary compute for recovery scenarios |

This model allows the organization to keep its existing CRM system on-premises while still benefiting from Azure-hosted services.

---

# On-Premises CRM Workload

The primary internal system of the organization is **EspoCRM**, which runs on the on-premises Ugreen NAS.

Architecture:

EspoCRM (Docker container)  
↓  
MySQL Database  
↓  
NAS SSD Storage

The CRM manages internal operational data such as:

- customer records
- service contracts
- communication history
- internal sales tracking
- business operations

Backups of the CRM system are stored in Azure Blob Storage as part of the hybrid backup architecture.

---

# Azure Hosted Applications

The landing zone hosts two primary cloud applications.

## Company Website

The organization hosts its **public company website** in Azure.

The website provides:

- company information
- service offerings
- marketing content
- contact and inquiry forms
- customer onboarding information

Hosting the website in Azure provides:

- global accessibility
- managed hosting
- simplified deployment
- scalability for future growth

---

## Customer Management Application

In addition to the public website, the organization provides a **customer-facing application**.

This application was **designed and developed internally by Yasser Warak and Amer Warak**.

The application functions as a **customer portal** that allows clients to manage their relationship with the agency.

Key capabilities of the application include:

- viewing active service contracts
- managing project details
- scheduling meetings
- reviewing pricing and service packages
- tracking project timelines
- managing deliverables
- accessing communication records

The application also includes **gamification elements** designed to increase user engagement.

Gamification features may include:

- progress tracking
- achievement milestones
- usage rewards
- engagement metrics

These elements improve the customer experience and encourage active interaction with the platform.

---

# Application Hosting Model

Both the **company website** and the **customer management application** are hosted using **Azure App Service**.

Azure App Service was selected because it provides:

- managed web hosting
- automatic scaling capabilities
- secure HTTPS endpoints
- integration with Microsoft Entra ID
- simplified deployment and management

Application resources are deployed in:

```
RG-Apps
```

This resource group contains all application workloads deployed in Azure.

---

# Identity Integration

The customer management application can integrate with **Microsoft Entra ID** for authentication and identity management.

Benefits include:

- centralized identity management
- secure login mechanisms
- support for role-based access
- alignment with the landing zone identity architecture

This ensures consistent identity governance across both internal and external users.

---

# Disaster Recovery Compute

The landing zone includes a **temporary Azure virtual machine** design for disaster recovery scenarios.

This VM is not intended for permanent operation.

Instead, it is used only when necessary, such as:

- restoring CRM backups from Azure Blob Storage
- testing disaster recovery procedures
- temporarily hosting services during NAS failure

The recovery VM is deployed in:

```
RG-Compute
```

---

# Disaster Recovery Restore Workflow

If the on-premises NAS becomes unavailable, Azure can temporarily host the CRM workload.

Example restore workflow:

Azure Blob Storage  
↓  
Deploy temporary Azure VM  
↓  
Install MySQL and EspoCRM  
↓  
Restore database backup  
↓  
Restore application files  
↓  
Resume temporary CRM operations

This allows the organization to maintain business continuity until the on-prem infrastructure is restored.

---

# Compute Design Principles

The compute architecture follows several principles.

## Hybrid Workload Placement

Existing systems remain on-prem while cloud-native workloads run in Azure.

## Managed Services First

Azure App Service is used instead of virtual machines whenever possible.

## Cost Efficiency

Virtual machines are deployed only when required for recovery scenarios.

## Scalable Cloud Layer

Web applications hosted in Azure can scale independently of on-prem systems.

---

# Resource Group Placement

The compute and application components are organized as follows:

| Resource Group | Workload Type |
|---|---|
| RG-Apps | Website and customer management application |
| RG-Compute | Temporary disaster recovery virtual machines |
| RG-Backup | Backup storage for CRM and NAS data |

---

# Benefits of the Compute Architecture

The selected compute model provides several benefits.

## Cloud Accessibility

Customers can access services through the web application hosted in Azure.

## Customer Self-Service

Clients can manage their services and interactions with the agency through the application.

## Scalability

Azure App Service allows the platform to scale as the customer base grows.

## Disaster Recovery

Azure compute resources allow the organization to restore operations during infrastructure failures.

---

# Alignment with Landing Zone Architecture

The compute architecture reflects the overall landing zone philosophy:

- hybrid infrastructure
- practical cloud adoption
- cost-aware architecture
- scalable cloud services

Azure is used strategically for:

- customer-facing applications
- website hosting
- backup storage
- disaster recovery compute

---

# Implementation Outcome

After completing the compute phase:

- the company website is hosted in Azure
- the customer portal application is deployed using Azure App Service
- customers can manage services and contracts through the platform
- the CRM system remains operational on-premises
- Azure provides recovery compute capabilities

---

# Next Phase

The next step in the landing zone implementation is **Monitoring and Logging**.

This phase will include:

- Azure Monitor
- Log Analytics Workspace
- diagnostic settings
- alert rules
- observability across the entire platform

This will be documented in:

06-monitoring.md
