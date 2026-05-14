# penetration-testing-lab09
PenTest Lab 9 — OSINT, Recon &amp; Exploitation of Metasploitable2 | Metasploit, Nmap, Censys | 4/4 Exploits Successful | ROOT Access via vsftpd &amp; Samba CVEs
# 🔴 Penetration Testing Lab — OSINT, Reconnaissance & Exploitation



---

## 🖥️ Lab Environment

| Field | Value |
|-------|-------|
| Attacker Machine | Kali Linux |
| Attacker IP | 192.168.17.128 |
| Target Machine | Metasploitable2 Linux |
| Target IP | 192.168.17.134 |
| Network | VMware NAT |
| Metasploit Version | 6.4.112-dev |

---

## 📋 Lab Phases

### Phase 1 — OSINT
- Used **OSINT Framework** for IP reconnaissance
- Analyzed target public IP via **IP2Location** (ISP: PTCL, Rawalpindi, Pakistan)

### Phase 2 — Reconnaissance
- **Censys** scan revealed 20,432 hosts on PTCL network including 11 exposed Hikvision CCTV cameras
- **Nmap** (`-sV -A`) scan identified 13 open ports on Metasploitable2 including FTP, SSH, Samba, HTTP, Telnet

### Phase 3 — Vulnerability Research
- Searched **Exploit-DB** for Hikvision CVEs
- Identified critical vulnerabilities: CVE-2011-2523 (vsftpd), CVE-2007-2447 (Samba), default credentials on SSH & Tomcat

### Phase 4 — Exploitation

| # | Attack | Module | Port | Access | Result |
|---|--------|--------|------|--------|--------|
| 1 | FTP Backdoor | vsftpd_234_backdoor | 21 | **ROOT** | ✅ |
| 2 | SSH Brute Force | ssh_login | 22 | msfadmin | ✅ |
| 3 | Samba Exploit | usermap_script | 139/445 | **ROOT** | ✅ |
| 4 | Tomcat Default Creds | Manual | 8180 | Admin | ✅ |

**4/4 exploits successful — 3/4 resulted in ROOT access**

---

## 🛠️ Tools Used

- **Kali Linux** — Attacker OS
- **Metasploit Framework 6.4** — Exploitation
- **Nmap** — Port scanning & service detection
- **Censys** — Network-wide OSINT
- **OSINT Framework** — Intelligence gathering
- **Exploit-DB** — Vulnerability research

---

## 🔑 Key Findings

- vsftpd 2.3.4 backdoor (CVE-2011-2523) — ROOT shell via FTP
- Samba 3.0.20 command injection (CVE-2007-2447) — ROOT shell
- Default credentials never changed (msfadmin:msfadmin, tomcat:tomcat)
- 13 unnecessary open ports = massive attack surface
- 11 Hikvision CCTV cameras publicly exposed on PTCL network

---

## ⚠️ Disclaimer

All activities were performed in a **controlled virtual lab environment** for educational purposes only. Metasploitable2 is an intentionally vulnerable machine designed for penetration testing practice. No real systems were targeted.
