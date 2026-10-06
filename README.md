# Cloud Security & IAM — Zero to Hero

> **A 9-month, build-first training program that turns a GRC / infosec background into a hireable IAM & Cloud Security Engineer** — 32 weekly sessions, 7 flagship portfolio projects, 3 certifications, and a slide deck + hands-on lab for every week.

Every build maps to one regulated enterprise — **Wisła Bank** (EU bank, 2,000 staff, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents) — so the portfolio reads as one coherent program, not scattered tutorials. Every repo ships a control-mapping table (ISO 27001:2022, NIS2, DORA, ISO 42001).

---

## Program design principles

1. **Build first, certify second.** Every month ends with a project pushed to GitHub. Certs back up what the repo already proves.
2. **One identity spine through everything.** All projects use Wisła Bank.
3. **Compliance-mapped by default.** Every repo maps to ISO 27001:2022, NIS2, DORA and ISO 42001 — the differentiator auditors and hiring managers notice.
4. **AI throughout, not bolted on.** AI as a coding/analysis assistant from Week 1; the capstone secures AI agents as identities.

---

## Roadmap at a glance

**🧱 Foundations → 🏛️ Entra/AD/Okta → ⚖️ Governance → ☁️ AWS → 🛰️ Detection → 🔷 Azure → 🔑 Workload ID → 🤖 Agent Identity → 🎯 Career**

| Month | Theme | Weeks | Flagship project | Cert |
|:--:|---|:--:|---|:--:|
| 🧱 **1** | [Foundations & Identity Protocols](Month-01-Foundations-and-Identity-Protocols/) | [1](Month-01-Foundations-and-Identity-Protocols/Week-01-Cloud-Networking/)–[4](Month-01-Foundations-and-Identity-Protocols/Week-04-SAML-SCIM-FIDO2/) | P1: `identity-protocol-lab` | — |
| 🏛️ **2** | [Entra ID, Hybrid AD & Okta](Month-02-Entra-ID-Hybrid-AD-and-Okta/) | [5](Month-02-Entra-ID-Hybrid-AD-and-Okta/Week-05-Active-Directory/)–[8](Month-02-Entra-ID-Hybrid-AD-and-Okta/Week-08-Okta-Migration/) | P2: `hybrid-identity-zero-trust` | — |
| ⚖️ **3** | [Identity Governance, PAM & Automation](Month-03-Identity-Governance-PAM-and-Automation/) | [9](Month-03-Identity-Governance-PAM-and-Automation/Week-09-Entra-Governance/)–[12](Month-03-Identity-Governance-PAM-and-Automation/Week-12-Evidence-SC-300/) | P3: `iam-governance-engine` | SC-300 |
| ☁️ **4** | [AWS IAM, Organizations & Terraform](Month-04-AWS-IAM-Organizations-and-Terraform/) | [13](Month-04-AWS-IAM-Organizations-and-Terraform/Week-13-IAM-Policy-Logic/)–[16](Month-04-AWS-IAM-Organizations-and-Terraform/Week-16-Keyless-CI-CD/) | P4: `secure-landing-zone` | — |
| 🛰️ **5** | [AWS Security Services & Detection](Month-05-AWS-Security-Services-and-Detection/) | [17](Month-05-AWS-Security-Services-and-Detection/Week-17-Detection-Services/)–[20](Month-05-AWS-Security-Services-and-Detection/Week-20-Simulation-SCS-C03/) | P5: `cloud-auto-remediation` | AWS |
| 🔷 **6** | [Azure Security & Policy-as-Code](Month-06-Azure-Security-and-Policy-as-Code/) | [21](Month-06-Azure-Security-and-Policy-as-Code/Week-21-Azure-Governance/)–[23](Month-06-Azure-Security-and-Policy-as-Code/Week-23-Unified-Dashboard/) | P4b: `secure-landing-zone` | SC-500 |
| 🔑 **7** | [Workload Identity, Kubernetes & Identity Threat Detection](Month-07-Workload-Identity-Kubernetes-and-ITDR/) | [24](Month-07-Workload-Identity-Kubernetes-and-ITDR/Week-24-Workload-Identity/)–[27](Month-07-Workload-Identity-Kubernetes-and-ITDR/Week-27-Detection-Engineering/) | P6: `zero-static-secrets + identity-detection-pack` | — |
| 🤖 **8** | [AI Agent Identity & AI Security (Capstone)](Month-08-AI-Agent-Identity-and-AI-Security/) | [28](Month-08-AI-Agent-Identity-and-AI-Security/Week-28-Agent-Identity/)–[30](Month-08-AI-Agent-Identity-and-AI-Security/Week-30-AI-Threats-Governance/) | P7: `agent-identity-gateway` | — |
| 🎯 **9** | [Portfolio, Positioning & Job Search](Month-09-Portfolio-Positioning-and-Job-Search/) | [31](Month-09-Portfolio-Positioning-and-Job-Search/Week-31-Portfolio-Site/)–[32](Month-09-Portfolio-Positioning-and-Job-Search/Week-32-Interviews-Search/) | P0: `portfolio-site` | — |

