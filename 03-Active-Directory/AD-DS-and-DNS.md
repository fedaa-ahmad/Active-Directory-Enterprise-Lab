# Active Directory Domain Services and DNS

**Status: Planned.** This project has not promoted the server. Do not promote it until the prerequisite gate below is reviewed and the lab owner approves the domain design.

## Components

- **AD DS** stores directory objects and provides domain authentication, authorization, and policy infrastructure.
- **DNS** locates domain services (including domain controllers) and resolves names. AD-integrated zones can replicate through AD DS after the directory exists.
- **Global Catalog, SYSVOL, and Netlogon** support directory searches, policy/script distribution, and domain logon operations.
- **Clients** use the lab AD DNS service for domain discovery and authentication-related records.

## Design decisions before deployment

Document forest/root domain FQDN, NetBIOS name, host/domain naming, sites/subnets, DNS forwarders, time hierarchy, directory restore method, and administrative model. Choose a domain name that will not conflict with real or production namespaces. Existing planning notes do not specify a domain name; none is assumed here.

## Prerequisite gate — all must pass

- [ ] Server installation and patch baseline are verified.
- [ ] Network isolation, address/prefix, gateway, routing, and DNS behavior are verified.
- [ ] Static addressing is stable and documented.
- [ ] Hostname and time source are final and verified.
- [ ] Domain and NetBIOS names are approved and documented.
- [ ] Storage, backup, recovery, and rollback plan are understood.
- [ ] Lab is isolated and contains no production identities or data.
- [ ] Operator understands promotion changes the server role and requires a controlled restart and follow-up checks.

## Future deployment outline (not performed)

1. Add the AD DS role and management tools using the supported Windows Server workflow.
2. Promote only after the prerequisite gate is signed off; select a new forest only if that is the approved design.
3. Configure DNS integration and forwarding from the documented design.
4. Restart as required, then verify AD DS, DNS, SYSVOL, Netlogon, and event logs.
5. Point lab clients to AD DNS; join a test client only after DNS and domain health checks pass.
6. Record sanitized evidence, date, and test results in `evidence/`.

## Validation plan

After a future deployment, verify IP configuration and DNS client settings, DNS service/zone health, domain service records, time synchronization, directory service status, SYSVOL and NETLOGON availability, and a test client's name resolution and authentication. Use appropriate Windows diagnostics (for example, `ipconfig /all`, `nslookup`, `dcdiag`, and `repadmin` where applicable); capture results and investigate errors before declaring success.

## Evidence record

| Date | Check | Result | Evidence path | Reviewer |
| --- | --- | --- | --- | --- |
| — | No deployment recorded | Not run | — | — |
