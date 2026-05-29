# Active-Directory-Attack-Detection-Lab

## Overview

This project is a Detection Engineering and Threat Hunting lab focused on
identifying malicious PowerShell activity, authentication failures, and
suspicious behavior within a Windows Active Directory environment using
Sysmon and Wazuh SIEM.

The lab simulates attacker behavior and demonstrates how defensive
telemetry can be collected, correlated, and analyzed using custom
detection rules and endpoint monitoring.

---

## Technologies Used

| Technology                               | Purpose                                 |
| ---------------------------------------- | --------------------------------------- |
| Windows Server 2022                      | Active Directory environment            |
| Active Directory Domain Services (AD DS) | Identity and domain services            |
| Sysmon                                   | Endpoint telemetry collection           |
| Wazuh SIEM                               | Log analysis and alert correlation      |
| PowerShell                               | Attack simulation                       |
| Windows Event Viewer                     | Log monitoring and investigation        |
| Kali Linux                               | Wazuh management and rule customization |

---

## Lab Architecture

```text
Attacker Activity
(PowerShell / Authentication Abuse)
                │
                ▼
Windows Server 2022 (DC01)
                │
                ▼
Sysmon
(Process Creation & Security Telemetry)
                │
                ▼
Wazuh Agent
                │
                ▼
Wazuh Manager
(Custom Detection Rules)
                │
                ▼
Wazuh Threat Hunting Dashboard
```

---

## Detection Scenarios

This project covers detection and monitoring for:

* Encoded PowerShell execution
* Suspicious PowerShell process creation
* Authentication failures (Event ID 4625)
* PowerShell-based enumeration activity
* Sysmon Event ID 1 monitoring
* Custom Wazuh detection rules
* Threat hunting and alert correlation

---

## Incident Response Workflow

This lab incorporates a simulated incident response process focused on
validating, investigating, and analyzing security alerts generated from
malicious PowerShell activity and authentication abuse within an Active
Directory environment.

The workflow demonstrates how a SOC analyst or incident responder would
handle alerts after detection and perform structured investigation and
response activities.

---

### Detection

Suspicious activity was identified through telemetry collected by Sysmon,
Windows Security Logs, and Wazuh SIEM.

Detection sources included:

* Sysmon Event ID 1 process creation monitoring
* PowerShell command-line visibility
* Custom Wazuh detection rules
* Failed authentication monitoring (Event ID 4625)
* Threat hunting dashboard alerts

Alerts were generated when activity matched predefined detection logic
designed to identify potentially malicious behavior.

---

### Triage

Initial alert validation was performed to determine whether the detected
activity represented legitimate administrative behavior or a potential
security threat.

Triage activities included:

* Reviewing Wazuh alert details
* Examining PowerShell command-line arguments
* Identifying affected systems
* Identifying affected user accounts
* Determining alert severity
* Assessing potential business impact

---

### Investigation

A detailed investigation was conducted to determine the scope and nature
of the detected activity.

Investigation activities included:

* Reviewing Sysmon Event ID 1 telemetry
* Examining parent-child process relationships
* Investigating PowerShell execution activity
* Correlating related Wazuh alerts
* Reviewing authentication failure events
* Analyzing account enumeration activity
* Mapping observed behavior to MITRE ATT&CK techniques

The collected telemetry provided visibility into attacker actions and
allowed suspicious behavior to be reconstructed from available logs.

---

### Containment (Simulated)

Because this project was performed within a controlled lab environment,
containment actions were simulated rather than executed.

Recommended containment actions included:

* Isolating affected hosts
* Disabling compromised accounts
* Terminating malicious PowerShell processes
* Blocking suspicious network activity
* Restricting unauthorized access attempts

---

### Eradication (Simulated)

Following containment, eradication activities were simulated to remove
potential malicious artifacts from the environment.

Recommended eradication actions included:

* Removing malicious scripts
* Deleting unauthorized scheduled tasks
* Eliminating persistence mechanisms
* Resetting compromised credentials
* Verifying system integrity

---

### Recovery (Simulated)

Recovery activities focused on restoring systems to normal operation
while ensuring no malicious activity remained.

Recommended recovery activities included:

* Re-enabling validated user accounts
* Returning isolated systems to service
* Monitoring for recurring activity
* Verifying security controls
* Validating logging functionality

---

### Lessons Learned

This exercise demonstrated the effectiveness of combining Sysmon
telemetry, Windows event logs, and Wazuh SIEM correlation for detecting
and investigating suspicious activity within an Active Directory
environment.

Key lessons learned included:

* Detection engineering principles
* Alert triage and validation
* Threat hunting methodologies
* Security event correlation
* Incident investigation workflows
* MITRE ATT&CK-based analysis
* Incident response lifecycle procedures

---

## Project Structure

```text
Active-Directory-Attack-Detection-Lab/
│
├── active-directory/
├── attack-simulation/
├── authentication-failures/
├── environment-setup/
├── incident-response/
├── sysmon-detection/
├── wazuh-alert-correlation/
└── wazuh-custom-rules/
```

---

## Key Screenshots

### Environment Setup

* Windows Server 2022 Domain Controller configuration
* Active Directory Organizational Units
* User and security group configuration

### Attack Simulation

* Encoded PowerShell command execution
* PowerShell enumeration activity
* Scheduled task persistence simulation

### Sysmon Detection

* Sysmon Event ID 1 process creation telemetry
* PowerShell command-line visibility
* Process correlation details

### Wazuh Detection

* Custom Wazuh rule creation
* Wazuh manager service restart
* Threat hunting dashboard detections

### Authentication Monitoring

* Windows Security Event ID 4625 failed logons
* Authentication abuse detection

---

## MITRE ATT&CK Mapping

| Technique                         | ATT&CK ID |
| --------------------------------- | --------- |
| PowerShell                        | T1059.001 |
| Command and Scripting Interpreter | T1059     |
| Account Discovery                 | T1087     |
| Valid Accounts                    | T1078     |
| Brute Force                       | T1110     |
| System Owner/User Discovery       | T1033     |
| Defense Evasion                   | T1218     |

---

## Example Wazuh Detection Rule

```xml
<rule id="100200" level="12">
  <if_group>sysmon_event1</if_group>

  <field name="win.eventdata.commandLine">-enc</field>

  <description>
    Encoded PowerShell Command Detected
  </description>

  <mitre>
    <id>T1059.001</id>
  </mitre>
</rule>
```

---

## Learning Objectives

This project helped reinforce:

* Detection engineering concepts
* Threat hunting workflows
* Sysmon telemetry analysis
* Wazuh rule development
* Windows event log analysis
* Active Directory administration
* Blue team monitoring strategies
* Incident response lifecycle execution
* Alert triage and validation
* Security event investigation and correlation

---

## Future Improvements

Planned improvements include:

* Sigma rule integration
* PowerShell logging enhancement
* Additional ATT&CK technique coverage
* Splunk integration
* Automated alert enrichment
* Sysmon configuration tuning

---

## Author

**Daniel Nwachukwu**

GitHub:

https://github.com/Danielnwachukwu

---

## Disclaimer

This project was created strictly for educational and defensive
cybersecurity purposes within a controlled lab environment.
