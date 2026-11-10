# DC01 Installation and Domain Deployment

**Project:** Active Directory Enterprise Lab  
**Document status:** Implementation record in progress  
**Last updated:** 2026-11-10

## Purpose and status

This guide records the reported build of the first domain controller. The infrastructure and Windows/role installation steps below are **reported complete** by the project owner. Promotion to a new forest remains **In Progress** until post-restart checks pass and evidence is recorded. No screenshots or command output proving completion are attached yet.

| Component | Current record |
|---|---|
| Physical server | HP ProLiant ML350 G6 |
| Hypervisor | VMware ESXi 6.0 U3 |
| Guest OS | Windows Server 2016 Datacenter |
| Server name | DC01 (reported renamed) |
| Intended forest and domain | corp.example.com |
| Intended NetBIOS name | CORP |
| Connectivity | Independent Starlink connection; ZeroTier One installed |
| AD DS and DNS roles | Reported installed |
| New-forest promotion | **In Progress — not yet verified successful** |

> Security: never publish production IP addresses, real network configuration, credentials, Starlink account details, ZeroTier network IDs, or tokens. IPs in examples are documentation-only and must not be copied into the live lab.

## Implementation record

Statuses distinguish owner-reported actions from verified results. Attach sanitized evidence using the [screenshots index](screenshots/README.md); evidence is currently Pending upload.

| Step | Status | Record |
|---|---|---|
| Prepare ESXi virtual machine | Reported complete | VM prepared on ESXi 6.0 U3. Resource allocation and virtual hardware details are not recorded. |
| Isolate lab from production | Reported complete | Lab server isolated from production; underlying topology and addressing are omitted. |
| Connect to independent internet | Reported complete | Independent Starlink connection reported; service/account identifiers omitted. |
| Install Windows Server 2016 Datacenter | Reported complete | Guest OS installed. |
| Rename server to DC01 | Reported complete | Hostname reported as DC01. |
| Install AD DS and DNS roles | Reported complete | Role installation reported. |
| Promote as first DC in new forest | **In Progress** | New forest corp.example.com selected and promotion started; successful completion and reboot are not confirmed. |
| Validate domain, forest, services, DNS, and DC health | Planned | Run the checks below after promotion and save sanitized results. |

## 1. Infrastructure preparation

Confirm physical host capacity, storage, time source, and restricted management access. Maintain isolation from production at physical and virtual network layers. The isolation and separate internet path above are owner-reported; this page intentionally omits the real design. Do not expose ESXi management, Windows management, or directory services to the public internet. Maintain a rollback plan. VM snapshots are useful for convenience but do not replace supported AD system-state backup.

## 2. VMware ESXi virtual machine

Reported platform: VMware ESXi 6.0 U3 on an HP ProLiant ML350 G6; guest: Windows Server 2016 Datacenter. The VM was prepared. CPU, memory, storage, firmware, virtual NIC, port group, and datastore settings were not provided as sanitized verified facts, so they are omitted. For future evidence, capture a sanitized VM summary and the lab port group. Confirm no unintended bridge to production and document permitted egress privately. Check vendor compatibility and support before using this legacy platform beyond an isolated learning lab.

## 3. Windows Server installation

Windows Server 2016 Datacenter installation is reported complete. A repeatable deployment uses trusted media, the licensed Datacenter edition, a planned system volume, a unique local Administrator password stored securely outside GitHub, and appropriate updates. Configure the private lab network from the private design record and verify no unintended production path. Do not commit product keys, credentials, or screenshots exposing activation information.

## 4. Rename the server to DC01

Rename to DC01 before promotion and restart when prompted. The rename is reported complete. To verify locally:

~~~powershell
$env:COMPUTERNAME
Get-CimInstance Win32_ComputerSystem | Select-Object Name, Domain, PartOfDomain
~~~

Expected before promotion: name DC01 and not yet domain joined. Keep output sanitized. This documentation task does not change the live server.

## 5. Install AD DS and DNS roles

AD DS and DNS Server roles are reported installed. Installing roles alone does not create a forest or prove that a healthy domain controller exists. The promotion and verification are separate. Reference: [Microsoft Learn — Install a new Active Directory forest](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/install-a-new-windows-server-2012-active-directory-forest--level-200-).

## 6. Promote DC01 into a new forest

The promotion wizard was started and **New forest** with root domain name **corp.example.com** was selected. Promotion remains **In Progress**. Do not mark deployment complete until the wizard finishes, DC01 restarts, and verification succeeds.

Review the forest/domain names, select functional levels based on planned domain controllers and compatibility, review DNS and Global Catalog options, set the Directory Services Restore Mode (DSRM) password securely, inspect prerequisite results, then review and start installation. Never record or screenshot the DSRM password. The functional level selected in this deployment has not been verified; record it from the wizard or completed forest.

