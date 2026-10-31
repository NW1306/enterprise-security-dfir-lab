# Enterprise Security & DFIR Lab
### Northstar Technologies

**Enterprise Security | Digital Forensics & Incident Response | Security Operations**

---

## 1. Project Overview

Northstar Technologies is a simulated enterprise environment designed and implemented using Oracle VirtualBox to explore practical enterprise cybersecurity operations.

The project focuses on building an enterprise IT infrastructure, implementing security controls, monitoring security events, and investigating security incidents through Digital Forensics and Incident Response (DFIR).

The lab integrates enterprise infrastructure, endpoint security, security monitoring and incident response practices, with implementation activities mapped to recognised cybersecurity frameworks and standards.

The project aims to demonstrate practical knowledge of:

- Enterprise infrastructure and network architecture.
- Windows Server and Active Directory.
- Endpoint security and system hardening.
- Security monitoring and SIEM using Wazuh.
- Threat detection and incident response.
- Digital Forensics and Incident Response (DFIR).
- Security risk assessment and governance.

**Environment:** Simulated enterprise network — Northstar Technologies  
**Virtualisation Platform:** Oracle VirtualBox  
**Project Type:** Hands-on cybersecurity lab and portfolio project

---

## 2. Project Objectives

The primary objectives of this project are to:

1. **Build an Enterprise Environment:** Design and deploy a simulated enterprise network with centralized identity management, endpoints and security infrastructure.

2. **Implement Security Controls:** Configure and evaluate technical security controls, including system hardening, access management and endpoint protection.

3. **Apply Security Frameworks:** Map implemented security practices to the Essential Eight, NIST CSF 2.0, CIS Controls and ISO/IEC 27001:2022.

4. **Establish Security Monitoring:** Deploy Wazuh SIEM to collect, monitor and analyse security events from enterprise endpoints.

5. **Perform Threat Detection:** Generate controlled security events, identify suspicious activity and investigate potential threats.

6. **Conduct DFIR Investigations:** Practise evidence collection, log analysis, incident timelines, investigation and incident reporting.

7. **Evaluate Security Posture:** Conduct asset identification, risk assessments and security control evaluations to identify gaps and recommend improvements.

8. **Document Implementation:** Maintain technical documentation, troubleshooting records, verification results and evidence throughout the project lifecycle.

---

## 3. Enterprise Environment

The project simulates the IT infrastructure of a fictional organisation, Northstar Technologies.

The planned environment consists of multiple virtual machines operating within an isolated VirtualBox network.

### Planned Infrastructure

| Machine | Role | Operating System |
|---|---|---|
| DC01 | Domain Controller, Active Directory and DNS | Windows Server 2022 |
| WIN01 | Employee workstation | Windows 10 |
| WAZUH01 | SIEM and security monitoring | Linux |
| KALI01 | Controlled security testing | Kali Linux |
| WIN02 | Additional endpoint (optional) | Windows |

### Planned Network Configuration

| Component | Configuration |
|---|---|
| Virtual Network | Northstar-Lab |
| Network Type | Internal Network |
| Subnet | 10.10.10.0/24 |
| DC01 IP | 10.10.10.10 |
| Domain | northstar.local |
| DNS Server | 10.10.10.10 |

*Note: These represent the intended architecture. Individual machine configurations and connectivity will be documented as they are implemented and verified.*

---

## 4. Technology Stack

The project uses the following technologies and tools.

| Technology | Purpose |
|---|---|
| Oracle VirtualBox | Virtualisation and lab infrastructure |
| Windows Server 2022 | Enterprise server infrastructure |
| Active Directory | Centralised identity and access management |
| Windows 10 | Employee endpoint simulation |
| Linux | SIEM infrastructure |
| Wazuh | Security monitoring and SIEM |
| Kali Linux | Controlled security testing |
| Sysmon | Endpoint activity monitoring |
| PowerShell | Windows administration and security testing |
| Git and GitHub | Version control and project documentation |
| Visual Studio Code | Documentation and scripting |

