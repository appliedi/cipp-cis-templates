# CIS Microsoft 365 Foundations Benchmark v7.0.0 - CIPP Coverage Map

Mapping of all 160 CIS v7.0.0 recommendations to CIPP standards. Built by AppliedI.

## Summary

| Status | Count | Where it lives |
|---|---|---|
| Mapped to a CIPP standard | 90 | In the L1 / L2 template JSON (Report + Alert) |
| Conditional Access control | 17 | Apply a CIPP Conditional Access template (see checklist) |
| Manual - not automatable | 32 | Manual checklist |
| No CIPP standard yet | 21 | Manual checklist |
| **Total** | **160** | |

L1 controls: 114 | L2 controls: 46

## 1. Microsoft 365 admin center

| Control | Lvl | Title | CIPP Standard | Status |
|---|---|---|---|---|
| 1.1.1 | L1 | Ensure Administrative accounts are cloud-only | - | Manual - not automatable |
| 1.1.2 | L1 | Ensure two emergency access accounts have been defined | - | Manual - not automatable |
| 1.1.3 | L1 | Ensure that between two and four global admins are designated | - | Manual - not automatable |
| 1.1.4 | L1 | Ensure administrative accounts use licenses with a reduced application footprint | - | Manual - not automatable |
| 1.2.1 | L2 | Ensure that only organizationally managed/approved public groups exist | `EnforcePrivateGroups` | Mapped (CIS-tagged) |
| 1.2.2 | L1 | Ensure sign-in to shared mailboxes is blocked | `DisableSharedMailbox` | Mapped (CIS-tagged) |
| 1.3.1 | L1 | Ensure the 'Password expiration policy' is set to 'Set passwords to never expire (recommended)' | `PasswordExpireDisabled` | Mapped (CIS-tagged) |
| 1.3.2 | L2 | Ensure 'Idle session timeout' is set to '3 hours (or less)' for unmanaged devices | `ActivityBasedTimeout` | Mapped (CIS-tagged) |
| 1.3.3 | L2 | Ensure 'External sharing' of calendars is not available | `DisableExternalCalendarSharing` | Mapped (CIS-tagged) |
| 1.3.4 | L1 | Ensure 'User owned apps and services' is restricted | `DisableSelfServiceLicenses` | Mapped (CIS-tagged) |
| 1.3.5 | L1 | Ensure internal phishing protection for Forms is enabled | `FormsPhishingProtection` | Mapped (CIS-tagged) |
| 1.3.6 | L2 | Ensure the customer lockbox feature is enabled | `EnableCustomerLockbox` | Mapped (CIS-tagged) |
| 1.3.7 | L2 | Ensure 'third-party storage services' are restricted in 'Microsoft 365 on the web' | `RestrictThirdPartyStorageServices` | Mapped (CIS-tagged) |
| 1.3.8 | L2 | Ensure that Sways cannot be shared with people outside of your organization | - | Manual - not automatable |
| 1.3.9 | L1 | Ensure shared bookings pages are restricted to select users | `Bookings` | Mapped (CIS-tagged) |

## 2. Microsoft Defender

