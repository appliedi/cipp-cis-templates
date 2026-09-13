# CIS Microsoft 365 Foundations v7.0.0 - Manual / Out-of-Report Checklist

The Report Builder template `CIS_Microsoft_365_Foundations_Report.json` evaluates **127 of 160**
controls automatically. This file covers the remaining **33**.

Those 33 split three ways, and the difference matters. Only the last group is genuinely manual.

| Section | Count | How it is covered |
|---|---|---|
| A. Conditional Access | 5 | Apply a CIPP Conditional Access template. Automated once assigned |
| B. Standards template only | 8 | Enforced by the L1 / L2 standards template. Appears in drift reporting, not in the report document |
| C. Genuinely manual | 20 | CIPP cannot collect the data. Check by hand each audit cycle |

> Earlier versions of this file claimed 136 automated and listed 19 manual controls, which left
> nine unaccounted for. The numbers above reconcile to 160. See CHANGELOG.md.

## A. Conditional Access controls - apply via a CA template

Enforced through a CIPP Conditional Access template, not by hand. Build or import a CA template
set and assign it. Once assigned these are effectively automated.

| Control | Lvl | Requirement | Where |
|---|---|---|---|
| 5.2.2.13 | L1 | Ensure that periodic reauthentication is required for all users | CA policy, session control: sign-in frequency |
| 5.2.2.14 | L2 | Ensure trusted 'named locations' are defined | Entra > Security > Named locations |
| 5.2.2.15 | L2 | Ensure exclusionary geographic access controls are utilized | CA policy + country named location (block) |
| 5.2.2.16 | L2 | Ensure Token Protection is enforced for session tokens | CA policy, session control: token protection |
| 5.2.2.17 | L1 | Ensure authentication transfer is blocked | CA policy blocking authentication transfer |

## B. Covered by the standards template, no report test

These are enforced. They carry a CIPP standard in the L1 or L2 template, so drift shows up in
Standards alignment. They simply have no matching test in CIPP's CIS test library, so they will
not appear in the report document. Do not audit these by hand. Read them off alignment instead.

| Control | Lvl | Requirement | CIPP standard |
|---|---|---|---|
| 5.1.3.4 | L2 | Ensure that 'Users can create Microsoft 365 groups in Azure portals, API or PowerShell' is set to 'No' | `DisableM365GroupUsers` |
| 5.1.5.3 | L2 | Ensure password addition is blocked for applications | `AppManagementPolicy` |
| 5.1.5.4 | L1 | Ensure password lifetime for applications does not exceed 180 days | `AppManagementPolicy` |
| 5.1.5.5 | L1 | Ensure new application passwords are system-generated | `AppManagementPolicy` |
| 5.1.5.6 | L1 | Ensure maximum certificate lifetime for applications does not exceed 180 days | `AppManagementPolicy` |
| 5.2.3.8 | L1 | Ensure that Account 'Lockout threshold' is '10' or less | `SmartLockout` |
| 5.2.3.9 | L1 | Ensure that Account 'Lockout duration in seconds' is at least 60 seconds | `SmartLockout` |
| 5.2.3.10 | L1 | Ensure Microsoft Authenticator on companion applications is disabled | `PWcompanionAppAllowedState` |

## C. Genuinely manual

CIPP does not cache the data. Check each in the relevant admin portal and record Pass / Fail / N/A
per tenant.

### Identity, Purview and Exchange (8)

| Control | Lvl | Requirement | Where to check | Target |
|---|---|---|---|---|
| 2.4.5 | L1 | Ensure 'AIR' remediation is enabled | Defender portal > Settings > Email & collaboration > Automation / AIR | AIR active, remediation actions reviewed |
| 3.2.3 | L1 | Ensure DLP policies are published for Copilot users | Purview > Data Loss Prevention > Policies | A DLP policy scoped to M365 Copilot is on and published |
| 5.1.3.3 | L1 | Ensure that 'Owners can manage group membership requests in My Groups' is set to 'No' | Entra > Groups > General (My Groups settings) | Owners can manage membership requests = No |
| 5.2.4.2 | L2 | Ensure that 2 methods are required for password reset | Entra > Protection > Password reset > Authentication methods | Methods required to reset = 2 |
| 5.2.4.3 | L1 | Ensure SSPR registration and authentication re-confirmation are required | Entra > Password reset > Registration | Require registration and periodic re-confirm |
| 5.2.4.4 | L1 | Ensure that users are notified on password resets | Entra > Password reset > Notifications | Notify users on password resets = Yes |
| 5.2.4.5 | L1 | Ensure all admins are notified when other admins reset their password | Entra > Password reset > Notifications | Notify all admins when other admins reset = Yes |
| 6.3.2 | L1 | Ensure the ability to add personal email accounts and calendars is disabled | Exchange admin center > OWA mailbox policy | Personal email accounts and calendars disabled |

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

1. Run the automated suite (Dashboard > Report Builder > CIS Microsoft 365 Foundations > Refresh) for the 127 automated controls.
2. Read section B off Standards alignment for the assigned L1 / L2 template.
3. Confirm a CA template is assigned, which covers section A.
4. Walk section C by hand, 20 controls, and record results.
5. The combined audit deliverable merges all four into one per-tenant document.

CIS Benchmarks are published by the Center for Internet Security. This file references control
numbers and titles only and does not reproduce the benchmark.