> 💡 Click any month or week to open its folder, labs, and slide deck.

---

## All 32 sessions

### 🧱 Month 1 — Foundations & Identity Protocols  <sub>Oct–Nov 2026</sub>

- **[Week 1 — Cloud Networking for Security Engineers](Month-01-Foundations-and-Identity-Protocols/Week-01-Cloud-Networking/)** · lab: Lab Stack Setup & HTTPS Dissection
- **[Week 2 — Linux, PowerShell, Python & Git for Identity Automation](Month-01-Foundations-and-Identity-Protocols/Week-02-Scripting-Git/)** · lab: Identity Inventory Script
- **[Week 3 — OAuth 2.0/2.1, OIDC & JWT Deep Dive](Month-01-Foundations-and-Identity-Protocols/Week-03-OAuth-OIDC-JWT/)** · lab: OIDC Client from Scratch
- **[Week 4 — SAML 2.0, SCIM 2.0, FIDO2/Passkeys & Terraform Basics](Month-01-Foundations-and-Identity-Protocols/Week-04-SAML-SCIM-FIDO2/)** · lab: SAML SSO + SCIM Endpoint

### 🏛️ Month 2 — Entra ID, Hybrid AD & Okta  <sub>Nov–Dec 2026</sub>

- **[Week 5 — Active Directory Fundamentals & the Tiered Admin Model](Month-02-Entra-ID-Hybrid-AD-and-Okta/Week-05-Active-Directory/)** · lab: Build Wisła Bank AD
- **[Week 6 — Entra ID Core: Sync, Auth Methods & App Registrations](Month-02-Entra-ID-Hybrid-AD-and-Okta/Week-06-Entra-ID-Core/)** · lab: Hybrid Sync & App Permission Audit
- **[Week 7 — Conditional Access as Code & Identity Protection](Month-02-Entra-ID-Hybrid-AD-and-Okta/Week-07-Conditional-Access/)** · lab: CA Baseline in Terraform
- **[Week 8 — Okta Workforce Identity & AD FS Migration](Month-02-Entra-ID-Hybrid-AD-and-Okta/Week-08-Okta-Migration/)** · lab: Okta Integration + AD FS Migration

### ⚖️ Month 3 — Identity Governance, PAM & Automation  <sub>Dec 2026–Jan 2027 · 🎓 SC-300 Identity & Access Administrator</sub>

- **[Week 9 — Entra ID Governance: Entitlements & Access Reviews](Month-03-Identity-Governance-PAM-and-Automation/Week-09-Entra-Governance/)** · lab: Access Packages & Reviews
- **[Week 10 — PIM, PAM, JIT Access & Break-Glass](Month-03-Identity-Governance-PAM-and-Automation/Week-10-PIM-PAM/)** · lab: PIM Configuration & Privileged Report
- **[Week 11 — Joiner-Mover-Leaver Automation & SoD](Month-03-Identity-Governance-PAM-and-Automation/Week-11-JML-SoD/)** · lab: Build the JML Engine
- **[Week 12 — Hygiene Scanner, Evidence Packs & AI-Assisted Reviews → SC-300](Month-03-Identity-Governance-PAM-and-Automation/Week-12-Evidence-SC-300/)** · lab: Evidence Pack + AI Summary

### ☁️ Month 4 — AWS IAM, Organizations & Terraform  <sub>Jan–Feb 2027</sub>

- **[Week 13 — AWS IAM Policy Evaluation Logic](Month-04-AWS-IAM-Organizations-and-Terraform/Week-13-IAM-Policy-Logic/)** · lab: Finding & Fixing Risky IAM Permissions
- **[Week 14 — STS, AssumeRole & Cross-Account Access](Month-04-AWS-IAM-Organizations-and-Terraform/Week-14-STS-AssumeRole/)** · lab: Entra ID → AWS Identity Center Federation
- **[Week 15 — AWS Organizations, Control Tower & SCP Guardrails](Month-04-AWS-IAM-Organizations-and-Terraform/Week-15-Organizations-SCPs/)** · lab: Org + SCP Guardrails in Terraform
- **[Week 16 — Keyless CI/CD with GitHub OIDC & Policy-as-Code](Month-04-AWS-IAM-Organizations-and-Terraform/Week-16-Keyless-CI-CD/)** · lab: OIDC Pipeline with Policy Gates

### 🛰️ Month 5 — AWS Security Services & Detection  <sub>Feb–Mar 2027 · 🎓 AWS Security – Specialty (SCS-C03)</sub>

- **[Week 17 — GuardDuty, Security Hub, Config, Inspector & Detective](Month-05-AWS-Security-Services-and-Detection/Week-17-Detection-Services/)** · lab: Enable the Detection Stack
- **[Week 18 — KMS, Secrets Manager, Macie & Data Protection](Month-05-AWS-Security-Services-and-Detection/Week-18-Data-Protection/)** · lab: Encryption & Secret Rotation
- **[Week 19 — Auto-Remediation with EventBridge, Lambda & Step Functions](Month-05-AWS-Security-Services-and-Detection/Week-19-Auto-Remediation/)** · lab: Eight Remediation Playbooks
- **[Week 20 — Attack Simulation, Demo & SCS-C03](Month-05-AWS-Security-Services-and-Detection/Week-20-Simulation-SCS-C03/)** · lab: Controlled Detect-and-Respond Demo