| Control | Lvl | Title | CIPP Standard | Status |
|---|---|---|---|---|
| 2.1.1 | L2 | Ensure Safe Links for Office Applications is Enabled | `SafeLinksPolicy` | Mapped (CIS-tagged) |
| 2.1.2 | L1 | Ensure the Common Attachment Types Filter is enabled | `MalwareFilterPolicy` | Mapped (CIS-tagged) |
| 2.1.3 | L1 | Ensure notifications for internal users sending malware is Enabled | `MalwareFilterPolicy` | Mapped (CIS-tagged) |
| 2.1.4 | L2 | Ensure Safe Attachments policy is enabled | `SafeAttachmentPolicy` | Mapped (CIS-tagged) |
| 2.1.5 | L2 | Ensure Safe Attachments for SharePoint, OneDrive, and Microsoft Teams is Enabled | `AtpPolicyForO365` | Mapped (CIS-tagged) |
| 2.1.6 | L1 | Ensure Exchange Online Spam Policies are set to notify administrators | `OutBoundSpamAlert` | Mapped (CIS-tagged) |
| 2.1.7 | L2 | Ensure that an anti-phishing policy has been created | `AntiPhishPolicy` | Mapped (CIS-tagged) |
| 2.1.8 | L1 | Ensure that SPF records are published for all Exchange Domains | - | No CIPP standard yet |
| 2.1.9 | L1 | Ensure that DKIM is enabled for all Exchange Online Domains | `RotateDKIM; AddDKIM` | Mapped (CIS-tagged) |
| 2.1.10 | L1 | Ensure DMARC records for all Exchange Online domains are published | `AddDMARCToMOERA` | Mapped (CIS-tagged) |
| 2.1.11 | L2 | Ensure comprehensive attachment filtering is applied | `MalwareFilterPolicy` | Mapped (CIS-tagged) |
| 2.1.12 | L1 | Ensure the connection filter IP allow list is not used | `EmptyFilterIPAllowList` | Mapped (CIS-tagged) |
| 2.1.13 | L1 | Ensure the connection filter safe list is off | `AntiSpamSafeList` | Mapped (CIS-tagged) |
| 2.1.14 | L1 | Ensure inbound anti-spam policies do not contain allowed domains | `SpamFilterPolicy` | Mapped (untagged std) |
| 2.1.15 | L1 | Ensure outbound anti-spam message limits are in place | `EXOOutboundSpamLimits` | Mapped (CIS-tagged) |
| 2.2.1 | L1 | Ensure emergency access account activity is monitored | - | Manual - not automatable |
| 2.4.1 | L1 | Ensure Priority account protection is enabled and configured | - | No CIPP standard yet |
| 2.4.2 | L1 | Ensure Priority accounts have 'Strict protection' presets applied | - | No CIPP standard yet |
| 2.4.3 | L2 | Ensure Microsoft Defender for Cloud Apps is enabled and configured | - | Manual - not automatable |
| 2.4.4 | L1 | Ensure Zero-hour auto purge for Microsoft Teams is on | `TeamsZAP` | Mapped (CIS-tagged) |
| 2.4.5 | L1 | Ensure 'AIR' remediation is enabled | - | Manual - not automatable |

## 3. Microsoft Purview

| Control | Lvl | Title | CIPP Standard | Status |
|---|---|---|---|---|
| 3.1.1 | L1 | Ensure Microsoft 365 audit log search is Enabled | `AuditLog` | Mapped (CIS-tagged) |
| 3.2.1 | L1 | Ensure DLP policies are enabled | - | No CIPP standard yet |
| 3.2.2 | L1 | Ensure DLP policies are enabled for Microsoft Teams | - | No CIPP standard yet |
| 3.2.3 | L1 | Ensure DLP policies are published for Copilot users | - | No CIPP standard yet |
| 3.3.1 | L1 | Ensure Information Protection sensitivity label policies are published | - | No CIPP standard yet |

## 4. Microsoft Intune admin center

| Control | Lvl | Title | CIPP Standard | Status |
|---|---|---|---|---|
| 4.1 | L1 | Ensure devices without a compliance policy are marked 'not compliant' | `IntuneComplianceSettings` | Mapped (CIS-tagged) |
| 4.2 | L1 | Ensure device enrollment for personally owned devices is blocked by default | `DefaultPlatformRestrictions` | Mapped (CIS-tagged) |

## 5. Microsoft Entra admin center

