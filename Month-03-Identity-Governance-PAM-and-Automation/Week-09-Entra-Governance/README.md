# Week 9 — Entra ID Governance: Entitlements & Access Reviews

**⚖️ Month 3 · Identity Governance, PAM & Automation** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Entitlement management: catalogs, access packages, policies, connected orgs
- Access reviews: scope, reviewers, recurrence, auto-apply
- Lifecycle workflows for joiners and leavers
- Okta Identity Governance: requests and certifications
- Designing reviews auditors accept

## Learning objectives

By the end of this week you can:

- Build three access packages for Wisła Bank roles
- Run a quarterly-style access review end to end
- Configure a leaver lifecycle workflow
- Export review decisions as audit evidence

## Core concepts

| Concept | In one line |
|---|---|
| **Access package** | Bundle of groups, apps and roles requested together with approval and expiry. |
| **Access review** | Periodic recertification. Auto-apply removes denied access. |
| **Lifecycle workflow** | Triggered on employeeHireDate / leaveDateTime attributes. |
| **Evidence** | Who reviewed what, when, decision and justification — exported, not screenshotted. |

## How it fits together

`Request` → `Approve` → `Assign with expiry` → `Review` → `Auto-remove`

## 🔨 Hands-on lab — Access Packages & Reviews

**Platform:** Entra ID Governance trial + Microsoft Learn · **Est. time:** 3.5 h

1. Create catalog 'Wisla-Retail-Banking' with 2 groups + 1 app
2. Create access package 'Loan Officer' with manager approval and 90-day expiry
3. Create a lifecycle workflow: leaver → disable, remove groups, notify manager
4. Launch an access review on the Loan Officer package
5. Export decisions via Graph
   ```bash
   Get-MgIdentityGovernanceAccessReviewDefinitionInstanceDecision -AccessReviewScheduleDefinitionId $def -AccessReviewInstanceId $inst -All | Export-Csv review-evidence.csv
   ```
6. Complete SC-300: Plan and implement identity governance

## Prove it

**Deliverable:** P3 repo: governance/ design doc, access package matrix and exported review evidence

Feeds the flagship project **P3 `iam-governance-engine`**.

**Done when:**

- [ ] 3 access packages live
- [ ] Review completed with auto-apply
- [ ] Leaver workflow tested
- [ ] Evidence CSV in repo (sanitised)

## 🎤 Interview drill

**Q — How do you design access reviews auditors trust?**

> Defined scope and population, independent reviewers, documented frequency, auto-apply of denials, completeness check, exported evidence with timestamps and reviewer identity, and follow-up on non-responses.

## Session deck

- [W9_Entra_Governance.pptx](W9_Entra_Governance.pptx)

## 🎓 Certification this month

SC-300 Identity & Access Administrator
