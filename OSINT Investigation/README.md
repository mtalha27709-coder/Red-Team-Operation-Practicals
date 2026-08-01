# OSINT Investigation Report

## Overview

This project demonstrates a passive Open Source Intelligence (OSINT) investigation conducted against the publicly accessible domain **cybrixen.com**.

The objective was to collect publicly available information, analyze the organization's online footprint, identify exposed assets, and evaluate whether any obvious security concerns were visible without interacting with or attacking the target.

> **Disclaimer:** This investigation used only passive OSINT techniques and publicly available information. No exploitation, scanning, or unauthorized access was performed.

---

# Target

- Domain: cybrixen.com
- Investigation Type: Passive OSINT
- Scope: Publicly Available Information Only

---

# Objectives

- Gather publicly available domain information
- Identify DNS records
- Review domain registration information
- Search for exposed public assets
- Check public reputation
- Document findings
- Provide security recommendations

---

# Tools Used

- WHOIS
- Dig
- NSLookup
- Google Dorking
- theHarvester
- VirusTotal
- Shodan

---

# Investigation Methodology

## Phase 1 — Domain Identification

The target domain was selected for passive information gathering.

---

## Phase 2 — WHOIS Lookup

Information collected:

- Domain registration details
- Registrar
- Registration dates
- Name Servers

---

## Phase 3 — DNS Enumeration

Performed using:

- dig
- nslookup

Information reviewed:

- A Records
- MX Records
- NS Records
- TXT Records

---

## Phase 4 — Search Engine Investigation

Google Dorks were used to identify publicly indexed resources.

Examples:

- site:cybrixen.com
- site:cybrixen.com login
- site:cybrixen.com admin
- filetype:pdf site:cybrixen.com

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
?
??? README.md
??? Investigation_Report.pdf
??? screenshots/
??? findings/
??? LICENSE
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

# Author

**Talha**

Cyber Security Student