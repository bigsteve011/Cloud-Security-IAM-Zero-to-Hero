# Week 20 — Attack Simulation, Demo & SCS-C03

**🛰️ Month 5 · AWS Security Services & Detection** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Safe attack simulation in an isolated sandbox
- Measuring detection and response time (MTTD/MTTR)
- Recording a clear detect → respond → evidence demo
- GenAI security on AWS: Bedrock guardrails and model access control
- SCS-C03 exam strategy

## Learning objectives

By the end of this week you can:

- Run a controlled CloudGoat scenario end to end
- Show detection and automatic response on video
- Explain Bedrock guardrails
- Pass SCS-C03

## Core concepts

| Concept | In one line |
|---|---|
| **Isolated sandbox** | Simulate only in a throwaway account with no real data, torn down after. |
| **MTTD/MTTR** | Time to detect and respond — the metrics that prove your pipeline works. |
| **Bedrock guardrails** | Content and topic filters plus least-privilege model access. |
| **Demo narrative** | Problem → attack → detection → automatic response → evidence. |

## How it fits together

`Isolated account` → `Run scenario` → `Detection fires` → `Auto-response` → `Evidence + teardown`

## 🔨 Hands-on lab — Controlled Detect-and-Respond Demo

**Platform:** Isolated AWS sandbox + CloudGoat + Tutorials Dojo · **Est. time:** 6 h

1. Deploy a CloudGoat scenario in an isolated, data-free account
   ```bash
   ./cloudgoat.py create iam_privesc_by_rollback
   ```
2. Trigger the scenario's activity and watch GuardDuty/Security Hub detect it
3. Confirm the matching remediation playbook responds automatically
4. Record a 3-minute demo and note MTTD/MTTR
5. Destroy the scenario and confirm teardown
   ```bash
   ./cloudgoat.py destroy all
   ```
6. Sit the AWS SCS-C03 exam

## Prove it

**Deliverable:** P5 complete: demo video link, MTTD/MTTR note, architecture diagram and LinkedIn post on detect-and-respond

Feeds the flagship project **P5 `cloud-auto-remediation`**.

**Done when:**

- [ ] Scenario detected automatically
- [ ] Response verified + logged
- [ ] Sandbox torn down
- [ ] SCS-C03 passed 🎓

## 🎤 Interview drill

**Q — An access key leaked on GitHub — what happens in the next 5 minutes?**

> GitHub + AWS detect the exposed key and quarantine it; GuardDuty flags anomalous use; the remediation playbook deactivates the key, notifies, and opens an incident; you review CloudTrail for actions taken, rotate dependent secrets, and preserve evidence. Long term: move to OIDC so no long-lived key exists.

## Session deck

- [W20_Simulation_SCS_C03.pptx](W20_Simulation_SCS_C03.pptx)

## 🎓 Certification this month

AWS Security – Specialty (SCS-C03)
