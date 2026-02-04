# Email Phishing Incident Analysis - Duolingo Impersonation

**Severity:** HIGH

**Incident ID:** 670-DUOLINGO 

**Analyst:** SancLogic

**Date:** 31 October 2025

---

## Executive Summary

A phishing email impersonating Duolingo targeted a business inbox. It included a password-protected ZIP attachment hosted on Discord. The user opened it, executed malware, and the workstation was compromised. This case highlights social engineering and encrypted attachments bypassing email security.

---

## WHO

- **Attacker**: Unknown (impersonating Duolingo)
- **Victim**: Business inbox (contractor)
- **Brand impersonated**: Duolingo

---

## WHAT

- Phishing email using a typosquatting domain
- Password-protected ZIP attachment containing malware
- Envelope From / Return-Path headers:

```sh
"Roger Chapman" <colla@duolingo-team[.]com>
Domain: duolingo-team[.]com
```

- User downloaded, extracted, and executed the file
- Automated analysis and endpoint detection confirmed malware execution

![Duolingo Impersonation](./assets/Duolingo_Impersonation_01.png)

![Duolingo Impersonation](./assets/Duolingo_Impersonation_02.png)

- **Payload URL:** `hxxps://cdn[.]discordapp[.]com/attachments/1432487189429616654/1433451752316997642/Duolingo_-_YouTube_Partnership[.]zip`
- **Archive Password:** `Duolingo`

---

## WHEN

- **Domain registered**: 10 July 2025
- **Email delivered**: 30 October 2025 - 13:48 UTC
- **Payload executed**: 30 October 2025 - ~15:19 UTC

---

## WHERE

- **Sender infrastructure**: Zoho Mail EU (136[.]143[.]171[.]19)
- **Domain hosting**: OVH Canada (51[.]222[.]203[.]80)
- **Payload hosting**: Discord CDN
- **Compromised system**: Contractor workstation

---

## WHY

- **Technical**:
  - Password-protected ZIP bypassed email scanning
  - Valid SPF/DKIM/DMARC allowed delivery
  - Domain aged 110+ days to bypass new-domain reputation filters

- **Human**:
  - Urgent and credible message
  - Financial incentive ($5,000 offer)

---

## HOW

- Attacker registered typosquatting domain
- Sent phishing email with fake partnership offer
- Included Discord link to password-protected ZIP
- User downloaded, extracted, and executed malware
- Endpoint compromised, C2 beaconing detected

---

## Indicators of Compromise (IOCs)

- **Domain**: `duolingo-team[.]com`
- **Email**: `Roger Chapman <colla@duolingo-team[.]com>`
- **Subject**: `Re: Duolingo | Collaboration proposal #8063`
- **Network**: `136[.]143[.]171[.]19, 51[.]222[.]203[.]80`
- **Payload**: `hxxps://cdn[.]discordapp[.]com/.../Duolingo_-_YouTube_Partnership[.]zip`
- **Password**: `Duolingo`
- **File Hash (SHA256)**: `3e3ee8ca0ae75aa9bc642c4ee2f924ec422bd714aa8e3361a2e6d61233644988`

---

## MITRE ATT&CK Mapping

- T1566.001 - Phishing via Email
- T1204.002 - User Execution
- T1027 - Encrypted Files (ZIP)
- T1583.001 - Domain Acquisition (typosquatting)
- T1105 - Ingress Tool Transfer (Discord CDN)

---

## Impact

- Confirmed execution of information-stealing malware
- C2 beaconing detected, exposing sensitive data and remote access risk

---

## Recommendations

- Block typosquatting domain and associated DNS records
- Implement policy to flag emails containing links to file-sharing/CDN domains (like Discord) when paired with urgent financial lures
- Quarantine external password-protected attachments
- Conduct user awareness training
- Report abuse to providers
