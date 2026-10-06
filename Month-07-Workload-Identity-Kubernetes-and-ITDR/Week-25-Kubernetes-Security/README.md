# Week 25 — Kubernetes Security: RBAC, Pod Security & Admission Control

**🔑 Month 7 · Workload Identity, Kubernetes & Identity Threat Detection** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Kubernetes RBAC: roles, bindings, service accounts
- Pod Security Standards (restricted/baseline)
- Admission control with Kyverno / OPA Gatekeeper
- Secrets handling and the zero-static-secrets pattern in-cluster
- Network policies and workload isolation

## Learning objectives

By the end of this week you can:

- Lock down cluster RBAC to least privilege
- Enforce Pod Security Standards
- Write Kyverno policies that block risky pods
- Prove no static secrets exist in-cluster

## Core concepts

| Concept | In one line |
|---|---|
| **Cluster RBAC** | Bind the narrowest role to each service account; avoid cluster-admin. |
| **Pod Security** | restricted blocks privileged pods, host mounts and root by default. |
| **Admission control** | Kyverno/Gatekeeper reject non-compliant manifests at apply time. |
| **Network policy** | Default-deny, then allow only required pod-to-pod traffic. |

## How it fits together

`Manifest` → `Admission (Kyverno)` → `RBAC check` → `Pod Security` → `Network policy`

## 🔨 Hands-on lab — Harden the Cluster

**Platform:** kind/EKS + Kyverno + KodeKloud · **Est. time:** 5 h

1. Audit current RBAC and remove wildcard permissions
   ```bash
   kubectl get clusterrolebindings -o json | jq '.items[] | select(.roleRef.name=="cluster-admin")'
   ```
2. Apply the restricted Pod Security Standard to a namespace
   ```bash
   kubectl label ns wisla-app pod-security.kubernetes.io/enforce=restricted
   ```
3. Install Kyverno and block privileged + :latest image pods
4. Add a default-deny NetworkPolicy, then allow required flows
5. Run a secrets scanner over manifests and the cluster
   ```bash
   kubectl get secrets -A && trivy k8s --report summary cluster
   ```
6. Complete a KodeKloud K8s security lab

## Prove it

**Deliverable:** P6: k8s-security/ Kyverno policies, RBAC audit and a scanner report

Feeds the flagship project **P6 `zero-static-secrets + identity-detection-pack`**.

**Done when:**

- [ ] No cluster-admin bindings for apps
- [ ] Restricted PSS enforced
- [ ] Kyverno blocks a bad pod
- [ ] Scanner finds no static secrets

## 🎤 Interview drill

**Q — How do you stop a compromised pod becoming a cluster compromise?**

> Least-privilege RBAC and service accounts, restricted Pod Security, default-deny network policies, no node/host mounts, short-lived workload identity instead of stored secrets, admission control, and runtime detection on anomalous API calls.

## Session deck

- [W25_Kubernetes_Security.pptx](W25_Kubernetes_Security.pptx)
