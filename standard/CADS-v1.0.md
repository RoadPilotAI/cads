# Canadian Audiometric Data Standard
## CADS v1.0 — Formal Specification

**Status:** Draft
**Version:** 1.0.1
**Date:** June 2026
**Maintainer:** RoadPilotAI
**Repository:** [github.com/RoadPilotAI/cads](https://github.com/RoadPilotAI/cads)

---

## Table of Contents

- [1. Introduction](#1-introduction)
  - [1.1 Purpose](#11-purpose)
  - [1.2 Scope](#12-scope)
  - [1.3 Intended Audience](#13-intended-audience)
- [2. Normative References](#2-normative-references)
- [3. Terms and Definitions](#3-terms-and-definitions)
- [4. Standard Overview](#4-standard-overview)
  - [4.1 Design Principles](#41-design-principles)
  - [4.2 Two-Tier Architecture](#42-two-tier-architecture)
  - [4.3 Record Architecture](#43-record-architecture)
  - [4.4 Data Format](#44-data-format)
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
- [7. Provincial Profile Schema](#7-provincial-profile-schema)
  - [7.1 Purpose of Provincial Profiles](#71-purpose-of-provincial-profiles)
  - [7.2 Profile Field Definitions](#72-profile-field-definitions)
  - [7.3 Profile Documents](#73-profile-documents)
- [8. Conformance Requirements](#8-conformance-requirements)
  - [8.1 Core Conformance](#81-core-conformance)
  - [8.2 Calculation Conformance](#82-calculation-conformance)
  - [8.3 Profile Conformance](#83-profile-conformance)
- [9. Versioning and Change Control](#9-versioning-and-change-control)
- [Appendix A — NOC 2021 Reference Codes](#appendix-a--noc-2021-reference-codes)
- [Appendix B — Age Correction Tables](#appendix-b--age-correction-tables)
- [Appendix C — Changelog](#appendix-c--changelog)

---

## 1. Introduction

### 1.1 Purpose

The Canadian Audiometric Data Standard (CADS) defines the national data exchange format for industrial audiometric testing conducted in Canada.

The standard governs how audiometric data is captured, structured, and exchanged when testing is conducted. It makes no determination about when testing is required — that is the domain of provincial and territorial occupational health and safety legislation. In jurisdictions where audiometric testing is mandated by regulation, CADS provides the data standard for that testing. In jurisdictions where testing is conducted as best practice under general duty of care, CADS provides the same standard. The data captured is identical regardless of the regulatory context in which testing occurs.

CADS exists to create consistency where none currently exists — across providers, across provinces, and across time.

### 1.2 Scope

This standard applies to industrial audiometric testing conducted as part of occupational health and safety programs across Canada, including:

- Baseline, periodic, and exit audiometric tests performed by qualified Industrial Audiometric Technicians (IATs), physicians, or audiologists
- Audiometric testing conducted under provincial and territorial occupational health and safety legislation
- Audiometric testing conducted as best practice under employer general duty of care obligations
- Data exchange between field applications, administrative platforms, employer systems, and provincial regulatory systems

This standard explicitly does not govern:

- Whether audiometric testing is required — that is determined by applicable provincial or territorial legislation
- How frequently testing must be conducted — that is a provincial profile matter addressed in jurisdiction-specific profile documents
- Whether a Hearing Conservation Program is required — that is a provincial legislative matter
- Clinical audiometric testing conducted for diagnostic or therapeutic purposes outside occupational health contexts
- Hearing aid fitting or dispensing

### 1.3 Intended Audience

- Software developers implementing CADS-conformant applications
- Industrial Audiometric Technicians and hearing test companies
- Industrial employers managing occupational hearing health programs
- Provincial and territorial occupational health and safety regulators
- Occupational health researchers working with Canadian audiometric data

---

## 2. Normative References

The following documents informed the development of this standard. Where audiometric methodology is described, this standard aligns with CSA Z107.6 as the Canadian reference. Provincial and territorial regulations are listed as informing references; in the event of conflict between this standard and applicable legislation, legislation takes precedence.

| Reference | Document |
|---|---|
| CSA Z107.6 | Audiometric Testing for Use in Hearing Loss Prevention Programs — Canadian Standards Association |
| CSA Z94.2 | Hearing Protection Devices — Performance, Selection, Care and Use — Canadian Standards Association |
| CSA Z1007 | Hearing Loss Prevention Program Management — Canadian Standards Association |
| NIOSH 1998 | Criteria for a Recommended Standard: Occupational Noise Exposure — National Institute for Occupational Safety and Health |
| ISO 8253-1 | Acoustics — Audiometric Test Methods — Part 1: Pure-tone air and bone conduction audiometry |
| NOC 2021 | National Occupational Classification, 5th Edition — Employment and Social Development Canada |
| WorkSafeBC OHS Regulation Part 7 | Noise, Vibration, Radiation and Temperature — British Columbia |
| Alberta OHS Code Part 16 | Noise Exposure — Alberta |
| Saskatchewan OHS Regulations Part 8 | Noise Control and Hearing Conservation — Saskatchewan |
| Manitoba WSH Regulation Part 12 | Noise Control and Hearing Conservation — Manitoba |
| Ontario O. Reg. 381/15 | Noise — Ontario |
| CNESST RSST Division XV | Bruit — Quebec |
| PEI OHS General Regulations Part 8 | Noise Control and Hearing Conservation — Prince Edward Island |
| NL OHS Regulations Part VI | Noise — Newfoundland and Labrador |

---

## 3. Terms and Definitions

| Term | Definition |
|---|---|
| **Action Level** | The noise exposure level above which specific regulatory obligations are triggered. Varies by jurisdiction — commonly 80 or 82 dBA TWA across Canadian provinces. |
| **Age Correction** | An adjustment applied to audiometric thresholds to account for expected age-related hearing change (presbycusis), allowing separation of occupational hearing loss from normal ageing. |
| **Audiogram** | A graphical or tabular representation of an individual's hearing thresholds at specified frequencies. |
| **Baseline Audiogram** | The initial audiometric test result used as the reference point for comparison in subsequent periodic testing. |
| **CADS Core Standard** | The universal requirements of this standard, applicable to all industrial audiometric testing conducted in Canada regardless of jurisdiction. |
| **CADS Provincial Profile** | A jurisdiction-specific document that defines the regulatory context in which the CADS Core Standard is applied. Provincial profiles do not modify the core standard — they extend it with jurisdiction-specific parameters. |
| **dB HL** | Decibels Hearing Level. The unit of measurement for audiometric thresholds, referenced to standardized normal hearing levels. |
| **Exit Audiogram** | An audiometric test conducted when a worker leaves noise-exposed employment, providing a final record of their occupational hearing status. |
| **HCP** | Hearing Conservation Program. A documented, employer-managed program that may include noise assessment, hearing protection, audiometric testing, worker education, and record keeping. Whether a formal HCP is required is a provincial legislative matter. |
| **HPD** | Hearing Protection Device. Personal protective equipment worn to reduce noise exposure at the ear. |
| **IAT** | Industrial Audiometric Technician. A certified technician qualified to conduct occupational audiometric testing under applicable provincial regulations. |
| **NIHL** | Noise-Induced Hearing Loss. Permanent sensorineural hearing loss caused by excessive noise exposure. |
| **NOC** | National Occupational Classification. Canada's national system for classifying occupations, maintained by Employment and Social Development Canada. This standard uses NOC 2021 (5th Edition). |
| **Periodic Audiogram** | An audiometric test conducted at regular intervals to monitor changes in a worker's hearing thresholds relative to baseline. Testing frequency is defined by applicable provincial legislation or employer program design. |
| **Proxy Estimation** | The practice of using available contextual information — time of day, shift schedule, visual observation, worker statements — to produce a reasonable estimate when a direct answer is unavailable or unreliable. An accepted and documented practice under this standard for contextual questionnaire fields. |
| **Record UUID** | A universally unique identifier assigned to each data record at creation time. |
| **STS** | Standard Threshold Shift. A clinically significant change in hearing thresholds from baseline, defined in this standard as an average shift of 10 dB or more at 2000, 3000, and 4000 Hz in either ear. This definition is consistent across all Canadian jurisdictions that define STS. |
| **TWA** | Time-Weighted Average. The average noise exposure level over an 8-hour work period, calculated using a 3 dB exchange rate. |

---

## 4. Standard Overview

### 4.1 Design Principles

**Independence.** The CADS Core Standard is independent of any specific software implementation, regulatory framework, and provincial jurisdiction. It does not require any particular technology, platform, or system to implement.

**Universality.** The core standard applies uniformly to all industrial audiometric testing conducted in Canada. Provincial and territorial regulatory differences are addressed through jurisdiction-specific profiles that extend the core without modifying it.

**Simplicity.** The standard captures what is needed for occupational hearing health documentation. It does not attempt to capture clinical diagnostic data beyond the scope of industrial audiometric programs.

**Privacy by design.** Worker identifiers are anonymized UUIDs. Date of birth is captured for calculation purposes only. Personally identifiable information remains within the control of the hearing test company and employer.

**Auditability.** Every record includes creation timestamp, technician identifier, and equipment identifier, enabling a complete audit trail.

**Honesty.** The standard acknowledges the operational reality of industrial field testing. Proxy estimation by qualified technicians is a recognized and documented practice. The questionnaire is designed to elicit accurate data through activity-type framing rather than self-reported compliance.

### 4.2 Two-Tier Architecture

CADS uses a two-tier architecture: the Core Standard and Provincial Profiles.

**Tier 1 — CADS Core Standard (this document)**

The universal requirements applicable to all industrial audiometric testing in Canada. Every CADS-conformant system must implement the core standard in full. The core standard is silent on provincial regulatory requirements — it defines what data is captured and how calculations are performed, not when testing must occur or how frequently.

**Tier 2 — CADS Provincial Profiles (separate documents)**

Jurisdiction-specific documents that define the regulatory context in which the core standard is applied. A provincial profile specifies the applicable regulatory authority and citation, testing requirements in that jurisdiction, testing frequency and baseline timing, HCP requirements, exit test requirements, record retention obligations, and language requirements.

Provincial profiles do not modify the core standard. They reference it and extend it with jurisdiction-specific parameters. A system that is conformant with a provincial profile must first be conformant with the core standard.

Provincial profile documents are maintained in the `provincial/` directory of the CADS repository.

### 4.3 Record Architecture

CADS defines six record types. Records reference each other by UUID:

```
Provider Record
  └── Technician Record (belongs to Provider)
  └── Equipment Record (belongs to Provider)
        Test Record (conducted by Technician, uses Equipment)
          ├── Worker Record (subject of Test)
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

### 4.4 Data Format

CADS records are expressed as JSON objects. All field names use `snake_case`. All dates use ISO 8601 format (`YYYY-MM-DD`). All datetimes use ISO 8601 format with UTC offset (`YYYY-MM-DDTHH:MM:SS±HH:MM`). All UUIDs use UUID v4 format.

**Record envelope:**

```json
{
  "cads_version": "1.0.1",
  "record_type": "test",
  "record_uuid": "550e8400-e29b-41d4-a716-446655440000",
  "province": "AB",
  "created_at": "2026-06-15T14:32:00-06:00",
  "payload": { }
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

| Field | Type | Req | Description | Constraints |
|---|---|---|---|---|
| `provider_uuid` | UUID | R | Unique identifier for this provider | UUID v4 |
| `company_name` | string | R | Legal name of the hearing test company | Max 200 chars |
| `province_of_registration` | string | R | Province where the company is registered | ISO 3166-2 CA code |
| `contact_name` | string | O | Primary contact name | Max 100 chars |
| `contact_email` | string | O | Primary contact email | Valid email format |
| `cads_version` | string | R | CADS version this record was created under | Semver e.g. `1.0.1` |
| `created_at` | datetime | R | Record creation timestamp | ISO 8601 with UTC offset |

---

### 5.2 Technician Record

| Field | Type | Req | Description | Constraints |
|---|---|---|---|---|
| `technician_uuid` | UUID | R | Unique identifier for this technician | UUID v4 |
| `provider_uuid` | UUID | R | Reference to the Provider Record | UUID v4 |
| `credential_type` | string | R | Type of qualification held | `IAT` `physician` `audiologist` |
| `certification_number` | string | R | Credential or certification number | Max 50 chars |
| `province_of_certification` | string | R | Province where credential was issued | ISO 3166-2 CA code |
| `cads_version` | string | R | CADS version this record was created under | Semver |
| `created_at` | datetime | R | Record creation timestamp | ISO 8601 with UTC offset |

---

### 5.3 Equipment Record

| Field | Type | Req | Description | Constraints |
|---|---|---|---|---|
| `equipment_uuid` | UUID | R | Unique identifier for this audiometer | UUID v4 |
| `provider_uuid` | UUID | R | Reference to the Provider Record | UUID v4 |
| `make` | string | R | Audiometer manufacturer | Max 100 chars |
| `model` | string | R | Audiometer model name | Max 100 chars |
| `serial_number` | string | R | Manufacturer serial number | Max 100 chars |
| `audiometer_type` | string | R | Classification of audiometer | `manual` `microprocessor` `automated` |
| `last_biological_calibration` | date | R | Date of most recent biological calibration | ISO 8601. Must be within 1 year of test date. |
| `last_acoustic_calibration` | date | R | Date of most recent electroacoustic calibration | ISO 8601. Must be within 1 year of test date. |
| `calibration_certificate_ref` | string | O | Reference number of calibration certificate | Max 100 chars |
| `firmware_version` | string | O | Audiometer firmware version if applicable | Max 50 chars |
| `cads_version` | string | R | CADS version this record was created under | Semver |
| `created_at` | datetime | R | Record creation timestamp | ISO 8601 with UTC offset |
| `updated_at` | datetime | R | Record last updated timestamp | ISO 8601 with UTC offset |

---

### 5.4 Worker Record

| Field | Type | Req | Description | Constraints |
|---|---|---|---|---|
| `worker_uuid` | UUID | R | Unique identifier for this worker | UUID v4. Stable across tests for the same worker. |
| `employer_uuid` | UUID | R | Reference to the employer | UUID v4 |
| `date_of_birth` | date | R | Worker's date of birth | ISO 8601. Required for age correction calculations. |
| `sex` | string | R | Biological sex for normative reference | `M` `F` |
| `province_of_employment` | string | R | Province of primary employment | ISO 3166-2 CA code |
| `noc_code` | string | R | National Occupational Classification code | 5-digit NOC 2021 code |
| `noise_exposure_group` | string | O | Employer-assigned exposure group label | Max 100 chars |
| `years_noise_exposed` | integer | O | Approximate years in noise-exposed work | 0–60 |
| `cads_version` | string | R | CADS version this record was created under | Semver |
| `created_at` | datetime | R | Record creation timestamp | ISO 8601 with UTC offset |
| `updated_at` | datetime | R | Record last updated timestamp | ISO 8601 with UTC offset |

---

### 5.5 Questionnaire Record

The CADS questionnaire instrument is fully defined in `standard/questionnaire.md`. This section defines the data fields that the questionnaire populates.

Fields are classified as:

- 🔵 **Contextual** — proxy estimation by the technician is accepted practice; basis documented in notes
- 🔴 **Clinical** — worker's actual answer required; do not estimate or substitute

#### Pre-Test Conditions

| Field | Type | Req | Class | Description | Valid Values |
|---|---|---|---|---|---|
| `questionnaire_uuid` | UUID | R | — | Unique identifier | UUID v4 |
| `test_uuid` | UUID | R | — | Reference to Test Record | UUID v4 |
| `worker_uuid` | UUID | R | — | Reference to Worker Record | UUID v4 |
| `recent_noise_exposure` | boolean | R | 🔵 | Noise exposure within the last 2 hours | `true` `false` |
| `recent_exposure_duration` | enum | C | 🔵 | Duration since last noise exposure. Required if `recent_noise_exposure` is `true`. | `lt_2hrs` `2_to_4hrs` `gt_4hrs` |

#### Occupational History

| Field | Type | Req | Class | Description | Valid Values |
|---|---|---|---|---|---|
| `previous_noise_employment` | boolean | R | 🔵 | Prior employment in noise-exposed roles | `true` `false` |

#### Non-Occupational Noise Exposure

| Field | Type | Req | Class | Description | Valid Values |
|---|---|---|---|---|---|
| `recreational_shooting` | boolean | R | 🔵 | Recreational use of firearms | `true` `false` |
| `recreational_shooting_type` | enum | C | 🔵 | Type of shooting activity. Required if `recreational_shooting` is `true`. | `hunting_casual` `competitive_sport` |
| `recreational_shooting_hpd` | enum | C | 🔵 | HPD use during shooting. Required if `recreational_shooting` is `true`. | `always` `sometimes` `never` |
| `power_tools_use` | boolean | R | 🔵 | Regular use of loud power tools outside work | `true` `false` |
| `power_tools_hpd` | enum | C | 🔵 | HPD use during power tool use. Required if `power_tools_use` is `true`. | `always` `sometimes` `never` |
| `motorsports` | boolean | R | 🔵 | Participation in or attendance at motorsports | `true` `false` |
| `motorsports_type` | enum | C | 🔵 | Nature of motorsports involvement. Required if `motorsports` is `true`. | `operator` `spectator` |
| `motorsports_hpd` | enum | C | 🔵 | HPD use during motorsports. Required if `motorsports` is `true`. | `always` `sometimes` `never` |
| `music_performance` | boolean | R | 🔵 | Playing music or performing in a band | `true` `false` |
| `music_performance_type` | enum | C | 🔵 | Nature of music involvement. Required if `music_performance` is `true`. | `casual` `regular_gigs` |
| `music_performance_hpd` | enum | C | 🔵 | HPD use during music performance. Required if `music_performance` is `true`. | `always` `sometimes` `never` |
| `concert_attendance` | enum | R | 🔵 | Frequency of attending loud concerts or events | `never` `occasional` `regular` |
| `non_occupational_notes` | string | O | 🔵 | Technician observation — non-occupational exposure context | Max 500 chars |

#### Hearing Protection

| Field | Type | Req | Class | Description | Valid Values |
|---|---|---|---|---|---|
| `hpd_type` | enum | R | 🔵 | Type of hearing protection used at work | `foam_plug` `premolded_plug` `earmuff` `custom` `combination` `none` |
| `hpd_consistency` | enum | R | 🔵 | Self-reported consistency of HPD use | `always` `usually` `sometimes` `never` `not_applicable` |
| `hpd_fit_training_received` | boolean | R | 🔵 | Whether worker has received HPD fit training | `true` `false` |

#### Medical History

| Field | Type | Req | Class | Description | Valid Values |
|---|---|---|---|---|---|
| `ear_surgery_history` | boolean | R | 🔴 | History of ear surgery | `true` `false` |
| `ear_infection_history` | boolean | R | 🔴 | History of chronic ear infections | `true` `false` |
| `ototoxic_medication` | boolean | R | 🔴 | Current use of potentially ototoxic medications | `true` `false` |
| `tinnitus_present` | boolean | R | 🔴 | Presence of tinnitus | `true` `false` |
| `tinnitus_frequency` | enum | C | 🔴 | Frequency of tinnitus. Required if `tinnitus_present` is `true`. | `constant` `frequent` `occasional` `rare` |
| `self_reported_hearing_difficulty` | boolean | R | 🔴 | Self-reported hearing difficulty in daily life | `true` `false` |

#### Technician Assessment

| Field | Type | Req | Class | Description | Valid Values |
|---|---|---|---|---|---|
| `worker_cooperation` | enum | R | 🔵 | Technician assessment of worker cooperation during testing | `good` `fair` `poor` |

#### Metadata

| Field | Type | Req | Description |
|---|---|---|---|
| `cads_version` | string | R | CADS version this record was created under |
| `created_at` | datetime | R | Record creation timestamp |

---

### 5.6 Test Record

#### 5.6.1 Test Identification and Context

| Field | Type | Req | Description | Constraints |
|---|---|---|---|---|
| `test_uuid` | UUID | R | Unique identifier for this test | UUID v4 |
| `worker_uuid` | UUID | R | Reference to the Worker Record | UUID v4 |
| `technician_uuid` | UUID | R | Reference to the Technician Record | UUID v4 |
| `equipment_uuid` | UUID | R | Reference to the Equipment Record | UUID v4 |
| `questionnaire_uuid` | UUID | R | Reference to the Questionnaire Record | UUID v4 |
| `province` | string | R | Province in which the test was conducted | ISO 3166-2 CA code |
| `test_date` | date | R | Date the test was conducted | ISO 8601 date |
| `test_time` | string | R | Time the test was conducted | HH:MM 24-hour format |
| `test_type` | string | R | Category of this test | `baseline` `periodic` `exit` `retest` |
| `baseline_test_uuid` | UUID | C | Reference to baseline Test Record for STS comparison | Required for `periodic` `exit` `retest` test types |

#### 5.6.2 Otoscopy

| Field | Type | Req | Description | Constraints |
|---|---|---|---|---|
| `otoscopy_right` | string | R | Otoscopy result for right ear | `normal` `abnormal` `not_performed` |
| `otoscopy_left` | string | R | Otoscopy result for left ear | `normal` `abnormal` `not_performed` |
| `otoscopy_notes` | string | O | Technician notes on otoscopy findings | Max 500 chars |

#### 5.6.3 Audiometric Thresholds

All threshold values are expressed in dB HL. Valid range: -10 to 120 dB HL. A value of `null` indicates the frequency was not tested or results were not obtainable.

**Right Ear:**

| Field | Type | Req | Description |
|---|---|---|---|
| `right_500` | integer | R | Right ear threshold at 500 Hz |
| `right_1000` | integer | R | Right ear threshold at 1000 Hz |
| `right_2000` | integer | R | Right ear threshold at 2000 Hz |
| `right_3000` | integer | R | Right ear threshold at 3000 Hz |
| `right_4000` | integer | R | Right ear threshold at 4000 Hz |
| `right_6000` | integer | O | Right ear threshold at 6000 Hz |
| `right_8000` | integer | O | Right ear threshold at 8000 Hz |

**Left Ear:**

| Field | Type | Req | Description |
|---|---|---|---|
| `left_500` | integer | R | Left ear threshold at 500 Hz |
| `left_1000` | integer | R | Left ear threshold at 1000 Hz |
| `left_2000` | integer | R | Left ear threshold at 2000 Hz |
| `left_3000` | integer | R | Left ear threshold at 3000 Hz |
| `left_4000` | integer | R | Left ear threshold at 4000 Hz |
| `left_6000` | integer | O | Left ear threshold at 6000 Hz |
| `left_8000` | integer | O | Left ear threshold at 8000 Hz |

> 500 Hz and 1000 Hz are required for audiogram completeness. 2000, 3000, and 4000 Hz are required for STS calculation. 6000 and 8000 Hz are optional but recommended as early indicators of noise-induced hearing loss.

#### 5.6.4 STS Calculations

| Field | Type | Req | Description | Constraints |
|---|---|---|---|---|
| `sts_right` | boolean | R | STS detected in right ear | `true` `false` |
| `sts_left` | boolean | R | STS detected in left ear | `true` `false` |
| `sts_right_value` | decimal | C | Calculated STS value for right ear in dB | Required if test_type is not `baseline` |
| `sts_left_value` | decimal | C | Calculated STS value for left ear in dB | Required if test_type is not `baseline` |
| `age_correction_applied` | boolean | R | Whether age correction was applied | `true` `false` |
| `age_correction_right` | decimal | C | Age correction value applied to right ear in dB | Required if `age_correction_applied` is `true` |
| `age_correction_left` | decimal | C | Age correction value applied to left ear in dB | Required if `age_correction_applied` is `true` |

#### 5.6.5 Outcome and Follow-Up

| Field | Type | Req | Description | Constraints |
|---|---|---|---|---|
| `outcome` | string | R | Overall test outcome classification | `normal` `sts_detected` `referral_required` `retest_required` |
| `referral_type` | string | C | Type of referral indicated | `medical` `audiological` `none`. Required if outcome is `referral_required`. |
| `follow_up_interval_months` | integer | O | Recommended follow-up interval in months | 1–12 |
| `physician_referral_flag` | boolean | R | Whether a physician referral is indicated | `true` `false` |
| `notes` | string | O | Technician notes on the test | Max 1000 chars |

#### 5.6.6 Record Metadata

| Field | Type | Req | Description | Constraints |
|---|---|---|---|---|
| `cads_version` | string | R | CADS version this record was created under | Semver |
| `sync_status` | string | R | Synchronization status | `pending` `synced` `failed` |
| `created_at` | datetime | R | Record creation timestamp | ISO 8601 with UTC offset |
| `updated_at` | datetime | R | Record last updated timestamp | ISO 8601 with UTC offset |
| `submitted_at` | datetime | O | Timestamp of provincial submission if applicable | ISO 8601 with UTC offset |

---

## 6. Compliance Calculations

### 6.1 Standard Threshold Shift (STS)

A Standard Threshold Shift is defined as a change in hearing threshold, relative to the baseline audiogram, of an average of **10 dB or more** at **2000, 3000, and 4000 Hz** in either ear.

This definition is consistent with CSA Z107.6 and is uniform across all Canadian jurisdictions that define STS.

**Calculation:**

```
STS_right = mean(right_2000_current − right_2000_baseline,
                 right_3000_current − right_3000_baseline,
                 right_4000_current − right_4000_baseline)

STS_left  = mean(left_2000_current − left_2000_baseline,
                 left_3000_current − left_3000_baseline,
                 left_4000_current − left_4000_baseline)
```

If age correction is applied, corrected baseline values are used in place of raw baseline values.

**STS flag is set to `true` when the calculated value is ≥ 10.0 dB.**

### 6.2 Age Correction

Age correction may be applied to adjust baseline thresholds upward to account for expected age-related hearing change (presbycusis), isolating occupational hearing loss from normal ageing.

Age correction is permitted across all Canadian jurisdictions. The `age_correction_applied` field must accurately reflect whether correction was used.

Age correction values are taken from the NIOSH 1998 tables (Appendix B). The correction is applied as the difference between the age correction at the current test age and the age correction at the baseline test age.

```
corrected_baseline = baseline_threshold + (age_correction_current_age − age_correction_baseline_age)
STS_value = current_threshold − corrected_baseline
```

### 6.3 Baseline Comparison Rules

1. Every test of type `periodic`, `exit`, or `retest` must reference a `baseline_test_uuid`
2. The referenced baseline must be of type `baseline`
3. If a worker's baseline has been revised following a confirmed STS, the most recent valid baseline is used
4. A baseline record may not reference another test as its baseline
5. The baseline and comparison test must reference the same `worker_uuid`

### 6.4 Outcome Classification

Outcomes are assigned according to the following hierarchy:

| Priority | Outcome | Condition |
|---|---|---|
| 1 | `retest_required` | Worker cooperation rated `poor`, otoscopy result is `abnormal`, or threshold reliability concern identified |
| 2 | `referral_required` | STS detected AND shift warrants medical or audiological evaluation per applicable provincial protocol |
| 3 | `sts_detected` | STS calculated as ≥ 10 dB in either ear, referral not yet indicated |
| 4 | `normal` | No STS detected, no otoscopy abnormality, no reliability concern |

---

## 7. Provincial Profile Schema

### 7.1 Purpose of Provincial Profiles

Provincial profiles define the regulatory context in which the CADS Core Standard is applied. The core standard is universal — the data model, calculations, and field definitions are identical across all jurisdictions. Provincial profiles specify jurisdiction-specific parameters without modifying the core.

A CADS-conformant system applies the profile corresponding to the province recorded in the Test Record's `province` field. When no profile exists for a jurisdiction, the core standard applies without profile extension.

### 7.2 Profile Field Definitions

Each provincial profile is a structured document containing the following fields:

| Field | Type | Required | Description |
|---|---|---|---|
| `province_code` | string | R | ISO 3166-2 CA province or territory code |
| `province_name` | string | R | Full jurisdiction name |
| `regulatory_authority` | string | R | Name of the occupational health and safety regulator |
| `regulation_reference` | string | R | Specific regulation citation for noise and hearing conservation |
| `exposure_limit_dba` | integer | R | Occupational exposure limit in dBA TWA over 8 hours |
| `peak_limit_dbc` | integer | O | Peak exposure limit in dBC or dB |
| `action_level_dba` | integer | O | Noise level above which specific obligations are triggered |
| `hcp_required` | boolean | R | Whether a formal Hearing Conservation Program is required by regulation |
| `hcp_worker_threshold` | integer | O | Minimum number of exposed workers before HCP is required (null = no threshold) |
| `audiometric_testing_required` | boolean | R | Whether audiometric testing is required by regulation |
| `testing_trigger_dba` | integer | O | dBA level above which audiometric testing is required |
| `baseline_months` | integer | O | Maximum months after first exposure before baseline test is required |
| `testing_frequency` | string | O | Required periodic testing frequency | `annual` `biennial` |
| `exit_test_required` | boolean | R | Whether exit audiometric testing is specifically required |
| `hpd_selection_documentation_required` | boolean | R | Whether HPD selection must be formally documented |
| `retention_years_minimum` | integer | O | Minimum record retention period in years (null = not specified or indefinite) |
| `language` | string | R | Primary language for this jurisdiction | `en` `fr` `bilingual` |
| `notes` | string | O | Additional regulatory context or jurisdiction-specific notes |
| `verification_date` | date | O | Date the profile was last verified against current regulation |

### 7.3 Profile Documents

Provincial profile documents are maintained separately from this standard in the `provincial/` directory of the CADS repository. Each file is named by province code (e.g., `BC.md`, `AB.md`).

Profiles are versioned independently of the core standard. A profile update does not increment the core standard version.

Current profiles:

| File | Jurisdiction | Status |
|---|---|---|
| `provincial/BC.md` | British Columbia | Draft |
| `provincial/AB.md` | Alberta | Draft |
| `provincial/SK.md` | Saskatchewan | Draft |

Profiles for remaining Canadian provinces and territories are in development. See `docs/provincial-comparison.md` for the current regulatory research baseline.

---

## 8. Conformance Requirements

### 8.1 Core Conformance

A CADS-conformant implementation must:

- Include all fields marked **R** (Required) in every record
- Populate conditional fields marked **C** when the specified condition is met
- Use the exact field names specified (snake_case throughout)
- Use the exact valid values specified for enumerated fields
- Generate a unique UUID v4 for every UUID field at record creation time
- Include `cads_version` in every record reflecting the version under which the record was created
- Accurately record whether proxy estimation was used in contextual questionnaire fields by documenting the basis in the relevant notes field

### 8.2 Calculation Conformance

A CADS-conformant implementation must:

- Calculate STS using the average shift at 2000, 3000, and 4000 Hz as defined in Section 6.1
- Apply age correction only from the NIOSH 1998 reference tables in Appendix B
- Accurately record whether age correction was applied in `age_correction_applied`
- Reference the correct baseline test in `baseline_test_uuid` for all non-baseline test types
- Assign outcome classifications following the hierarchy in Section 6.4

### 8.3 Profile Conformance

A system claiming conformance with a specific provincial profile must:

- First be conformant with the CADS Core Standard
- Apply the profile corresponding to the `province` field in each Test Record
- Enforce mandatory elements specified in the provincial profile
- Reference the profile version in implementation documentation

---

## 9. Versioning and Change Control

CADS uses semantic versioning (`MAJOR.MINOR.PATCH`):

- **MAJOR** — breaking changes to the record schema. Existing records remain valid under their original version. Implementations must declare which major version they support.
- **MINOR** — new optional fields or new province profile schema fields. Backward compatible.
- **PATCH** — corrections, clarifications, or editorial changes. No schema changes.

The `cads_version` field in every record identifies the version under which the record was created. Systems receiving CADS records must process records from any minor or patch version within the same major version.

Provincial profile additions and updates are versioned separately from the core standard.

---

## Appendix A — NOC 2021 Reference Codes

Common occupational codes encountered in industrial hearing conservation programs. Not exhaustive — full NOC 2021 listings available at [noc.esdc.gc.ca](https://noc.esdc.gc.ca).

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

---

## Appendix B — Age Correction Tables

Age correction values represent expected threshold increase due to presbycusis. Values derived from NIOSH 1998 (Tables B-1 and B-2). Applied as the difference between age correction at current test age and age correction at baseline test age.

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
| 1.0.1-draft | June 2026 | Removed platform references. Established two-tier Core/Profile architecture. Updated questionnaire fields to v1.0.2 (replaced `hours_since_noise_exposure` with `recent_noise_exposure`/`recent_exposure_duration`; added activity-type and HPD fields for non-occupational noise). Added CSA Z107.6 to normative references. Clarified scope exclusions. Added Contextual/Clinical field classification. Added proxy estimation to Terms and Design Principles. |

---

*Canadian Audiometric Data Standard (CADS) v1.0.1*
*Open specification. See repository for licensing terms.*
