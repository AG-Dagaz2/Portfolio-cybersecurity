# Personal Wazuh

This project documents the use of a personal Wazuh deployment to monitor endpoints and investigate security findings beyond the scope of the SIEM deployment documented in the TFE.

The objective is not only to collect vulnerabilities reported by Wazuh, but to manually validate selected findings on the affected endpoints, assess their relevance, and document the remediation process.

## Environment

The Wazuh environment is hosted on an Ubuntu virtual machine and is used to monitor several endpoints within my personal environment.

The project is intended to explore different Wazuh capabilities through practical use cases.

The first part of this project focuses on:

- Vulnerability Detection
- Endpoint inventory
- Manual vulnerability validation
- Security configuration verification
- Remediation
- Post-remediation validation

## Vulnerability Detection

Wazuh Vulnerability Detection was used to identify known vulnerabilities affecting software installed on the monitored endpoints.

The initial vulnerability inventory contained:

| Severity | Count |
| --- | ---: |
| Critical | 25 |
| High | 180 |
| Medium | 182 |
| Low | 20 |
| Pending | 151 |
| **Total** | **558** |

<img width="1905" height="771" alt="Capture d&#39;écran 2026-09-01 175101" src="https://github.com/user-attachments/assets/71e896ec-823f-410c-b0bf-5fa80e1e3600" />


This initial state provides a baseline for evaluating the effect of remediation actions.

A significant number of vulnerabilities were detected on the Raspberry Pi, including vulnerabilities published recently in 2026.

This highlights the importance of regularly updating systems and monitoring newly disclosed vulnerabilities.

However, the number of vulnerabilities reported by a vulnerability management tool should not automatically be interpreted as the number of exploitable vulnerabilities present on an endpoint.

The findings therefore require investigation to determine their actual relevance.

## Investigation Approach

A vulnerability reported by Wazuh is not automatically considered proof that the endpoint is currently exposed.

Selected findings are investigated manually in order to determine whether the vulnerability is relevant to the actual state of the endpoint.

The investigation follows these steps:

1. Identify the vulnerability in Wazuh.
2. Record the affected endpoint, software or package, version and severity.
3. Verify the software or package locally.
4. Determine whether the affected component is actually used when relevant.
5. Compare the local state with the vulnerability information.
6. Investigate any discrepancies between Wazuh and the endpoint.
7. Assess the practical relevance of the finding.
8. Select an appropriate remediation.
9. Apply the remediation.
10. Allow Wazuh to refresh its vulnerability information.
11. Verify the result locally and in Wazuh.
12. Document the final result.

This approach makes it possible to distinguish between an automated vulnerability finding and a manually validated security issue.

It also demonstrates that vulnerability management is not limited to applying updates. Understanding the affected software, its usage and the conditions required for exploitation is an important part of the investigation.

## Selected Case Studies

Three vulnerabilities were selected for detailed investigation.

The cases were deliberately chosen with different severities and different investigation scenarios:

- A **Critical** vulnerability on the Raspberry Pi involving a Linux package.
- A **High** vulnerability on a Windows endpoint involving FortiClient.
- A **Medium** vulnerability on a Windows endpoint involving Steam, where the Wazuh inventory and the actual executable version differ.

This provides several different perspectives on vulnerability management.

### Raspberry Pi - CVE-2026-15043

A Critical vulnerability affecting `libdi-perl` was selected for investigation on the Raspberry Pi.

The package was confirmed to be installed at version `1.643`.

A local investigation also confirmed that the package was not being used by the workload examined on the system.

<img width="1261" height="1288" alt="Capture d&#39;écran 2026-09-01 164737" src="https://github.com/user-attachments/assets/aca38db4-00c9-4b38-a211-c28014182a34" />

<img width="1468" height="494" alt="Capture d&#39;écran 2026-09-01 164812" src="https://github.com/user-attachments/assets/cd527a64-4f57-4868-8763-2c14c093c114" />

<img width="666" height="574" alt="Capture d&#39;écran 2026-09-01 164831" src="https://github.com/user-attachments/assets/40dccb8c-75e8-4dba-af21-33f3f2d574fa" />

<img width="717" height="34" alt="Capture d&#39;écran 2026-09-01 165003" src="https://github.com/user-attachments/assets/bd8fc0c8-0290-45cb-8ffd-36a7dce5423c" />


The Raspberry Pi was subsequently updated using `sudo apt update && sudo apt upgrade`.

The objective was to bring installed packages to their available patched versions.

The effect of this remediation on the Wazuh vulnerability inventory will be validated after the vulnerability information has been refreshed.

See [CVE-2026-15043](./vulnerability-detection/raspberry-pi/CVE-2026-15043.md).

### Father's PC - CVE-2021-41031

A High severity vulnerability affecting FortiClient was selected for investigation on another Windows endpoint.

The installed FortiClient version was verified as `6.4.3.1608`.

<img width="1236" height="1283" alt="Capture d&#39;écran 2026-09-01 165339" src="https://github.com/user-attachments/assets/9eaefeaf-e842-42f0-bb1d-1b8265fb7d54" />

<img width="1432" height="299" alt="Capture d&#39;écran 2026-09-01 171343" src="https://github.com/user-attachments/assets/a6b731dd-a5cd-4cac-ada9-bffb4543bd2d" />

