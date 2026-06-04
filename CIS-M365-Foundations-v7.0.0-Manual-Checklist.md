# CIS Microsoft 365 Foundations v7.0.0 - Manual / Out-of-Template Checklist

Controls that the L1/L2 CIPP templates do **not** cover, with how to handle each. Three groups: Conditional Access (apply a CA template), Manual (no CIPP automation), and No CIPP standard yet (configurable, but build/track outside the standards engine).

## A. Conditional Access controls (17)

These are enforced through CIPP **Conditional Access templates**, not standalone standards. The standards engine references a CA template by GUID that must exist in your tenant, so they are intentionally left out of the JSON. Build or import a CA template set in CIPP (Tenant Administration > Templates > Conditional Access), then add the ConditionalAccessTemplate standard pointing at it. CyberDrain ships baseline CA templates you can import.

| Control | Lvl | Title |
|---|---|---|
| 5.2.2.1 | L1 | Ensure multifactor authentication is enabled for all users in administrative roles |
| 5.2.2.2 | L1 | Ensure multifactor authentication is enabled for all users |
| 5.2.2.3 | L1 | Enable Conditional Access policies to block legacy authentication |
| 5.2.2.4 | L1 | Ensure Sign-in frequency is enabled and browser sessions are not persistent for Administrative users |
| 5.2.2.5 | L2 | Ensure 'Phishing-resistant MFA strength' is required for Administrators |
| 5.2.2.6 | L1 | Enable Identity Protection user risk policies |
| 5.2.2.7 | L1 | Enable Identity Protection sign-in risk policies |
| 5.2.2.8 | L2 | Ensure 'sign-in risk' is blocked for medium and high risk |
| 5.2.2.9 | L1 | Ensure a managed device is required for authentication |
| 5.2.2.10 | L1 | Ensure a managed device is required to register security information |
| 5.2.2.11 | L1 | Ensure sign-in frequency for Intune Enrollment is set to 'Every time' |
| 5.2.2.12 | L1 | Ensure the device code sign-in flow is blocked |
| 5.2.2.13 | L1 | Ensure that periodic reauthentication is required for all users |
| 5.2.2.14 | L2 | Ensure trusted 'named locations' are defined |
| 5.2.2.15 | L2 | Ensure exclusionary geographic access controls are utilized |
| 5.2.2.16 | L2 | Ensure Token Protection is enforced for session tokens |
| 5.2.2.17 | L1 | Ensure authentication transfer is blocked |

## B. Manual controls - no CIPP automation (32)

