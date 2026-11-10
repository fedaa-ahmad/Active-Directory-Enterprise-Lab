# Troubleshooting Runbook

**Status: Planned reference.** Record symptoms and evidence before changing configuration.

## General workflow

1. Define symptom, scope, start time, and recent changes.
2. Check virtual link/network attachment, IP, prefix, gateway, DNS, and time.
3. Test name resolution separately from IP connectivity; identify which resolver answered.
4. Check relevant services and event logs; preserve timestamps and exact error text.
5. Make one controlled change at a time, then repeat the failing test and record results.
6. Escalate or roll back if directory health worsens. Avoid destructive repair commands without a verified backup and scenario-specific plan.

## Common diagnostic areas

| Symptom | First checks | Useful tools (as applicable) |
| --- | --- | --- |
| Cannot reach server | VM network/port group, link, IP/prefix, gateway, route, firewall | `ipconfig /all`, `ping`, `tracert`, `route print` |
| Names fail to resolve | Configured DNS server, suffix, zone/record, reachability, forwarders | `ipconfig /all`, `nslookup`, `Resolve-DnsName` |
| Domain join or logon fails | Client uses AD DNS, time skew, domain service records, account status, secure channel | `nltest`, `w32tm`, `Test-ComputerSecureChannel` |
| GPO not applied | OU placement, link/enforcement, security filtering, replication, client processing/events | `gpresult`, `gpupdate`, Group Policy event logs |
| Directory health warning | System/DNS/Directory Service logs, time, storage, SYSVOL, replication topology | `dcdiag`, `repadmin` where applicable |

Commands are examples for later diagnosis, not evidence that a domain controller exists. Run elevated commands only with appropriate authorization and review their impact first.

## Incident record template

```text
Date/time and timezone:
System / role:
Observed symptom:
Scope and impact:
Recent changes:
Tests and exact results:
Changes made and rollback:
Resolution / validation:
Evidence location (sanitized):
```
