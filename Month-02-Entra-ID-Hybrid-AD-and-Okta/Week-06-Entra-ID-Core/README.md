# Week 6 — Entra ID Core: Sync, Auth Methods & App Registrations

**🏛️ Month 2 · Entra ID, Hybrid AD & Okta** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Entra Cloud Sync vs Entra Connect Sync; PHS, PTA and federation
- Authentication methods policy, authentication strengths, passkeys in Entra
- App registrations vs enterprise apps (service principals)
- Managed identities: system- vs user-assigned
- B2B collaboration and cross-tenant access settings

## Learning objectives

By the end of this week you can:

- Sync the lab AD to an Entra tenant with Cloud Sync
- Enforce phishing-resistant auth for admins
- Explain app registration vs service principal
- Audit risky app permissions with Graph

## Core concepts

| Concept | In one line |
|---|---|
| **PHS** | Password hash sync — most resilient. Enables leaked-credential detection. |
| **Service principal** | The tenant-local instance of an app. Permissions live here. |
| **Auth strength** | Named combos (e.g. phishing-resistant MFA) usable in Conditional Access. |
| **Managed identity** | Azure-managed credentials for workloads. No secret to leak. |

## How it fits together

`AD DS` → `Cloud Sync agent` → `Entra ID` → `Auth methods` → `Apps + MIs`

## 🔨 Hands-on lab — Hybrid Sync & App Permission Audit

**Platform:** Entra ID P2 trial + Microsoft Learn SC-300 · **Est. time:** 3.5 h

1. Activate an Entra ID P2 trial on a dev tenant
2. Install the Cloud Sync provisioning agent on the DC; scope to Users OU
3. Enable passkeys (FIDO2) in Authentication methods policy
4. List service principals with high-risk Graph permissions
   ```bash
   Get-MgServicePrincipal -All | % { Get-MgServicePrincipalAppRoleAssignment -ServicePrincipalId $_.Id } | Where AppRoleId -in $risky
   ```
5. Create a user-assigned managed identity
   ```bash
   az identity create -g rg-wisla-lab -n mi-reporting
   ```
6. Complete SC-300 module: Implement authentication

## Prove it

**Deliverable:** P2: sync/ design doc, auth-methods export and app-permission risk report

Feeds the flagship project **P2 `hybrid-identity-zero-trust`**.

**Done when:**

- [ ] Synced users visible in Entra
- [ ] Passkey registered for your admin
- [ ] Risky-permission report generated
- [ ] SC-300 module done

## 🎤 Interview drill

**Q — App registration vs enterprise app?**

> App registration is the global definition in the home tenant; the enterprise app is the service principal in each tenant where it is used. Consent and role assignments attach to the service principal.

## Session deck

- [W6_Entra_ID_Core.pptx](W6_Entra_ID_Core.pptx)