| Control | Lvl | Title | CIPP Standard | Status |
|---|---|---|---|---|
| 5.1.2.1 | L1 | Ensure 'Per-user MFA' is disabled | - | No CIPP standard yet |
| 5.1.2.2 | L1 | Ensure users cannot register applications | `DisableAppCreation` | Mapped (CIS-tagged) |
| 5.1.2.3 | L1 | Ensure 'Restrict non-admin users from creating tenants' is set to 'Yes' | `DisableTenantCreation` | Mapped (CIS-tagged) |
| 5.1.2.4 | L1 | Ensure access to the Entra admin center is restricted | - | Manual - not automatable |
| 5.1.2.5 | L2 | Ensure the option to remain signed in is hidden | - | Manual - not automatable |
| 5.1.2.6 | L2 | Ensure 'LinkedIn account connections' is disabled | - | Manual - not automatable |
| 5.1.3.1 | L1 | Ensure users cannot create security groups | `GroupTemplate` | Mapped (CIS-tagged) |
| 5.1.3.2 | L2 | Ensure that 'Restrict user ability to access groups features in My Groups' is set to 'Yes' | `DisableSecurityGroupUsers` | Mapped (CIS-tagged) |
| 5.1.3.3 | L1 | Ensure that 'Owners can manage group membership requests in My Groups' is set to 'No' | - | Manual - not automatable |
| 5.1.3.4 | L2 | Ensure that 'Users can create Microsoft 365 groups in Azure portals, API or PowerShell' is set to 'No' | `DisableM365GroupUsers` | Mapped (untagged std) |
| 5.1.4.1 | L2 | Ensure the ability to join devices to Entra is restricted | `intuneRestrictUserDeviceRegistration` | Mapped (CIS-tagged) |
| 5.1.4.2 | L1 | Ensure the maximum number of devices per user is limited | `intuneDeviceReg` | Mapped (CIS-tagged) |
| 5.1.4.3 | L1 | Ensure the GA role is not added as a local administrator during Entra join | `intuneDeviceRegLocalAdmins` | Mapped (CIS-tagged) |
| 5.1.4.4 | L1 | Ensure local administrator assignment is limited during Entra join | `intuneDeviceRegLocalAdmins` | Mapped (CIS-tagged) |
| 5.1.4.5 | L1 | Ensure Local Administrator Password Solution is enabled | `laps` | Mapped (CIS-tagged) |
| 5.1.4.6 | L2 | Ensure users are restricted from recovering BitLocker keys | `BitLockerKeysForOwnedDevice` | Mapped (CIS-tagged) |
| 5.1.5.1 | L2 | Ensure user consent to apps accessing company data on their behalf is not allowed | `OauthConsent` | Mapped (CIS-tagged) |
| 5.1.5.2 | L1 | Ensure the admin consent workflow is enabled | `EnableAppConsentRequests` | Mapped (CIS-tagged) |
| 5.1.5.3 | L2 | Ensure password addition is blocked for applications | `AppManagementPolicy` | Mapped (untagged std) |
| 5.1.5.4 | L1 | Ensure password lifetime for applications does not exceed 180 days | `AppManagementPolicy` | Mapped (untagged std) |
| 5.1.5.5 | L1 | Ensure new application passwords are system-generated | `AppManagementPolicy` | Mapped (untagged std) |
| 5.1.5.6 | L1 | Ensure maximum certificate lifetime for applications does not exceed 180 days | `AppManagementPolicy` | Mapped (untagged std) |
| 5.1.6.1 | L2 | Ensure that collaboration invitations are sent to allowed domains only | `CollaborationDomainRestriction` | Mapped (CIS-tagged) |
| 5.1.6.2 | L1 | Ensure that guest user access is restricted | `DisableGuestDirectory` | Mapped (CIS-tagged) |
| 5.1.6.3 | L2 | Ensure guest user invitations are limited | `GuestInvite` | Mapped (untagged std) |
| 5.1.8.1 | L1 | Ensure that password hash sync is enabled for hybrid deployments | - | Manual - not automatable |
| 5.2.2.1 | L1 | Ensure multifactor authentication is enabled for all users in administrative roles | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.2 | L1 | Ensure multifactor authentication is enabled for all users | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.3 | L1 | Enable Conditional Access policies to block legacy authentication | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.4 | L1 | Ensure Sign-in frequency is enabled and browser sessions are not persistent for Administrative users | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.5 | L2 | Ensure 'Phishing-resistant MFA strength' is required for Administrators | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.6 | L1 | Enable Identity Protection user risk policies | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.7 | L1 | Enable Identity Protection sign-in risk policies | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.8 | L2 | Ensure 'sign-in risk' is blocked for medium and high risk | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.9 | L1 | Ensure a managed device is required for authentication | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.10 | L1 | Ensure a managed device is required to register security information | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.11 | L1 | Ensure sign-in frequency for Intune Enrollment is set to 'Every time' | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.12 | L1 | Ensure the device code sign-in flow is blocked | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.13 | L1 | Ensure that periodic reauthentication is required for all users | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.14 | L2 | Ensure trusted 'named locations' are defined | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.15 | L2 | Ensure exclusionary geographic access controls are utilized | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.16 | L2 | Ensure Token Protection is enforced for session tokens | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.2.17 | L1 | Ensure authentication transfer is blocked | `ConditionalAccessTemplate` | Conditional Access template |
| 5.2.3.1 | L1 | Ensure Microsoft Authenticator is configured to protect against MFA fatigue | `PWdisplayAppInformationRequiredState` | Mapped (CIS-tagged) |
| 5.2.3.2 | L1 | Ensure custom banned passwords lists are used | `CustomBannedPasswordList` | Mapped (CIS-tagged) |
| 5.2.3.3 | L1 | Ensure password protection is enabled for on-prem Active Directory | - | Manual - not automatable |
| 5.2.3.4 | L1 | Ensure all member users are 'MFA capable' | - | Manual - not automatable |
| 5.2.3.5 | L1 | Ensure weak authentication methods are disabled | `DisableSMS; DisableVoice` | Mapped (CIS-tagged) |
| 5.2.3.6 | L1 | Ensure system-preferred multifactor authentication is enabled | `AuthMethodsSettings` | Mapped (CIS-tagged) |
| 5.2.3.7 | L2 | Ensure the email OTP authentication method is disabled | `DisableEmail` | Mapped (CIS-tagged) |
| 5.2.3.8 | L1 | Ensure that Account 'Lockout threshold' is '10' or less | - | Manual - not automatable |
| 5.2.3.9 | L1 | Ensure that Account 'Lockout duration in seconds' is at least 60 seconds | - | Manual - not automatable |
| 5.2.3.10 | L1 | Ensure Microsoft Authenticator on companion applications is disabled | `PWcompanionAppAllowedState` | Mapped (untagged std) |
| 5.2.4.1 | L1 | Ensure 'Self service password reset enabled' is set to 'All' | - | Manual - not automatable |
| 5.2.4.2 | L2 | Ensure that 2 methods are required for password reset | - | Manual - not automatable |
| 5.2.4.3 | L1 | Ensure SSPR registration and authentication re-confirmation are required | - | Manual - not automatable |
| 5.2.4.4 | L1 | Ensure that users are notified on password resets | - | Manual - not automatable |
| 5.2.4.5 | L1 | Ensure all admins are notified when other admins reset their password | - | Manual - not automatable |
| 5.3.1 | L2 | Ensure privileged role assignments are activated and not assigned | - | Manual - not automatable |
| 5.3.2 | L1 | Ensure 'Access reviews' for guest users are configured | - | Manual - not automatable |
| 5.3.3 | L1 | Ensure 'Access reviews' for privileged roles are configured | - | Manual - not automatable |
| 5.3.4 | L1 | Ensure approval is required for Global Administrator role activation | - | Manual - not automatable |
| 5.3.5 | L1 | Ensure approval is required for Privileged Role Administrator activation | - | Manual - not automatable |

