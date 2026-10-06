# Week 23 — Unified Multi-Cloud Compliance Dashboard → SC-500

**🔷 Month 6 · Azure Security & Policy-as-Code** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Normalising AWS Security Hub and Azure Defender findings
- Mapping findings to ISO 27001 / NIS2 / DORA controls
- Building a single posture view across clouds
- Evidence and reporting for auditors
- SC-500 exam strategy (optional cert)

## Learning objectives

By the end of this week you can:

- Pull findings from both clouds into one dataset
- Map each finding to a control
- Render a unified dashboard
- Finish the P4 landing-zone capstone

## Core concepts

| Concept | In one line |
|---|---|
| **Normalisation** | Different schemas → one common finding model (resource, severity, control). |
| **Control mapping** | Each finding traced to ISO/NIS2/DORA — the differentiator few engineers show. |
| **Single pane** | One posture view beats two consoles for leadership and audit. |
| **Traceability** | Every guardrail links to a requirement; every finding links to a control. |

## How it fits together

`AWS findings` → `Azure findings` → `Normalise` → `Map to controls` → `Dashboard + report`

## 🔨 Hands-on lab — Cross-Cloud Compliance View

**Platform:** Python + AWS + Azure APIs · **Est. time:** 5 h

1. Pull Security Hub findings via boto3
   ```bash
   aws securityhub get-findings --max-results 100 > aws-findings.json
   ```
2. Pull Defender findings via the Azure SDK
3. Normalise both into one schema and map to controls (controls.yaml)
4. Render an HTML dashboard with per-control pass/fail
5. Generate an auditor evidence export
6. Optionally sit SC-500

## Prove it

**Deliverable:** P4 complete: one landing zone, two clouds, one identity source — README with full control mapping and a LinkedIn post; SC-500 optional 🎓

Feeds the flagship project **P4b `secure-landing-zone`**.

**Done when:**

- [ ] Findings from both clouds in one view
- [ ] Each finding mapped to a control
- [ ] Evidence export works
- [ ] P4 pinned on GitHub

## 🎤 Interview drill

**Q — How do you prove multi-cloud compliance to an auditor?**

> A normalised findings model mapped to the control framework, a dashboard showing per-control status, timestamped evidence exports with scope statements, and traceability from each guardrail (SCP/Azure Policy) back to the requirement it satisfies.

## Session deck

- [W23_Unified_Dashboard.pptx](W23_Unified_Dashboard.pptx)

## 🎓 Certification this month

SC-500 Cloud & AI Security (optional)
