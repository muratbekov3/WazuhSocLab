Markdown

# 🛡️ SOC Lab: Automated Threat Detection & Mitigation with Wazuh

<p align="center">
  <img src="https://img.shields.io/badge/SIEM-Wazuh-blue?style=for-the-badge&logo=wazuh" alt="Wazuh">
  <img src="https://img.shields.io/badge/Security-IPS-red?style=for-the-badge" alt="IPS">
  <img src="https://img.shields.io/badge/Environment-Docker-2496ED?style=for-the-badge&logo=docker" alt="Docker">
  <img src="https://img.shields.io/badge/Framework-MITRE_ATT%26CK-orange?style=for-the-badge" alt="MITRE">
</p>

## 📝 Project Overview
This project demonstrates the deployment of a **Security Operations Center (SOC)** environment using **Wazuh (SIEM/XDR)**. The lab is designed to detect and automatically mitigate real-world cyber attacks, such as **DDoS (HTTP Flooding)**, **SSH Brute Forcing**, and **Suspicious Windows Process Chains**, by leveraging custom detection rules and **Active Response (IPS)**.

---

## 🏗️ Lab Architecture

<p align="center">
  <img src="img/Gemini_Generated_Image_yurqlkyurqlkyurq.png" width="800">
  <br>
  <em>High-level architecture: Kali Linux (Attacker) ➔ Ubuntu/Windows (Agents) ➔ Wazuh Manager (Docker Analysis Engine).</em>
</p>

### 🛠️ Components:
* **Wazuh Manager:** Centralized engine hosted in **Docker**.
* **Ubuntu Server:** Running **Nginx** and the Wazuh Agent.
* **Windows 10:** Running **Sysmon** for advanced endpoint telemetry.
* **Kali Linux:** Attacker machine using `ab`, `curl`, and `hydra`.

---

## 🛠️ Monitoring & Hygiene

Before launching attacks, the environment was audited for baseline security and agent health.

<p align="center">
  <img src="img/Screenshot from 2026-04-06 17-06-17.png" width="800">
  <br>
  <em><b>Fleet Status:</b> Monitoring active connectivity for Ubuntu and Windows 10 agents.</em>
</p>

<p align="center">
  <img src="img/Screenshot from 2026-04-06 17-06-37.png" width="800">
  <br>
  <em><b>Threat Hunting Overview:</b> Aggregated security events dashboard ready for analysis.</em>
</p>

---

## 🚀 Attack Simulation & Detection

### 1. DDoS Attack (Nginx HTTP Flood)
Simulated a high-volume attack from Kali Linux using Apache Benchmark (`ab`).

<p align="center">
  <img src="img/Screenshot from 2026-04-06 17-07-33.png" width="800">
  <br>
  <em><b>Alert Triggered:</b> Rule 100210 (Level 12) detecting 100+ requests in 10 seconds.</em>
</p>


### 2. Web Vulnerability & OS Attacks

Detecting Local File Inclusion (LFI) attempts and unauthorized administrative activity.

<p align="center">
<img src="img/Screenshot from 2026-04-06 17-33-09.png" width="800">

<em><b>Events:</b> Successful detection of LFI, PAM session closures, and unauthorized sudo commands.</em>
</p>
🛡️ Automated Mitigation (Active Response)

The lab moves from detection to prevention. When the DDoS threshold is met, the Manager commands the Agent to block the attacker's IP automatically using the firewall-drop script.

<p align="center">
<img src="img/Screenshot from 2026-04-06 17-32-15.png" width="800">

<em><b>IPS Action:</b> The Active Response engine confirming the automated firewall block was executed.</em>
</p>

📈 Advanced Analytics & Compliance
MITRE ATT&CK Mapping

Alerts are mapped to the MITRE framework to visualize adversary tactics.

<p align="center">
<img src="img/Screenshot from 2026-04-06 17-09-15.png" width="800">

<em><b>MITRE Dashboard:</b> Mapping lab events to T1110 (Brute Force) and T1190 (Exploiting Public Applications).</em>
</p>
File Integrity Monitoring (FIM)

Tracking unauthorized changes to system configuration files in real-time.

<p align="center">
<img src="img/Screenshot from 2026-04-06 17-08-17.png" width="800">

<em><b>FIM Dashboard:</b> Real-time auditing of /etc/ and other critical system directories.</em>
</p>
