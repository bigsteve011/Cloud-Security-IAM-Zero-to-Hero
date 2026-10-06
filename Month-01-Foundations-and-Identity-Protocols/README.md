# 🧱 Month 1 — Foundations & Identity Protocols

*Oct–Nov 2026*

[← Back to program](../README.md)


## Flagship project — P1: Identity Protocol Lab

`identity-protocol-lab`

A Python app implementing OIDC Authorization Code + PKCE, SAML SP-initiated SSO and a SCIM 2.0 endpoint against Entra ID and Okta, with a token-inspector page and an attack/defence section.

**Deliverables**

- Flask/FastAPI app with OIDC + PKCE login against Entra ID and Okta
- SAML SP-initiated SSO flow with signature and audience validation
- SCIM 2.0 /Users and /Groups endpoint with bearer-token auth
- Token inspector page: decoded header/claims + each validation step shown
- Mermaid sequence diagram per flow
- Attacks section: replay, alg=none / key confusion, open redirect, missing PKCE — and the fix for each

**Compliance mapping**

| Control | Requirement |
|---|---|
| ISO 27001:2022 A.5.17 | Authentication information |
| ISO 27001:2022 A.8.5 | Secure authentication |
| NIS2 Art. 21(2)(j) | MFA / secured authentication |
| DORA Art. 9(4)(c) | Strong authentication mechanisms |

## Weeks

| Week | Topic | Lab | Deck |
|---|---|---|---|
| **1** | [Cloud Networking for Security Engineers](Week-01-Cloud-Networking/) | Lab Stack Setup & HTTPS Dissection | [pptx](Week-01-Cloud-Networking/W1_Cloud_Networking.pptx) |
| **2** | [Linux, PowerShell, Python & Git for Identity Automation](Week-02-Scripting-Git/) | Identity Inventory Script | [pptx](Week-02-Scripting-Git/W2_Scripting_Git.pptx) |
| **3** | [OAuth 2.0/2.1, OIDC & JWT Deep Dive](Week-03-OAuth-OIDC-JWT/) | OIDC Client from Scratch | [pptx](Week-03-OAuth-OIDC-JWT/W3_OAuth_OIDC_JWT.pptx) |
| **4** | [SAML 2.0, SCIM 2.0, FIDO2/Passkeys & Terraform Basics](Week-04-SAML-SCIM-FIDO2/) | SAML SSO + SCIM Endpoint | [pptx](Week-04-SAML-SCIM-FIDO2/W4_SAML_SCIM_FIDO2.pptx) |
