# Week 27 — Writing Detections: KQL, Sigma & the Detection Pack

**🔑 Month 7 · Workload Identity, Kubernetes & Identity Threat Detection** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- KQL for Sentinel / Defender XDR
- Sigma rules and conversion to multiple SIEMs
- CloudTrail-based detections for AWS identity events
- Detection quality: false-positive tuning, enrichment, test cases
- Packaging detections with reproduction steps and playbooks

## Learning objectives

By the end of this week you can:

- Write and tune KQL and Sigma detections
- Build CloudTrail detections for risky IAM events
- Document each detection to a repeatable standard
- Ship the 12-detection pack

## Core concepts

| Concept | In one line |
|---|---|
| **KQL** | Sentinel's query language. Join sign-in + audit logs to spot abuse. |
| **Sigma** | Vendor-neutral rule format; convert to Sentinel, Splunk, Elastic. |
| **Tuning** | Enrich and baseline to cut false positives — an untuned rule gets ignored. |
| **Repeatability** | Each detection ships with logs, repro steps, FP/TP notes and a playbook. |

## How it fits together

`Hypothesis` → `Query (KQL/Sigma)` → `Test on sample logs` → `Tune FPs` → `Package + playbook`

## 🔨 Hands-on lab — Build the 12-Detection Pack

**Platform:** Sentinel + Sigma + AWS CloudTrail · **Est. time:** 6 h

1. Write KQL for impossible-travel and MFA-fatigue sign-ins
   ```bash
   SigninLogs | where ResultType == 0 | ... summarize by UserPrincipalName
   ```
2. Write Sigma rules for new OAuth consent and privileged-role assignment
3. Write CloudTrail detections: new access key, policy-version change, root login
4. Add sample logs and test cases for each
5. Tune to reduce false positives and document FP/TP notes
6. Package each with a response playbook

## Prove it

**Deliverable:** P6 complete: identity-detection-pack/ (12 detections) + zero-static-secrets demo, README and a LinkedIn post on NHI + ITDR

Feeds the flagship project **P6 `zero-static-secrets + identity-detection-pack`**.

**Done when:**

- [ ] 12 detections with repro + playbooks
- [ ] Rules tested on sample logs
- [ ] FP notes present
- [ ] P6 pinned on GitHub

## 🎤 Interview drill

**Q — What makes a good detection versus a noisy one?**

> A clear hypothesis tied to an ATT&CK technique, a specific telemetry source, enrichment and baselining to cut false positives, documented test cases, and a response playbook — so the SOC trusts and acts on it rather than muting it.

## Session deck

- [W27_Detection_Engineering.pptx](W27_Detection_Engineering.pptx)
