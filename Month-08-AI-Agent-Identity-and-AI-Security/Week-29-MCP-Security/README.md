# Week 29 — MCP Security & the Policy Enforcement Point

**🤖 Month 8 · AI Agent Identity & AI Security (Capstone)** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- MCP architecture: servers, tools, resources and the authorization spec
- Securing an MCP server with OAuth 2.1 and scoped tokens
- Per-tool least privilege and consent
- Policy enforcement point: out-of-scope deny, high-risk approval, kill switch
- Logging and audit of every tool invocation

## Learning objectives

By the end of this week you can:

- Protect an MCP server with OAuth 2.1
- Enforce per-tool least privilege
- Build a policy enforcement point in front of tools
- Log every invocation for audit

## Core concepts

| Concept | In one line |
|---|---|
| **MCP server** | Exposes tools/resources to agents. Must authenticate and authorise every call. |
| **Per-tool scope** | The DB-read tool cannot write; the ticket tool cannot touch customers. |
| **PEP** | A gate before tools: checks scope, risk and approval before the call runs. |
| **Kill switch** | One control disables the agent instantly across all tools. |

## How it fits together

`Agent call` → `PEP: scope check` → `Risk / approval` → `Tool executes` → `Audit log`

## 🔨 Hands-on lab — Secure MCP Server + PEP

**Platform:** Local MCP server + OAuth 2.1 + Python · **Est. time:** 6 h

1. Build an MCP server exposing read-ticket and query-customer tools
2. Protect it with OAuth 2.1; validate scoped tokens on every call
3. Implement a PEP: deny out-of-scope, require approval for high-risk, expose a kill switch
4. Give each tool a distinct least-privilege scope
5. Log every invocation (who, which tool, args hash, decision) immutably
6. Test that an over-scoped call is denied

## Prove it

**Deliverable:** P7: mcp-server/ with OAuth 2.1, a policy enforcement point and an immutable invocation log

Feeds the flagship project **P7 `agent-identity-gateway`**.

**Done when:**

- [ ] MCP server rejects unscoped calls
- [ ] High-risk action needs approval
- [ ] Kill switch works
- [ ] Every call logged

## 🎤 Interview drill

**Q — How do you stop an AI agent doing more than it should?**

> Least-privilege per-tool scopes, a policy enforcement point that denies out-of-scope calls and requires human approval for high-risk actions, short-lived tokens, a kill switch, and full audit logging — identity and authorization controls, not prompt instructions, are what actually constrain it.

## Session deck

- [W29_MCP_Security.pptx](W29_MCP_Security.pptx)
