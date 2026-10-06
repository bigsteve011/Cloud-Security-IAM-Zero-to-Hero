# Week 12 — Hygiene Scanner, Evidence Packs & AI-Assisted Reviews → SC-300

**⚖️ Month 3 · Identity Governance, PAM & Automation** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Identity hygiene metrics: stale, orphaned, MFA gaps, dormant privilege
- Generating timestamped evidence auditors accept
- LLM-assisted review summaries: prompt design and data minimisation
- Human-in-the-loop approval and logging of AI output
- SC-300 exam strategy and practice assessment

## Learning objectives

By the end of this week you can:

- Ship the hygiene scanner and evidence pack
- Add an AI summary with mandatory approval
- Score 80%+ on the SC-300 practice assessment
- Book and pass SC-300

## Core concepts

| Concept | In one line |
|---|---|
| **Stale account** | No sign-in for 90 days. Disable, then delete after 30. |
| **Evidence pack** | Report + raw data + hash + timestamp + scope statement. |
| **Human in the loop** | AI drafts, a named human decides; both are logged. |
| **Data minimisation** | Send the LLM only what the summary needs. No secrets, no PII beyond need. |

## How it fits together

`Collect` → `Analyse` → `AI summary` → `Human approval` → `Signed evidence`

## 🔨 Hands-on lab — Evidence Pack + AI Summary

**Platform:** Local Python + Claude API + Microsoft Learn · **Est. time:** 5 h

1. Implement scanner checks and output findings.json
   ```bash
   python -m hygiene scan --out findings.json
   ```
2. Render HTML evidence with Jinja2 and hash it
   ```bash
   sha256sum evidence-2027-01-15.html > evidence-2027-01-15.sha256
   ```
3. Call an LLM to summarise findings for reviewers
   ```bash
   pip install anthropic
   ```
4. Require approve/reject CLI step; log reviewer and decision
5. Take the SC-300 practice assessment on Microsoft Learn
6. Book the SC-300 exam

## Prove it

**Deliverable:** P3 complete with sample evidence pack, architecture diagram and LinkedIn post on audit-ready IAM

Feeds the flagship project **P3 `iam-governance-engine`**.

**Done when:**

- [ ] Evidence pack generated + hashed
- [ ] AI output never applied without approval
- [ ] SC-300 practice ≥ 80%
- [ ] SC-300 passed 🎓

## 🎤 Interview drill

**Q — How would you safely use an LLM in access reviews?**

> Minimised input, summarisation only, no autonomous changes, mandatory human decision, prompt and output logged, accuracy spot-checks, and documented in the AI risk register (ISO 42001).

## Session deck

- [W12_Evidence_SC_300.pptx](W12_Evidence_SC_300.pptx)

## 🎓 Certification this month

SC-300 Identity & Access Administrator
