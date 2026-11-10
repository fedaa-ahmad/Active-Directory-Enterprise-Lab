# Active Directory Enterprise Lab

Portfolio project for planning, building, administering, and securing a Windows Server Active Directory lab. This repository is the project record: documentation describes intended work, while implementation evidence will be added only after a task has actually been completed and verified.

> **Current status:** Planning / in progress. The existing planning notes list a Windows Server 2016 Datacenter virtual machine and proposed network values. Those values have not been independently verified. No domain controller promotion or completed AD configuration is claimed.

## Learning objectives

- Plan an isolated, supportable Windows Server lab and document its network.
- Install and baseline Windows Server 2016.
- Deploy and validate Active Directory Domain Services (AD DS) and DNS.
- Design OUs, users, groups, delegation, and Group Policy for a small enterprise.
- Apply least privilege, secure administration, and auditing practices.
- Plan backups, test recovery, and troubleshoot common identity and DNS failures.
- Use PowerShell carefully, with readable scripts and verification steps.

## Repository map

| Path | Purpose |
| --- | --- |
| `01-Planning/` | Scope, requirements, and network design |
| `02-Installation/` | Windows Server installation and baseline checklist |
| `03-Active-Directory/` | AD DS and DNS deployment guide and validation record |
| `04-Identity-Design/` | Planned OU, user, group, and GPO design worksheets |
| `05-Security/` | Security baseline and administration practices |
| `06-Backup-Recovery/` | Backup and recovery plan and test evidence |
| `07-Troubleshooting/` | Diagnostic workflow and issue runbook |
| `scripts/` | PowerShell scripts; review before running |
| `evidence/` | Future sanitized screenshots, command output, and test records |

## Project status

| Workstream | Status |
| --- | --- |
| Planning and inventory | In progress; existing values require validation |
| Windows Server installation | Planned; no completion evidence recorded |
| AD DS and DNS | Planned; server must not be promoted until prerequisites are validated |
| Users, groups, OUs, and GPO | Design documentation prepared; implementation planned |
| Security, backup, recovery, troubleshooting | Documentation prepared; lab validation planned |

Use the status labels **Planned**, **In progress**, **Completed (verified)**, and **Blocked**. A task is completed only when its evidence, date, and validation result are recorded. Do not commit passwords, recovery keys, private IPs from a production environment, or unredacted personal data.

## Start here

1. Read [the lab overview](01-Planning/Lab-Overview.md), [requirements](01-Planning/Requirements.md), and [network design](01-Planning/Network-Design.md).
2. Resolve the network questions and confirm the lab is isolated before installing anything.
3. Follow the [Windows Server installation guide](02-Installation/Windows-Server-2016.md).
4. Record evidence and pass the prerequisite checklist in the [AD DS and DNS guide](03-Active-Directory/AD-DS-and-DNS.md) before any future promotion.

## Safety and scope

This is a lab plan, not a record of a deployed domain. Use a non-production isolated virtual network, snapshots only as a convenience (not as a substitute for system-state backup), and synthetic accounts and data. Windows Server 2016 is a legacy platform; use it only in an isolated learning environment and consult current vendor lifecycle/security guidance before any real deployment.

## Existing project notes

The original [lab overview](01-Planning/Lab-Overview.md) is retained and expanded. Its listed hardware, VM sizing, and IP/DNS values are treated as **proposed inputs**, not verified live configuration. In particular, the listed address `192.168.2.250` and gateway `192.168.3.1` appear to be in different /24 networks, and the two listed DNS addresses are in `192.168.44.0/24`; the intended subnet, mask, routing, and DNS design must be confirmed before use.

## License

See [LICENSE](LICENSE).
