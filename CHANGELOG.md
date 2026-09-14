# Changelog

## 2026-09-14, generated reports

- Added five Report Builder templates: one technical report per QIT level (Baseline 192 checks,
  Good 21, Better 49, Best 13) and a client-facing QIT M365 Security Summary. The checks are the
  CIPP tests that CIPP links to each level's standards through `appliesToTest`. One
  `ConditionalAccessTemplate` standard carries all 28 conditional access tests, so those are split
  by level by hand. A test linked at two levels appears only at the lower one.
- Removed `CIS_Microsoft_365_Foundations_Report.json` and `CISA_ScubaGear_Report_ExchangeOnline.json`.
  CIPP's built-in CIS suite is now v7.0.0 with 148 tests. Ours had 128, and one of those
  (`CIS_7_3_2`) no longer exists. CIPP's built-in CISA suite has the same 24 tests as ours. A sync
  never deletes, so remove the old templates in CIPP by hand: **Tools > Report Builder >
  Templates > Delete**.
- The coverage map's `Report_Test` column and the manual checklist now measure against CIPP's CIS
  suite: 148 of 160 controls are tested, and only the 12 Microsoft Fabric controls are manual.

## 2026-09-14, template GUIDs

The L1 and L2 templates had their GUID only in the community-repo wrapper, not in the template
JSON itself. CIPP resolves a single-template run by the GUID inside the template JSON, so **Run
Template Now** matched nothing and logged `Template:  ()`. Both templates are set to run manually,
so scheduled runs skip them as well. As a result, neither had ever run: their alignment scores were
built from other templates' results for the same standards. Both now carry their GUID inside the
template JSON, matching the Baseline and CyberDrain's templates.

## 2026-09-13, template values

Every template was checked against the CIPP-API backend scripts that run each standard, not only
against `standards.json`. Several standards were configured without values, so CIPP compared the
tenant against nothing and they could never report compliant. The values chosen match what CIPP's
own CIS v7.0.0 tests check.

### L1, 51 to 48 standards

- Filled in missing values for 11 standards: `SpamFilterPolicy`, `MalwareFilterPolicy`,
  `EXOOutboundSpamLimits` (`BlockUser`), `intuneDeviceReg` (10 devices), `AuthMethodsSettings`,
  `TeamsGlobalMeetingPolicy`, `TeamsMessagingPolicy`, `DefaultSharingLink` (`Direct`), `Bookings`
  (Disabled, the only CIPP value that meets 1.3.9), `SpoofWarn` and `PWcompanionAppAllowedState`
  (disabled).
- Removed `OutBoundSpamAlert`, `CustomBannedPasswordList` and `UserSubmissions`. They only pass
  with tenant-specific values. The manual checklist now lists them.

### L2, 29 to 28 standards

- Filled in missing values for 7 standards: `SafeLinksPolicy`, `SafeAttachmentPolicy` (Block),
  `MalwareFilterPolicy`, `TeamsFederationConfiguration`, `TeamsGlobalMeetingPolicy`,
  `BitLockerKeysForOwnedDevice` and `EXODirectSend`. `AntiPhishPolicy` now names CIPP's default
  policy explicitly.
- `TeamsFederationConfiguration` is set to `BlockAllExternal`, the only generic value that passes
  8.2.1. Tenants that federate with partners should use an allow list in a local template instead.
- Removed `sharingDomainRestriction`, which needs a domain list.
- `TeamsGlobalMeetingPolicy` and `MalwareFilterPolicy` now carry identical values in L1 and L2, so
  a tenant assigned both templates has a single target.

### QIT M365 Baseline

- `DefaultSharingLink` stored `Direct` as a plain string. The backend only reads `.value`, so it
  discarded the string and audited `Internal`. The value is now stored as `{label, value}`.
- `PWcompanionAppAllowedState` changed to `disabled`, matching CIS 5.2.3.10.
- `AddDMARCToMOERA` is now stored in the format the backend reads. No change in behaviour, because
  the backend's fallback was already `p=reject`.

