# Vulnerability Investigation Methodology

## Overview

This document describes the methodology used to investigate vulnerabilities detected by Wazuh in the personal monitoring environment.

The objective is not to treat every vulnerability reported by Wazuh as an automatically confirmed security issue. Instead, selected findings are investigated manually in order to determine their actual relevance to the monitored endpoint.

The methodology combines automated vulnerability detection with local verification, vulnerability analysis, remediation and post-remediation validation.

The overall workflow is:

**Detection → Verification → Assessment → Remediation → Validation**

---

## 1. Vulnerability Detection

The investigation starts with a vulnerability reported by Wazuh Vulnerability Detection.

Wazuh correlates endpoint software inventory information with vulnerability intelligence in order to identify potentially affected software or packages.

At this stage, the finding is considered a **detection**, not yet a confirmed exploitable vulnerability.

The following information is recorded:

* Endpoint affected
* Operating system
* Software or package name
* Installed version
* CVE identifier
* Severity
* Vulnerability description
* Vulnerability status reported by Wazuh

<img width="2551" height="963" alt="image" src="https://github.com/user-attachments/assets/1ab325ff-dce9-49bf-ba22-726e27c436f1" />

The initial vulnerability inventory is also recorded when relevant in order to establish a baseline for later comparison.

---

## 2. Local Verification

The next step is to verify the information reported by Wazuh directly on the affected endpoint.

The purpose is to determine whether the software or package identified by Wazuh is actually installed and to compare the local version with the inventory information.

### Linux

For Debian-based systems, package information can be verified using tools such as:

`dpkg`

`apt`

`apt-cache`

For example:

`dpkg -l | grep -i <package>`

`apt-cache policy <package>`

This allows the installed version and available repository version to be compared.

### Windows

On Windows endpoints, software information can be verified using:

* Installed application information
* Windows registry entries
* Executable metadata
* PowerShell
* File properties

For example, executable metadata can be inspected through PowerShell:

`(Get-Item "C:\Path\to\application.exe").VersionInfo`

Registry information can also be examined when Wazuh obtains software inventory information from Windows registry data.

<img width="635" height="152" alt="Capture d&#39;écran 2026-09-01 193326" src="https://github.com/user-attachments/assets/e5934df7-3ac6-4269-8b45-517ad33968e7" />

The objective is to establish an independent source of truth rather than relying exclusively on the Wazuh inventory.

---

## 3. Usage and Exposure Assessment

Software being installed does not necessarily mean that it is actively used.

When relevant, the investigation therefore determines whether the affected component is actually used by the endpoint or by a workload running on the system.

This can include checking:

* Running processes
* Installed services
* Application configuration
* Dependencies
* Files using the affected library
* Application workloads
* Network exposure
* Relevant registry configuration

For example, a vulnerable library may remain installed as a dependency while not being used by any workload currently running on the endpoint.

This distinction is important because vulnerability management should consider the actual attack surface and exploitation conditions rather than software presence alone.

The result of this phase is an initial exposure assessment.

Possible conclusions include:

* Component actively used
* Component installed but not currently used
* Component required by another application
* Component no longer required
* Configuration condition required for exploitation
* Exposure cannot be determined from the available information

---

## 4. Vulnerability Analysis

The vulnerability itself is then analysed in order to understand the conditions under which exploitation is possible.

The investigation considers:

* CVE identifier
* Affected versions
* Fixed versions
* Vulnerability type
* Attack prerequisites
* Required privileges
* Required user interaction
* Affected component
* Configuration dependencies
* Known mitigations
* Vendor or distribution information

The vulnerability description provided by Wazuh's CTI can be used as an initial source of information.

<img width="1236" height="1283" alt="Capture d&#39;écran 2026-09-01 165339" src="https://github.com/user-attachments/assets/40f8472b-c6fa-4e37-a426-8d5fc1d86598" />

<img width="1432" height="299" alt="Capture d&#39;écran 2026-09-01 171343" src="https://github.com/user-attachments/assets/ab7d95fb-ec7c-4093-b188-dc7e3f3a73e5" />

