# 🛰️ Month 5 — AWS Security Services & Detection

*Feb–Mar 2027* · 🎓 **AWS Security – Specialty (SCS-C03)**

[← Back to program](../README.md)


## Flagship project — P5: Cloud Detection & Auto-Remediation

`cloud-auto-remediation`

Org-wide GuardDuty, Security Hub and Config with eight auto-remediation playbooks, immutable audit logging and a controlled attack-simulation demo showing detect → respond → evidence.

**Deliverables**

- Org-wide GuardDuty, Security Hub (CIS + AWS FSBP), Config
- 8 EventBridge → Lambda/Step Functions remediation playbooks
- Slack/Teams notifications on every action
- Immutable audit bucket for all remediation events
- Attack-simulation demo (controlled sandbox) with a 3-minute video
- KMS, Secrets Manager and Macie hardening of the data path

**Compliance mapping**

| Control | Requirement |
|---|---|
| ISO 27001:2022 A.8.16 | Monitoring activities |
| ISO 27001:2022 A.5.26 | Response to incidents |
| NIS2 Art. 23 | Incident reporting |
| DORA Art. 17–19 | ICT incident management and reporting |

## Weeks

| Week | Topic | Lab | Deck |
|---|---|---|---|
| **17** | [GuardDuty, Security Hub, Config, Inspector & Detective](Week-17-Detection-Services/) | Enable the Detection Stack | [pptx](Week-17-Detection-Services/W17_Detection_Services.pptx) |
| **18** | [KMS, Secrets Manager, Macie & Data Protection](Week-18-Data-Protection/) | Encryption & Secret Rotation | [pptx](Week-18-Data-Protection/W18_Data_Protection.pptx) |
| **19** | [Auto-Remediation with EventBridge, Lambda & Step Functions](Week-19-Auto-Remediation/) | Eight Remediation Playbooks | [pptx](Week-19-Auto-Remediation/W19_Auto_Remediation.pptx) |
| **20** | [Attack Simulation, Demo & SCS-C03](Week-20-Simulation-SCS-C03/) | Controlled Detect-and-Respond Demo | [pptx](Week-20-Simulation-SCS-C03/W20_Simulation_SCS_C03.pptx) |
