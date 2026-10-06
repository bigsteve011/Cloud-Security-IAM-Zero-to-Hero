# Week 17 — GuardDuty, Security Hub, Config, Inspector & Detective

**🛰️ Month 5 · AWS Security Services & Detection** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- GuardDuty finding types and the organisation delegated-admin model
- Security Hub standards (CIS, AWS FSBP) and finding aggregation
- AWS Config rules and conformance packs
- Inspector for workload vulnerabilities; Detective for investigation
- Security Lake and centralised findings

## Learning objectives

By the end of this week you can:

- Enable the detection stack org-wide from a security account
- Read and triage GuardDuty findings
- Deploy a Config conformance pack
- Aggregate findings into one view

## Core concepts

| Concept | In one line |
|---|---|
| **Delegated admin** | Run security services from the security account, not management. |
| **FSBP** | AWS Foundational Security Best Practices — a strong default baseline. |
| **Conformance pack** | A bundle of Config rules mapped to a framework, deployed org-wide. |
| **Finding severity** | Triage by severity + resource criticality, not volume. |

## How it fits together

`Enable org-wide` → `Findings` → `Security Hub aggregate` → `Triage` → `Route to response`

## 🔨 Hands-on lab — Enable the Detection Stack

**Platform:** AWS Organizations + AWS Skill Builder Builder Labs · **Est. time:** 4 h

1. Delegate GuardDuty + Security Hub admin to the security account
   ```bash
   aws guardduty enable-organization-admin-account --admin-account-id $SEC_ACCT
   ```
2. Auto-enable new accounts
3. Turn on Security Hub CIS + FSBP standards
4. Deploy a Config conformance pack mapped to CIS
5. Generate sample GuardDuty findings and triage them
   ```bash
   aws guardduty create-sample-findings --detector-id $DET
   ```
6. Study the matching SCS-C03 detection domain

## Prove it

**Deliverable:** P5 repo started: detection/ Terraform, a triage runbook and a findings screenshot set

Feeds the flagship project **P5 `cloud-auto-remediation`**.

**Done when:**

- [ ] GuardDuty org-wide
- [ ] Security Hub standards on
- [ ] Conformance pack deployed
- [ ] Sample finding triaged with notes

## 🎤 Interview drill

**Q — GuardDuty flags an EC2 instance beaconing to a known-bad IP. What do you do?**

> Confirm scope in Detective, isolate the instance with a quarantine security group, snapshot for forensics, rotate any credentials it held, check CloudTrail for lateral movement, and open an incident with evidence preserved to the audit bucket.

## Session deck

- [W17_Detection_Services.pptx](W17_Detection_Services.pptx)

## 🎓 Certification this month

AWS Security – Specialty (SCS-C03)
