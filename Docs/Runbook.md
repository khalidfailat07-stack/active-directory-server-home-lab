@'
# IT Support Operations Runbook
**Environment:** `khalid.local` (Active Directory Domain Services)  
**Target:** Enterprise Operations / Service Desk  
**Author:** Khalid Failat  

---

## 1. Overview & Operational Scope
This runbook defines standard operating procedures (SOPs) for administrative credential management, user support, and endpoint connectivity troubleshooting across the `khalid.local` domain. It provides standardized steps for both on-site field technicians and remote support teams.

---

## 2. Password Resets & Credential Management
When a user forgets their credentials or experiences account lockouts, perform administrative maintenance using the steps below.

### Procedure: Identity Verification & Password Reset
1. Verify user identity following standard corporate identity verification procedures.
2. Open PowerShell as Administrator on **`DC-01`**.
3. Set temporary administrative credentials and enforce mandatory password change upon next logon:
   ```powershell
   # Define target user account
   $TargetUser = "sconner"

   # Create secure temporary password
   $TempPass = ConvertTo-SecureString "TempP@ssword2026!" -AsPlainText -Force

   # Reset user password
   Set-ADAccountPassword -Identity $TargetUser -NewPassword $TempPass -Reset

   # Force user password change on next interactive login
   Set-ADUser -Identity $TargetUser -ChangePasswordAtLogon $true

   # If an account becomes locked due to multiple invalid login attempts
   Unlock-ADAccount -Identity $TargetUser #
   
## 3. Client Connectivity Troubleshooting
When an an endpoint is unable to connect to the network.

### Procedure: Begin troubleshooting at the physical level before moving to other configurations.
1. Physical Cable and Link Status Check
   * Examine RJ-45 Ethernet Cable connected to the endpoint and wall/switch. Ensure the cable isnt physically damaged and that clip is securely intact.
   * Verify link light Status
      * **Solid/Flashing Green:** Active physical link established at full speed
      * **Orange/Off:** No link detected, duplex mismatch, or faulty cable.

2. Patch Cable and Wall Jack Isolation
   * Swap patch cable with a known-working Ethernet cable.
   * Connect the endpoint to a secondary known-working switch port or wall outlet to isolate structured cabling failures.

3. Power and Hardware Status
   * Confirm NIC is enabled in BIOS and device manager.
   * Ensure any hardware switch or physical button for networking/wireless on mobile endpoints is enabled.

### Procedure: Begin troubleshooting device configurations 
1. Endpoint IP and DNS Configurations
   * Run ipconfig /all and ensure correct DNS and DHCP configurations if needed.
2. Test Active Directory Port Reachability
   *Test LDAP (Port 389) connectivity from the client workstation to the Domain Controller using: Test-NetConnection -ComputerName (hostname of DC) -Port 389.

## 4. Documentation & Ticket Resolution Checklist
1. Document the technician name, target account or workstation hostname, and actions taken in the ticketing platform.
2. Escalate unresolved issues and hardware failues.
