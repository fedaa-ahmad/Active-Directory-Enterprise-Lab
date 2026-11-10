# Security Baseline

**Status: Planned.** This is a control checklist, not a claim that controls have been applied.

## Lab boundary

- Isolate virtual networking from production and the public internet by default.
- Permit only documented update and administration paths.
- Use synthetic identities and data; do not copy production objects or credentials.
- Use supported host firmware/hypervisor where practical. Windows Server 2016 is a legacy platform; restrict it to an isolated learning environment and consult current vendor lifecycle guidance.

## Administration

- Use separate daily and administrative accounts where practical.
- Apply least privilege; avoid routine use of highly privileged directory accounts.
- Restrict remote administration to a trusted management segment and required operators.
- Protect secrets in an approved password manager; never place passwords, tokens, keys, recovery keys, or license keys in scripts or Git.
- Review privileged group membership and remove temporary access promptly.

## Host and directory controls

- Patch from trusted sources and record patch status.
- Enable the host firewall and only required services/protocols.
- Use strong authentication and secure credential handling appropriate to this isolated legacy lab.
- Enable relevant security auditing; define log retention and review cadence.
- Document account lifecycle, lockout, service account, delegation, and GPO change processes before implementation.
- Store backups offline or access-controlled and test restore procedures.

## Review record

| Control | Status | Evidence / exception |
| --- | --- | --- |
| Lab isolation checked | Planned | |
| Admin access restricted | Planned | |
| Patch status recorded | Planned | |
| Firewall/services reviewed | Planned | |
| Audit/log retention defined | Planned | |
| Privileged access reviewed | Planned | |
| Backup protected and restore tested | Planned | |
