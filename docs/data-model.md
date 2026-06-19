# CADS Data Model Reference
## Canadian Audiometric Data Standard — Developer Reference v1.0

**Status:** Draft
**Version:** 1.0.0
**Date:** June 2026
**Maintainer:** RoadPilotAI

> This document is a developer-friendly companion to the formal specification in `standard/CADS-v1.0.md`. The spec is authoritative. This document provides entity diagrams, enumeration references, and complete JSON examples for implementation guidance.

---

## Table of Contents

- [1. Entity Relationships](#1-entity-relationships)
- [2. Record Summary](#2-record-summary)
- [3. Enumeration Reference](#3-enumeration-reference)
- [4. JSON Examples](#4-json-examples)
  - [4.1 Provider Record](#41-provider-record)
  - [4.2 Technician Record](#42-technician-record)
  - [4.3 Equipment Record](#43-equipment-record)
  - [4.4 Worker Record](#44-worker-record)
  - [4.5 Questionnaire Record](#45-questionnaire-record)
  - [4.6 Test Record](#46-test-record)
- [5. Province Configuration Reference](#5-province-configuration-reference)
- [6. Record Envelope](#6-record-envelope)
- [7. Field Updates — Questionnaire v1.0.2](#7-field-updates--questionnaire-v102)

---

## 1. Entity Relationships

```
┌─────────────────────────────────────────────────────────────┐
│                      CADS Record Model                       │
└─────────────────────────────────────────────────────────────┘

Provider Record
│   provider_uuid (PK)
│   company_name
│   province_of_registration
│
├── Technician Record
│   │   technician_uuid (PK)
│   │   provider_uuid (FK → Provider)
│   │   credential_type
│   │   certification_number
│   │
│   └── Test Record ──────────────────────────────────────┐
│           test_uuid (PK)                                 │
│           technician_uuid (FK → Technician)              │
│           equipment_uuid (FK → Equipment)                │
│           worker_uuid (FK → Worker)                      │
│           questionnaire_uuid (FK → Questionnaire)        │
│           province                                       │
│           test_type                                      │
│           baseline_test_uuid (FK → Test, self-ref)       │
│           [thresholds, STS calculations, outcome]        │
│                                                          │
├── Equipment Record                                       │
│       equipment_uuid (PK)                                │
│       provider_uuid (FK → Provider)                      │
│       make / model / serial_number                       │
│       last_biological_calibration                        │
│       last_acoustic_calibration                          │
│                                                          │
Worker Record ◄───────────────────────────────────────────┘
│   worker_uuid (PK)
│   employer_uuid (FK → Employer)
│   date_of_birth
│   noc_code
│   province_of_employment
│
└── Questionnaire Record
        questionnaire_uuid (PK)
        test_uuid (FK → Test)
        worker_uuid (FK → Worker)
        [pre-test conditions, exposure history,
         medical history, HPD use]
```

**Key relationships:**

- One Provider has many Technicians
- One Provider has many Equipment records
- One Technician conducts many Tests
- One Worker has many Tests (one per test event)
- One Test has exactly one Questionnaire
- One Test references one Equipment record
- Periodic/exit/retest Tests reference a baseline Test via `baseline_test_uuid`

---

## 2. Record Summary

Compact field reference. R = Required, O = Optional, C = Conditional.

### Provider

| Field | Type | Req |
|---|---|---|
| `provider_uuid` | UUID | R |
| `company_name` | string | R |
| `province_of_registration` | string | R |
| `contact_name` | string | O |
| `contact_email` | string | O |
| `cads_version` | string | R |
| `created_at` | datetime | R |

### Technician

| Field | Type | Req |
|---|---|---|
| `technician_uuid` | UUID | R |
| `provider_uuid` | UUID | R |
| `credential_type` | enum | R |
| `certification_number` | string | R |
| `province_of_certification` | string | R |
| `cads_version` | string | R |
| `created_at` | datetime | R |

### Equipment

| Field | Type | Req |
|---|---|---|
| `equipment_uuid` | UUID | R |
| `provider_uuid` | UUID | R |
| `make` | string | R |
| `model` | string | R |
| `serial_number` | string | R |
| `audiometer_type` | enum | R |
| `last_biological_calibration` | date | R |
| `last_acoustic_calibration` | date | R |
| `calibration_certificate_ref` | string | O |
| `firmware_version` | string | O |
| `cads_version` | string | R |
| `created_at` | datetime | R |
| `updated_at` | datetime | R |

### Worker

| Field | Type | Req |
|---|---|---|
| `worker_uuid` | UUID | R |
| `employer_uuid` | UUID | R |
| `date_of_birth` | date | R |
| `sex` | enum | R |
| `province_of_employment` | string | R |
| `noc_code` | string | R |
| `noise_exposure_group` | string | O |
| `years_noise_exposed` | integer | O |
| `cads_version` | string | R |
| `created_at` | datetime | R |
| `updated_at` | datetime | R |

### Questionnaire

| Field | Type | Req |
|---|---|---|
| `questionnaire_uuid` | UUID | R |
| `test_uuid` | UUID | R |
| `worker_uuid` | UUID | R |
| `recent_noise_exposure` | boolean | R |
| `recent_exposure_duration` | enum | C |
| `previous_noise_employment` | boolean | R |
| `recreational_shooting` | boolean | R |
| `recreational_shooting_type` | enum | C |
| `recreational_shooting_hpd` | enum | C |
| `power_tools_use` | boolean | R |
| `power_tools_hpd` | enum | C |
| `motorsports` | boolean | R |
| `motorsports_type` | enum | C |
| `motorsports_hpd` | enum | C |
| `music_performance` | boolean | R |
| `music_performance_type` | enum | C |
| `music_performance_hpd` | enum | C |
| `concert_attendance` | enum | R |
| `non_occupational_notes` | string | O |
| `hpd_type` | enum | R |
| `hpd_consistency` | enum | R |
| `hpd_fit_training_received` | boolean | R |
| `ear_surgery_history` | boolean | R |
| `ear_infection_history` | boolean | R |
| `ototoxic_medication` | boolean | R |
| `tinnitus_present` | boolean | R |
| `tinnitus_frequency` | enum | C |
| `self_reported_hearing_difficulty` | boolean | R |
| `worker_cooperation` | enum | R |
| `cads_version` | string | R |
| `created_at` | datetime | R |

### Test

| Field | Type | Req |
|---|---|---|
| `test_uuid` | UUID | R |
| `worker_uuid` | UUID | R |
| `technician_uuid` | UUID | R |
| `equipment_uuid` | UUID | R |
| `questionnaire_uuid` | UUID | R |
| `province` | string | R |
| `test_date` | date | R |
| `test_time` | string | R |
| `test_type` | enum | R |
| `baseline_test_uuid` | UUID | C |
| `otoscopy_right` | enum | R |
| `otoscopy_left` | enum | R |
| `otoscopy_notes` | string | O |
| `right_500` | integer | R |
| `right_1000` | integer | R |
| `right_2000` | integer | R |
| `right_3000` | integer | R |
| `right_4000` | integer | R |
| `right_6000` | integer | O |
| `right_8000` | integer | O |
| `left_500` | integer | R |
| `left_1000` | integer | R |
| `left_2000` | integer | R |
| `left_3000` | integer | R |
| `left_4000` | integer | R |
| `left_6000` | integer | O |
| `left_8000` | integer | O |
| `sts_right` | boolean | R |
| `sts_left` | boolean | R |
| `sts_right_value` | decimal | C |
| `sts_left_value` | decimal | C |
| `age_correction_applied` | boolean | R |
| `age_correction_right` | decimal | C |
| `age_correction_left` | decimal | C |
| `outcome` | enum | R |
| `referral_type` | enum | C |
| `follow_up_interval_months` | integer | O |
| `physician_referral_flag` | boolean | R |
| `notes` | string | O |
| `cads_version` | string | R |
| `sync_status` | enum | R |
| `created_at` | datetime | R |
| `updated_at` | datetime | R |
| `submitted_at` | datetime | O |

---

## 3. Enumeration Reference

All valid enum values across the CADS data model. String values are case-sensitive and must match exactly.

### credential_type
```
IAT | physician | audiologist
```

### audiometer_type
```
manual | microprocessor | automated
```

### sex
```
M | F
```

### recent_exposure_duration
```
lt_2hrs | 2_to_4hrs | gt_4hrs
```

### recreational_shooting_type
```
hunting_casual | competitive_sport
```

### hpd_use (shared by recreational_shooting_hpd, power_tools_hpd, motorsports_hpd, music_performance_hpd)
```
always | sometimes | never
```

### motorsports_type
```
operator | spectator
```

### music_performance_type
```
casual | regular_gigs
```

### concert_attendance
```
never | occasional | regular
```

### hpd_type
```
foam_plug | premolded_plug | earmuff | custom | combination | none
```

### hpd_consistency
```
always | usually | sometimes | never | not_applicable
```

### tinnitus_frequency
```
constant | frequent | occasional | rare
```

### worker_cooperation
```
good | fair | poor
```

### test_type
```
baseline | periodic | exit | retest
```

### otoscopy_result
```
normal | abnormal | not_performed
```

### outcome
```
normal | sts_detected | referral_required | retest_required
```

### referral_type
```
medical | audiological | none
```

### sync_status
```
pending | synced | failed
```

### province_code (ISO 3166-2 CA)
```
AB | BC | MB | NB | NL | NS | NT | NU | ON | PE | QC | SK | YT
```

---

## 4. JSON Examples

Complete example records for each type. UUIDs are illustrative.

### 4.1 Provider Record

```json
{
  "cads_version": "1.0.0",
  "record_type": "provider",
  "record_uuid": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
  "payload": {
    "provider_uuid": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "company_name": "Northern Hearing Conservation Ltd.",
    "province_of_registration": "AB",
    "contact_name": "Jane Smith",
    "contact_email": "jane.smith@example.com",
    "cads_version": "1.0.0",
    "created_at": "2026-01-15T09:00:00-07:00"
  }
}
```

### 4.2 Technician Record

```json
{
  "cads_version": "1.0.0",
  "record_type": "technician",
  "record_uuid": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
  "payload": {
    "technician_uuid": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
    "provider_uuid": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "credential_type": "IAT",
    "certification_number": "IAT-2019-04471",
    "province_of_certification": "BC",
    "cads_version": "1.0.0",
    "created_at": "2026-01-15T09:05:00-07:00"
  }
}
```

### 4.3 Equipment Record

```json
{
  "cads_version": "1.0.0",
  "record_type": "equipment",
  "record_uuid": "c3d4e5f6-a7b8-9012-cdef-123456789012",
  "payload": {
    "equipment_uuid": "c3d4e5f6-a7b8-9012-cdef-123456789012",
    "provider_uuid": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "make": "Interacoustics",
    "model": "AD629",
    "serial_number": "AD629-20221047",
    "audiometer_type": "microprocessor",
    "last_biological_calibration": "2026-05-10",
    "last_acoustic_calibration": "2026-04-22",
    "calibration_certificate_ref": "CAL-2026-0422-047",
    "firmware_version": "3.2.1",
    "cads_version": "1.0.0",
    "created_at": "2026-01-15T09:10:00-07:00",
    "updated_at": "2026-05-10T14:30:00-07:00"
  }
}
```

### 4.4 Worker Record

```json
{
  "cads_version": "1.0.0",
  "record_type": "worker",
  "record_uuid": "d4e5f6a7-b8c9-0123-defa-234567890123",
  "payload": {
    "worker_uuid": "d4e5f6a7-b8c9-0123-defa-234567890123",
    "employer_uuid": "e5f6a7b8-c9d0-1234-efab-345678901234",
    "date_of_birth": "1978-03-22",
    "sex": "M",
    "province_of_employment": "AB",
    "noc_code": "73300",
    "noise_exposure_group": "Heavy Equipment",
    "years_noise_exposed": 18,
    "cads_version": "1.0.0",
    "created_at": "2023-06-10T08:00:00-07:00",
    "updated_at": "2026-06-15T10:15:00-07:00"
  }
}
```

### 4.5 Questionnaire Record

```json
{
  "cads_version": "1.0.0",
  "record_type": "questionnaire",
  "record_uuid": "f6a7b8c9-d0e1-2345-fabc-567890123456",
  "payload": {
    "questionnaire_uuid": "f6a7b8c9-d0e1-2345-fabc-567890123456",
    "test_uuid": "a7b8c9d0-e1f2-3456-abcd-678901234567",
    "worker_uuid": "d4e5f6a7-b8c9-0123-defa-234567890123",
    "recent_noise_exposure": true,
    "recent_exposure_duration": "gt_4hrs",
    "previous_noise_employment": true,
    "recreational_shooting": true,
    "recreational_shooting_type": "hunting_casual",
    "recreational_shooting_hpd": "never",
    "power_tools_use": true,
    "power_tools_hpd": "always",
    "motorsports": false,
    "motorsports_type": null,
    "motorsports_hpd": null,
    "music_performance": false,
    "music_performance_type": null,
    "music_performance_hpd": null,
    "concert_attendance": "never",
    "non_occupational_notes": "Deer hunter, 2-3 times per season. Reports no HPD use during hunting.",
    "hpd_type": "foam_plug",
    "hpd_consistency": "usually",
    "hpd_fit_training_received": true,
    "ear_surgery_history": false,
    "ear_infection_history": false,
    "ototoxic_medication": false,
    "tinnitus_present": true,
    "tinnitus_frequency": "occasional",
    "self_reported_hearing_difficulty": false,
    "worker_cooperation": "good",
    "cads_version": "1.0.0",
    "created_at": "2026-06-15T10:20:00-07:00"
  }
}
```

### 4.6 Test Record

```json
{
  "cads_version": "1.0.0",
  "record_type": "test",
  "record_uuid": "a7b8c9d0-e1f2-3456-abcd-678901234567",
  "payload": {
    "test_uuid": "a7b8c9d0-e1f2-3456-abcd-678901234567",
    "worker_uuid": "d4e5f6a7-b8c9-0123-defa-234567890123",
    "technician_uuid": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
    "equipment_uuid": "c3d4e5f6-a7b8-9012-cdef-123456789012",
    "questionnaire_uuid": "f6a7b8c9-d0e1-2345-fabc-567890123456",
    "province": "AB",
    "test_date": "2026-06-15",
    "test_time": "10:30",
    "test_type": "periodic",
    "baseline_test_uuid": "b8c9d0e1-f2a3-4567-bcde-789012345678",
    "otoscopy_right": "normal",
    "otoscopy_left": "normal",
    "otoscopy_notes": null,
    "right_500": 15,
    "right_1000": 15,
    "right_2000": 20,
    "right_3000": 30,
    "right_4000": 35,
    "right_6000": 40,
    "right_8000": 35,
    "left_500": 10,
    "left_1000": 15,
    "left_2000": 15,
    "left_3000": 20,
    "left_4000": 25,
    "left_6000": 30,
    "left_8000": 25,
    "sts_right": true,
    "sts_left": false,
    "sts_right_value": 11.7,
    "sts_left_value": 3.3,
    "age_correction_applied": true,
    "age_correction_right": 4.0,
    "age_correction_left": 4.0,
    "outcome": "sts_detected",
    "referral_type": null,
    "follow_up_interval_months": 6,
    "physician_referral_flag": false,
    "notes": "Worker reports right ear tinnitus increasing over past year. STS right ear confirmed with age correction. Recommend retest in 6 months.",
    "cads_version": "1.0.0",
    "sync_status": "synced",
    "created_at": "2026-06-15T10:45:00-07:00",
    "updated_at": "2026-06-15T11:02:00-07:00",
    "submitted_at": "2026-06-15T18:30:00-07:00"
  }
}
```

---

## 5. Province Configuration Reference

Province configurations are JSON objects that define the regulatory context in which the CADS standard is applied. The standard itself is universal — data model, calculations, and field definitions are identical across all jurisdictions. Configurations tell the platform which jurisdiction-specific requirements are in effect. Full schema in `standard/CADS-v1.0.md` Section 7.

### British Columbia
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

### Alberta
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

### Saskatchewan
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

## 6. Record Envelope

Every CADS record is wrapped in a standard envelope before transmission or storage. The envelope identifies the record type and version independently of the payload.

```json
{
  "cads_version": "1.0.0",
  "record_type": "test",
  "record_uuid": "a7b8c9d0-e1f2-3456-abcd-678901234567",
  "province": "AB",
  "created_at": "2026-06-15T10:45:00-07:00",
  "payload": {
    "..."
  }
}
```

**Envelope fields:**

| Field | Description |
|---|---|
| `cads_version` | Version of the standard under which this record was created |
| `record_type` | One of: `provider` `technician` `equipment` `worker` `questionnaire` `test` |
| `record_uuid` | Matches the primary key UUID within the payload |
| `province` | Province code for routing and configuration lookup |
| `created_at` | Record creation timestamp — duplicated from payload for envelope-level filtering |
| `payload` | The full record object as defined in the specification |

---

## 7. Field Updates — Questionnaire v1.0.2

The following fields were added or changed in questionnaire instrument v1.0.2. The formal spec (`standard/CADS-v1.0.md`) will be updated in the next revision to reflect these changes.

### Replaced Fields

| Old Field | New Fields | Reason |
|---|---|---|
| `hours_since_noise_exposure` (decimal) | `recent_noise_exposure` (boolean) + `recent_exposure_duration` (enum) | Decimal precision not achievable in field conditions; two-question approach produces more accurate and consistent data |

### Added Fields

| Field | Type | Record | Description |
|---|---|---|---|
| `recent_noise_exposure` | boolean | Questionnaire | Whether worker was exposed to noise in the last 2 hours |
| `recent_exposure_duration` | enum | Questionnaire | `lt_2hrs` `2_to_4hrs` `gt_4hrs` — conditional on `recent_noise_exposure: true` |
| `recreational_shooting_type` | enum | Questionnaire | `hunting_casual` `competitive_sport` — conditional on `recreational_shooting: true` |
| `recreational_shooting_hpd` | enum | Questionnaire | HPD use during shooting — conditional on `recreational_shooting: true` |
| `power_tools_hpd` | enum | Questionnaire | HPD use during power tool use — conditional on `power_tools_use: true` |
| `motorsports_type` | enum | Questionnaire | `operator` `spectator` — conditional on `motorsports: true` |
| `motorsports_hpd` | enum | Questionnaire | HPD use during motorsports — conditional on `motorsports: true` |
| `music_performance_type` | enum | Questionnaire | `casual` `regular_gigs` — conditional on `music_performance: true` |
| `music_performance_hpd` | enum | Questionnaire | HPD use during music — conditional on `music_performance: true` |
| `concert_attendance` | enum | Questionnaire | `never` `occasional` `regular` |
| `non_occupational_notes` | string | Questionnaire | Technician observation field for non-occupational context |

---

*Canadian Audiometric Data Standard (CADS) — Data Model Reference v1.0.0*
*© RoadPilotAI — Open specification. See repository for licensing terms.*
