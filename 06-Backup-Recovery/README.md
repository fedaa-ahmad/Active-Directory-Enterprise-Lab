# Backup and Recovery Plan

**Status: Planned.** No backup or restore has been completed or tested.

## Planning requirements

Before deploying AD DS, choose a backup destination separate from the VM datastore; define access controls, encryption, retention, monitoring, and ownership. Protect backup credentials independently. A hypervisor snapshot may support a short maintenance rollback but is not a substitute for supported system-state and file-level backups.

## Future protection scope

- Windows Server system state, including AD DS data if the server later becomes a domain controller.
- System volume and any separate volumes containing directory-related or lab data.
- DNS/AD configuration and recovery documentation, with no secrets in Git.
- Hypervisor configuration and VM inventory needed to rebuild the lab.

Use a backup product and procedure supported for the selected Windows Server and AD DS version. Confirm application-aware handling and authoritative/non-authoritative restore requirements with current Microsoft guidance before directory recovery.

## Recovery runbook outline

1. Declare the incident and identify the failed component and recovery point.
2. Isolate the affected VM if compromise is suspected; preserve logs and avoid overwriting evidence.
3. Confirm backup integrity, date, scope, and compatibility.
4. Restore using the supported recovery method for the failure scenario; do not improvise a domain controller restore from a copied VM disk.
5. Validate OS health, AD DS, DNS, time, SYSVOL, authentication, and replication if more than one DC is ever deployed.
6. Record recovery time, data loss window, validation results, and follow-up actions.

## Restore test record

| Date | Scenario | Backup point | Result | Evidence | Follow-up |
| --- | --- | --- | --- | --- | --- |
| — | No restore test recorded | — | Not run | — | Plan a test before claiming recoverability |
