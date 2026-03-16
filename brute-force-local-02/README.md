# Project 02 — Local Brute Force Attack in Windows 🔐💻

## 1. Overview 📘
This project documents a simulated **local brute force attack** on a Windows workstation. Multiple failed authentication attempts (Event ID **4625**) were intentionally generated, followed by a successful interactive login (Event ID **4624**). The goal is to demonstrate the ability to detect, analyze, and document authentication-related security events using Windows Event Viewer.

---

## 2. Incident Summary ⚠️
A user named **“atacante”** attempted several incorrect logins on the workstation **FEEDACK**, producing repeated failed authentication events. Eventually, the same user successfully authenticated locally, completing the brute force pattern.

This scenario replicates a common attack technique where an adversary repeatedly guesses credentials until access is obtained.

---

## 3. Technical Evidence 🧪

### 3.1 Failed Authentication — Event ID 4625 ❌
**Extracted fields:**
- **Account Name:** atacante  
- **Workstation Name:** FEEDACK  
- **Failure Reason:** Unknown user name or bad password  
- **Logon Type:** 2 (Interactive)  
- **Source Network Address:** 127.0.0.1  
- **Process Name:** `C:\Windows\System32\svchost.exe`  

These values confirm repeated **local** login failures using incorrect credentials.

---

### 3.2 Successful Authentication — Event ID 4624 ✅
**Extracted fields:**
- **Account Name:** atacante  
- **Workstation Name:** FEEDACK  
- **Logon Type:** 2 (Interactive)  
- **Source Network Address:** 127.0.0.1  
- **Process Name:** `C:\Windows\System32\svchost.exe`  

This event confirms that the attacker eventually logged in successfully.




