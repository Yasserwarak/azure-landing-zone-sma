# Identity – Governance and Security

## Overview

After establishing the identity foundation, provisioning users, defining security groups, and implementing Azure RBAC, the final phase of identity implementation is **identity governance and security controls**.

Identity governance ensures that privileged access to the Azure environment is:

- controlled
- monitored
- auditable
- protected against misuse

The landing zone uses **Microsoft Entra ID Plan 2 (P2)**, which enables advanced governance capabilities such as:

- Privileged Identity Management (PIM)
- Conditional Access
- Identity Protection
- Access Reviews

These capabilities improve the overall security posture of the environment.

---

# Identity Governance Objectives

The identity governance model is designed to achieve the following objectives:

- minimize standing privileged access
- enforce secure authentication policies
- monitor risky sign-in behavior
- regularly review user access
- protect administrative identities

These controls align with Microsoft security best practices and the Cloud Adoption Framework.

---

# Privileged Identity Management (PIM)

Privileged Identity Management (PIM) provides **just-in-time administrative access**.

Instead of permanently assigning high-privilege roles, administrators activate roles only when required.

This reduces the risk of:

- privilege abuse
- compromised administrator accounts
- accidental configuration changes

---

## PIM Design Principles

The landing zone follows these principles for privileged access:

- privileged roles should be **eligible rather than permanent**
- role activation should require justification
- privileged sessions should be time-limited
- administrative actions should be auditable

Typical roles that may be governed by PIM include:

- Global Administrator
- Privileged Role Administrator
- Azure Subscription Owner
- Security Administrator

---

# Conditional Access

Conditional Access policies provide **context-aware authentication controls**.

These policies enforce additional security requirements when users attempt to sign in.

Typical controls include:

- multi-factor authentication (MFA)
- device compliance requirements
- location-based access restrictions
- sign-in risk evaluation

Conditional Access is an essential component of a **Zero Trust security model**.

---

## Planned Conditional Access Policies

The landing zone is designed to support the following policies:

### Multi-Factor Authentication

All administrative accounts should require MFA when accessing Azure resources.

### Admin Access Protection

Privileged roles should require additional authentication controls.

### Risk-Based Access

Sign-ins identified as risky can trigger additional verification requirements.

These controls significantly reduce the likelihood of compromised credentials being used to access the environment.

---

# Identity Protection

Microsoft Entra ID P2 provides **Identity Protection capabilities**.

Identity Protection analyzes user behavior and sign-in patterns to detect potential security risks.

Examples include:

- impossible travel detection
- leaked credential detection
- unfamiliar sign-in properties
- suspicious IP addresses

When risks are detected, automated responses may include:

- requiring password reset
- blocking sign-in
- requiring MFA verification

This helps detect compromised accounts early.

---

# Access Reviews

Access Reviews allow organizations to **periodically review permissions and group memberships**.

Regular access reviews help ensure that users retain only the permissions necessary for their roles.

Typical review scenarios include:

- administrative group membership
- guest user access
- privileged RBAC roles
- security-sensitive permissions

Access reviews reduce the risk of **permission creep** over time.

---

# Break-Glass Emergency Accounts

To prevent administrative lockout scenarios, the environment should maintain **emergency break-glass accounts**.

Break-glass accounts are used only if:

- administrators lose access
- Conditional Access policies block administrators
- identity infrastructure becomes unavailable

Characteristics of break-glass accounts:

- extremely strong passwords
- excluded from Conditional Access policies
- monitored closely
- used only for emergency recovery

These accounts provide a last-resort recovery mechanism.

---

# External Collaboration Governance

External guest users are managed through **Microsoft Entra B2B collaboration**.

Guest accounts should follow strict governance rules:

- minimum required permissions
- access granted through security groups
- regular access review
- removal when collaboration ends

This ensures secure collaboration with external partners such as the IT partner **Hiba Almsouti**.

---

# Identity Security Best Practices

The landing zone identity governance model follows several security best practices.

### Least Privilege

Users receive only the permissions required to perform their tasks.

### Just-in-Time Access

Privileged roles should be activated temporarily when needed.

### Continuous Monitoring

Identity activity is monitored for suspicious behavior.

### Periodic Access Review

User access is reviewed regularly to ensure it remains appropriate.

These practices significantly reduce identity-related security risks.

---

# Implementation Outcome

After completing the identity governance phase:

- identity governance capabilities are enabled
- privileged access can be controlled using PIM
- conditional access policies can enforce strong authentication
- identity risks can be monitored through Identity Protection
- access reviews support long-term governance
- emergency break-glass accounts provide recovery capability

These controls ensure the Azure environment follows modern identity security practices.

---

# Identity Implementation Summary

The identity implementation for the landing zone includes the following components:

- Microsoft Entra ID cloud-only identity model
- executive and employee user provisioning
- external partner collaboration
- security group based access control
- Azure RBAC role assignments
- identity governance and security controls

This identity architecture provides a secure and scalable foundation for the Azure Landing Zone.

---

# Next Implementation Area

After completing the identity design area, the next landing zone implementation phase is:

**Subscription and Resource Organization**

This includes:

- subscription structure
- resource group architecture
- naming conventions
- tagging strategy
- governance policies

These components will define how Azure resources are structured within the environment.
