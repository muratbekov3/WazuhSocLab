🛡️ SOC Lab: Automated Threat Detection & Mitigation with Wazuh
📝 Project Overview

This project demonstrates the deployment of a Security Operations Center (SOC) environment...
🏗️ Lab Architecture

    ![Wazuh Dashboard Overview](WazuhSocLab/Gemini_Generated_Image_yurqlkyurqlkyurq.png)
    Figure 1: High-level architecture showing the flow from Kali (Attacker) to Wazuh (SIEM) and back to the Agent (IPS).

🛠️ Key Features & Configurations
1. Custom Detection Rules

I developed a suite of custom rules in local_rules.xml to identify specific threats...
2. Monitoring & Hygiene

Before attacking, the environment is monitored for overall health and security posture.

    [INSERT SCREENSHOT: Wazuh Overview Dashboard]
    Figure 2: Global overview showing active agents (Ubuntu & Windows) and overall security events.

    [INSERT SCREENSHOT: Security Hygiene / SCA Dashboard]
    Figure 3: Configuration Assessment showing the "hygiene" and vulnerability status of the endpoints.

🚀 Attack Simulation & Proof of Work
Phase 1: The Attack (Kali Linux)

I simulated several attack vectors from a Kali Linux VM:

    DDoS: ab -n 10000 -c 100 http://<AGENT_IP>/

    LFI/Recon: curl http://<AGENT_IP>/etc/passwd

    [INSERT SCREENSHOT: Docker Compose PS]
    Figure 4: Terminal output showing the Wazuh stack running successfully in Docker.

Phase 2: Detection (Threat Hunting)

Wazuh successfully parsed the logs and triggered high-severity alerts.

    [INSERT SCREENSHOT: Threat Hunting Events - DDoS Alert]
    Figure 5: High-severity alert for Rule 100210 (Nginx DDoS) showing the attacker's IP.

    [INSERT SCREENSHOT: Events - LFI & Sudo Attempts]
    Figure 6: Detection of Local File Inclusion (LFI) and unauthorized sudo command execution.

Phase 3: Mitigation (Active Response)

The most critical part of the lab: the Manager automatically commanded the Agent to block the malicious IP.

    [INSERT SCREENSHOT: Events - "Host blocked by firewall-drop"]
    Figure 7: The Active Response log confirming the automated block was successful.

📈 Advanced Analytics
MITRE ATT&CK Mapping

The alerts are automatically mapped to the MITRE framework for tactical analysis.

    [INSERT SCREENSHOT: MITRE ATT&CK Dashboard]
    Figure 8: Visualization of detected techniques mapped to the MITRE ATT&CK matrix.

File Integrity Monitoring (FIM)

I monitored sensitive system files for unauthorized changes.

    [INSERT SCREENSHOT: File Integrity Monitoring Dashboard]
    Figure 9: Real-time tracking of file modifications on the Ubuntu server.
