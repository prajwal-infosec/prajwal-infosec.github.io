# Apache CVE-2021-41773 – Path Traversal & RCE

## 📌 Overview

This project reproduces and analyzes **CVE-2021-41773**, a critical vulnerability in **Apache HTTP Server 2.4.49** that allows **path traversal** and can lead to **remote code execution (RCE)** when CGI is misconfigured.

The objective was to understand **why the vulnerability works**, its **real-world limitations**, and the role of **server configuration** in exploitability.

---

## 🎯 Objectives

- Deploy a vulnerable Apache 2.4.49 environment
- Validate path traversal using encoded payloads
- Achieve remote command execution through CGI
- Analyze privilege boundaries and execution context
- Study Apache behavior in containerized environments

---

## 🧠 Methodology

### Environment
- Apache HTTP Server 2.4.49 (Docker)
- Kali Linux attacker system
- Manual CGI configuration

### Exploitation Flow
1. Identify vulnerable Apache version
2. Validate directory traversal via encoded paths
3. Enable and abuse CGI execution
4. Invoke `/bin/sh` through traversal
5. Execute arbitrary commands remotely

---

## 🛡️ Observations

- RCE executes as the **Apache daemon user**, not root
- Privilege separation works as intended
- CGI configuration is the key exploitation enabler
- Containers influence exploit behavior but do not invalidate impact

---

## 📘 Key Takeaways

- CVEs must be evaluated in **context**, not isolation
- Execution context matters more than “RCE achieved”
- Misconfigurations often decide exploitability
- Understanding internals improves reporting quality

---

## 🔒 Ethics

All testing was performed in **isolated, controlled environments** strictly for educational and research purposes.
