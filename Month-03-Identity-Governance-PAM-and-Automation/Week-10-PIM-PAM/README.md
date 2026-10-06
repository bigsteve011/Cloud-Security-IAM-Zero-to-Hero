# Week 10 — PIM, PAM, JIT Access & Break-Glass

**⚖️ Month 3 · Identity Governance, PAM & Automation** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Privileged Identity Management for Entra roles, Azure roles and groups
- JIT and JEA; approval, MFA and justification on activation
- PAM concepts: vaulting, session recording, credential rotation (CyberArk model)
- Break-glass governance and testing cadence
- Privileged access reporting for audit

## Learning objectives

By the end of this week you can:

- Remove all standing Global Admin assignments except break-glass
- Configure PIM with approval and 2-hour max activation
- Explain the CyberArk vault + PSM model
- Produce a privileged-access report

## Core concepts

| Concept | In one line |
|---|---|
| **Standing access** | Always-on admin rights. The thing attackers hunt for. |
| **JIT** | Eligible, not active. Activate with MFA + reason for a time-box. |
| **Vault** | Credentials checked out, rotated after use, never known by humans. |
| **Session recording** | Privileged sessions proxied and recorded for forensics. |

## How it fits together

`Eligible` → `Request + MFA` → `Approval` → `Time-boxed active` → `Auto-expire + log`

## 🔨 Hands-on lab — PIM Configuration & Privileged Report

**Platform:** Entra P2 trial + Azure · **Est. time:** 3 h

1. Convert permanent role assignments to eligible
2. Set Global Admin activation: approval, MFA, 2h, ticket number
3. Enable PIM for Groups on an Azure subscription Owner group
4. Activate a role and capture the audit trail
   ```bash
   Get-MgAuditLogDirectoryAudit -Filter "category eq 'RoleManagement'" -Top 20
   ```
5. Script a report of all eligible/active privileged assignments
6. Read CyberArk PAM fundamentals and diagram the vault model

## Prove it

**Deliverable:** P3: pam/ folder with PIM settings export, privileged report script and break-glass test log

Feeds the flagship project **P3 `iam-governance-engine`**.

**Done when:**

- [ ] Zero standing GA (except break-glass)
- [ ] Activation requires approval
- [ ] Report script runs
- [ ] Break-glass test documented

## 🎤 Interview drill

**Q — An auditor asks for proof admin access is controlled. What do you show?**

> PIM settings (eligible only, approval, MFA, max duration), activation logs with justification, quarterly review of eligible assignments, break-glass monitoring alerts and test records.

## Session deck

- [W10_PIM_PAM.pptx](W10_PIM_PAM.pptx)

## 🎓 Certification this month

SC-300 Identity & Access Administrator
