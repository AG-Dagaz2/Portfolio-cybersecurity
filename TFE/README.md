# Final Year Project — TFE

## Title

**Is an open-source SIEM solution such as Wazuh sufficient to ensure attack detection in an Active Directory environment?**

## Overview

This Final Year Project was completed as part of my Bachelor's degree in Cybersecurity at **Hénallux — Département Technique de Namur**.

The project focused on evaluating the capabilities and limitations of **Wazuh** as an open-source SIEM solution for detecting attacks in an **Active Directory environment**.

A dedicated cybersecurity laboratory was deployed using **Proxmox** and **GOAD-Light** to reproduce a small Active Directory infrastructure and perform controlled security experiments.

---

## Objectives

The main objectives of the project were to:

* Deploy and configure Wazuh as a SIEM platform
* Build an Active Directory laboratory environment
* Collect and analyze Windows security events
* Evaluate Wazuh's detection capabilities
* Investigate security alerts
* Evaluate File Integrity Monitoring
* Configure Active Response
* Integrate additional security tools
* Identify the limitations of an open-source SIEM solution

---

## Technologies

### Infrastructure

* Proxmox
* GOAD-Light
* Windows Server
* Windows
* Linux

### Security Monitoring

* Wazuh
* Wazuh Agent
* Wazuh Manager
* Wazuh Indexer
* Wazuh Dashboard
* Sysmon
* Windows Event Logs

### Network & Detection

* Suricata
* YARA
* VirusTotal

### Automation

* Ansible
* Packer
* Terraform

---

## Laboratory

The laboratory was built using Proxmox and GOAD-Light.

The environment provided an Active Directory infrastructure in which different security scenarios could be performed and monitored through Wazuh.

The deployment was automated using infrastructure-as-code and configuration-management tools where appropriate.

This allowed the laboratory to be rebuilt consistently while reducing manual configuration.

---

## Areas Investigated

The project investigated several Wazuh capabilities, including:

* Security event monitoring
* Active Directory monitoring
* Windows Event Logs
* Sysmon telemetry
* File Integrity Monitoring
* Active Response
* Network intrusion detection
* Malware detection
* Threat intelligence enrichment
* Security alert analysis

Additional integrations with **Suricata, YARA and VirusTotal** were explored to determine whether external security technologies could improve the visibility and detection capabilities of the SIEM.

---

## Methodology

The project followed an experimental approach.

Security events and controlled attack scenarios were generated within the laboratory environment and then analyzed through Wazuh.

The general methodology was:

1. Prepare the laboratory environment
2. Deploy and configure Wazuh
3. Configure endpoint monitoring
4. Generate controlled security activity
5. Collect the resulting telemetry
6. Analyze Wazuh alerts
7. Evaluate detection effectiveness
8. Identify limitations
9. Test additional detection mechanisms

The objective was not only to determine whether an event generated an alert, but also to understand the conditions required for successful detection.

---

## Key Findings

The project demonstrated that Wazuh can provide significant security monitoring capabilities in an Active Directory environment, particularly when combined with appropriate endpoint telemetry.

However, the effectiveness of detection depends on several factors, including:

* Quality of collected telemetry
* Endpoint configuration
* Detection rules
* Additional security tools
* Configuration and tuning
* The specific behavior being investigated

The project therefore examined both the strengths and limitations of Wazuh rather than treating the SIEM as a complete security solution by itself.

---

## Skills Demonstrated

This project allowed me to develop practical experience in:

* SIEM deployment
* Security monitoring
* Active Directory security
* Windows security events
* Detection engineering
* Incident investigation
* Network security monitoring
* Malware analysis
* Linux administration
* Virtualization
* Infrastructure automation
* Security tool integration

---

## Full Report

The complete TFE is available below.

**[Download / view the complete TFE](./TFE-Hugo-Delporte.pdf)**

---

## Context

This project was completed during my Bachelor's degree in Cybersecurity in 2026.

The laboratory and experiments documented in this report form the basis for my continued work with Wazuh and security monitoring in my personal cybersecurity laboratory.
