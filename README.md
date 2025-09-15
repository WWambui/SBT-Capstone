<h1 align="center">SBT Vulnerability Management 🛡️</h1>
<p align="center">
  Vulnerability assessment of the intentionally vulnerable system, Metasploitable 2
</p>

---

## 🚀 Project Overview

This is a capstone challenge from **Security Blue Team**'s *Intro to Vulnerability Management*.  
In this project I:

- Conducted vulnerability scanning using **Nessus**  
- Analyzed results to identify **critical issues**  
- Suggested appropriate **remediation steps**


---

## 🛠️ CHALLENGE SCENARIO
You are looking to move into a Vulnerability Analyst position within the security team, but first you have to prove your skills. You have been asked to conduct a vulnerability assessment of the intentionally vulnerable system, Metasploitable 2. You are required to work individually to conduct a scan of the system using Nessus (preferably within Kali Linux), you will host both systems yourself in virtual machines. You have been given a report template, which you must fill out completely and submit to be considered for the new role. Download the template to your local machine, conduct the scan, and fill out the questions, before uploading your report in the next section.



---

## ⚙️ Key Highlights

- Clear identification of **high & critical vulnerabilities**  
- Risk rating and priority for remediation  
- Suggestion of countermeasures / fixes, best practices  
- Learning outcome: understanding how automated vulnerability scanning tools work, how to interpret results, and how to take action  

---

##  ## CHALLENGE QUESTIONS
Provide an overview of the results from the scan. How vulnerable is this system?

The scan results indicate that the system is **critically vulnerable**. Several high-risk issues were identified, including remote backdoors, weak authentication, outdated operating systems, and insecure cryptographic protocols. An attacker exploiting these flaws could achieve **full remote compromise**, persistence, and lateral movement within the network.

<p align="center">
<img src="https://raw.githubusercontent.com/WWambui/SBT-Vulnerability-Management/main/Nessus_Scan.png" width="750"/>
<img src="https://raw.githubusercontent.com/WWambui/SBT-Vulnerability-Management/main/Scan_Evidence.png" width="750"/>

</p>
---

### Top 5 Most Serious Security Issues (In priority order - most important first)

1. **UnrealIRCd Backdoor Detection**  
   - A malicious backdoor exists in the installed version of UnrealIRCd.  
   - Exploitation would allow **unauthenticated attackers** to execute arbitrary commands with system privileges, leading to **complete compromise**.

2. **Bind Shell Backdoor Detected**  
   - A shell service is listening on a remote port without requiring authentication.  
   - An attacker can connect directly and run system commands, resulting in **immediate remote code execution**.

3. **Canonical Ubuntu Linux End of Life (8.04.x)**  
   - The operating system is no longer supported by the vendor and does not receive security updates.  
   - Attackers can exploit **unpatched vulnerabilities** to gain access, escalate privileges, or install malware.

4. **VNC Server Weak Password (`password`)**  
   - The VNC server is configured with the password `password`. Nessus was able to log in successfully.  
   - This gives attackers **full remote desktop control** over the system, allowing data theft, malware installation, and further compromise.

5. **SSL Version 2 and 3 Protocol Support**  
   - The system accepts insecure SSLv2 and SSLv3 connections.  
   - These protocols are vulnerable to downgrade attacks (e.g., POODLE), enabling attackers to **intercept and decrypt sensitive communications**.

---

### Top 5 - Remediations (In priority order - most important first)

1. **Remove UnrealIRCd Backdoor**  
   - Immediately uninstall the compromised version of UnrealIRCd.  
   - Replace it with a clean version downloaded from a trusted source or remove the service entirely if not needed.  
   - Rebuild and harden the host if compromise is confirmed.

2. **Eliminate the Bind Shell Backdoor**  
   - Isolate the host and investigate how the backdoor was introduced.  
   - Stop the listening service, kill associated processes, and remove malicious binaries.  
   - If integrity cannot be trusted, reimage the system from a known-good baseline.

3. **Upgrade the Operating System**  
   - Migrate from Ubuntu 8.04 (end-of-life) to a supported release.  
   - Ensure the new version is fully patched and receives security updates.  
   - Apply hardening measures and baseline configurations after upgrade.

4. **Secure VNC Access**  
   - Replace the weak password with a strong, randomly generated one (`vncpasswd`).  
   - Restrict VNC access to trusted IPs or require tunneling over SSH/VPN.  
   - Where possible, disable VNC in favor of more secure remote administration tools.

5. **Disable SSLv2/SSLv3 and Enforce TLS 1.2+**  
   - Reconfigure services to reject SSLv2/SSLv3 connections.  
   - Enable only TLS 1.2 or TLS 1.3 with secure cipher suites.  
   - Test with tools such as `openssl s_client` to confirm the changes.

## 🔧 Technologies & Tools

<p align="left">
  <img src="https://img.shields.io/badge/Kali_Linux-000000?style=for-the-badge&logo=kali-linux&logoColor=white" />  
  <img src="https://img.shields.io/badge/Nessus-CE5240?style=for-the-badge&logo=tenable&logoColor=white" />  
  <img src="https://img.shields.io/badge/Metasploitable2-7F1717?style=for-the-badge&logo=metasploit&logoColor=white" />  
  <img src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black" />  
</p>

