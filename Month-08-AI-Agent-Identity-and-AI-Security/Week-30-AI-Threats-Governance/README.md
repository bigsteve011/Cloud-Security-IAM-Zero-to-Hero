# Week 30 — AI Threats, Red-Teaming & AI Governance

**🤖 Month 8 · AI Agent Identity & AI Security (Capstone)** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- OWASP Top 10 for LLM Apps and agentic threats; MITRE ATLAS
- Prompt injection (direct/indirect), tool poisoning, excessive agency
- Red-teaming the agent safely
- ISO/IEC 42001, EU AI Act deployer duties, NIST AI RMF
- Agent governance: inventory, ownership, certification

## Learning objectives

By the end of this week you can:

- Run an indirect prompt-injection test and show the identity control blocking exfiltration
- Map agent risks to OWASP LLM / ATLAS
- Produce an ISO 42001 / EU AI Act control mapping
- Finish the capstone

## Core concepts

| Concept | In one line |
|---|---|
| **Indirect injection** | Malicious instructions hidden in data (a poisoned ticket) the agent reads. |
| **Excessive agency** | An agent with more permissions/autonomy than its task needs. |
| **Defence in depth** | Identity scoping + PEP + approval + logging, not prompt wording, stop abuse. |
| **ISO 42001** | An AI management system — your Lead Auditor background applies directly. |

## How it fits together

`Poisoned ticket` → `Agent reads` → `Attempts exfil` → `PEP denies (out of scope)` → `Alert + evidence`

## 🔨 Hands-on lab — Red-Team the Agent + Governance Pack

**Platform:** P7 environment + Pwned Labs AI (defensive) · **Est. time:** 6 h

1. Plant an indirect prompt injection in a test ticket instructing data exfiltration
2. Show the agent attempts an out-of-scope call and the PEP denies it
3. Map the scenario to OWASP LLM Top 10 and MITRE ATLAS
4. Write the ISO 42001 / EU AI Act control mapping
5. Produce the agent governance pack: inventory, owners, quarterly certification covering humans + agents
6. Record a 3-minute capstone demo

## Prove it

**Deliverable:** P7 complete ⭐: red-team write-up, governance pack, full control mapping, demo video and a flagship LinkedIn post

Feeds the flagship project **P7 `agent-identity-gateway`**.

**Done when:**

- [ ] Injection blocked by an identity control, not a prompt
- [ ] Risks mapped to OWASP LLM / ATLAS
- [ ] ISO 42001 mapping done
- [ ] Capstone demo recorded

## 🎤 Interview drill

**Q — An AI agent reads a poisoned document telling it to exfiltrate customer data. What stops it?**

> Not the prompt — the identity and authorization controls: the agent holds only short-lived, per-tool, least-privilege scopes, so the exfiltration call is out of scope and the policy enforcement point denies it, logs it and alerts. Human approval and the kill switch are backstops. Prompt-injection defence lives in the authorization layer.

## Session deck

- [W30_AI_Threats_Governance.pptx](W30_AI_Threats_Governance.pptx)