<img width="474" height="679" alt="Capture d’écran 2026-09-01 170952" src="https://github.com/user-attachments/assets/1deacc76-7785-4589-b924-9e44d1901495" />


FortiClient is no longer required on this endpoint.

Instead of upgrading software that is no longer needed, the selected remediation is therefore to uninstall FortiClient entirely.

Removing unnecessary software also reduces the attack surface of the endpoint by eliminating the vulnerable component rather than continuing to maintain it.

The remediation and subsequent Wazuh validation will be documented after the uninstall has been performed.

See [CVE-2021-41031](./vulnerability-detection/fathers-pc/CVE-2021-41031.md).

### Personal PC - CVE-2019-14743

A Medium severity vulnerability affecting the Steam Client was selected for investigation on my main Windows PC.

This case is more complex than the previous two because the investigation revealed a discrepancy between the version reported by Wazuh and the version information exposed by the current Steam executable.

Wazuh reports:

`package.version = 2.10.91.91`

This value corresponds to the `DisplayVersion` stored in the Windows uninstall registry.

The installed Steam entry was independently verified:

`DisplayName = Steam`

`DisplayVersion = 2.10.91.91`

`Publisher = Valve Corporation`

<img width="1245" height="1291" alt="Capture d&#39;écran 2026-09-01 171714" src="https://github.com/user-attachments/assets/505d05e1-3230-4c86-a958-6a3c5370a8d6" />

<img width="1429" height="300" alt="Capture d&#39;écran 2026-09-01 171730" src="https://github.com/user-attachments/assets/42e1f677-a608-435c-be9f-214f3d5f9fee" />

<img width="988" height="262" alt="Capture d&#39;écran 2026-09-01 190125" src="https://github.com/user-attachments/assets/ef5010e9-5630-4b84-acef-7daf7d5e0e5a" />


However, the current `steam.exe` reports:

`ProductVersion = 01.00.00.02`

`FileVersion = 10.87.82.64`

<img width="635" height="152" alt="image" src="https://github.com/user-attachments/assets/5660142c-62ad-4536-9b96-aefd2d10f685" />

The investigation therefore revealed that the software inventory version used by Wazuh does not directly correspond to the current executable `FileVersion`.

The registry configuration associated with the historical vulnerability was also investigated.

The following explicit permission was found on the Steam registry key:

`IdentityReference : BUILTIN\Utilisateurs`

`RegistryRights : FullControl`

`AccessControlType : Allow`

`IsInherited : False`

`InheritanceFlags : None`

`PropagationFlags : None`

<img width="1074" height="486" alt="Capture d&#39;écran 2026-09-01 190802" src="https://github.com/user-attachments/assets/b9934c1c-3d15-4301-a5de-00bcbfac49f7" />


This means that `BUILTIN\Utilisateurs` has an explicit `FullControl` permission directly on the Steam registry key.

The case is therefore being investigated further rather than immediately being classified as either a true positive or a false positive.

The investigation must distinguish between two separate questions:

1. Is `CVE-2019-14743` still applicable to the current Steam client?
2. Does the current registry configuration represent an unnecessary security weakness that should be remediated independently?

See [CVE-2019-14743](./vulnerability-detection/personal-pc/CVE-2019-14743.md).

## Initial Results

The three investigations demonstrate different situations that can occur during vulnerability management.

| Case | Severity | Initial finding |
| --- | --- | --- |
| CVE-2026-15043 | Critical | Vulnerable package confirmed installed but not used |
| CVE-2021-41031 | High | Vulnerable application confirmed installed and no longer required |
| CVE-2019-14743 | Medium | Wazuh finding requires additional validation due to version metadata discrepancy |

These cases show why automated vulnerability detection should be followed by manual investigation.

A vulnerability scanner can identify a potentially vulnerable component, but additional context is required to determine whether the component is actually relevant, used, exploitable, or in need of remediation.

## Remediation and Validation

The remediation phase will be documented separately for each case.

The general process is:

**Detection**

↓

**Local verification**

↓

**Vulnerability assessment**

↓

**Remediation**

↓

**Wazuh inventory refresh**

↓

**Post-remediation validation**


After remediation, the vulnerability inventory will be compared with the initial state to determine whether the expected findings have disappeared.

Where appropriate, local verification will also be performed to confirm that the affected package or application has actually been updated or removed.

## Current Status

| Case | Investigation | Remediation | Validation |
| --- | --- | --- | --- |
| CVE-2026-15043 | Complete | `apt update && apt upgrade` performed | Pending Wazuh refresh |
| CVE-2021-41031 | Complete | FortiClient removal planned | Pending |
| CVE-2019-14743 | In progress | Not decided | Pending |

## Lessons Learned

The investigations demonstrate several important aspects of vulnerability management:

- A vulnerability finding should be independently validated.
- Software presence does not necessarily mean that the affected component is actively used.
- Removing unnecessary software can be a more appropriate remediation than upgrading it.
- Software inventory metadata may not always accurately represent the current executable version.
- Vulnerabilities can depend on configuration as well as software version.
- Post-remediation validation is necessary to confirm that the security state has actually changed.
- Vulnerability management is therefore an iterative process rather than a simple update operation.

## Scope

This project is separate from the TFE and is intended to demonstrate the practical use of Wazuh in a personal environment.

Vulnerability Detection is the first capability explored in this project.

Additional Wazuh capabilities and use cases will be added over time.
