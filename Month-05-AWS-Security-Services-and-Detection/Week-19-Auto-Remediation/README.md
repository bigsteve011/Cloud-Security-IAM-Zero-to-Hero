# Week 19 — Auto-Remediation with EventBridge, Lambda & Step Functions

**🛰️ Month 5 · AWS Security Services & Detection** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Event-driven response: EventBridge rules on findings
- Lambda remediation functions and idempotency
- Step Functions for multi-step response with approval
- Safe automation: dry-run, allow-lists and rollback
- Notification and audit of every automated action

## Learning objectives

By the end of this week you can:

- Build event-driven remediations for common misconfigurations
- Make every action logged and reversible
- Add human approval for destructive steps
- Notify Slack/Teams

## Core concepts

| Concept | In one line |
|---|---|
| **Event-driven** | Finding → EventBridge → Lambda in seconds. Faster than any human. |
| **Idempotent remediation** | Re-running must be safe; check state before acting. |
| **Guarded automation** | Allow-list resources, dry-run first, require approval for high impact. |
| **Audit trail** | Every automated action written immutably — the auditor's proof. |

## How it fits together

`Finding` → `EventBridge rule` → `Lambda/Step Fn` → `Remediate + notify` → `Immutable log`

## 🔨 Hands-on lab — Eight Remediation Playbooks

**Platform:** AWS sandbox + Terraform · **Est. time:** 6 h

1. Public S3 bucket → apply Block Public Access
2. Security group open to 0.0.0.0/0 on 22/3389 → revoke the rule
3. New IAM access key on a human user → notify + open a ticket
4. Root console login → high-priority alert
5. Disabled CloudTrail/GuardDuty → re-enable + alert
6. Wire Slack/Teams notifications and write each action to the audit bucket

## Prove it

**Deliverable:** P5: remediation/ Lambdas + Step Functions, a playbook catalogue table and notification screenshots

Feeds the flagship project **P5 `cloud-auto-remediation`**.

**Done when:**

- [ ] 8 playbooks deployed
- [ ] Each action logged immutably
- [ ] High-impact step needs approval
- [ ] Slack/Teams alerts working

## 🎤 Interview drill

**Q — When is auto-remediation unsafe?**

> When an action could cause outage or destroy evidence — e.g. terminating a compromised instance before forensics. Use guarded automation: allow-lists, reversible actions, approval gates for destructive steps, and always preserve evidence first.

## Session deck

- [W19_Auto_Remediation.pptx](W19_Auto_Remediation.pptx)

## 🎓 Certification this month

AWS Security – Specialty (SCS-C03)
