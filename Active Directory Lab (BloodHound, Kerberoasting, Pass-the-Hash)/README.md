# 🔴 Active Directory Red Team Attack Simulation Lab

<p align="center">

![Platform](https://img.shields.io/badge/Platform-Windows%20Server%20%7C%20Windows%2010-blue?style=for-the-badge)
![Attack](https://img.shields.io/badge/Attack-Active%20Directory-red?style=for-the-badge)
![Lab](https://img.shields.io/badge/Environment-Virtual%20Lab-success?style=for-the-badge)
![Tools](https://img.shields.io/badge/Tools-BloodHound%20%7C%20Impacket-orange?style=for-the-badge)

</p>

---

# 📌 Overview

This project demonstrates a **complete Active Directory Red Team attack simulation** performed within a secure and isolated enterprise lab environment.

The objective was to deploy an enterprise-style Active Directory infrastructure, enumerate domain assets, identify privilege escalation opportunities, perform Kerberos-based attacks, extract credentials, and simulate lateral movement using industry-standard offensive security tools.

The lab follows a realistic Red Team methodology aligned with common enterprise attack workflows while maintaining a defensive learning perspective.

---

# 🎯 Objectives

- Deploy an enterprise Active Directory environment
- Configure Domain Controller and Active Directory Domain Services (AD DS)
- Create and manage domain users and groups
- Join Windows clients to the domain
- Perform Active Directory reconnaissance
- Enumerate domain relationships with BloodHound
- Conduct Kerberoasting attacks
- Extract credential hashes using Impacket
- Simulate Pass-the-Hash authentication
- Understand attacker techniques and defensive considerations

---

# 🏗️ Lab Architecture

```
                    +-------------------------+
                    | Windows Server 2022     |
                    | Domain Controller       |
                    | DNS + Active Directory  |
                    +-----------+-------------+
                                |
                    lab.local Domain
                                |
               ------------------------------
               |                            |
               |                            |
      +--------+--------+          +--------+--------+
      | Windows 10      |          | Kali Linux      |
      | Domain Client   |          | Red Team Host   |
      +-----------------+          +-----------------+
```

---

# 💻 Lab Environment

## 🖥️ Domain Controller

| Component | Details |
|-----------|---------|
| Operating System | Windows Server |
| Hostname | DC01 |
| Role | Domain Controller |
| Services | Active Directory, DNS |
| Domain | lab.local |

---

## 🖥️ Client Machine

| Component | Details |
|-----------|---------|
| Operating System | Windows 10 |
| Role | Domain Joined Workstation |
| Purpose | Enterprise User Simulation |

---

## ⚔️ Red Team Machine

| Component | Details |
|-----------|---------|
| Operating System | Kali Linux |
| Role | Attacker Machine |

### Tools Used

- BloodHound
- SharpHound
- Impacket Toolkit
- secretsdump.py
- psexec.py
- GetUserSPNs.py
- PowerShell
- SMB
- Kerberos

---

# 🚀 Lab Deployment

## Phase 1 — Active Directory Deployment

- Installed Windows Server
- Configured Static IP Address
- Installed Active Directory Domain Services
- Promoted Server to Domain Controller
- Created Enterprise Domain
- Configured DNS

---

## Phase 2 — Domain Configuration

Created multiple enterprise user accounts.

### Domain Users

- Administrator
- Talha
- John
- helpdesk
- service_sql

---

## Phase 3 — Domain Join

The Windows 10 workstation was successfully joined to:

```
lab.local
```

Authentication and communication with the Domain Controller were verified successfully.

---

# ⚔️ Red Team Attack Simulation

---

# 1️⃣ Active Directory Enumeration

## Goal

Identify domain relationships, privileged users, attack paths, and misconfigurations.

### Tool

- BloodHound
- SharpHound

### Activities

- Collected AD data
- Imported collected data
- Mapped user relationships
- Enumerated groups
- Identified privileged accounts
- Analyzed attack paths

### Key Findings

✔ Privileged Groups

✔ User Relationships

✔ Domain Trust Information

✔ Attack Path Visualization

---

# 2️⃣ Kerberoasting Attack

## Goal

Identify Service Principal Names (SPNs) and request Kerberos service tickets for offline password cracking.

### Tool

- GetUserSPNs.py

### Target Account

```
service_sql
```

### Attack Workflow

```
Domain User
      │
      ▼
Request TGS Ticket
      │
      ▼
Extract Kerberos Hash
      │
      ▼
Offline Password Analysis
```

---

# 3️⃣ Credential Dumping

## Goal

Extract Windows credentials from the Domain Controller.

### Tool

- secretsdump.py

### Extracted Artifacts

- NTLM Hashes
- Local SAM Hashes
- Kerberos Keys
- Domain Accounts
- RID Information

---

# 4️⃣ Pass-the-Hash Attack

## Goal

Authenticate without knowing the user's password by using NTLM hashes.

### Tool

- psexec.py

### Attack Flow

```
Extract NTLM Hash
        │
        ▼
Authenticate
        │
        ▼
Remote Command Execution
```

### Result

✅ Successful authentication using NTLM hashes.

---

# 🔍 Attack Chain

```
Deploy Active Directory
          │
          ▼
Domain Enumeration
          │
          ▼
BloodHound Analysis
          │
          ▼
Kerberoasting
          │
          ▼
Credential Dumping
          │
          ▼
Pass-the-Hash
          │
          ▼
Domain Compromise Simulation
```

---

# 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| Windows Server | Domain Controller |
| Windows 10 | Domain Workstation |
| Kali Linux | Attack Platform |
| BloodHound | Attack Path Analysis |
| SharpHound | Data Collection |
| Impacket | Offensive Toolkit |
| GetUserSPNs | Kerberoasting |
| secretsdump | Credential Extraction |
| psexec | Pass-the-Hash |
| PowerShell | Administration |

---

# 🛡️ Security Concepts Covered

- Active Directory Security
- Identity & Access Management
- Domain Enumeration
- BloodHound Analysis
- Kerberoasting
- Credential Dumping
- NTLM Authentication
- Pass-the-Hash
- Lateral Movement
- Privilege Escalation
- Enterprise Attack Methodology

---

# 📂 Project Structure

```
Active Directory Lab/

│
├── README.md
├── Report.pdf
├── Screenshots/
├── BloodHound/
├── SharpHound Output/
├── Commands Used.md
├── Findings.md
├── MITRE ATT&CK Mapping.md
└── References.md
```

---

# 🎓 Skills Demonstrated

- Active Directory Administration
- Windows Domain Management
- BloodHound Enumeration
- Kerberoasting
- Credential Extraction
- Pass-the-Hash
- Offensive Security
- Red Team Operations
- Enterprise Attack Simulation
- Attack Path Analysis
- Documentation & Reporting

---

# ⚠️ Disclaimer

This project was conducted exclusively within a personal virtual lab environment for educational, research, and defensive cybersecurity purposes.

No production systems or unauthorized environments were targeted.

---

# 📈 Project Status

**✅ Completed Successfully**

### Covered Topics

- Active Directory Deployment
- Domain Administration
- BloodHound Enumeration
- Kerberoasting
- Credential Dumping
- Pass-the-Hash
- Red Team Methodology
- Enterprise Attack Simulation

---

# 👨‍💻 Author

## Muhammad Talha

**Cybersecurity | Red Team | Blue Team | Detection Engineering | SOC Operations**

⭐ If you found this project useful, consider giving the repository a **Star**.
