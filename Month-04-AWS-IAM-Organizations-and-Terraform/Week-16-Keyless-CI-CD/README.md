# Week 16 — Keyless CI/CD with GitHub OIDC & Policy-as-Code

**☁️ Month 4 · AWS IAM, Organizations & Terraform** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- GitHub Actions OIDC federation with AWS (no stored keys)
- IaC scanning: Checkov and Trivy
- Policy-as-code gates with OPA/Conftest
- Pipeline design: plan → scan → policy → approval → apply
- Protecting state and requiring manual approval for prod

## Learning objectives

By the end of this week you can:

- Replace stored AWS keys with OIDC role assumption
- Gate Terraform with Checkov, Trivy and OPA
- Require human approval before apply
- Ship P4 Part 1

## Core concepts

| Concept | In one line |
|---|---|
| **OIDC in CI** | GitHub presents a signed token; AWS trusts it for a scoped role. No secret stored. |
| **Checkov** | Scans Terraform for misconfigurations before they deploy. |
| **Conftest/OPA** | Rego policies that fail the build on violations (e.g. unencrypted bucket). |
| **Approval gate** | GitHub Environments require a reviewer before the apply job runs. |

## How it fits together

`PR` → `terraform plan` → `Checkov + Trivy` → `OPA gate` → `Approve → apply`

## 🔨 Hands-on lab — OIDC Pipeline with Policy Gates

**Platform:** GitHub Actions + AWS + Checkov/OPA · **Est. time:** 5 h

1. Create an IAM OIDC provider for token.actions.githubusercontent.com
2. Create a deploy role trusting the repo+branch via the sub claim
   ```bash
   StringLike: token.actions.githubusercontent.com:sub = repo:bigsteve011/secure-landing-zone:ref:refs/heads/main
   ```
3. Write the workflow: plan on PR, apply on main after approval
   ```bash
   permissions: { id-token: write, contents: read }
   ```
4. Add Checkov and Trivy steps
   ```bash
   pip install checkov && checkov -d . --compact
   ```
5. Add a Conftest/OPA gate
   ```bash
   conftest test plan.json -p policy/
   ```
6. Add a GitHub Environment protection rule requiring a reviewer

## Prove it

**Deliverable:** P4 Part 1 complete: pipeline YAML, OPA policies, README with architecture diagram and control mapping

Feeds the flagship project **P4 `secure-landing-zone`**.

**Done when:**

- [ ] No AWS keys in GitHub secrets
- [ ] Checkov + OPA fail a bad plan
- [ ] Apply needs approval
- [ ] LinkedIn post drafted on keyless IaC

## 🎤 Interview drill

**Q — Remove static AWS keys from a CI pipeline — how?**

> Use GitHub OIDC: configure an IAM OIDC provider, a role with a trust policy scoped to the repo/branch/environment sub claim, request id-token: write in the workflow, assume the role at runtime for short-lived credentials, and delete all stored access keys.

## Session deck

- [W16_Keyless_CI_CD.pptx](W16_Keyless_CI_CD.pptx)
