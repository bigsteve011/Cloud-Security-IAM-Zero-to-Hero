# 🔑 Month 7 — Workload Identity, Kubernetes & Identity Threat Detection

*Apr–May 2027*

[← Back to program](../README.md)


## Flagship project — P6: Zero-Static-Secrets & Identity Threat Detection Pack

`zero-static-secrets + identity-detection-pack`

A demo workload on EKS/AKS where CI/CD, pods and functions authenticate with zero long-lived credentials, plus a pack of twelve identity detections mapped to MITRE ATT&CK with reproduction steps and response playbooks.

**Deliverables**

- Demo app on EKS/AKS (or kind) with zero long-lived credentials
- GitHub OIDC, EKS Pod Identity/IRSA and Azure workload identity federation
- Secrets scanner proving no static secrets exist
- Vault dynamic secrets for the one unavoidable legacy case
- 12 identity detections (KQL + Sigma + CloudTrail) with ATT&CK mapping
- Per-detection: reproduction steps, sample logs, FP/TP notes, response playbook

**Compliance mapping**

| Control | Requirement |
|---|---|
| ISO 27001:2022 A.8.5 | Secure authentication |
| ISO 27001:2022 A.8.16 | Monitoring activities |
| NIS2 Art. 21(2)(i) | Access control and asset management |
| DORA Art. 10 | Detection of anomalous activities |

## Weeks

| Week | Topic | Lab | Deck |
|---|---|---|---|
| **24** | [Non-Human Identity & Workload Identity Federation](Week-24-Workload-Identity/) | Keyless Workloads | [pptx](Week-24-Workload-Identity/W24_Workload_Identity.pptx) |
| **25** | [Kubernetes Security: RBAC, Pod Security & Admission Control](Week-25-Kubernetes-Security/) | Harden the Cluster | [pptx](Week-25-Kubernetes-Security/W25_Kubernetes_Security.pptx) |
| **26** | [Identity Attack Techniques & MITRE ATT&CK](Week-26-Identity-Attacks/) | Attack-Path Analysis & Detection Design | [pptx](Week-26-Identity-Attacks/W26_Identity_Attacks.pptx) |
| **27** | [Writing Detections: KQL, Sigma & the Detection Pack](Week-27-Detection-Engineering/) | Build the 12-Detection Pack | [pptx](Week-27-Detection-Engineering/W27_Detection_Engineering.pptx) |
