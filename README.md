# 🛡️ Active Directory Home SOC Lab 🛡️
![windows-server-azure-banner-900x450](https://github.com/user-attachments/assets/6042f415-ce54-45d7-9065-7d905c40cf7e)


---

## Introduction
- This project is a hands-on Active Directory (AD) home lab designed to help me build real SOC Analyst skills while I finish my cybersecurity degree. Since most security incidents in the real world involve Windows domains, I wanted to create a small AD environment where I could learn how attacks actually happen and how defenders detect them.

- In this lab, I set up a Windows Server 2022 domain controller and connected Windows 11 clients to it. From there, I practiced tasks that SOC analysts deal with every day monitoring authentication events, detecting suspicious behavior, reviewing logs, and testing common attack techniques in a safe and controlled environment.

---

## Project Steps

### 1. Enabling Hyper-V on Windows 11
- Enabled Hyper-V in Windows Optional Features

**Enabling Hyper-V on Host System**
<img width="411" height="364" alt="1st step enabling hyper-v" src="https://github.com/user-attachments/assets/0868e33a-4562-469a-93cd-ae6abbb33a6c" />


---

### 2. Creating a Virtual Network (Internal Switch)
- Created an Internal Virtual Switch
- Configured network settings

**Created Virtual Network for AD Environment**
<img width="1095" height="710" alt="2nd step creating virtual network" src="https://github.com/user-attachments/assets/0094beb4-df2d-46bb-8fa3-b134f45b3fe9" />


---

### 3. Downloading Windows Server 2022 ISO + Creating VM
- Downloaded Windows Server 2022 ISO from Microsoft Evaluation Center
- Created a new Generation 2 Hyper-V VM for the domain controller
- Assigned CPU, RAM, and virtual disk to prepare for AD installation

**Domain Controller VM Configuration Summary**
<img width="752" height="556" alt="3rd step domain controller vm summary" src="https://github.com/user-attachments/assets/a70cd997-01e9-4b17-b69d-7a8d82f829f2" />


---

### 4. Installing Windows Server + Setting IP/Naming Server
- Installed Windows Server 2022 using the downloaded ISO
- Set a static IP address (10.0.0.10) for the DC
- Named the server DC01-Mcvay before promoting it to a domain controller

**Static IP Address and DNS assigned to Domain Controller**
<img width="1413" height="803" alt="4th step assigning ip" src="https://github.com/user-attachments/assets/8b8366a3-6229-4729-8111-e09b97808c94" />


---

### 5. Renaming Server
- Opened System Properties and changed hostname
- Restarted server to apply new computer name
- Verified renaming before AD DS installation

**Server renamed to DC01-Mcvay**
<img width="778" height="532" alt="5th step renaming Server" src="https://github.com/user-attachments/assets/83db8283-302e-4a43-b65b-9d68423cc833" />


---

### 6. Active Directory Domain Services
- Added the AD Domain Services role using Server Manager
- Included DNS Server role in the installation
- Prepared server for promotion to domain controller

**Installing AD Domain Services**
<img width="971" height="605" alt="6th step installing AD Domain Services" src="https://github.com/user-attachments/assets/58a911ba-bdf6-46cc-99b2-9411d8b78337" />


---

### 7. Results of Forest Creation and Server Promotion
- Created new AD forest named lab.local
- Completed server promotion to domain controller
- Restarted server to finalize domain services configuration

**Domain Controller Promotion Completion**
<img width="871" height="654" alt="7th step Domain Controller Promotion" src="https://github.com/user-attachments/assets/50fe163c-bec3-45f4-8e82-419cd1d2d033" />


---

### 8. Created Organizational Units + Users
- Created OUs for Users, Computers, and Admin accounts
- Started building domain structure for realistic enterprise organization
- Prepared environment for Group Policy testing

**Organizational Units Created for Domain Structure**
<img width="962" height="594" alt="8th step units created" src="https://github.com/user-attachments/assets/a51ad6c6-090b-4cd9-b43c-20a63c61d90d" />


---

### 9. Creating Users
- Added new standard user accounts inside the Users OU
- Assigned secure passwords and logon settings
- Created an admin-level account with elevated domain privileges

**New Domain User Created "Luke Skywalker"**
<img width="827" height="678" alt="9th step user creation" src="https://github.com/user-attachments/assets/aad033ef-3b80-4a69-a057-8a20b92fc6f5" />

**Privilege Assignment for admin1**
<img width="1000" height="783" alt="9th step  1 assignment for admin" src="https://github.com/user-attachments/assets/8931dbdd-240f-49bb-80d6-be080fe40dc9" />


---

### 10. Creating Windows 11 Client VM
- Created a new Windows 11 Pro VM in Hyper-V
- Allocated CPU, RAM, and virtual disk resources
- Prepared workstation for domain join testing

**Windows 11 Client VM Configuration**
<img width="820" height="631" alt="Windows 11 Client VM Configuration" src="https://github.com/user-attachments/assets/8f714361-9baa-4990-9a01-cb325b5b401f" />


---

### 11. Joining Windows 11 to Domain
- Set the Windows 11 VM DNS server to 10.0.0.10 (Domain Controller)
- Verified connectivity using ping between client and DC
- Joined Windows 11 machine to lab.local successfully

**Configured Client to Use Domain Controller as DNS**
<img width="957" height="684" alt="Domain controller as dns " src="https://github.com/user-attachments/assets/25cd353f-eed3-4749-99dc-91222cb710ab" />

**Successfully Joined WIN11-Mcvay Client to lab.local**
<img width="1210" height="665" alt="Client joined to lab local" src="https://github.com/user-attachments/assets/f055e8e1-4e91-4d07-a180-304fa45297b5" />


---

### 12. Group Policy Configuration
- Created Baseline-Security GPO for domain hardening
- Enabled Windows Firewall and ICMP exceptions across all profiles
- Added auditing policies for Logon/Logoff, Account Logon, and Object Access

**Baseline Security GPO Configuration**
<img width="981" height="639" alt="image" src="https://github.com/user-attachments/assets/005afe34-3d21-4fa8-9f14-a0b509131924" />
**Windows Firewall Configuration**
<img width="996" height="681" alt="image" src="https://github.com/user-attachments/assets/abc31dfa-3835-45cd-bcb0-297d55c6ee33" />


---

### 13. SOC Anaylst-Style Monitoring
- Reviewed Event Viewer logs on both client and domain controller
- Observed successful logons (Event ID 4624)
- Analyzed events the same way SOC analysts review authentication logs

**Successful Logon Event Captured (4624)**
<img width="780" height="339" alt="image" src="https://github.com/user-attachments/assets/33f7b06b-bae1-43c4-8ddc-19752743a352" />

---
## Conclusion
This project allowed me to build and secure an Active Directory environment from scratch while gaining hands-on experience with domain management, GPO hardening, and Windows security auditing. Completing this lab strengthened my understanding of how authentication, logging, and policy enforcement work in a real enterprise setup. It also helped me develop practical troubleshooting and analysis skills that are directly relevant to a SOC Analyst role.

---
## 🧠 What I Learned
- Deploying Active Directory from scratch
- Managing domain users, groups, and OUs
- Applying GPOs for real-world security baselines
- Breaking and fixing domain connectivity
- Understanding Windows firewall profiles
- Reading and interpreting security event logs





