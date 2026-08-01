# Password Attacks (Hydra + Hashcat)

## Overview

This project demonstrates two fundamental password attack techniques commonly used during authorized security assessments and cybersecurity training.

- **Hydra** – Online password attack (Brute Force)
- **Hashcat** – Offline password hash cracking (Dictionary Attack)

The objective of this project is to understand how weak passwords can be identified and why organizations should enforce strong password policies and secure password storage.

---

## Project Objectives

- Perform an online password attack using Hydra.
- Perform an offline password cracking attack using Hashcat.
- Understand the difference between online and offline password attacks.
- Learn defensive measures against password-based attacks.

---

## Lab Environment

| Component | Description |
|-----------|-------------|
| Attacker Machine | Kali Linux |
| Target | Ubuntu SSH Service (Hydra Lab) |
| Password Cracking | MD5 Hash |
| Wordlist | rockyou.txt |

---

## Tools Used

- Hydra
- Hashcat
- OpenSSH
- md5sum
- rockyou.txt

---

## Project Structure

```
Password_Attacks/
?
??? Hydra_Password_Attack.md
??? Hashcat_Password_Cracking.md
??? README.md
??? screenshots/
```

---

## Attack 1 — Hydra

Hydra was used to perform an authorized online brute-force attack against an SSH service using a predefined password wordlist.

### Demonstrated Concepts

- SSH Authentication
- Password Brute Force
- Dictionary Attack
- Weak Password Discovery

---

## Attack 2 — Hashcat

Hashcat was used to perform an offline dictionary attack against an MD5 password hash using the RockYou wordlist.

### Demonstrated Concepts

- Password Hashing
- MD5 Hash Cracking
- Dictionary Attack
- Offline Password Recovery

---

## Learning Outcomes

After completing this project, I gained practical experience with:

- Password attack methodologies
- Online vs Offline password attacks
- Wordlist-based password cracking
- Password security best practices
- Ethical security testing within controlled lab environments

---

## Defensive Recommendations

- Use strong and unique passwords.
- Enable Multi-Factor Authentication (MFA).
- Implement account lockout policies.
- Disable password authentication where possible.
- Store passwords using secure hashing algorithms such as Argon2 or bcrypt.
- Continuously monitor authentication logs for suspicious login attempts.

---

## Disclaimer

This project was conducted entirely within a controlled and authorized laboratory environment for educational and ethical cybersecurity purposes. No unauthorized systems or third-party networks were targeted.