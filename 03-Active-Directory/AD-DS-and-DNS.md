# Active Directory Domain Services and DNS

**Status:** AD DS and DNS roles are reported installed on DC01. Promotion to a new forest was started with corp.example.com selected and remains **In Progress** until completion, restart, and verification are documented.

| Item | Status |
|---|---|
| Server name DC01 | Reported complete |
| AD DS role | Reported installed |
| DNS Server role | Reported installed |
| New forest corp.example.com | Promotion In Progress; success unverified |
| NetBIOS name CORP | Intended value; verify after promotion |
| Domain/forest health | Pending verification |

## Verification after promotion and restart

Run from elevated PowerShell on DC01 after the promotion process completes. The Active Directory cmdlets require the AD module. Sanitize outputs before sharing.

~~~powershell
Get-ADDomain
Get-ADForest
Get-Service NTDS,DNS,Netlogon,KDC
dcdiag
nslookup corp.example.com
~~~

Record results, date, and redacted evidence. Expected checks include the correct domain and forest names, core services running, successful diagnostic results, and name resolution using intended lab DNS. Do not publish actual answer addresses.

## Deployment guide

Follow [DC01 Installation and Domain Deployment](../02-Installation/01-DC01-Installation.md) for the implementation record, wizard workflow, functional-level guidance, static IP and DNS delegation warnings, ZeroTier adapter review, and screenshot evidence index.

Role installation alone does not demonstrate a functioning domain controller. Keep the promotion status In Progress until post-restart checks pass. No server configuration is changed by this documentation.
