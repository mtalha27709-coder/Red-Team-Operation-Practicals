# 🔵 OSINT Investigation Report

<p align="center">

![Platform](https://img.shields.io/badge/Investigation-Passive%20OSINT-blue?style=for-the-badge)
![Target](https://img.shields.io/badge/Target-cybrixen.com-orange?style=for-the-badge)
![Scope](https://img.shields.io/badge/Scope-Public%20Information-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

</p>

---

## 📌 Overview

This project demonstrates a **Passive Open Source Intelligence (OSINT) Investigation** of the publicly accessible domain **cybrixen.com**.

The investigation focused on collecting publicly available information, reviewing the domain's online footprint, identifying exposed assets, and assessing potential information leakage without performing active attacks.

> ⚠️ **Disclaimer:** Only passive OSINT techniques and publicly available information were used. No exploitation, intrusive scanning, or unauthorized access was performed.

---

## 🎯 Objectives

- Gather public domain information
- Review DNS records
- Analyze domain registration information
- Identify publicly exposed assets
- Perform search engine reconnaissance
- Review domain reputation
- Document findings
- Provide security recommendations

---

## 🛠️ Tools Used

- WHOIS
- Dig
- NSLookup
- Google Dorking
- theHarvester
- VirusTotal
- Shodan

---

## 🔎 Investigation Methodology

### 1️⃣ Domain & WHOIS Analysis

Reviewed:

- Domain registration
- Registrar information
- Registration dates
- Name servers

### 2️⃣ DNS Enumeration

Used `dig` and `nslookup` to review:

- A Records
- MX Records
- NS Records
- TXT Records

### 3️⃣ Search Engine Reconnaissance

Google search operators were used to identify publicly indexed resources.

```text
site:cybrixen.com
site:cybrixen.com login
site:cybrixen.com admin
filetype:pdf site:cybrixen.com
```

---

## Phase 5 — Email & Public Information Gathering

theHarvester was used to identify publicly available information such as:

- Email addresses
- Hostnames
- Public references

---

## Phase 6 — Reputation Analysis

The domain reputation was reviewed using:

- VirusTotal
- Shodan

---

# Investigation Findings

| Category | Result |
|----------|--------|
| WHOIS Information | Successfully Retrieved |
| DNS Records | Available |
| Google Indexing | Normal |
| Email Enumeration | Limited Public Information |
| VirusTotal Reputation | No Significant Issues Observed |
| Shodan | No Publicly Indexed Services Found |

---

# Security Assessment

During this passive OSINT investigation:

- No publicly exposed sensitive information was identified.
- No obvious security misconfigurations were observed.
- No publicly indexed services were identified through Shodan.
- The publicly available information appeared limited.

---

# Recommendations

- Continue monitoring exposed assets regularly.
- Review DNS configuration periodically.
- Maintain secure domain management practices.
- Perform regular external security assessments.
- Monitor domain reputation through public intelligence sources.

---

# Conclusion

The passive OSINT investigation successfully collected publicly available information related to the target domain.

Based on the information available during the assessment, no significant public security exposure or obvious information leakage was identified. The organization's publicly accessible footprint appeared well maintained from an OSINT perspective.

---

# Project Structure

```
OSINT-Investigation/
README.md
Investigation_Report.pdf
screenshots/
findings/
LICENSE
```

---

# Skills Demonstrated

- Passive Reconnaissance
- Open Source Intelligence (OSINT)
- DNS Enumeration
- Domain Investigation
- Information Gathering
- Security Reporting
- Public Exposure Assessment

---

# 🏁 Conclusion

This project demonstrated a practical passive OSINT investigation workflow using publicly available information.
The assessment covered domain intelligence, DNS analysis, search engine reconnaissance, public information gathering, and reputation analysis.
No significant public exposure was identified during the assessment, demonstrating the importance of continuously monitoring an organization's external digital footprint.


---

# 👨‍💻 Author
# Muhammad Talha

Cybersecurity | SOC Analyst | OSINT | Red Team | Blue Team | Detection Engineering
