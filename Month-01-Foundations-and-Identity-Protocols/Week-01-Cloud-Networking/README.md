# Week 1 — Cloud Networking for Security Engineers

**🧱 Month 1 · Foundations & Identity Protocols** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- DNS resolution chain and DNS-based attacks (hijack, dangling CNAME takeover)
- TLS 1.3 handshake, certificates, chains of trust and mTLS
- HTTP anatomy: methods, headers, cookies, CORS and redirects
- CIDR maths, subnets, routing tables, NAT gateways
- VPN, proxies, load balancers (L4 vs L7) and where identity is enforced

## Learning objectives

By the end of this week you can:

- Read a packet capture and explain every step of an HTTPS request
- Design a /16 VPC split into public, private and isolated subnets
- Explain why identity providers depend on DNS and TLS integrity
- Set up the program lab stack and cost guardrails

## Core concepts

| Concept | In one line |
|---|---|
| **DNS** | Every SSO redirect starts with a DNS lookup. Poison it and the login page is the attacker's. |
| **TLS** | Proves the server's identity and protects tokens in transit. mTLS adds client identity. |
| **CIDR** | 10.0.0.0/16 = 65,536 addresses. Plan subnets per tier and per AZ before you build. |
| **L7 proxies** | ALBs, API gateways and reverse proxies are where tokens are validated in the cloud. |

## How it fits together

`Browser` → `DNS resolver` → `TLS handshake` → `Load balancer` → `App + IdP`

## 🔨 Hands-on lab — Lab Stack Setup & HTTPS Dissection

**Platform:** Local + AWS free tier + KodeKloud · **Est. time:** 2.5 h

1. Create AWS account, enable MFA on root, create an AWS Budget alert at $10
   ```bash
   aws budgets create-budget --account-id $ACCT --budget file://budget.json --notifications-with-subscribers file://notify.json
   ```
2. Create an Azure free account and a cost alert in Cost Management
3. Trace DNS end to end
   ```bash
   dig +trace login.microsoftonline.com
   ```
4. Inspect a TLS chain and the negotiated version
   ```bash
   openssl s_client -connect login.microsoftonline.com:443 -servername login.microsoftonline.com </dev/null | openssl x509 -noout -subject -issuer -dates
   ```
5. Watch an OIDC redirect chain with headers
   ```bash
   curl -sIL 'https://accounts.google.com/.well-known/openid-configuration'
   ```
6. Subnet practice: split 10.20.0.0/16 into 6 /20 subnets across 3 AZs
   ```bash
   python3 -c "import ipaddress;[print(s) for s in list(ipaddress.ip_network('10.20.0.0/16').subnets(new_prefix=20))[:6]]"
   ```

## Prove it

**Deliverable:** lab-01/README.md with the DNS trace, certificate chain, a subnet plan table and screenshots of both cost alerts

Feeds the flagship project **P1 `identity-protocol-lab`**.

**Done when:**

- [ ] Root MFA on AWS + budget alert live
- [ ] Azure cost alert live
- [ ] Subnet plan committed
- [ ] Can explain TLS 1.3 handshake in 2 minutes

## 🎤 Interview drill

**Q — A user reaches a fake login page even though the URL looks right. What failed?**

> DNS integrity — likely hijack, poisoned resolver or dangling-CNAME takeover. Mitigate with DNSSEC, CAA records, removing stale records and phishing-resistant auth (FIDO2 binds to origin).

## Session deck

- [W1_Cloud_Networking.pptx](W1_Cloud_Networking.pptx)
