# active-directory-server-home-lab
Documentation and scripts for my active directory, DNS, and GPO home lab, applying prior learned knowledge to actual environments


# Azure Cloud Infrastructure & Windows Server 2022 Lab

## Project Overview
Deployed and configured a production-ready Windows Server 2022 instance in Microsoft Azure. Designed as a foundational cloud environment for enterprise Active Directory Domain Services (AD DS), Group Policy Management, and Network Services administration.

---

## Architecture & Deployment Details

| Parameter | Configuration |
| :--- | :--- |
| **Cloud Provider** | Microsoft Azure |
| **Deployment Region** | Sweden Central (`swedencentral`) |
| **Virtual Machine SKU** | `Standard_B4as_v2` (4 vCPUs, 16 GB RAM) |
| **Operating System** | Windows Server 2022 Datacenter (x64 Gen2) |
| **Security Architecture**| Trusted Launch (vTPM & Secure Boot Enabled) |
| **Networking & Firewalls**| Azure VNet, Network Security Group (NSG) with restricted RDP access |
<img width="500" height="250" alt="01-DC-VM-Creation-Specs" src="https://github.com/user-attachments/assets/22737d6c-a7dc-4a5f-992a-2b026db712fc" />
<img width="500" height="250" alt="06-ClientVM-Created" src="https://github.com/user-attachments/assets/57edbae5-289f-476c-9025-74141513e4da" />


---

## Technical Tasks & Implementation Steps

### Phase 1: Cloud Provisioning & Governance
- Negotiated Azure subscription policy restrictions and regional quota limitations to select optimal datacenter compute resources.
- Configured Gen2 Trusted Launch infrastructure enforcing Secure Boot and virtual TPM.
- Defined custom Network Security Group (NSG) rules to isolate management ports.

### Phase 2: Active Directory & Network Services 
- [X] Install and configure Active Directory Domain Services (AD DS).
- [X] Promote VM to Primary Domain Controller for domain `khalid.local`.
- [X] Configure DNS Server roles and reverse lookup zones.
- [X] Implement Organizational Unit (OU) structure following tier-based administrative models.
- [X] Create and enforce Group Policy Objects (GPOs) for enterprise security baselines.
<img width="500" height="250" alt="04-gpo-security-baseline png" src="https://github.com/user-attachments/assets/805c1515-fecd-463a-9c32-a6ecb2b5db96" />
<img width="500" height="250" alt="09-Remote-Desktop-Policy-Creation" src="https://github.com/user-attachments/assets/68f0c488-a683-4a9e-82b0-5fbd9eec4ec0" />

---

## Administrative Verification
- Successful remote administration via Remote Desktop Protocol (RDP).
- Verified OS patch level, VM agent status, and Azure Monitor metrics.

---

## Operational Cost Management
- Applied manual deallocation (`Stop/Deallocate`) policies in Azure Portal to optimize cloud compute consumption against subscription credits.