A DNS delegation warning can be expected when no accessible parent DNS zone exists. It does not by itself mean promotion failed; review it against the intended hierarchy. Microsoft describes this in [AD DS Configuration Wizard page descriptions](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/ad-ds-installation-and-removal-wizard-page-descriptions).

## 7. Post-promotion verification

After the wizard completes and the server restarts, run these commands in elevated PowerShell. The AD cmdlets require the Active Directory PowerShell module. Sanitize results before publishing.

~~~powershell
Get-ADDomain
Get-ADForest
Get-Service NTDS,DNS,Netlogon,KDC
~~~

Then run diagnostics and query the domain name:

~~~powershell
dcdiag
nslookup corp.example.com
~~~

| Check | Expected evidence | Status |
|---|---|---|
| Get-ADDomain | Domain name corp.example.com; sanitized output recorded | Pending |
| Get-ADForest | Forest root corp.example.com; functional level recorded | Pending |
| Get-Service NTDS,DNS,Netlogon,KDC | Services exist and are Running after promotion | Pending |
| dcdiag | Review all tests; resolve failures and retain sanitized results | Pending |
| nslookup corp.example.com | Intended lab DNS answers for the domain; do not publish returned real address | Pending |
| Restart confirmation | DC01 restarted and loads normally after promotion | Pending |

Update statuses with date, result, and redacted evidence. Only then change promotion to **Completed (verified)**.

## 8. Deployment warnings and troubleshooting

### Static IP warning

A domain controller should use stable addressing, but the address, prefix, gateway, and DNS values must come from the private lab plan. A static-IP warning means the selected adapter may not have stable addressing; inspect the correct interface and isolated segment. This public documentation intentionally omits all live network values. Domain members should use AD DNS for domain lookups. Configure upstream resolvers as DNS forwarders on internal DNS rather than assigning unrelated public resolvers directly to domain clients. See [Microsoft DNS client settings best practices](https://learn.microsoft.com/en-us/troubleshoot/windows-server/networking/best-practices-for-dns-client-settings).

### DNS delegation warning

For a standalone first forest, the wizard may be unable to create a delegation if there is no parent zone under your control. Check whether a parent zone exists and whether delegation is part of this design. Do not dismiss other prerequisite failures. After restart, check DNS service, zone, SRV records, and domain lookup.

### ZeroTier virtual adapter considerations

ZeroTier One is reported installed. A virtual adapter may affect interface selection, routes, DNS client behavior, and which addresses register in DNS. Before verification, inspect adapter metrics, DNS settings, routes, and DNS registration locally. Ensure DC locator and domain records advertise only intended lab-reachable addresses. Never publish ZeroTier IDs, managed addresses, credentials, tokens, routes, or identifying screenshots. Do not change live adapter settings without a deliberate change plan. See [ZeroTier DNS management](https://docs.zerotier.com/dns-management/).

### Forest functional level selection

Select the highest functional level supported by every planned domain controller and required compatibility. Functional level constrains supported AD features and eligible domain controller versions; it does not change the guest OS edition. The chosen level is unverified for this deployment. Record it only after checking the wizard or Get-ADForest. See [Microsoft Learn — AD functional levels](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/active-directory-functional-levels) and [raising domain and forest levels](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/raise-domain-forest-functional-levels?tabs=desktop).

## 9. Evidence and change control

Use the [screenshots index](screenshots/README.md). Upload genuine sanitized evidence only. Redact usernames, public or production addresses, MAC addresses, serials, account identifiers, network IDs, credentials, recovery secrets, and other sensitive data. Keep exact network settings in a private record outside this public repository.

All completion statements above reflect owner-reported progress. Successful promotion, reboot, service health, DNS answers, selected functional level, and diagnostics remain unverified until evidence is recorded.

## References

- [Microsoft Learn — Install a new Active Directory forest](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/install-a-new-windows-server-2012-active-directory-forest--level-200-)
- [Microsoft Learn — AD DS Configuration Wizard page descriptions](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/ad-ds-installation-and-removal-wizard-page-descriptions)
- [Microsoft Learn — DNS client settings best practices](https://learn.microsoft.com/en-us/troubleshoot/windows-server/networking/best-practices-for-dns-client-settings)
- [Microsoft Learn — Active Directory functional levels](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/active-directory-functional-levels)
- [Microsoft Learn — Raise domain and forest levels](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/raise-domain-forest-functional-levels?tabs=desktop)
- [ZeroTier — DNS management](https://docs.zerotier.com/dns-management/)
