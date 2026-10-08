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

---

## Technical Tasks & Implementation Steps

### Phase 1: Cloud Provisioning & Governance
- Negotiated Azure subscription policy restrictions and regional quota limitations to select optimal datacenter compute resources.
- Configured Gen2 Trusted Launch infrastructure enforcing Secure Boot and virtual TPM.
- Defined custom Network Security Group (NSG) rules to isolate management ports.

### Phase 2: Active Directory & Network Services *(Upcoming/In Progress)*
- [ ] Install and configure Active Directory Domain Services (AD DS).
- [ ] Promote VM to Primary Domain Controller for domain `lab.local`.
- [ ] Configure DNS Server roles, forwarders, and reverse lookup zones.
- [ ] Implement Organizational Unit (OU) structure following tier-based administrative models.
- [ ] Create and enforce Group Policy Objects (GPOs) for enterprise security baselines.

---

## Administrative Verification
- Successful remote administration via Remote Desktop Protocol (RDP).
- Verified OS patch level, VM agent status, and Azure Monitor metrics.

---

## Operational Cost Management
- Applied manual deallocation (`Stop/Deallocate`) policies in Azure Portal to optimize cloud compute consumption against subscription credits.
