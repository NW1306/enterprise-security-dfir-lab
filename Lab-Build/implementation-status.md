# Implementation Status
## Northstar Technologies — Enterprise Security & DFIR Lab

**Last updated:** 1 November 2026  
**Virtualisation Platform:** Oracle VirtualBox 7.2.22  
**Working Git Branch:** `dev`  
**Lab Network:** `Northstar-Lab`  
**Domain:** `northstar.local`

---

## 1. Project Overview

This document records the implementation progress of the Northstar Technologies Enterprise Security & DFIR Lab.

It tracks:

- Virtual machine deployment and configuration.
- Enterprise network configuration.
- Active Directory and DNS deployment.
- Windows workstation configuration and domain integration.
- Group Policy and security baseline implementation.
- Verification results and outstanding issues.
- Planned infrastructure and security capabilities.

Implementation status is classified as follows:

| Status | Meaning |
|---|---|
| **Planned** | Not yet implemented. |
| **In Progress** | Implementation has started but is incomplete. |
| **Configured** | Configuration has been performed. |
| **Implemented** | Component or capability has been deployed. |
| **Verified** | Expected behaviour has been confirmed through testing or evidence. |
| **Issue Identified** | An unexpected result has been observed and requires investigation. |
| **Pending Verification** | Configuration is reported as complete, but sufficient verification evidence is not yet recorded. |

---

## 2. Lab Environment

### 2.1 Virtualisation Platform

| Component | Configuration |
|---|---|
| Hypervisor | Oracle VirtualBox |
| VirtualBox Version | 7.2.22 r175245 |
| Network Type | Internal Network |
| Internal Network Name | `Northstar-Lab` |
| Network Subnet | `10.10.10.0/24` |
| Domain | `northstar.local` |

The lab is designed to operate within an isolated virtual network for controlled enterprise security testing.

### 2.2 Planned Virtual Machines

| Machine | Operating System | Role | Status |
|---|---|---|---|
| DC01 | Windows Server 2022 Standard Evaluation | Domain Controller, AD DS and DNS | Configured |
| WIN01 | Windows 11 Pro | Employee workstation | Domain joined |
| WAZUH01 | Linux | SIEM and security monitoring | Planned |
| KALI01 | Kali Linux | Controlled security testing | Planned |
| WIN02 | Windows | Additional employee endpoint | Optional / Planned |

---

## 3. Network Configuration

### 3.1 Addressing Plan

| Machine | IP Address | Subnet Mask | Preferred DNS |
|---|---|---|---|
| DC01 | `10.10.10.10` | `255.255.255.0` | `10.10.10.10` |
| WIN01 | `10.10.10.20` | `255.255.255.0` | `10.10.10.10` |

**Default Gateway:** Not configured in the current isolated network design.

### 3.2 Network Implementation Status

| Task | Status |
|---|---|
| Create VirtualBox Internal Network | Configured |
| Configure DC01 network settings | User-reported as resolved |
| Configure WIN01 network settings | Verified |
| Configure WIN01 DNS to use DC01 | Verified as part of workstation network configuration |
| Establish domain connectivity | Verified through successful domain join |

---

## 4. DC01 — Domain Controller

### 4.1 System Configuration

| Component | Configuration |
|---|---|
| Virtual Machine Name | `DC01-Rebuild` |
| Windows Hostname | `DC01` |
| Operating System | Windows Server 2022 Standard Evaluation |
| Installation Type | Desktop Experience |
| IP Address | `10.10.10.10` |
| Subnet Mask | `255.255.255.0` |
| Preferred DNS | `10.10.10.10` |
| Domain | `northstar.local` |

### 4.2 Implementation Progress

| Task | Status |
|---|---|
| Deploy replacement Windows Server VM | Completed |
| Install Windows Server 2022 | Completed |
| Configure hostname as DC01 | Configured |
| Configure static IP address | User-reported as resolved |
| Install Active Directory Domain Services | Configured |
| Configure DNS | Configured |
| Promote server to Domain Controller | Configured |
| Create `northstar.local` domain | Configured |

### 4.3 Notes

The original server installation was abandoned and replaced with a rebuilt virtual machine.

The replacement machine is named `DC01-Rebuild` in VirtualBox, while its Windows hostname is `DC01`.

Active Directory Domain Services and DNS have been configured, and the `northstar.local` domain has been created.

