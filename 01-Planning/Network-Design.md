# Network Design

**Status:** Lab isolation and separate internet connectivity are reported complete. Detailed network configuration is intentionally not published.

## Security and disclosure

This repository is public. Never record production IP addresses, actual subnets, gateways, DNS servers, VLANs, routes, MAC addresses, Starlink account details, ZeroTier network identifiers, or credentials. Maintain exact configuration in a private operational record. The project owner reports the lab server is isolated from production and connected through an independent Starlink service. This page does not verify or describe the underlying topology.

## Logical design

The design intent is an isolated lab segment hosting DC01 and future lab clients, with controlled internet access for updates and administration from trusted lab access. Confirm the isolation at the physical and ESXi virtual switch/port group layers. Do not expose ESXi management, RDP, LDAP, DNS, or other directory services to the public internet.

~~~text
Trusted lab administration -> isolated lab segment -> DC01 (planned domain services)
                                              -> future lab clients
                                              -> controlled outbound update access
~~~

This is a logical concept only, not a record of deployed cabling, routes, or IP configuration.

## Addressing worksheet

| Role | Hostname | Address/prefix | Gateway and DNS | Status |
|---|---|---|---|---|
| Domain controller | DC01 | Maintained privately | Maintained privately | Address configuration not documented here |
| Future client | TBD | Maintained privately | AD DNS after promotion verification | Planned |

If an example is needed in a separate instructional context, use only documentation ranges reserved for examples (RFC 5737 TEST-NET); label them fictional and never imply they are the lab's real settings.

## DNS and routing principles

- Use stable addressing for servers, based on the private lab plan.
- After domain deployment, domain members should use the AD DNS service for domain names and records.
- Configure upstream resolution as forwarders on internal DNS as appropriate; avoid unrelated public resolvers as the direct DNS setting on domain members.
- Validate routing, name resolution, time synchronization, and outbound update paths from the isolated segment.
- Review ZeroTier routes, DNS behavior, and adapter registration locally. Do not disclose its network identity, managed addresses, or credentials.

## Validation record

Isolation from production and independent Starlink connectivity are reported complete by the project owner. No live network settings or screenshots are included. Add sanitized evidence only after review. Verify that management remains private, that the intended lab segment has no unintended production bridge, and that outbound access is limited to the documented requirement.

See [DC01 Installation and Domain Deployment](../02-Installation/01-DC01-Installation.md) for adapter considerations and [Lab Overview](Lab-Overview.md) for project status.
