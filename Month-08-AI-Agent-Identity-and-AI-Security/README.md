# 🤖 Month 8 — AI Agent Identity & AI Security (Capstone)

*May–Jun 2027*

[← Back to program](../README.md)


## Flagship project — P7: Agent Identity Gateway for Wisła Bank ⭐

`agent-identity-gateway`

The headline capstone: an AI agent that acts on behalf of a signed-in employee through MCP tools, with a policy enforcement point, short-lived scoped tokens, a red-team section and an ISO 42001 / EU AI Act governance pack.

**Deliverables**

- AI agent (loan-ops assistant) calling MCP tools on behalf of a user
- MCP server protected by OAuth 2.1; agent registered as a first-class identity
- Short-lived scoped tokens via token exchange; per-tool least privilege
- Policy enforcement point: deny out-of-scope calls, approval for high-risk, kill switch
- Red-team section: indirect prompt injection → blocked by identity control
- Governance pack: agent inventory, human owner, quarterly certification, ISO 42001 / EU AI Act mapping

**Compliance mapping**

| Control | Requirement |
|---|---|
| ISO/IEC 42001 | AI management system |
| EU AI Act | Deployer obligations |
| ISO 27001:2022 A.5.15/A.8.2 | Access control / privileged access (for agents) |
| NIST AI RMF | Govern, Map, Measure, Manage |

## Weeks

| Week | Topic | Lab | Deck |
|---|---|---|---|
| **28** | [Agent Identity Platforms & Protocols](Week-28-Agent-Identity/) | Register & Scope an Agent Identity | [pptx](Week-28-Agent-Identity/W28_Agent_Identity.pptx) |
| **29** | [MCP Security & the Policy Enforcement Point](Week-29-MCP-Security/) | Secure MCP Server + PEP | [pptx](Week-29-MCP-Security/W29_MCP_Security.pptx) |
| **30** | [AI Threats, Red-Teaming & AI Governance](Week-30-AI-Threats-Governance/) | Red-Team the Agent + Governance Pack | [pptx](Week-30-AI-Threats-Governance/W30_AI_Threats_Governance.pptx) |
