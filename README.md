# CIPP CIS Templates

CIS Benchmark templates and coverage mappings for [CIPP](https://cipp.app) (CyberDrain Improved Partner Portal), the multi-tenant Microsoft 365 management platform for MSPs.

This repository maps a CIS Benchmark to CIPP's standards engine so you can **report and alert on CIS drift across every managed tenant**, then enforce when ready. It is maintained by AppliedI and shared in the spirit of the community templates from [CyberDrain](https://github.com/CyberDrain/CyberDrain-CIS-Templates).

## Available benchmarks

| Benchmark | Templates | Coverage |
|---|---|---|
| CIS Microsoft 365 Foundations **v7.0.0** | `StandardsTemplateV2/` (L1 and L2) | 90 of 160 controls map to a CIPP standard |

## CIS Microsoft 365 Foundations v7.0.0

Two importable CIPP standard templates, split by CIS profile **Level 1** and **Level 2** so each level reports separately. Every standard is set to **Report + Alert** (non-enforcing) out of the box, so CIPP surfaces drift without changing tenant configuration. Switch a standard to **Remediate** in the CIPP editor when you are ready to enforce it.

| File | Contents |
|---|---|
| `StandardsTemplateV2/CIS_Microsoft_365_Foundations_v7.0.0__L1_Report.json` | Level 1 standards template — 49 standards |
| `StandardsTemplateV2/CIS_Microsoft_365_Foundations_v7.0.0__L2_Report.json` | Level 2 standards template — 30 standards |
| `CIS-M365-Foundations-v7.0.0-Coverage-Map.md` / `.csv` | All 160 controls mapped to their CIPP standard and status |
| `CIS-M365-Foundations-v7.0.0-Manual-Checklist.md` | The controls the templates do not cover, with where to handle each |

The two template files live under `StandardsTemplateV2/` and are wrapped in CIPP's community-repository format (a `PartitionKey` of `StandardsTemplateV2` plus the template serialized into the `JSON` field). That folder name and wrapper are how CIPP recognizes them as Standards templates. Do not move them to the repo root or rename the folder, or CIPP will fail to classify them on sync.

### Coverage at a glance (160 controls)

| Status | Count | Handled by |
|---|---|---|
| Mapped to a CIPP standard | 90 | The L1 / L2 template JSON |
| Conditional Access control (5.2.2.x) | 17 | A CIPP Conditional Access template (see checklist) |
| Manual — no CIPP automation | 32 | Manual checklist |
| No CIPP standard yet | 21 | Manual checklist |

About two-thirds of the benchmark maps to a ready CIPP standard. The remainder is either something CIPP cannot automate today (PIM, emergency access accounts, SSPR notifications, on-prem AD) or a newer v7.0.0 area without a CIPP standard yet, most notably the entire **Microsoft Fabric** section (9.1.x), DLP (3.2.x), and sensitivity labels (3.3.1).

### How to use (CIPP Community Repository)

This repo is built to be consumed as a CIPP Community Repository.

1. In CIPP, open **Settings > Community Repositories** and add this repo (`appliedi/cipp-cis-templates`).
2. Sync it. CIPP reads the `StandardsTemplateV2/` folder and imports both files as **Standards templates** (not Intune templates).
3. The two templates appear under **Tenant Administration > Standards > Templates**, synced and **unassigned** ("Template Tenant").
4. Edit each template and assign the tenant or tenant group you want to measure, then run it (scheduled or manually) to produce alignment data.

Synced standards templates arrive unassigned by design. Assign tenants locally after the first sync. If a later sync resets the assignment, reassign. No tenant data is stored in this public repo.

Prefer a one-off manual import instead? Open a file under `StandardsTemplateV2/`, copy the value of its `JSON` field (the inner template), and paste it into **Standards > Add Standard > import JSON**.

### Read before you enforce

1. **CIPP tags against CIS 6.0.1.** CIPP carries CIS M365 **6.0.1** control numbers on its standards. The numbering aligns with 7.0.0 in nearly every case; spot-check the 5.1.3 group controls, where the numbering looks reordered between versions.

2. **Conditional Access controls are not in the JSON on purpose.** The 17 controls under 5.2.2 (MFA, legacy auth, sign-in risk and frequency, named locations, token protection, and so on) are enforced through a CIPP **Conditional Access template** that references a template GUID unique to your tenant. Embedding one would import broken. Build or import a CA template set, then add the `ConditionalAccessTemplate` standard pointing at it. CyberDrain ships baseline CA templates you can start from.

3. **Per-user MFA (5.1.2.1) has no matching standard.** CIS wants per-user MFA *disabled* in favor of Conditional Access. CIPP's `PerUserMFA` standard does the opposite, so it is deliberately not mapped.

4. **Some standards import as Report-only because their target is org-specific.** Notification addresses, allowed domains, banned-word lists, and a few dropdown / numeric values load live in the CIPP editor. Set them before switching those standards to Remediate. They are flagged in the coverage map.

5. **Embedded values are CIS-aligned defaults.** Where the target was unambiguous (external sharing only, 3-hour idle timeout, 180-day app credential lifetime, anti-phishing thresholds, Teams anonymous-join off, and similar) the value is pre-filled. Review against your own baseline before enforcing.

## Disclaimer and CIS attribution

CIS Benchmarks™ are published by the [Center for Internet Security](https://www.cisecurity.org/). This repository does **not** include, redistribute, or reproduce the CIS Benchmark document. It references CIS control numbers and recommendation titles only, to map them to CIPP standards. To obtain the benchmark itself, download it from CIS. Use of CIS Benchmark content is subject to the CIS SecureSuite Membership Terms of Use.

These templates are provided as-is, with no warranty. Review every control against your own requirements and test in a non-production tenant before enforcing. This project is not affiliated with or endorsed by CIS, Microsoft, or CyberDrain.

## License

The original work in this repository (the mapping, the template JSON structure, the documentation, and scripts) is released under the [MIT License](LICENSE). CIS control numbers and titles remain the property of the Center for Internet Security.
