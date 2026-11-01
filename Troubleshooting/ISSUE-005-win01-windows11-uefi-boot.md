# ISSUE-005: WIN01 Windows 11 Installation and UEFI Boot Issues

## Issue Summary

| Field | Details |
|---|---|
| Issue ID | ISSUE-005 |
| System | WIN01 |
| Operating system | Windows 11 Pro |
| Virtualisation platform | Oracle VirtualBox 7.2.22 |
| Component | UEFI, Secure Boot, TPM and Windows 11 installation |
| Status | Workaround successful; installation completed |
| Root cause | Not confirmed |

## Environment

- VirtualBox version: `7.2.22 r175245 (Qt6.8.0 on Windows)`
- VM name: `WIN01`
- Guest OS: Windows 11 Pro
- Network: `Northstar-Lab`
- Intended IP: `10.10.10.20`
- Intended DNS: `10.10.10.10`

## Problem 1: Windows 11 Hardware Compatibility Check

Windows 11 Setup reported hardware compatibility requirements involving TPM 2.0 and Secure Boot.

The VM was configured with EFI/UEFI, TPM 2.0 and Secure Boot settings.

## Problem 2: Blank Screen with Secure Boot Enabled

When Secure Boot was enabled alongside EFI, the VM displayed a blank screen during startup.

Disabling Secure Boot allowed Windows Setup to start, but the Windows 11 hardware compatibility check then failed.

Disabling EFI did not resolve the issue.

Resetting Secure Boot keys was also attempted, but the blank-screen issue persisted.

## Problem 3: Processor Allocation

A configuration with one virtual processor was attempted.

Windows Setup rejected the configuration because it did not meet the minimum processor requirement.

The VM processor allocation was subsequently changed to three processors.

**Observed outcome:** Windows Setup then passed the hardware compatibility check and installation proceeded.

This is a successful workaround observed in this environment. It does not establish that processor allocation was the sole root cause of the earlier boot and compatibility problems.

## Problem 4: Local Account Setup During OOBE

During Windows 11 out-of-box experience (OOBE), Setup requested an internet connection.

The following command was attempted:

```cmd
OOBE\BYPASSNRO
```

It returned:

```text
The system cannot find the path specified.
```

The following command was then used:

```cmd
start ms-cxh:localonly
```

This opened the local account creation interface.

The setup initially appeared stuck while the network setup window remained in the background. The user subsequently confirmed that setup had completed and the Windows desktop was available.

A local account was created.

## Final Configuration Status

The user confirmed the following:

- Windows 11 Pro installed.
- Hostname verified as `WIN01`.
- Network settings verified.
- Domain join to `northstar.local` verified.
- Local account created.
- Three-processor workaround used successfully.

The intended network configuration is:

| Setting | Value |
|---|---|
| IPv4 address | `10.10.10.20` |
| Subnet mask | `255.255.255.0` |
| Preferred DNS | `10.10.10.10` |
| Domain | `northstar.local` |

## Lessons Learned

- Windows 11 virtual machine configuration requires attention to supported hardware and firmware settings.
- Confirm EFI, TPM and Secure Boot configuration before installation.
- Ensure the VM has sufficient virtual processors and memory.
- Record configuration changes and the observed result after each change.
- Do not assume that a successful workaround identifies the root cause.
- Confirm Windows edition before attempting a traditional Active Directory domain join.

## Evidence

Evidence to retain:

- VirtualBox WIN01 processor and firmware settings.
- Windows 11 edition information.
- Hostname output.
- `ipconfig /all` output.
- Successful domain membership evidence.
- Successful domain sign-in or computer object evidence, where appropriate.

Do not include passwords or other credentials in evidence.

## Final Status

WIN01 is installed with Windows 11 Pro, its hostname and network configuration have been verified, and its domain join has been confirmed by the user.

The three-processor change allowed Setup to proceed. The underlying cause of the earlier UEFI/Secure Boot behaviour remains unconfirmed.
