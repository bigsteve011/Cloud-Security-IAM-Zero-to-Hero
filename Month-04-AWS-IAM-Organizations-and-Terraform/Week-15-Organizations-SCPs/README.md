# Week 15 — AWS Organizations, Control Tower & SCP Guardrails

**☁️ Month 4 · AWS IAM, Organizations & Terraform** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Organization structure: management, security, log-archive, workload OUs
- Control Tower landing-zone concepts and guardrails
- SCP design patterns: region lock, root protection, service protection
- Organization CloudTrail and immutable log archive
- RCPs for resource-level org guardrails

## Learning objectives

By the end of this week you can:

- Build the org structure in Terraform
- Write and attach SCP guardrails
- Centralise CloudTrail to an immutable bucket
- Validate guardrails from a workload account

## Core concepts

| Concept | In one line |
|---|---|
| **Log archive** | Separate account, Object Lock on the bucket. Even admins cannot alter logs. |
| **Region lock** | SCP denying all regions except eu-central-1/eu-west-1 — data residency + blast radius. |
| **Root protection** | SCP denying root-user actions in member accounts. |
| **Service protection** | Deny cloudtrail:StopLogging, guardduty:DeleteDetector org-wide. |

## How it fits together

`Management` → `Security OU` → `Log-archive OU` → `Workload OU` → `SCPs attached`

## 🔨 Hands-on lab — Org + SCP Guardrails in Terraform

**Platform:** AWS Organizations + Terraform · **Est. time:** 5 h

1. Define the organization, OUs and member accounts in Terraform
   ```bash
   resource "aws_organizations_organizational_unit" "security" { name = "Security" parent_id = aws_organizations_organization.this.roots[0].id }
   ```
2. Write SCPs: region lock, deny root, protect CloudTrail/GuardDuty, deny public S3
3. Attach SCPs to OUs and apply
   ```bash
   terraform apply
   ```
4. Create an org CloudTrail delivering to a log-archive bucket with Object Lock
5. From a workload account, confirm a disallowed region is blocked
   ```bash
   AWS_PROFILE=workload aws ec2 describe-instances --region us-east-1   # expect AccessDenied
   ```
6. Confirm StopLogging is denied
   ```bash
   AWS_PROFILE=workload aws cloudtrail stop-logging --name org-trail   # expect AccessDenied
   ```

## Prove it

**Deliverable:** P4: organizations/ Terraform module, SCP matrix and guardrail test evidence

Feeds the flagship project **P4 `secure-landing-zone`**.

**Done when:**

- [ ] Org + OUs created as code
- [ ] SCP blocks non-EU region
- [ ] CloudTrail cannot be stopped
- [ ] Log bucket has Object Lock

## 🎤 Interview drill

**Q — How do SCPs and IAM policies interact?**

> SCPs set the maximum available permissions for an account; IAM policies grant within that ceiling. An action needs an Allow in IAM and no Deny in any SCP. SCPs never grant on their own.

## Session deck

- [W15_Organizations_SCPs.pptx](W15_Organizations_SCPs.pptx)
