# Cloud-Security-IAM-Zero-to-Hero
# IAM & Cloud Security Engineer — 9-Month Accelerated Program

> **For:** Steve — Senior GRC / Infosec Risk & Compliance (Kraków), moving into hands-on IAM / Cloud Security Engineering
> **Start:** Mid-October 2026 → **Job-ready:** July 2027 (standard track) or April 2027 (6-month fast track)
> **Effort:** 12–15 hrs/week (standard) · 18–20 hrs/week (fast track)
> **Outcome:** Hireable as **IAM Engineer / Cloud Security Engineer** with 6 flagship portfolio projects, 3 certifications, and a public write-up for every build.

---

## 1. Program Design Principles

1. **Build first, certify second.** Every month ends with a project you push to GitHub. Certifications back up what the repo already proves.
2. **One identity spine through everything.** All projects use the same fictional regulated company — **"Wisła Bank"** (EU bank, 2,000 staff, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents). Your portfolio then reads as one coherent enterprise program, not scattered tutorials.
3. **Compliance-mapped by default.** Every repo has a control-mapping table (ISO 27001:2022, NIS2, DORA, ISO 42001). This is your differentiator — few engineers can do it, and auditors and hiring managers notice.
4. **AI throughout, not bolted on.** Use AI as a coding/analysis assistant from Week 1, and spend the final phase securing AI agents as identities.

---

## 2. Hands-On Training Platforms (Your Lab Stack)

### Core platforms (buy/use these)

| Platform | Use it for | Cost model | When |
|---|---|---|---|
| **Microsoft Learn** (SC-300, SC-500 paths + free sandboxes) | Entra ID, Conditional Access, PIM, Azure security | Free | Months 1–3, 6 |
| **Okta Learning** (on-demand hands-on labs: Universal Directory, SSO, FastPass, Lifecycle, "Secure AI with Okta") + free Okta developer/integrator org | Okta workforce identity, agent identity | Free / low | Months 2, 8 |
| **AWS Skill Builder** (Security Engineer learning plan, Builder Labs, Cloud Quest) | AWS IAM & security services in real sandboxed accounts | Free tier + subscription | Months 3–5 |
| **Pwned Labs** | Attack & defend real AWS, Azure, M365, Entra, AD, K8s and AI environments; free labs + paid bootcamps | Free labs; paid bootcamps/certs | Months 2–7 (weekly) |
| **KodeKloud** | Terraform, Linux, Kubernetes & DevOps sandboxes | Subscription | Months 1, 4, 7 |
| **Tutorials Dojo** (practice exams + PlayCloud sandboxes) | AWS SCS-C03 exam prep | Low | Month 5 |

### Free self-hosted / CTF labs

| Lab | Focus |
|---|---|
| **flAWS / flAWS2** | Classic AWS misconfigurations (attacker + defender paths) |
| **CloudGoat** (Rhino Security Labs) | Terraform-deployed vulnerable AWS scenarios, IAM privilege escalation |
| **IAM Vulnerable** | 30+ AWS IAM privilege-escalation paths |
| **AzureGoat** | Vulnerable Azure environment |
| **Wiz Cloud Security Championship** | Monthly cloud CTF — great for LinkedIn posts |
| **AWS Well-Architected Security Workshops** | Defensive, best-practice builds |
| **Awesome-CloudSec-Labs** (GitHub index) | Directory of further free labs |

### Optional premium (if employer pays)
- **SANS SEC559 – Identity Security for Cloud and Hybrid** — Entra ID + hybrid AD attack detection, governance, response (~16–20 labs).
- **Pwned Labs bootcamps** — MCRTP (Microsoft cloud), ACRTP (AWS) practical certs: strong for proving hands-on skill.

> **Budget tip:** Set AWS Budgets + Azure cost alerts on day one. Tear down everything with `terraform destroy` after each session.

---

## 3. Program at a Glance

