# Week 13 — AWS IAM Policy Evaluation Logic

**☁️ Month 4 · AWS IAM, Organizations & Terraform** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Principals, actions, resources, conditions; policy JSON anatomy
- Identity vs resource policies; explicit deny always wins
- Permission boundaries and session policies
- SCPs and RCPs as organisation-wide ceilings
- Debugging AccessDenied with CloudTrail and the policy simulator

## Learning objectives

By the end of this week you can:

- Predict the outcome of any multi-layer policy evaluation
- Write least-privilege policies with conditions
- Debug a real AccessDenied in under 10 minutes
- Recognise and remediate common privilege-escalation misconfigurations

## Core concepts

| Concept | In one line |
|---|---|
| **Explicit deny** | Any matching Deny in any layer ends evaluation. No Allow overrides it. |
| **Boundary** | A ceiling on what an identity policy can grant. Great for delegated admin. |
| **SCP** | Restricts accounts, never grants. Even root is bound by it. |
| **Condition keys** | aws:SourceIp, aws:PrincipalOrgID, aws:RequestedRegion — precision tools. |

## How it fits together

`Explicit deny?` → `SCP / RCP allow?` → `Resource policy` → `Boundary + session` → `Identity policy`

## 🔨 Hands-on lab — Finding & Fixing Risky IAM Permissions

**Platform:** AWS sandbox account + IAM Access Analyzer · **Est. time:** 5 h

1. Enable IAM Access Analyzer for the account
   ```bash
   aws accessanalyzer create-analyzer --analyzer-name wisla-lab --type ACCOUNT
   ```
2. Generate a credential report and flag unused keys and permissions
   ```bash
   aws iam generate-credential-report && aws iam get-credential-report --query Content --output text | base64 -d > cred.csv
   ```
3. Review the escalation patterns documented by IAM Vulnerable (BishopFox) as a defender — understand why iam:CreatePolicyVersion and iam:PassRole are dangerous, then write detections for them
4. Use the policy simulator to confirm a least-privilege policy denies the risky action
   ```bash
   aws iam simulate-principal-policy --policy-source-arn $ROLE --action-names iam:CreatePolicyVersion
   ```
5. Add a permission boundary that caps what delegated admins can grant
6. Write an Access Analyzer finding triage note for each result

## Prove it

**Deliverable:** P4 repo started: iam/ folder with least-privilege policies, a permission boundary and a privilege-escalation detection checklist

Feeds the flagship project **P4 `secure-landing-zone`**.

**Done when:**

- [ ] Access Analyzer enabled
- [ ] Unused credentials identified
- [ ] Boundary caps delegated grants
- [ ] Detection checklist for known escalation paths written

## 🎤 Interview drill

**Q — A user has AdministratorAccess but gets AccessDenied — debug it.**

> Check for an explicit deny in an SCP or boundary, the requested region against a region-restriction SCP, a resource policy denying the principal, a session policy, and a service-control condition. Explicit deny anywhere wins; trace it with CloudTrail and the policy simulator.

## Session deck

- [W13_IAM_Policy_Logic.pptx](W13_IAM_Policy_Logic.pptx)
