# Troubleshooting FAQ

This document records explanations for recurring technical issues encountered while building the Northstar Technologies Enterprise Security & DFIR Lab.

## 1. What does an APIPA address mean?

An IPv4 address beginning with `169.254` is generally an Automatic Private IP Addressing (APIPA) address.

Windows may assign one when it cannot obtain an IPv4 address from a DHCP server.

In this lab, DC01 is intended to use a static IP address, so an APIPA address indicates that the intended network configuration needs to be checked.

## 2. Why does DC01 need a static IP address?

DC01 provides core Active Directory and DNS services.

Other domain-joined machines depend on being able to locate the domain controller consistently.

A stable IP address makes DNS configuration and domain connectivity more predictable.

The intended address is:

`10.10.10.10/24`

## 3. What is the difference between the Administrator and DSRM passwords?

The Administrator password is used for normal administrative sign-in.

The Directory Services Restore Mode (DSRM) password is a separate recovery credential configured during domain controller promotion.

The DSRM password is used when starting a domain controller in Directory Services Restore Mode. It is not the normal everyday Administrator password.

## 4. Why should a server be renamed before domain controller promotion?

The server hostname is part of the server's identity in the environment.

Configuring the intended hostname before promotion helps establish a consistent naming structure and reduces the need for later identity changes.

For this lab, the intended hostname is `DC01`.

## 5. Why did Windows 11 Setup reject the one-processor configuration?

Windows 11 has a minimum processor requirement that includes at least two processor cores.

In this lab, the one-processor VM configuration was rejected by Setup. Changing the VM allocation to three processors allowed Setup to proceed.

The observed workaround should not be treated as proof of the root cause of the earlier boot issue.

## 6. Why did Secure Boot cause a blank screen in the WIN01 VM?

The blank-screen behaviour occurred when Secure Boot was enabled with EFI.

Several configuration changes were attempted, including resetting Secure Boot keys and changing EFI/Secure Boot settings.

The exact cause was not established. The successful installation workaround was to allocate three processors, after which Setup proceeded.

Do not generalise this result to every VirtualBox Windows 11 VM.

## 7. Why was a local account created during Windows 11 setup?

Windows 11 OOBE requested an internet connection.

The command `OOBE\BYPASSNRO` did not work in the observed environment. The command `start ms-cxh:localonly` opened the local account creation interface, allowing setup to continue.

WIN01 was subsequently joined to the `northstar.local` domain.

## 8. What does `NotConfigured` mean in effective Group Policy settings?

`NotConfigured` indicates that the particular policy setting is not being set by the effective policy result being viewed.

For the Northstar workstation baseline, the expected Windows Defender Firewall default inbound and outbound actions did not appear as `Block` and `Allow` in the effective settings.

The policy application and configuration therefore require further investigation. A GPO being created and linked does not, by itself, prove that the intended settings are being applied to WIN01.

## 9. Does a successful domain join prove that every domain service works?

No.

A successful domain join is useful evidence that the workstation was able to communicate with the domain controller sufficiently to complete the join.

It does not independently prove that every DNS record, Group Policy setting, authentication workflow, or domain service is functioning correctly.

Each relevant service should be tested separately.

## 10. What is the difference between a workaround and a root-cause resolution?

A workaround allows the task to proceed without necessarily identifying or eliminating the underlying cause.

A root-cause resolution requires evidence that the actual cause has been identified and corrected.

For example, changing WIN01 to three virtual processors allowed Windows Setup to proceed. That is a confirmed observed workaround, but the underlying cause of the earlier blank-screen behaviour remains unknown.

## 11. What evidence should be retained for troubleshooting?

Useful evidence includes:

- Exact error messages.
- Relevant VM configuration settings.
- Command output.
- Screenshots of the affected configuration.
- Before-and-after results.
- The corrective action taken.
- Verification results.

Sensitive information such as passwords, private keys, tokens, and personal data must be excluded.

## 12. How should troubleshooting records be maintained?

Each significant issue should receive a unique ID.

A record should include:

1. Issue summary.
2. Affected system and component.
3. Observed symptoms.
4. Relevant environment and configuration.
5. Troubleshooting actions.
6. Actual outcome.
7. Root-cause assessment.
8. Verification evidence.
9. Lessons learned.
10. Final status.

Do not label an issue resolved unless the result has been verified or clearly identify it as user-reported.
