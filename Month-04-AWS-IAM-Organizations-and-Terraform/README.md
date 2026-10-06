# ☁️ Month 4 — AWS IAM, Organizations & Terraform

*Jan–Feb 2027*

[← Back to program](../README.md)


## Flagship project — P4: Secure Multi-Cloud Landing Zone (Part 1: AWS)

`secure-landing-zone`

Terraform-built AWS Organization with security, log-archive and workload accounts, SCP guardrails, Identity Center federated with Entra ID, and a keyless GitHub Actions pipeline with policy checks.

**Deliverables**

- AWS Organization: management, security, log-archive, workload OUs/accounts
- SCPs: EU-only regions, deny root, protect CloudTrail/GuardDuty, deny public S3
- Organization CloudTrail to an immutable log-archive bucket
- IAM Identity Center federated with Entra ID (SAML + SCIM); permission sets per role
- GitHub Actions with OIDC: plan → Checkov/Trivy → OPA → approval → apply
- Access Analyzer findings reviewed

**Compliance mapping**

| Control | Requirement |
|---|---|
| ISO 27001:2022 A.8.2 | Privileged access rights |
| ISO 27001:2022 A.8.15 | Logging |
| ISO 27001:2022 A.8.9 | Configuration management |
| NIS2 Art. 21(2)(d) | Supply chain / secure development |

## Weeks

| Week | Topic | Lab | Deck |
|---|---|---|---|
| **13** | [AWS IAM Policy Evaluation Logic](Week-13-IAM-Policy-Logic/) | Finding & Fixing Risky IAM Permissions | [pptx](Week-13-IAM-Policy-Logic/W13_IAM_Policy_Logic.pptx) |
| **14** | [STS, AssumeRole & Cross-Account Access](Week-14-STS-AssumeRole/) | Entra ID → AWS Identity Center Federation | [pptx](Week-14-STS-AssumeRole/W14_STS_AssumeRole.pptx) |
| **15** | [AWS Organizations, Control Tower & SCP Guardrails](Week-15-Organizations-SCPs/) | Org + SCP Guardrails in Terraform | [pptx](Week-15-Organizations-SCPs/W15_Organizations_SCPs.pptx) |
| **16** | [Keyless CI/CD with GitHub OIDC & Policy-as-Code](Week-16-Keyless-CI-CD/) | OIDC Pipeline with Policy Gates | [pptx](Week-16-Keyless-CI-CD/W16_Keyless_CI_CD.pptx) |
