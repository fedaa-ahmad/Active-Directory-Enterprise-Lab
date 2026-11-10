# Windows Server 2016 Installation and Baseline

**Status: Planned.** No installation completion is claimed.

## Before installation

- Validate host and hypervisor compatibility, capacity, firmware, storage, and virtualization settings.
- Obtain legitimate Windows Server 2016 Datacenter media and record its source and checksum locally; never commit license keys.
- Confirm licensing/evaluation terms and the security implications of this legacy OS.
- Resolve the network worksheet and verify lab isolation before connecting the VM NIC.
- Verify VM name and resource allocation. Existing notes propose AD-Test, 16 vCPU, 16 GB RAM, and 120 GB storage; confirm these values against actual capacity and requirements.
- Define a secure local administrator credential and store it in an approved password manager, never in this repository.

## Installation outline

1. Create a VM with approved virtual hardware and an isolated network attachment.
2. Attach verified installation media and install Windows Server 2016 Datacenter using the selected option (Desktop Experience or Server Core); record the choice.
3. Set a unique computer name. Keep the server in a workgroup during initial baseline; do not promote it to a domain controller.
4. Apply approved updates from a trusted source; restart as required and record date, build, and patch level.
5. Configure time zone and time source per the lab plan.
6. Configure static addressing only after subnet, prefix, gateway, and DNS are reconciled. Verify routing and name resolution.
7. Enable only required management services, restrict access to the admin segment, and record firewall posture.
8. Configure monitoring/logging and an initial recovery method. A VM snapshot is not a backup.
9. Capture sanitized evidence and complete the checklist.

## Baseline checklist

| Check | Status | Evidence / date |
| --- | --- | --- |
| Media provenance and edition recorded | Planned | |
| VM isolated from production | Planned | |
| OS installation and hostname verified | Planned | |
| Patch level and restart state recorded | Planned | |
| IP, prefix, gateway, DNS, and time verified | Planned | |
| Local administrator access protected | Planned | |
| Firewall and remote management reviewed | Planned | |
| Backup/recovery approach documented | Planned | |

Only mark a row **Completed (verified)** after recording evidence and validation. Redact details that expose sensitive information.
