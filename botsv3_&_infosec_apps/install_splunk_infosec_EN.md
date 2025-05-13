# Splunk InfoSec Installation Guide

This document provides a comprehensive, step-by-step guide for installing **Splunk InfoSec**, based on best practices and official Splunk recommendations. It aims to help security analysts and architects deploy a powerful and scalable InfoSec solution efficiently.

---

## Table of Contents

- [Overview of Splunk InfoSec](#overview-of-splunk-infosec)
  - [Key Features](#key-features)
  - [Benefits](#benefits)
- [Who Should Deploy Splunk InfoSec](#who-should-deploy-splunk-infosec)
- [About Boss of the SOC (BOTS) Dataset Version 3](#about-boss-of-the-soc-bots-dataset-version-3)
- [Prerequisite Apps](#prerequisite-apps)
- [System Requirements and Prerequisites](#system-requirements-and-prerequisites)
- [Installing the Splunk InfoSec App & BOTS v3 Dataset](#installing-the-splunk-infosec-app--bots-v3-dataset)
- [End of Guide](#end-of-guide)

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

## About Boss of the SOC (BOTS) Dataset Version 3

A sample security dataset and CTF platform for information security professionals, researchers, students, and enthusiasts.

### About BOTS v3 Prerequisite Apps

The dataset requires the following apps which are distributed and licensed separately and **should be installed before using the dataset**. We are using different app versions from the originally intended use of the dataset and some things may not work properly, but it will work fine for lab purposes. More information about BOTS v3 can be found [here](https://github.com/splunk/botsv3).

---

## Prerequisite Apps

Before deploying Splunk InfoSec, install the following prerequisite apps:

| App | Purpose | Benefit | Link |
|:----|:--------|:--------|:-----|
| **Splunk Common Information Model (CIM)** | Normalizes and categorizes data | Actionable and consistent data across sources | [Splunkbase](https://splunkbase.splunk.com/app/1621) |
| **Punchcard - Custom Visualization** | Temporal pattern visualization | Identify trends/anomalies easily | [Splunkbase](https://splunkbase.splunk.com/app/3129) |
| **Force Directed App for Splunk** | Relationship graph visualization | Uncover hidden patterns in networks | [Splunkbase](https://splunkbase.splunk.com/app/3767) |
| **Splunk App for Lookup File Editing** | Edit lookup files | Improve accuracy and efficiency in data handling | [Splunkbase](https://splunkbase.splunk.com/app/1724) |
| **Splunk Sankey Diagram - Custom Visualization** | Flow and interaction visualization | Understand data movement and relationships | [Splunkbase](https://splunkbase.splunk.com/app/3112) |
| **Splunk Security Essentials (SSE)** | Use case examples and insights | Accelerate security deployment | [Splunkbase](https://splunkbase.splunk.com/app/3435) |
| **Alert Manager Add-on** | Enhance alert management | Improve alert triage and incident response | [Splunkbase](https://splunkbase.splunk.com/app/3365) |
| **Alert Manager** | Extend alert framework | Comprehensive alert lifecycle management | [Splunkbase](https://splunkbase.splunk.com/app/2665) |

Before deploying BOTS v3 dataset, install the following prerequisite apps:

| App / Add-on | Purpose | Benefit | Link |
|:----|:--------|:--------|:-----|
| **Amazon GuardDuty Add-on for Splunk** | Provides knowledge objects for GuardDuty data via Amazon CloudWatch Events. | Enhances threat detection by integrating GuardDuty insights into Splunk. | [Splunkbase](https://splunkbase.splunk.com/app/3790/) |
| **Cisco Endpoint Security Analytics (CESA)** | Analyzes and correlates user and endpoint behavior in Splunk Enterprise. | Provides greater visibility into endpoint behaviors with context such as user, device, and location. | [Splunkbase](https://splunkbase.splunk.com/app/2992/) |
| **Code42 App For Splunk** | Integrates Splunk and Code42 for endpoint and backup data correlation. | Enhances data protection and recovery insights. | [Splunkbase](https://splunkbase.splunk.com/app/3736/) |
| **Code42ForSplunk Technology Add-On** | Provides technical add-on for Code42 App for Splunk. | Facilitates data ingestion and indexing for Code42 data. | [Splunkbase](https://splunkbase.splunk.com/app/3746/) |
| **DecryptCommands** | Provides commands for Base32, Base64, XOR, ROTX, RC4, and ROL/ROR routines. | Useful for deciphering obfuscated malware communications. | [Splunkbase](https://splunkbase.splunk.com/app/2655/) |
| **ES Content Updates** | Delivers pre-packaged Security Content for Splunk Enterprise Security. | Keeps security content up-to-date with the latest threat detection methods. | [Splunkbase](https://splunkbase.splunk.com/app/3449/) |
| **Microsoft Azure Active Directory Reporting Add-on for Splunk** | Collects data from Microsoft Azure including user data, sign-ins, and audits. | Enhances monitoring and compliance reporting for Azure environments. | [Splunkbase](https://splunkbase.splunk.com/app/3757/) |
| **Microsoft Cloud App for Splunk** | Provides dashboards for Microsoft 365 data. | Improves visibility and management of Microsoft 365 services. | [Splunkbase](https://splunkbase.splunk.com/app/3786/) |
| **Microsoft Office 365 Reporting Add-on for Splunk** | Collects message trace data from Microsoft Office 365. | Enhances email security and compliance monitoring. | [Splunkbase](https://splunkbase.splunk.com/app/3720/) |
| **Microsoft Sysmon Add-on** | Provides data input and CIM-compliant field extractions for Microsoft Sysmon. | Enhances process creation and network connection monitoring. | [Splunkbase](https://splunkbase.splunk.com/app/1914/) |
| **OSquery App for Splunk** | Allows remote data collection from osquery clients. | Acts as an osquery management server for enhanced endpoint visibility. | [Splunkbase](https://splunkbase.splunk.com/app/3902/) |
| **Splunk Add-on for Cisco ASA** | Maps Cisco ASA device events to the Splunk CIM. | Facilitates integration with other Splunk apps for comprehensive security monitoring. | [Splunkbase](https://splunkbase.splunk.com/app/1620/) |
| **Splunk Add-on for Microsoft Cloud Services** | Pulls data from various Microsoft cloud services. | Enhances cloud service monitoring and compliance. | [Splunkbase](https://splunkbase.splunk.com/app/3110/) |
| **Splunk Add-on for Microsoft Office 365** | Collects service status and management activity logs from Office 365. | Improves monitoring and compliance for Office 365 environments. | [Splunkbase](https://splunkbase.splunk.com/app/4055/) |
| **Splunk Add-on for Microsoft Windows** | Collects data from Windows systems and normalizes it to the CIM. | Enhances visibility and monitoring of Windows environments. | [Splunkbase](https://splunkbase.splunk.com/app/742/) |
| **Splunk Add-on for Symantec Endpoint Protection** | Collects SEP server and client activity logs. | Improves endpoint security monitoring and threat detection. | [Splunkbase](https://splunkbase.splunk.com/app/2772/) |
| **Splunk Add-on for Tenable** | Collects Tenable vulnerability scan data. | Enhances vulnerability management and compliance reporting. | [Splunkbase](https://splunkbase.splunk.com/app/1710/) |
| **Splunk Add-on for Unix and Linux** | Provides insights into Unix and Linux environments. | Enhances operational visibility and performance monitoring. | [Splunkbase](https://splunkbase.splunk.com/app/833/) |
| **Splunk Stream Add-on** | Captures and analyzes network traffic data. | Enhances network visibility and forensic analysis. | [Splunkbase](https://splunkbase.splunk.com/app/1809/) |
| **Splunk Add-on for AWS** | Collects data from AWS services for integration into Splunk. | Enhances cloud service monitoring and compliance. | [Splunkbase](https://splunkbase.splunk.com/app/1876/) |
| **SA-cim_vladiator** | Validates CIM compliance of technology add-ons. | Simplifies validation process and ensures data model compliance. | [Splunkbase](https://splunkbase.splunk.com/app/2968/) |
| **URL Toolbox** | Provides tools for URL manipulation and analysis. | Enhances security analysis with advanced URL parsing capabilities. | [Splunkbase](https://splunkbase.splunk.com/app/2734/) |
| **TA-VirusTotalActions** | Provides workflow actions for VirusTotal. | Enhances threat intelligence by integrating VirusTotal insights. | [Splunkbase](https://splunkbase.splunk.com/app/3446/) |
| ---- | -------- | -------- | ----- |
| **Splunk Common Information Model** | Normalizes and categorizes data | --**already installed with InfoSec**-- | [Splunkbase](https://splunkbase.splunk.com/app/1621/) |
| **Splunk Security Essentials**  | Use case examples and insights | --**already installed with InfoSec**-- | [Splunkbase](https://splunkbase.splunk.com/app/3435/) |

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

## Installing the Splunk InfoSec App & BOTS v3 Dataset

### Prerequisites

Ensure Splunk Enterprise is installed and running. Verify the installation status:

```
su splunkuser
```
```
/opt/splunk/bin/splunk status
```

If Splunk is not running, start it using:

```
/opt/splunk/bin/splunk start
```

### Step-by-Step Installation

#### Method 1: Install via Splunk Web

1. **Access Splunkbase:**
   - Visit [Splunkbase](https://splunkbase.splunk.com).
   - Search for "Splunk InfoSec App" and download it along with all prerequisite apps.

2. **Upload the App to Splunk:**
   - Log in to your Splunk Web interface.
   - Navigate to **Apps** > **Manage Apps**.
   - Click on **Install app from file**.
   - Select the downloaded app package and click **Upload**.

3. **Verify Installation:**
   - Ensure the apps are listed under **Apps**.

4. **BOTS v3 Installation:**
   - Download the BOTS v3 dataset:
     ```bash
     wget https://botsdataset.s3.amazonaws.com/botsv3/botsv3_data_set.tgz
     ```
   - Unzip/untar the downloaded file into `$SPLUNK_HOME/etc/apps`:
     ```bash
     sudo tar -xvf botsv3_data_set.tgz -C /opt/splunk/etc/apps/
     ```
   - Ensure the correct user has ownership of the directories and files used by Splunk:
     ```bash
     sudo chown -R splunkuser:splunkuser /opt/splunk
     ```

#### Method 2: Install via Command Line

1. **Stop Splunk:**
   ```bash
   /opt/splunk/bin/splunk stop
   ```

2. **Download and Extract Apps:**
   Create a downloads directory:
   ```bash
   sudo mkdir /opt/downloads
   ```
   ```bash
   cd /opt/downloads/
   ```
   Clone the repository or download manually:
   ```bash
   git clone https://github.com/artioli/splunk.git
   ```
   ```bash
   cd /opt/downloads/botsv3_&_infosec_apps/
   ```

3. **Download BOTS v3 Dataset:**
   ```bash
   wget https://botsdataset.s3.amazonaws.com/botsv3/botsv3_data_set.tgz
   ```

4. **Extract Files:**
   ```bash
   for file in *.tgz; do
       tar -xf "$file" -C /opt/splunk/etc/apps/
   done
   ```

5. **Assign Ownership:**
   ```bash
   sudo chown -R splunkuser:splunkuser /opt/splunk
   ```

6. **Start Splunk:**
   ```bash
   /opt/splunk/bin/splunk start
   ```

7. **Verify Data Import:**
   Open Splunk Web and search for the dataset using:
     ```
     index=botsv3 earliest=0
     ```
   - Ensure the data is accessible.
   - > **Note** that this dataset does not count against Splunk's licensing limits due to its pre-indexed nature.

8. **Configuring InfoSec:**

   - All data used by InfoSec app must be Common Information Model (CIM)-compliant. 
   - The following Data Models must be accelerated:
      - Authentication
      - Change
      - Intrusion_Detection
      - Malware
      - Network_Sessions
      - Network_Traffic
      - Endpoint
      - Web

   - Steps
      - On your Splunk platform deployment, in Splunk Web, go to **Settings > Data Models**.
      - Select **Edit > Edit Acceleration** for an accelerated data model that you want to edit.
      - Select **Summary Range > All Time** and click **Save**.
      - > **Note** When accelerating data models to *All Time*, ensure this is only done in a controlled lab environment. In production, consider the impact on performance and storage.

   - Refer to the [Splunk® InfoSec App Docs](https://docs.splunk.com/Documentation/InfoSec) for detailed instructions.

---

## End of Guide
