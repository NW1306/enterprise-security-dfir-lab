# Enterprise Security & DFIR Lab — Architecture Overview

## 1. Project Overview

The Northstar Technologies Enterprise Security & DFIR Lab is a simulated enterprise environment designed to demonstrate the implementation of enterprise infrastructure, security controls, security monitoring, incident response and digital forensics.

The lab is built using Oracle VirtualBox and is intended to simulate a small enterprise network in which systems, users, security controls and monitoring capabilities can be progressively deployed and tested.

The project integrates concepts and controls from:

- Essential Eight
- NIST Cybersecurity Framework (CSF) 2.0
- ISO/IEC 27001:2022
- CIS Critical Security Controls v8.1

These frameworks serve different purposes and are used as complementary references when designing and evaluating the lab.

## 2. Architecture Objectives

The architecture is designed to support the following objectives:

1. Establish a simulated enterprise domain environment.
2. Implement centralised identity and access management using Active Directory.
3. Configure secure workstation and server baselines.
4. Apply security policies through Group Policy.
5. Deploy centralised security monitoring using Wazuh.
6. Simulate controlled attack activity using Kali Linux.
7. Collect and analyse security events.
8. Develop incident response and digital forensic investigation workflows.
9. Integrate AI-assisted security monitoring and investigation after the foundational environment is operational.

## 3. Architecture Design

The lab follows a layered architecture.

| Layer | Purpose | Components |
|---|---|---|
| Virtualisation | Provides isolated virtual infrastructure | Oracle VirtualBox |
| Network | Connects lab systems through an isolated network | `Northstar-Lab` |
| Identity and infrastructure | Provides domain services and name resolution | DC01, Active Directory, DNS |
| Endpoints | Represents enterprise employee systems | WIN01 |
| Security monitoring | Collects and analyses security events | Wazuh — planned |
| Attack simulation | Generates controlled security testing activity | Kali Linux — planned |
| Incident response and forensics | Supports investigation and response workflows | DFIR tooling and procedures — planned |
| AI-assisted security | Supports future alert triage and investigation workflows | AI integration — planned |

## 4. Virtual Infrastructure

The environment is hosted using Oracle VirtualBox.

| Virtual machine | Operating system | Role | Status |
|---|---|---|---|
| DC01 | Windows Server 2022 Standard Evaluation | Domain Controller, AD DS and DNS | Configured |
| WIN01 | Windows 11 Pro | Domain-joined workstation | Configured and domain join verified |
| WAZUH01 | Linux distribution — to be selected/configured | SIEM and security monitoring | Planned |
| KALI01 | Kali Linux | Controlled attacker and testing machine | Planned |
| WIN02 | Windows workstation | Additional enterprise endpoint | Optional; not started |

## 5. Network Design

The lab uses an isolated VirtualBox Internal Network.

| Parameter | Configuration |
|---|---|
| Network name | `Northstar-Lab` |
| Network address | `10.10.10.0/24` |
| DC01 | `10.10.10.10` |
| WIN01 | `10.10.10.20` |
| DC01 DNS | `10.10.10.10` |
| Active Directory domain | `northstar.local` |

The network is intended to remain isolated from the host and external networks unless a specific requirement justifies a controlled change.

A default gateway is not part of the current addressing plan.

## 6. Identity and Access Management

Active Directory Domain Services provides centralised identity and domain management.

The lab domain is:

`northstar.local`

DC01 provides the domain controller and DNS roles.

WIN01 has been joined to the domain. Group Policy is being used to establish workstation security baselines.

The `Northstar-Workstation-Baseline` GPO has been created and linked to the `Northstar/Workstations` OU. Its effective Windows Defender Firewall settings still require investigation because the observed inbound and outbound default actions were `NotConfigured`.

## 7. Security Architecture and Framework Alignment

The lab uses the following frameworks as design and assessment references.

### Essential Eight

The Essential Eight provides prioritised mitigation strategies to reduce exposure to common cyber threats.

The lab will progressively implement relevant controls, including application control, patching, administrative restrictions, application hardening, MFA and backup-related practices where supported by the environment.

### NIST CSF 2.0

The NIST Cybersecurity Framework provides the high-level structure for organising security activities:

- Govern
- Identify
- Protect
- Detect
- Respond
- Recover

### CIS Critical Security Controls v8.1

CIS Controls provide prioritised safeguards that can guide technical security implementation and validation.

### ISO/IEC 27001:2022

ISO/IEC 27001 provides an Information Security Management System (ISMS) reference, including risk management, governance, policies and continual improvement.

The project demonstrates selected practices and technical controls. It does not claim formal certification or complete compliance with any framework.

## 8. Security Monitoring and DFIR Architecture

The planned security monitoring workflow is:

1. Enterprise endpoints generate operating system and security events.
2. Wazuh collects and analyses supported telemetry.
3. Security alerts are reviewed and triaged.
4. Relevant activity is investigated.
5. Evidence is collected and preserved.
6. Incident response actions are documented.
7. Recovery and lessons learned are recorded.
8. Relevant security controls are reviewed and improved.

Wazuh deployment, attack simulation and full DFIR workflow implementation remain future build activities.

## 9. AI-Assisted Security Integration

AI integration is a later project phase, dependent on the successful implementation and verification of the foundational enterprise and security monitoring environment.

Planned capabilities include:

- AI-assisted alert triage.
- Security event summarisation.
- Detection investigation support.
- Threat intelligence enrichment.
- DFIR investigation assistance.
- Incident report preparation.

AI-generated analysis will be treated as decision support. Security findings and incident conclusions must be validated against underlying telemetry and evidence.

## 10. Architecture Principles

The project follows these principles:

- Isolation: Keep the lab network separated from production and external networks.
- Least privilege: Avoid unnecessary administrative access.
- Defence in depth: Apply multiple complementary security controls.
- Centralisation: Use centralised identity and security monitoring where appropriate.
- Evidence-based validation: Verify configurations and document actual results.
- Repeatability: Maintain clear configuration and troubleshooting records.
- Framework alignment: Map implemented controls to relevant framework objectives.
- Separation of phases: Build and verify foundational capabilities before adding AI integration.

## 11. Current Implementation Boundary

The architecture describes both the current environment and the intended target environment.

Configured or user-verified components:
- DC01 Windows Server 2022.
- Active Directory Domain Services and DNS configuration.
- `northstar.local` domain creation.
- WIN01 Windows 11 Pro.
- WIN01 network configuration and domain join.
- Initial workstation baseline GPO configuration.

Still requiring implementation or verification:
- Effective Group Policy and firewall baseline validation.
- Wazuh deployment and endpoint integration.
- Kali Linux deployment and controlled testing.
- Security alert investigation workflows.
- DFIR procedures and evidence-handling workflows.
- AI-assisted SOC/DFIR integration.

## 12. Project Scope Limitation

This is a simulated enterprise lab for learning, implementation and portfolio demonstration.

It is not a production enterprise deployment, an accredited security assessment or a certification exercise. Framework mappings indicate design alignment and implemented evidence, not formal compliance.
