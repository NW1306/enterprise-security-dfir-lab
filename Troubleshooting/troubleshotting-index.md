# Troubleshooting Register
## Northstar Technologies — Enterprise Security & DFIR Lab

This directory maintains a chronological record of technical issues encountered during the design, deployment and configuration of the Northstar Technologies Enterprise Security & DFIR Lab.

Each issue record documents:

- The observed problem.
- The environment and relevant configuration.
- Troubleshooting steps attempted.
- The outcome and current status.
- Root cause, where established.
- Lessons learned.

The purpose of this register is to maintain a transparent technical history of the lab implementation and provide a reference for future troubleshooting.

---

## Issue Register

| Issue ID | Description | Outcome | Status |
|---|---|---|---|
| ISSUE-001 | Windows Server installation error — License Terms not found | Original installation abandoned; replacement VM created | Workaround |
| ISSUE-002 | DC01 hostname and domain promotion considerations | Replacement server configured as DC01 and domain established | Rebuild completed |
| ISSUE-003 | Windows Administrator and DSRM password confusion | Password distinction identified; replacement VM used | Documented |
| ISSUE-004 | DC01 network configuration — APIPA address | User reported network issue resolved | Verification pending |
| ISSUE-005 | WIN01 Windows 11 installation and UEFI boot issues | Three-processor workaround allowed installation to proceed | Workaround successful |

---

## Additional Outstanding Issue

### Group Policy — Windows Defender Firewall

**Affected system:** WIN01  
**GPO:** `Northstar-Workstation-Baseline`

The effective firewall verification output displayed `NotConfigured` for the default inbound and outbound actions, instead of the intended `Block` and `Allow` values.

The issue remains under investigation. A dedicated troubleshooting record should be added once the policy investigation and corrective steps are completed.

---

## Recording Standards

1. Issue IDs must remain sequential.
2. Record actual observations rather than assumptions.
3. Do not claim a root cause unless it has been established.
4. Distinguish a successful workaround from a confirmed permanent resolution.
5. Include relevant command output or screenshots where available.
6. Update the issue status when additional troubleshooting or verification is completed.

---

**Project:** Northstar Technologies Enterprise Security & DFIR Lab  
**Repository branch:** `dev`
