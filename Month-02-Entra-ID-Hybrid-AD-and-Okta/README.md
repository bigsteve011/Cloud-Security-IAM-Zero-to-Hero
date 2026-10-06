# 🏛️ Month 2 — Entra ID, Hybrid AD & Okta

*Nov–Dec 2026*

[← Back to program](../README.md)


## Flagship project — P2: Wisła Bank Hybrid Identity & Zero Trust Access

`hybrid-identity-zero-trust`

On-prem AD synced to Entra ID and federated with Okta, with a Conditional Access baseline deployed as code and an executed AD FS → Entra ID migration runbook.

**Deliverables**

- Windows Server AD lab (wislabank.local) with tiered OUs
- Entra Cloud Sync configured with scoped OUs
- ~12 Conditional Access policies as code (Terraform azuread or Graph)
- Break-glass accounts excluded and monitored
- Okta ↔ Entra federation for a subset of SaaS apps
- AD FS → Entra ID migration runbook with rollback, executed in the lab

**Compliance mapping**

| Control | Requirement |
|---|---|
| ISO 27001:2022 A.5.15–5.18 | Access control, identity, auth info, access rights |
| ISO 27001:2022 A.8.2–8.5 | Privileged access, restriction, secure auth |
| NIS2 Art. 21 | Access control and MFA |
| DORA Art. 9 | ICT access control policies |

## Weeks

| Week | Topic | Lab | Deck |
|---|---|---|---|
| **5** | [Active Directory Fundamentals & the Tiered Admin Model](Week-05-Active-Directory/) | Build Wisła Bank AD | [pptx](Week-05-Active-Directory/W5_Active_Directory.pptx) |
| **6** | [Entra ID Core: Sync, Auth Methods & App Registrations](Week-06-Entra-ID-Core/) | Hybrid Sync & App Permission Audit | [pptx](Week-06-Entra-ID-Core/W6_Entra_ID_Core.pptx) |
| **7** | [Conditional Access as Code & Identity Protection](Week-07-Conditional-Access/) | CA Baseline in Terraform | [pptx](Week-07-Conditional-Access/W7_Conditional_Access.pptx) |
| **8** | [Okta Workforce Identity & AD FS Migration](Week-08-Okta-Migration/) | Okta Integration + AD FS Migration | [pptx](Week-08-Okta-Migration/W8_Okta_Migration.pptx) |
