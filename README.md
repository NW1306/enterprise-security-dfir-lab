# Enterprise Security & DFIR Lab
### Northstar Technologies

**Enterprise Security | Security Operations | Digital Forensics & Incident Response**

---

## 1. Project Overview

The **Northstar Technologies Enterprise Security & DFIR Lab** is a simulated enterprise environment built using Oracle VirtualBox. It is designed to explore the practical implementation of enterprise cybersecurity infrastructure, security controls, security monitoring, incident response and digital forensics.

The project simulates the IT environment of a fictional organisation, Northstar Technologies. It involves building an enterprise network, deploying Windows-based infrastructure, configuring centralized identity management, implementing endpoint security controls, and progressively developing security monitoring and DFIR capabilities.

The lab incorporates established cybersecurity frameworks and standards to guide security implementation, risk assessment and evaluation:

- Australian Essential Eight
- NIST Cybersecurity Framework (CSF) 2.0
- CIS Critical Security Controls v8.1
- ISO/IEC 27001:2022

The project also includes a planned AI-assisted security operations component, which will be developed after the foundational enterprise infrastructure, security monitoring and DFIR workflows have been established and verified.

**Environment:** Simulated enterprise network — Northstar Technologies  
**Virtualisation Platform:** Oracle VirtualBox 7.2.22  
**Network:** Isolated VirtualBox Internal Network  
**Project Type:** Hands-on cybersecurity implementation and portfolio project

---

## 2. Project Objectives

The primary objectives are to:

1. **Build an Enterprise Environment:** Design and deploy a simulated enterprise network with centralized identity management, servers and employee endpoints.

2. **Implement Security Controls:** Configure and evaluate technical security controls, including endpoint hardening, access management, firewall policies and security baselines.

3. **Apply Cybersecurity Frameworks:** Map implemented security practices to Essential Eight, NIST CSF 2.0, CIS Controls v8.1 and ISO/IEC 27001:2022.

4. **Establish Security Monitoring:** Deploy Wazuh SIEM to collect, monitor and analyse security events from enterprise endpoints.

5. **Develop Threat Detection Capabilities:** Generate controlled security events, identify suspicious activity and investigate potential threats.

6. **Conduct DFIR Investigations:** Practise evidence collection, event and log analysis, incident timeline construction and technical incident reporting.

7. **Evaluate Security Posture:** Perform asset identification, risk assessments and security control evaluations to identify gaps and recommend improvements.

8. **Integrate AI-Assisted Security Operations:** Explore AI-assisted alert triage, threat detection, security event analysis and DFIR support.

9. **Maintain Technical Documentation:** Record implementation procedures, troubleshooting activities, verification results, security configurations and supporting evidence.

---

## 3. Enterprise Environment

The lab represents a fictional organisation, Northstar Technologies, with an isolated enterprise network containing servers, workstations and security testing infrastructure.

### 3.1 Virtual Machine Architecture

| Machine | Role | Operating System | Current Status |
|---|---|---|---|
| DC01 | Domain Controller, Active Directory and DNS | Windows Server 2022 Standard Evaluation | Configured |
| WIN01 | Employee workstation | Windows 11 Pro | Installed and domain joined |
| WAZUH01 | SIEM and security monitoring | Linux | Planned |
| KALI01 | Controlled security testing | Kali Linux | Planned |
| WIN02 | Additional employee endpoint | Windows | Optional / planned |

### 3.2 Network Configuration

| Component | Configuration |
|---|---|
| Virtualisation Platform | Oracle VirtualBox |
| Virtual Network | Northstar-Lab |
| Network Type | Internal Network |
| Subnet | 10.10.10.0/24 |
| Domain Controller | DC01 |
| DC01 IP Address | 10.10.10.10 |
| WIN01 IP Address | 10.10.10.20 |
| Domain | northstar.local |
| DNS Server | 10.10.10.10 |

The network is designed as an isolated lab environment. Individual machine configurations and connectivity are recorded in the implementation documentation.

### 3.3 Active Directory Environment

The Windows Server infrastructure provides centralized identity and domain management.

Current implementation includes:

- Windows Server 2022 deployment on DC01.
- Active Directory Domain Services configuration.
- DNS configuration.
- Creation of the `northstar.local` domain.
- Promotion of DC01 as the domain controller.
- Windows 11 Pro workstation domain join.

