# CADS Provincial Profile — Saskatchewan
## CADS/SK v1.0

**Status:** Draft
**Date:** June 2026
**Regulatory Authority:** Saskatchewan Occupational Health and Safety
**CADS Core Standard:** v1.0

---

## Profile Configuration

| Field | Value |
|---|---|
| `province_code` | `SK` |
| `province_name` | Saskatchewan |
| `regulatory_authority` | Saskatchewan Occupational Health and Safety |
| `regulation_reference` | Saskatchewan Employment Act — OHS Regulations 2020, Part 8, Sections 111–114 |
| `exposure_limit_dba` | 85 |
| `peak_limit_dbc` | null (not specified) |
| `action_level_dba` | 80 |
| `hcp_required` | `true` |
| `hcp_worker_threshold` | 10 (HCP required when 10 or more workers are exposed above 85 dBA Lex) |
| `audiometric_testing_required` | `true` |
| `testing_trigger_dba` | 85 |
| `baseline_months` | 6 |
| `testing_frequency` | `biennial` |
| `exit_test_required` | `false` |
| `hpd_selection_documentation_required` | `false` |
| `retention_years_minimum` | null (not specifically defined) |
| `language` | `en` |
| `verification_date` | 2026-06-01 |

---

## Regulatory Context

### Overview

Saskatchewan's hearing conservation requirements are established under the Saskatchewan Employment Act, Occupational Health and Safety Regulations 2020, Part 8. Saskatchewan's framework closely mirrors Alberta's in most respects, with one notable distinction: a worker threshold that determines when a formal Hearing Conservation Program is required.

### Noise Exposure Limits

Workers must not be exposed to noise exceeding:
- **85 dBA Lex** (time-weighted average over an 8-hour shift)

An action level of **80 dBA** applies — employers must conduct noise assessment and implement controls when exposure may exceed this level.

### Hearing Conservation Program

A written Hearing Conservation Program is required when **10 or more workers** are exposed to noise levels above 85 dBA Lex. This worker threshold is unique among western Canadian provinces — BC and Alberta have no threshold.

Small employers with fewer than 10 noise-exposed workers do not have a specific HCP requirement under Saskatchewan regulation, though general duty of care still applies. CADS testing and documentation represents best practice for these employers regardless of threshold.

The HCP must be reviewed every **3 years** or when significant changes to noise exposure occur.

### Audiometric Testing Requirements

**Baseline test:** Must be conducted prior to first noise exposure or within a reasonable period thereafter. Specific timing not explicitly stated in regulation — 6 months is applied as best practice in alignment with other provinces.

**Periodic testing:** At least every **24 months** (biennial) for workers exposed above 85 dBA Lex.

**Qualified tester:** Testing must be conducted by a person certified and competent to conduct audiometric testing — IAT, physician, or audiologist.

### Hearing Protection

Hearing protection is required when noise levels exceed 85 dBA Lex and exposure cannot be controlled through engineering or administrative means.

HPD must be adequate for the worker's noise exposure level. CSA Z94.2 is referenced for HPD standards.

### Record Keeping

Specific record retention periods are not defined in the Saskatchewan OHS Regulations 2020. Best practice is to retain audiometric records for the duration of employment plus 10 years, consistent with BC and industry best practice.

### Standard Threshold Shift

Saskatchewan uses the standard CADS definition: an average shift of **10 dB or more** at 2000, 3000, and 4000 Hz in either ear. Age correction is permitted.

When an STS is detected the employer must review the HCP, investigate the cause, and take corrective action. Worker notification is required.

---

## CADS Implementation Notes

**Worker threshold:** The `hcp_worker_threshold` is set to `10`. CADS systems operating in Saskatchewan should note when an employer's noise-exposed worker count falls below this threshold — the HCP requirement technically does not apply, though testing may still be conducted as best practice.

**Baseline timing:** Saskatchewan regulation does not specify an explicit baseline timing window. 6 months is applied as the standard consistent with BC and Alberta practice. Systems should flag when a worker has been in noise-exposed work for more than 6 months without a baseline audiogram.

**Testing frequency:** Biennial — same as Alberta. CADS systems should flag when a worker's most recent periodic test exceeds 24 months.

**Exit test:** Not required. May be offered as best practice.

**Program review:** Saskatchewan specifically requires HCP review every 3 years. CADS systems supporting employer HCP management should track this review cycle.

---

## Differences from BC and AB Profiles

| Element | BC | Alberta | Saskatchewan |
|---|---|---|---|
| Testing frequency | Annual | Biennial (after year 1) | Biennial |
| Exit test | Required | Not required | Not required |
| HPD documentation | Required | Not required | Not required |
| HCP worker threshold | None | None | 10 workers |
| HCP review cycle | Not specified | Not specified | Every 3 years |
| Retention | Employment + 10 years | Duration of operations | Not specified |
| Action level | 82 dBA | 82 dBA | 80 dBA |

---

## Verification Items

- [ ] Confirm 10-worker threshold for HCP requirement — OHS Regulations 2020 Part 8 Section 111
- [ ] Confirm biennial testing — Part 8 Section 112 or 113
- [ ] Confirm baseline timing is not explicitly specified in the regulation
- [ ] Confirm 3-year HCP review requirement — Part 8 Section 114
- [ ] Confirm record retention is not specified in Part 8
- [ ] Confirm action level is 80 dBA (lower than BC/AB at 82 dBA)
- [ ] Confirm no peak limit is specified in Saskatchewan regulation

---

*CADS Provincial Profile — Saskatchewan*
*Draft for internal review — regulatory references subject to verification*
*© RoadPilotAI*
