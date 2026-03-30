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

---

> *"The more I learn, the more I realize how much I don't know."*
> — Richard Feynman

---

## 👋🏽 Welcome

This is my student artifact repository for **Phase 1** of the TKH Innovation
Fellowship Cybersecurity program. Every week I'll be pushing the work I build
in class — scripts, lab outputs, notes, and documentation — so there's a living
record of how far I've come.

If you're a student in this cohort: your repo can look like this too. Actually,
make it better. That's the point.

**Student:** Jane G. Pierre
**Role:** Teaching Assistant · TKH Innovation Fellowship 2026
**Program:** [The Knowledge House](https://theknowledgehouse.org) · Cybersecurity
**Phase:** 1 of 2 · Spring–Summer 2026
**Cohort:** Class of 2026

---

## 📁 Repository Structure
```
tkh-ifcs-p1-student/
│
├── week-01/
│   ├── discovery.txt              # S01 — filesystem recon output
│   ├── harden.sh                  # S02 — hardening script
│   ├── threat_ips.txt             # S03 — extracted attacker IPs
│   └── final_threat_report.txt    # TLAB-01 — Operation Clean Sweep
│
├── week-02/
│   ├── network_audit.txt          # S04 — Operation Broken Link
│   ├── subnet_blueprint.txt       # S05 — Operation Grid Lock
│   ├── protocol_audit.txt         # S06 — Operation Hidden Door
│   └── tlab_report.txt            # TLAB-02 — Operation Blackout
│
├── week-03/
│   ├── port_check.py              # S07 — Python port scanner
│   ├── brute_detector.py          # S08 — auth log brute force detector
│   ├── brute_report.txt           # S08 — brute force findings
│   ├── system_auditor.py          # S09 — automated process auditor
│   ├── incident_response.py       # S09 — threat response script
│   ├── security_alert.json        # S09 — structured JSON alert
│   └── handshake.txt              # S09 — tcpdump capture
│
└── README.md
```

---

## 🗓️ Week Tracker

| Week | Dates | Theme | Status |
|:---:|:---:|---|:---:|
| 01 | Mar 9–11 | Terminal · Permissions · Stream Editing · Git | ✅ |
| 02 | Mar 16–18 | Networking · Subnetting · Protocol Interrogation | ✅ |
| 03 | Mar 23–25 | Python Scripting · Port Scanner · Brute Force Detector · Process Auditor | ✅ |
| 04 | Mar 30–Apr 1 | Virtualization · Docker · Container Security | ⏳ |

---

## 🚀 Getting Started

**Step 1 — Clone the repo**
```bash
git clone git@github.com:janepierresgithub/tkh-ifcs-p1-student.git
cd tkh-ifcs-p1-student
```

**Step 2 — Run the lab bootstrap**
```bash
# Night 1 (S01)
curl -sL https://gist.githubusercontent.com/grobbins-cell/126d5c64f5f071ae950cc18c09b391fa/raw | bash

# Night 2 (S02)
curl -sL https://gist.githubusercontent.com/grobbins-cell/8dea0f5a0c65b29efe0b91dd3afa6842/raw/698804520709884999cba0c54411303bff3ae6aa/setup_lab_02.sh | bash

# Night 3 (S03)
curl -sL https://gist.githubusercontent.com/grobbins-cell/610867dae208e88154070b0ca78084df/raw/661e54024519f558ba4ed7e5d78655a429bef748/setup_lab_03.sh | bash

# Session 07 (S07)
curl -sL https://gist.githubusercontent.com/grobbins-cell/eea802f31544515afd22877b0c85502b/raw/s07_provisioning.sh | sudo bash
```

**Step 3 — Push your work**
```bash
git add .
git commit -m "edited: port_check.py"
git push origin master
```

---

## 📚 Week 01 — Completed

### 🌱 S01 · Terminal Genesis
Your first night in a headless Linux environment. No GUI. Just you and the terminal.

Key skills: `ls` `cd` `pwd` `mkdir` `cat` `find` `man` · FHS navigation · SSH · Git setup
```bash
ssh jane@janetheta
```

### 🔐 S02 · The Keymaster
Who can read it? Who can write it? Who can run it? Linux answers these questions
with nine bits and three letters: `rwx`.

Key skills: `chmod` `chown` `ls -la` · SUID auditing · Principle of Least Privilege
```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
sudo chmod 640 /etc/shadow
sudo chown root:shadow /etc/shadow
```

### 🔍 S03 · Stream Editing & Automation
10,000 lines of web server logs. Three attackers buried in the noise.
One pipeline to find them all.

Key skills: `grep` `awk` `sed` `sort` `uniq` · stdout redirection · pipeline chaining
```bash
grep "UNION SELECT" ~/access.log \
    | awk '{print $1}' \
    | sort | uniq \
    > ~/threat_ips.txt
```

### 🎯 TLAB-01 · Operation Clean Sweep
Full threat hunt mission. Extracted malicious IPs from web logs, correlated with auth logs, and filed a final threat report.

Key skills: pipeline chaining · log correlation · threat reporting
```bash
# Artifact: final_threat_report.txt
```

---

## 📡 Week 02 — Completed

### 🌐 S04 · Operation Broken Link
Your machine is blind. Restore the wire. Bring the interface up and manually add the default gateway route.

Key skills: `ip link` `ip addr` `ip route` `traceroute` · Layer 1-3 recovery
```bash
sudo ip link set enp0s3 up
sudo ip route add default via 10.0.0.1
# Artifact: network_audit.txt
```

### 🧮 S05 · Operation Grid Lock
You can see the network but can't talk to the gateway. Your subnet mask has isolated you mathematically.

Key skills: `ipcalc` · binary conversion · CIDR · subnet masks
```bash
ipcalc 10.50.50.150/26
sudo ip addr del 10.50.50.150/26 dev enp0s3
sudo ip addr add 10.50.50.150/24 dev enp0s3
# Artifact: subnet_blueprint.txt
```

### 🔌 S06 · Operation Hidden Door
DNS poisoning. A cloaked local service. Find it, fix it, document it.

Key skills: `ss -tuln` `curl -I` `dig` `cat /etc/hosts` · TCP vs UDP
```bash
cat /etc/hosts
sudo nano /etc/hosts
dig google.com
ss -tuln
# Artifact: protocol_audit.txt
```

### 🎯 TLAB-02 · Operation Blackout
Full remediation mission across Layers 3, 4, and 7. Restored subnet, cleansed DNS poisoning, captured TCP 3-way handshake as forensic proof.

Key skills: `ip addr` `ip route` `/etc/hosts` `tcpdump` · OSI Layers 3/4/7
```bash
sudo tcpdump -i enp0s3 host 192.168.10.193 -n -c 10
# Artifact: tlab_report.txt
```

---

## 🐍 Week 03 — Completed

### 🔭 S07 · The Automation Forge
No Nmap. Just Python and raw sockets. Write a script that checks whether
Port 22 is open across a list of target IPs — and does it automatically.

Key skills: `python3` · `socket` · `for` loops · data types · `connect_ex`
```bash
python3 port_check.py
# Artifact: port_check.py
```

### 🚨 S08 · The Paper Trail
Parse a simulated auth log. Extract every failed login attempt.
Write the findings to a clean report automatically.

Key skills: `python3` · file I/O · `with open()` · `try/except` · string matching
```bash
python3 brute_detector.py
# Artifacts: brute_detector.py · brute_report.txt
```

### 🔎 S09 · The Automation Pivot
Give Python the keys to the OS. Run system commands from inside a script,
capture the output, and export a structured JSON security alert.

Key skills: `python3` · `subprocess` · `json` · `os` · process interrogation
```bash
python3 system_auditor.py
# Artifacts: system_auditor.py · incident_response.py · security_alert.json · handshake.txt
```

---

## 💡 Core Concepts

### The CIA Triad

| Property | Question It Answers | Example |
|---|---|---|
| **Confidentiality** | Who can see it? | `chmod 600 secrets.txt` |
| **Integrity** | Has it been tampered with? | Git commit hashes |
| **Availability** | Can authorized users access it? | Uptime, backups, failover |

### The Holy Trinity of Text Processing
```
grep  →  finds lines that match a pattern       (The Scalpel)
sed   →  finds and replaces text on the fly     (The Laser)
awk   →  extracts specific columns from data    (The Formatter)
```

### Git as an Accountability Tool
Every `git commit` creates a cryptographic hash — a tamper-evident, timestamped,
attributed record of exactly what changed and when. That is Accounting — the
third pillar of the AAA framework.

---

## 🛠️ TA Notes

> Hi, I'm Jane — your TA for your time as a Cybersecurity Fellow 
in the Class of 2026 Cohort. This repo is my own student artifact repo,
built to show you what yours can look like. Every script, every note, 
every commit message here was written with intention.
>
> You don't have to be perfect. You have to be consistent.
> Push something every week. Document what you learned.
> Future you — and future employers — will thank you.
>
> My door is always open. Well, my Slack is. Same thing.

---

## 📖 References

Chapple, M., Stewart, J. M., & Gibson, D. (2021). *ISC2 CISSP certified information
systems security professional official study guide* (9th ed.). Sybex.

NIST. (2022). *NICE Cybersecurity Workforce Framework* (NIST SP 800-181r1).
National Institute of Standards and Technology.

---

**Built intentionally · Current Status: Updated Often · TKH IF 2026**