| Control | Lvl | Title (target state) | Where to set it |
|---|---|---|---|
| 1.1.1 | L1 | Ensure Administrative accounts are cloud-only | Microsoft 365 admin center |
| 1.1.2 | L1 | Ensure two emergency access accounts have been defined | Microsoft 365 admin center |
| 1.1.3 | L1 | Ensure that between two and four global admins are designated | Microsoft 365 admin center |
| 1.1.4 | L1 | Ensure administrative accounts use licenses with a reduced application footprint | Microsoft 365 admin center |
| 1.3.8 | L2 | Ensure that Sways cannot be shared with people outside of your organization | Microsoft 365 admin center |
| 2.2.1 | L1 | Ensure emergency access account activity is monitored | Microsoft Defender |
| 2.4.3 | L2 | Ensure Microsoft Defender for Cloud Apps is enabled and configured | Microsoft Defender |
| 2.4.5 | L1 | Ensure 'AIR' remediation is enabled | Microsoft Defender |
| 5.1.2.4 | L1 | Ensure access to the Entra admin center is restricted | Microsoft Entra admin center |
| 5.1.2.5 | L2 | Ensure the option to remain signed in is hidden | Microsoft Entra admin center |
| 5.1.2.6 | L2 | Ensure 'LinkedIn account connections' is disabled | Microsoft Entra admin center |
| 5.1.3.3 | L1 | Ensure that 'Owners can manage group membership requests in My Groups' is set to 'No' | Microsoft Entra admin center |
| 5.1.8.1 | L1 | Ensure that password hash sync is enabled for hybrid deployments | Microsoft Entra admin center |
| 5.2.3.3 | L1 | Ensure password protection is enabled for on-prem Active Directory | Microsoft Entra admin center |
| 5.2.3.4 | L1 | Ensure all member users are 'MFA capable' | Microsoft Entra admin center |
| 5.2.3.8 | L1 | Ensure that Account 'Lockout threshold' is '10' or less | Microsoft Entra admin center |
| 5.2.3.9 | L1 | Ensure that Account 'Lockout duration in seconds' is at least 60 seconds | Microsoft Entra admin center |
| 5.2.4.1 | L1 | Ensure 'Self service password reset enabled' is set to 'All' | Microsoft Entra admin center |
| 5.2.4.2 | L2 | Ensure that 2 methods are required for password reset | Microsoft Entra admin center |
| 5.2.4.3 | L1 | Ensure SSPR registration and authentication re-confirmation are required | Microsoft Entra admin center |
| 5.2.4.4 | L1 | Ensure that users are notified on password resets | Microsoft Entra admin center |
| 5.2.4.5 | L1 | Ensure all admins are notified when other admins reset their password | Microsoft Entra admin center |
| 5.3.1 | L2 | Ensure privileged role assignments are activated and not assigned | Microsoft Entra admin center |
| 5.3.2 | L1 | Ensure 'Access reviews' for guest users are configured | Microsoft Entra admin center |
| 5.3.3 | L1 | Ensure 'Access reviews' for privileged roles are configured | Microsoft Entra admin center |
| 5.3.4 | L1 | Ensure approval is required for Global Administrator role activation | Microsoft Entra admin center |
| 5.3.5 | L1 | Ensure approval is required for Privileged Role Administrator activation | Microsoft Entra admin center |
| 6.2.2 | L1 | Ensure mail transport rules do not whitelist specific domains | Exchange admin center |
| 6.3.2 | L1 | Ensure the ability to add personal email accounts and calendars is disabled | Exchange admin center |
| 6.5.1 | L1 | Ensure modern authentication for Exchange Online is enabled | Exchange admin center |
| 8.2.4 | L1 | Ensure the organization cannot communicate with accounts in trial Teams tenants | Microsoft Teams admin center |
| 8.4.1 | L1 | Ensure app permission policies are configured | Microsoft Teams admin center |

## C. No CIPP standard yet (configurable, track manually) (21)

| Control | Lvl | Title (target state) | Where to set it |
|---|---|---|---|
| 2.1.8 | L1 | Ensure that SPF records are published for all Exchange Domains | Microsoft Defender |
| 2.4.1 | L1 | Ensure Priority account protection is enabled and configured | Microsoft Defender |
| 2.4.2 | L1 | Ensure Priority accounts have 'Strict protection' presets applied | Microsoft Defender |
| 3.2.1 | L1 | Ensure DLP policies are enabled | Microsoft Purview |
| 3.2.2 | L1 | Ensure DLP policies are enabled for Microsoft Teams | Microsoft Purview |
| 3.2.3 | L1 | Ensure DLP policies are published for Copilot users | Microsoft Purview |
| 3.3.1 | L1 | Ensure Information Protection sensitivity label policies are published | Microsoft Purview |
| 5.1.2.1 | L1 | Ensure 'Per-user MFA' is disabled | Microsoft Entra admin center |
| 7.2.8 | L2 | Ensure external sharing is restricted by security group | SharePoint admin center |
| 9.1.1 | L1 | Ensure guest user access is restricted | Microsoft Fabric |
| 9.1.2 | L1 | Ensure external user invitations are restricted | Microsoft Fabric |
| 9.1.3 | L1 | Ensure guest access to content is restricted | Microsoft Fabric |
| 9.1.4 | L1 | Ensure 'Publish to web' is restricted | Microsoft Fabric |
| 9.1.5 | L2 | Ensure 'Interact with and share R and Python' visuals is 'Disabled' | Microsoft Fabric |
| 9.1.6 | L1 | Ensure 'Allow users to apply sensitivity labels for content' is 'Enabled' | Microsoft Fabric |
| 9.1.7 | L1 | Ensure shareable links are restricted | Microsoft Fabric |
| 9.1.8 | L1 | Ensure enabling of external data sharing is restricted | Microsoft Fabric |
| 9.1.9 | L1 | Ensure 'Block ResourceKey Authentication' is 'Enabled' | Microsoft Fabric |
| 9.1.10 | L1 | Ensure access to APIs by service principals is restricted | Microsoft Fabric |
| 9.1.11 | L1 | Ensure service principals cannot create and use profiles | Microsoft Fabric |
| 9.1.12 | L1 | Ensure service principals ability to create workspaces, connections and deployment pipelines is restricted | Microsoft Fabric |


