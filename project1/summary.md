# Week 1 CTF Project – Challenge Summary

This markdown file documents the steps, tools, and reasoning I used to solve the required CTF challenges for Week 1. A minimum of 8 points is required for full credit.

---

## 🧠 Trivia Challenges

### Challenge 1: Honesty is Best Policy (1 point)
**Question:** Which part of the CIA Triad ensures information is not altered?
**Answer:** Integrity  
**Steps Taken:**
- Googled "CIA Triad components"
- Read definitions from cybersecurity sources like NIST, remembered from cybersecurity cert study.
- Confirmed "Integrity" ensures no unauthorized or accidental modification

---

### Challenge 2: Lots of Jobs! (1 point)
**Question:** Which state has the most cybersecurity jobs according to CyberSeek?
**Answer:** California  
**Steps Taken:**
- Visited [CyberSeek.org](https://www.cyberseek.org)
- Opened the interactive map
- Hovered over each state and recorded the job numbers
- California had the highest number listed

---

### Challenge 3: Hostage (1 point)
**Question:** Which malware encrypts files and demands payment?
**Answer:** Ransomware  
**Steps Taken:**
- Searched: “malware that locks files until you pay”
- Read articles from Norton and IBM Security
- Ransomware matches the description (e.g., WannaCry)

---

## 🔍 Reconnaissance Challenges

### Challenge 4: 11,185,272 (1 point)
**Answer:** [11,185,273]  
**Steps Taken:**
Observed the challenge title hinting at a number pattern
Incremented the number by one
Final result: 11185273

---

### Challenge 5: Read Me (1 point)
**Answer:** [flag{h3r3syerfl@g}]  
**Steps Taken:**
-Opened the README.txt file in a text editor
-Noticed “PDF” at the top of the content
-Renamed file from .txt to .pdf using Git Bash:
mv README.txt README.pdf
-Opened the file as a PDF and found the flag

---

### Challenge 6: Three Even, Two Odd (1 point)
**Answer:** [12456]  
**Steps Taken:**
-Opened the README.txt file in a text editor
-Noticed “PDF” at the top of the content
-Renamed file from .txt to .pdf using Git Bash:
mv README.txt README.pdf
-Opened the file as a PDF and found the flag

---

## 🔐 Cryptography Challenges

### Challenge 7: Shifty (2 points)
**Encrypted Message:** `Qeb mxpptloa fp MibxpbZexkdbJb`  
**Answer:** The encryption used is ROT13
**Decrypted Text:** `The password is PleaseChangeMe`  
**Steps Taken:**
- Opened CyberChef and used the ROT13 tool
Noticed the shift wasn't ROT13, so tried different amounts
Found the correct output at a ROT shift of 29
Output made logical sense and revealed a full sentence
![image](https://github.com/user-attachments/assets/8edde433-2f76-4f84-acaf-ba9220e84570)

---

### Challenge 8: Encoded Message (2 points)
**Base64 Input:** `aXRnZXRzaGFyZGVyZnJvbWhlcmU=`  
**Decoded Answer:** `itgetsharderfromhere`  
**Steps Taken:**
- Used CyberChef → From Base64
- Removed padding (`=`) after decoding
- Output was a readable phrase
![image](https://github.com/user-attachments/assets/a02e416c-52e9-4fa6-a688-b55d3c164c68)

---

### Challenge 9: Kasiski Who? (2 points)
**Encrypted Message:** `JYWMEIDVRTTYDOZPEDSUGQ`  
**Key:** `POELR`  
**Answer:** [HAVINGFUNCRACKINGCODES]  
**Steps Taken:**
-The prompt mentioned the key was "encoded twice," which hinted at using multiple ciphers
I assumed ROT13 might be one of them and applied it to the given key: POELR
ROT13 output was CBYRE, which didn’t make sense at first, but sounded like a scrambled version of cyber
Guessed the final key was cyber
Used CyberChef → Vigenère Decode with cyber as the key
![image](https://github.com/user-attachments/assets/7a593f52-4da7-4fea-9813-41d55ab85d26)

---

### Challenge 10: Kasiski Who? (2 points)
**Encrypted Message:** `AAAAA AAAAB BAAAA AAAAA AAABA AAAAA AAABB AAAAA AAAAB BAAAA AAAAA`    
**Answer:** [ABRACADABRA]  
**Steps Taken:**
Researched the cipher description and found it matched the Bacon Cipher (developed by Francis Bacon).
Pasted the message into CyberChef and used the Bacon Cipher Decode tool.
At first, it didn’t show anything useful, so I changed the translation setting from 0/1 to A/B.
The correct solution ABRACADABRA was revealed.

### Challenge 11: Arch EXIF! (2 points)    
**Answer:** [flag{h1ding_in_plane_s1ght}]  
**Steps Taken:**
Uploaded Arch.jpg to CyberChef
Used the "Extract EXIF" tool under Forensics
Found a suspicious Base64 string in the Make tag
Decoded it with "From Base64" to reveal the hidden flag
![image](https://github.com/user-attachments/assets/eb65f332-5c87-4bc5-9753-f656be8bcb29)
![image](https://github.com/user-attachments/assets/319ce75a-98b4-4f17-9998-46c38f87b7f1)


## 🏁 Summary

- **Total Challenges Completed:** 8+
- **Tools Used:** CyberChef, Google, CyberSeek, image viewers
- **Skills Demonstrated:** Online research, logic reasoning, cryptography, forensic file analysis

---
