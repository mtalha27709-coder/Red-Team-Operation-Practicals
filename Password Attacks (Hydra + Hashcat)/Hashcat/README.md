# Hashcat Password Cracking Lab

## Objective

Demonstrate offline password hash cracking using Hashcat and a dictionary attack.

---

## Lab Environment

- Operating System: Kali Linux
- Tool: Hashcat
- Hash Type: MD5
- Wordlist: rockyou.txt

---

## Tools Used

- Hashcat
- rockyou.txt
- md5sum

---

## Procedure

### 1. Generate MD5 Hash

```bash
echo -n "password" | md5sum
```

Example Output:

```
5f4dcc3b5aa765d61d8327deb882cf99
```

### 2. Save Hash

```bash
nano hash.txt
```

Paste:

```
5f4dcc3b5aa765d61d8327deb882cf99
```

### 3. Run Hashcat

```bash
hashcat -m 0 hash.txt /usr/share/wordlists/rockyou.txt.gz
```

### 4. Display Cracked Password

```bash
hashcat -m 0 hash.txt --show
```

Example Output:

```
5f4dcc3b5aa765d61d8327deb882cf99:password
```

---

## Result

- Successfully recovered the plaintext password using a dictionary attack.
- Demonstrated the risk of weak and commonly used passwords.

---

## Mitigation

- Use long and unique passwords.
- Store passwords using modern hashing algorithms such as Argon2 or bcrypt.
- Implement password complexity requirements.
- Avoid common passwords found in public wordlists.

---

## Disclaimer

This exercise was performed in a controlled lab environment for educational and ethical cybersecurity training purposes only.