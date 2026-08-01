# Linux Cron Job Privilege Escalation Lab

## Overview

This lab demonstrates a Linux privilege escalation scenario caused by an insecure Cron Job configuration.

The objective was to simulate a real-world attack where an attacker gains initial access through SSH, performs enumeration, discovers a vulnerable root Cron job, exploits weak file permissions, and escalates privileges to root.

---

# Lab Environment

| Component | Details |
|---|---|
| Attacker Machine | Kali Linux |
| Target Machine | Ubuntu Server |
| Initial Access Method | SSH |
| Target User | student |
| Initial Privilege | Low Privileged User |
| Final Privilege | Root |
| Vulnerability Type | Cron Job Misconfiguration |

---

# Objective

- Gain initial access through SSH
- Enumerate scheduled Cron jobs
- Identify insecure Cron configurations
- Analyze file permissions
- Exploit writable scripts executed by root
- Achieve privilege escalation

---

# Attack Methodology

## 1. Initial Access Through SSH

The attacker used Kali Linux to connect to the Ubuntu server using SSH.

Command executed from Kali Linux:
- ssh student@<target-ip>
 

After successful authentication, a remote shell was obtained.

- Verify current user:
  whoami

- Output:
  student

The attacker now had low-privileged access to the target machine.


---



## 2. System Enumeration

The attacker started enumerating the target system to identify possible privilege escalation paths.

- Checked current privileges:
   id
- Output:
   uid=1001(student)

The user did not have administrative privileges.


---




## 3. Cron Job Enumeration

- The attacker searched for scheduled tasks:
   ls -la /etc/cron*
- During enumeration, a custom Cron configuration was discovered:
   /etc/cron.d/backup


---



## 4. Cron Job Analysis

- The Cron configuration was reviewed:
   cat /etc/cron.d/backup
-  Output:
  * * * * * root /home/student/backup.sh


Finding

The Cron job:
- Runs every minute
- Executes as root
- Runs the script:
- /home/student/backup.sh
- This indicated a possible privilege escalation opportunity.



---




## 5. File Permission Analysis

- The script permissions were checked:
   ls -la /home/student/backup.sh

- Output:
   -rwxrwxrwx 1 root root backup.sh


Vulnerability Identified

- The script had insecure permissions:
   777 Permissions


Meaning:

- Any user could read the file
- Any user could modify the file
- Any user could execute the file

Since the script was executed by root through Cron, modifying this file could lead to privilege escalation.



---




## 6. Exploitation

- The attacker modified the writable script.
- The Cron service automatically executed the modified script with root privileges.
- The execution was verified by checking the command output and root context.



---




## 7. Privilege Escalation Verification

- After successful exploitation:
  whoami


- Output:
  root


- Additional verification:
  id


- Output:
  uid=0(root)


- The attacker successfully escalated privileges from:
  student

- to:
  root


---





## - Attack Chain
Kali Linux
     |
     | SSH Login
     ?
Ubuntu Server
     |
     ?
Low Privileged User (student)
     |
     ?
Cron Job Enumeration
     |
     ?
Root Cron Script Discovery
     |
     ?
Weak File Permission Detection
     |
     ?
Script Modification
     |
     ?
Root Privilege Escalation



---




## 8. Impact

Successful exploitation allowed the attacker to:

- Gain complete root access
- Modify system files
- Access sensitive data
- Execute commands with administrative privileges
- Fully compromise the Linux system
- Root Cause

The vulnerability existed because:

- A root Cron job executed a script located in a user-controlled directory.
- The script had insecure 777 permissions.
- A low-privileged user could modify a file executed by root.
- Mitigation Recommendations

To prevent this vulnerability:

- Avoid executing user-writable scripts as root
- Restrict file permissions: chmod 755 backup.sh
- Regularly audit Cron jobs
- Monitor changes in scheduled tasks
- Apply the principle of least privilege
- Use file integrity monitoring solutions



---




## 9. Conclusion

- This lab successfully demonstrated a Linux Cron Job Privilege Escalation attack.

- The attacker gained initial access through SSH, identified a vulnerable root Cron job, exploited weak file permissions, and successfully obtained root privileges.