# Network Architecture

## Overview

After defining the subscription structure and resource group organization, the next step in the Azure Landing Zone implementation is the **network architecture**.

Networking provides the communication foundation for Azure resources and defines how workloads connect securely within the cloud environment.

For this landing zone, a **simple and cost-optimized network model** was selected.

This aligns with the architectural goals of the fictional organization:

- small company size
- limited budget
- learning-focused environment
- low operational complexity
- future scalability

---

# Network Design Strategy

The landing zone uses a **single Virtual Network (VNet)** as the primary network boundary.

This design was intentionally selected because the organization:

- has only one primary Azure environment
- does not yet require complex segmentation
- does not operate multiple Azure subscriptions
- does not currently need hub-spoke networking

The network model follows the principle:

**Start simple, design for future expansion.**

---

# Core Network Decisions

The following architectural decisions were made for the network design.

| Area | Decision |
|---|---|
| Azure Network Model | Single VNet |
| Initial Segmentation | One shared subnet |
| VPN Connectivity | Not implemented in phase 1 |
| On-Prem to Azure Communication | Public internet over HTTPS |
| Security Baseline | Network Security Group (NSG) |
| Future Expansion | Private Endpoints, VPN, subnet segmentation |

---

# Virtual Network (VNet)

## Purpose

The **Virtual Network (VNet)** provides the private network boundary for Azure resources deployed in the landing zone.

The VNet enables Azure resources to communicate securely with each other and forms the foundation for:

- application hosting
- compute deployment
- future private connectivity
- future segmentation

In this landing zone, a single VNet is sufficient for the initial architecture.

---

# Initial Subnet Design

## Purpose

Within the VNet, the landing zone initially uses **one shared subnet**.

This subnet hosts the first cloud resources that require network placement, such as:

- virtual machines
- future private application components
- future private endpoints

The use of a single subnet in phase 1 reduces operational complexity and supports the learning-focused nature of the environment.

---

# Why a Single Subnet Was Chosen

A more advanced enterprise architecture would normally separate workloads into multiple subnets, for example:

- application subnet
- management subnet
- private endpoint subnet
- security subnet

However, this landing zone intentionally starts with **one shared subnet** because:

- the organization is small
- the workload count is low
- no production-grade segmentation is yet required
- simplicity is prioritized in the initial phase

This decision reduces deployment complexity while preserving the option to introduce subnet segmentation later.

---

# On-Premises Connectivity Model

The organization operates a **Ugreen NAS on-premises** which stores EspoCRM and backup data.

At the current stage, the architecture does **not** include a Site-to-Site VPN.

Instead, the NAS communicates with Azure services using:

- public internet connectivity
- HTTPS-based secure transfer

This model was chosen because it is:

- cost-efficient
- easy to implement
- sufficient for the current workload
- appropriate for a trial and learning environment

---

# Backup Traffic Flow

The most important hybrid communication path in the environment is the backup flow from the on-premises NAS to Azure Blob Storage.

The flow is:

On-Prem Ugreen NAS  
↓  
Backup job / snapshot export  
↓  
Public internet over HTTPS  
↓  
Azure Blob Storage

This design allows the organization to maintain off-site backups in Azure without deploying dedicated private connectivity in the initial phase.

---

# Network Security Group (NSG)

## Purpose

A **Network Security Group (NSG)** is used to provide the baseline network security control for the landing zone.

The NSG filters traffic to and from resources deployed in the subnet.

It helps control:

- inbound traffic
- outbound traffic
- administrative access
- service exposure

Even in a simple architecture, NSGs provide an important baseline protection mechanism.

---

# NSG Design Principles

The landing zone applies the following NSG principles:

- deny unnecessary inbound traffic
- allow only required management access
- restrict exposure of compute resources
- keep the initial rule set simple and understandable

This helps ensure that cloud resources are not exposed more broadly than required.

---

# No VPN in Phase 1

The architecture intentionally does **not** implement VPN connectivity in the first phase.

Reasons include:

- budget limitations
- reduced complexity
- limited hybrid traffic requirements
- backup workload can operate over HTTPS

This decision supports the overall **Start-Small Landing Zone** model.

---

# Future Network Evolution

Although the initial network design is simple, the architecture is designed to support future expansion.

Possible future improvements include:

- Site-to-Site VPN
- subnet segmentation
- private endpoints for storage
- hub-spoke topology
- Azure Firewall
- network peering

These enhancements can be introduced if the organization grows or if security requirements become more demanding.

---

# Alignment with Landing Zone Architecture

The networking model aligns with the overall landing zone strategy:

- lightweight
- cost-optimized
- practical
- scalable

The design is intentionally minimal in the beginning, while still providing a structured network foundation for future platform growth.

---

# Implementation Outcome

After completing the networking phase:

- the Azure environment has a defined private network boundary
- one initial subnet supports early cloud resources
- NSG-based baseline protection is established
- on-prem backup connectivity to Azure is supported over HTTPS
- the architecture is prepared for future private connectivity enhancements

---

# Next Phase

The next step in the landing zone implementation is **Storage Architecture**.

This phase includes:

- Azure Storage Account design
- Blob container structure
- backup retention considerations
- access control for backup operations

This will be documented in:

04-storage.md
