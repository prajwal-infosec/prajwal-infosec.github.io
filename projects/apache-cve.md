# Mini Project – Apache CVE-2021-41773

## 📌 Overview
This project involved **reproducing and analyzing CVE-2021-41773**, a critical vulnerability in **Apache HTTP Server 2.4.49** that allows **path traversal** and can lead to **remote code execution (RCE)** when CGI is misconfigured.

The goal was not just exploitation, but to **understand why the vulnerability works, its limitations, and real-world behavior** in a controlled environment.

📄 *Based on my officially submitted academic mini-project report* :contentReference[oaicite:0]{index=0}

---

## 🎯 Objectives
- Deploy a vulnerable Apache 2.4.49 environment
- Validate path traversal using encoded payloads
- Achieve remote command execution via CGI
- Analyze privilege boundaries and exploitation limits
- Study Apache and CGI behavior in containerized setups

---

## 🧠 Technical Methodology

### 🔍 Environment Setup
- Vulnerable Apache HTTP Server 2.4.49 deployed using Docker
- Attacker system: Kali Linux
- Manual CGI configuration to replicate realistic misconfigurations

### 🔎 Vulnerability Validation
- Used crafted URL-encoded traversal sequences (`.%2e`)
- Successfully accessed restricted files such as `/etc/passwd`
- Confirmed improper path normalization behavior

### ⚔️ Remote Code Execution
- Enabled CGI execution
- Invoked `/bin/sh` through path traversal
- Executed arbitrary shell commands remotely

> RCE was achieved as the **Apache daemon user**, which accurately reflects real-world Apache privilege separation.

---

## 🛡️ Observations & Limitations
- RCE does **not escalate to root** due to Apache’s security model
- CGI configuration plays a critical role in exploitability
- Containerized environments can introduce behavior differences compared to bare-metal servers

---

## 📘 Key Learnings
- How URL normalization flaws translate into real attacks
- Importance of CGI configuration in Apache security
- Difference between “RCE achieved” and **meaningful impact**
- Why understanding **execution context** matters in penetration testing

---

## 🔒 Ethical Considerations
All testing was conducted in a **local, isolated lab environment** strictly for educational and research purposes.
