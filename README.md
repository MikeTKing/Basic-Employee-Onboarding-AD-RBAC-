# Basic-Employee-Onboarding-AD-RBAC-
Active Directory infrastructure rebuild for a fictional company called “Northstar Medical Group”. Includes domain setup, organizational structure, user provisioning, RBAC implementation, and incident resolution.

## Problem Statement
Northstar Medical Group's IT environment had been mismanaged by a previous MSP, leaving behind a domain with no consistent organizational structure. User accounts were provisioned manually and inconsistently, with no standardized naming conventions, department mapping, or group-based access control. This created real HIPAA compliance risk, since there was no reliable way to guarantee that staff only had access to the resources appropriate to their role and department. Without proper OU segmentation or RBAC, a misconfigured account (like an HR employee incorrectly placed in Operations) could go unnoticed and expose protected data to the wrong personnel.

## Solution Overview
I rebuilt the domain from scratch, standing up NMG.com and promoting the first domain controller before designing a clean organizational structure around four core departments: IT, HR, Finance, and Operations. Each department was given its own OU along with a matching security group (IT-Users, HR-Users, Finance-Users, Operations-Users) to enforce a flat RBAC model — access is scoped by department membership rather than individual, one-off permissions. User provisioning was standardized using PowerShell scripts with the ActiveDirectory module, ensuring every account was created with consistent naming conventions (first-initial + last name), correct UPNs, job titles, and department attributes, then automatically assigned to the correct security group. This structure was validated in a real incident (NMG-0047), where a misplaced user account and incorrect group membership were diagnosed and corrected, confirming that the OU/group design actually enforces the intended access boundaries.

## Video Walkthrough
[[Building Role Based Access in Active Directory](https://www.loom.com/share/e74d39d155864dae8380d302f939be1d)]

## Tools Used
* Windows Server
* Active Directory Domain Services
* VirtualBox
* UTM
* RBAC
* GitHub

## Project Timeline
* Day 1: Domain creation and domain controller promotion
* Day 2: Organizational unit and security group design
* Day 3: User provisioning and RBAC implementation
* Day 4: Incident response and resolution (NMG-0047)
* Day 5: Documentation and case study packaging

## Key Accomplishments
* Built NMG.com domain from scratch
* Automated user provisioning across 4 departments using PowerShell, replacing manual GUI-based account creation
* Diagnosed and resolved a real-world access control incident (NMG-0047) by correcting OU placement and group membership, restoring HIPAA-appropriate access boundaries
