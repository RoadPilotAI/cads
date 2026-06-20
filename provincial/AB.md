# CADS Provincial Profile — Alberta
## CADS/AB v1.0

**Status:** Draft
**Date:** June 2026
**Regulatory Authority:** Alberta OHS
**CADS Core Standard:** v1.0

---

## Profile Configuration

| Field | Value |
|---|---|
| `province_code` | `AB` |
| `province_name` | Alberta |
| `regulatory_authority` | Alberta Occupational Health and Safety |
| `regulation_reference` | Occupational Health and Safety Code Part 16, Sections 218–224 |
| `exposure_limit_dba` | 85 |
| `peak_limit_dbc` | 140 |
| `action_level_dba` | 82 |
| `hcp_required` | `true` |
| `hcp_worker_threshold` | null (no threshold — applies to any exposed worker) |
| `audiometric_testing_required` | `true` |
| `testing_trigger_dba` | 85 |
| `baseline_months` | 6 |
| `testing_frequency` | `biennial` (see notes — first periodic at 12 months, then biennial) |
| `exit_test_required` | `false` |
| `hpd_selection_documentation_required` | `false` |
| `retention_years_minimum` | null (records retained for duration of employer operations) |
| `language` | `en` |
| `verification_date` | 2026-06-01 |

---

## Regulatory Context

### Overview

Alberta's hearing conservation requirements are established under the Occupational Health and Safety Code Part 16, administered by Alberta OHS under the Occupational Health and Safety Act. Alberta's framework is employer-friendly in approach — comprehensive in coverage but with fewer prescriptive documentation requirements than British Columbia.

### Noise Exposure Limits

Workers must not be exposed to noise exceeding:
- **85 dBA** (time-weighted average over an 8-hour shift)
- **140 dBC peak** (instantaneous peak level)

A noise assessment is required when workers may be exposed to A-weighted sound pressure levels above **82 dBA** (OHS Code Section 219).

### Hearing Conservation Program

A written noise control and hearing conservation program is required when a hazard assessment identifies workers exposed to noise levels above 85 dBA Lex or 140 dBC peak. The program must include:

- Noise exposure assessment results
- Engineering and administrative noise controls
- Hearing protection program
- Audiometric testing program
- Worker training
- Program review schedule

Alberta requires noise exposure records to be retained **for as long as the employer operates**. This is a unique and more stringent requirement than most other provinces, though it applies to noise exposure records specifically rather than audiometric test records.

### Audiometric Testing Requirements

**Baseline test:** Must be conducted within 6 months of first exposure to hazardous noise.

**First periodic test:** Must be conducted within 12 months of the baseline test.

**Subsequent periodic tests:** At least every **24 months** (biennial) after the first periodic test.

This is a meaningful distinction from British Columbia's annual requirement. After the initial baseline and first-year test, Alberta workers on a biennial schedule may go up to two years between tests.

**Qualified tester:** Testing must be conducted by a person certified and competent to conduct audiometric testing — IAT, physician, or audiologist.

### Hearing Protection

Hearing protection is required when noise levels cannot be controlled to below the exposure limit through engineering or administrative controls.

HPD must be adequate for the worker's noise exposure. HPD selection documentation is recommended but not specifically required by regulation.

### Record Keeping

Noise exposure records must be retained for the duration of the employer's operations. Audiometric test records — minimum retention period not specifically defined in the regulation; best practice is to retain for the duration of employment plus 10 years.

### Standard Threshold Shift

Alberta uses the standard CADS definition: an average shift of **10 dB or more** at 2000, 3000, and 4000 Hz in either ear. Age correction is permitted.

When an STS is detected, the employer must:
- Inform the worker
- Review and update the HCP
- Consider engineering or administrative controls
- Consider referral for medical evaluation

---

## CADS Implementation Notes

**Testing frequency:** Alberta's biennial schedule is different from BC's annual requirement. CADS systems operating in Alberta should flag when a worker's most recent periodic test exceeds:
- 12 months from the baseline (first periodic due)
- 24 months from the most recent periodic test (subsequent periodic due)

The `testing_frequency` field is set to `biennial` but the first periodic interval (12 months) should be tracked separately in implementation logic.

**Exit test:** Not required in Alberta. The `exit_test_required` flag is `false`. Exit testing may still be offered as best practice and documented as test_type `exit`.

**Retention:** Alberta's "duration of operations" requirement for noise records is open-ended. CADS systems should not delete Alberta records without explicit employer instruction and legal review.

**HPD documentation:** Not specifically required. The CADS questionnaire captures HPD type and consistency, which constitutes reasonable documentation under Alberta's due diligence standard.

---

## Differences from BC Profile

| Element | BC | Alberta |
|---|---|---|
| Testing frequency | Annual | Biennial (after first year) |
| Exit test | Required | Not required |
| HPD documentation | Required | Not required |
| Retention | Employment + 10 years | Duration of operations |

---

## Verification Items

- [ ] Confirm action level (82 dBA) — OHS Code Section 219
- [ ] Confirm first periodic at 12 months, then biennial — OHS Code Section 223
- [ ] Confirm HPD selection documentation is recommended only, not required
- [ ] Confirm noise record retention is "duration of operations" — OHS Code Section 220(2)(b)
- [ ] Confirm audiometric record retention — is there a specific requirement separate from noise records?
- [ ] Confirm exit test is recommended not required

---

*CADS Provincial Profile — Alberta*
*Draft for internal review — regulatory references subject to verification*
*© RoadPilotAI*
