# Week 18 — KMS, Secrets Manager, Macie & Data Protection

**🛰️ Month 5 · AWS Security Services & Detection** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- KMS key policies, grants, envelope encryption and key rotation
- Secrets Manager rotation vs long-lived secrets
- Macie for sensitive-data discovery in S3
- VPC endpoints and endpoint policies
- WAF basics for identity-aware protection

## Learning objectives

By the end of this week you can:

- Design a least-privilege KMS key policy
- Rotate a database secret automatically
- Discover PII in S3 with Macie
- Lock data access to VPC endpoints

## Core concepts

| Concept | In one line |
|---|---|
| **Key policy** | The root of KMS authorisation. Grant decrypt narrowly, by role and condition. |
| **Envelope encryption** | Data key encrypts data; KMS encrypts the data key. Scales and audits well. |
| **Rotation** | Secrets Manager rotates credentials on a schedule via a Lambda. |
| **Endpoint policy** | Restrict which principals/resources a VPC endpoint will serve. |

## How it fits together

`Create CMK` → `Scoped key policy` → `Encrypt data` → `Rotate secrets` → `Audit via CloudTrail`

## 🔨 Hands-on lab — Encryption & Secret Rotation

**Platform:** AWS sandbox + Tutorials Dojo PlayCloud · **Est. time:** 4 h

1. Create a CMK with a least-privilege key policy
   ```bash
   aws kms create-key --description wisla-data --policy file://key-policy.json
   ```
2. Enable automatic annual rotation
   ```bash
   aws kms enable-key-rotation --key-id $KEY
   ```
3. Store and auto-rotate an RDS secret
4. Run a Macie job over a test S3 bucket with synthetic PII
5. Add an S3 VPC endpoint with a restrictive endpoint policy
6. Take a Tutorials Dojo SCS-C03 practice set on data protection

## Prove it

**Deliverable:** P5: data-protection/ Terraform, key-policy rationale and a Macie findings summary

Feeds the flagship project **P5 `cloud-auto-remediation`**.

**Done when:**

- [ ] CMK rotation on
- [ ] Secret rotates on schedule
- [ ] Macie finds synthetic PII
- [ ] S3 reachable only via endpoint

## 🎤 Interview drill

**Q — How does envelope encryption work and why use it?**

> A data key encrypts the data locally; KMS encrypts that data key with a CMK. Only the small data key touches KMS, so it scales, every use is audited in CloudTrail, and rotating the CMK does not require re-encrypting all data.

## Session deck

- [W18_Data_Protection.pptx](W18_Data_Protection.pptx)

## 🎓 Certification this month

AWS Security – Specialty (SCS-C03)