Operational verification evidence, including the final network configuration and domain-controller health checks, should be retained as part of the project evidence.

---

## 5. WIN01 — Employee Workstation

### 5.1 System Configuration

| Component | Configuration |
|---|---|
| Virtual Machine | WIN01 |
| Operating System | Windows 11 Pro |
| Role | Employee workstation |
| Hostname | `WIN01` |
| IP Address | `10.10.10.20` |
| Subnet Mask | `255.255.255.0` |
| Preferred DNS | `10.10.10.10` |
| Domain | `northstar.local` |

### 5.2 Installation and Configuration

| Task | Status |
|---|---|
| Install Windows 11 Pro | Completed |
| Configure VirtualBox VM hardware | Completed |
| Resolve Windows 11 setup compatibility issue | Workaround successful |
| Create local Windows account | Completed |
| Verify hostname | Verified |
| Configure workstation network settings | Verified |
| Configure DNS to use DC01 | Verified |
| Join `northstar.local` domain | Verified |

### 5.3 Windows 11 Setup Workaround

During Windows 11 installation, the virtual machine encountered a setup compatibility issue involving the virtual hardware configuration.

The VM was configured with:

- UEFI enabled.
- TPM 2.0 enabled.
- Secure Boot configuration enabled during setup troubleshooting.
- Processor allocation increased to three virtual CPUs.

The Windows 11 installation proceeded successfully after the processor allocation was changed to three CPUs.

This records the successful workaround. The underlying cause of the earlier setup failure has not been conclusively established.

### 5.4 Domain Integration

WIN01 has successfully joined the `northstar.local` domain.

The workstation is intended to operate as a managed employee endpoint within the Northstar Technologies enterprise environment.

Future verification will include:

- Domain authentication.
- Group Policy application.
- Workstation security baseline enforcement.
- Centralized endpoint monitoring.

---

## 6. Group Policy and Workstation Security Baseline

### 6.1 Group Policy Object

| Component | Configuration |
|---|---|
| GPO Name | `Northstar-Workstation-Baseline` |
| Target OU | `Workstations` |
| Policy Purpose | Centralized workstation security baseline |
| Target System | WIN01 |

The Group Policy Object has been created and linked to the Workstations OU.

### 6.2 Windows Defender Firewall Configuration

The following firewall settings were configured through Group Policy:

| Firewall Profile | Intended State |
|---|---|
| Domain Profile | Enabled |
| Private Profile | Enabled |
| Public Profile | Enabled |

Intended default traffic actions:

| Setting | Intended Value |
|---|---|
| Inbound Connections | Block |
| Outbound Connections | Allow |

### 6.3 Verification Issue

During effective firewall policy verification, the inbound and outbound default actions did not display the intended values.

Instead of:

- Default Inbound Action: `Block`
- Default Outbound Action: `Allow`

The verification output displayed:

- Default Inbound Action: `NotConfigured`
- Default Outbound Action: `NotConfigured`

The firewall profiles had been configured as enabled, but the expected default traffic actions were not reflected in the effective settings.

### 6.4 Current Status

| Task | Status |
|---|---|
| Create workstation baseline GPO | Configured |
| Link GPO to Workstations OU | Configured |
| Configure Domain firewall profile | Configured |
| Configure Private firewall profile | Configured |
| Configure Public firewall profile | Configured |
| Verify effective firewall profile settings | Performed |
| Confirm inbound default action is Block | Issue Identified |
| Confirm outbound default action is Allow | Issue Identified |
| Resolve policy configuration/application issue | Pending |

**Important:** The firewall baseline is not considered fully verified. The `NotConfigured` result must be investigated and resolved before the intended inbound and outbound traffic policies can be marked as enforced.

---

## 7. Security Monitoring Infrastructure

### 7.1 Wazuh SIEM

| Task | Status |
|---|---|
| Plan Wazuh deployment | Completed |
| Deploy Wazuh server | Planned |
| Configure Wazuh dashboard | Planned |
| Integrate Windows endpoints | Planned |
| Configure log collection | Planned |
| Verify alert generation | Planned |

Wazuh will serve as the central security monitoring and alerting platform.

### 7.2 Endpoint Telemetry

Planned endpoint monitoring activities include:

- Windows event log collection.
- Sysmon deployment and configuration.
- Process and authentication monitoring.
- Detection of suspicious PowerShell activity.
- Monitoring of account and privilege changes.
- Forwarding endpoint telemetry to Wazuh.

