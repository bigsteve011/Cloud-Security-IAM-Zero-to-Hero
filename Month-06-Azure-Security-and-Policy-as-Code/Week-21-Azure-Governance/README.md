# Week 21 — Azure Governance: Management Groups & Azure Policy

**🔷 Month 6 · Azure Security & Policy-as-Code** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Management groups, subscriptions and the governance hierarchy
- Azure Policy: definitions, initiatives, effects (deny, audit, deployIfNotExists)
- Azure RBAC vs Azure Policy — different jobs
- Landing-zone concepts (Azure Landing Zone / CAF)
- Blueprints vs Terraform for governance

## Learning objectives

By the end of this week you can:

- Build a management-group hierarchy as code
- Write deny and audit policies
- Explain RBAC vs Policy
- Remediate non-compliant resources

## Core concepts

| Concept | In one line |
|---|---|
| **Management group** | Container above subscriptions where policy and RBAC inherit down. |
| **Initiative** | A named set of policies assigned together and reported as one score. |
| **deployIfNotExists** | Policy that auto-deploys a missing control (e.g. a diagnostic setting). |
| **RBAC vs Policy** | RBAC = who can act; Policy = what resources may exist. |

## How it fits together

`Tenant root MG` → `Platform + Landing-zone MGs` → `Subscriptions` → `Initiatives` → `Compliance score`

## 🔨 Hands-on lab — Management Groups + Policy-as-Code

**Platform:** Azure free/dev subscription + Microsoft Learn SC-500 · **Est. time:** 4 h

1. Create the MG hierarchy in Terraform
   ```bash
   resource "azurerm_management_group" "platform" { display_name = "Platform" parent_management_group_id = azurerm_management_group.root.id }
   ```
2. Write policies: EU-only regions, require encryption, deny public IP, require tags
3. Bundle them into an initiative and assign at the MG
4. Trigger remediation for an existing non-compliant resource
5. Review the compliance score
   ```bash
   az policy state summarize --management-group wisla-root
   ```
6. Complete the SC-500 governance module

## Prove it

**Deliverable:** P4 Azure: management-groups/ + policy/ Terraform and a compliance-score screenshot

Feeds the flagship project **P4b `secure-landing-zone`**.

**Done when:**

- [ ] MG hierarchy as code
- [ ] Public IP denied by policy
- [ ] Remediation task runs
- [ ] Initiative assigned at MG

## 🎤 Interview drill

**Q — Azure RBAC vs Azure Policy — when do you use each?**

> RBAC controls who can perform actions on resources; Policy controls which resources and configurations are allowed to exist and can audit or auto-remediate. You need both: RBAC for access, Policy for guardrails.

## Session deck

- [W21_Azure_Governance.pptx](W21_Azure_Governance.pptx)

## 🎓 Certification this month

SC-500 Cloud & AI Security (optional)
