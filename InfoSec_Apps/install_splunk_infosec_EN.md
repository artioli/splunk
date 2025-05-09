# Splunk InfoSec Installation Guide

This document provides a comprehensive, step-by-step guide for installing **Splunk InfoSec**, based on best practices and official Splunk recommendations. It aims to help security analysts and architects deploy a powerful and scalable InfoSec solution efficiently.

---

## Table of Contents

- [Overview of Splunk InfoSec](#overview-of-splunk-infosec)
  - [Key Features](#key-features)
  - [Benefits](#benefits)
- [Who Should Deploy Splunk InfoSec](#who-should-deploy-splunk-infosec)
- [Prerequisite Apps](#prerequisite-apps)
- [System Requirements and Prerequisites](#system-requirements-and-prerequisites)
- [Installing Splunk Single Server Deployment (S1)](#installing-splunk-single-server-deployment-s1)
- [Downloading Splunk Enterprise](#downloading-splunk-enterprise)
- [Next Steps](#next-steps)

---

## Overview of Splunk InfoSec

Splunk InfoSec is a cutting-edge security solution that leverages Splunk's data analytics capabilities to provide comprehensive security insights and real-time threat detection. It is essential for organizations seeking to strengthen their cybersecurity posture in today’s dynamic threat landscape.

### Key Features

- **Real-time Monitoring and Analytics**: Continuous monitoring of data streams for real-time threat detection and response.
- **Advanced Threat Detection**: Integration with Splunk Machine Learning Toolkit (MLTK) for ML-based threat correlation and alerts.
- **Incident Investigation and Forensics**: Tools for detailed investigation and forensics.
- **Compliance and Reporting**: Assists in regulatory compliance with extensive reporting tools.

### Benefits

- **Enhanced Security Posture**: Proactive threat identification using advanced analytics.
- **Streamlined Operations**: Centralized management of security operations.
- **Scalability and Flexibility**: Suitable for organizations of all sizes.
- **Rapid Threat Detection and Response**: Minimize damage through fast action.
- **Operational Intelligence**: Gain strategic insights and optimize security processes.

---

## Who Should Deploy Splunk InfoSec

Splunk InfoSec is designed to align **people, processes, and tools**, offering:

- **Efficiency for Limited Resources**: Ideal for small security teams.
- **Skill Enhancement**: Simplifies complex tasks through intuitive interfaces.
- **One-Stop Security Platform**: Centralizes threat detection, response, and reporting.
- **Integration and Customization**: Seamlessly integrates with existing infrastructure.
- **Incident Response Playbooks**: Aids in creating and refining IR playbooks.
- **Automated Workflows**: Ensures repeatable, documented incident handling.

---

## Prerequisite Apps

Before deploying Splunk InfoSec, install the following prerequisite apps:

| App | Purpose | Benefit | Link |
|:----|:--------|:--------|:-----|
| Splunk Common Information Model (CIM) | Normalizes and categorizes data | Actionable and consistent data across sources | [Splunkbase](https://splunkbase.splunk.com/app/1621) |
| Punchcard - Custom Visualization | Temporal pattern visualization | Identify trends/anomalies easily | [Splunkbase](https://splunkbase.splunk.com/app/3129) |
| Force Directed App for Splunk | Relationship graph visualization | Uncover hidden patterns in networks | [Splunkbase](https://splunkbase.splunk.com/app/3767) |
| Splunk App for Lookup File Editing | Edit lookup files | Improve accuracy and efficiency in data handling | [Splunkbase](https://splunkbase.splunk.com/app/1724) |
| Splunk Sankey Diagram - Custom Visualization | Flow and interaction visualization | Understand data movement and relationships | [Splunkbase](https://splunkbase.splunk.com/app/3112) |
| Splunk Security Essentials (SSE) | Use case examples and insights | Accelerate security deployment | [Splunkbase](https://splunkbase.splunk.com/app/3435) |
| Alert Manager Add-on | Enhance alert management | Improve alert triage and incident response | [Splunkbase](https://splunkbase.splunk.com/app/3365) |
| Alert Manager | Extend alert framework | Comprehensive alert lifecycle management | [Splunkbase](https://splunkbase.splunk.com/app/2665) |

---

## System Requirements and Prerequisites

### Linux Kernel Compatibility

- **General**: Most modern Linux distributions supported.
- **Recommended**: Follow [Splunk OS Requirements](https://docs.splunk.com/Documentation/Splunk/latest/Installation/Systemrequirements#Supported_Operating_Systems).
- **Custom Kernel**: May require additional configuration.

### Minimum Hardware Requirements

| Resource | Minimum Requirements |
|:---------|:----------------------|
| Processor | Quad-core CPU (x64) |
| Memory | 16 GB RAM |
| Storage | 500 GB disk space (SSD recommended) |
| Network | 1 Gbps internal network |

### Required Software Dependencies

- **Operating System**: Updated Linux (Ubuntu, CentOS, RHEL).
- **Java Runtime Environment**: JRE 8 or later (for specific functionalities).
- **Splunk Enterprise**: Latest version compatible with Splunk InfoSec.

> **Note**: Open necessary ports following Splunk's guidelines and best practices.

### Additional Recommendations

- Scale hardware for larger deployments.
- Implement firewall and IDS.
- Maintain regular backups of Splunk data.

---

## Installing Splunk Single Server Deployment (S1)

### What is a Single Server Deployment (S1)?

A cost-effective, simple Splunk deployment suitable when:

- No high availability or automatic disaster recovery is needed.
- Daily ingestion is below ~300GB/day.
- User base is small and non-critical.

**Use cases**: DevOps, test environments, departmental monitoring.

> Refer to official documentation: [Splunk Validated Architectures PDF](https://www.splunk.com/en_us/pdfs/tech-brief/splunk-validated-architectures.pdf)

### System and Software Requirements

Follow [System Requirements](#system-requirements-and-prerequisites) above.

Ensure installation of:

- Linux OS
- Java Runtime (if required)
- Splunk Enterprise

---

## Downloading Splunk Enterprise

1. Go to [www.splunk.com](https://www.splunk.com).
2. Navigate to **Free Trials** > **Splunk Enterprise**.
3. Sign in or create a Splunk account.
4. Download the version compatible with your OS (Linux 64-bit recommended).
5. Accept the software license agreement if prompted.

---

## Next Steps

After completing the initial installation:

- Install and configure the prerequisite apps listed in [Prerequisite Apps](#prerequisite-apps).
- Configure data ingestion:
  - Integrate data sources such as authentication logs, endpoint telemetry, firewall logs, and network traffic.
- Verify CIM Compliance:
  - Use the Splunk Common Information Model (CIM) app to validate field normalization.
- Deploy Key Use Cases:
  - Utilize Splunk Security Essentials to activate ready-to-use detections.
- Customize Incident Response:
  - Configure alerting and integrate Alert Manager for enhanced triage and workflows.
- Monitor and Tune:
  - Continuously tune correlation searches and dashboards for better detection and performance.

> **Tip**: Regularly update apps and Splunkbase integrations to leverage the latest security improvements and use cases.

---

## Boss of the SOC (BOTS) Dataset Version 3
A sample security dataset and CTF platform for information security professionals, researchers, students, and enthusiasts.

### Download

| Dataset          | Description | Size | Format | MD5 |
| ---------------- | ----------- | ---- | ------ | --- |
| [BOTS V3 Dataset](https://botsdataset.s3.amazonaws.com/botsv3/botsv3_data_set.tgz) |  BOTSv3 dataset. | 320.1MB | Pre-indexed Splunk | d7ccca99a01cff070dff3c139cdc10eb |


### Installation
1. Download the dataset file indicated above and check the MD5 hash to ensure integrity.
2. Install Splunk Enterprise and the apps/add-ons listed in the *Required Software* section below. It is important to match the specific version of each app and add-on.
3. Unzip/untar the downloaded file into $SPLUNK_HOME/etc/apps
4. Restart Splunk
5. The BOTS v3 data will be available by searching:
```
index=botsv3 earliest=0
```
6. Note that because the data is distributed in a pre-indexed format, there are no volume-based licensing limits to be concerned with.


### Required Apps
The dataset requires the following software which is distributed and licensed separately
and should be installed before using the dataset. The versions listed are
those that were used to create the dataset. Different versions of the software
may or may not work properly. If you are new to Splunk, follow [these instructions](http://docs.splunk.com/Documentation/Splunk/latest/Installation/Whatsinthismanual) to install the free Splunk Enterprise trial and [these instructions](https://docs.splunk.com/Documentation/AddOns/released/Overview/Singleserverinstall) to install apps and add-ons.


|	App / Add-on	|	Link |
| ----------- | -------- |
|	Aws_guardduty	                                  |	[Splunkbase](https://splunkbase.splunk.com/app/3790/) |
|	Cisco Endpoint Security Analytics (former CiscoNVM) |	[Splunkbase](https://splunkbase.splunk.com/app/2992/) |
|	Code42 App For Splunk	                          |	[Splunkbase](https://splunkbase.splunk.com/app/3736/) |
|	Code42ForSplunk Technology Add-On	              |	[Splunkbase](https://splunkbase.splunk.com/app/3746/) |
|	DecryptCommands	                                |	[Splunkbase](https://splunkbase.splunk.com/app/2655/) |
|	ES Content Updates	                            |	[Splunkbase](https://splunkbase.splunk.com/app/3449/) |
|	Microsoft Azure Active Directory Reporting Add-on for Splunk	|	[Splunkbase](https://splunkbase.splunk.com/app/3757/) |
|	Microsoft Cloud App for Splunk	                |	[Splunkbase](https://splunkbase.splunk.com/app/3786/) |
|	Microsoft Office 365 Reporting Add-on for Splunk  |	[Splunkbase](https://splunkbase.splunk.com/app/3720/) |
|	Microsoft Sysmon Add-on	                        |	[Splunkbase](https://splunkbase.splunk.com/app/1914/) |
|	OSquery App for Splunk	                        |	[Splunkbase](https://splunkbase.splunk.com/app/3902/) |
|	Splunk Add-on for Cisco ASA	                    |	[Splunkbase](https://splunkbase.splunk.com/app/1620/) |
|	Splunk Add-on for Microsoft Cloud Services	    |	[Splunkbase](https://splunkbase.splunk.com/app/3110/) |
|	Splunk Add-on for Microsoft Office 365	        |	[Splunkbase](https://splunkbase.splunk.com/app/4055/) |
|	Splunk Add-on for Microsoft Windows	            |	[Splunkbase](https://splunkbase.splunk.com/app/742/) |
|	Splunk Add-on for Symantec Endpoint Protection	|	[Splunkbase](https://splunkbase.splunk.com/app/2772/) |
|	Splunk Add-on for Tenable	                      |	[Splunkbase](https://splunkbase.splunk.com/app/1710/) |
|	Splunk Add-on for Unix and Linux	              |	[Splunkbase](https://splunkbase.splunk.com/app/833/) |
|	Splunk Stream Add-on	                          |	[Splunkbase](https://splunkbase.splunk.com/app/1809/) |
|	Splunk Add-on for AWS	                          |	[Splunkbase](https://splunkbase.splunk.com/app/1876/) |
|	SA-cim_vladiator	                              |	[Splunkbase](https://splunkbase.splunk.com/app/2968/) |
|	URL Toolbox	                                    |	[Splunkbase](https://splunkbase.splunk.com/app/2734/) |
|	TA-VirusTotalActions	                          |	[Splunkbase](https://splunkbase.splunk.com/app/3446/) |
| ----------- | -------- |
|	Splunk Common Information Model **already installed with InfoSec** |	[Splunkbase](https://splunkbase.splunk.com/app/1621/) |
|	Splunk Security Essentials *already installed with InfoSec*  |	[Splunkbase](https://splunkbase.splunk.com/app/3435/) |

---

# End of Guide


