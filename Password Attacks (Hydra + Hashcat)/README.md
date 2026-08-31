# 🔐 Password Attacks — Hydra & Hashcat

<p align="center">

![Platform](https://img.shields.io/badge/Platform-Kali%20Linux-blue?style=for-the-badge)
![Hydra](https://img.shields.io/badge/Tool-Hydra-red?style=for-the-badge)
![Hashcat](https://img.shields.io/badge/Tool-Hashcat-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

</p>

---

## 📌 Overview

This project demonstrates two fundamental password attack techniques used in authorized security testing and cybersecurity training:

- **Hydra** — Online password attack
- **Hashcat** — Offline password hash cracking

The lab focuses on understanding how weak credentials can be compromised and how organizations can defend against password-based attacks.

---

## 🎯 Objectives

- Perform an authorized online password attack using Hydra.
- Perform offline hash cracking using Hashcat.
- Understand online vs. offline password attacks.
- Analyze the security impact of weak passwords.
- Identify defensive measures against credential attacks.

---

## 🧪 Lab Environment

| Component | Details |
|---|---|
| Attacker | Kali Linux |
| Hydra Target | Ubuntu SSH Service |
| Hashcat Target | MD5 Hash |
| Wordlist | `rockyou.txt` |
| Environment | Controlled Virtual Lab |

---

## 🛠️ Tools Used

- Hydra
- Hashcat
- OpenSSH
- `md5sum`
- RockYou Wordlist

---

# 1️⃣ Hydra — Online Password Attack

Hydra was used to perform an authorized dictionary-based password attack against an SSH service.

### Concepts Demonstrated

- SSH Authentication
- Online Password Attacks
- Dictionary Attacks
- Weak Password Identification

### Result

✅ Successful authentication was demonstrated in the controlled lab environment.

---

# 2️⃣ Hashcat — Offline Password Cracking

Hashcat was used to perform an offline dictionary attack against an MD5 password hash using the RockYou wordlist.

### Concepts Demonstrated

- Password Hashing
- MD5
- Offline Cracking
- Dictionary Attacks
- Password Recovery

### Result

✅ The password hash was successfully tested against the provided wordlist.

---

## 🔄 Online vs Offline Attack

| Feature | Hydra | Hashcat |
|---|---|---|
| Attack Type | Online | Offline |
| Target | Authentication Service | Password Hash |
| Network Required | Yes | No |
| Main Risk | Account Compromise | Fast Password Recovery |
| Defense | MFA, Rate Limiting | Strong Password Hashing |

---

## 🛡️ Defensive Recommendations

- Use strong and unique passwords.
- Enable MFA.
- Implement login rate limiting.
- Use account lockout controls carefully.
- Disable password authentication where practical.
- Store passwords using modern algorithms such as **Argon2id** or **bcrypt**.
- Monitor authentication logs for brute-force activity.

---

## 📂 Project Structure

```text
Password_Attacks/
│
├── README.md
├── Hydra_Password_Attack.md
├── Hashcat_Password_Cracking.md
└── screenshots/
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

---


## 👨‍💻 Author
## Muhammad Talha

Cybersecurity | SOC | Red Team | Blue Team | Detection Engineering
