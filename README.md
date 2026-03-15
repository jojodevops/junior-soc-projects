## Purpose of This Repository

This repository contains my hands-on cybersecurity investigations focused on phishing, smishing, and other social engineering attacks. Each project documents a real-world case, including evidence collection, OSINT analysis, risk evaluation, and defensive recommendations. The goal is to demonstrate practical SOC analyst skills through structured, professional incident documentation.

## What This Repository Shows

- Ability to analyze real malicious messages (SMS, email, links).
- Use of OSINT tools such as WHOIS, DNS lookups, VirusTotal, and IP reputation checks.
- Identification and documentation of Indicators of Compromise (IOCs).
- Clear and structured incident reporting aligned with SOC workflows.
- Understanding of social engineering techniques used by attackers.
- Professional documentation following cybersecurity best practices.

## Structure of Each Project

Each investigation is organized in its own folder and includes:

- A dedicated README.md with the full analysis.
- An /evidence folder containing screenshots used in the investigation.
- A step-by-step breakdown of the attack and the defensive reasoning.

Example structure:

phishing-analysis-01/
    README.md
    evidence/
    
## Skills Demonstrated

- OSINT investigation
- Threat analysis
- Smishing and phishing detection
- Sender ID spoofing identification
- DNS and WHOIS interpretation
- Social engineering analysis
- Documentation and reporting for SOC environments

## Why These Projects Matter

These cases simulate the type of incidents handled by Tier 1 SOC Analysts and IT Support Security roles. They demonstrate:

- Real-world analytical thinking
- Ability to communicate findings clearly
- Understanding of attacker behavior
- Defensive mindset and risk evaluation

This repository acts as a portfolio of my cybersecurity investigation skills.

## Current Projects

### Completed
- **phishing-analysis-01** — Completed smishing case involving sender ID spoofing and abuse of legitimate AWS infrastructure.

### Upcoming Projects 

- **siem-log-analysis-01** — Event triage using Microsoft Sentinel (failed logins, brute force patterns, suspicious authentication).
- **siem-detection-rules-01** — Create and tune detection rules mapped to MITRE ATT&CK.
- **phishing-investigation-02** — Full investigation of a phishing email (headers, URLs, attachments, sandboxing).
- **domain-osint-01** — OSINT investigation of a suspicious domain using WHOIS, DNS, IP reputation, and threat intel.
- **ip-reputation-analysis-01** — Investigation of a malicious IP using OSINT and enrichment tools.
- **xdr-alert-analysis-01** — Endpoint alert investigation using SentinelOne or Microsoft Defender XDR.
- **incident-triage-01** — Simulated SOC triage workflow (initial detection → analysis → escalation decision).
- **malicious-link-analysis-01** — Deep analysis of a malicious URL using redirect tracing and sandbox tools.
- **vulnerability-scan-review-01** — Review and prioritization of vulnerabilities using Tenable/Rapid7 methodology.
- **linux-security-basics-01** — Basic Linux log analysis for SOC investigations.
- **windows-security-basics-01** — Windows Event Viewer investigation (4624/4625/4688/7045 events).
- **mitre-attack-mapping-01** — Mapping an attack scenario to MITRE ATT&CK techniques.
- **cyber-kill-chain-01** — Documenting an incident using the Cyber Kill Chain model.
- **security-tooling-01** — Configuration and tuning of a security tool (SIEM, EDR, or log source).
- **customer-support-simulation-01** — SOC-style communication: writing a professional incident summary for a client.

More projects will be added as I continue building real-world SOC analyst skills.
