# CIS Microsoft 365 Foundations v7.0.0 - Manual / Out-of-Report Checklist

This covers only the controls that the automated CIPP report does **not** assess. With CIPP's built-in CIS test library plus the custom v7.0.0 delta checks, the "CIS Microsoft 365 Foundations v7.0.0" report now evaluates **136 of 160 controls automatically**. The remaining **24** are below.

Of these 24, five are Conditional Access controls handled by applying a CA template (section A), and nineteen are genuinely manual because CIPP cannot collect the data (section B). Work section B by hand each audit cycle and record the result per tenant.

## A. Conditional Access controls (5) - apply via a CA template

These are enforced through a CIPP Conditional Access template, not by hand. Build or import a CA template set (CyberDrain ships baselines) and assign it. Once assigned, they are effectively automated.

| Control | Lvl | Requirement | Where |
|---|---|---|---|
| 5.2.2.13 | L1 | Periodic reauthentication required for all users | CA policy, session control: sign-in frequency |
| 5.2.2.14 | L2 | Trusted named locations are defined | Entra > Security > Named locations |
| 5.2.2.15 | L2 | Exclusionary geographic access controls are used | CA policy + country named location (block) |
| 5.2.2.16 | L2 | Token Protection enforced for session tokens | CA policy, session control: token protection |
| 5.2.2.17 | L1 | Authentication transfer is blocked | CA policy blocking authentication transfer |

## B. Genuinely manual controls (19)

CIPP does not cache the data for these, so check each in the relevant admin portal and record Pass / Fail / N/A per tenant.

### Identity and Defender / Purview (3)

| Control | Lvl | Requirement | Where to check | Target |
|---|---|---|---|---|
| 2.4.5 | L1 | AIR remediation is enabled | Microsoft Defender portal > Settings > Email & collaboration > Automation / AIR | Automated investigation and response active, remediation actions reviewed |
| 3.2.3 | L1 | DLP policies published for Copilot users | Microsoft Purview > Data Loss Prevention > Policies | A DLP policy scoped to Microsoft 365 Copilot is on and published |
| 5.1.3.3 | L1 | Owners can manage group membership requests in My Groups is set to No | Entra admin center > Groups > General (My Groups settings) | Set to No |

### Self-service password reset notifications (4)

| Control | Lvl | Requirement | Where to check | Target |
|---|---|---|---|---|
| 5.2.4.2 | L2 | Two methods required for password reset | Entra > Protection > Password reset > Authentication methods | Number of methods required to reset = 2 |
| 5.2.4.3 | L1 | SSPR registration and re-confirmation required | Entra > Password reset > Registration | Require registration; require re-confirm authentication info on a set cadence |
| 5.2.4.4 | L1 | Users notified on password resets | Entra > Password reset > Notifications | Notify users on password resets = Yes |
| 5.2.4.5 | L1 | Admins notified when other admins reset a password | Entra > Password reset > Notifications | Notify all admins when other admins reset their password = Yes |

### Microsoft Fabric (12) - Fabric admin portal > Tenant settings

| Control | Lvl | Requirement | Target |
|---|---|---|---|
| 9.1.1 | L1 | Guest user access is restricted | Restricted / disabled |
| 9.1.2 | L1 | External user invitations are restricted | Restricted / disabled |
| 9.1.3 | L1 | Guest access to content is restricted | Restricted |
| 9.1.4 | L1 | 'Publish to web' is restricted | Restricted (existing only, or disabled) |
| 9.1.5 | L2 | 'Interact with and share R and Python' visuals is Disabled | Disabled |
| 9.1.6 | L1 | Allow users to apply sensitivity labels for content is Enabled | Enabled |
| 9.1.7 | L1 | Shareable links are restricted | Restricted to people in org |
| 9.1.8 | L1 | Enabling of external data sharing is restricted | Restricted to specific security groups |
| 9.1.9 | L1 | Block ResourceKey Authentication is Enabled | Enabled |
| 9.1.10 | L1 | Access to APIs by service principals is restricted | Restricted to specific security groups |
| 9.1.11 | L1 | Service principals cannot create and use profiles | Disabled |
| 9.1.12 | L1 | Service principal creation of workspaces, connections, deployment pipelines is restricted | Restricted |

## How this is used

- Run the automated suite first (Dashboard > Report Builder > CIS Microsoft 365 Foundations v7.0.0 > Refresh) for the 136 automated controls.
- Then walk section B for the 19 manual controls and record results.
- The combined audit deliverable merges both into one per-tenant document.

CIS Benchmarks are published by the Center for Internet Security. This file references control numbers and titles only and does not reproduce the benchmark.
