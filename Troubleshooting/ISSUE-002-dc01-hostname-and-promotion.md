# ISSUE-002: DC01 Hostname and Domain Controller Promotion

## Issue Summary

| Field | Details |
|---|---|
| Issue ID | ISSUE-002 |
| System | Initial domain controller VM and DC01-Rebuild |
| Operating system | Windows Server 2022 |
| Component | Hostname configuration and Active Directory Domain Services |
| Status | Rebuild completed; original VM retired |
| Root cause | Original configuration sequence documented; exact technical failure not established |

## Background

During the initial domain controller setup, the Windows Server machine had not been renamed to the intended hostname `DC01` before the domain controller configuration process was attempted.

The intended hostname for the lab's domain controller was `DC01`.

## Intended Configuration

| Setting | Intended value |
|---|---|
| Hostname | `DC01` |
| Domain | `northstar.local` |
| Static IPv4 address | `10.10.10.10` |
| Subnet mask | `255.255.255.0` |
| DNS server | `10.10.10.10` |
| Roles | Active Directory Domain Services and DNS |

## Action Taken

The original virtual machine was not retained for the final lab configuration.

A replacement VM named `DC01-Rebuild` was created. Windows Server 2022 was installed, and the server was configured with the intended hostname `DC01`.

Active Directory Domain Services and DNS were subsequently configured, and the server was promoted to a domain controller for the new forest:

`northstar.local`

## Outcome

The replacement server became the domain controller used in the current lab.

The original VM was superseded by the rebuild.

## Root Cause Analysis

The original setup sequence did not establish the intended hostname before domain controller configuration was attempted.

However, the available record does not establish that this alone caused a specific promotion failure. No unsupported root-cause conclusion is made.

## Lessons Learned

- Configure and verify the server hostname before promoting a server to a domain controller.
- Configure the intended static IP address and DNS settings before AD DS promotion.
- Record the server's identity and network configuration before installing server roles.
- Use a clean rebuild when the original VM's configuration becomes unreliable, while retaining the troubleshooting history.

## Evidence

Evidence to retain:

- Windows Server hostname output (`hostname`).
- `ipconfig /all` output.
- Server Manager showing AD DS and DNS roles.
- Active Directory Users and Computers showing the domain.
- DNS Manager showing the relevant DNS zone.

## Final Status

The replacement DC01 configuration and domain creation are reported as completed. The original VM was superseded. The original promotion attempt's precise failure mechanism remains unconfirmed.