| Month | Theme | Flagship Project | Certification |
|---|---|---|---|
| **1** (Oct–Nov '26) | Engineering foundations + identity protocols | P1: Identity Protocol Lab | — |
| **2** (Nov–Dec '26) | Entra ID, hybrid AD, Okta | P2: Hybrid Identity & Zero Trust Access (Wisła Bank) | — |
| **3** (Dec '26–Jan '27) | Identity governance, PAM, automation | P3: IAM Governance Automation Engine | **SC-300** |
| **4** (Jan–Feb '27) | AWS IAM + multi-account + Terraform | P4: Secure Multi-Cloud Landing Zone (part 1: AWS) | — |
| **5** (Feb–Mar '27) | AWS security services + auto-remediation | P4 (part 2) + P5: Cloud Detection & Auto-Remediation | **AWS SCS-C03** |
| **6** (Mar–Apr '27) | Azure security + policy-as-code | P4 (part 3: Azure) | **SC-500** *(optional)* |
| **7** (Apr–May '27) | Workload identity, K8s, identity threat detection | P6: Zero-Static-Secrets & Identity Threat Detection Pack | — |
| **8** (May–Jun '27) | AI agent identity & AI security | P7: Agent Identity Gateway (capstone) | — |
| **9** (Jun–Jul '27) | Portfolio polish, interviews, job search | Portfolio site + case studies | — |

**6-month fast track:** merge Months 1+2, 4+5, 7+8 and skip SC-500 → done by **April 2027**.

---

## 4. Month-by-Month Plan

### MONTH 1 — Foundations & Identity Protocols
**Learn**
- Networking for cloud: DNS, TLS, HTTP, CIDR, NAT, VPN, proxies, load balancers.
- Linux & Bash; PowerShell; Python (`requests`, `boto3`, `msgraph`), Git workflow.
- **Identity protocols (core):** SAML 2.0, OAuth 2.0/2.1 grant types, PKCE, OIDC, JWT anatomy & validation, SCIM 2.0, FIDO2/passkeys.
- Terraform basics (KodeKloud Terraform course).

**Labs:** KodeKloud Linux/Terraform labs · decode SAML with SAML-tracer · build an OIDC client from scratch.

#### 🔨 Project 1 — Identity Protocol Lab (`identity-protocol-lab`)
- A small Python/Flask (or FastAPI) app that implements **OIDC Authorization Code + PKCE**, **SAML SP-initiated SSO**, and a **SCIM 2.0** endpoint — against both Entra ID and Okta.
- Sequence diagrams (Mermaid) for each flow; a "token inspector" page showing decoded claims and validation steps.
- **Security section:** common attacks (token replay, alg-none/confusion, open redirect, missing PKCE) and how the app prevents them.
- **Why it impresses:** proves you understand protocols, not just admin consoles.

---

### MONTH 2 — Microsoft Entra ID, Hybrid AD & Okta
**Learn**
- AD DS: OUs, GPO, Kerberos/NTLM, tiered admin model.
- Entra ID: Cloud Sync / Entra Connect, auth methods, Conditional Access design, authentication strengths, Identity Protection, B2B, app registrations vs enterprise apps, managed identities.
- Okta: Universal Directory, AD agent, SSO, FastPass, authentication policies, Lifecycle Management, Workflows.
- Federation between Okta and Entra ID.

**Labs:** Microsoft Learn SC-300 modules · Okta Learning hands-on labs · Pwned Labs Entra/M365 free labs (see the attacker's view of your config).

#### 🔨 Project 2 — Wisła Bank Hybrid Identity & Zero Trust Access (`hybrid-identity-zero-trust`)
- On-prem AD (Windows Server VM) → synced to Entra ID → federated with Okta for a subset of SaaS apps.
- **Conditional Access baseline as code** (~12 policies) deployed via Microsoft Graph PowerShell or Terraform `azuread` provider: phishing-resistant MFA for admins, device compliance, legacy-auth block, risk-based policies, break-glass exclusions.
- **AD FS → Entra ID migration runbook** executed in the lab, with rollback plan.
- **Deliverables:** architecture diagram, policy JSON, migration runbook, control mapping (ISO 27001 A.5.15–5.18, A.8.2–8.5; NIS2 Art. 21; DORA ICT access controls).
- **Why it impresses:** hybrid identity migrations appear in many 2026 IAM job ads.

---

### MONTH 3 — Identity Governance, PAM & Automation → **SC-300**
**Learn**
- Entra ID Governance: entitlement management, access packages, access reviews, lifecycle workflows, PIM for roles & groups.
- Okta Identity Governance concepts (certifications, access requests).
- PAM concepts: JIT/JEA, break-glass, session recording, CyberArk vault model.
- Segregation of Duties (SoD) — your audit background applies directly.

**Labs:** Microsoft Learn governance modules · SC-300 practice assessment.

#### 🔨 Project 3 — IAM Governance Automation Engine (`iam-governance-engine`)
- Python service that reads a **fake HRIS CSV/API** and drives **Joiner-Mover-Leaver** across Entra ID + Okta (+ AWS Identity Center in Month 4).
- **Hygiene scanner:** stale accounts, MFA gaps, orphaned accounts, toxic SoD combinations, dormant privileged roles.
- **Audit evidence pack:** auto-generated, timestamped report (HTML/PDF) mapped to ISO 27001 controls — "evidence an auditor would accept."
- **AI feature:** LLM-generated plain-language summary for access reviewers, with **mandatory human approval** and full logging.
- **Why it impresses:** combines engineering + automation + audit — exactly your niche.

**🎓 Certification:** **SC-300** (Microsoft Identity and Access Administrator).

---

### MONTH 4 — AWS IAM, Organizations & Terraform
**Learn**
- IAM policy evaluation logic: identity vs resource policies, SCPs/RCPs, permission boundaries, session policies, explicit deny.
- STS, AssumeRole, cross-account access, IAM Identity Center federated with Entra ID (SAML + SCIM).
- AWS Organizations, Control Tower concepts, CloudTrail organization trail, IAM Access Analyzer.

**Labs:** AWS Skill Builder Security Engineer plan · flAWS / flAWS2 · **IAM Vulnerable** (exploit then fix every escalation path) · CloudGoat IAM scenarios · Pwned Labs AWS labs.

#### 🔨 Project 4 (Part 1) — Secure Multi-Cloud Landing Zone (`secure-landing-zone`)
- Terraform: AWS Organization with management, security, log-archive, and workload accounts.
- SCP guardrails (EU-only regions, deny root, deny disabling CloudTrail/GuardDuty, deny public S3).
- IAM Identity Center federated with your Entra tenant; permission sets mapped to Wisła Bank roles.
- **CI pipeline (GitHub Actions + OIDC — no static keys):** `terraform plan` → Checkov/Trivy scan → OPA policy check → manual approval → apply.

---

### MONTH 5 — AWS Security Services & Detection → **AWS SCS-C03**
**Learn**
- GuardDuty, Security Hub, Config, Inspector, Macie, Detective, Security Lake.
- KMS (key policies, grants), Secrets Manager, VPC security & endpoint policies, WAF.
- Incident response automation: EventBridge → Lambda / Step Functions.
- GenAI security on AWS (Bedrock guardrails, model access controls) — now part of SCS-C03.

**Labs:** Skill Builder Builder Labs · Tutorials Dojo SCS-C03 practice exams + PlayCloud · CloudGoat detection scenarios.

#### 🔨 Project 4 (Part 2) + Project 5 — Cloud Detection & Auto-Remediation (`cloud-auto-remediation`)
- Enable org-wide GuardDuty, Security Hub (CIS + AWS FSBP standards), Config in the landing zone.
- **8 auto-remediation playbooks**, e.g. public S3 bucket → block; SG open to 0.0.0.0/0 on 22/3389 → revoke; compromised access key → deactivate + quarantine role; root login → alert + ticket.
- Slack/Teams notifications; every action logged to an immutable audit bucket.
- **Attack simulation:** run a CloudGoat scenario → show detection → show automatic response (record a 3-minute demo video).
- **Why it impresses:** demonstrates detect → respond → evidence, end to end.

**🎓 Certification:** **AWS Certified Security – Specialty (SCS-C03).**

---

### MONTH 6 — Azure Security & Policy-as-Code → **SC-500** *(optional)*
**Learn**
- Azure Management Groups, Azure Policy/initiatives, Defender for Cloud (CSPM), Key Vault, Private Endpoints, NSGs, Azure Firewall, Sentinel basics, workload identity federation, securing Azure AI Foundry deployments.

**Labs:** Microsoft Learn SC-500 path · AzureGoat · Pwned Labs Azure labs.

#### 🔨 Project 4 (Part 3) — Landing Zone: Azure side
- Terraform Azure landing zone with Policy-as-code: EU-only regions, encryption required, no public IPs, mandatory tags, Defender plans enabled.
- **Unified compliance dashboard:** pulls AWS Security Hub + Azure Defender for Cloud findings into one view mapped to ISO 27001 / NIS2 / DORA.
- **Final P4 README:** one landing zone, two clouds, one identity source (Entra ID), every guardrail traceable to a requirement.

**🎓 Certification:** **SC-500 Cloud & AI Security Engineer** (replaced AZ-500, retired 31 Aug 2026). Skip on fast track.

---

### MONTH 7 — Workload Identity, Kubernetes & Identity Threat Detection
**Learn**
- Non-human identity (NHI): GitHub Actions OIDC, EKS Pod Identity / IRSA, Azure workload identity federation, SPIFFE/SPIRE concepts, HashiCorp Vault dynamic secrets.
- Kubernetes RBAC, service accounts, Pod Security Standards, Kyverno/OPA Gatekeeper.
- Identity attack techniques: token theft, MFA fatigue, consent phishing, OAuth app abuse, Golden SAML, AWS privilege-escalation paths; MITRE ATT&CK identity techniques.
- KQL (Sentinel / Defender XDR) and Sigma rule writing.

**Labs:** KodeKloud K8s security labs · Pwned Labs identity/hybrid attack labs · BloodHound / AzureHound in your lab.

#### 🔨 Project 6 — Zero-Static-Secrets & Identity Threat Detection Pack (`zero-static-secrets` + `identity-detection-pack`)
- **Part A:** A demo app on EKS/AKS (or kind locally) where CI/CD, pods, and functions authenticate to AWS & Azure with **zero long-lived credentials**; secrets scanner proving none exist.
- **Part B:** **12 identity detections** (KQL + Sigma + CloudTrail queries), each with: ATT&CK mapping, lab reproduction steps, sample logs, true/false-positive notes, and response playbook.
- **Why it impresses:** NHI/secrets and ITDR are exactly what 2026 hiring managers probe for.

---

### MONTH 8 — AI Agent Identity & AI Security (Capstone)
**Learn**
- Agent identity platforms: **Microsoft Entra Agent ID**, **Okta for AI Agents / Agent SSO / Agent Gateway**, Auth0 Auth for MCP.
- Protocols: OAuth 2.1, Token Exchange (RFC 8693) / on-behalf-of, Cross App Access (XAA) & ID-JAG, **MCP authorization spec**, sender-constrained tokens (DPoP).
- AI threats: OWASP Top 10 for LLM Apps & agentic AI threats, MITRE ATLAS, prompt injection (direct/indirect), tool poisoning, excessive agency.
- Governance: ISO/IEC 42001, EU AI Act deployer duties, NIST AI RMF — your Lead Auditor credential applies here.

**Labs:** Okta Learning "Secure AI with Okta" path · Pwned Labs AI security labs · Microsoft Learn Entra Agent ID modules.

#### 🔨 Project 7 (CAPSTONE) — Agent Identity Gateway for Wisła Bank (`agent-identity-gateway`)
- An **AI agent** (e.g., "loan-ops assistant") that reads tickets and queries a customer DB **on behalf of a signed-in employee** via **MCP tools**.
- MCP server protected by **OAuth 2.1**; agent registered as a first-class identity (Entra Agent ID or Okta); **short-lived, scoped tokens** via token exchange; per-tool least privilege.
- **Policy enforcement point** in front of tools: deny out-of-scope calls, require human approval for high-risk actions, kill switch.
- **Red-team section:** indirect prompt injection via a poisoned ticket → attempted data exfiltration → show which identity control blocks it.
- **Governance pack:** agent inventory, human owner per agent, quarterly access certification covering humans + agents, ISO 42001 / EU AI Act control mapping.
- **Why it impresses:** very few candidates in 2026–27 can show working agent identity. This is your headline project.

---

### MONTH 9 — Portfolio, Positioning & Job Search
- **Portfolio site** (GitHub Pages): "Steve — Identity & Cloud Security Engineer," one case-study page per project (problem → architecture → build → security results → control mapping → lessons learned).
- **3–5 minute demo video** per flagship project (P2, P5, P7 at minimum).
- **Pin 6 repos** on GitHub; consistent README template (below).
- **Write 4 LinkedIn/blog posts:** P3 (audit-ready IAM automation), P5 (detect & respond), P6 (zero static secrets), P7 (agent identity).
- **Interview prep:** 2 mock system-design interviews/week (scenarios in Section 7).
- **Target employers:** banks & fintech centres in Kraków (regulated identity under DORA), Big 4 / consultancies (identity practices), SaaS firms using Okta, Microsoft/AWS partners.

---

## 5. Portfolio Summary

| # | Repo | Skills proven | Stack |
|---|---|---|---|
| P1 | `identity-protocol-lab` | SAML, OIDC, OAuth, SCIM, JWT security | Python, Entra, Okta |
| P2 | `hybrid-identity-zero-trust` | Hybrid AD, Conditional Access as code, migration | AD, Entra, Okta, Graph, Terraform |
| P3 | `iam-governance-engine` | JML, IGA, SoD, PAM, audit evidence, AI-assisted reviews | Python, Entra Governance, Okta |
| P4 | `secure-landing-zone` | Multi-account AWS, Azure, IaC, policy-as-code, CI/CD | Terraform, OPA, Checkov, GitHub Actions |
| P5 | `cloud-auto-remediation` | Detection, IR automation, CSPM | GuardDuty, Security Hub, EventBridge, Lambda |
| P6 | `zero-static-secrets` + `identity-detection-pack` | NHI, workload identity, K8s, ITDR, KQL/Sigma | EKS/AKS, OIDC, Vault, Sentinel |
| P7 | `agent-identity-gateway` ⭐ | AI agent identity, MCP auth, AI red-teaming, ISO 42001 | MCP, OAuth 2.1, Entra Agent ID/Okta, LLM |

### README template (use for every repo)
```
# Project name — one-line value statement
## Business problem (Wisła Bank context)
## Architecture (diagram)
## What I built (bullet list)
## Security controls & threat model (STRIDE table)
## Compliance mapping (ISO 27001 / NIS2 / DORA / ISO 42001)
## Demo (GIF or video link)
## How to deploy (terraform apply / make run)
## Lessons learned & what I'd do next
```

---

## 6. Weekly Rhythm (Standard Track, ~14 hrs)

| Day | Activity | Hours |
|---|---|---|
| Mon | Course/reading (Microsoft Learn, Skill Builder, Okta Learning) | 1.5 |
| Tue | Platform labs (Pwned Labs / KodeKloud / CloudGoat) | 2 |
| Thu | Project build | 2 |
| Sat | Deep project block | 5 |
| Sun | Documentation, diagram, README, post draft | 2 |
| Flexible | Cert practice questions (exam months) | 1.5 |

**Rules:** one Pwned Labs or CTF lab every week · every Sunday commit = documentation · tear down cloud resources every session.

---

## 7. Interview Scenarios to Rehearse (Using Your Projects)

1. "Walk me through SAML SSO, then OIDC — where can each be attacked?" → **P1**
2. "Migrate 2,000 users off AD FS with zero downtime." → **P2**
3. "Design JML for 200 SaaS apps and prove it to auditors." → **P3**
4. "A user has AdministratorAccess but gets AccessDenied — debug it." → **P4**
5. "An access key leaked on GitHub — what happens in the next 5 minutes?" → **P5**
6. "Remove every long-lived credential from our pipelines." → **P6**
7. "An AI agent must act on behalf of employees across 3 systems — design its identity." → **P7**

---

## 8. Certification Summary (status October 2026)

| Cert | When | Notes |
|---|---|---|
| **SC-300** Identity & Access Administrator | Month 3 | Most common cert on 2026 IAM résumés |
| **AWS Security – Specialty (SCS-C03)** | Month 5 | Current since Dec 2025; includes GenAI security; $300 |
| **SC-500** Cloud & AI Security Engineer | Month 6 (optional) | Replaced AZ-500 (retired 31 Aug 2026) |
| *Optional:* Okta Certified Professional | Month 2–3 | Okta reportedly moved to hands-on performance exams in 2026 — check current format |
| *Optional:* Pwned Labs MCRTP / ACRTP | Months 6–8 | Practical cloud attack/defend certs |

Re-check each exam's status before booking — vendors changed many certifications in 2026.

---

## 9. After the Program (Next 12–24 Months)
- CKS (Kubernetes security), Terraform Associate, a vendor IGA/PAM cert (SailPoint, CyberArk) depending on employer.
- SC-100 Cybersecurity Architect → CCSP for the architect path.
- Keep extending P7 as agent identity standards evolve (MCP, XAA, Entra Agent ID).

---

## Sources (researched October 2026)
- [Pwned Labs — platform overview (Capterra)](https://www.capterra.com/p/10039452/Pwned-Labs/)
- [Pwned Labs — reviews (G2)](https://www.g2.com/products/pwned-labs/reviews)
- [CloudaQube — Best hands-on cloud labs platforms 2026](https://cloudaqube.com/blog/best-hands-on-cloud-labs-platforms-2026)
- [Awesome-CloudSec-Labs (GitHub)](https://github.com/iknowjason/Awesome-CloudSec-Labs)
- [Okta Learning — hands-on labs](https://learning.okta.com/)
- [SANS SEC559 — Identity Security for Cloud and Hybrid](https://www.sans.org/cyber-security-courses/identity-security-cloud-hybrid)
- [MindMajix — Okta training (performance exam note)](https://mindmajix.com/okta-training)
- [KORE1 — IAM engineer salary guide 2026](https://www.kore1.com/iam-engineer-salary-guide/)
- [Whizlabs — AWS SCS-C03](https://www.whizlabs.com/aws-certified-security-specialty/)
- [Certification Camps — SC-500 exam guide](https://www.certificationcamps.com/sc-500-exam-guide/)
- [Start With Identity — Agent identity gets a protocol](https://startwithidentity.com/blog/agent-identity-gets-a-protocol/)
