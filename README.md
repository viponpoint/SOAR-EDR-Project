# SOAR-EDR-Project

# Introduction

In modern cybersecurity practices, the integration of SOAR (Security Orchestration, Automation, and Response) platforms with EDR (Endpoint Detection and Response) tools is essential for efficient threat management and incident response. Many security operations centers are starting to implement some kind of SOAR, and the objectives remain the same, reduction of repetitive task with automation while following a structured process, and these processes are also known as PlayBooks. This project leverages LimaCharlie as the EDR solution and Tines as the SOAR platform to create an automated response workflow for handling malware infections. Specifically, it addresses the scenario where a user executes a hack tool that infects their computer with LaZagne, an open-source credential retrieval tool. This playbook demonstrates how to automate detection, notification, and remediation steps to enhance security operations. One of the goals of this project is to get some hands-on experience with an EDR and SOAR by using Lima Charlie and Tines.

# Diagram

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/SOAR-EDR.Diagram.png)

#### Objectives
1. **Set Up the Environment:** Install and configure Windows Server 2022 as the client machine.
2. **Facilitate Infection:** Disable the Windows Server firewall to allow LaZagne malware installation.
3. **Detect Malware Execution:** Identify when a user executes a hack tool that leads to a LaZagne infection.
4. **Automate Threat Notifications:** Send detailed alerts to the security team via Slack and email upon detection.
5. **Prompt for User Action:** Request user input on whether to isolate the compromised machine.
6. **Automate Machine Isolation:** Automatically isolate the infected machine if the user approves.
7. **Update on Action Taken:** Inform the security team about the isolation status and the next steps.

#### Skills Learnt
- Installing and configuring Windows Server 2022.
- Configuring and using EDR tools for malware detection.
- Setting up and managing SOAR platforms for automated incident response.
- Integrating different security tools to create cohesive workflows.
- Automating notifications and user prompts through communication platforms.
- Implementing decision-based automation for incident remediation.

#### Tools Used
- **Windows Server 2022:** Operating system serving as the client machine for infection.
- **LaZagne:** Malware used for retrieving passwords stored on the infected computer.
- **LimaCharlie:** EDR platform used for detecting and responding to the malware infection.
- **Tines:** SOAR platform used for orchestrating the automated incident response workflow.
- **Slack:** Messaging platform for real-time notifications to the security team.
- **Email:** Communication medium for sending detailed alerts and user prompts.

#### Steps Taken

1. **Environment Setup:**

   - Install and configure Windows Server 2022.
   - Disable the Windows Server firewall to facilitate the installation of LaZagne malware.
   - To set up Slack for the project, register an account and then create a workspace, configure channels for security alerts, and generate an incoming webhook URL for Tines to send 
     notifications.
   - For Tines, register an account, create a new automation story, and integrate it with LimaCharlie and Slack by configuring the appropriate connectors and actions for the incident    
     response workflow.
   - To set up LimaCharlie for the project, register an account, deploy the LimaCharlie agent on the Windows Server 2022 machine, and configure detection rules to identify and respond 
     to LaZagne malware infections.

2. **Execution of Hack Tool:**
   - A user inadvertently executes a hack tool, resulting in the computer being infected with LaZagne malware.

3. **Detection by LimaCharlie:**
   - LimaCharlie detects the presence of LaZagne and logs the incident as a security threat.
   - The detection event is sent to Tines for further processing.

4. **Processing by Tines:**
   - Upon receiving the detection data from LimaCharlie, Tines initiates an automated workflow.
   - Tines sends a detailed alert message to a predefined Slack channel, notifying the security team of the malware detection.
   - Simultaneously, Tines sends an email with the detection details to a designated email address, prompting the recipient (SOC analyst) to decide whether to isolate the infected     
     machine or not.

5. **User Prompt for Action:**
   - The email from Tines includes options for the user to select "YES" or "NO" regarding isolating the compromised machine.

6. **User Response Handling:**
   - If the user selects "YES":
     - Tines triggers LimaCharlie to automatically isolate the infected machine from the network.
     - A follow-up message is sent to Slack, informing the team that "The computer has been isolated" along with the isolation status.
   - If the user selects "NO":
     - A message is sent to Slack stating, "The computer was not isolated, please investigate," prompting further manual investigation by the security team.

By implementing this automated incident response playbook, organizations can significantly reduce the time to detect and respond to security threats, ensuring swift action to mitigate potential damage and enhance overall security posture.

### Conclusion

The integration of SOAR and EDR platforms is a critical advancement in modern cybersecurity practices, enabling organizations to respond to threats with greater speed and efficiency. This project demonstrates the power of combining LimaCharlie’s robust detection and response capabilities with Tines’ sophisticated orchestration and automation features. By implementing this automated incident response workflow, we achieved the following:

- **Rapid Detection:** Immediate identification of malicious activity through LimaCharlie, reducing the window of exposure.
- **Automated Notification:** Swift and detailed alerts delivered via Slack and email, ensuring the security team is promptly informed.
- **User-Driven Response:** Empowering users to make critical decisions regarding machine isolation, enhancing the responsiveness of the security operations center (SOC).
- **Efficient Isolation:** Automatic isolation of infected machines when approved, minimizing potential damage and preventing further spread of malware.
- **Clear Communication:** Transparent status updates on actions taken, ensuring the security team remains informed and can act accordingly.

This project showcases the benefits of automating incident response processes, leading to a more resilient security posture. By leveraging tools like LimaCharlie and Tines, organizations can streamline their workflows, reduce manual intervention, and effectively mitigate risks. The successful implementation of this playbook not only demonstrates the technical capabilities of these tools but also highlights the importance of integrating SOAR and EDR solutions to safeguard against evolving cyber threats.

# Diagram

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/InstallLimaCharlie.jpeg)
This is the installation of LimaCharlie on my Server machine

</br>

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/LimaToServer.png)
Information about my connected Server can be seen in LimaCharlie interface

</br>

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/RuleForLazagne.png)
Creation of LaZagne detection and response rule in LimaCharlie. The purpose of creating detection and response rules for LaZagne in LimaCharlie is to automatically identify and mitigate the malware infection, triggering the necessary alerts and actions to protect the system.

</br>

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/RunLazagne.jpeg)
Running of LaZagne in Powershell on the Server to generate Telemetry

</br>

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/LimaCharlieAlert.png)
Alert is sent to LimaCharlie that LaZagne has been discovered

</br>

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/TinesMessage.png)
Tines get an Alert about the activity of LaZagne

</br>

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/SlackAlert.png)
Slack received an alert about the discovery of LaZagne as well

</br>

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/EmailAlert.png)
An email is also sent to the provided Email address of the SOC analyst

</br>

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/YESorNO.png)
If the Analyst clicks on YES, the system will be Isolated immediately

</br>

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/CompIsolated.png)
The system is immediately isolated as seen in the above diagram because the Analyst clicks YES

</br>

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/SlackIsolatedEM.png)
An alert is also sent to Slack as seen above that the system has been Isolated

</br>

![SOAR-EDR Diagram](https://github.com/viponpoint/SOAR-EDR-Project/blob/main/SlackNotIsolated.png)
But if the Analyst click NO, then the system won't be isolated as seen from this Slack alert

</br>





