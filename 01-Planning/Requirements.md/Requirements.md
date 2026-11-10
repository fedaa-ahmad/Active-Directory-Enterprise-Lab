# Lab Requirements and Scope

**Status: Planned.** This document records requirements and decisions to verify; it does not assert that equipment is available or configured.

## Goals

Build a small, isolated enterprise-style identity lab to practice Windows Server installation, AD DS, DNS, identity organization, Group Policy, security administration, backup, recovery, and troubleshooting. Keep implementation evidence separate from plans.

## Proposed environment from existing notes

| Item | Existing planning note | Verification needed |
| --- | --- | --- |
| Hypervisor | VMware ESXi 6.0 U3 | Confirm version, compatibility, support status, and available resources |
| Physical host | HP ProLiant ML350 G6 | Confirm CPU virtualization support, firmware, RAM, storage, and NICs |
| VM name | AD-Test | Confirm intended naming convention |
| Guest OS | Windows Server 2016 Datacenter | Confirm licensed installation media, edition, patch source, and evaluation/licensing terms |
| vCPU / memory / disk | 16 vCPU / 16 GB / 120 GB | Confirm host capacity and whether sizing suits the chosen roles |
| Network | Static address noted as 192.168.2.250 | Confirm subnet/prefix, gateway, VLAN/port group, DNS, and isolation |

These values are transcribed from the original planning file and are not a recommendation or evidence of deployment.

## Functional requirements

- A reproducible installation and baseline checklist.
- A documented AD DS forest/domain naming decision before deployment.
- DNS resolution design and validation steps.
- A proposed OU hierarchy, user/group conventions, and GPO design worksheets.
- Security, backup, recovery, and troubleshooting procedures.
- PowerShell scripts that are safe by default, parameterized, and reviewed before execution.
- Evidence records for every task marked completed.

## Non-functional and safety requirements

- Keep the lab isolated from production networks and identities.
- Use synthetic identities and non-sensitive test data.
- Apply least privilege; use separate administrative accounts where practical.
- No real credentials, secrets, recovery keys, or production data in Git.
- Do not promote the server to a domain controller as part of this documentation change.
- Validate host support and legacy OS security/lifecycle constraints before operating the lab.

## Decisions still required

Record decisions with a date and rationale before implementation:

| Decision | Status | Decision / evidence |
| --- | --- | --- |
| Lab isolation method and virtual switch/port group | Open | |
| IP subnet, prefix, gateway, and DNS forwarders | Open | |
| Internal AD DNS name and NetBIOS name | Open | |
| Time source and time-zone policy | Open | |
| VM sizing and storage layout | Open | |
| Backup destination and retention | Open | |
| Client VM(s) and validation scenarios | Open | |
