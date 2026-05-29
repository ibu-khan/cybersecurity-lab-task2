<div align="center">

# 🛡️ Cybersecurity Internship — Task 2
## Build Your Personal Cybersecurity Lab

[![Internship](https://img.shields.io/badge/Internship-Maincrafts%20Technology-0A66C2?style=for-the-badge&logo=briefcase&logoColor=white)](https://www.maincrafts.com)
[![Platform](https://img.shields.io/badge/Platform-Kali%20Linux%202025.4-557C94?style=for-the-badge&logo=kalilinux&logoColor=white)](https://www.kali.org)
[![Tool](https://img.shields.io/badge/Hypervisor-VirtualBox-183A61?style=for-the-badge&logo=virtualbox&logoColor=white)](https://www.virtualbox.org)
[![Target](https://img.shields.io/badge/Target-DVWA-E44D26?style=for-the-badge&logo=html5&logoColor=white)](https://github.com/digininja/DVWA)
[![Status](https://img.shields.io/badge/Status-Completed%20✔-2ECC71?style=for-the-badge)](#)

<br/>

> *A fully isolated, professional-grade cybersecurity practice environment built from scratch — covering network segmentation, traffic interception, packet analysis, and vulnerable web application deployment.*

</div>

---

## 📌 Overview

This repository documents **Task 2** of my Cybersecurity Internship at **Maincrafts Technology**. The objective was to design and deploy a safe, isolated cybersecurity lab environment on a personal machine — serving as the foundation for all future tasks including vulnerability assessment, web application penetration testing, and incident response.

The lab replicates a real-world attacker/target architecture inside a fully controlled virtual environment.

---

## 🏗️ Lab Architecture

```
┌─────────────────────────────────────────────────┐
│              Host System (Windows)               │
│                                                  │
│   ┌─────────────────────────────────────────┐   │
│   │         Oracle VirtualBox               │   │
│   │                                         │   │
│   │   ┌──────────────────────────────┐      │   │
│   │   │  Kali Linux 2025.4 (Attacker)│      │   │
│   │   │  RAM: 4GB | CPUs: 2          │      │   │
│   │   │  Adapter 1: NAT              │      │   │
│   │   │  Adapter 2: Host-Only        │      │   │
│   │   └──────────────┬───────────────┘      │   │
│   │                  │                      │   │
│   │   ┌──────────────▼───────────────┐      │   │
│   │   │  DVWA on Apache (Target)     │      │   │
│   │   │  http://127.0.0.1:80         │      │   │
│   │   └──────────────────────────────┘      │   │
│   │                                         │   │
│   │   Networks:                             │   │
│   │   • NAT (eth0)       → Internet         │   │
│   │   • Host-Only (eth1) → 192.168.56.0/24  │   │
│   └─────────────────────────────────────────┘   │
└─────────────────────────────────────────────────┘
```

---

## ⚙️ Environment Specifications

| Component | Details |
|-----------|---------|
| **Host OS** | Windows (64-bit) |
| **Hypervisor** | Oracle VirtualBox |
| **Attacker VM** | Kali Linux 2025.4 (Debian 64-bit) |
| **RAM** | 4096 MB |
| **vCPUs** | 2 |
| **Storage** | 40 GB VDI |
| **Network Adapter 1** | NAT — Internet access |
| **Network Adapter 2** | Host-Only — 192.168.56.0/24 |
| **Kali IP (Host-Only)** | 192.168.56.101 |
| **Target Application** | DVWA on Apache/PHP (http://127.0.0.1) |
| **Docker Version** | 28.5.2+dfsg4 |

---

## 🧰 Tools Used & Validated

| Tool | Purpose | Result |
|------|---------|--------|
| **Nmap 7.95** | Host discovery & service enumeration | ✅ 3 hosts found on 192.168.56.0/24 |
| **Burp Suite CE v2025.10.6** | HTTP proxy interception & traffic analysis | ✅ HTTP requests intercepted |
| **Wireshark** | Packet capture & frame-level analysis | ✅ Full HTTP request/response captured |
| **Docker 28.5.2** | Container-based service deployment | ✅ Installed & operational |
| **Apache/PHP** | DVWA web server stack | ✅ Running on port 80 |

---

## 📋 Steps Completed

- [x] **Step 1** — Installed Oracle VirtualBox and configured Host-Only network adapter
- [x] **Step 2** — Imported and deployed Kali Linux 2025.4 VM with dual network adapters
- [x] **Step 3** — Configured NAT + Host-Only network segmentation
- [x] **Step 4** — Deployed DVWA on Apache/PHP stack as the vulnerable target
- [x] **Step 5** — Validated connectivity using Nmap (host discovery + service scan)
- [x] **Step 6** — Intercepted HTTP traffic using Burp Suite proxy
- [x] **Step 7** — Captured and analysed packets using Wireshark on loopback interface
- [x] **Step 8** — Confirmed DVWA is fully accessible with all 14 vulnerability modules

---

## 📂 Repository Structure

```
cybersecurity-lab-task2/
│
├── 📄 README.md                          ← You are here
├── 📋 docs/
│   └── CyberSecurity_Lab_Build_Report_Task2.pdf   ← Full lab report
│
└── 📁 .github/
    └── SECURITY.md                       ← Security & ethical use policy
```

---

## 📄 Report

The full lab build report is available in the [`docs/`](./docs/) folder:

**[📥 Download Lab Report PDF](./docs/CyberSecurity_Lab_Build_Report_Task2.pdf)**

The report includes:
- Complete VM configuration details
- Network interface documentation
- Nmap scan results with analysis
- Burp Suite interception screenshots
- Wireshark packet capture analysis (frame-level)
- DVWA deployment and module verification
- 19 annotated screenshots

---

## 🔍 Key Learnings

**Network Segmentation** — Understanding the difference between NAT (internet access) and Host-Only (isolated lab traffic) is fundamental. Vulnerable services must never be exposed to external networks.

**Traffic Interception** — Burp Suite acts as a Man-in-the-Middle proxy, revealing exactly how browsers communicate with web applications — headers, cookies, parameters, and all.

**Packet Analysis** — Wireshark at the frame level shows that HTTP is plaintext by nature. Even a simple page load reveals User-Agent, server version, and caching policies in the clear.

**Lab Isolation** — Building a dedicated lab environment prevents accidental damage to production systems and provides a safe space to practice offensive techniques legally and ethically.

---

## 🔐 Ethical Use Disclaimer

> All techniques and tools documented in this repository were used **exclusively within a controlled, isolated lab environment** on systems I own and have full authorisation to test. No external systems, networks, or third-party services were targeted. This work is conducted solely for **educational and professional development purposes** as part of a supervised internship programme.
>
> Unauthorised use of these techniques against systems you do not own is **illegal**. Always obtain proper written authorisation before conducting any security testing.

---

## 🗺️ What's Next

Following tasks in this internship will build upon this lab environment:

- [ ] Task 3 — Vulnerability Assessment & Scanning
- [ ] Task 4 — Web Application Penetration Testing (DVWA)
- [ ] Task 5 — Exploitation & Post-Exploitation
- [ ] Task 6 — Incident Response & Log Analysis

---

## 🏢 Internship Details

| | |
|--|--|
| **Organisation** | Maincrafts Technology |
| **Website** | [www.maincrafts.com](https://www.maincrafts.com) |
| **Contact** | hr@maincrafts.com |
| **Programme** | Cybersecurity & Ethical Hacking Internship |
| **Task** | Task-2 — Build Your Personal Cybersecurity Lab |
| **Date Completed** | May 21, 2026 |

---

<div align="center">

*If you found this useful, consider giving it a ⭐ — it helps others discover this resource.*

**[⬆ Back to Top](#)**

</div>
