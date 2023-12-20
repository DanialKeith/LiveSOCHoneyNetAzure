# Creating a Live SOC Honey Net in Azure

![1](https://github.com/DanialKeith/LiveSOCHoneyNetAzure/assets/154257195/c8da8a80-8a51-40c5-833d-2bf200cec0d9)


## Introduction: Conceptualizing an Azure-Based Honeynet
I am pleased to present my recent project, which involves setting up a honeynet in the Azure environment to simulate real-world cyber threats. This project demonstrates my skills in Azure security, emphasizing my experience in handling incident responses and enhancing network security.
## Project Objective: Simulating Cyber Attacks for Enhanced Security
The central aim was to deploy intentionally vulnerable virtual machines in Azure's cloud infrastructure. This setup was designed to attract cyber-attacks, thereby enabling a detailed analysis of adversary tactics and methods. The project serves as a testament to my adeptness in swiftly identifying and resolving security issues.
## Project Foundations: Technologies and Frameworks Utilized
The project leveraged a comprehensive array of Azure services and security standards, including:

-	Azure Virtual Network (VNet) and Network Security Group (NSG)
-	Windows (2) and Linux (1) Virtual Machines
-	Log Analytics Workspace with Kusto Query Language (KQL) Queries
-	Azure Key Vault, Azure Storage Account
-	Microsoft Sentinel for SIEM
-	Microsoft Defender for Cloud
-	Remote access via Windows Remote Desktop
-	System management using CLI and PowerShell
-	Compliance with NIST SP 800-53 Rev 5 and NIST SP 800-61 Rev 2
  
## Methodology
### Setting up the Honeynet

I commenced by [Deploying Vulnerable VMs in Azure](https://github.com/DanialKeith/AzureVirtualMachinePrep), creating an environment that mirrors real-world insecurities.

### Monitoring and Analytical Framework

Using Azure, I integrated log sources into a Log Analytics workspace. Microsoft Sentinel's capabilities were harnessed for creating attack maps, alerting, and incident management.

### Metric-Based Evaluation

An initial 24-hour observation period established a baseline of security metrics in the unsecured environment. This was crucial for a comparative analysis post-remediation.

### Incident Response and Hardening

[Post-incident analysis](https://github.com/DanialKeith/AzureIncidentAnalysis) led to implementing security measures, alert analysis, and best practices tailored to Azure, marking a transition to a more secure environment.
### Re-Evaluation Post-Security Enhancements

A subsequent 24-hour observation quantified the impact of the security enhancements, allowing for a detailed comparative assessment.

### Architectural Overview

![2](https://github.com/DanialKeith/LiveSOCHoneyNetAzure/assets/154257195/0f923cf8-c729-4e45-a372-1a23b38f2fb2)


### Initial Setup: Pre-Hardening Architecture

Initially, all resources were intentionally exposed to the internet, with VMs having open NSGs and firewalls. This stage was crucial for attracting and analyzing cyber threats.

### Post-Enhancement Architecture

![3](https://github.com/DanialKeith/LiveSOCHoneyNetAzure/assets/154257195/8004aa02-ee4d-436b-8604-bdf01f73411e)


Following the security enhancements, the architecture underwent significant modifications:
-	Refined NSG settings to limit traffic.
-	Configured VM firewalls for specific access control.
-	Shifted to Private Endpoints for Azure resources, enhancing security and minimizing public exposure.
  
## Attack Maps and Security Metrics

### Pre-Hardening Analysis

>Please note: The attack maps were created using data extracted from a workbook that employed pre-configured [KQL .JSON](https://github.com/DanialKeith/KQLMonitoringSecurity) map files. These files offered an organized depiction of the attack patterns along with relevant data, facilitating the production of visual aids that effectively depicted the cyber threats and their influence on the system.

This attack map highlights the risks associated with an unsecured Network Security Group (NSG), showing how it permits unchecked flow of malicious traffic. The visual representation emphasizes the critical need for robust security protocols, including the tightening of NSG rules, to block unauthorized access and reduce potential security threats.

![map 1](https://github.com/DanialKeith/LiveSOCHoneyNetAzure/assets/154257195/2a4e8d21-4305-4119-b34f-08bd9757e69a)


This attack map displays a substantial number of syslog authentication failures on the deployed Linux server, indicating external attempts at unauthorized access. It highlights the need for securing Linux servers with strong authentication procedures and carefully monitoring system logs for any signs of intrusion attempts.

![map 2](https://github.com/DanialKeith/LiveSOCHoneyNetAzure/assets/154257195/4dc72b6e-57a1-42e5-a2ec-55e290dfc43c)


This attack map reveals a multitude of RDP failures, depicting continuous efforts by potential attackers to take advantage of these protocols. The graphic representation underlines the importance of safeguarding remote access and file sharing services to prevent unauthorized entry and guard against possible cyber risks.

![map 3](https://github.com/DanialKeith/LiveSOCHoneyNetAzure/assets/154257195/387da31f-2f1f-455f-9eee-fbdb15b76377)


### Post-Hardening Outcomes

The post-enhancement period showed a notable decrease in security incidents, validating the effectiveness of the implemented security measures.
The table below presents the metrics recorded in our unsecured environment over a 24-hour period: Start Time: 2023-12-14 12:04 Stop Time: 2023-12-15 12:04

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 21430
| Syslog                   | 1382
| SecurityAlert            | 1
| SecurityIncident         | 149
| AzureNetworkAnalytics_CL | 2841

The table below presents the metrics recorded in our secured environment over a 24-hour period: Start Time: 2023-12-15 14:16 Stop Time: 2023-12-16 14:16

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 7852
| Syslog                   | 12
| SecurityAlert            | 0
| SecurityIncident         | 0
| AzureNetworkAnalytics_CL | 0

The table below illustrates the reduction in attacks following the implementation of a secure environment:

| Metric                                         | Reduction in Attacks |
| ---------------------------------------------- | -------------------- |
| Security Events (Windows VMs)                  | -63.36%              |
| Syslog (Linux VMs)                             | -99.13%              |
| SecurityAlert (Microsoft Defender for Cloud)   | -100.00%             |
| Security Incident (Sentinel Incidents)         | -100.00%             |
| NSG Inbound Malicious Flows Allowed            | -100.00%             |


## Conclusion: Demonstrating the Efficacy of Azure Security Measures

This project successfully established a honeynet within Azure, utilizing Microsoft Sentinel for incident management and alert generation. The stark contrast in security metrics before and after the implementation of security controls underscored the effectiveness of these measures. It is, however, important to consider that in a network with regular user activity, different outcomes in terms of security events and alerts might emerge, even with stringent security controls in place.

