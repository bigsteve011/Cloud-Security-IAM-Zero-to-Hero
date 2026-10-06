# Week 24 — Non-Human Identity & Workload Identity Federation

**🔑 Month 7 · Workload Identity, Kubernetes & Identity Threat Detection** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- The NHI problem: service accounts, API keys, machine credentials at scale
- GitHub Actions OIDC, EKS Pod Identity / IRSA, Azure workload identity federation
- SPIFFE/SPIRE concepts and workload attestation
- HashiCorp Vault dynamic secrets
- Inventorying and rotating non-human identities

## Learning objectives

By the end of this week you can:

- Explain why NHIs outnumber humans and why that is a risk
- Federate a workload to AWS and Azure without static keys
- Issue a short-lived dynamic secret from Vault
- Inventory NHIs across the estate

## Core concepts

| Concept | In one line |
|---|---|
| **NHI** | Machines, pipelines, pods, agents — now most identities and often the least governed. |
| **IRSA / Pod Identity** | A Kubernetes service account maps to an IAM role; pods get short-lived creds. |
| **SPIFFE** | A standard workload identity (SVID) issued after attestation. |
| **Dynamic secret** | Vault creates a credential on demand with a short TTL, then revokes it. |

## How it fits together

`Workload` → `Attest / OIDC token` → `Exchange` → `Short-lived credential` → `Auto-expire`

## 🔨 Hands-on lab — Keyless Workloads

**Platform:** kind/EKS/AKS + Vault + KodeKloud · **Est. time:** 5 h

1. Stand up a cluster (kind locally or EKS/AKS)
   ```bash
   kind create cluster --name wisla
   ```
2. Configure IRSA / Pod Identity so a pod assumes an IAM role
3. Configure Azure workload identity federation for a second workload
4. Run Vault dev and issue a dynamic database credential
   ```bash
   vault secrets enable database && vault read database/creds/readonly
   ```
5. Build an NHI inventory script across both clouds
6. Complete a KodeKloud Kubernetes module

## Prove it

**Deliverable:** P6 Part A started: workload-identity/ manifests, Vault config and an NHI inventory

Feeds the flagship project **P6 `zero-static-secrets + identity-detection-pack`**.

**Done when:**

- [ ] Pod authenticates with no stored secret
- [ ] Azure workload federated
- [ ] Vault issues a TTL'd secret
- [ ] NHI inventory generated

## 🎤 Interview drill

**Q — Remove every long-lived credential from our pipelines — approach?**

> Inventory all NHIs and secrets, move CI to OIDC, pods to IRSA/workload identity, and remaining cases to Vault dynamic secrets; add a scanner to block new static secrets, rotate and retire the old ones, and monitor for any reintroduced.

## Session deck

- [W24_Workload_Identity.pptx](W24_Workload_Identity.pptx)
