# Lab Overview

## Project purpose

This portfolio documents the design, deployment, administration, and security of an isolated Active Directory learning environment. It records progress with clear status labels and sanitized evidence.

## Infrastructure inventory

| Layer | Reported specification | Status |
|---|---|---|
| Physical server | HP ProLiant ML350 G6 | In use for lab |
| Hypervisor | VMware ESXi 6.0 U3 | VM prepared |
| Guest OS | Windows Server 2016 Datacenter | Installed |
| Domain controller hostname | DC01 | Renamed |
| Forest/domain | corp.example.com | New forest promotion In Progress; not verified successful |
| NetBIOS name | CORP | Intended value; verify after promotion |
| Connectivity | Lab isolated from production; independent Starlink connection | Owner reported complete |
| Overlay networking | ZeroTier One installed | Adapter and DNS behavior require review |

## Current progress

The owner reports that the ESXi virtual machine was prepared, the lab server isolated from production and connected to an independent Starlink path, Windows Server installed and renamed DC01, and AD DS and DNS roles installed. Promotion was started, with a new forest corp.example.com selected. Promotion is **In Progress** until the wizard completes, the server restarts, and the domain, forest, services, DNS, and health checks are recorded.

No verification screenshots or command output have been uploaded. This status is an owner report, not an independent audit.

## Network disclosure

The public repository contains no live addressing, subnet, gateway, DNS server, VLAN, route, MAC, Starlink account, or ZeroTier network details. Maintain exact network configuration privately. See [Network Design](Network-Design.md) for the logical design and disclosure rules.

## Learning objectives

- Build an isolated virtualized Windows Server environment.
- Install and baseline Windows Server and directory services.
- Validate AD DS, DNS, domain controller health, and name resolution.
- Design identity structure, Group Policy, and delegated administration.
- Apply security controls and document operational decisions.
- Plan backup, recovery, and troubleshooting procedures.

## Related documentation

- [Requirements](Requirements.md)
- [Network Design](Network-Design.md)
- [DC01 Installation and Domain Deployment](../02-Installation/01-DC01-Installation.md)
