# Week 4 — SAML 2.0, SCIM 2.0, FIDO2/Passkeys & Terraform Basics

**🧱 Month 1 · Foundations & Identity Protocols** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- SAML 2.0: SP- vs IdP-initiated, assertions, signatures, audience restriction
- SAML attacks: XML signature wrapping, Golden SAML, assertion replay
- SCIM 2.0 provisioning: /Users, /Groups, PATCH semantics
- FIDO2/WebAuthn and passkeys: origin binding and why they beat OTP
- Terraform fundamentals: providers, state, plan/apply, remote state

## Learning objectives

By the end of this week you can:

- Decode a live SAML response with SAML-tracer
- Implement a minimal SCIM server that Okta can provision to
- Explain phishing resistance in one sentence
- Deploy and destroy a first Terraform stack

## Core concepts

| Concept | In one line |
|---|---|
| **Assertion** | Signed XML statement: subject, audience, conditions, attributes. |
| **Golden SAML** | Steal the IdP signing key and you can forge any user. Protect AD FS keys like domain admin. |
| **SCIM** | Standard REST API for provisioning. The IdP pushes create/update/deactivate. |
| **Passkey** | Key pair bound to the site origin. A phishing site gets nothing usable. |

## How it fits together

`User → SP` → `AuthnRequest` → `IdP authenticates` → `Signed assertion` → `SP validates`

## 🔨 Hands-on lab — SAML SSO + SCIM Endpoint

**Platform:** Local + Okta + KodeKloud Terraform · **Est. time:** 4 h

1. Install SAML-tracer in your browser and capture an Okta SAML login
2. Add SAML SP to the P1 app
   ```bash
   pip install python3-saml
   ```
3. Build SCIM /Users endpoint (GET, POST, PATCH active=false)
4. Expose locally for Okta provisioning tests
   ```bash
   ngrok http 5000
   ```
5. Terraform hello-world: an S3 bucket with block-public-access
   ```bash
   terraform init && terraform plan -out tf.plan && terraform apply tf.plan
   ```
6. Destroy everything
   ```bash
   terraform destroy -auto-approve
   ```

## Prove it

**Deliverable:** P1 complete: OIDC + SAML + SCIM, README with diagrams, attack table and control mapping

Feeds the flagship project **P1 `identity-protocol-lab`**.

**Done when:**

- [ ] SAML login validates signature + audience
- [ ] Okta deactivates a user via SCIM
- [ ] Terraform apply/destroy cycle done
- [ ] P1 pinned on GitHub + LinkedIn post drafted

## 🎤 Interview drill

**Q — SAML or OIDC for a new SaaS integration — which and why?**

> OIDC for new apps (JSON/JWT, mobile-friendly, simpler). SAML where the vendor only supports it or for legacy enterprise SSO. Either way: signed responses, strict audience, short lifetimes and SCIM for lifecycle.

## Session deck

- [W4_SAML_SCIM_FIDO2.pptx](W4_SAML_SCIM_FIDO2.pptx)
