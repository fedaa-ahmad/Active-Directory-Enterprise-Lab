# Windows Server 2016 Installation

**Status:** Windows Server 2016 Datacenter installation and rename to DC01 are reported complete. This checklist is retained as the repeatable installation reference; see the [DC01 implementation record](01-DC01-Installation.md) for current status and evidence.

## Installation checklist

- [x] Prepare the ESXi virtual machine — reported complete.
- [x] Install Windows Server 2016 Datacenter — reported complete.
- [x] Rename the server to DC01 — reported complete.
- [ ] Verify installed edition/build and record sanitized evidence.
- [ ] Confirm local time, updates, and intended private lab network settings.
- [ ] Confirm isolation from production and restricted management access.
- [ ] Upload redacted screenshots to the [evidence index](screenshots/README.md).

Checked items above reflect owner-reported progress and are not independent verification. Do not publish the exact IP configuration, product key, password, or other credentials. Do not apply example values from public documentation to the live server.

For the detailed sequence, VMware context, role installation, promotion warnings, verification, and troubleshooting, see [01-DC01-Installation.md](01-DC01-Installation.md).
