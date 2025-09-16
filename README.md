# Attack Artifacts in Logs — Analysis and Threat Detection in SIEM Systems

> **Engineering thesis project — author: Damian Bugaj**  
> *Faculty of Applied Informatics and Mathematics, SGGW*

---

## 📌 Project Overview

The project focuses on **analyzing attack artifacts in system and network logs** and on **detecting threats using SIEM-class systems**.  
For this purpose, a complete **laboratory environment simulating a SOC** was built, allowing to simulate real cyberattacks, capture their traces, and analyze detection methods.

Main project goals:

- understand how attacks **leave detectable artifacts in logs**
- learn how to **collect and correlate data from multiple sources**
- detect attacks using **Elastic Stack, Zeek, Suricata, Sysmon, Windows Event Log**
- map attacker activity to the **MITRE ATT&CK** model
- design and build a **SOC laboratory environment** enabling **realistic attack simulations**

---

## 🧪 Laboratory Environment

The environment replicates a corporate network and consists of:

- **pfSense** — firewall and SPAN/mirror port  
- **Kali Linux** — attacking machine  
- **Windows Server 2019** — AD domain controller, DNS, IIS  
- **Windows 10** — domain client (victim machine)  
- **Ubuntu (Wazuh)** — HIDS host collecting logs from agents  
- **Ubuntu (Elastic Stack)** — main SIEM detection host containing:
  - **Fleet Server with Elastic Agent**
  - **Filebeat, Winlogbeat and other Beats**
  - **Kibana and Elasticsearch**
  - integrated **Suricata** and **Zeek** for network traffic analysis

> Entire environment runs on VMware Workstation

---

## ⚡ Attack Scenario — Implementation and Execution

1. **Network reconnaissance** – subnet and port scanning (Nmap)
2. **Brute-force attack on RDP** – Hydra + SecLists dictionaries
3. **Remote login to the machine** – xfreerdp (RDP)
4. **Download and execute Apollo payload** – generated in Mythic C2
5. **Persistence** – scheduled task (SYSTEM) and registry entry (user)
6. **Post-exploitation reconnaissance and data exfiltration** – Apollo functions (screenshot, keylogger, download)
7. **Test of persistence mechanisms** – logging in as another user

---

## 🕵️ Detection and Analysis

The following tools and methods were used to detect and investigate the attack:

- **Network detection** — Suricata alerts, Zeek logs
- **Host detection** — Sysmon and Windows Event Log 
- **Central log analysis** — Elastic Stack dashboards (Kibana)  
- **File Integrity Monitoring (FIM)** — tracking file and registry changes  
- **Sandbox and reputation** — analyzing the file in VirusTotal

Identified artifacts included: **attacker IP address, file hashes, paths, registry changes, encoded PowerShell commands, process trees, network anomalies**, and **techniques mapped to MITRE ATT&CK**.

---

## 🧠 Analytical Models

Collected artifacts and activities were classified using:

- **Pyramid of Pain** — assessing detection value vs. ease of evasion  
- **MITRE ATT&CK** — mapping each attack stage to known tactics and techniques (visualized in ATT&CK Navigator)

This allowed determining which techniques were effectively detected and where visibility gaps existed.

---

## 📈 Results

- Built a complete SOC lab environment from scratch  
- Executed a full attack chain and collected real detection data  
- Performed a **comprehensive detection analysis**  
- **Reconstructed the exact attack timeline from logs**
- Mapped all stages to **MITRE ATT&CK** and evaluated tool effectiveness  

The repository contains **step-by-step documentation of attack and detection** along with **screenshots from the attack and detection process**.

---

## 🚀 Future Work

Possible future enhancements:

- Integration of TheHive + Cortex (SOAR)  
- Connecting MISP for automated IoC ingestion  
- Exposing a Cowrie honeypot to the Internet  
- Adding vulnerable hosts for penetration testing  
- Introducing a DMZ network zone  
- Enabling IPS mode in Suricata  
- Creating and testing custom Sigma rules  
- RAM analysis using Volatility  
- Adding more offensive tools and APT-style scenarios

---

## 📂 Repository Structure
```
siem-attack-detection-lab
├── 03_lab_environment/         → documentation of the lab environment configuration
├── 05_attack_scenario/         → implementation and execution of the attack scenario
├── 06_detection_and_analysis/  → log analysis and threat detection process
├── 07_final_analysis/          → final analysis, conclusions, evaluation of tools
├── 8.3_future_work.md          → directions for further development of the environment
├── docs/                       → folder with the engineering thesis (PDF)
├── README.md                   → main project description
```

Each chapter folder contains:
- one `chapter_overview.md` (introduction to the chapter),
- a set of `.md` files for each subchapter,
- an `images/` folder with related screenshots.

---

## 📘 Full Engineering Thesis

The repository also includes the **complete engineering thesis** containing:

- a detailed description of the detection machines’ configuration,  
- a diagram of the log flow within the environment,  
- additional theoretical and practical information.

📄 [View full thesis (PDF)](./docs/my_engineering_thesis.pdf)

---

## 📫 Contact

🔗 [LinkedIn](https://www.linkedin.com/in/damian-bugaj-4a948827a/)  
📧 Email: damianbugaj6@icloud.com

---

## 📌 Keywords

`siem` · `cybersecurity` · `elastic-stack` · `suricata` · `zeek` · `sysmon` · `Windows-event-log` · `threat-detection` · `mitre-attack` · `soc` · `log-analysis` · `blue-team` · `filebeat` · `winlogbeat` · `kibana` · `elasticsearch` · `kali-linux` · `network-security` · `endpoint-security` · `pfsense` · `mythic` · `c2-framework` · `log-monitoring` · `event-correlation` · `homelab` · `vmware` · `pyramid-of-pain` 