When necessary, the information is compared against external authoritative sources such as:

* Vendor security advisories
* Operating system security trackers
* CVE databases
* Security advisories from software maintainers

This step is particularly important when the Wazuh finding does not appear to match the observed endpoint state.

---

## 5. Discrepancy Investigation

A vulnerability finding can sometimes contain information that does not directly correspond to the current state of the endpoint.

Examples include:

* Different software versions reported by different inventory mechanisms
* Outdated inventory information
* Incorrect or ambiguous software metadata
* Package versions that have been backported with security fixes
* Vulnerabilities depending on specific configuration conditions
* Vulnerabilities affecting software that is installed but not actually used

When a discrepancy is identified, the investigation does not immediately classify the finding as either a true positive or a false positive.

Instead, each relevant data source is compared.

For example:

**Wazuh inventory**

↓

**Local software inventory**

↓

**Executable metadata**

↓

**Configuration**

↓

**Vulnerability conditions**

↓

**Final assessment**

This approach prevents a vulnerability from being incorrectly dismissed simply because one piece of information appears inconsistent.

---

## 6. Risk and Relevance Assessment

After the technical information has been collected, the finding is assessed in its actual environment.

The assessment considers both the vulnerability itself and the endpoint context.

Relevant factors include:

| Factor              | Question                                            |
| ------------------- | --------------------------------------------------- |
| Software presence   | Is the affected component installed?                |
| Software usage      | Is the component actually used?                     |
| Version             | Is the installed version affected?                  |
| Configuration       | Are the vulnerable conditions present?              |
| Exposure            | Can the vulnerable component be reached or abused?  |
| Privileges          | What privileges are required for exploitation?      |
| Business relevance  | Is the software required on the endpoint?           |
| Remediation options | Can the component be updated, removed or mitigated? |

The Wazuh severity is therefore treated as an important indicator, but not as the sole factor determining the practical risk.

The final assessment may result in different conclusions, such as:

* Vulnerability confirmed and remediation required
* Vulnerability confirmed but exploitation conditions are limited
* Vulnerable software installed but not currently used
* Vulnerable software no longer required
* Finding affected by inventory or version metadata
* Configuration represents an independent security weakness
* Finding requires additional investigation

---

## 7. Remediation Selection

Once the finding has been assessed, an appropriate remediation is selected.

The preferred remediation depends on the actual situation.

Typical options include:

### Software Update

If the vulnerable software is required and a fixed version is available, updating the software is generally the preferred remediation.

For Debian-based systems, this may involve:

`sudo apt update`

followed by:

`sudo apt upgrade`

### Software Removal

If the vulnerable application is no longer required, removing it can be preferable to maintaining unnecessary software.

This reduces the attack surface by eliminating the vulnerable component entirely.

### Configuration Remediation

Some vulnerabilities depend on insecure permissions or configuration.

In these cases, remediation may involve changing the relevant configuration rather than updating the software.

However, configuration changes must be tested for operational impact.

### Mitigation

If immediate remediation is not possible, a compensating control or mitigation may be considered.

The selected remediation should therefore address the actual cause of exposure rather than simply attempting to make the vulnerability scanner report fewer findings.

---

## 8. Controlled Remediation

Remediation actions are performed carefully on the affected endpoint.

Where possible, the original state is first documented so that the effect of the remediation can be evaluated.

This is particularly important when modifying:

* Registry permissions
* Security configuration
* Application configuration
* System services
* Access controls

A remediation that removes a vulnerability but breaks the application cannot automatically be considered successful.

Operational behaviour must therefore be considered alongside the security improvement.

<img width="578" height="231" alt="image" src="https://github.com/user-attachments/assets/b8f7e32b-681a-405b-b0c6-2f0e1ac72c6d" />


---

## 9. Wazuh Inventory Refresh

After remediation, Wazuh must receive updated endpoint information before the vulnerability state can be evaluated.

The endpoint inventory and vulnerability information may not change immediately after a local remediation.

