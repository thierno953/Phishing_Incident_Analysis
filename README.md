# Phishing Incident Analysis

Two examples show my ability to analyze phishing attacks, assess risks, and give actionable recommendations. One is link-based (MetaMask), the other attachment-based (Duolingo).

---

## MetaMask Malicious Link

- Unicode obfuscation in sender name and text.
- Shortened URL (t.co) hides phishing destination.
- Key Recommendation: Filter emails with non-Latin characters in display name or subject if domain isn't the official brand. Use MFA for wallets.

---

##  Duolingo Malicious Attachment

- Password-protected ZIP attachment delivered via trusted services (Discord CDN, Zoho Mail).
- Valid SPF/DKIM/DMARC ensured delivery; the encrypted attachment bypassed content scanning.
- **Key Recommendation**: Scan all attachments, even from trusted sources, and educate users.

---

## Cross-Case Insight

- Attackers exploit legitimate services to bypass controls:

| Type       | Service Abused              | How Bypassed                            |
| ---------- | --------------------------- | --------------------------------------- |
| Link       | URL shortener, `.io` domain | Hides phishing URL, evades filters      |
| Attachment | Discord CDN, Zoho, OVH      | Trusted delivery, passes authentication |

- **Takeaway**: Defenses must focus on behavior: urgency, brand impersonation, and interactions with external platforms.

---

## Conclusion

Structured approach (5W/H, IOCs, MITRE ATT&CK) shows layered defense matters: technical controls, monitoring, and user awareness.