*Technologies will be marked as implemented once their deployment is confirmed.*

---

## 5. Cybersecurity Frameworks

The project incorporates recognised cybersecurity frameworks and security standards to guide implementation and evaluate the simulated enterprise environment.

| Framework | Application |
|---|---|
| Australian Essential Eight | Implementation and assessment of prioritised mitigation strategies |
| NIST Cybersecurity Framework 2.0 | Organising cybersecurity activities across six core functions |
| CIS Critical Security Controls v8.1 | Identifying and implementing prioritised security safeguards |
| ISO/IEC 27001:2022 | Applying information security management and ISMS concepts |

### NIST CSF 2.0

Project activities will be organised around the six NIST CSF functions:

- **Govern:** Establish cybersecurity governance, policies and risk management.
- **Identify:** Identify assets, vulnerabilities and organisational risks.
- **Protect:** Implement security controls to safeguard systems and information.
- **Detect:** Monitor systems and identify potentially malicious activity.
- **Respond:** Investigate and manage security incidents.
- **Recover:** Restore systems and improve resilience following incidents.

Framework mapping will be supported by actual implementation records, testing and evidence.

---

## 6. Security Monitoring & DFIR

A key component of the project is developing a security monitoring and incident investigation workflow.

The planned workflow is:

**Security Events → Wazuh Alerts → Incident Triage → Investigation → DFIR → Response → Recovery → Lessons Learned**

The investigation process will involve:

- Collecting endpoint and system logs.
- Identifying indicators of compromise (IOCs).
- Analysing suspicious processes and activities.
- Correlating security events.
- Constructing incident timelines.
- Preserving and analysing digital evidence.
- Preparing technical incident reports.
- Identifying improvements to existing security controls.

---

## 7. Project Documentation

The repository maintains technical documentation throughout the implementation process.

Documentation will include:

- Enterprise and network architecture.
- Virtual machine configuration and deployment.
- Infrastructure implementation records.
- Security control implementation and testing.
- Troubleshooting and frequently asked questions.
- Security framework mappings.
- Evidence and investigation reports.

The documentation aims to capture the actual implementation journey, including technical decisions, errors, troubleshooting procedures, resolutions and lessons learned.

---

## 8. Repository Structure

```text
Enterprise-Security-DFIR-Lab/
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
│
└── [Additional documentation directories
     will be introduced as the project develops]
```

---

## 9. Implementation Status

The project is being developed progressively. The following table distinguishes completed setup activities from planned and unverified components.

| Component | Status |
|---|---|
| GitHub repository | Created |
| VirtualBox environment | In use |
| WIN01 installation | Installed |
| Original DC01 installation | Rebuild required |
| DC01-Rebuild | Troubleshooting |
| Static IP configuration | User-reported as resolved; verification pending |
| Active Directory | Not yet verified operational |
| Wazuh SIEM | Planned |
| Kali Linux | Planned |
| Security controls | Planned |
| DFIR investigations | Planned |

Implementation progress and verification evidence are maintained separately in `Lab-Build/implementation-status.md`.

---

## 10. Project Goals & Future Development

The project will progressively develop into a simulated enterprise security environment incorporating:

- Enterprise infrastructure and identity management.
- Security hardening and control implementation.
- Centralised security monitoring.
- Threat detection and incident response.
- Digital forensic investigations.
- Security risk assessment and reporting.
- Framework-based security evaluation.

Future development will also explore AI-assisted SOC monitoring, alert triage, threat detection and DFIR workflows after the foundational enterprise environment and monitoring capabilities are established.

---

## 11. Disclaimer

This project is developed exclusively for educational purposes within a controlled virtual environment.

All security testing and simulated attacks are conducted against authorised lab systems. The project does not involve unauthorised access to external systems or networks.

This project demonstrates practical learning and implementation of cybersecurity concepts. It does not constitute formal certification, accreditation or compliance with any referenced cybersecurity framework or standard.

---

## Author

**Cybersecurity Portfolio Project — Northstar Technologies**

