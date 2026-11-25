# NETWORKWALKS-DANIEL-B084-WK3-PM1-PM2-PASSWORD-CRACKING

**Cybersecurity & Ethical Hacking Internship — Networkwalks Academy**
**Student:** Olanipekun Daniel Dayo (Wick)
**Week 3 — Password Cracking**

---

## ⚠️ Disclaimer

This project was carried out strictly as part of the Networkwalks Cybersecurity & Ethical Hacking internship, using files and tools officially provided by Networkwalks Academy for educational purposes only. All password cracking in this repo was performed on a sample PDF file supplied by Networkwalks for this lab — not on any real, third-party, or unauthorized system. No real-world systems, accounts, or data were accessed. This work should not be replicated outside an authorized lab environment.

## Authorization

This task falls within the authorized scope defined in the Networkwalks internship Letter of Authorization: cracking a sample password-protected PDF file (`My Locked PDF1.pdf`) explicitly provided by Networkwalks Academy for this lab exercise, performed entirely within my own local lab environment (Kali Linux VM).

---

## Overview

This week covered two modules on password cracking against a protected PDF file:

- **W3-PM1:** Password Cracking with John the Ripper (JTR)
- **W3-PM2:** Password Cracking with Networkwalks' own Hash Calculator + Password Cracker tools

Both modules follow the same core idea: extract a crackable hash from an encrypted PDF, then run a dictionary attack against that hash to recover the plaintext password.

---

## W3-PM1 — Password Cracking with John the Ripper (JTR)

**Tool used:** John the Ripper (`pdf2john` + `john`), run on Kali Linux
**Target file:** `My Locked PDF1.pdf`

### Steps

1. Extracted the crackable hash from the PDF using `pdf2john`:
   ```
   pdf2john "My Locked PDF1.pdf" > hash1.txt
   cat hash1.txt
   ```
2. Ran John the Ripper against the extracted hash using the default wordlist:
   ```
   john hash1.txt
   ```
3. Confirmed the cracked password:
   ```
   john --show hash1.txt
   ```
4. **Result:** Password cracked → `good-luck`
5. Opened the PDF using the recovered password and confirmed successful decryption.

**Flag captured:** `nw{cybersecurity_flag_captured_2608}`

### Screenshots

![Hash extracted with pdf2john](screenshots/01-pm1-hash-extraction.png)
*Extracting the hash from the locked PDF using pdf2john*

![Password cracked with John the Ripper](screenshots/02-pm1-jtr-cracked.png)
*John the Ripper successfully cracking the password: good-luck*

![Unlocked PDF](screenshots/03-pm1-pdf-unlocked.png)
*PDF unlocked using the cracked password, showing the captured flag*

---

## W3-PM2 — Password Cracking with Networkwalks Tools

**Tools used:** Networkwalks Hash Calculator + Networkwalks Password Cracker (browser-based)
**Target file:** `My Locked PDF1 (for NW Tools Lab WK3-PM2).pdf`

### Steps

1. Uploaded the locked PDF to the Networkwalks Hash Calculator (`networkwalks.com/hash-calculator`) to extract the crackable `$pdf$...` hash.
2. Copied the generated hash.
3. Pasted the hash into the Networkwalks Password Cracker (`networkwalks.com/password-cracker`) and ran the dictionary attack.
4. **Result:** Password cracked → `password1`
5. Opened the PDF using the recovered password and confirmed successful decryption.

**Flag captured:** `nw{networkwalks_flag1_jtr_270521_1}`

### Screenshots

![Hash extracted with Networkwalks Hash Calculator](screenshots/04-pm2-hash-calculator.png)
*Extracting the hash using the Networkwalks Hash Calculator tool*

![Password cracked with Networkwalks Password Cracker](screenshots/05-pm2-password-cracker.png)
*Networkwalks Password Cracker successfully cracking the password: password1*

![Unlocked PDF](screenshots/06-pm2-pdf-unlocked.png)
*PDF unlocked using the cracked password, showing the captured flag*

---

## Troubleshooting

While attempting W3-PM1 on Windows, both the John the Ripper and Johnny GUI executables were repeatedly flagged by Windows Defender as containing a virus/unwanted software, and Johnny itself began launching multiple duplicate windows uncontrollably, requiring a PC restart. After confirming this is a known false-positive behavior for password-cracking tools (and since the module explicitly permits using Kali Linux, where JTR comes pre-installed), I switched the entire task over to my Kali Linux VM instead of continuing to troubleshoot the Windows install. This avoided any further risk to the host machine and completed the task faster using the built-in `pdf2john` and `john` commands.

---

## Key Takeaway

This lab demonstrated how quickly weak, common passwords (`good-luck`, `password1`) can be recovered using basic dictionary attacks — both with a dedicated tool like John the Ripper and with simple browser-based tools. It reinforces why strong, unique passwords are essential for protecting sensitive files and accounts.

---

*© Networkwalks Academy — www.networkwalks.com*
