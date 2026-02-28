# Structured 12-Phase Implementation Order

The landing zone will be implemented in the following structured order.

---

## Phase 1 – Identity & Access
- Create Microsoft Entra ID security groups
- Define RBAC model
- Assign roles at appropriate scopes
- Apply the least-privilege principle

---

## Phase 2 – Subscription Structure
- Confirm single subscription setup
- Assign subscription-level RBAC roles
- Prepare future multi-subscription design

---

## Phase 3 – Resource Group Organization
- Create structured Resource Groups:
  - RG-Network
  - RG-Apps
  - RG-Backup
  - RG-Monitoring
  - RG-Compute
- Apply naming standards

---

## Phase 4 – Networking
- Deploy Virtual Network (VNet)
- Configure subnet
- Apply Network Security Group (NSG)
- Establish baseline isolation

---

## Phase 5 – Storage
- Deploy Azure Storage Account (Blob)
- Configure backup container
- Enable encryption at rest
- Configure access control

---

## Phase 6 – Compute & Applications
- Deploy Web App (Content Tracker)
- Deploy a temporary Azure VM for DR restore
- Configure Entra ID SSO

---

## Phase 7 – Monitoring
- Deploy Log Analytics Workspace
- Enable diagnostic settings
- Configure alert rules
- Define log retention policy

---

## Phase 8 – Governance & Hardening
- Implement tagging strategy
- Apply Azure Policies
- Define compliance controls
- Plan future multi-subscription expansion
- Consider private endpoints and VPN implementation

---

## Phase 9 – Operations & Management
- Define incident response process
- Create operational runbooks
- Configure Azure Update Management for VM
- Test backup and restore procedures
- Define RTO (Recovery Time Objective)
- Define RPO (Recovery Point Objective)

---

## Phase 10 – Automation & DevOps
- Introduce Infrastructure as Code (Bicep or Terraform)
- Structure IaC repository
- Implement CI/CD pipeline (GitHub Actions or Azure DevOps)
- Enable repeatable environment deployments

---

## Phase 11 – Security Posture & Continuous Improvement
- Enable Microsoft Defender for Cloud (baseline tier)
- Review Secure Score recommendations
- Implement security hardening suggestions
- Plan Microsoft Sentinel integration (future phase)

---

## Phase 12 – Cost Management & Optimization
- Define Azure budget and cost alerts
- Implement resource tagging for cost tracking
- Configure storage lifecycle policies (Hot/Cool/Archive)
- Review cost reports monthly
- Optimize unused resources
