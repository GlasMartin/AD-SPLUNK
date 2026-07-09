# AD-SPLUNK

A hands-on cybersecurity laboratory project focused on deploying, configuring, and testing a Splunk SIEM environment integrated with Active Directory using VirtualBox.

## Project Overview

The objective of this project was to gain practical experience with Security Information and Event Management (SIEM) technologies by deploying a centralized Splunk monitoring environment, collecting Windows security telemetry, and validating detection capabilities through simulated attacks.

The laboratory environment was built around Active Directory authentication, endpoint monitoring, and attack simulation.

The lab consists of:

- Ubuntu Server running Splunk Enterprise
- Windows Server 2022 running Active Directory Domain Services, Sysmon, and Splunk Universal Forwarder
- Windows 11 employee workstation joined to the domain running Sysmon and Splunk Universal Forwarder
- Kali Linux used for attack simulation

## Architecture

The laboratory network architecture is shown below:

![Architecture](IP.png)

## Environment

| Machine | Operating System | Purpose |
|----------|----------------|----------|
| Splunk Server | Ubuntu Server | Splunk Enterprise SIEM Platform |
| Domain Controller | Windows Server 2022 | Active Directory Domain Services, Sysmon, Splunk Universal Forwarder |
| Employee Endpoint | Windows 11 | Domain Client, Sysmon, Splunk Universal Forwarder |
| Attacker | Kali Linux | Attack Simulation |

**Virtualization Platform:** Oracle VirtualBox

## Installation

### Splunk Server

Splunk Enterprise was installed on Ubuntu Server and configured as the centralized SIEM platform.

The server was responsible for:

- Receiving endpoint logs
- Searching security events
- Creating detection queries
- Monitoring authentication activity
- Investigating suspicious behavior

### Windows Endpoint Monitoring

Windows systems were configured with:

- Splunk Universal Forwarder
- Sysmon
- Windows Event Log Collection

Sysmon provided detailed endpoint telemetry including:

- Process creation events
- Network connections
- System activity
- Security-related events

The collected telemetry was forwarded to Splunk for analysis.

### Active Directory Deployment

Windows Server 2022 was configured as an Active Directory Domain Controller.

The Windows 11 workstation was joined to the domain to simulate a realistic enterprise environment.

Active Directory allowed monitoring of:

- Domain authentication events
- User activity
- Failed login attempts
- Successful logins
- Endpoint security events

## Detection Engineering

### RDP Brute Force Detection

A simulated RDP brute-force attack was performed from Kali Linux against the Windows 11 employee workstation.

The attack was used to validate Splunk's ability to detect suspicious authentication activity.

Splunk was used to analyze:

- Failed authentication attempts
- Source IP addresses
- Target usernames
- Windows Security Event Logs

Relevant Windows Event IDs:
4625 - Failed Logon


The objective was to identify suspicious authentication patterns and detect possible unauthorized access attempts.

### Sysmon Event Monitoring

Sysmon telemetry was collected through Splunk Universal Forwarders.

Monitored activity included:

- Process execution
- Network connections
- Endpoint behavior
- System activity

This provided additional visibility into endpoint activity beyond standard Windows logs.

## Testing

### RDP Brute Force Simulation

A brute-force attack was simulated from Kali Linux against the Windows 11 employee endpoint.

Expected outcome:

- Multiple failed login events generated
- Windows Security logs forwarded to Splunk
- Suspicious authentication activity identified
- Attack source visible through Splunk searches

### Active Directory Authentication Testing

Domain authentication was tested by:

- Logging in with domain users
- Generating failed login attempts
- Monitoring authentication events inside Splunk

Expected outcome:

- Authentication events collected successfully
- User activity visible in Splunk
- Security events available for investigation

## Results

### Splunk Log Collection

Splunk successfully collected security telemetry from Windows endpoints through Universal Forwarders.

Collected data included:

- Windows Security Events
- Sysmon Events
- Authentication logs
- Endpoint activity

### RDP Attack Detection

The simulated brute-force attack generated detectable authentication events.

The activity was identified through analysis of:

- Failed login attempts
- Source IP information
- Targeted usernames
- Authentication patterns

This demonstrated how SIEM solutions can be used to investigate suspicious activity and improve security visibility.

## Skills Demonstrated

- Splunk Administration
- SIEM Deployment
- Splunk Universal Forwarder Configuration
- Active Directory Administration
- Windows Security Monitoring
- Sysmon Configuration
- Detection Engineering
- Authentication Log Analysis
- RDP Attack Detection
- Security Event Investigation
- Linux Administration
- VirtualBox Lab Development
- Attack Simulation

## Lessons Learned

This project provided practical experience in building a small enterprise-style security monitoring environment.

The most valuable learning areas were understanding how endpoint telemetry is collected, how Windows authentication events can be analyzed, and how SIEM queries can be used to identify suspicious behavior.

Building the Active Directory environment and connecting multiple endpoints demonstrated how centralized logging improves visibility across an organization.

The project also improved understanding of how attackers generate detectable activity and how defenders can investigate those events using SIEM technologies.

## Future Improvements

Potential enhancements include:

- Splunk Enterprise Security deployment
- MITRE ATT&CK technique mapping
- Custom Splunk detection rules
- Sigma rule integration
- PowerShell attack detection
- Malware execution monitoring
- Additional domain endpoints
- Threat intelligence integration
- Automated alerting and response workflows
- Dashboard customization

## Screenshots

- ![Architecture](Infra2.png)
- ![Splunk Alerts](Alerts.png)
- ![Splunk Logs](logproof.png)
- ![Splunk Dashboard](dash.png)

## Author

**Martin Glas**

Cybersecurity Laboratory Project (2026)
