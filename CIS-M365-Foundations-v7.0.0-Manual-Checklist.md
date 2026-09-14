# CIS Microsoft 365 Foundations v7.0.0 - Manual Checklist

CIPP's built-in CIS v7.0.0 test suite evaluates **148 of 160** controls automatically. Run it from
the Dashboard's test suite picker, or add its tests to a Report Builder template. This file covers
the remaining **12**.

| Section | Count | How it is covered |
|---|---|---|
| A. Conditional Access | 0 | Every 5.2.2 control now has a CIPP test |
| B. Standards template only | 0 | Every control the L1 / L2 templates enforce now also has a CIPP test |
| C. Genuinely manual | 12 | CIPP cannot collect the data. Check by hand each audit cycle |

> Until 14 September 2026 this file counted 127 automated controls. It was measured against this
> repo's own CIS report template, which tracked CIPP's older 6.0.1 tests. CIPP's suite moved to
> v7.0.0 on 5 June 2026. See CHANGELOG.md.

## Per-tenant standards, not in the templates

These four controls have a CIPP standard, but it only passes with values specific to each tenant.
A synced template overwrites local edits on every sync, so the standards are left out of L1 and L2.
CIPP's CIS suite still tests all four controls. To enforce one, add its standard to a local,
unsynced template for that tenant.

| Control | Lvl | CIPP standard | Per-tenant input |
|---|---|---|---|
| 2.1.6 | L1 | `OutBoundSpamAlert` | Admin notification address, plus a BCC address for suspicious outbound mail |
| 5.2.3.2 | L1 | `CustomBannedPasswordList` | Organisation-specific banned words: company name, brands, local terms. Needs Entra ID P1 |
| 8.6.1 | L1 | `UserSubmissions` | Mailbox that receives user-reported messages. This standard accepts CIPP `%variables%` |
| 7.2.6 | L2 | `sharingDomainRestriction` | Allowed or blocked domain list for SharePoint external sharing |

## A. Conditional Access controls

None. CIPP now tests all 17 controls under 5.2.2. A test only reports: 5.2.2.13 to 5.2.2.17 still
need a CIPP Conditional Access template to enforce them.

## B. Covered by the standards template, no CIPP test

None. The eight controls listed here before (5.1.3.4, 5.1.5.3 to 5.1.5.6, 5.2.3.8 to 5.2.3.10)
now have a CIPP test as well as their L1 / L2 standard.

## C. Genuinely manual

### Microsoft Fabric (12) - Fabric admin portal > Tenant settings

| Control | Lvl | Requirement |
|---|---|---|
| 9.1.1 | L1 | Ensure guest user access is restricted |
| 9.1.2 | L1 | Ensure external user invitations are restricted |
| 9.1.3 | L1 | Ensure guest access to content is restricted |
| 9.1.4 | L1 | Ensure 'Publish to web' is restricted |
| 9.1.5 | L2 | Ensure 'Interact with and share R and Python' visuals is 'Disabled' |
| 9.1.6 | L1 | Ensure 'Allow users to apply sensitivity labels for content' is 'Enabled' |
| 9.1.7 | L1 | Ensure shareable links are restricted |
| 9.1.8 | L1 | Ensure enabling of external data sharing is restricted |
| 9.1.9 | L1 | Ensure 'Block ResourceKey Authentication' is 'Enabled' |
| 9.1.10 | L1 | Ensure access to APIs by service principals is restricted |
| 9.1.11 | L1 | Ensure service principals cannot create and use profiles |
| 9.1.12 | L1 | Ensure service principals ability to create workspaces, connections and deployment pipelines is restricted |

## How this is used

1. Run CIPP's CIS suite (Dashboard > Select a test suite > CIS > Refresh Test Data) for the 148 automated controls.
2. Walk section C by hand, 12 controls, and record results.
3. The combined audit deliverable merges both into one per-tenant document.

CIS Benchmarks are published by the Center for Internet Security. This file references control
numbers and titles only and does not reproduce the benchmark.
