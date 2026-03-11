# TKH Innovation Fellowship — Phase 1 Cybersecurity
### `tkh-ifcs-p1-student` · Class of 2026

---

```
 _____ _  ___   _   ___ _  _             _
|_   _| |/ / | | | |_ _| \| |_ __  ___ _| |_ ___ _ _
  | | | ' /| |_| |  | || .` | '_ \/ _ \ |  _/ -_) '_|
  |_| |_|\_\ \___/  |___|_|\_| .__/\___/_|\__\___|_|
                               |_|
  Cybersecurity · Phase 1 · Spring 2026
```

---

> *"The more I learn, the more I realize how much I don't know."*
> — Richard Feynman

---

## 👋 Welcome

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
│   ├── discovery.txt          # Filesystem recon — Night 1 lab output
│   ├── threat_ips.txt         # Extracted attacker IPs — Night 3 lab output
│   └── notes.md               # Week 01 concept notes
│
├── week-02/                   # Coming March 17
├── week-03/                   # Coming March 24
│
└── README.md
```

---

## 🗓️ Week Tracker

| Week | Dates | Theme | Status |
|:---:|:---:|---|:---:|
| 01 | Mar 10–12 | Terminal · Permissions · Stream Editing · Git | ✅ |
| 02 | Mar 17–19 | Access Control · Cryptography · Networking | ⏳ |
| 03 | Mar 24–26 | Advanced Automation · Bash Scripting · Cron | ⏳ |
| 04 | Mar 31–Apr 2 | Reconnaissance · OSINT · Threat Modeling | ⏳ |

---

## 🚀 Getting Started

New to the program? Here's how to clone this repo and set up your environment.

**Step 1 — Clone the repo**
```bash
git clone git@github.com:janepierresgithub/tkh-ifcs-p1-student.git
cd tkh-ifcs-p1-student
```

**Step 2 — Run the lab bootstrap**
```bash
# Night 1
curl -sL https://gist.githubusercontent.com/grobbins-cell/raw/setup_lab_01.sh | bash

# Night 3
curl -sL https://gist.githubusercontent.com/grobbins-cell/610867dae208e88154070b0ca78084df/raw/661e54024519f558ba4ed7e5d78655a429bef748/setup_lab_03.sh | bash
```

**Step 3 — Do the work, then push it**
```bash
git add .
git commit -m "feat: add week-01 lab artifacts"
git push origin main
```

---

## 📚 Week 01 — What We Covered

### 🌱 Night 1 · Terminal Genesis
Your first night in a headless Linux environment. No GUI. Just you and the terminal.

Key skills: `ls` `cd` `pwd` `mkdir` `cat` `find` `man` · FHS navigation · SSH · Git setup

```bash
# The command that started everything
ssh jane@janetheta
```

---

### 🔐 Night 2 · The Keymaster
Who can read it? Who can write it? Who can run it? Linux answers these questions
with nine bits and three letters: `rwx`.

Key skills: `chmod` `chown` `ls -la` · SUID auditing · Principle of Least Privilege

```bash
# Lock down your SSH directory
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

---

### 🔍 Night 3 · Stream Editing & Automation
10,000 lines of web server logs. Three attackers buried in the noise.
One pipeline to find them all.

Key skills: `grep` `awk` `sed` `sort` `uniq` · stdout redirection · pipeline chaining

```bash
# The pipeline that extracts attacker IPs from a live log
grep "UNION SELECT" ~/access.log \
    | awk '{print $1}' \
    | sort | uniq \
    > ~/threat_ips.txt
```

---

## 💡 Core Concepts

### The CIA Triad
Everything in cybersecurity comes back to three things:

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
attributed record of exactly what changed and when. That's not just version control.
That's **Accounting** — the third pillar of the AAA framework.

---

## 🛠️ TA Notes

> Hi, I'm Jane — your TA for Phase 1. This repo is my own student artifact repo,
> built to show you what yours can look like. Every script, every note, every
> commit message here was written with intention.
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

*Built in public · Updated weekly · TKH IF 2026 · Class of 2026*