## 6. Exchange admin center

| Control | Lvl | Title | CIPP Standard | Status |
|---|---|---|---|---|
| 6.1.1 | L1 | Ensure 'AuditDisabled' organizationally is set to 'False' | `EnableMailboxAuditing` | Mapped (CIS-tagged) |
| 6.1.2 | L1 | Ensure mailbox audit actions are configured | `EnableMailboxAuditing` | Mapped (CIS-tagged) |
| 6.1.3 | L1 | Ensure 'AuditBypassEnabled' is not enabled on mailboxes | `EnableMailboxAuditing` | Mapped (CIS-tagged) |
| 6.2.1 | L1 | Ensure all forms of mail forwarding are blocked and/or disabled | `EXODisableAutoForwarding` | Mapped (CIS-tagged) |
| 6.2.2 | L1 | Ensure mail transport rules do not whitelist specific domains | - | Manual - not automatable |
| 6.2.3 | L1 | Ensure email from external senders is identified | `SpoofWarn` | Mapped (CIS-tagged) |
| 6.3.1 | L2 | Ensure users installing Outlook add-ins is not allowed | `DisableOutlookAddins` | Mapped (CIS-tagged) |
| 6.3.2 | L1 | Ensure the ability to add personal email accounts and calendars is disabled | - | Manual - not automatable |
| 6.5.1 | L1 | Ensure modern authentication for Exchange Online is enabled | - | Manual - not automatable |
| 6.5.2 | L1 | Ensure MailTips are enabled for end users | `EnableMailTips` | Mapped (CIS-tagged) |
| 6.5.3 | L2 | Ensure additional storage providers are restricted in Outlook on the web | `DisableAdditionalStorageProviders` | Mapped (CIS-tagged) |
| 6.5.4 | L1 | Ensure SMTP AUTH is disabled | `DisableBasicAuthSMTP` | Mapped (CIS-tagged) |
| 6.5.5 | L2 | Ensure Direct Send submissions are rejected | `EXODirectSend` | Mapped (CIS-tagged) |

