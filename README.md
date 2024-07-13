# SOAR-EDR-Project

# Introduction

In modern cybersecurity practices, the integration of SOAR (Security Orchestration, Automation, and Response) platforms with EDR (Endpoint Detection and Response) tools is essential for efficient threat management and incident response. This project leverages LimaCharlie as the EDR solution and Tines as the SOAR platform to create an automated response workflow for handling malware infections. Specifically, it addresses the scenario where a user executes a hack tool that infects their computer with LaZagne, an open-source credential retrieval tool. This playbook demonstrates how to automate detection, notification, and remediation steps to enhance security operations.

# Diagram

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/SOAR-EDR.Diagram.png)


## Objectives
1.  Detect Malware Execution: Identify when a user executes a hack tool that leads to a LaZagne infection.
2.  Automate Threat Notifications: Send detailed alerts to the security team via Slack and email upon detection.
3.  Prompt for User Action: Request user input on whether to isolate the compromised machine.
4.  Automate Machine Isolation: Automatically isolate the infected machine if the user approves.
5.  Update on Action Taken: Inform the security team about the isolation status and the next steps.

### Skills Learned

- Advanced understanding of SIEM concepts and practical application.
- Development of critical thinking and problem-solving skills in cybersecurity.
- Proficiency in analyzing and interpreting network logs.
- Installation and configuration of Windows Server 2022
- Installation and configuration of Splunk Server
- Installation and configuration of Windows machine, splunk universal forwarder, sysmon, actomic red team. 
- Installation and configuration of Kali linux machine for the bruteforce attack using Crowbar.
- Understanding of forwarders (Universal and Heavy Forwarders) and configuring them to send data to the Splunk indexer.
- Initial configuration of Splunk, including setting up management ports, specifying directories for indexing data, and configuring Splunk to start at boot.
- Setting up and managing DNS, which is critical for AD operations.
- Installing the Active Directory Domain Services (AD DS) role.
- Promoting a server to a domain controller.
- Initial configuration tasks, such as creating the first domain in a new forest.
- Installation, configuration, and management of Windows Server operating systems.
- Enhanced knowledge of network protocols and security vulnerabilities.


### Tools Used
- Security Information and Event Management (SIEM) system for log ingestion and analysis.
- Windows Server 2022 was used to install and configure Active Directory, which serves as the primary directory service for user and computer management within the domain.
- Windows 10 Client Machine was used to act as domain-joined client machines for testing user authentication, policy enforcement, and monitoring.
- Active Directory Domain Services (AD DS) was used to manage domain resources, user authentication, and policy enforcement within the Windows Server environment.
- Splunk Universal Forwarder was used to collect and forward log data from Windows machines to the Splunk server for centralized log analysis.
- Sysmon (System Monitor) was used to provide detailed event logging on Windows machines, capturing high-value security event data.
- Kali Linux was used to serve as a penetration testing platform, executing various security assessments and vulnerability exploits against the network.
- Crowbar (Brute Force Tool) was used to perform brute force attacks against services such as RDP, SSH, VNC, and others, specifically targeting Active Directory credentials.
- Splunk inputs.conf
  
## Steps
The objective is to install virtual machines on virtualbox. By the end of the installation, i had one Windows 10 machine, one Kali Linux up, one Splunk server, and one Windows Server 2022. Diagrams to follow


The objective is to install and configure both sysmon and splunk onto my Windows target machine and Windows Server so they can start collecting telemetry and send logs over to our splunk server. Diagrams to follow


The objective is to install and configure active directory onto my server, and then promote it to a domain controller, and finally configure the target machine to join the newly created domain. Diagrams to follow


The objective is to use Kali Linux to perform a brute force attack onto the created new users. By doing so, we will be able to see what this looks like by using splunk to query for this activity afterwards. Also, the set up and installation of atomic red team and then run a test using atomic red team to generate telemetry and detect similar attacks.
Diagrams to follow


## Splunk inputs.conf
Splunk inputs.conf

[WinEventLog://Application]

index = endpoint

disabled = false

[WinEventLog://Security]

index = endpoint

disabled = false

[WinEventLog://System]

index = endpoint

disabled = false

[WinEventLog://Microsoft-Windows-Sysmon/Operational]

index = endpoint

disabled = false

renderXml = true

source = XmlWinEventLog:Microsoft-Windows-Sysmon/Operational

