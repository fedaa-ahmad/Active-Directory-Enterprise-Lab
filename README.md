# Active Directory Enterprise Lab

A professional, evidence-based portfolio project documenting the preparation and deployment of an isolated Windows Server Active Directory lab.

## Project overview

The lab is hosted on an HP ProLiant ML350 G6 using VMware ESXi 6.0 U3. The guest is Windows Server 2016 Datacenter. The intended first domain controller is **DC01** for the **corp.example.com** forest/domain, with NetBIOS name **CORP**. The lab is reported isolated from the production network and uses an independent internet connection. ZeroTier One is installed.

This repository records implementation progress without claiming unverified results. Current progress is based on the project owner’s report; verification evidence has not yet been uploaded.

## Current implementation status

| Work item | Status |
|---|---|
| ESXi virtual machine prepared | Reported complete |
| Lab isolated from production and connected to an independent internet path | Reported complete |
| Windows Server 2016 Datacenter installed and renamed DC01 | Reported complete |
| AD DS and DNS roles installed | Reported complete |
| New forest promotion for corp.example.com | **In Progress — successful completion not yet verified** |
| Domain/forest, services, DNS, and DC health checks | Pending |
| Users, groups, OUs, and Group Policy | Planned |

Promotion remains In Progress until the server completes promotion and restart and the verification checks pass. See the [DC01 installation and deployment guide](02-Installation/01-DC01-Installation.md).

## Learning objectives

- Prepare and isolate a virtualized Windows Server lab.
- Install and baseline Windows Server 2016 Datacenter.
- Deploy AD DS and DNS and validate domain controller health.
- Design OUs, users, groups, delegation, and Group Policy.
- Apply least privilege, secure administration, and auditing practices.
- Plan backup and recovery and troubleshoot directory and DNS issues.
- Use PowerShell with reviewable commands and evidence.

## Repository guide

| Path | Purpose |
|---|---|
| [01-Planning/](01-Planning/Lab-Overview.md) | Scope, requirements, infrastructure, and network design |
| [02-Installation/01-DC01-Installation.md](02-Installation/01-DC01-Installation.md) | Infrastructure preparation, ESXi, Windows, roles, promotion, verification, and troubleshooting |
| [02-Installation/screenshots/](02-Installation/screenshots/README.md) | Screenshot filename index for DC01 deployment evidence |
| [02-Installation/Windows-Server-2016.md](02-Installation/Windows-Server-2016.md) | Windows installation checklist and links to the implementation record |
| [03-Active-Directory/AD-DS-and-DNS.md](03-Active-Directory/AD-DS-and-DNS.md) | AD DS and DNS deployment status and checks |
| [Screenshots/](Screenshots/README.md) | Gallery of the first three supplied Windows Server installation screenshots |
| [04-Identity-Design/](04-Identity-Design/README.md) | Planned users, groups, OUs, and GPO design |
| [05-Security/](05-Security/README.md) | Security baseline and administration practices |
| [06-Backup-Recovery/](06-Backup-Recovery/README.md) | Backup and recovery planning |
| [07-Troubleshooting/](07-Troubleshooting/README.md) | Diagnostic workflows and issue guidance |
| [scripts/](scripts/README.md) | PowerShell scripts and safe-use guidance |
| [evidence/](evidence/README.md) | Sanitized project evidence guidance |

## Documentation and evidence standards

Statuses are **Planned**, **In Progress**, **Reported complete**, and **Completed (verified)**. Owner-reported completion is not independent verification. Mark a task Completed (verified) only after its checks pass and dated, sanitized evidence is linked.

The repository is public. Never publish passwords, credentials, product keys, recovery secrets, access tokens, service account details, ZeroTier credentials or network identifiers, production IP addresses, or real network configurations. Exact network settings remain in a private record. Any sample addressing must use documentation-only ranges and be clearly labeled as fictional.

No actual server configuration is changed by this documentation. The project record describes reported actions and planned verification only.

## Safety and scope

Keep the lab isolated from production and restrict administration to trusted lab access. Do not expose ESXi management, Windows management, or directory services to the public internet. Treat snapshots as convenience only; they do not replace supported Active Directory system-state backup. Windows Server 2016 and ESXi 6.0 U3 are legacy releases; this project is a learning lab, and lifecycle/support should be evaluated before any production use.

## Start here

1. Review the [lab overview](01-Planning/Lab-Overview.md), [requirements](01-Planning/Requirements.md), and [network design](01-Planning/Network-Design.md).
2. Follow the [DC01 installation and promotion record](02-Installation/01-DC01-Installation.md).
3. Keep promotion marked In Progress until post-restart verification passes.
4. Review the new [installation screenshot gallery](Screenshots/README.md) and add only genuine, sanitized project evidence.

See [LICENSE](LICENSE) for repository licensing.
