# 🔴 Linux Cron Job Privilege Escalation Lab

<p align="center">

![Platform](https://img.shields.io/badge/Platform-Kali%20Linux-blue?style=for-the-badge)
![Target](https://img.shields.io/badge/Target-Ubuntu%20Server-orange?style=for-the-badge)
![Technique](https://img.shields.io/badge/Technique-Cron%20Privilege%20Escalation-red?style=for-the-badge)
![Access](https://img.shields.io/badge/Access-SSH-purple?style=for-the-badge)
![Impact](https://img.shields.io/badge/Impact-Root%20Access-critical?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

</p>

---

# 📌 Overview

This project demonstrates a practical **Linux Privilege Escalation** scenario caused by an insecure **Cron Job configuration**.

The lab simulates a realistic attack path in which an attacker first gains low-privileged access through **SSH**, performs local enumeration, discovers a **root-level Cron Job**, identifies insecure file permissions, and exploits the writable script to achieve **root privileges**.

The assessment was performed in a controlled virtual laboratory environment for educational and defensive cybersecurity purposes.

> ⚠️ **Disclaimer:** All activities were performed against an authorized laboratory system. No production or unauthorized systems were targeted.

---

# 🎯 Objectives

The primary objectives of this lab were to:

- Obtain initial access through SSH
- Verify the current user and privilege level
- Enumerate scheduled Cron Jobs
- Identify privileged scheduled tasks
- Analyze Cron configurations
- Inspect file permissions
- Identify writable files executed by root
- Demonstrate privilege escalation
- Verify root-level access
- Understand the security impact
- Develop appropriate mitigation strategies

---

# 🏗️ Lab Environment

| Component | Details |
|-----------|---------|
| Attacker Machine | Kali Linux |
| Target Machine | Ubuntu Server |
| Initial Access | SSH |
| Target User | `student` |
| Initial Privilege | Low Privileged User |
| Final Privilege | `root` |
| Vulnerability | Cron Job Misconfiguration |
| Attack Type | Local Privilege Escalation |
| Environment | Controlled Virtual Lab |

---

# 🛠️ Tools & Commands

| Tool / Command | Purpose |
|----------------|---------|
| Kali Linux | Attack Platform |
| Ubuntu Server | Target System |
| SSH | Initial Access |
| `whoami` | User Verification |
| `id` | Privilege Verification |
| `ls` | File / Directory Enumeration |
| `cat` | Configuration Analysis |
| Cron | Scheduled Task Analysis |
| File Permissions | Privilege Escalation Analysis |

---

# 🧪 Attack Methodology

The assessment followed this attack chain:

```text
SSH Initial Access
        │
        ▼
User & Privilege Enumeration
        │
        ▼
Cron Job Enumeration
        │
        ▼
Root Cron Job Discovery
        │
        ▼
Script Permission Analysis
        │
        ▼
World-Writable Script Identified
        │
        ▼
Script Modification
        │
        ▼
Cron Execution
        │
        ▼
Root Privilege Escalation

```

---


# 1️⃣ Initial Access Through SSH

The attack began with an SSH connection from the Kali Linux attacker machine to the Ubuntu Server.

# Command
```
ssh student@<target-ip>
```
After successful authentication, a remote shell was obtained.

# Current User Verification
```
whoami
```
# Output
```
student
```
The attacker initially had access as a low-privileged user.



---


# 2️⃣ Initial Privilege Enumeration

The current user's privileges were verified using:
```
id
```
# Output
```
uid=1001(student)
```
The account did not have administrative privileges.
This established the starting point for the privilege escalation phase.


---

# 3️⃣ Cron Job Enumeration

The attacker searched for system Cron configurations.
# Command
```
ls -la /etc/cron*
```
During enumeration, a custom Cron configuration was identified:
```
/etc/cron.d/backup
```
This configuration required further analysis because scheduled tasks running with elevated privileges can become potential privilege escalation vectors when incorrectly configured.


---


# 4️⃣ Cron Job Analysis

The discovered Cron configuration was reviewed.

# Command
```
cat /etc/cron.d/backup
```
# Output
```
* * * * * root /home/student/backup.sh
```

# Analysis

The Cron Job:
- Executes every minute
- Runs as root
- Executes /home/student/backup.sh
This created a potential privilege escalation path because the executed script was located inside a user's home directory.

# Attack Surface
```
Cron
 │
 ├── Schedule: Every Minute
 │
 ├── User: root
 │
 └── Script: /home/student/backup.sh
```


---

 
# 5️⃣ File Permission Analysis

The permissions of the Cron-executed script were inspected.
# Command
```
ls -la /home/student/backup.sh
```
# Output
```
-rwxrwxrwx 1 root root backup.sh
```
The script had 777 permissions.


# 🚨 Vulnerability Identified
The permission configuration allowed any local user to modify the script.
```
-rwxrwxrwx
  │ │ │
  │ │ └── Others: Read + Write + Execute
  │ └──── Group: Read + Write + Execute
  └────── Owner: Read + Write + Execute
  ```
# Security Issue
The combination of:
```
User-Writable Script
        +
Root Cron Execution
        =
Privilege Escalation
```
The critical issue was not simply that the file was executable, but that a low-privileged user could modify a script that would subsequently execute with root privileges.



---


# 6️⃣ Exploitation

The identified writable script was modified within the authorized lab environment.
Because the Cron Job executed the script as root, the modified script was subsequently executed with elevated privileges.

# Exploitation Flow
```
student
   │
   ▼
Writable backup.sh
   │
   ▼
Modify Script
   │
   ▼
Cron Executes Script
   │
   ▼
Execution as root
```
The Cron service automatically triggered the modified script according to its configured schedule.


---

# 7️⃣ Privilege Escalation Verification

After the Cron Job executed the modified script, elevated privileges were verified.

Command
```
whoami
```
Output
```
root
```

# Additional verification:
```
id
```
# Output
```
uid=0(root)
```
# Final Result
```
Low Privileged User
        │
        ▼
    student
        │
        ▼
Privilege Escalation
        │
        ▼
      root
```
The attacker successfully escalated from a standard user to root-level access.


---



# 🔥 Complete Attack Chain
```
┌────────────────────────────┐
│        Kali Linux          │
└──────────────┬─────────────┘
               │
               │ SSH Login
               ▼
┌────────────────────────────┐
│       Ubuntu Server        │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│ Low Privileged User        │
│          student           │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│   Cron Job Enumeration     │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│ Root Cron Job Discovered   │
│ /etc/cron.d/backup         │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│ Writable backup.sh         │
│ Permissions: 777           │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│     Script Modification    │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│     Cron Execution         │
│        as root             │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│       ROOT ACCESS          │
└────────────────────────────┘
```
---



# 💥 Impact

Successful exploitation resulted in complete root-level access to the target system.
An attacker with root privileges could potentially:

- Execute privileged commands
- Access protected files
- Modify system configurations
- Create privileged accounts
- Modify security controls
- Access sensitive information
- Establish persistence
- Compromise system integrity


# Security Impact
```
Initial Access
      │
      ▼
Low Privilege
      │
      ▼
Privilege Escalation
      │
      ▼
     Root
      │
      ▼
Full System Compromise
```

# 🔎 Root Cause

The privilege escalation was possible because of multiple insecure configuration choices:

# 1. Root Cron Execution
A Cron Job executed a script as root.

# 2. User-Controlled Location
The script was stored under:
```
/home/student/
```
# 3. Insecure Permissions
The script was configured with:
```
777
```
# 4. Missing Permission Boundary
A low-privileged user could modify a file executed by a privileged process.


---


# 🛡️ Mitigation Recommendations
# 1. Restrict File Permissions

Do not allow privileged scripts to be writable by untrusted users.

For example:
```
chmod 755 backup.sh
```
Permissions should be selected according to the required ownership and execution model.

# 2. Use Secure Script Locations
Privileged Cron scripts should be stored in properly controlled system directories rather than user-writable locations.

# 3. Verify File Ownership
Ensure privileged scripts are owned by an appropriate administrative account.
Example:
```
chown root:root /path/to/backup.sh
```
# 4. Audit Cron Jobs

Regularly review:
```
/etc/crontab
/etc/cron.d/
/etc/cron.hourly/
/etc/cron.daily/
/etc/cron.weekly/
/etc/cron.monthly/
```
Look for scripts executed with elevated privileges.

# 5. Monitor File Modifications
Implement file integrity monitoring to detect unauthorized changes to:

- Cron configurations
- Privileged scripts
- System binaries
- Security-sensitive files

# 6. Apply Least Privilege
Scheduled tasks should run with the minimum privileges required to perform their intended function.



---


# 📊 Finding Summary

- Finding	Severity	Impact
- Root Cron Job Executes User-Space Script	High	Privileged execution
- World-Writable Script	Critical	Unauthorized modification
- Local Privilege Escalation	Critical	Root-level compromise


---



# 🧠 Skills Demonstrated
This project demonstrates practical experience with:

- Linux Privilege Escalation
- SSH Enumeration
- Linux System Enumeration
- Cron Job Enumeration
- Scheduled Task Analysis
- File Permission Analysis
- Linux Security
- Local Privilege Escalation
- Vulnerability Identification
- Exploitation Validation
- Security Impact Assessment
- Security Hardening
- Penetration Testing Documentation


---


# 🏁 Conclusion

This Linux Cron Job Privilege Escalation Lab successfully demonstrated a complete local privilege escalation attack path.
The attacker gained initial access through SSH as the student user, performed local enumeration, discovered a root-level Cron Job, and identified that the Cron-executed script had insecure 777 permissions.
Because the low-privileged user could modify a script executed by root, the configuration created a critical privilege escalation vulnerability.
The vulnerability was successfully validated in the controlled lab, resulting in root-level access.
This project strengthened practical skills in Linux Enumeration, Cron Job Analysis, File Permission Auditing, Privilege Escalation, Vulnerability Assessment, and Security Hardening.


---


# ⚠️ Disclaimer

This project was conducted exclusively in an authorized and isolated virtual laboratory environment.
No production, third-party, or unauthorized systems were targeted.
The techniques documented in this repository are intended strictly for educational, penetration testing, and defensive cybersecurity purposes.


---


# 👨‍💻 Author
# Muhammad Talha

Cybersecurity | SOC Analyst | Detection Engineering | Threat Hunting | Blue Team | Red Team | Purple Team
