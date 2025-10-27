# Elastic Security Detection Lab

A complete hands-on cybersecurity training lab featuring Elastic Security SIEM with automated threat detection, monitoring, and incident response capabilities. This lab is designed for CyberRangeCZ/KYPO platform and adapted from [Ludus](https://ludus.cloud) badsectorlabs roles.

> 🎓 **Perfect for**: SOC Analysts, Security Engineers, Detection Engineers, Incident Responders, and Cybersecurity Students

---

## 📋 Table of Contents

- [What is This Lab?](#what-is-this-lab)
- [What You'll Learn](#what-youll-learn)
- [Lab Architecture](#lab-architecture)
- [Prerequisites](#prerequisites)
- [Quick Start Guide](#quick-start-guide)
- [Detailed Setup Instructions](#detailed-setup-instructions)
- [Using the Lab](#using-the-lab)
- [Training Exercises](#training-exercises)
- [Troubleshooting](#troubleshooting)
- [Advanced Configuration](#advanced-configuration)
- [Contributing](#contributing)
- [Credits](#credits)

---

## 🎯 What is This Lab?

This lab creates a complete cybersecurity environment where you can:

- **Monitor security events** from Windows and Linux systems in real-time
- **Detect threats** using pre-built and custom detection rules
- **Investigate alerts** like a real SOC analyst
- **Practice attacks** in a safe, isolated environment
- **Learn SIEM operations** with industry-standard tools

### Components

| Component | Description | IP Address |
|-----------|-------------|------------|
| **Elastic Server** | Central logging and analysis platform (Elasticsearch + Kibana + Fleet) | 10.20.30.10 |
| **Windows Endpoint** | Windows 10 machine with monitoring agents (Elastic Agent + Sysmon) | 10.20.30.30 |
| **Debian Endpoint** | Linux machine with Elastic Agent for monitoring | 10.20.30.20 |
| **Kali Attacker** | Attack simulation machine with Metasploit and penetration testing tools | 10.20.30.100 |

---

## 📚 What You'll Learn

By completing this lab, you will:

1. ✅ Deploy and configure Elastic Security SIEM
2. ✅ Install and manage Elastic Agents on Windows and Linux
3. ✅ Query security logs using KQL (Kibana Query Language)
4. ✅ Create custom detection rules for threats
5. ✅ Investigate security alerts and incidents
6. ✅ Detect malicious PowerShell, Meterpreter, and other attack techniques
7. ✅ Understand MITRE ATT&CK framework integration
8. ✅ Practice real-world SOC analyst workflows

---

## 🏗️ Lab Architecture

