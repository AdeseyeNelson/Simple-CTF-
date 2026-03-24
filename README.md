# Simple-CTF-

*A full end‑to‑end penetration testing engagement conducted by Adeseye Nelson Olaiyapo*
# Simple CTF Penetration Testing – TryHackMe (EasyCTF)

## 📌 Project Overview
This repository documents a complete penetration testing engagement performed on the **TryHackMe EasyCTF machine**. The assessment simulates a real‑world attack scenario, evaluating the security posture of a vulnerable virtual machine by identifying weaknesses, exploiting them, and escalating privileges to achieve full system compromise.
The project follows a structured penetration testing methodology and includes detailed findings, exploitation steps, and remediation recommendations.



## 🎯 Objective
The primary objective of this engagement is to:

- Identify vulnerabilities in the target system  
- Assess exploitability and real‑world impact  
- Demonstrate unauthorized access paths  
- Escalate privileges to root  
- Capture user and root flags  

This aligns with industry‑standard penetration testing practices.



## 📚 Scope
The assessment covers:

- Network exposure  
- Vulnerability identification  
- Exploit feasibility  
- Privilege escalation paths  
- Sensitive information exposure  


## 🛠 Methodology
The engagement follows a structured approach:

1. **Network Scanning**  
2. **Vulnerability Analysis**  
3. **Exploitation**  
4. **Privilege Escalation**  
5. **Flag Discovery**  
6. **Reporting**

---

## 🔍 Key Findings

### **1. Network Scanning**
Tools used:
- Rustscan  
- Nmap  

Open ports discovered:
| Port | Service | Version |
|------|----------|----------|
| 21   | FTP      | vsftpd 3.0.3 |
| 80   | HTTP     | Apache 2.4.18 (outdated) |
| 2222 | SSH      | OpenSSH 7.2p2 |

---

### **2. Vulnerability Analysis**
- Directory enumeration revealed `/simple/`
- CMS Made Simple **v2.2.8** detected  
- Version is outdated and vulnerable to **SQL Injection (CVE‑2019‑9053)**  
- Exploit scripts used to extract:
  - Username  
  - Salt  
  - Email  
  - Hashed password  

*“Manual version enumeration confirmed that the web server is running an outdated version associated with known security issues.”*

---

### **3. Exploitation**
#### FTP
- Anonymous login allowed  
- Sensitive file `Formitch.txt` exposed weak password reuse  
  - *“Dammit man... you’re the worst dev I’ve seen…”*

#### SSH
- SQLi exploit + Hydra brute‑force revealed:
  - **Username:** mitch  
  - **Password:** secret  

SSH access achieved on port 2222.


### **4. Privilege Escalation**
- `sudo -l` revealed passwordless sudo access via **vim**
- Using GTFOBins:
  
  sudo vim
  :!sh
  
- Root shell obtained  
- Root flag captured successfully  


## 🏁 Flags Captured
- **User Flag:** `G00d j0b, keep up!`  
- **Root Flag:** `W3ll d0n3. You made it!`  


## 🛡 Recommendations
To improve security posture:

- Patch outdated software  
- Enforce strong authentication  
- Disable unnecessary services  
- Harden system configurations  
- Implement continuous monitoring  
- Conduct periodic penetration testing  


## 👨‍💻  Author
**Adeseye Nelson Olaiyapo**  
Penetration Testing Lead  
Xaltius Academy  


## 🔗 Reference
TryHackMe Room: https://tryhackme.com/room/easyctf

PROJECT STRUCTURE

Simple-CTF-Penetration-Testing/
│
├── README.md
├── /screenshots
│     ├── rustscan.png
│     ├── nmap.png
│     ├── cms-version.png
│     ├── exploit-output.png
│     ├── ftp-access.png
│     ├── ssh-access.png
│     ├── user-flag.png
│     └── root-flag.png
│
├── /exploits
│     ├── exploit.py
│     └── 46635.py
│
├── /notes
│     ├── enumeration.txt
│     ├── exploitation.txt
│     └── privilege-escalation.txt
│
└── report/
      └── Simple-CTF-Pentest-Report.pdf   (optional)
