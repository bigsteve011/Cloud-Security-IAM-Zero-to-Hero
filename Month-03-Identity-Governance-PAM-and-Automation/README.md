# ⚖️ Month 3 — Identity Governance, PAM & Automation

*Dec 2026–Jan 2027* · 🎓 **SC-300 Identity & Access Administrator**

[← Back to program](../README.md)


## Flagship project — P3: IAM Governance Automation Engine

`iam-governance-engine`

A Python service that reads a fake HRIS feed and drives Joiner-Mover-Leaver across Entra ID and Okta, scans identity hygiene, and produces an auditor-ready evidence pack with an AI-assisted reviewer summary under human approval.

**Deliverables**

- HRIS CSV/API simulator (joiners, movers, leavers)
- JML engine for Entra ID + Okta (AWS Identity Center added in Month 4)
- Hygiene scanner: stale, orphaned, MFA gaps, SoD conflicts, dormant privileged roles
- Timestamped HTML/PDF evidence pack mapped to ISO 27001
- LLM summary for reviewers with mandatory human approval and full logging
- Unit tests + GitHub Actions CI

**Compliance mapping**

| Control | Requirement |
|---|---|
| ISO 27001:2022 A.5.16 | Identity management |
| ISO 27001:2022 A.5.18 | Access rights (provision, review, removal) |
| ISO 27001:2022 A.5.3 | Segregation of duties |
| DORA Art. 9(4)(c) | Access rights limited to need |

## Weeks

| Week | Topic | Lab | Deck |
|---|---|---|---|
| **9** | [Entra ID Governance: Entitlements & Access Reviews](Week-09-Entra-Governance/) | Access Packages & Reviews | [pptx](Week-09-Entra-Governance/W9_Entra_Governance.pptx) |
| **10** | [PIM, PAM, JIT Access & Break-Glass](Week-10-PIM-PAM/) | PIM Configuration & Privileged Report | [pptx](Week-10-PIM-PAM/W10_PIM_PAM.pptx) |
| **11** | [Joiner-Mover-Leaver Automation & SoD](Week-11-JML-SoD/) | Build the JML Engine | [pptx](Week-11-JML-SoD/W11_JML_SoD.pptx) |
| **12** | [Hygiene Scanner, Evidence Packs & AI-Assisted Reviews → SC-300](Week-12-Evidence-SC-300/) | Evidence Pack + AI Summary | [pptx](Week-12-Evidence-SC-300/W12_Evidence_SC_300.pptx) |