### 🔷 Month 6 — Azure Security & Policy-as-Code  <sub>Mar–Apr 2027 · 🎓 SC-500 Cloud & AI Security (optional)</sub>

- **[Week 21 — Azure Governance: Management Groups & Azure Policy](Month-06-Azure-Security-and-Policy-as-Code/Week-21-Azure-Governance/)** · lab: Management Groups + Policy-as-Code
- **[Week 22 — Defender for Cloud, Key Vault & Network Security](Month-06-Azure-Security-and-Policy-as-Code/Week-22-Defender-Key-Vault/)** · lab: Defender + Key Vault Hardening
- **[Week 23 — Unified Multi-Cloud Compliance Dashboard → SC-500](Month-06-Azure-Security-and-Policy-as-Code/Week-23-Unified-Dashboard/)** · lab: Cross-Cloud Compliance View

### 🔑 Month 7 — Workload Identity, Kubernetes & Identity Threat Detection  <sub>Apr–May 2027</sub>

- **[Week 24 — Non-Human Identity & Workload Identity Federation](Month-07-Workload-Identity-Kubernetes-and-ITDR/Week-24-Workload-Identity/)** · lab: Keyless Workloads
- **[Week 25 — Kubernetes Security: RBAC, Pod Security & Admission Control](Month-07-Workload-Identity-Kubernetes-and-ITDR/Week-25-Kubernetes-Security/)** · lab: Harden the Cluster
- **[Week 26 — Identity Attack Techniques & MITRE ATT&CK](Month-07-Workload-Identity-Kubernetes-and-ITDR/Week-26-Identity-Attacks/)** · lab: Attack-Path Analysis & Detection Design
- **[Week 27 — Writing Detections: KQL, Sigma & the Detection Pack](Month-07-Workload-Identity-Kubernetes-and-ITDR/Week-27-Detection-Engineering/)** · lab: Build the 12-Detection Pack

### 🤖 Month 8 — AI Agent Identity & AI Security (Capstone)  <sub>May–Jun 2027</sub>

- **[Week 28 — Agent Identity Platforms & Protocols](Month-08-AI-Agent-Identity-and-AI-Security/Week-28-Agent-Identity/)** · lab: Register & Scope an Agent Identity
- **[Week 29 — MCP Security & the Policy Enforcement Point](Month-08-AI-Agent-Identity-and-AI-Security/Week-29-MCP-Security/)** · lab: Secure MCP Server + PEP
- **[Week 30 — AI Threats, Red-Teaming & AI Governance](Month-08-AI-Agent-Identity-and-AI-Security/Week-30-AI-Threats-Governance/)** · lab: Red-Team the Agent + Governance Pack

### 🎯 Month 9 — Portfolio, Positioning & Job Search  <sub>Jun–Jul 2027</sub>

- **[Week 31 — Portfolio Site & Case Studies](Month-09-Portfolio-Positioning-and-Job-Search/Week-31-Portfolio-Site/)** · lab: Build the Portfolio
- **[Week 32 — Interview Preparation & Job Search](Month-09-Portfolio-Positioning-and-Job-Search/Week-32-Interviews-Search/)** · lab: Interview Readiness

---

## Portfolio summary

| # | Repo | Skills proven |
|--|---|---|
| P1 | `identity-protocol-lab` | SAML, OIDC, OAuth, SCIM, JWT security |
| P2 | `hybrid-identity-zero-trust` | Hybrid AD, Conditional Access as code, migration |
| P3 | `iam-governance-engine` | JML, IGA, SoD, PAM, audit evidence, AI-assisted reviews |
| P4 | `secure-landing-zone` | Multi-account AWS + Azure, IaC, policy-as-code, keyless CI/CD |
| P5 | `cloud-auto-remediation` | Detection, IR automation, CSPM |
| P6 | `zero-static-secrets` + `identity-detection-pack` | NHI, workload identity, K8s, ITDR, KQL/Sigma |
| P7 ⭐ | `agent-identity-gateway` | AI agent identity, MCP auth, AI red-teaming, ISO 42001 |

## Certifications

| Cert | When |
|---|---|
| SC-300 Identity & Access Administrator | Month 3 |
| AWS Security – Specialty (SCS-C03) | Month 5 |
| SC-500 Cloud & AI Security Engineer *(optional)* | Month 6 |

---

## Full narrative plan

The original month-by-month narrative (platforms, budgets, weekly rhythm, interview scenarios, sources) is preserved in [PROGRAM-PLAN.md](PROGRAM-PLAN.md).

## How to use this repo

Each week is a folder with a `README.md` (topics, objectives, concepts, a hands-on lab, a deliverable checklist and an interview drill) and a `.pptx` session deck. Work through a week, build its deliverable, and let it feed that month's flagship project. Tear down cloud resources after every session and set budget alerts on day one.
