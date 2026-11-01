# WIN01 Build and Configuration Record

**Date:** 1 November 2026  
**Project:** Northstar Technologies — Enterprise Security & DFIR Lab  
**Virtualisation platform:** Oracle VirtualBox 7.2.22  
**Endpoint:** WIN01  
**Operating system:** Windows 11 Pro

## 1. Objective

Rebuild the WIN01 employee workstation using Windows 11 Pro and prepare it for integration into the Northstar Technologies Active Directory domain.

## 2. Installation Environment

| Parameter | Configuration |
|---|---|
| Virtualisation platform | Oracle VirtualBox |
| Virtual machine | WIN01 |
| Operating system | Windows 11 Pro |
| Firmware | UEFI |
| TPM | Version 2.0 |
| Secure Boot | Enabled |
| Virtual processors | 3 |
| Domain | northstar.local |

Note: The three-processor configuration was used to get past the observed UEFI blank-screen issue. The underlying cause has not been conclusively established.

## 3. Installation and Troubleshooting

### 3.1 Windows 11 hardware compatibility

Windows Setup initially reported that the virtual machine did not meet the TPM 2.0 and Secure Boot requirements.

The VM was configured with UEFI, TPM 2.0 and Secure Boot. However, enabling Secure Boot resulted in a blank screen.

Resetting the Secure Boot keys did not resolve the blank-screen behaviour.

Reducing the virtual processor count to one was also attempted, but Windows Setup required at least two processors.

The processor allocation was subsequently changed to three. Windows Setup then proceeded successfully.

**Outcome:** Windows 11 installation proceeded past the hardware compatibility check.

### 3.2 Windows initial setup

Windows Setup requested an internet connection during initial configuration.

The `OOBE\BYPASSNRO` command was attempted but returned a path-not-found error.

The command `start ms-cxh:localonly` was then used to open the local account creation interface. The setup process appeared temporarily stuck, but subsequently proceeded to the Windows desktop.

**Outcome:** A local Windows account was created and the Windows 11 Pro desktop became accessible.

### 3.3 Active Directory domain integration

WIN01 was subsequently reported to have successfully joined the `northstar.local` domain.

**Outcome:** Domain join confirmation was received.

**Verification still required:**
- Restart WIN01.
- Sign in using a domain account.
- Confirm the logged-in domain identity.
- Verify domain connectivity and DNS resolution.

## 4. Current Implementation Status

| Task | Status |
|---|---|
| Windows 11 Pro installation | Implemented |
| UEFI configuration | Implemented |
| TPM 2.0 configuration | Implemented |
| Secure Boot configuration | Implemented |
| Three-processor workaround | Implemented |
| Local account creation | Implemented |
| Domain join | Reported successful |
| Hostname verification | Pending |
| Domain-user sign-in | Pending |
| Network configuration verification | Pending |

## 5. Security Relevance

WIN01 represents an employee workstation within the simulated enterprise environment.

Its integration with Active Directory will provide the foundation for:
- Centralised identity and access management.
- Group Policy-based security configuration.
- Endpoint security monitoring.
- Security event collection through Wazuh.
- Controlled attack simulation and DFIR investigations.

## 6. Evidence to Capture

- VirtualBox VM configuration.
- Windows 11 Pro version information.
- Successful Windows desktop.
- Computer hostname.
- Domain membership confirmation.
- Successful domain-user sign-in after restart.
- `ipconfig /all` output.

Sanitise screenshots and command output before publishing them.

## 7. Notes

This record documents observed installation behaviour and reported outcomes. The cause of the Secure Boot blank-screen issue remains unconfirmed. No claim of formal compliance with any cybersecurity framework is made.
