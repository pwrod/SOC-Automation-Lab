# SOC Automation Lab  
A hands-on Security Operations Center (SOC) lab designed to simulate real-world detection, alerting, enrichment, and automation workflows. This project integrates Wazuh, Sysmon, TheHive, Shuffle SOAR, and the VirusTotal API to create a fully functional automated incident response pipeline.

---

## 📌 Overview  
This lab demonstrates how to build and automate a modern SOC workflow from scratch. It includes:

- Collecting and enriching Windows endpoint telemetry using Sysmon  
- Detecting malicious activity with Wazuh  
- Automating enrichment and case creation with Shuffle  
- Integrating VirusTotal for threat intelligence  
- Managing alerts and cases with TheHive  
- Triggering analyst notifications via email  

The project simulates an end-to-end incident lifecycle — from initial detection to automated triage and case creation.

---

## 🧱 Lab Architecture  

**Virtual Machines Used:**

- **Windows 11 VM**  
  - Sysmon installed for enriched telemetry  
  - Wazuh agent installed for log forwarding  
  - Used to generate alerts (e.g., by running Mimikatz)

- **Wazuh Server (Ubuntu 24.04 LTS)**  
  - Handles log ingestion, rules, and alerting  
  - Receives Sysmon logs from the Windows endpoint  
  - Provides alert payloads to Shuffle SOAR

- **TheHive Server (Ubuntu 24.04 LTS)**  
  - Manages case creation and incident tracking  
  - Receives automated alerts from Shuffle  
  - Utilizes Elasticsearch and Cassandra

- **Shuffle SOAR Platform**  
  - Serves as the automation engine  
  - Extracts hashes from alerts  
  - Queries VirusTotal  
  - Creates alerts in TheHive  
  - Sends email notifications

---

## 🔄 Workflow: End-to-End Automation  
The core automation pipeline performs the following sequence:

1. **Wazuh detects malicious activity** (e.g., Mimikatz execution)  
2. **Shuffle receives the alert** via webhook  
3. **Regex node extracts the SHA-256 hash** from the alert payload  
4. **VirusTotal API is queried** for threat intelligence  
5. **TheHive case is automatically created**  
6. **Email notification is sent** to the SOC analyst  
7. **Analyst reviews case in TheHive** with enriched intel

![Image Alt](https://github.com/pwrod/SOC-Automation-Lab/blob/main/images/shuffle%20workflow.png?raw=true)

This replicates a realistic SOC enrichment and triage process.

---

## 🛠️ Tools & Technologies

- **Wazuh** – SIEM for log analysis, detection, and alerting  
- **Sysmon** – Windows telemetry collection  
- **TheHive** – Security incident response and case management  
- **Shuffle** – No-code SOAR platform for automated workflows  
- **VirusTotal API** – External threat intelligence enrichment  
- **VirtualBox** – Virtualization platform for running the lab  
- **Ubuntu 24.04 LTS / Windows 11** – Operating systems for the environment  

---

## 🚨 Alert Simulation  
To validate detection and automation:

- Windows Defender was disabled  
- Mimikatz was executed on the Windows VM to generate malicious behavior  
- A custom Wazuh rule was created to detect the activity  
- Verified that logs were forwarded, parsed, and triggered the SOAR workflow
![image alt](https://github.com/pwrod/chat-gpt-test/blob/main/images/the%20hive%20alert.png?raw=true)

This ensured realistic detection and incident generation.

---

## 🧠 Skills Learned  

- **Security Event Monitoring & SIEM Configuration**  
  - Implemented log collection and analysis using Wazuh Manager and Wazuh Agents  
  - Created custom detection rules for malicious activity  
  - Forwarded enriched Sysmon logs for deep visibility  

- **Endpoint Telemetry & Logging Configuration**  
  - Installed and tuned Sysmon to capture process, network, and file events  
  - Improved signal-to-noise ratio by customizing event collection  

- **Security Automation & SOAR Workflows**  
  - Built automated workflows in Shuffle integrating Wazuh, VirusTotal, and TheHive  
  - Extracted hashes using regex and automated enrichment with VirusTotal  
  - Implemented automated notifications and case creation to accelerate response  

- **Incident Response Practices**  
  - Managed alerts and structured cases within TheHive  
  - Enriched events with threat intelligence for faster triage  
  - Learned key components of the detection → analysis → response lifecycle  

- **Threat Intelligence Integration**  
  - Queried VirusTotal via API to gather malware data  
  - Automated VirusTotal enrichment as part of the triage workflow  

- **Virtualization & Lab Architecture**  
  - Built a multi-VM SOC lab environment using VirtualBox  
  - Configured Ubuntu and Windows systems for production-like SIEM/SOAR usage  

- **Adversary Simulation & Testing**  
  - Used Mimikatz to generate realistic malicious events  
  - Verified detection accuracy and end-to-end automation functionality  

- **API Usage & Data Parsing**  
  - Interacted with REST APIs for Wazuh, TheHive, VirusTotal, and Shuffle  
  - Extracted structured data using regex and JSON parsing techniques  

---

## 📚 Future Enhancements  
Potential improvements include:

- Adding Sigma rules for cross-platform detection  
- Integrating an ELK or OpenSearch dashboard for visualization  
- Adding an auto-remediation step to isolate compromised hosts  
- Expanding detections to include ransomware behavior  

---

## 📁 Project Purpose  
This project demonstrates practical, hands-on cybersecurity skills applicable to:

- SOC Analyst (Tier 1–2) roles  
- Incident Response  
- Detection Engineering  
- Threat Intelligence  
- Cybersecurity Automation  

It showcases the ability to design, build, and automate a functioning SOC pipeline from scratch.