The domain environment will be used to implement and test centralized security policies, workstation baselines and access management.

---

## 4. Technology Stack

| Technology | Purpose |
|---|---|
| Oracle VirtualBox 7.2.22 | Virtualisation and lab infrastructure |
| Windows Server 2022 | Enterprise server infrastructure |
| Windows 11 Pro | Employee workstation |
| Active Directory Domain Services | Centralized identity and domain management |
| DNS | Internal name resolution |
| Group Policy | Centralized security configuration |
| Windows Defender Firewall | Host-based network traffic control |
| Linux | SIEM infrastructure |
| Wazuh | Security monitoring and SIEM |
| Kali Linux | Controlled security testing |
| Sysmon | Endpoint activity monitoring |
| PowerShell | Windows administration, automation and security testing |
| Git and GitHub | Version control and project documentation |
| Visual Studio Code | Documentation and scripting |

Technologies are identified as implemented only when their deployment or configuration has been confirmed. Planned components will be updated as implementation progresses.

---

## 5. Cybersecurity Frameworks and Standards

The project uses established cybersecurity frameworks and standards to guide security implementation and evaluate the simulated enterprise environment.

| Framework / Standard | Application |
|---|---|
| Australian Essential Eight | Prioritised mitigation strategies to reduce exposure to common cyber threats |
| NIST Cybersecurity Framework 2.0 | Organising cybersecurity activities across six core functions |
| CIS Critical Security Controls v8.1 | Identifying and implementing prioritised security safeguards |
| ISO/IEC 27001:2022 | Applying information security management, risk assessment and ISMS concepts |

### 5.1 NIST CSF 2.0

Project activities will be organised around the six NIST CSF functions:

- **Govern:** Establish cybersecurity governance, policies, responsibilities and risk management.
- **Identify:** Identify assets, vulnerabilities, threats and organisational risks.
- **Protect:** Implement security controls to safeguard systems, users and information.
- **Detect:** Monitor systems and identify potentially malicious activity.
- **Respond:** Investigate and manage cybersecurity incidents.
- **Recover:** Restore systems and improve resilience following incidents.

### 5.2 Framework Mapping

The frameworks serve complementary purposes:

- Essential Eight provides prioritised mitigation strategies.
- NIST CSF 2.0 provides an overarching cybersecurity risk management structure.
- CIS Controls provide actionable security safeguards.
- ISO/IEC 27001 provides the basis for applying an information security management system approach.

Framework mappings will be supported by actual implementation records, testing and evidence. The project does not claim formal certification or compliance with these standards.

---

## 6. Security Controls and Endpoint Hardening

The project includes the implementation of security controls at the enterprise and workstation levels.

Initial workstation security configuration includes:

- Active Directory domain membership.
- Group Policy-based workstation security configuration.
- Centralized Windows Defender Firewall policy.
- Domain, Private and Public firewall profiles.
- Default inbound and outbound traffic policy configuration.

A workstation baseline Group Policy Object, `Northstar-Workstation-Baseline`, has been created and linked to the Workstations OU.

The firewall profiles have been configured as enabled. However, verification identified an issue where the effective default inbound and outbound actions displayed as `NotConfigured` instead of the intended `Block` and `Allow` values.

This issue remains subject to investigation and verification. The firewall baseline will not be marked fully verified until the effective policy reflects the intended configuration.

Further endpoint hardening and security controls will be implemented progressively.

---

## 7. Security Monitoring and DFIR

A major objective is to develop a security monitoring and incident investigation workflow using enterprise endpoint telemetry and SIEM capabilities.

The planned workflow is:

**Security Events → Wazuh Alerts → Alert Triage → Incident Investigation → DFIR → Response → Recovery → Lessons Learned**

The investigation process will involve:

- Collecting endpoint and system logs.
- Monitoring suspicious processes and activities.
- Identifying indicators of compromise (IOCs).
- Analysing security events and correlating relevant activity.
- Constructing incident timelines.
- Preserving and analysing digital evidence.
- Investigating simulated security incidents.
- Preparing technical incident reports.
- Identifying improvements to existing security controls.

Wazuh deployment, endpoint log collection and the complete monitoring workflow remain part of the planned implementation.

---

## 8. AI-Assisted SOC and DFIR Integration

AI-assisted security operations are a planned extension of the project.

The objective is to explore how AI can support security analysts in monitoring, analysing and investigating security events.

