# ISSUE-003: Windows Administrator and DSRM Password Confusion

## Issue Summary

| Field | Details |
|---|---|
| Issue ID | ISSUE-003 |
| System | Initial Windows Server VM |
| Operating system | Windows Server 2022 |
| Component | Windows authentication and recovery credentials |
| Status | Documented; original VM superseded |
| Root cause | Credential distinction misunderstood |

## Problem Description

During the initial Windows Server setup, the normal Windows Administrator password was forgotten.

The Directory Services Restore Mode (DSRM) password had also been configured during the Active Directory Domain Services promotion process.

The distinction between these two credentials caused confusion during recovery attempts.

## Technical Explanation

Windows Server uses different credentials for different purposes.

### Administrator account

The local or domain Administrator account is used for normal administrative access, depending on the server's current role and logon context.

### DSRM password

The Directory Services Restore Mode password is a separate recovery credential configured when promoting a server to a domain controller.

It is used to access the domain controller in Directory Services Restore Mode for directory-service maintenance and recovery.

**Important:** The DSRM password is not a replacement for the normal Administrator password during everyday Windows sign-in.

## Action Taken

The original virtual machine was eventually superseded by the replacement server build.

No successful password recovery on the original VM was established in the available project record.

## Preventive Measures

- Store administrative credentials securely.
- Maintain a secure record of the DSRM password separately from normal administrative credentials.
- Never store passwords in GitHub repositories, screenshots, or project documentation.
- Verify administrative access after installation and before proceeding with server-role configuration.
- Ensure recovery credentials are accessible through an appropriate secure password-management process.

## Security Considerations

Domain controller recovery credentials are sensitive.

They should never be committed to source control, even in a private repository.

## Final Status

The distinction between the Administrator and DSRM credentials has been documented. The original VM was superseded. No claim is made that the original Administrator password was recovered.