## 2026-09-13

Coverage map validated against CIPP's own `CIS M365 7.0.0 (x.y.z)` standard tags, which now exist on
100 CIPP standards. Where the map and CIPP's tags disagreed, CIPP's tag wins. Four mapping errors and
one reconciliation error were found and corrected.

### Mapping corrections

| Control | Lvl | Was | Now | Note |
|---|---|---|---|---|
| 5.1.3.1 | L1 | `GroupTemplate` | `DisableSecurityGroupUsers` | `GroupTemplate` is a Templates-category standard for deploying group templates and is unrelated. It appeared in neither the L1 nor the L2 template, so this L1 control was unreachable. CIPP tags `DisableSecurityGroupUsers` with 5.1.3.1 directly |
| 5.1.3.2 | L2 | `DisableSecurityGroupUsers`, marked CIS-tagged | none, `No CIPP standard yet` | The standard belongs to 5.1.3.1. CIPP carries no v7.0.0 tag for 5.1.3.2. This is the 5.1.3 reordering the README previously flagged as needing a spot-check. It is now resolved |
| 5.1.4.1 | L2 | `intuneRestrictUserDeviceRegistration` | `intuneRestrictUserDeviceJoin` | CIPP tags Join, not Registration, with 5.1.4.1. Registration carries no CIS tag at all. These control different things: device join versus device registration |
| 5.2.3.8 | L1 | unmapped, `Manual - not automatable` | `SmartLockout` | CIPP tags `SmartLockout` with both 5.2.3.8 and 5.2.3.9. Two controls were being audited by hand unnecessarily |
| 5.2.3.9 | L1 | unmapped, `Manual - not automatable` | `SmartLockout` | As above |

### Template changes

- **L1**, 49 to 51 standards: added `DisableSecurityGroupUsers` (5.1.3.1) and `SmartLockout`
  (5.2.3.8, 5.2.3.9, threshold 10, duration 60s).
- **L2**, 30 to 29 standards: removed `DisableSecurityGroupUsers`, which is an L1 control and now
  sits in the L1 template. Replaced `intuneRestrictUserDeviceRegistration` with
  `intuneRestrictUserDeviceJoin`.

Every standard name and parameter in both templates validates against CIPP's live `standards.json`.

### Checklist reconciliation

The manual checklist claimed the report evaluated "136 of 160" controls using "the built-in CIS test
library plus custom v7.0.0 delta checks", and listed 19 manual controls. The report contains 128
tests, all `CIS_` prefixed, and no delta checks exist in this repo. 128 plus 5 CA plus 19 manual
reconciles to 152, leaving nine controls unaccounted for. Anyone working the checklist was skipping
them believing the report had covered them.

The checklist is rewritten around what is actually shipped:

| Section | Count | Coverage |
|---|---|---|
| Report Builder test | 127 | Automated by `CIS_Microsoft_365_Foundations_Report.json` |
| A. Conditional Access | 5 | CA template, automated once assigned |
| B. Standards template only | 8 | Enforced by L1 / L2, visible in alignment, no report test |
| C. Genuinely manual | 20 | Check by hand |

127 + 5 + 8 + 20 = 160.

Section B is new and is the point of the rewrite. Those eight controls are enforced and were being
listed as work to do by hand. They should be read off Standards alignment instead.

One report test, `CIS_7_3_2`, has no matching v7.0.0 control. CIPP's CIS test library still tracks
6.0.1, so 128 tests map to 127 v7.0.0 controls.

### Additions

- `Report_Test` column added to the coverage map CSV and markdown, showing per control whether a
  Report Builder test exists. Standards-template coverage and report coverage are different things
  and the map now says which is which.
- `StandardsTemplateV2/QIT_M365_Baseline.json`, the QIT M365 Baseline, 54 standards, all in Report.
  See the README section for the three deliberate divergences from CIS L1 and the four settings that
  need local values before promotion.
- `CHANGELOG.md`, this file.
