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

## What Was Built

### 1. Domain Controller Deployment
- Installed Windows Server 2022 in VirtualBox
- Promoted server to Domain Controller for domain `marquis.local`
- Configured DNS to point to the Domain Controller

### 2. Organizational Unit (OU) Structure
Created a logical OU structure mirroring a real corporate environment:

```
marquis.local
├── IT
├── HR
└── Finance
```

### 3. User Accounts Provisioned
Created 6 domain user accounts across departments:

| Username | Department | Role |
|----------|-----------|------|
| jsmith | IT | IT Technician |
| mwilliams | HR | HR Coordinator |
| tharris | Finance | Financial Analyst |
| amorgan | IT | Systems Admin |
| ljones | HR | HR Manager |
| rthompson | Finance | Finance Manager |

### 4. Security Groups
- Created department-level Security Groups (IT-Staff, HR-Staff, Finance-Staff)
- Added users to appropriate groups for resource access control

### 5. Group Policy Object (GPO)
Authored and linked a GPO enforcing domain-wide password security policy:

| Policy Setting | Value |
|----------------|-------|
| Minimum password length | 10 characters |
| Password complexity | Enabled |
| Maximum password age | 90 days |
| Account lockout threshold | 5 failed attempts |
| Lockout duration | 30 minutes |

---

## Tier 1 Help Desk Simulations

The following real-world help desk scenarios were simulated in this lab:

### Scenario 1 — Account Unlock
**Issue:** User `jsmith` locked out after multiple failed login attempts.  
**Action:** Located account in ADUC → Right-clicked → Unlocked account.  
**Result:** User confirmed successful login.

### Scenario 2 — Password Reset
**Issue:** User `mwilliams` forgot domain password after vacation.  
**Action:** Reset password in ADUC → Enabled "User must change password at next logon."  
**Result:** User logged in with temporary password and set new password.

### Scenario 3 — Account Disable (Terminated Employee)
**Issue:** HR requested immediate account disable for terminated employee `tharris`.  
**Action:** Located account in ADUC → Disabled account → Moved to Disabled Users OU.  
**Result:** Account disabled within 15 minutes of request. Security policy followed.

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

## Screenshots

Screenshots documenting each phase of this lab are included in the `/screenshots` folder of this repository.

---

## Related Projects

- [ServiceNow ITSM Help Desk Lab](https://github.com/Marquisb2170506/servicenow-itsm-lab) — The same three scenarios from this lab were formally documented as ServiceNow incident tickets, demonstrating the full IT support workflow from Active Directory action to ticket closure.

---

## Contact

**Marquis Borney**  
Email: marquisb.2315@gmail.com  
Location: St. Louis, MO (Open to Remote)  
LinkedIn: [linkedin.com/in/marquis-borney](https://linkedin.com/in/marquis-borney)
