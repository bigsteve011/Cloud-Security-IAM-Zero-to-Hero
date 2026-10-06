# Week 5 — Active Directory Fundamentals & the Tiered Admin Model

**🏛️ Month 2 · Entra ID, Hybrid AD & Okta** · [← Back to program](../../README.md) · [Month overview](../README.md)

> Continuity case study: **Wisła Bank** — EU bank, hybrid AD, Entra ID, Okta, AWS + Azure, rolling out AI agents.

## Topics

- Forests, domains, OUs, groups and GPOs
- Kerberos (TGT, TGS, PAC) vs NTLM — and why NTLM must die
- Tier 0/1/2 admin model and Privileged Access Workstations
- Common AD attacks: Kerberoasting, AS-REP roasting, DCSync, pass-the-hash
- AD hardening: LAPS, Protected Users, disabling NTLMv1

## Learning objectives

By the end of this week you can:

- Build a two-VM AD lab for Wisła Bank
- Implement tiered OUs and admin accounts
- Run BloodHound and read an attack path
- Apply five hardening GPOs

## Core concepts

| Concept | In one line |
|---|---|
| **Tier 0** | Anything that controls identity: DCs, AD FS, Entra Connect, PKI. Treat as crown jewels. |
| **Kerberos** | Ticket-based. Service accounts with weak passwords → Kerberoasting. |
| **LAPS** | Unique, rotated local admin password per machine. Kills lateral movement. |
| **BloodHound** | Graphs who can reach Domain Admins. Defenders should run it first. |

## How it fits together

`Tier 2 workstation` → `Tier 1 servers` → `Tier 0 DCs` → `Entra Connect` → `Cloud`

## 🔨 Hands-on lab — Build Wisła Bank AD

**Platform:** Local Hyper-V/VirtualBox or Azure VM + Pwned Labs · **Est. time:** 4 h

1. Deploy Windows Server 2022 and promote to DC
   ```bash
   Install-WindowsFeature AD-Domain-Services -IncludeManagementTools; Install-ADDSForest -DomainName wislabank.local
   ```
2. Create tiered OUs
   ```bash
   'Tier0','Tier1','Tier2','Users','ServiceAccounts' | % { New-ADOrganizationalUnit -Name $_ -Path 'DC=wislabank,DC=local' }
   ```
3. Bulk-create 50 users from CSV
   ```bash
   Import-Csv users.csv | % { New-ADUser -Name $_.Name -SamAccountName $_.Sam -Path $_.OU -AccountPassword (ConvertTo-SecureString $_.Pw -AsPlainText -Force) -Enabled $true }
   ```
4. Deploy Windows LAPS policy
   ```bash
   Update-LapsADSchema; Set-LapsADComputerSelfPermission -Identity 'OU=Tier1,DC=wislabank,DC=local'
   ```
5. Run SharpHound and import into BloodHound CE
6. Complete one Pwned Labs AD/hybrid free lab

## Prove it

**Deliverable:** P2 repo: ad/ folder with build scripts, OU design diagram and BloodHound before/after findings

Feeds the flagship project **P2 `hybrid-identity-zero-trust`**.

**Done when:**

- [ ] DC running with tiered OUs
- [ ] LAPS active on Tier 1
- [ ] One BloodHound path documented and closed
- [ ] Pwned Labs write-up drafted

## 🎤 Interview drill

**Q — How would you protect AD from Kerberoasting?**

> gMSAs or 25+ char random service-account passwords, AES-only encryption, monitor 4769 events with RC4, remove unnecessary SPNs, and tier service accounts.

## Session deck

- [W5_Active_Directory.pptx](W5_Active_Directory.pptx)
