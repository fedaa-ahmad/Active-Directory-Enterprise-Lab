# Network Design

**Status: Proposed; do not configure from this page until the open values are validated.**

## Existing values to reconcile

The original overview records a static host address of `192.168.2.250`, gateway `192.168.3.1`, preferred DNS `192.168.44.100`, and alternate DNS `192.168.44.254`. It gives no subnet mask/prefix or VLAN. If the intended subnet is /24, the address and gateway are on different networks, while both DNS addresses are outside `192.168.2.0/24`. This may be intentional routing, but the route and DNS purpose are undocumented. Treat every value as unverified and resolve with the lab network owner before use.

## Design principles

- Use an isolated virtual network with no unintended bridge to production.
- Give the server a static address or a documented reservation and record prefix, gateway, and DNS purpose together.
- After a domain is deployed, domain members should use the AD DNS service for domain lookups. Document forwarders and upstream resolvers separately; do not put unrelated public resolvers directly on domain clients.
- Ensure the domain controller has reliable time synchronization and that the lab resolves only the names it needs.
- Limit inbound management access to a trusted lab administration segment; avoid exposing management protocols to the internet.

## Addressing worksheet

| Role | Hostname | IPv4/prefix | Gateway | DNS | VLAN / segment | Status |
| --- | --- | --- | --- | --- | --- | --- |
| Planned server | AD-Test (existing note) | 192.168.2.250 (unverified) | 192.168.3.1 (unverified) | 192.168.44.100, 192.168.44.254 (unverified) | Not recorded | Requires validation |
| Future client | TBD | TBD | TBD | Planned AD DNS after deployment | TBD | Planned |

## Required validation before installation or promotion

1. Identify the intended subnet/prefix, VLAN/port group, gateway, and route. Confirm that the server address is valid for that segment.
2. Identify what each listed DNS address serves and whether it is reachable from the lab segment.
3. Confirm isolation and approved egress/update paths.
4. Record a simple network diagram and test plan (connectivity, name resolution, time source).
5. Reconcile this table with actual hypervisor and guest settings, recording evidence without secrets.

## Diagram (logical intent only)

```text
[Admin workstation]       [Future client VM(s)]
         \                    /
          +-- [Isolated lab segment] -- [AD-Test VM: planned Windows Server]

External routing / update access: undecided; explicitly control and document before enabling.
```

This is a planning aid and does not describe a deployed network.
