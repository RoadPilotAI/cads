# CADS Provincial Profile — British Columbia
## CADS/BC v1.0

**Status:** Draft
**Date:** June 2026
**Regulatory Authority:** WorkSafeBC
**CADS Core Standard:** v1.0

---

## Profile Configuration

| Field | Value |
|---|---|
| `province_code` | `BC` |
| `province_name` | British Columbia |
| `regulatory_authority` | WorkSafeBC |
| `regulation_reference` | Workers Compensation Act — OHS Regulation Part 7, Sections 7.1–7.9 |
| `exposure_limit_dba` | 85 |
| `peak_limit_dbc` | 140 |
| `action_level_dba` | 82 |
| `hcp_required` | `true` |
| `hcp_worker_threshold` | null (no threshold — applies to any exposed worker) |
| `audiometric_testing_required` | `true` |
| `testing_trigger_dba` | 85 |
| `baseline_months` | 6 |
| `testing_frequency` | `annual` |
| `exit_test_required` | `true` |
| `hpd_selection_documentation_required` | `true` |
| `retention_years_minimum` | 10 (plus duration of employment) |
| `language` | `en` |
| `verification_date` | 2026-06-01 |

---

## Regulatory Context

### Overview

British Columbia has the most comprehensive hearing conservation regulatory framework in Canada. WorkSafeBC's OHS Regulation Part 7 establishes specific and enforceable requirements for noise assessment, hearing conservation program development, audiometric testing, hearing protection, and record keeping.

BC's framework serves as the benchmark for the CADS Core Standard. Where BC requirements are more stringent than other provinces, they are reflected as profile-specific flags rather than core requirements.

### Noise Exposure Limits

Workers must not be exposed to noise exceeding:
- **85 dBA Lex** (time-weighted average over an 8-hour shift)
- **140 dBC peak** (instantaneous peak level)

An action level of **82 dBA** applies — employers must implement a hearing conservation program when worker exposure meets or exceeds this level.

### Hearing Conservation Program

A written Hearing Conservation Program is required when workers are exposed at or above the action level of 82 dBA. The program must include:

- Noise exposure assessment
- Engineering and administrative noise controls
- Hearing protection devices and selection documentation
- Audiometric testing program
- Worker education and training
- Record keeping and program review

### Audiometric Testing Requirements

**Baseline test:** Must be conducted within 6 months of first exposure to hazardous noise. A pre-employment audiogram conducted within the previous 6 months may serve as the baseline.

**Periodic testing:** Annual. Workers exposed at or above the action level must receive annual audiometric testing.

**Exit test:** Required. An exit audiometric test must be conducted when a worker permanently leaves noise-exposed work. BC is the only Canadian jurisdiction that specifically mandates exit testing.

**Qualified tester:** Testing must be conducted by a qualified Industrial Audiometric Technician (IAT), physician, or audiologist.

**Equipment:** Audiometer must meet CSA Z107.6 specifications and be calibrated within the required intervals.

### Hearing Protection

Hearing protection is required when noise levels exceed 85 dBA Lex or 140 dBC peak, or when engineering and administrative controls cannot reduce exposure to below the exposure limit.

HPD selection must be documented, including the rationale for the chosen device and its adequacy for the worker's noise exposure level. CSA Z94.2 is the referenced standard for HPD selection.

### Record Keeping

Audiometric test records must be retained for the duration of the worker's employment plus a minimum of **10 years** after employment ends.

Workers have the right to access their own audiometric records.

### Standard Threshold Shift

WorkSafeBC uses the standard CADS definition: an average shift of **10 dB or more** at 2000, 3000, and 4000 Hz in either ear compared to the baseline audiogram. Age correction is permitted.

When an STS is detected:
- The worker must be informed in writing
- The cause must be investigated
- The HCP must be reviewed and corrective action taken
- Medical or audiological referral must be considered

---

## CADS Implementation Notes

**Exit test field:** The `exit_test_required` flag is `true` for BC. CADS-conformant systems operating in BC must prompt for an exit test when a worker's employment status changes to noise-exit.

**HPD selection documentation:** The `hpd_selection_documentation_required` flag is `true` for BC. The questionnaire's HPD type and consistency fields satisfy partial documentation requirements. Full HPD selection documentation — including NRR adequacy calculation — is an employer HCP obligation beyond the CADS test record.

**Annual testing frequency:** CADS systems operating in BC should flag when a worker's most recent periodic test exceeds 12 months from the previous test date.

**Retention:** CADS records for BC workers must be retained for a minimum of 10 years after the worker's last date of employment in noise-exposed work. Conformant systems should not purge BC records within this window.

---

## Verification Items

- [ ] Confirm action level (82 dBA) is correctly cited from OHS Regulation Section 7.2
- [ ] Confirm exit test requirement section reference (OHS Regulation Section 7.8 or 7.9)
- [ ] Confirm HPD selection documentation requirement section reference
- [ ] Confirm record retention requirement — duration of employment + 10 years or fixed 10 years?
- [ ] Confirm whether pre-employment audiogram within 6 months is accepted as baseline

---

*CADS Provincial Profile — British Columbia*
*Draft for internal review — regulatory references subject to verification*
*© AudioPilot*
