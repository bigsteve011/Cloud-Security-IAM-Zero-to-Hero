# Week 26 — Identity Attack Techniques & MITRE ATT&CK

**🔑 Month 7 · Workload Identity, Kubernetes & Identity Threat Detection** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Identity-centric techniques: token theft, MFA fatigue, consent phishing, OAuth app abuse, Golden SAML
- AWS and Entra privilege-escalation patterns (defender's view)
- MITRE ATT&CK identity techniques and mapping
- Attack-path analysis with BloodHound / AzureHound
- Turning techniques into detections

## Learning objectives

By the end of this week you can:

- Map common identity attacks to ATT&CK
- Explain each technique's telemetry footprint
- Use BloodHound to find and close attack paths
- Translate a technique into a detection requirement

## Core concepts

| Concept | In one line |
|---|---|
| **MFA fatigue** | Repeated push prompts until the user approves. Fix: number matching, limits. |
| **Consent phishing** | Trick a user into consenting a malicious OAuth app. Fix: app governance, admin consent. |
| **Golden SAML** | Forged assertions from a stolen IdP key. Fix: protect/rotate signing keys, detect anomalies. |
| **ATT&CK mapping** | Each detection cites a technique ID — shared language with the SOC. |

## How it fits together

`Technique` → `Telemetry source` → `Detection logic` → `ATT&CK ID` → `Response playbook`

## 🔨 Hands-on lab — Attack-Path Analysis & Detection Design

**Platform:** Lab AD + BloodHound + Pwned Labs (defensive) · **Est. time:** 5 h

1. Run SharpHound/AzureHound and import into BloodHound CE
2. Identify the shortest paths to Tier 0 and document how to cut each
3. For 6 techniques, record the log source and the signal they produce
4. Map each to its ATT&CK technique ID
5. Complete a Pwned Labs identity lab from the defender's perspective and note detections
6. Draft detection requirements for the pack

## Prove it

**Deliverable:** P6: an ATT&CK-mapped technique catalogue and attack-path remediation notes

Feeds the flagship project **P6 `zero-static-secrets + identity-detection-pack`**.

**Done when:**

- [ ] Paths to Tier 0 documented + mitigations
- [ ] 6 techniques mapped to telemetry
- [ ] ATT&CK IDs recorded
- [ ] Detection requirements drafted

## 🎤 Interview drill

**Q — How would you detect consent phishing in Entra ID?**

> Monitor audit logs for new OAuth app consents, especially user-consented apps requesting high-value scopes (Mail.Read, Files.Read.All); alert on first-seen publishers, restrict user consent to verified/low-risk apps, require admin consent for sensitive scopes, and review app governance recommendations.

## Session deck

- [W26_Identity_Attacks.pptx](W26_Identity_Attacks.pptx)
