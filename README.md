# 🛡️ End-to-End Enterprise Cyber Security Assessment & Hardening Portfolio

<img width="1080" height="1080" alt="Poster" src="https://github.com/user-attachments/assets/c5bd4fed-dc34-49b0-b7a0-06efe3c1ddae" />


![Project Status](https://img.shields.io/badge/Status-Completed-success?style=flat-square)
![Role](https://img.shields.io/badge/Role-Cyber%20Security%20Intern-blue?style=flat-square)
![Company](https://img.shields.io/badge/Organization-Kairiz%20Cyber%20Technologies-orange?style=flat-square)

This repository serves as a comprehensive portfolio containing the technical documentation, proof-of-concept exploits, hardening configurations, and monitoring strategies developed during a **1-Month Remote Cyber Security Internship** at Kairiz Cyber Technologies. The project is systematically broken down into four foundational phases covering assessment, exploitation, defensive engineering, and continuous monitoring.

---

## 👥 Contributor Details
* **Intern Name:** Kanwar Azlan
* **Role:** Cyber Security Internee
* **Project Type:** 1-Month Remote Internship Project Report

---

## 🏗️ Lab Infrastructure & Asset Inventory
A multi-tier virtualized enterprise lab environment was built using VMware to isolate, test, attack, and defend corporate assets safely.

| Asset Identifier | IP Address | MAC Address | Role / Purpose | Operating System |
| :--- | :--- | :--- | :--- | :--- |
| **Kali Linux VM** | `192.168.210.131` | `00:0c:29:36:70:ef` | Security Testing Host Machine | Kali Linux |
| **SEED Ubuntu Server** | `192.168.210.130` | `00:0c:29:a5:63:2b` | Central Infrastructure Server | Ubuntu Server |
| **SEED Ubuntu WS** | `192.168.210.129` | `00:0c:29:72:e5:c8` | Internal Corporate Workstation | Ubuntu Desktop |
| **Metasploitable** | `192.168.210.128` | `00:0c:29:22:3c:c8` | Intentionally Vulnerable Target Client | Linux (Metasploitable) |
| **Wazuh SIEM** | `192.168.210.132` | `00:0c:29:3d:7e:70` | Central Log Analytics Manager | CentOS Linux 7 (Core) |

---

## 📂 Project Phases Summary

### 🔍 Phase 1: Initial Network Assessment
* **Objective:** Discover live network assets, identify open interaction ports, map local topologies, and verify endpoint operating systems.
* **Technical Implementations:**
  * Utilized `Nmap` ping sweep parameters (`-sP`) to enumerate live systems on the local subnet.
  * Executed deep OS fingerprinting engines (`-O`) to map architecture parameters.
  * Ran advanced Nmap Scripting Engine (`NSE`) routines over open SMB interfaces to match physical hardware layer layers (`MAC address`).

### 💥 Phase 2: Penetration Testing (Internal & External PoCs)
* **Objective:** Conduct targeted active exploitation tests to isolate insecure authentication patterns.
* **Technical Implementations:**
  * **Internal Exploitation:** Discovered an unencrypted FTP service enabling cleartext credential exposures via native `Nmap` scans.
  * Used Metasploit modules to perform automated authentication audits against target accounts.
  * **Traffic Analysis:** Executed network interceptions via `Wireshark` from an adjacent workstation during user transactions to harvest active usernames and passwords directly out of plaintext transport layers.
  * Simulated the workflow across separate infrastructure interfaces (NAT vs Host-Only) to isolate visibility scopes during pivoting maneuvers.

### 🧱 Phase 3: Security Hardening & Disaster Recovery
* **Objective:** Remediation engineering aimed at eliminating discovery vectors, validating system perimeters, and ensuring data survival.
* **Technical Implementations:**
  * **FTP Hardening:** Disabled anonymous server access bindings inside the FTP server engine configuration file:
    ```bash
    sudo nano /etc/vsftpd.conf
    # Set anonymous_enable = NO
    sudo systemctl restart vsftpd
    ```
  * **Firewall Engineering:** Configured a strict **Default-Deny** incoming policy using `ufw` on core nodes, adding explicit allow rules strictly for production requirements:
    ```bash
    sudo ufw default deny incoming
    sudo ufw default allow outgoing
    sudo ufw allow 22/tcp
    sudo ufw allow 80/tcp
    sudo ufw allow 443/tcp
    sudo ufw enable
    ```
  * **Disaster Recovery Strategy:** Authored a high-availability and business continuity playbook managing weekly full system snapshots, automated `rsync` file mirror rotations, hardware RAID structures, and multi-factor authentication requirements.

### 📊 Phase 4: Monitoring and Incident Response (SIEM)
* **Objective:** Establish continuous visibility and active alert ingestion workflows across enterprise assets.
* **Technical Implementations:**
  * Deployed a centralized **Wazuh** open-source SIEM infrastructure engine to process real-time events.
  * Tuned alert aggregation filters to flag anomalous activities, host-level modifications, or brute-force tracking behaviors.
  * Simulated network exploit scripts to validate custom monitoring rule execution paths and check live threat dashboard generation graphs.

---

## 🚀 Verification Commands Quick Reference

### Nmap Discovery Sweep
```bash
nmap -sP 192.168.210.0/24
nmap -O 192.168.210.128
