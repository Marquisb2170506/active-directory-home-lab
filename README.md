# Active Directory Home Lab

**Platform:** Windows Server 2022 | VirtualBox  
**Domain:** marquis.local  
**Status:** Complete ✅

---

## Project Overview

This home lab documents the deployment of a fully functional Active Directory domain environment built from scratch on a personal machine using VirtualBox. The lab simulates a real enterprise IT environment and demonstrates core skills required for Tier 1 IT Help Desk and System Administrator roles.

---

## Environment Setup

| Component | Details |
|-----------|---------|
| Hypervisor | Oracle VirtualBox |
| Server OS | Windows Server 2022 (Evaluation) |
| Domain Name | marquis.local |
| Domain Controller | MARQUIS-DC |
| Client Machine | Windows 10 Pro (domain-joined) |

---

## Lab Walkthrough — Step by Step

### Phase 1 — Virtual Machine Creation

**Step 1 — VM Creation Settings**  
Configured the VirtualBox virtual machine with appropriate memory, CPU, and storage settings for Windows Server 2022.

![VM Creation Settings](screenshots/01_VM_Creation_Settings.png.png)

---

**Step 2 — VM Summary**  
Reviewed the final VM configuration summary before starting the installation.

![VM Summary](screenshots/02_VM_Summary.png.png)

---

**Step 3 — Windows Setup Start**  
Booted the VM from the Windows Server 2022 ISO and began the installation process.

![Windows Setup Start](screenshots/03_Windows_Setup_Start.png.png)

---

**Step 4 — Version Selection**  
Selected Windows Server 2022 Standard Evaluation (Desktop Experience) for the GUI-based server environment.

![Version Selection](screenshots/04_Version_Selection.png.png)

---

**Step 5 — Installation Progress**  
Windows Server 2022 installation in progress on the virtual machine.

![Installation Progress](screenshots/05_Installation_Progress.png.png)

---

**Step 6 — Admin Password Setup**  
Set the local Administrator password after installation completed.

![Admin Password Setup](screenshots/06_Admin_Password_Setup.png.png)

---

### Phase 2 — Server Configuration

**Step 7 — Server Lock Screen**  
First boot into Windows Server 2022 — lock screen confirming successful installation.

![Server Lock Screen](screenshots/07_Server_Lock_Screen.png.png)

---

**Step 8 — Server Desktop First Login**  
Successfully logged into the server desktop for the first time. Server Manager launched automatically.

![Server Desktop First Login](screenshots/08_Server_Desktop_First_Login.png.png)

---

### Phase 3 — Active Directory Domain Services Installation

**Step 9 — ADDS Installing**  
Installed the Active Directory Domain Services (AD DS) role via Server Manager.

![ADDS Installing](screenshots/09_ADDS_Installing.png.png)

---

**Step 10 — New Forest Setup**  
Promoted the server to a Domain Controller by creating a new forest with the domain name `marquis.local`.

![New Forest Setup](screenshots/10_New_Forest_Setup.png.png)

---

**Step 11 — Server Desktop Post Promotion**  
Server successfully rebooted after Domain Controller promotion. Server Manager now shows AD DS role active.

![Server Desktop Post Promotion](screenshots/11_Server_Desktop_Post_Promotion.png.png)

---

**Step 12 — System Info**  
System information confirming the server is now operating as a Domain Controller for `marquis.local`.

![System Info](screenshots/12_System_Info.png.png)

---

**Step 13 — DC Verified via CMD**  
Ran `nltest /dsgetdc:marquis.local` in Command Prompt to verify the Domain Controller is responding and the domain is live.

![DC Verified CMD](screenshots/13_DC_Verified_CMD.png.png)

---

**Step 14 — ADUC Open**  
Opened Active Directory Users and Computers (ADUC) — the primary tool for managing users, groups, and organizational units.

![ADUC Open](screenshots/14_ADUC_Open.png.png)

---

**Step 15 — Server Manager DC Live**  
Server Manager dashboard confirming Active Directory Domain Services is running and healthy.

![Server Manager DC Live](screenshots/15_Server_Manager_DC_Live.png.png)

---

**Step 16 — ADUC Domain Live**  
Active Directory Users and Computers showing the live `marquis.local` domain structure.

![ADUC Domain Live](screenshots/16_ADUC_Domain_Live.png.png)

---