## 7. SharePoint admin center

| Control | Lvl | Title | CIPP Standard | Status |
|---|---|---|---|---|
| 7.2.1 | L1 | Ensure modern authentication for SharePoint applications is required | `DisableSharePointLegacyAuth` | Mapped (CIS-tagged) |
| 7.2.2 | L1 | Ensure SharePoint and OneDrive integration with Azure AD B2B is enabled | `SPAzureB2B` | Mapped (CIS-tagged) |
| 7.2.3 | L1 | Ensure external content sharing is restricted | `sharingCapability` | Mapped (CIS-tagged) |
| 7.2.4 | L2 | Ensure OneDrive content sharing is restricted | `sharingCapability` | Mapped (CIS-tagged) |
| 7.2.5 | L2 | Ensure that SharePoint guest users cannot share items they don't own | `DisableReshare` | Mapped (CIS-tagged) |
| 7.2.6 | L2 | Ensure SharePoint external sharing is restricted | `sharingDomainRestriction` | Mapped (CIS-tagged) |
| 7.2.7 | L1 | Ensure link sharing is restricted in SharePoint and OneDrive | `DefaultSharingLink` | Mapped (CIS-tagged) |
| 7.2.8 | L2 | Ensure external sharing is restricted by security group | - | No CIPP standard yet |
| 7.2.9 | L1 | Ensure guest access to a site or OneDrive will expire automatically | `SPExternalUserExpiration` | Mapped (CIS-tagged) |
| 7.2.10 | L1 | Ensure reauthentication with verification code is restricted | `SPEmailAttestation` | Mapped (CIS-tagged) |
| 7.2.11 | L1 | Ensure the SharePoint default sharing link permission is set | `DefaultSharingLink` | Mapped (CIS-tagged) |
| 7.3.1 | L2 | Ensure Office 365 SharePoint infected files are disallowed for download | `SPDisallowInfectedFiles` | Mapped (CIS-tagged) |

## 8. Microsoft Teams admin center

