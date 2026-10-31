# Infrastructure Implementation Status

**Project:** Northstar Technologies — Enterprise Security & DFIR Lab  
**Last updated:** 1 November 2026

## 1. Objective

Establish the foundational enterprise infrastructure using Oracle VirtualBox, Windows Server and Windows client operating systems.

The infrastructure will provide the foundation for Active Directory, endpoint management, security monitoring, incident response and AI-assisted SOC/DFIR capabilities.

## 2. Virtual Infrastructure

| Component | Configuration | Status |
|---|---|---|
| Virtualisation | Oracle VirtualBox | In use |
| Lab network | Northstar-Lab (Internal Network) | Configured |
| Network subnet | 10.10.10.0/24 | Planned/configured |
| Domain Controller | DC01-Rebuild | Configured |
| Domain | northstar.local | Created |
| Windows workstation | Original WIN01 (Windows 10 Home) | Tested; being replaced |
| Replacement workstation | WIN01 (Windows 11 Pro) | ISO downloading |
| SIEM | Wazuh | Not yet deployed |
| Attacker simulation | Kali Linux | Not yet deployed |

## 3. Domain Controller — DC01

**Operating system:** Windows Server 2022 Standard Evaluation (Desktop Experience)

**Configuration:**

| Setting | Value |
|---|---|
| Hostname | DC01 |
| IP address | 10.10.10.10 |
| Subnet mask | 255.255.255.0 |
| DNS | 10.10.10.10 |
| Active Directory domain | northstar.local |
| Network | Northstar-Lab |

Active Directory Domain Services and DNS were configured.

The server was promoted to a domain controller for the northstar.local forest.

## 4. Initial Workstation — WIN01

The original workstation used Windows 10 Home, version 22H2.

The following activities were completed:

- Connected the VM to the Northstar-Lab internal network.
- Configured the workstation hostname as WIN01.
- Configured its static IPv4 address as 10.10.10.20.
- Configured DC01 (10.10.10.10) as its preferred DNS server.
- Successfully pinged DC01 with 0% packet loss.
- Successfully resolved the Active Directory LDAP SRV record to dc01.northstar.local.

### Domain-joining limitation

The workstation was unable to join the Active Directory domain because Windows 10 Home does not support traditional Active Directory domain joining.

A replacement Windows 11 Pro workstation is therefore being prepared.

## 5. Replacement Workstation

The replacement workstation will use Windows 11 Pro.

Planned configuration:

| Setting | Value |
|---|---|
| VM hostname | WIN01 |
| Operating system | Windows 11 Pro |
| RAM | 4–6 GB |
| CPU | 2 |
| Virtual disk | 64 GB |
| IP address | 10.10.10.20 |
| DNS | 10.10.10.10 |
| Domain | northstar.local |

These settings are planned and must be verified after installation.

## 6. Current Project Status

### Completed or configured
- VirtualBox lab environment established.
- Northstar-Lab internal network configured.
- DC01-Rebuild configured.
- Active Directory domain northstar.local created.
- DNS configured on DC01.
- Original Windows 10 workstation network connectivity tested.
- Active Directory DNS SRV lookup tested successfully.

### In progress
- Windows 11 Pro ISO download.
- Replacement WIN01 workstation preparation.

### Outstanding
- Install Windows 11 Pro.
- Configure replacement WIN01 network settings.
- Verify DNS resolution from the replacement workstation.
- Join WIN01 to northstar.local.
- Verify domain authentication.
- Deploy Wazuh and Sysmon.
- Begin security control implementation.

## 7. Future Security Integration

The infrastructure will eventually support:

- Essential Eight implementation and assessment.
- NIST CSF 2.0 mapping.
- CIS Controls implementation.
- ISO/IEC 27001:2022 ISMS documentation.
- Wazuh-based security monitoring.
- Controlled attack simulations.
- Digital forensics and incident response.
- AI-assisted alert triage, threat analysis, MITRE ATT&CK mapping and DFIR investigation assistance.

AI capabilities will be integrated after the foundational monitoring and investigation workflows are operational.

## 8. Evidence Requirements

Evidence to capture and retain:

- VirtualBox VM configuration screenshots.
- DC01 network configuration.
- Active Directory domain configuration.
- DNS configuration and successful SRV lookup.
- Successful connectivity tests.
- Windows 11 Pro installation and domain membership.
- Subsequent SIEM and security control verification.

Screenshots must not expose passwords, licence keys or other sensitive information.

---

**Documentation principle:** A planned configuration must not be presented as a completed implementation. Each configuration should be supported by verification evidence.