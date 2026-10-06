# Week 14 — STS, AssumeRole & Cross-Account Access

**☁️ Month 4 · AWS IAM, Organizations & Terraform** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- STS, temporary credentials and the AssumeRole trust model
- Cross-account roles and external IDs (confused-deputy defence)
- IAM Identity Center federated with Entra ID (SAML + SCIM)
- Permission sets and account assignments
- Role chaining limits and session tags

## Learning objectives

By the end of this week you can:

- Federate Identity Center with Entra ID
- Design permission sets mapped to Wisła Bank roles
- Explain the confused-deputy problem and the external-ID fix
- Replace long-lived keys with role assumption

## Core concepts

| Concept | In one line |
|---|---|
| **STS** | Short-lived credentials from AssumeRole. The goal: no long-lived keys. |
| **Trust policy** | Who may assume a role. The resource policy of the role itself. |
| **External ID** | Shared secret in a third-party trust policy — stops confused-deputy abuse. |
| **Permission set** | Identity Center's reusable role template provisioned into accounts. |

## How it fits together

`Entra ID` → `SAML + SCIM` → `Identity Center` → `Permission set` → `Account role`

## 🔨 Hands-on lab — Entra ID → AWS Identity Center Federation

**Platform:** AWS Organizations + Entra ID + AWS Skill Builder · **Est. time:** 4 h

1. Enable IAM Identity Center in the management account
2. Configure Entra ID as the external IdP (SAML) and enable SCIM provisioning
3. Create permission sets: Billing-ReadOnly, SecurityAudit, PowerUser-NonProd
4. Assign groups from Entra to accounts
5. Assume a role via the CLI using the SSO profile
   ```bash
   aws sso login --profile wisla-securityaudit && aws sts get-caller-identity --profile wisla-securityaudit
   ```
6. Complete the AWS Skill Builder Security Engineer identity modules

## Prove it

**Deliverable:** P4: identity-center/ config, permission-set definitions and a federation diagram

Feeds the flagship project **P4 `secure-landing-zone`**.

**Done when:**

- [ ] SSO login from Entra works
- [ ] SCIM provisions groups
- [ ] 3 permission sets mapped
- [ ] No IAM users created for humans

## 🎤 Interview drill

**Q — Why is the external ID important in cross-account roles?**

> It defends against the confused-deputy problem: a third party that manages many customers must present the right external ID, so it cannot be tricked into using its access against the wrong customer's resources.

## Session deck

- [W14_STS_AssumeRole.pptx](W14_STS_AssumeRole.pptx)
