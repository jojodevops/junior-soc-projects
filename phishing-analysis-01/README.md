# Smishing Analysis – "Stripe" Case
## 1. Summary
I received an SMS from a sender labeled “Stripe” containing a verification code and a link to stop receiving messages. Since I do not have a Stripe account, I considered the message suspicious. After performing OSINT analysis, I concluded that this was a smishing attempt using sender ID spoofing and abuse of legitimate AWS infrastructure through temporary redirects.

## 2. SMS Description
"Your Link verification code is: 498876. To stop receiving these messages, visit (Temporary link)"

## 3. Evidence

The following evidence was collected during the investigation:

- Screenshot of the SMS (link redacted for safety).
- VirusTotal analysis showing:
- Redirection to a legitimate domain.
- Final HTTP status code 404.
- Serving IP address 3.228.62.110 (AWS).
- WHOIS results confirming that link.com is a legitimate Stripe-owned domain.
- DNS lookup results showing multiple AWS IPs associated with support.link.com.


## 4. OSINT Technical Analysis

### WHOIS Analysis
A WHOIS lookup of `link.com` confirmed:
- The domain is legitimate and owned by Stripe.
- It was created in 1989 and is protected against unauthorized transfers.
- DNS infrastructure is hosted on AWS.

This indicates the attacker did not control the domain but abused a legitimate endpoint.

### DNS Lookup
DNS queries for `support.link.com` returned multiple AWS IPs:
- 3.106.27.78
- 52.62.31.47
- 13.238.83.218

This reflects load balancing and legitimate infrastructure.

### VirusTotal Analysis
VirusTotal showed:
- A redirect to a legitimate Stripe/Link support endpoint.
- Final response: **HTTP 404 Not Found**.
- Serving IP: **3.228.62.110** (AWS).
- No malware detected, consistent with smishing relying on social engineering rather than malicious files.

This suggests the attacker used a temporary redirect or abused an open redirect on a legitimate service.

## 5. Social Engineering Analysis

The message uses several social engineering techniques:

- **Authority impersonation** — Spoofing “Stripe” to appear trustworthy.
- **Urgency** — Presenting a verification code to imply immediate action.
- **Annoyance pressure** — Offering an “opt‑out” link to push the victim into clicking.
- **Minimal context** — Legitimate companies provide detailed context; attackers keep messages vague.
- **Psychological manipulation** — Combining urgency, authority, and annoyance increases the chance of user interaction.

These elements match common smishing patterns.

## 7. Risk Assessment (I classify this incident as Medium–High Risk)

**Potential impact if clicked:**
- Credential harvesting.
- Redirection to a phishing page (before expiration).
- Validation of my phone number for future attacks.
- Inclusion in targeted smishing campaigns.

Likelihood: High, due to the effectiveness of sender ID spoofing and fake verification codes.

## 8. Recommendations
- Avoid clicking links in unsolicited SMS messages.
- Block the spoofed sender.
- Report the message to the mobile carrier’s spam reporting service.
- Educate users about sender ID spoofing and fake verification codes.
- Monitor for future smishing attempts, as attackers often reuse validated numbers.
- Document incidents like this for awareness and training.
