# TKH Innovation Fellowship — Phase 1 Cybersecurity
### `tkh-ifcs-p1-student` · Class of 2026

---
```
 _____ _  ___   _  _   ___ ___ _    _    _____      __  ___  ___ ___  ___  
|_   _| |/ / | | || | | __| __| |  | |  / _ \ \    / / | _ \| __| _ \/ _ \ 
  | | | ' /| |_| __ | | _|| _|| |__| |_| (_) \ \/\/ /  |   /| _||  _/ (_) |
  |_| |_|\_\ \___/_||_| |___|___|____|____\___/ \_/\_/   |_|_\|___|_|  \___/ 

  Cybersecurity · Phase 1 · Spring 2026
```
> *"The more I learn, the more I realize how much I don't know."* — Richard Feynman

---

## 👋🏽 Welcome

This is my student artifact repository for Phase 1 of the TKH Innovation Fellowship Cybersecurity program. Every week I push the work I build in class — scripts, lab outputs, notes, and documentation — so there is a living record of how far I have come.

If you are a student in this cohort: your repo can look like this too. Actually, make it better. That is the point.

**Student:** Jane G. Pierre

**Role:** Teaching Assistant · TKH Innovation Fellowship 2026

**Program:** [The Knowledge House](https://theknowledgehouse.org) · Cybersecurity

**Phase:** 1 of 2 · Spring–Summer 2026

**Cohort:** Class of 2026

---

## 📁 Repository Structure

```
tkh-ifcs-p1-student/
├── week-01/
│   ├── discovery.txt
│   ├── harden.sh
│   ├── threat_ips.txt
│   └── final_threat_report.txt
├── week-02/
│   ├── network_audit.txt
│   ├── subnet_blueprint.txt
│   ├── protocol_audit.txt
│   └── tlab_report.txt
├── week-03/
│   ├── port_check.py
│   ├── brute_detector.py
│   ├── brute_report.txt
│   ├── system_auditor.py
│   ├── incident_response.py
│   ├── security_alert.json
│   └── handshake.txt
├── week-04/
│   ├── sandbox_report.txt
│   ├── deploy_web.sh
│   ├── docker-compose.yml
│   ├── docker-compose-tlab4.yml
│   └── hyperstack_audit.json
└── README.md
```

---

## 🗓️ Week Tracker

| Week | Dates | Theme | Status |
|---|---|---|---|
| 01 | Mar 9-11 | Terminal · Permissions · Stream Editing · Git | ✅ Complete |
| 02 | Mar 16-18 | Networking · Subnetting · Protocol Interrogation | ✅ Complete |
| 03 | Mar 23-25 | Python Scripting · Port Scanner · Brute Force Detector · Process Auditor | ✅ Complete |
| 04 | Mar 30-Apr 1 | Virtualization · Docker · Container Security · Network Segmentation | ✅ Complete |
| 05 | Apr 6-8 | Identity · Active Directory · Windows Server Core | ✅ Complete |
| 06 | Apr 13-15 | Forge Capstone · Hybrid Architecture · Secure Deployment | ⏳ Upcoming |

---

## 🚀 Getting Started

**Step 1 — Clone the repo**

```
git clone git@github.com:janepierresgithub/tkh-ifcs-p1-student.git
cd tkh-ifcs-p1-student
```

**Step 2 — Run the lab bootstrap**

```
# Night 1 (S01)
curl -sL https://gist.githubusercontent.com/grobbins-cell/126d5c64f5f071ae950cc18c09b391fa/raw | bash

# Night 2 (S02)
curl -sL https://gist.githubusercontent.com/grobbins-cell/8dea0f5a0c65b29efe0b91dd3afa6842/raw/698804520709884999cba0c54411303bff3ae6aa/setup_lab_02.sh | bash

# Night 3 (S03)
curl -sL https://gist.githubusercontent.com/grobbins-cell/610867dae208e88154070b0ca78084df/raw/661e54024519f558ba4ed7e5d78655a429bef748/setup_lab_03.sh | bash
```

**Step 3 — Push your work**

```
git add .
git commit -m "edited: filename"
git push origin master
```

---

## 📚 Week 01 — Linux Foundations and Version Control

### 🌱 S01 · Terminal Genesis
Your first night in a headless Linux environment. No GUI. Just you and the terminal.

Key skills: `ls` `cd` `pwd` `mkdir` `cat` `find` · FHS navigation · SSH · Git setup

### 🔐 S02 · The Keymaster
Who can read it? Who can write it? Who can run it? Linux answers these questions with nine bits and three letters: `rwx`.

Key skills: `chmod` `chown` `ls -la` · SUID auditing · Principle of Least Privilege

### 🔍 S03 · Stream Editing and Automation
10,000 lines of web server logs. Three attackers buried in the noise. One pipeline to find them all.

Key skills: `grep` `awk` `sed` `sort` `uniq` · stdout redirection · pipeline chaining

### 🎯 TLAB-01 · Operation Clean Sweep
Full threat hunt mission. Extracted malicious IPs from web logs, correlated with auth logs, and filed a final threat report.

---

## 📡 Week 02 — Networking · Subnetting · Protocol Interrogation

### 🌐 S04 · Operation Broken Link
Your machine is blind. Restore the wire. Bring the interface up and manually add the default gateway route.

Key skills: `ip link` `ip addr` `ip route` · Layer 1-3 recovery

### 🧮 S05 · Operation Grid Lock
You can see the network but cannot talk to the gateway. Your subnet mask has isolated you mathematically.

Key skills: `ipcalc` · binary conversion · CIDR · subnet masks

### 🔌 S06 · Operation Hidden Door
DNS poisoning. A cloaked local service. Find it, fix it, document it.

Key skills: `ss -tuln` `curl -I` `dig` `cat /etc/hosts` · TCP vs UDP

### 🎯 TLAB-02 · Operation Blackout
Full remediation mission across Layers 3, 4, and 7. Restored subnet, cleansed DNS poisoning, captured TCP 3-way handshake as forensic proof.

---

## 🐍 Week 03 — Python Scripting for Security Automation

### 🔭 S07 · The Automation Forge
No Nmap. Just Python and raw sockets. Write a script that checks whether Port 22 is open across a list of target IPs and does it automatically.

Key skills: `python3` · `socket` · `for` loops · `connect_ex`

### 🚨 S08 · The Paper Trail
Parse a simulated auth log. Extract every failed login attempt. Write the findings to a clean report automatically.

Key skills: `python3` · file I/O · `with open()` · `try/except` · string matching

### 🔎 S09 · The Automation Pivot
Give Python the keys to the OS. Run system commands from inside a script, capture the output, and export a structured JSON security alert.

Key skills: `python3` · `subprocess` · `json` · process interrogation

### 🎯 TLAB-03 · Operation Automated Hunt
Automated incident response pipeline built entirely in Python. Used subprocess to run grep programmatically, parsed raw output to extract attacker IPs, and exported a structured JSON alert ready for SIEM ingestion.

---

## 🐳 Week 04 — Virtualization · Docker · Container Security

### 🏖️ S10 · Sandbox Detonation
Configured a Host-Only network adapter to air-gap the VM from the internet before detonating a simulated malware payload. Documented isolation verification and explained why Bridged mode is never acceptable for malware analysis.

Key skills: VirtualBox network modes · Host-Only · sandbox isolation

### 🚢 S11 · The Disposable Web Server
Deployed, modified, and destroyed an nginx container. Demonstrated the full container lifecycle and automated the deployment sequence in a reusable bash script.

Key skills: `docker run` `docker exec` `docker stop` `docker rm` · container lifecycle

### 🔒 S12 · The Air-Gapped Stack
Deployed a WordPress and MySQL multi-container stack using Docker Compose with explicit network segmentation. MySQL isolated to backend only with `internal: true` — provably air-gapped from the internet.

Key skills: `docker-compose` · network segmentation · `internal: true` · Defense in Depth

### 🏰 TLAB-04 · Operation Fortified Node
Capstone of Week 4. Evicted a rogue container, built a three-tier WordPress and MariaDB stack from scratch with public and private network segmentation, verified port isolation with nmap, and produced a machine-readable JSON audit report.

Key skills: Docker Compose · nmap · JSON reporting · Security Architecture Verification

---

## 💡 Core Concepts

### The CIA Triad

| Property | Question It Answers | Example |
|---|---|---|
| Confidentiality | Who can see it? | `chmod 600 secrets.txt` |
| Integrity | Has it been tampered with? | Git commit hashes |
| Availability | Can authorized users access it? | Uptime, backups, failover |

### The Holy Trinity of Text Processing

```
grep  →  finds lines that match a pattern       (The Scalpel)
sed   →  finds and replaces text on the fly     (The Laser)
awk   →  extracts specific columns from data    (The Formatter)
```

### Git as an Accountability Tool
Every `git commit` creates a cryptographic hash — a tamper-evident, timestamped, attributed record of exactly what changed and when. That is Accounting — the third pillar of the AAA framework.

### Defense in Depth
No single security control is sufficient. The container network architecture in Week 04 layers multiple controls so that a breach of one layer does not mean a breach of all.

### SOAR — Security Orchestration, Automation and Response
The Python scripts in Week 03 demonstrate the foundational logic of SOAR platforms — ingest a log source, apply a detection rule, extract indicators of compromise, and export a structured alert.

---

## 🛠️ TA Notes

> Hi, I am Jane — your TA for Phase 1 of the TKH Innovation Fellowship Cybersecurity program. This repo is my own student artifact repo, built to show you what yours can look like. Every script, every note, every commit message here was written with intention.
>
> You do not have to be perfect. You have to be consistent. Push something every week. Document what you learned. Future you — and future employers — will thank you.
>
> My Slack is always open. Same thing.

---

## 📖 References

Chapple, M., Stewart, J. M., and Gibson, D. (2021). ISC2 CISSP certified information systems security professional official study guide (9th ed.). Sybex.

NIST. (2022). NICE Cybersecurity Workforce Framework (NIST SP 800-181r1). National Institute of Standards and Technology.

---

**Built intentionally · Current Status: Updated Often · TKH IF 2026**
