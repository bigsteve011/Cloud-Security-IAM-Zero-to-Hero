# Week 8 — Okta Workforce Identity & AD FS Migration

**🏛️ Month 2 · Entra ID, Hybrid AD & Okta** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Okta Universal Directory, AD agent and profile mastering
- Okta SSO, authentication policies and FastPass
- Lifecycle Management and Okta Workflows
- Okta ↔ Entra federation patterns
- AD FS → Entra ID migration: app inventory, staged rollout, rollback

## Learning objectives

By the end of this week you can:

- Connect the lab AD to Okta with the AD agent
- Federate selected apps between Okta and Entra ID
- Write and execute an AD FS migration runbook
- Ship P2

## Core concepts

| Concept | In one line |
|---|---|
| **Profile master** | One source of truth per attribute. Usually HR → AD → IdPs. |
| **FastPass** | Okta's phishing-resistant, device-bound authenticator. |
| **Staged rollout** | Move groups from federated to managed auth gradually; rollback is a group change. |
| **Workflows** | No-code automation for JML events across SaaS. |

## How it fits together

`Inventory AD FS apps` → `Prioritise` → `Recreate in Entra` → `Staged rollout` → `Decommission`

## 🔨 Hands-on lab — Okta Integration + AD FS Migration

**Platform:** Okta Learning labs + Okta Integrator org + Azure VM · **Est. time:** 5 h

1. Install Okta AD agent and import users
2. Complete Okta Learning: SSO + FastPass hands-on labs
3. Deploy AD FS on a lab VM with one relying party
   ```bash
   Install-WindowsFeature ADFS-Federation -IncludeManagementTools
   ```
4. Export AD FS relying parties for migration inventory
   ```bash
   Get-AdfsRelyingPartyTrust | Select Name,Identifier,IssuanceTransformRules | Export-Csv rp.csv
   ```
5. Run Entra staged rollout for a pilot group
6. Write the runbook: pre-checks, cutover, validation, rollback

## Prove it

**Deliverable:** P2 complete: architecture diagram, CA code, Okta config notes, migration runbook, control mapping

Feeds the flagship project **P2 `hybrid-identity-zero-trust`**.

**Done when:**

- [ ] Pilot group migrated off AD FS
- [ ] Rollback tested
- [ ] P2 README follows template
- [ ] LinkedIn post published

## 🎤 Interview drill

**Q — Migrate 2,000 users off AD FS with zero downtime.**

> Inventory relying parties, map claims, recreate apps in Entra, enable PHS as fallback, staged rollout by group, monitor sign-ins, keep AD FS until all apps cut over, then decommission and rotate trust.

## Session deck

- [W8_Okta_Migration.pptx](W8_Okta_Migration.pptx)
