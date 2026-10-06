# Week 28 — Agent Identity Platforms & Protocols

**🤖 Month 8 · AI Agent Identity & AI Security (Capstone)** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Why agents need first-class identities (not shared service accounts)
- Microsoft Entra Agent ID, Okta for AI Agents / Agent Gateway, Auth0 Auth for MCP
- OAuth 2.1, Token Exchange (RFC 8693) / on-behalf-of, Cross App Access (XAA)
- The MCP authorization spec
- Sender-constrained tokens (DPoP) and proof-of-possession

## Learning objectives

By the end of this week you can:

- Explain the on-behalf-of model for agents
- Register an agent as a first-class identity
- Exchange a user token for a scoped agent token
- Describe DPoP and why it matters for agents

## Core concepts

| Concept | In one line |
|---|---|
| **Agent identity** | Each agent has its own identity and human owner — auditable, revocable. |
| **On-behalf-of** | The agent acts as the user, with the user's scoped permissions, not more. |
| **Token exchange** | RFC 8693 trades one token for a narrower, short-lived one per tool. |
| **DPoP** | Binds a token to the client's key so a stolen token is useless elsewhere. |

## How it fits together

`User signs in` → `Agent identity` → `Token exchange` → `Scoped token` → `MCP tool call`

## 🔨 Hands-on lab — Register & Scope an Agent Identity

**Platform:** Entra Agent ID / Okta + Okta Learning 'Secure AI' · **Est. time:** 4.5 h

1. Register the loan-ops agent as a first-class identity with a human owner
2. Configure OAuth 2.1 for the agent client
3. Implement token exchange: user token → per-tool scoped token
4. Enforce DPoP / sender-constrained tokens
5. Complete the Okta Learning 'Secure AI with Okta' path
6. Document the agent in an inventory with its owner and scopes

## Prove it

**Deliverable:** P7 started: agent-identity/ config, token-exchange flow diagram and an agent inventory entry

Feeds the flagship project **P7 `agent-identity-gateway`**.

**Done when:**

- [ ] Agent has its own identity + owner
- [ ] Token exchange yields scoped tokens
- [ ] DPoP enforced
- [ ] Inventory entry created

## 🎤 Interview drill

**Q — An AI agent must act on behalf of employees across 3 systems — design its identity.**

> Give the agent its own first-class identity with a human owner; authenticate the user, then use OAuth 2.1 on-behalf-of/token exchange to mint short-lived, per-system, least-privilege tokens; sender-constrain them (DPoP); enforce scopes at a policy point; log every call; and certify the agent's access quarterly.

## Session deck

- [W28_Agent_Identity.pptx](W28_Agent_Identity.pptx)
