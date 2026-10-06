# Week 22 — Defender for Cloud, Key Vault & Network Security

**🔷 Month 6 · Azure Security & Policy-as-Code** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Defender for Cloud: CSPM, secure score and workload protection plans
- Key Vault: RBAC model, soft-delete, purge protection, private endpoints
- NSGs, Azure Firewall and Private Link
- Microsoft Sentinel basics
- Workload identity federation for keyless pipelines

## Learning objectives

By the end of this week you can:

- Enable Defender plans and read the secure score
- Harden Key Vault with RBAC and private endpoints
- Federate a pipeline with workload identity (no secrets)
- Connect findings to Sentinel

## Core concepts

| Concept | In one line |
|---|---|
| **Secure score** | Defender's prioritised posture metric. Track it over time. |
| **Purge protection** | Prevents permanent deletion of keys within the retention window. |
| **Workload identity federation** | Azure trusts a GitHub/K8s OIDC token — no client secret. |
| **Private endpoint** | Brings a PaaS service onto your VNet with a private IP. |

## How it fits together

`Enable Defender` → `Secure score` → `Harden Key Vault` → `Private endpoints` → `Findings → Sentinel`

## 🔨 Hands-on lab — Defender + Key Vault Hardening

**Platform:** Azure + AzureGoat (defensive) + Microsoft Learn · **Est. time:** 4.5 h

1. Enable Defender for Cloud plans on the subscription
2. Create a Key Vault with RBAC, soft-delete and purge protection
   ```bash
   az keyvault create -n wisla-kv -g rg-wisla --enable-rbac-authorization --enable-purge-protection
   ```
3. Add a private endpoint and disable public network access
4. Configure GitHub workload identity federation to Azure
5. Deploy AzureGoat and use it to understand misconfigurations, then write Defender recommendations to fix each
6. Stream Defender findings into Sentinel

## Prove it

**Deliverable:** P4 Azure: key-vault/ + defender/ Terraform, secure-score note and a hardening checklist

Feeds the flagship project **P4b `secure-landing-zone`**.

**Done when:**

- [ ] Defender plans on
- [ ] Key Vault private + purge-protected
- [ ] Pipeline has no stored secret
- [ ] Findings in Sentinel

## 🎤 Interview drill

**Q — How do you give a CI pipeline access to Azure without storing a secret?**

> Workload identity federation: register a federated credential on an app/managed identity trusting the pipeline's OIDC issuer and subject; the pipeline exchanges its OIDC token for an Azure token at runtime. No client secret exists to leak.

## Session deck

- [W22_Defender_Key_Vault.pptx](W22_Defender_Key_Vault.pptx)

## 🎓 Certification this month

SC-500 Cloud & AI Security (optional)
