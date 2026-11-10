# Lab Requirements

## Scope

This document records the lab platform and operational requirements. Reported implementation is summarized separately from items that still need validation. Exact network configuration and credentials are maintained outside this public repository.

## Platform inventory

| Component | Requirement or reported value | Status |
|---|---|---|
| Physical host | HP ProLiant ML350 G6 | In use for lab |
| Hypervisor | VMware ESXi 6.0 U3 | VM prepared |
| Guest OS | Windows Server 2016 Datacenter | Installed |
| Hostname | DC01 | Renamed (reported) |
| Forest/domain | corp.example.com | Promotion started; not verified complete |
| NetBIOS name | CORP | Intended; verify after promotion |
| Internet path | Independent Starlink connection | Reported connected; details private |
| Overlay | ZeroTier One installed | Review adapter effects before validating AD DNS |

## Operational requirements

- Keep the lab isolated from production.
- Restrict management access to trusted lab administration.
- Maintain private records for real addresses, routes, DNS, and access details.
- Use stable server addressing selected from the private lab plan.
- Keep credentials, DSRM secrets, recovery keys, and service tokens out of GitHub.
- Capture sanitized evidence and date verification results.
- Use supported system-state backup before relying on the domain for anything important.

## Status convention

**Reported complete** means the project owner says the work was done. **Completed (verified)** requires validation and dated sanitized evidence. The server installation, rename, roles, VM preparation, isolation, and separate internet connection are reported complete. Forest promotion is **In Progress**; post-restart validation remains pending.

See [Lab Overview](Lab-Overview.md), [Network Design](Network-Design.md), and the [DC01 installation record](../02-Installation/01-DC01-Installation.md).