These capabilities will be implemented after the foundational enterprise infrastructure and workstation baseline are established.

---

## 8. Security Testing Infrastructure

### 8.1 Kali Linux

| Task | Status |
|---|---|
| Deploy Kali Linux VM | Planned |
| Configure lab network connectivity | Planned |
| Establish controlled testing environment | Planned |
| Perform authorised attack simulations | Planned |

Kali Linux will be used to generate controlled security events and simulate attacker techniques within the isolated lab.

### 8.2 Additional Windows Endpoint

WIN02 is an optional additional workstation.

It may be introduced later to expand endpoint monitoring, Group Policy testing and enterprise security scenarios.

---

## 9. DFIR Implementation

The project will progressively develop a complete incident investigation workflow.

| Capability | Status |
|---|---|
| Endpoint log collection | Planned |
| Centralized security monitoring | Planned |
| Alert triage | Planned |
| Incident identification | Planned |
| Evidence collection | Planned |
| Log analysis and event correlation | Planned |
| Incident timeline construction | Planned |
| Digital forensic investigation | Planned |
| Incident reporting | Planned |
| Recovery and lessons learned | Planned |

The objective is to conduct controlled investigations using generated lab events and document the investigation process with supporting evidence.

---

## 10. AI-Assisted SOC and DFIR

AI integration is a planned extension of the Northstar Technologies lab.

Potential capabilities include:

- AI-assisted security alert triage.
- Threat and anomaly analysis.
- Security event summarisation.
- Assistance with incident investigation.
- DFIR timeline and report preparation.

AI development will begin after the foundational infrastructure, monitoring and DFIR capabilities have been implemented and verified.

---

## 11. Outstanding Tasks

The following tasks remain part of the implementation roadmap.

### Infrastructure and Security Configuration

- [ ] Verify DC01 network configuration and domain-controller health.
- [ ] Investigate why effective firewall inbound and outbound actions display `NotConfigured`.
- [ ] Correct the firewall policy configuration or application issue.
- [ ] Verify the effective firewall settings on WIN01.
- [ ] Verify successful Group Policy application on WIN01.

### Security Monitoring

- [ ] Deploy WAZUH01.
- [ ] Configure the Wazuh dashboard.
- [ ] Integrate WIN01 with Wazuh.
- [ ] Configure endpoint log collection.
- [ ] Deploy and configure Sysmon.
- [ ] Verify security alert generation.

### Security Testing and DFIR

- [ ] Deploy KALI01.
- [ ] Conduct controlled security testing.
- [ ] Generate and investigate security events.
- [ ] Develop incident investigation procedures.
- [ ] Document forensic evidence and incident timelines.
- [ ] Prepare technical DFIR reports.

### AI Integration

- [ ] Define AI-assisted SOC architecture.
- [ ] Identify suitable AI integration points.
- [ ] Develop AI-assisted alert triage.
- [ ] Explore AI-assisted threat analysis.
- [ ] Integrate AI support into DFIR workflows.
- [ ] Evaluate accuracy, limitations and analyst oversight.

---

## 12. Implementation Principles

The following principles will guide the remaining project work:

1. Every major configuration must be tested before being marked verified.
2. Screenshots, command outputs and relevant logs should be retained as implementation evidence.
3. Troubleshooting records must document the observed problem, investigation, resolution and verification.
4. Security framework mappings must reflect actual controls and evidence.
5. Planned capabilities must not be represented as implemented.
6. AI-assisted functionality must retain human oversight and support evidence-based security investigations.
7. The lab must remain isolated and all testing must be authorised.

---

## 13. Current Project Summary

The foundational Windows enterprise environment has been established.

DC01 has been configured with Windows Server 2022, Active Directory Domain Services and DNS for the `northstar.local` domain.

WIN01 has been installed with Windows 11 Pro. Its hostname and network configuration have been verified, and it has successfully joined the domain.

A workstation security baseline GPO has also been created and linked to the Workstations OU. However, the effective Windows Defender Firewall inbound and outbound default actions are displaying `NotConfigured`. This remains an outstanding configuration and verification issue.

The next implementation priority is to resolve the firewall policy issue and confirm successful Group Policy enforcement before proceeding to centralized security monitoring with Wazuh.

**Project status:** Foundational enterprise infrastructure established; workstation firewall baseline verification and security monitoring deployment remain in progress.
