# Week 2 — Linux, PowerShell, Python & Git for Identity Automation

**🧱 Month 1 · Foundations & Identity Protocols** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Linux permissions, users, sudo, SSH keys and auditd basics
- Bash for log triage: grep, awk, jq on JSON logs
- PowerShell 7 and the Microsoft Graph PowerShell SDK
- Python: requests, boto3, msgraph-sdk, virtual environments
- Git workflow: branches, PRs, signed commits, pre-commit secret scanning

## Learning objectives

By the end of this week you can:

- Automate a read-only identity inventory across AWS and Entra ID
- Parse CloudTrail JSON with jq
- Use signed commits and a secret scanner on every repo
- Write reusable Python with typed functions and tests

## Core concepts

| Concept | In one line |
|---|---|
| **jq** | Your first SIEM. Filter CloudTrail: jq '.Records[] | select(.eventName=="ConsoleLogin")'. |
| **Graph SDK** | One API for users, groups, apps and Conditional Access in Entra ID. |
| **boto3** | Python access to every AWS API. Read-only first: iam.list_users(). |
| **pre-commit** | gitleaks runs before every commit, so secrets never reach GitHub. |

## How it fits together

`Write script` → `gitleaks scan` → `Signed commit` → `PR review` → `Merge`

## 🔨 Hands-on lab — Identity Inventory Script

**Platform:** Local + AWS + Entra free tenant · **Est. time:** 3 h

1. Create a Python venv and install the SDKs
   ```bash
   python3 -m venv .venv && source .venv/bin/activate && pip install boto3 msgraph-sdk azure-identity
   ```
2. List AWS IAM users with last-used keys
   ```bash
   aws iam generate-credential-report && aws iam get-credential-report --query Content --output text | base64 -d > cred.csv
   ```
3. Connect to Entra ID with Graph PowerShell
   ```bash
   Connect-MgGraph -Scopes 'User.Read.All','AuditLog.Read.All'; Get-MgUser -All -Property signInActivity | Select DisplayName,@{n='Last';e={$_.SignInActivity.LastSignInDateTime}}
   ```
4. Install pre-commit + gitleaks
   ```bash
   pip install pre-commit && pre-commit install
   ```
5. Configure SSH-signed commits
   ```bash
   git config --global gpg.format ssh && git config --global user.signingkey ~/.ssh/id_ed25519.pub && git config --global commit.gpgsign true
   ```
6. Merge both outputs into inventory.csv with a Python script

## Prove it

**Deliverable:** inventory/ folder: inventory.py, a test, .pre-commit-config.yaml and a sample (sanitised) output

Feeds the flagship project **P1 `identity-protocol-lab`**.

**Done when:**

- [ ] gitleaks blocks a planted fake key
- [ ] Commits show 'Verified' on GitHub
- [ ] Script runs against both clouds
- [ ] jq one-liner for ConsoleLogin saved

## 🎤 Interview drill

**Q — How do you stop engineers committing secrets?**

> Layers: pre-commit gitleaks, GitHub push protection + secret scanning, short-lived credentials (OIDC) so nothing long-lived exists, and an automated revoke playbook if one leaks.

## Session deck

- [W2_Scripting_Git.pptx](W2_Scripting_Git.pptx)