### Phase 4 — Organizational Unit Structure

**Step 17 — IT OU Created**  
Created the IT Organizational Unit (OU) under the `marquis.local` domain to organize IT department accounts.

![IT OU Created](screenshots/17_IT_OU_Created.png.png)

---

**Step 18 — Three OUs Created**  
Completed the full OU structure with three departments: IT, HR, and Finance — mirroring a real corporate environment.

![Three OUs Created](screenshots/18_Three_OUs_Created.png.png)

---

### Phase 5 — User Account Provisioning

**Step 19 — First User Created**  
Created the first domain user account (`jsmith`) in the IT OU with full name, username, and initial password.

![First User Created](screenshots/19_First_User_Created.png.png)

---

**Step 20 — All Users Created**  
All 6 domain user accounts provisioned across IT, HR, and Finance OUs.

| Username | Department |
|----------|-----------|
| jsmith | IT |
| mwilliams | HR |
| tharris | Finance |
| amorgan | IT |
| ljones | HR |
| rthompson | Finance |

![Users Created](screenshots/20_Users_Created.png..png)

---

**Step 21 — Security Groups Created**  
Created department-level Security Groups (IT-Staff, HR-Staff, Finance-Staff) for resource access control.

![Security Groups Created](screenshots/21_Security_Groups_Created.png.png)

---

**Step 22 — Users Added to Group**  
Added users to their respective Security Groups based on department assignment.

![Users Added To Group](screenshots/22_Users_Added_To_Group.png.png)

---

### Phase 6 — Tier 1 Help Desk Simulations

**Step 23 — Password Reset**  
Simulated a password reset for user `mwilliams` who forgot their domain password. Reset via ADUC and enabled "User must change password at next logon."

![Password Reset](screenshots/23_Password_Reset.png.png)

---

**Step 24 — Account Disabled (Terminated Employee)**  
Disabled the account for terminated employee `tharris` per HR offboarding request. Account moved to Disabled Users OU.

![Account Disabled](screenshots/24_Account_Disabled.png.png)

---

**Step 25 — Account Unlock**  
Unlocked the account for `jsmith` who was locked out after multiple failed login attempts. Verified identity before taking action.

![Account Unlock](screenshots/25_Account_Unlock.png.png)

---

### Phase 7 — Group Policy Object (GPO)

**Step 26 — GPMC Open**  
Opened the Group Policy Management Console (GPMC) to create and manage Group Policy Objects.

![GPMC Open](screenshots/26_GPMC_Open.png.png)

---

**Step 27 — DC Baseline Confirmed**  
Confirmed the Default Domain Policy baseline before creating a new custom GPO.

![DC Baseline Confirmed](screenshots/27_DC_Baseline_Confirmed.png..png)

---

**Step 28 — GPO Password Policy**  
Created a new GPO named "Password Security Policy" and configured the following settings:

| Policy Setting | Value |
|----------------|-------|
| Minimum password length | 10 characters |
| Password complexity | Enabled |
| Maximum password age | 90 days |
| Account lockout threshold | 5 failed attempts |
| Lockout duration | 30 minutes |

![GPO Password Policy](screenshots/28_GPO_Password_Policy.png.png)

---

**Step 29 — GPO Linked**  
Linked the Password Security Policy GPO to the `marquis.local` domain, enforcing the policy for all domain users.

![GPO Linked](screenshots/29_GPO_Linked.png.png)

---

## Skills Demonstrated

- Active Directory Domain Services (AD DS)
- Organizational Unit (OU) Design
- User and Group Provisioning
- Group Policy Object (GPO) Creation and Linking
- Password Policy Enforcement
- Account Lifecycle Management (Create, Modify, Disable)
- Security-Aware Offboarding Procedures
- VirtualBox Virtualization

---

## Related Projects

- [ServiceNow ITSM Help Desk Lab](https://github.com/Marquisb2170506/servicenow-itsm-lab) — The same three scenarios from this lab (account unlock, password reset, terminated employee disable) were formally documented as ServiceNow incident tickets, demonstrating the full IT support workflow from Active Directory action to ticket closure.

---

## Contact

**Marquis Borney**  
Email: marquisb.2315@gmail.com  
Location: St. Louis, MO (Open to Remote)  
LinkedIn: [linkedin.com/in/marquis-borney-717326102](https://www.linkedin.com/in/marquis-borney-717326102)
