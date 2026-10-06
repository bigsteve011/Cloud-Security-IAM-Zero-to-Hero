# 🔷 Month 6 — Azure Security & Policy-as-Code

*Mar–Apr 2027* · 🎓 **SC-500 Cloud & AI Security (optional)**

[← Back to program](../README.md)


## Flagship project — P4b: Secure Multi-Cloud Landing Zone (Part 2: Azure)

`secure-landing-zone`

The Azure half of the landing zone: management groups, Azure Policy initiatives, Defender for Cloud, Key Vault and a unified cross-cloud compliance dashboard mapped to ISO 27001, NIS2 and DORA.

**Deliverables**

- Management-group hierarchy with Azure Policy initiatives
- Policy-as-code: EU-only regions, encryption required, no public IPs, mandatory tags
- Defender for Cloud plans enabled with CSPM
- Key Vault with RBAC + private endpoints
- Workload identity federation for pipelines
- Unified dashboard: AWS Security Hub + Azure Defender findings mapped to controls

**Compliance mapping**

| Control | Requirement |
|---|---|
| ISO 27001:2022 A.8.9 | Configuration management |
| ISO 27001:2022 A.8.16 | Monitoring |
| NIS2 Art. 21 | Risk-management measures |
| DORA Art. 6–9 | ICT risk-management framework |

## Weeks

| Week | Topic | Lab | Deck |
|---|---|---|---|
| **21** | [Azure Governance: Management Groups & Azure Policy](Week-21-Azure-Governance/) | Management Groups + Policy-as-Code | [pptx](Week-21-Azure-Governance/W21_Azure_Governance.pptx) |
| **22** | [Defender for Cloud, Key Vault & Network Security](Week-22-Defender-Key-Vault/) | Defender + Key Vault Hardening | [pptx](Week-22-Defender-Key-Vault/W22_Defender_Key_Vault.pptx) |
| **23** | [Unified Multi-Cloud Compliance Dashboard → SC-500](Week-23-Unified-Dashboard/) | Cross-Cloud Compliance View | [pptx](Week-23-Unified-Dashboard/W23_Unified_Dashboard.pptx) |
