# DC01 Evidence Screenshots

This folder is the screenshot documentation directory for the DC01 deployment. The filenames below are reserved placeholders; no screenshot evidence has been uploaded yet. Add only genuine screenshots after capture and sanitize them before publication.

| Screenshot filename | Description | Related implementation step | Evidence status |
|---|---|---|---|
| 01-esxi-vm-summary.png | Sanitized VM hardware and guest summary | ESXi virtual machine preparation | Pending upload |
| 02-isolated-lab-network.png | Sanitized evidence of the lab-only virtual network attachment | Production network isolation | Pending upload |
| 03-independent-internet-path.png | Sanitized connectivity evidence without account or topology details | Internet connectivity | Pending upload |
| 04-windows-server-edition.png | Windows Server edition/build, with identifiers redacted | Windows Server installation | Pending upload |
| 05-server-name-dc01.png | System information showing DC01 | Server renaming | Pending upload |
| 06-adds-role-installed.png | Server Manager showing AD DS role installed | AD DS role installation | Pending upload |
| 07-dns-role-installed.png | Server Manager showing DNS role installed | DNS role installation | Pending upload |
| 08-new-forest-selection.png | Promotion wizard showing new forest and corp.example.com | Domain Controller promotion | Pending upload |
| 09-promotion-prerequisite-check.png | Sanitized prerequisite-check result | Domain Controller promotion | Pending upload |
| 10-promotion-complete-restart.png | Successful completion notice after restart | Domain Controller promotion | Pending upload |
| 11-domain-forest-verification.png | Sanitized Get-ADDomain and Get-ADForest output | Post-promotion verification | Pending upload |
| 12-core-service-status.png | Sanitized NTDS, DNS, Netlogon, and KDC service status | Post-promotion verification | Pending upload |
| 13-dcdiag-results.png | Sanitized dcdiag results | Health verification | Pending upload |
| 14-domain-dns-lookup.png | Sanitized nslookup corp.example.com result | DNS verification | Pending upload |

## Upload and redaction rules

Before uploading, remove or obscure passwords, recovery secrets, tokens, usernames where unnecessary, public or production IP addresses, real network configuration, MAC addresses, serial numbers, Starlink account details, ZeroTier IDs/managed addresses, and management endpoints. Never fabricate evidence or mark a placeholder complete before the screenshot exists and has been reviewed.

Record the capture date and evidence link in this index when each real screenshot is added. Keep private network configuration in a private record; this repository is public.
