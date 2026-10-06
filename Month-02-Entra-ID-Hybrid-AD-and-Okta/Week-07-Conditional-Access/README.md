# Week 7 — Conditional Access as Code & Identity Protection

**🏛️ Month 2 · Entra ID, Hybrid AD & Okta** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Conditional Access evaluation: assignments, conditions, grant and session controls
- Baseline design: admins, all users, guests, workloads, legacy auth
- Break-glass accounts: exclusion, monitoring and FIDO2 keys
- Identity Protection: user and sign-in risk, risk-based policies
- Report-only mode, What If tool and CA deployment via Terraform

## Learning objectives

By the end of this week you can:

- Design a 12-policy CA baseline for Wisła Bank
- Deploy it as code in report-only, then enforce
- Alert on any break-glass sign-in
- Test with the What If tool

## Core concepts

| Concept | In one line |
|---|---|
| **Report-only** | See impact for 1–2 weeks before enforcing. Never skip. |
| **Break-glass** | 2 cloud-only accounts, FIDO2, excluded from CA, alerted on every use. |
| **Legacy auth** | No MFA possible. Block with one policy; it stops most password spray. |
| **Policy as code** | Terraform azuread_conditional_access_policy = reviewable, versioned, repeatable. |

## How it fits together

`Sign-in` → `Assignments match` → `Conditions` → `Grant controls` → `Session controls`

## 🔨 Hands-on lab — CA Baseline in Terraform

**Platform:** Entra P2 trial + Terraform · **Est. time:** 4 h

1. Create two break-glass accounts + exclusion group
2. Write CA policies in Terraform (state = enabledForReportingButNotEnforced)
   ```bash
   resource "azuread_conditional_access_policy" "block_legacy" { display_name = "CA001-Block-Legacy-Auth" state = "enabledForReportingButNotEnforced" ... }
   ```
3. Plan and apply
   ```bash
   terraform plan -out ca.plan && terraform apply ca.plan
   ```
4. Use What If for an admin from an unknown country
5. Create a Log Analytics alert for break-glass sign-ins
   ```bash
   SigninLogs | where UserPrincipalName in ('bg1@wisla.onmicrosoft.com','bg2@wisla.onmicrosoft.com')
   ```
6. Enforce after review; export policy JSON to repo

## Prove it

**Deliverable:** P2: ca-policies/ Terraform module, policy matrix table and break-glass runbook

Feeds the flagship project **P2 `hybrid-identity-zero-trust`**.

**Done when:**

- [ ] 12 policies deployed via code
- [ ] Break-glass alert fires on test
- [ ] Legacy auth blocked
- [ ] Policy matrix in README

## 🎤 Interview drill

**Q — Design Conditional Access for 2,000 users without locking anyone out.**

> Persona-based policies, break-glass exclusions, report-only for 2 weeks, What If testing, staged rollout via groups, monitor sign-in logs, then enforce; manage as code with PR review.

## Session deck

- [W7_Conditional_Access.pptx](W7_Conditional_Access.pptx)
