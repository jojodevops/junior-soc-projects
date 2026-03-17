# Log Analysis and Event Correlation - 03 

## 1. Overview 📘📝
This project documents the analysis of Windows Security Logs and Sysmon events related to the creation, authentication, and activity of a local user account named **“atacante”**. The investigation focuses on identifying key events, correlating them using the shared **LogonId**, and reconstructing the activity timeline to determine whether the behavior is suspicious.

The activity sequence shows:

1. Manual creation of a local user  
2. Immediate interactive logon  
3. Execution of PowerShell  
4. Interaction with system/security components  
---

## 2. Incident Summary ⚠️
A local user account named **“atacante”** was manually created on the workstation **FEEDACK**. Shortly after, the same account successfully authenticated locally and executed **PowerShell**, interacting with system and security components.

This pattern is consistent with scenarios where an attacker creates a local account to maintain access and perform post‑authentication actions.

---

## 3. Technical Evidence 🧪

### 3.1 Local User Creation — PowerShell (Administrator)
Extracted details:

- Command executed: `net user atacante Password123! /add`
- Account active: Yes  
- Group: Users  
- Password set manually  
- No expiration date  

This confirms the manual creation of a new local user account.


---

### 3.2 Successful Authentication — Event ID 4624 ✅
Extracted fields:

- Account Name: **atacante**  
- Workstation Name: **FEEDACK**  
- Logon Type: **2 (Interactive)**  
- Source Network Address: **127.0.0.1**  
- Process Name: `C:\Windows\System32\svchost.exe`  
- LogonId: **0x196DA2FA**

This event confirms that the newly created account authenticated successfully on the local machine.


---

### 3.3 PowerShell Execution — Event ID 4688 ⚙️
Extracted fields:

- New Process Name: `powershell.exe`  
- User: **FEEDACK\atacante**  
- Command Line: Non‑interactive PowerShell modifying ESET components  
- LogonId: **0x196DA2FA**

This shows that the authenticated user executed PowerShell shortly after logging in.


---

### 3.4 Sysmon Process Create — Event ID 1 🔍
Extracted fields:

- Image: `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`  
- Parent Image: `C:\Windows\explorer.exe`  
- User: **FEEDACK\atacante**  
- Integrity Level: Medium  
- LogonId: **0x196DA2FA**

Sysmon validates that the PowerShell binary was legitimate and executed within the same user session.

---

## 4. Manual LogonId Correlation 🔗
The same **LogonId: 0x196DA2FA** appears in:

- Event ID 4624 — Successful Logon  
- Event ID 4688 — PowerShell Process Creation  
- Sysmon Event ID 1 — Process Create  

This confirms that:

- The same session authenticated the user  
- The same session executed PowerShell  
- All events belong to a single activity chain  

This correlation technique is essential in SOC investigations when reconstructing activity across multiple log sources.

---

## 5. Indicators of Compromise (IOCs) 🧩

| Type | Value |
|------|-------|
| User | atacante |
| Process | C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe |
| LogonId | 0x196DA2FA |
| Source IP | 127.0.0.1 |

---

Although the binaries used are legitimate, the behavior is **suspicious** and consistent with local persistence or post‑exploitation activity. Further investigation is recommended.

---

## 7. Recommendations 🛡️
- Review the legitimacy of the user account **“atacante”**  
- Disable or remove the account if unauthorized  
- Audit scheduled tasks, services, and RunKeys for persistence  
- Review additional events tied to the same LogonId  
- Implement alerts for:
- Local user creation  
- PowerShell execution by newly created accounts  
- Modifications to security software  
