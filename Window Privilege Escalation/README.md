# 🔴 Windows Privilege Escalation Lab

<p align="center">

![Platform](https://img.shields.io/badge/Platform-Kali%20Linux-blue?style=for-the-badge)
![Target](https://img.shields.io/badge/Target-Windows%207-0078D6?style=for-the-badge)
![Technique](https://img.shields.io/badge/Technique-Privilege%20Escalation-red?style=for-the-badge)
![VM](https://img.shields.io/badge/Environment-VMware-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

</p>

---

## 📌 Overview

This project demonstrates the identification and analysis of common **Windows Privilege Escalation** misconfigurations in a controlled virtual lab.

The lab focused on post-exploitation enumeration, identifying potential escalation vectors, and understanding how insecure Windows configurations can lead to elevated privileges.

---

## 🎯 Objectives

- Understand Windows privilege escalation concepts.
- Perform post-exploitation enumeration.
- Identify common privilege escalation vectors.
- Analyze services, permissions, and configurations.
- Practice Windows security assessment in a safe lab.

---

## 🧪 Lab Environment

| Component | Details |
|---|---|
| Attacker | Kali Linux |
| Target | Windows 7 |
| Virtualization | VMware |
| Network | Host-Only |
| Testing Type | Privilege Escalation |

---

## 🔎 Enumeration Performed

- User & Privilege Enumeration
- System Information
- Installed Software
- Running Services
- Scheduled Tasks
- Registry Inspection
- File & Folder Permissions
- Environment Variables

---

## 🛠️ Tools Used

- WinPEAS
- CMD
- PowerShell
- WMIC
- AccessChk (Sysinternals)

---

## 💥 Privilege Escalation Techniques Studied

- Unquoted Service Paths
- Weak Service Permissions
- AlwaysInstallElevated
- Registry Misconfigurations
- Scheduled Task Misconfigurations
- Weak File Permissions
- Insecure Service Executables
- Stored Credentials
- DLL Hijacking — Concept

---

## 🧠 Key Learning Outcomes

- Improved Windows system enumeration skills.
- Learned how to identify privilege escalation opportunities.
- Strengthened understanding of Windows services and permissions.
- Practiced analyzing common security misconfigurations.
- Gained hands-on experience in a controlled lab environment.

---

## 📂 Project Structure

```text
Windows-Privilege-Escalation/
│
├── README.md
├── screenshots/
├── enumeration/
├── evidence/
└── report/
```

---

## 🏁 Conclusion

This lab provided practical experience in Windows post-exploitation enumeration and privilege escalation analysis.
It demonstrated how insecure services, permissions, registry settings, scheduled tasks, and other misconfigurations can create potential paths to elevated privileges.

---

## ⚠️ Disclaimer

This project was performed exclusively in a personal and authorized virtual laboratory environment for educational and defensive cybersecurity purposes.

---
## 👨‍💻 Author
## Muhammad Talha

Cybersecurity | SOC | Red Team | Blue Team | Detection Engineering
