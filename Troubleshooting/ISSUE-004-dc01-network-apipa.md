# ISSUE-004: DC01 Assigned an APIPA Address

## Issue Summary

| Field | Details |
|---|---|
| Issue ID | ISSUE-004 |
| System | DC01-Rebuild |
| Operating system | Windows Server 2022 |
| Component | IPv4 network configuration |
| Status | User-reported resolved; final verification evidence pending |
| Root cause | Not confirmed |

## Problem Description

During network configuration, DC01 was observed using an Automatic Private IP Addressing (APIPA) address:

`169.254.49.122`

An APIPA address in the `169.254.0.0/16` range is generally assigned when a Windows system cannot obtain an IPv4 address from a DHCP server.

The lab design required DC01 to use a static IPv4 address.

## Intended Network Configuration

| Setting | Intended value |
|---|---|
| IPv4 address | `10.10.10.10` |
| Subnet mask | `255.255.255.0` |
| Default gateway | Blank for the isolated lab, unless later configured |
| Preferred DNS | `10.10.10.10` |
| Alternate DNS | Not configured |
| VirtualBox network | Internal Network — `Northstar-Lab` |

## Troubleshooting Considerations

The following configuration areas are relevant when investigating an APIPA address:

1. Confirm that the VM's network adapter is enabled.
2. Confirm that the adapter is attached to the intended VirtualBox Internal Network.
3. Verify the exact internal network name on the relevant VMs.
4. Check the Windows network adapter and IPv4 configuration.
5. Configure the intended static IPv4 address.
6. Recheck the active adapter configuration.

These are diagnostic checks, not a record of confirmed root cause.

## Resolution Status

The user subsequently reported that the DC01 IP address issue had been resolved.

The intended configuration is:

- IP: `10.10.10.10`
- Subnet mask: `255.255.255.0`
- DNS: `10.10.10.10`

A final `ipconfig /all` output has not been included in the available evidence.

## Verification Required

Run the following command on DC01:

```powershell
ipconfig /all
```

Confirm that the active network adapter shows the intended static IPv4 address and DNS server, rather than an APIPA address.

Also check connectivity and DNS functionality as appropriate:

```powershell
ping 10.10.10.10
nslookup northstar.local
```

A successful ping to the server's own IP is not sufficient to establish that all network and DNS services are healthy.

## Lessons Learned

- Domain controllers should use stable static IP addresses in this lab design.
- APIPA addresses indicate that the expected network addressing configuration has not been obtained.
- Verify the correct VirtualBox network attachment before troubleshooting Windows network settings.
- Record the final output of `ipconfig /all` as implementation evidence.

## Final Status

The issue is reported as resolved by the user. Final configuration verification and supporting evidence remain to be recorded.
