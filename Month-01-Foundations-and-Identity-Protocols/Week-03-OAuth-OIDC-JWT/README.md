# Week 3 — OAuth 2.0/2.1, OIDC & JWT Deep Dive

**🧱 Month 1 · Foundations & Identity Protocols** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- OAuth roles: resource owner, client, authorization server, resource server
- Grant types: Authorization Code + PKCE, Client Credentials, Device Code; why Implicit and ROPC are gone in 2.1
- OIDC: ID token vs access token, discovery document, JWKS, nonce and state
- JWT anatomy and validation: iss, aud, exp, nbf, signature, kid rotation
- Attacks: alg=none, RS256→HS256 confusion, token replay, open redirect, code interception

## Learning objectives

By the end of this week you can:

- Draw the Authorization Code + PKCE flow from memory
- Validate a JWT by hand and in code
- Explain why access tokens must never be used as identity proof
- Build an OIDC client from scratch

## Core concepts

| Concept | In one line |
|---|---|
| **PKCE** | code_verifier → SHA-256 → code_challenge. Stops an intercepted code being redeemed. |
| **ID token** | Who the user is, for the client. Audience = the client ID. |
| **Access token** | What the client may do, for the API. Audience = the API. |
| **JWKS** | The IdP's public keys. Validate the signature with the key matching 'kid'. |

## How it fits together

`Client + PKCE` → `/authorize` → `User auth + consent` → `Code → /token` → `Validate ID token`

## 🔨 Hands-on lab — OIDC Client from Scratch

**Platform:** Local Python + Entra ID + Okta developer org · **Est. time:** 4 h

1. Register an app in Entra ID (redirect http://localhost:5000/callback)
   ```bash
   az ad app create --display-name p1-oidc-lab --web-redirect-uris http://localhost:5000/callback
   ```
2. Create a free Okta Integrator org and an OIDC web app
3. Fetch the discovery document and JWKS
   ```bash
   curl -s https://login.microsoftonline.com/$TENANT/v2.0/.well-known/openid-configuration | jq '.jwks_uri,.issuer'
   ```
4. Generate a PKCE verifier/challenge in Python
   ```bash
   python3 -c "import secrets,hashlib,base64;v=secrets.token_urlsafe(64);print(v);print(base64.urlsafe_b64encode(hashlib.sha256(v.encode()).digest()).rstrip(b'=').decode())"
   ```
5. Build Flask /login and /callback; validate with PyJWT (iss, aud, exp, nonce)
   ```bash
   pip install flask requests pyjwt[crypto]
   ```
6. Attack yourself: send a token with alg=none and confirm rejection

## Prove it

**Deliverable:** P1 repo started: oidc/ module with PKCE login against both IdPs and a token-inspector page

Feeds the flagship project **P1 `identity-protocol-lab`**.

**Done when:**

- [ ] Login works against Entra ID and Okta
- [ ] Rejects expired, wrong-aud and alg=none tokens
- [ ] Mermaid diagram in README
- [ ] Can explain ID vs access token

## 🎤 Interview drill

**Q — Walk me through OIDC Auth Code + PKCE. Where can it be attacked?**

> Client sends challenge → user authenticates → code returned to redirect URI → client redeems code + verifier. Attack points: redirect URI manipulation, code interception (PKCE fixes), CSRF (state), replay (nonce), weak token validation (alg confusion).

## Session deck

- [W3_OAuth_OIDC_JWT.pptx](W3_OAuth_OIDC_JWT.pptx)