| Control | Lvl | Title | CIPP Standard | Status |
|---|---|---|---|---|
| 8.1.1 | L2 | Ensure external file sharing in Teams is enabled for only approved cloud storage services | `TeamsExternalFileSharing` | Mapped (CIS-tagged) |
| 8.1.2 | L1 | Ensure users can't send emails to a channel email address | `TeamsEmailIntegration` | Mapped (CIS-tagged) |
| 8.2.1 | L2 | Ensure external domains are restricted in the Teams admin center | `TeamsExternalAccessPolicy; TeamsFederationConfiguration` | Mapped (CIS-tagged) |
| 8.2.2 | L1 | Ensure communication with unmanaged Teams users is disabled | `TeamsExternalAccessPolicy` | Mapped (CIS-tagged) |
| 8.2.3 | L1 | Ensure external Teams users cannot initiate conversations | `TeamsExternalChatWithAnyone` | Mapped (CIS-tagged) |
| 8.2.4 | L1 | Ensure the organization cannot communicate with accounts in trial Teams tenants | - | Manual - not automatable |
| 8.4.1 | L1 | Ensure app permission policies are configured | - | Manual - not automatable |
| 8.5.1 | L2 | Ensure anonymous users can't join a meeting | `TeamsGlobalMeetingPolicy` | Mapped (CIS-tagged) |
| 8.5.2 | L1 | Ensure anonymous users and dial-in callers can't start a meeting | `TeamsGlobalMeetingPolicy` | Mapped (CIS-tagged) |
| 8.5.3 | L1 | Ensure only people in my org can bypass the lobby | `TeamsGlobalMeetingPolicy` | Mapped (CIS-tagged) |
| 8.5.4 | L1 | Ensure users dialing in can't bypass the lobby | `TeamsGlobalMeetingPolicy` | Mapped (CIS-tagged) |
| 8.5.5 | L2 | Ensure meeting chat does not allow anonymous users | `TeamsGlobalMeetingPolicy` | Mapped (CIS-tagged) |
| 8.5.6 | L2 | Ensure only organizers and co-organizers can present | `TeamsGlobalMeetingPolicy` | Mapped (CIS-tagged) |
| 8.5.7 | L1 | Ensure external participants can't give or request control | `TeamsGlobalMeetingPolicy` | Mapped (CIS-tagged) |
| 8.5.8 | L2 | Ensure external meeting chat is off | `TeamsGlobalMeetingPolicy` | Mapped (CIS-tagged) |
| 8.5.9 | L2 | Ensure meeting recording is off by default | `TeamsGlobalMeetingPolicy` | Mapped (CIS-tagged) |
| 8.6.1 | L1 | Ensure users can report security concerns in Teams | `UserSubmissions; TeamsMessagingPolicy` | Mapped (CIS-tagged) |

## 9. Microsoft Fabric

| Control | Lvl | Title | CIPP Standard | Status |
|---|---|---|---|---|
| 9.1.1 | L1 | Ensure guest user access is restricted | - | No CIPP standard yet |
| 9.1.2 | L1 | Ensure external user invitations are restricted | - | No CIPP standard yet |
| 9.1.3 | L1 | Ensure guest access to content is restricted | - | No CIPP standard yet |
| 9.1.4 | L1 | Ensure 'Publish to web' is restricted | - | No CIPP standard yet |
| 9.1.5 | L2 | Ensure 'Interact with and share R and Python' visuals is 'Disabled' | - | No CIPP standard yet |
| 9.1.6 | L1 | Ensure 'Allow users to apply sensitivity labels for content' is 'Enabled' | - | No CIPP standard yet |
| 9.1.7 | L1 | Ensure shareable links are restricted | - | No CIPP standard yet |
| 9.1.8 | L1 | Ensure enabling of external data sharing is restricted | - | No CIPP standard yet |
| 9.1.9 | L1 | Ensure 'Block ResourceKey Authentication' is 'Enabled' | - | No CIPP standard yet |
| 9.1.10 | L1 | Ensure access to APIs by service principals is restricted | - | No CIPP standard yet |
| 9.1.11 | L1 | Ensure service principals cannot create and use profiles | - | No CIPP standard yet |
| 9.1.12 | L1 | Ensure service principals ability to create workspaces, connections and deployment pipelines is restricted | - | No CIPP standard yet |