Potential capabilities include:

- AI-assisted security alert triage and prioritisation.
- Contextual analysis of suspicious activity.
- Assistance with threat detection and event correlation.
- Security log analysis and investigation support.
- Incident summarisation and timeline assistance.
- DFIR investigation support and report preparation.

AI integration will be developed after the foundational enterprise environment, security monitoring and core DFIR capabilities have been implemented and verified.

The objective is to demonstrate how AI can assist security operations while retaining analyst oversight and evidence-based investigation practices.

---

## 9. Project Documentation

The repository maintains technical documentation throughout the implementation process.

Documentation includes:

- Enterprise architecture and network design.
- Virtual machine configuration and deployment.
- Infrastructure implementation records.
- Security control implementation and testing.
- Troubleshooting records and frequently asked questions.
- Security framework mappings.
- Security monitoring and DFIR workflows.
- Investigation reports and supporting evidence.

The documentation aims to capture the actual implementation journey, including technical decisions, errors, troubleshooting procedures, resolutions, verification results and lessons learned.

Implementation status distinguishes between:

- **Configured:** A setting or component has been configured.
- **Implemented:** A component or capability has been deployed.
- **Verified:** Its expected behaviour has been confirmed through testing or evidence.
- **Pending:** Work remains incomplete or requires further investigation.

---

## 10. Repository Structure

```text
enterprise-security-dfir-lab/
│
├── README.md
├── .gitignore
│
├── Architecture/
│   ├── architecture.md
│   ├── enterprise-architecture
│   └── network-diagram
│
├── Lab-Build/
│   └── implementation-status.md
│
├── Troubleshooting/
│   ├── troubleshooting-index.md
│   ├── ISSUE-001-server-installation-error.md
│   ├── ISSUE-002-dc01-hostname-and-promotion.md
│   ├── ISSUE-003-administrator-password-confusion.md
│   ├── ISSUE-004-dc01-network-apipa.md
│   ├── ISSUE-005-win01-windows11-uefi-boot.md
│   └── FAQ.md
│
└── [Additional documentation directories
    will be introduced as the project develops]
```

The structure will expand as additional infrastructure, security controls, monitoring capabilities and DFIR investigations are implemented.

---

## 11. Current Implementation Status

The project is being developed progressively. The following is a high-level summary; detailed implementation records and outstanding issues are maintained in `Lab-Build/implementation-status.md`.

| Component | Current Status |
|---|---|
| GitHub repository and project structure | Created |
| VirtualBox lab environment | In use |
| DC01 Windows Server 2022 | Configured |
| DC01 static network configuration | User-reported as resolved |
| Active Directory Domain Services | Configured |
| DNS and `northstar.local` domain | Configured |
| WIN01 Windows 11 Pro installation | Completed |
| WIN01 hostname verification | Verified |
| WIN01 network configuration | Verified |
| WIN01 domain join | Verified |
| Workstation baseline GPO | Created and linked |
| Firewall profile configuration | Configured |
| Effective firewall inbound/outbound actions | Issue identified; resolution pending |
| Wazuh SIEM | Planned |
| Kali Linux testing environment | Planned |
| Centralized security monitoring | Planned |
| DFIR investigation workflows | Planned |
| AI-assisted SOC and DFIR | Planned |

---

## 12. Future Development

The project will progressively develop into a simulated enterprise security environment incorporating:

1. Completion and verification of the enterprise infrastructure.
2. Workstation and server security hardening.
3. Centralized security monitoring using Wazuh.
4. Endpoint telemetry and threat detection.
5. Controlled security testing and attack simulation.
6. Incident response and DFIR investigations.
7. Security risk assessment and framework mapping.
8. AI-assisted SOC and DFIR capabilities.
9. Technical evaluation, evidence collection and project reporting.

Each stage will be documented and tested before being treated as completed.

---

## 13. Disclaimer

This project is developed exclusively for educational and portfolio purposes within a controlled virtual environment.

All security testing and simulated attacks are conducted against authorised lab systems. The project does not involve unauthorised access to external systems or networks.

This project demonstrates practical learning and implementation of cybersecurity concepts. It does not constitute formal certification, accreditation or compliance with any referenced cybersecurity framework or standard.

---

## Author

**Northstar Technologies — Enterprise Security & DFIR Lab**

Cybersecurity Portfolio Project
