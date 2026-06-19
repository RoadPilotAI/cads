# Canadian Audiometric Data Standard
## CADS v1.0 — Formal Specification

**Status:** Draft
**Version:** 1.0.0
**Date:** June 2026
**Maintainer:** RoadPilotAI
**Repository:** [github.com/RoadPilotAI/cads](https://github.com/RoadPilotAI/cads)

---

## Table of Contents

- [1. Introduction](#1-introduction)
  - [1.1 Purpose](#11-purpose)
  - [1.2 Scope](#12-scope)
  - [1.3 Intended Audience](#13-intended-audience)
  - [1.4 Relationship to the CADS Platform](#14-relationship-to-the-cads-platform)
- [2. Normative References](#2-normative-references)
- [3. Terms and Definitions](#3-terms-and-definitions)
- [4. Standard Overview](#4-standard-overview)
  - [4.1 Design Principles](#41-design-principles)
  - [4.2 Record Architecture](#42-record-architecture)
  - [4.3 Data Format](#43-data-format)
- [5. Record Specifications](#5-record-specifications)
  - [5.1 Provider Record](#51-provider-record)
  - [5.2 Technician Record](#52-technician-record)
  - [5.3 Equipment Record](#53-equipment-record)
  - [5.4 Worker Record](#54-worker-record)
  - [5.5 Questionnaire Record](#55-questionnaire-record)
  - [5.6 Test Record](#56-test-record)
- [6. Compliance Calculations](#6-compliance-calculations)
  - [6.1 Standard Threshold Shift (STS)](#61-standard-threshold-shift-sts)
  - [6.2 Age Correction](#62-age-correction)
  - [6.3 Baseline Comparison Rules](#63-baseline-comparison-rules)
  - [6.4 Outcome Classification](#64-outcome-classification)
- [7. Province Configuration Schema](#7-province-configuration-schema)
  - [7.1 Configuration Fields](#71-configuration-fields)
  - [7.2 Reference Configurations](#72-reference-configurations)
- [8. Conformance Requirements](#8-conformance-requirements)
  - [8.1 Mandatory Fields](#81-mandatory-fields)
  - [8.2 Calculation Compliance](#82-calculation-compliance)
  - [8.3 Province Configuration Compliance](#83-province-configuration-compliance)
- [9. Versioning and Change Control](#9-versioning-and-change-control)
- [Appendix A — NOC 2021 Reference Codes](#appendix-a--noc-2021-reference-codes)
- [Appendix B — Age Correction Tables](#appendix-b--age-correction-tables)
- [Appendix C — Changelog](#appendix-c--changelog)

---

## 1. Introduction

### 1.1 Purpose

The Canadian Audiometric Data Standard (CADS) defines a national data exchange format for industrial audiometric testing conducted under occupational health and safety regulations across Canadian provinces and territories.

CADS enables consistent capture, exchange, and analysis of hearing conservation data between field technicians, hearing test companies, industrial employers, and provincial regulators — regardless of which software platform generates or receives the data.

### 1.2 Scope

This standard applies to:

- Audiometric testing conducted as part of a mandated Hearing Conservation Program (HCP) under provincial occupational health and safety legislation
- Baseline, periodic, and exit audiometric tests performed by qualified Industrial Audiometric Technicians (IATs), physicians, or audiologists
- Data exchange between field applications, administrative platforms, employer portals, and provincial regulatory systems

This standard does not apply to:

- Clinical audiometric testing conducted for diagnostic or therapeutic purposes
- Hearing aid fitting or dispensing
- Noise exposure assessment methodologies (noise dosimetry, area monitoring)

### 1.3 Intended Audience

- Software developers implementing CADS-compliant applications
- Industrial Audiometric Technicians and hearing test companies
- Industrial employers managing Hearing Conservation Programs
- Provincial occupational health and safety regulators
- Researchers working with Canadian occupational hearing health data

### 1.4 Relationship to the CADS Platform

The Canadian Audiometric Data System is the reference implementation of this standard. Compliance with this standard does not require use of the CADS platform. Any platform that correctly implements the record specifications, compliance calculations, and province configuration schema defined in this document may claim CADS conformance.

---

## 2. Normative References

The following documents are referenced by this standard. In the event of conflict, this standard takes precedence for data formatting purposes; the referenced regulations take precedence for compliance requirements.

| Reference | Document |
|---|---|
| WorkSafeBC OHS Regulation Part 7 | Noise, Vibration, Radiation and Temperature — British Columbia |
| Alberta OHS Code Part 16 | Noise Exposure — Alberta |
| Saskatchewan OHS Regulations Part 7 | Noise — Saskatchewan |
| NOC 2021 | National Occupational Classification, 5th Edition — Employment and Social Development Canada |
| ISO 8253-1 | Acoustics — Audiometric test methods — Part 1: Pure-tone air and bone conduction audiometry |
| NIOSH 1998 | Criteria for a Recommended Standard: Occupational Noise Exposure |

---

## 3. Terms and Definitions

| Term | Definition |
|---|---|
| **Action Level** | The noise exposure level at which an employer is required to implement a Hearing Conservation Program. Currently 82 dBA TWA across all supported provinces. |
| **Age Correction** | An adjustment applied to audiometric thresholds to account for expected age-related hearing change (presbycusis), allowing separation of occupational hearing loss from age-related change. |
| **Audiogram** | A graphical or tabular representation of an individual's hearing thresholds at specified frequencies. |
| **Baseline Audiogram** | The initial audiometric test result used as the reference point for comparison in subsequent periodic testing. |
| **dB HL** | Decibels Hearing Level. The unit of measurement for audiometric thresholds, referenced to standardized normal hearing levels. |
| **Exit Audiogram** | An audiometric test conducted when a worker leaves noise-exposed employment, providing a final record of their occupational hearing status. |
| **HCP** | Hearing Conservation Program. A documented, employer-managed program that includes noise assessment, hearing protection, audiometric testing, worker education, and record keeping. |
| **HPD** | Hearing Protection Device. Personal protective equipment worn to reduce noise exposure at the ear, including foam plugs, pre-moulded plugs, earmuffs, and custom-moulded devices. |
| **IAT** | Industrial Audiometric Technician. A certified technician qualified to conduct occupational audiometric testing under applicable provincial regulations. |
| **NIHL** | Noise-Induced Hearing Loss. Permanent sensorineural hearing loss caused by excessive noise exposure. |
| **NOC** | National Occupational Classification. Canada's national system for classifying occupations, maintained by Employment and Social Development Canada. This standard uses NOC 2021 (5th Edition). |
| **Periodic Audiogram** | An audiometric test conducted at regular intervals (typically annually) to monitor changes in a worker's hearing thresholds relative to baseline. |
| **Province Config** | A province-specific configuration file that defines regulatory variations, required fields, and system endpoints for a given jurisdiction. |
| **Record UUID** | A universally unique identifier assigned to each data record at creation time, enabling unambiguous identification across systems. |
| **STS** | Standard Threshold Shift. A clinically significant change in hearing thresholds from baseline, defined in this standard as an average shift of 10 dB or greater at 2000, 3000, and 4000 Hz in either ear. |
| **TWA** | Time-Weighted Average. The average noise exposure level over an 8-hour work period, calculated using a 3 dB exchange rate. |

---

## 4. Standard Overview

### 4.1 Design Principles

CADS is designed around the following principles:

**Simplicity.** The standard captures what is needed for occupational hearing conservation compliance. It does not attempt to capture clinical diagnostic data beyond the scope of industrial audiometric programs.

**Province-configurability.** Meaningful regulatory differences between provinces are handled through configuration, not structural variation. The core data model is identical across all provinces.

**Interoperability.** Records are self-describing and include version metadata, enabling future evolution without breaking existing implementations.

**Privacy by design.** Worker identifiers are anonymized UUIDs. Date of birth is captured for calculation purposes but is not required in provincial data transfers. Personally identifiable information remains within the control of the hearing test company and employer.

**Auditability.** Every record includes creation timestamp, technician identifier, and equipment identifier, enabling a complete audit trail from test to provincial submission.

### 4.2 Record Architecture

CADS defines six record types. Records reference each other by UUID:

```
Provider Record
  └── Technician Record (belongs to Provider)
        └── Test Record (conducted by Technician)
              ├── Worker Record (subject of Test)
              ├── Equipment Record (used in Test)
              └── Questionnaire Record (collected during Test)
```

**Record types and their purpose:**

| Record Type | Purpose |
|---|---|
| Provider Record | Identifies the hearing test company conducting the program |
| Technician Record | Identifies the qualified individual conducting the test |
| Equipment Record | Identifies the audiometer and its calibration status |
| Worker Record | Identifies the worker being tested (anonymized) |
| Questionnaire Record | Captures pre-test health and exposure history |
| Test Record | Captures the audiometric results and compliance calculations |

### 4.3 Data Format

CADS records are expressed as JSON objects. All field names use `snake_case`. All dates use ISO 8601 format (`YYYY-MM-DD`). All datetimes use ISO 8601 format with UTC offset (`YYYY-MM-DDTHH:MM:SS±HH:MM`). All UUIDs use the standard UUID v4 format.

**Example record envelope:**

```json
{
  "cads_version": "1.0.0",
  "record_type": "test",
  "record_uuid": "550e8400-e29b-41d4-a716-446655440000",
  "province": "AB",
  "created_at": "2026-06-15T14:32:00-06:00",
  "payload": { ... }
}
```

---

## 5. Record Specifications

Field requirement indicators:

- **R** — Required. Must be present and non-null.
- **O** — Optional. May be omitted or null.
- **C** — Conditional. Required when a specified condition is met.

---

### 5.1 Provider Record

Identifies the hearing test company or individual practitioner delivering the audiometric program.

| Field | Type | Req | Description | Valid Values / Constraints |
|---|---|---|---|---|
| `provider_uuid` | string | R | Unique identifier for this provider | UUID v4 |
| `company_name` | string | R | Legal name of the hearing test company | Max 200 chars |
| `province_of_registration` | string | R | Province where the company is registered | ISO 3166-2 CA province code |
| `contact_name` | string | O | Primary contact name | Max 100 chars |
| `contact_email` | string | O | Primary contact email | Valid email format |
| `cads_version` | string | R | CADS version this record was created under | Semver format e.g. `1.0.0` |
| `created_at` | datetime | R | Record creation timestamp | ISO 8601 with UTC offset |

---

### 5.2 Technician Record

Identifies the qualified individual who conducted the audiometric test.

| Field | Type | Req | Description | Valid Values / Constraints |
|---|---|---|---|---|
| `technician_uuid` | string | R | Unique identifier for this technician | UUID v4 |
| `provider_uuid` | string | R | Reference to the Provider Record | UUID v4 |
| `credential_type` | string | R | Type of qualification held | `IAT` `physician` `audiologist` |
| `certification_number` | string | R | Credential or certification number | Max 50 chars |
| `province_of_certification` | string | R | Province where credential was issued | ISO 3166-2 CA province code |
| `cads_version` | string | R | CADS version this record was created under | Semver format |
| `created_at` | datetime | R | Record creation timestamp | ISO 8601 with UTC offset |

---

### 5.3 Equipment Record

Identifies the audiometer used in testing and its calibration status. A valid, current calibration is a conformance requirement.

| Field | Type | Req | Description | Valid Values / Constraints |
|---|---|---|---|---|
| `equipment_uuid` | string | R | Unique identifier for this audiometer | UUID v4 |
| `provider_uuid` | string | R | Reference to the Provider Record | UUID v4 |
| `make` | string | R | Audiometer manufacturer | Max 100 chars |
| `model` | string | R | Audiometer model name | Max 100 chars |
| `serial_number` | string | R | Manufacturer serial number | Max 100 chars |
| `audiometer_type` | string | R | Classification of audiometer | `manual` `microprocessor` `automated` |
| `last_biological_calibration` | date | R | Date of most recent biological calibration | ISO 8601 date. Must be within 1 year of test date. |
| `last_acoustic_calibration` | date | R | Date of most recent electroacoustic calibration | ISO 8601 date. Must be within 1 year of test date. |
| `calibration_certificate_ref` | string | O | Reference number of calibration certificate | Max 100 chars |
| `firmware_version` | string | O | Audiometer firmware version if applicable | Max 50 chars |
| `cads_version` | string | R | CADS version this record was created under | Semver format |
| `created_at` | datetime | R | Record creation timestamp | ISO 8601 with UTC offset |
| `updated_at` | datetime | R | Record last updated timestamp | ISO 8601 with UTC offset |

---

### 5.4 Worker Record

Identifies the worker being tested. Worker identity is anonymized — personally identifiable information does not leave the control of the employer and hearing test company.

| Field | Type | Req | Description | Valid Values / Constraints |
|---|---|---|---|---|
| `worker_uuid` | string | R | Unique identifier for this worker | UUID v4. Stable across tests for the same worker. |
| `employer_uuid` | string | R | Reference to the employer | UUID v4 |
| `date_of_birth` | date | R | Worker's date of birth | ISO 8601 date. Required for age correction calculations. |
| `sex` | string | R | Biological sex for normative reference purposes | `M` `F` |
| `province_of_employment` | string | R | Province where the worker is primarily employed | ISO 3166-2 CA province code |
| `noc_code` | string | R | National Occupational Classification code | 5-digit NOC 2021 code e.g. `73200` |
| `noise_exposure_group` | string | O | Employer-assigned noise exposure group label | Max 100 chars |
| `years_noise_exposed` | integer | O | Approximate years in noise-exposed employment | 0–60 |
| `cads_version` | string | R | CADS version this record was created under | Semver format |
| `created_at` | datetime | R | Record creation timestamp | ISO 8601 with UTC offset |
| `updated_at` | datetime | R | Record last updated timestamp | ISO 8601 with UTC offset |

---

### 5.5 Questionnaire Record

Captures pre-test health and exposure history collected from the worker before testing. See `standard/questionnaire.md` for the standardized questionnaire instrument.

| Field | Type | Req | Description | Valid Values / Constraints |
|---|---|---|---|---|
| `questionnaire_uuid` | string | R | Unique identifier for this questionnaire | UUID v4 |
| `test_uuid` | string | R | Reference to the associated Test Record | UUID v4 |
| `worker_uuid` | string | R | Reference to the Worker Record | UUID v4 |
| `hours_since_noise_exposure` | decimal | R | Hours elapsed since last significant noise exposure | 0.0–168.0. Provincial minimum is 14 hours. |
| `previous_noise_employment` | boolean | R | Prior employment in noise-exposed roles | `true` `false` |
| `recreational_shooting` | boolean | R | Regular recreational shooting or hunting | `true` `false` |
| `recreational_shooting_frequency` | string | C | Frequency if recreational_shooting is true | `occasional` `regular` Required if `recreational_shooting` is `true` |
| `power_tools_use` | boolean | R | Regular use of power tools outside work | `true` `false` |
| `motorsports` | boolean | R | Regular motorsports participation | `true` `false` |
| `music_performance` | boolean | R | Regular music performance or attendance | `true` `false` |
| `hpd_type` | string | R | Type of hearing protection used at work | `foam_plug` `premolded_plug` `earmuff` `custom` `combination` `none` |
| `hpd_consistency` | string | R | Self-reported consistency of HPD use | `always` `usually` `sometimes` `never` `not_applicable` |
| `hpd_fit_training_received` | boolean | R | Has the worker received HPD fit training | `true` `false` |
| `ear_surgery_history` | boolean | R | History of ear surgery | `true` `false` |
| `ear_infection_history` | boolean | R | History of chronic ear infections | `true` `false` |
| `ototoxic_medication` | boolean | R | Current use of known ototoxic medications | `true` `false` |
| `tinnitus_present` | boolean | R | Presence of tinnitus | `true` `false` |
| `tinnitus_frequency` | string | C | Frequency of tinnitus if present | `constant` `frequent` `occasional` `rare`. Required if `tinnitus_present` is `true` |
| `self_reported_hearing_difficulty` | boolean | R | Self-reported difficulty hearing in daily life | `true` `false` |
| `worker_cooperation` | string | R | Technician assessment of worker cooperation during test | `good` `fair` `poor` |
| `cads_version` | string | R | CADS version this record was created under | Semver format |
| `created_at` | datetime | R | Record creation timestamp | ISO 8601 with UTC offset |

---

### 5.6 Test Record

The core record of the standard. Captures audiometric thresholds, compliance calculations, and outcomes for a single audiometric test event.

#### 5.6.1 Test Identification and Context

| Field | Type | Req | Description | Valid Values / Constraints |
|---|---|---|---|---|
| `test_uuid` | string | R | Unique identifier for this test | UUID v4 |
| `worker_uuid` | string | R | Reference to the Worker Record | UUID v4 |
| `technician_uuid` | string | R | Reference to the Technician Record | UUID v4 |
| `equipment_uuid` | string | R | Reference to the Equipment Record | UUID v4 |
| `questionnaire_uuid` | string | R | Reference to the Questionnaire Record | UUID v4 |
| `province` | string | R | Province in which the test was conducted | ISO 3166-2 CA province code |
| `test_date` | date | R | Date the test was conducted | ISO 8601 date |
| `test_time` | string | R | Time the test was conducted | HH:MM in 24-hour format |
| `test_type` | string | R | Category of this test | `baseline` `periodic` `exit` `retest` |
| `baseline_test_uuid` | string | C | Reference to the baseline Test Record used for STS comparison | UUID v4. Required for `periodic`, `exit`, and `retest` test types. |

#### 5.6.2 Otoscopy

| Field | Type | Req | Description | Valid Values / Constraints |
|---|---|---|---|---|
| `otoscopy_right` | string | R | Otoscopy result for right ear | `normal` `abnormal` `not_performed` |
| `otoscopy_left` | string | R | Otoscopy result for left ear | `normal` `abnormal` `not_performed` |
| `otoscopy_notes` | string | O | Technician notes on otoscopy findings | Max 500 chars |

#### 5.6.3 Audiometric Thresholds

All threshold values are expressed in dB HL (decibels Hearing Level). Valid range is -10 to 120 dB HL. A value of `null` indicates the frequency was not tested or the result was not obtainable.

**Right Ear Thresholds:**

| Field | Type | Req | Description |
|---|---|---|---|
| `right_500` | integer | R | Right ear threshold at 500 Hz |
| `right_1000` | integer | R | Right ear threshold at 1000 Hz |
| `right_2000` | integer | R | Right ear threshold at 2000 Hz |
| `right_3000` | integer | R | Right ear threshold at 3000 Hz |
| `right_4000` | integer | R | Right ear threshold at 4000 Hz |
| `right_6000` | integer | O | Right ear threshold at 6000 Hz |
| `right_8000` | integer | O | Right ear threshold at 8000 Hz |

**Left Ear Thresholds:**

| Field | Type | Req | Description |
|---|---|---|---|
| `left_500` | integer | R | Left ear threshold at 500 Hz |
| `left_1000` | integer | R | Left ear threshold at 1000 Hz |
| `left_2000` | integer | R | Left ear threshold at 2000 Hz |
| `left_3000` | integer | R | Left ear threshold at 3000 Hz |
| `left_4000` | integer | R | Left ear threshold at 4000 Hz |
| `left_6000` | integer | O | Left ear threshold at 6000 Hz |
| `left_8000` | integer | O | Left ear threshold at 8000 Hz |

> **Note:** 500 Hz and 1000 Hz are required for completeness of the audiogram. 2000, 3000, and 4000 Hz are required for STS calculation. 6000 and 8000 Hz are optional but strongly recommended as early indicators of noise-induced hearing loss.

#### 5.6.4 STS Calculations

| Field | Type | Req | Description | Valid Values / Constraints |
|---|---|---|---|---|
| `sts_right` | boolean | R | STS detected in right ear | `true` `false` |
| `sts_left` | boolean | R | STS detected in left ear | `true` `false` |
| `sts_right_value` | decimal | C | Calculated STS value for right ear in dB | Required if `test_type` is not `baseline` |
| `sts_left_value` | decimal | C | Calculated STS value for left ear in dB | Required if `test_type` is not `baseline` |
| `age_correction_applied` | boolean | R | Whether age correction was applied to STS calculation | `true` `false` |
| `age_correction_right` | decimal | C | Age correction value applied to right ear in dB | Required if `age_correction_applied` is `true` |
| `age_correction_left` | decimal | C | Age correction value applied to left ear in dB | Required if `age_correction_applied` is `true` |

#### 5.6.5 Outcome and Follow-Up

| Field | Type | Req | Description | Valid Values / Constraints |
|---|---|---|---|---|
| `outcome` | string | R | Overall test outcome classification | `normal` `sts_detected` `referral_required` `retest_required` |
| `referral_type` | string | C | Type of referral indicated | `medical` `audiological` `none`. Required if `outcome` is `referral_required` |
| `follow_up_interval_months` | integer | O | Recommended follow-up interval in months | 1–12 |
| `physician_referral_flag` | boolean | R | Whether a physician referral is indicated | `true` `false` |
| `notes` | string | O | Technician notes on the test | Max 1000 chars |

#### 5.6.6 Record Metadata

| Field | Type | Req | Description | Valid Values / Constraints |
|---|---|---|---|---|
| `cads_version` | string | R | CADS version this record was created under | Semver format e.g. `1.0.0` |
| `sync_status` | string | R | Synchronization status of this record | `pending` `synced` `failed` |
| `created_at` | datetime | R | Record creation timestamp | ISO 8601 with UTC offset |
| `updated_at` | datetime | R | Record last updated timestamp | ISO 8601 with UTC offset |
| `submitted_at` | datetime | O | Timestamp of provincial submission if applicable | ISO 8601 with UTC offset |

---

## 6. Compliance Calculations

### 6.1 Standard Threshold Shift (STS)

A Standard Threshold Shift is defined as a change in hearing threshold, relative to the baseline audiogram, of an average of **10 dB or more** at **2000, 3000, and 4000 Hz** in either ear.

**Calculation:**

```
STS_right = mean(right_2000_current - right_2000_baseline,
                 right_3000_current - right_3000_baseline,
                 right_4000_current - right_4000_baseline)

STS_left  = mean(left_2000_current - left_2000_baseline,
                 left_3000_current - left_3000_baseline,
                 left_4000_current - left_4000_baseline)
```

If age correction is applied, the corrected baseline values are used in place of the raw baseline values (see Section 6.2).

**STS flag is set to `true` when the calculated value is ≥ 10.0 dB.**

A positive STS in either ear triggers the outcome classification process described in Section 6.4.

### 6.2 Age Correction

Age correction may be applied to adjust baseline thresholds upward to account for expected age-related hearing change (presbycusis), isolating occupational hearing loss from normal ageing.

Age correction is **permitted but not mandatory** across all supported provinces. The `age_correction_applied` field must accurately reflect whether correction was used.

Age correction values are taken from the NIOSH 1998 tables (Annex B of the Criteria for a Recommended Standard: Occupational Noise Exposure). See Appendix B for the reference correction values.

**Application:**

```
corrected_baseline_frequency = baseline_threshold_frequency + age_correction_value
STS_value = current_threshold_frequency - corrected_baseline_frequency
```

The age correction value is always additive to the baseline (i.e., it increases the baseline threshold, making it harder to trigger an STS flag). This is the established convention.

### 6.3 Baseline Comparison Rules

1. Every test of type `periodic`, `exit`, or `retest` must reference a `baseline_test_uuid`.
2. The referenced baseline must be of type `baseline`.
3. If a worker's baseline has been revised (e.g., following a confirmed STS and re-established baseline), the most recent valid baseline is used.
4. A baseline may not reference another test as its baseline.
5. The baseline and comparison test must be for the same `worker_uuid`.

### 6.4 Outcome Classification

Outcomes are assigned according to the following hierarchy:

| Priority | Outcome | Condition |
|---|---|---|
| 1 | `retest_required` | Worker cooperation rated `poor`, or otoscopy result is `abnormal`, or thresholds are inconsistent with prior tests indicating reliability concern |
| 2 | `referral_required` | STS detected AND shift warrants medical or audiological evaluation per provincial protocol |
| 3 | `sts_detected` | STS calculated as ≥ 10 dB in either ear, referral not yet indicated |
| 4 | `normal` | No STS detected, no otoscopy abnormality, no reliability concern |

---

## 7. Province Configuration Schema

### 7.1 Configuration Fields

Each supported province is defined by a configuration object with the following fields:

| Field | Type | Description | Valid Values |
|---|---|---|---|
| `province_code` | string | ISO 3166-2 CA province code | e.g. `BC` `AB` `SK` |
| `province_name` | string | Full province name | |
| `regulatory_authority` | string | Name of the occupational health regulator | |
| `regulation_reference` | string | Specific regulation citation | |
| `exit_test_required` | boolean | Whether exit testing is mandatory | `true` `false` |
| `hpd_selection_documentation_required` | boolean | Whether HPD selection must be formally documented | `true` `false` |
| `retention_years_minimum` | integer | Minimum record retention period in years | |
| `language` | string | Primary language for this province | `en` `fr` |
| `api_endpoint` | string | Provincial API endpoint if applicable | Valid URL or `null` |
| `billing_webhook` | string | Billing event endpoint if applicable | Valid URL or `null` |

### 7.2 Reference Configurations

**British Columbia**

```json
{
  "province_code": "BC",
  "province_name": "British Columbia",
  "regulatory_authority": "WorkSafeBC",
  "regulation_reference": "OHS Regulation Part 7",
  "exit_test_required": true,
  "hpd_selection_documentation_required": true,
  "retention_years_minimum": 10,
  "language": "en",
  "api_endpoint": null,
  "billing_webhook": null
}
```

**Alberta**

```json
{
  "province_code": "AB",
  "province_name": "Alberta",
  "regulatory_authority": "Alberta OHS",
  "regulation_reference": "OHS Code Part 16",
  "exit_test_required": false,
  "hpd_selection_documentation_required": false,
  "retention_years_minimum": 10,
  "language": "en",
  "api_endpoint": null,
  "billing_webhook": null
}
```

**Saskatchewan**

```json
{
  "province_code": "SK",
  "province_name": "Saskatchewan",
  "regulatory_authority": "Saskatchewan OHS",
  "regulation_reference": "OHS Regulations Part 7",
  "exit_test_required": false,
  "hpd_selection_documentation_required": false,
  "retention_years_minimum": 10,
  "language": "en",
  "api_endpoint": null,
  "billing_webhook": null
}
```

---

## 8. Conformance Requirements

### 8.1 Mandatory Fields

A CADS-conformant implementation must:

- Include all fields marked **R** (Required) in every record submitted
- Populate conditional fields marked **C** when the specified condition is met
- Use the exact field names specified in this document (snake_case)
- Use the exact valid values specified for enumerated fields
- Generate a unique UUID v4 for every record UUID field at creation time
- Include `cads_version` in every record reflecting the version of this standard under which the record was created

### 8.2 Calculation Compliance

A CADS-conformant implementation must:

- Calculate STS using the average shift at 2000, 3000, and 4000 Hz as defined in Section 6.1
- Apply age correction only from the NIOSH 1998 reference tables in Appendix B
- Accurately record whether age correction was applied in `age_correction_applied`
- Reference the correct baseline test in `baseline_test_uuid` for all non-baseline test types
- Assign outcome classifications following the hierarchy defined in Section 6.4

### 8.3 Province Configuration Compliance

A CADS-conformant implementation must:

- Apply the province configuration for the province specified in the Test Record's `province` field
- Enforce mandatory fields that are required by the province configuration (e.g., exit test documentation in BC)
- Not override province configuration with application defaults

---

## 9. Versioning and Change Control

CADS uses semantic versioning (`MAJOR.MINOR.PATCH`):

- **MAJOR** version increments indicate breaking changes to the record schema. Existing records remain valid under their original version. Implementations must declare which major version they support.
- **MINOR** version increments indicate new optional fields or new province configurations. Backward compatible.
- **PATCH** version increments indicate corrections, clarifications, or editorial changes. No schema changes.

The `cads_version` field in every record identifies the version of this standard under which the record was created. Systems receiving CADS records must be able to process records from any minor or patch version within the same major version.

Province configuration additions (new provinces) are minor version increments.

---

## Appendix A — NOC 2021 Reference Codes

The following NOC 2021 codes represent the occupational categories most commonly encountered in industrial hearing conservation programs. This list is illustrative, not exhaustive.

| NOC Code | Title |
|---|---|
| 72010 | Contractors and supervisors, oil and gas drilling and services |
| 72020 | Contractors and supervisors, mining and quarrying |
| 72100 | Machinists and machining and tooling inspectors |
| 72200 | Electricians (except industrial and power system) |
| 72300 | Plumbers |
| 72310 | Steamfitters, pipefitters and sprinkler system installers |
| 72400 | Carpenters |
| 72410 | Cabinetmakers |
| 73100 | Crane operators |
| 73200 | Drillers and blasters — surface mining, quarrying and construction |
| 73201 | Oil and gas well drillers, servicers, testers and related workers |
| 73300 | Heavy equipment operators (except crane) |
| 73301 | Longshore workers |
| 73400 | Railway and yard locomotive engineers |
| 74100 | Transport truck drivers |
| 75100 | Logging machinery operators |
| 75200 | Agricultural equipment operators |
| 82010 | Supervisors, oil and gas drilling and services |
| 82020 | Supervisors, mining and quarrying |
| 92010 | Supervisors, mineral ore processing and metallurgy |
| 93100 | Sawmill machine operators |
| 93102 | Pulp mill operators |
| 95100 | Labourers in processing, manufacturing and utilities |

Full NOC 2021 code listings are available from Employment and Social Development Canada at [noc.esdc.gc.ca](https://noc.esdc.gc.ca).

---

## Appendix B — Age Correction Tables

Age correction values represent the expected increase in hearing threshold due to presbycusis (age-related hearing change) for a given sex and age. Values are expressed in dB and are subtracted from the shift to reduce the likelihood of flagging age-related change as occupational STS.

Values below are derived from NIOSH 1998 (Appendix B, Tables B-1 and B-2). The correction is applied as the difference between the age correction at the current test age and the age correction at the baseline test age.

**Male Age Correction (dB HL)**

| Age | 2000 Hz | 3000 Hz | 4000 Hz |
|---|---|---|---|
| 20 | 0 | 0 | 0 |
| 25 | 0 | 1 | 1 |
| 30 | 1 | 2 | 3 |
| 35 | 1 | 3 | 5 |
| 40 | 2 | 5 | 7 |
| 45 | 3 | 7 | 10 |
| 50 | 5 | 9 | 13 |
| 55 | 7 | 12 | 16 |
| 60 | 9 | 15 | 20 |

**Female Age Correction (dB HL)**

| Age | 2000 Hz | 3000 Hz | 4000 Hz |
|---|---|---|---|
| 20 | 0 | 0 | 0 |
| 25 | 0 | 0 | 1 |
| 30 | 1 | 1 | 2 |
| 35 | 1 | 2 | 3 |
| 40 | 2 | 3 | 5 |
| 45 | 2 | 4 | 7 |
| 50 | 3 | 5 | 8 |
| 55 | 4 | 7 | 10 |
| 60 | 5 | 9 | 13 |

For ages between table values, linear interpolation is applied. For ages below 20 or above 60, the nearest table value is used without extrapolation.

---

## Appendix C — Changelog

| Version | Date | Description |
|---|---|---|
| 1.0.0-draft | June 2026 | Initial draft specification |

---

*Canadian Audiometric Data Standard (CADS) v1.0*
*© RoadPilotAI — Open specification. See repository for licensing terms.*
