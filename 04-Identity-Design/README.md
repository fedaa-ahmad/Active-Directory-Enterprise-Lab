# Identity Design Worksheets

**Status: Planned.** No users, groups, OUs, or policies are asserted to exist. Complete and review these worksheets before creating directory objects.

## Proposed OU worksheet

Design OUs around delegated administration and policy scope, not simply the organization chart. Keep privileged identities and servers in tightly controlled scopes. These examples require review and are not a final or implemented hierarchy.

| Proposed OU | Purpose | Delegated admins | GPO links | Status |
| --- | --- | --- | --- | --- |
| Lab (placeholder) | Root for lab objects, if approved | TBD | TBD | Planned |
| Users (placeholder) | Standard user accounts | TBD | TBD | Planned |
| Workstations (placeholder) | Client computer accounts | TBD | TBD | Planned |
| Servers (placeholder) | Member server accounts | TBD | TBD | Planned |
| Privileged (placeholder) | Restricted administrative identities | TBD | TBD | Planned |

## Users

Use synthetic test identities. Define naming, account purpose, owner, lifecycle, disable/delete process, password and MFA expectations where supported, and separation between daily and administrative accounts. Never store passwords in this repository. Record only non-sensitive test metadata.

| Test identity | Purpose | OU | Group memberships | Lifecycle | Status |
| --- | --- | --- | --- | --- | --- |
| TBD | TBD | TBD | TBD | TBD | Planned |

## Groups

Use role-based groups and a documented nesting/assignment model. Grant access through groups rather than direct user ACLs where practical. Separate privileged roles from ordinary access and review memberships regularly.

| Group | Scope/type | Intended access | Owner/reviewer | Status |
| --- | --- | --- | --- | --- |
| TBD | TBD | TBD | TBD | Planned |

## Group Policy

Create a policy inventory before linking GPOs. Prefer narrowly scoped, documented policies; test in a pilot OU; check inheritance and resultant settings; keep an approved rollback path. Avoid editing Default Domain Policy for unrelated settings.

| GPO | Purpose | Link scope | Pilot / validation | Status |
| --- | --- | --- | --- | --- |
| TBD | TBD | TBD | TBD | Planned |
