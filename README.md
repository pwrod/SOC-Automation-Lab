<h2 align="left">SOC-Automation-Lab</h2>

###

<h3 align="left">📃Project Description:</h3>

###

<h6 align="left">📌Enrich logs with Sysmon<br>📌Receive alerts from Wazuh<br>📌Utilize TheHive case management<br>📌Create a shuffle workflow for email notifications</h6>

###

<h3 align="left">🛠️Tools:</h3>

###

<h6 align="left">VirtualBox: Install and run various operating systems on a host machine.<br><br>Sysmon: Windows system service and device driver that logs system activity.<br><br>Wazuh: (SIEM) platform designed for threat detection, log analysis, and incident response.<br><br>TheHive: open-source Security Incident Response Platform.<br><br>Shuffle: A platform for building and executing automation workflows.<br><br>VirusTotal API:  interact with VirusTotal's extensive database of malware samples.</h6>

###

<h3 align="left">📃Steps:</h3>

###

<h4 align="left">VirtualBox Install:</h4>

###

<p align="left">https://www.virtualbox.org/wiki/Downloads</p>

###

<h4 align="left">Create Windows 11 VM</h4>

###

<p align="left">RAM: 4GB+<br>SSD: 80GB+</p>

###

<p align="left">Install and Configure Sysmon</h4>

###

<p align="left">https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon</p>

###

<h4 align="left">VM for Wazuh</h4>

###

<p align="left">RAM: 8GB+<br>SSD: 30GB+<br>OS: Ubuntu 24.04 LTS</p>

###

<h4 align="left">Install Wazuh</h4>

###

<p align="left">https://documentation.wazuh.com/current/installation-guide/index.html</p>

###

<h4 align="left">VM for TheHive</h4>

###

<p align="left">RAM: 16GB+<br>SSD: 30GB+<br>OS: Ubuntu 24.04 LTS</p>

###

<h4 align="left">TheHive Install:</h4>

###

<p align="left">https://docs.strangebee.com/thehive/installation/installation-guide-linux-standalone-server/</p>

###

<p align="left">Install and Configure TheHive, Cassandra, and Elasticsearch</h4>

###

<h4 align="left">On Windows 11 VM install Wazuh-agent</h4>

###

![image alt](https://github.com/pwrod/SOC-Automation-Lab/blob/main/images/Wazuh%20Agent.png?raw=true)

###

<p align="left">Disable Windows defender</p>

###

<h4 align="left">Install latest mimikatz release: https://github.com/gentilkiwi/mimikatz/releases</h4>

###

<p align="left">Create custom rule for mimikatz alert on Wazuh</p>

###

<p align="left">Run mimikatz on Windows 11 VM to generate alert in Wazuh</p>

###

![image alt](https://github.com/pwrod/SOC-Automation-Lab/blob/main/images/mimikatz%20alert.png?raw=true)

###

<h4 align="left">Shuffle Workflow:</h4>

###

<p align="left">Step 1:  Wazuh Alert<br>- Webhook trigger<br>- Configure Wazuh to send alerts via webhook<br><br>Step 2: Regex Capture<br>- Capture the SHA256 hash from Wazuh alert<br><br>Step 3:  VirusTotal API<br>- Receive data from regex capture<br>- Get hash report from virustotal<br><br>Step 4: TheHive<br>- Create new Hive organization with a service and normal account<br>- Connect service account API to shuffle <br>- Use details from Wazuh alert to create TheHive alert<br><br>Step 5: Email<br>- When virustotal node is activated send analyst email</p>

###

![image alt](https://github.com/pwrod/SOC-Automation-Lab/blob/main/images/shuffle%20workflow.png?raw=true)

###

<h3 align="left">Node Data:</h3>

###

<p align="left">[image of thehive alert]</p>

###

<p align="left">[image of email from shuffle]</p>

###
