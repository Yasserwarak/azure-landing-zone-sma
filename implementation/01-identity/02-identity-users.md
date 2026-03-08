# Identity – User Provisioning

## Overview

After establishing the identity foundation of the Azure Landing Zone, the next step is **user provisioning** in Microsoft Entra ID.

User provisioning establishes the organizational identity structure used to manage access to Azure resources and applications.

The fictional organization used in this landing zone represents a **20-person social media agency located in Germany**, with one additional **external IT partner**.

User provisioning enables:

- administrative access to Azure
- role-based access control (RBAC)
- application authentication
- monitoring and operational access
- collaboration with external partners

---

# Organizational Identity Structure

The identity structure implemented for this landing zone consists of:

| Category | Count |
|---|---|
| Executive Leadership | 2 |
| Employees | 18 |
| External IT Partner | 1 |
| Total Identities | 21 |

This distribution reflects a realistic organizational model for a small digital agency.

Departments represented include:

- Marketing
- Media Production
- Design
- IT
- Analytics
- Finance
- Sales
- Operations
- HR

These identities will later be mapped to **security groups and RBAC roles**.

---

# Executive Accounts

Two executive identities were created manually during the initial tenant setup.

| Name | Role | Responsibility |
|---|---|---|
| Yasser Warak | CEO | Organizational leadership and platform oversight |
| Amer Warak | CFO | Financial governance and operational oversight |

Both accounts were initially assigned the **Global Administrator** role to allow tenant configuration and identity setup.

Typical responsibilities of these accounts include:

- tenant administration
- user and group management
- platform governance
- RBAC role assignment

In mature environments, these privileges are normally controlled using **Privileged Identity Management (PIM)** to reduce standing administrative privileges.

---

# Employee Account Provisioning

To simulate a realistic workforce, **18 employee accounts** were created.

Instead of creating each account manually, the **Bulk User Creation feature** in Microsoft Entra ID was used.

Bulk provisioning improves:

- efficiency when creating many users
- identity consistency
- operational scalability

---

# Bulk User Creation Process

The following process was used to create the employee identities.

### Step 1 – Navigate to Bulk User Creation

Open the Microsoft Entra Admin Center.

Navigate to:

Microsoft Entra ID  
→ Users  
→ Bulk operations  
→ Bulk create

---

### Step 2 – Download CSV Template

The official Microsoft Entra CSV template was downloaded from the portal.

The template includes a required version header:

version:v1.0

This row must remain unchanged.

---

### Step 3 – Populate User Data

The template was populated with employee information including:

- UserPrincipalName
- DisplayName
- MailNickname
- Password
- AccountEnabled

Each row represents a new employee identity.

User accounts follow a standardized naming convention:

firstname.lastname@tenantdomain

This improves directory readability and administrative consistency.

---

### Step 4 – Upload CSV File

The populated CSV file was uploaded through the Bulk Create interface.

The system performs validation checks including:

- correct column formatting
- valid user principal names
- correct template structure

---

### Step 5 – Execute Bulk Provisioning

After validation succeeded, the bulk user creation operation was executed.

Microsoft Entra ID automatically created the **18 employee accounts**.

---

# External Partner Account

An additional **guest account** was created for an external IT partner.

| Name | Account Type | Role |
|---|---|---|
| Hiba Almsouti | Guest User (B2B) | External IT Partner |

This account represents an external partner assisting with cloud infrastructure and IT support.

The user was added using **Microsoft Entra External Collaboration (B2B)**.

External collaboration enables organizations to securely grant limited access to partners without creating full internal identities.

Typical partner scenarios include:

- IT consulting
- infrastructure management
- security auditing
- application support

Guest users can later be granted access through **security groups and RBAC roles**, similar to internal users.

---

# Resulting Directory

After completing the provisioning process, the Microsoft Entra directory contains **21 identities**.

| Identity Type | Count |
|---|---|
| CEO | 1 |
| CFO | 1 |
| Employees | 18 |
| External Partner | 1 |

This directory structure represents the workforce and external collaboration model of the fictional organization.

---

# Identity Management Considerations

## Standardized Naming

User accounts follow a consistent naming convention:

firstname.lastname@tenantdomain

This ensures:

- clear identity management
- easier auditing
- improved administrative readability

---

## External Collaboration

External users are managed through **Microsoft Entra B2B collaboration**.

This allows organizations to:

- invite partner identities
- restrict access to specific resources
- audit external user activity

Guest users receive **minimal permissions** required for their tasks.

---

## Expandable Directory Model

The identity structure is designed to scale with organizational growth.

If the company expands beyond the initial 20 users, additional employees can be added through the same provisioning process.

---

# Alignment with Landing Zone Architecture

User provisioning prepares the identity platform for the next stage of the landing zone implementation.

Access will follow the architecture model:

User  
↓  
Security Group  
↓  
Azure RBAC Role  
↓  
Resource Scope

This layered model ensures secure and scalable access control across the Azure environment.

---

# Implementation Outcome

After completing this phase:

- executive identities are established
- employee identities are provisioned
- external collaboration is enabled
- the Entra ID directory reflects the full organizational structure
- The environment is ready for group-based access control

---

# Next Phase

The next step in the identity implementation is **Security Group Architecture**.

Security groups will represent operational roles within the organization and will be mapped to Azure RBAC roles.

This will be documented in:

03-identity-security-groups.md