The investigation therefore allows the relevant Wazuh inventory mechanisms to refresh.

The objective is to determine whether the vulnerability finding is removed, changed or remains present.

If the vulnerability remains visible, this does not automatically mean that the remediation failed.

The endpoint state is checked again before drawing a conclusion.

---

## 10. Post-Remediation Validation

The remediation is validated using both local and Wazuh-side evidence.

### Local validation

The endpoint is checked to confirm that the intended security change actually occurred.

Examples include:

* Installed package version
* Installed application version
* Application presence
* Registry permissions
* Configuration state
* Running services
* Process state

### Wazuh validation

The corresponding vulnerability finding is then checked in Wazuh.

Possible outcomes include:

* Vulnerability removed
* Vulnerability remains
* Vulnerability status changed
* Vulnerability still reported despite the endpoint being remediated
* New information requires additional investigation

The local and Wazuh results are compared before the case is closed.

---

## 11. Final Classification

Each investigated vulnerability is assigned a final status based on the available evidence.

A case can be classified as:

### Remediated

The vulnerability was confirmed and the remediation successfully removed the affected condition.

### Remediated by Removal

The vulnerable software was no longer required and was removed from the endpoint.

### Not Applicable / Limited Exposure

The vulnerable component is present, but investigation shows that the conditions required for practical exploitation are not currently present or the component is not used by the relevant workload.

This classification should be supported by evidence and should not simply be based on the assumption that unused software is harmless.

### Detection Discrepancy

The Wazuh finding cannot be directly reconciled with the current endpoint state due to inventory, version or metadata discrepancies.

Additional validation may be required before classifying the finding.

### Configuration Weakness

The vulnerability finding may be affected by software inventory information, but an independently identified insecure configuration remains relevant.

In this situation, the software-version question and the configuration-security question should be treated separately.

### Requires Further Investigation

The available evidence is insufficient to reach a reliable conclusion.

---

## 12. Documentation

The final step is to document the complete investigation.

Each case study should contain:

1. Initial Wazuh finding
2. Affected endpoint
3. Vulnerability information
4. Local verification
5. Usage or exposure assessment
6. Discrepancies identified
7. Risk assessment
8. Selected remediation
9. Remediation result
10. Wazuh validation
11. Final conclusion

Screenshots are included where they provide useful evidence for the investigation.

The objective is not to document every command executed during troubleshooting, but to preserve the evidence necessary to understand how the final conclusion was reached.

---

## Investigation Model

The methodology can be summarized as follows:

**1. Detect**

Identify the vulnerability reported by Wazuh.

↓

**2. Verify**

Confirm the software, package and version locally.

↓

**3. Assess**

Determine whether the vulnerability and its exploitation conditions are actually relevant.

↓

**4. Remediate**

Apply the most appropriate corrective action.

↓

**5. Validate**

Verify the change locally and in Wazuh.

↓

**6. Document**

Record the evidence, outcome and lessons learned.

---

## Methodology Principles

The investigation follows several principles.

### Do not blindly trust scanner output

Automated detection provides valuable information, but it does not replace manual validation.

### Do not blindly dismiss scanner output

An unexpected or inconsistent finding should be investigated rather than immediately classified as a false positive.

### Consider the actual endpoint

The practical relevance of a vulnerability depends on software usage, configuration, privileges and exposure.

### Prefer appropriate remediation

Updating software is not always the best solution. Removing unnecessary software or correcting an insecure configuration can sometimes provide a better security outcome.

### Validate remediation

A remediation is only considered successful once the resulting security state has been verified.

### Preserve evidence

Screenshots, version information and configuration data provide evidence supporting the final assessment.

---

## Scope and Limitations

This methodology was developed for a personal Wazuh environment and is intended to demonstrate practical vulnerability management and endpoint investigation.

It is not intended to replace a formal enterprise vulnerability management process.

The investigation is also limited by the information available from the monitored endpoints, Wazuh inventory mechanisms and available vulnerability intelligence.

The methodology can nevertheless be extended to additional Wazuh capabilities and more complex enterprise environments.
