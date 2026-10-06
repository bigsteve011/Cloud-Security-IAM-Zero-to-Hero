# Week 11 — Joiner-Mover-Leaver Automation & SoD

**⚖️ Month 3 · Identity Governance, PAM & Automation** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- HR as the authoritative source; attribute mapping
- Joiner, mover and leaver logic and edge cases (rehires, contractors)
- Role-based vs attribute-based access models
- Segregation of Duties: toxic combinations and rule sets
- Idempotent automation, dry-run mode and audit logging

## Learning objectives

By the end of this week you can:

- Build the JML engine core against Entra ID and Okta
- Implement an SoD rule engine
- Add dry-run and structured audit logs
- Write unit tests for every JML path

## Core concepts

| Concept | In one line |
|---|---|
| **Mover risk** | Access accumulates when people change role. Remove old, then add new. |
| **Toxic combo** | e.g. 'Create vendor' + 'Approve payment' in one person. |
| **Idempotent** | Running twice gives the same result. Essential for safe automation. |
| **Dry-run** | Show planned changes before applying — just like terraform plan. |

## How it fits together

`HRIS feed` → `Diff vs state` → `SoD check` → `Apply (or dry-run)` → `Audit log`

## 🔨 Hands-on lab — Build the JML Engine

**Platform:** Local Python + Entra + Okta APIs · **Est. time:** 6 h

1. Generate a fake HRIS with Faker
   ```bash
   pip install faker && python hris_sim.py --users 200 --out hris.csv
   ```
2. Map job codes to roles in roles.yaml
3. Implement joiner/mover/leaver handlers with Graph and Okta SDK
   ```bash
   pip install msgraph-sdk okta
   ```
4. Add SoD rules (sod_rules.yaml) and block conflicting assignments
5. Run in dry-run, review, then apply
   ```bash
   python -m jml run --source hris.csv --dry-run
   ```
6. Write pytest cases for each scenario
   ```bash
   pytest -q
   ```

## Prove it

**Deliverable:** P3: engine/ package with JML, SoD, dry-run, JSON audit logs and tests

Feeds the flagship project **P3 `iam-governance-engine`**.

**Done when:**

- [ ] Leaver disabled in both IdPs < 5 min
- [ ] SoD conflict blocked and logged
- [ ] Tests pass in CI
- [ ] Dry-run output in README

## 🎤 Interview drill

**Q — Design JML for 200 SaaS apps and prove it to auditors.**

> HR as source, IdP as hub with SCIM to apps, role/attribute model, SoD checks, leaver SLA, reconciliation for non-SCIM apps, logs and periodic reviews as evidence.

## Session deck

- [W11_JML_SoD.pptx](W11_JML_SoD.pptx)

## 🎓 Certification this month

SC-300 Identity & Access Administrator
