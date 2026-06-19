# CADS Standardized Pre-Test Questionnaire
## Canadian Audiometric Data Standard — Questionnaire Instrument v1.0

**Status:** Draft
**Version:** 1.0.0
**Date:** June 2026
**Maintainer:** RoadPilotAI

---

## Table of Contents

- [1. Overview](#1-overview)
- [2. Administration Guidelines](#2-administration-guidelines)
- [3. The Questionnaire](#3-the-questionnaire)
  - [Section A — Pre-Test Conditions](#section-a--pre-test-conditions)
  - [Section B — Occupational Noise History](#section-b--occupational-noise-history)
  - [Section C — Non-Occupational Noise Exposure](#section-c--non-occupational-noise-exposure)
  - [Section D — Hearing Protection](#section-d--hearing-protection)
  - [Section E — Medical History](#section-e--medical-history)
  - [Section F — Technician Completion](#section-f--technician-completion)
- [4. CADS Field Mapping](#4-cads-field-mapping)
- [5. Guidance Notes](#5-guidance-notes)

---

## 1. Overview

The CADS Standardized Pre-Test Questionnaire is the instrument used to collect worker health and noise exposure history before conducting an industrial audiometric test. It is administered by the technician at the start of each test session.

**Purpose:**

- Identify pre-test conditions that may affect audiometric results (particularly quiet period compliance)
- Document non-occupational noise exposures that provide context for interpreting threshold changes
- Record hearing protection practices relevant to program effectiveness
- Capture medical history that may affect hearing or indicate referral need
- Generate a standardized, comparable dataset across all CADS-participating providers and provinces

**Design principle:** Every question maps to a defined field in the CADS Questionnaire Record (see Section 5.5 of CADS-v1.0). No question is included that does not serve a specific data or clinical purpose. No required data element is left uncaptured.

---

## 2. Administration Guidelines

### Before You Begin

- Confirm the worker's identity and locate or create their Worker Record
- Confirm the test type (baseline, periodic, exit, or retest)
- Administer the questionnaire verbally or allow the worker to self-complete — either method is acceptable
- All questions must be answered before proceeding to otoscopy and audiometric testing
- Record answers directly into the CADS system; do not rely on paper transcription

### Quiet Period

The most critical pre-test condition is quiet period compliance. If the worker has been exposed to significant noise within the past 14 hours, the test should be rescheduled where possible. If rescheduling is not possible, document the actual quiet period accurately and note the circumstance. **Do not record 14 hours if the actual period was less — accurate data is the priority.**

### Worker Instructions

Read or display the following to the worker before beginning:

> *"I'm going to ask you a few questions about your hearing health and noise exposure before we do your hearing test. There are no right or wrong answers — we just want to make sure we have an accurate picture of your situation. Everything you tell me is kept confidential within your hearing conservation program."*

---

## 3. The Questionnaire

---

### Section A — Pre-Test Conditions

**A1. When did you last work in a noisy environment, or experience significant noise (power tools, loud music, shooting, etc.)?**

> Estimated hours ago: ______

*CADS field: `hours_since_noise_exposure`*
*Note: If the worker is unsure, help them estimate. Record your best estimate if they cannot provide one.*

---

**A2. Were you wearing hearing protection during that noise exposure?**

- [ ] Yes
- [ ] No
- [ ] Not applicable

*Technician note: If no HPD was worn during recent exposure and quiet period is less than 14 hours, flag for potential temporary threshold shift. Consider rescheduling.*

---

### Section B — Occupational Noise History

**B1. How many years have you worked in your current role or in noise-exposed work overall?**

> Years in current role: ______
> Total years in noise-exposed work: ______

*CADS field: Worker Record `years_noise_exposed`*

---

**B2. Have you had previous employment in other noisy environments, outside of your current employer?**

- [ ] Yes
- [ ] No

*CADS field: `previous_noise_employment`*

---

### Section C — Non-Occupational Noise Exposure

**C1. Do you regularly go hunting or participate in recreational shooting (firearms, including at a range)?**

- [ ] Yes
- [ ] No

*CADS field: `recreational_shooting`*

*If Yes:* **How often?**
- [ ] Occasional (a few times per year)
- [ ] Regular (monthly or more)

*CADS field: `recreational_shooting_frequency` → `occasional` or `regular`*

---

**C2. Do you regularly use loud power tools outside of work (woodworking, yard equipment, etc.)?**

- [ ] Yes
- [ ] No

*CADS field: `power_tools_use`*

---

**C3. Do you participate in motorsports (racing, off-road, snowmobiling, etc.)?**

- [ ] Yes
- [ ] No

*CADS field: `motorsports`*

---

**C4. Do you regularly play or perform music, or attend loud concerts or events?**

- [ ] Yes
- [ ] No

*CADS field: `music_performance`*

---

### Section D — Hearing Protection

**D1. What type of hearing protection do you use at work?**

- [ ] Foam earplugs (disposable)
- [ ] Pre-moulded earplugs (reusable)
- [ ] Earmuffs
- [ ] Custom-moulded earplugs
- [ ] Combination (plugs and muffs together)
- [ ] None

*CADS field: `hpd_type` → `foam_plug` `premolded_plug` `earmuff` `custom` `combination` `none`*

---

**D2. How consistently do you wear your hearing protection when working in noisy areas?**

- [ ] Always — I wear it whenever I am in a noisy area
- [ ] Usually — I wear it most of the time but occasionally forget
- [ ] Sometimes — I wear it some of the time
- [ ] Never — I do not wear hearing protection
- [ ] Not applicable — I am not exposed to hazardous noise levels

*CADS field: `hpd_consistency` → `always` `usually` `sometimes` `never` `not_applicable`*

---

**D3. Have you received training or instruction on how to properly fit your hearing protection?**

- [ ] Yes
- [ ] No

*CADS field: `hpd_fit_training_received`*

---

### Section E — Medical History

**E1. Have you ever had surgery on either ear?**

- [ ] Yes
- [ ] No

*CADS field: `ear_surgery_history`*

---

**E2. Do you have a history of chronic or recurring ear infections?**

- [ ] Yes
- [ ] No

*CADS field: `ear_infection_history`*

---

**E3. Are you currently taking any medications? (Some medications can affect hearing.)**

- [ ] Yes — medication(s) that may affect hearing
- [ ] Yes — medications unrelated to hearing
- [ ] No

*CADS field: `ototoxic_medication`*
*Record `true` only if the worker indicates medications that may affect hearing. Common ototoxic medications include certain antibiotics (aminoglycosides), loop diuretics, high-dose ASA, and some chemotherapy agents. When in doubt, record `true` and note in the technician notes field.*

---

**E4. Do you experience ringing, buzzing, or other sounds in your ears (tinnitus)?**

- [ ] Yes
- [ ] No

*CADS field: `tinnitus_present`*

*If Yes:* **How often do you notice it?**
- [ ] Constant — I hear it all the time
- [ ] Frequent — I hear it most days
- [ ] Occasional — I hear it sometimes
- [ ] Rare — I only notice it occasionally

*CADS field: `tinnitus_frequency` → `constant` `frequent` `occasional` `rare`*

---

**E5. Do you feel you have difficulty hearing in your daily life — for example, in conversation, on the phone, or in noisy environments?**

- [ ] Yes
- [ ] No

*CADS field: `self_reported_hearing_difficulty`*

---

### Section F — Technician Completion

*This section is completed by the technician. It is not presented to the worker.*

---

**F1. Otoscopy — Right Ear**

- [ ] Normal
- [ ] Abnormal — describe: ______________________________
- [ ] Not performed

*CADS field: Test Record `otoscopy_right` + `otoscopy_notes`*

---

**F2. Otoscopy — Left Ear**

- [ ] Normal
- [ ] Abnormal — describe: ______________________________
- [ ] Not performed

*CADS field: Test Record `otoscopy_left` + `otoscopy_notes`*

---

**F3. Worker Cooperation**

*(To be completed after testing)*

- [ ] Good — worker followed instructions consistently, reliable results
- [ ] Fair — minor inconsistencies noted, results are likely valid
- [ ] Poor — significant inconsistencies, results may not be reliable

*CADS field: `worker_cooperation`*

---

**F4. Technician Notes**

> _______________________________________________________________
> _______________________________________________________________
> _______________________________________________________________

*CADS field: Test Record `notes`*

---

## 4. CADS Field Mapping

Complete reference mapping from questionnaire items to CADS Questionnaire Record fields (CADS-v1.0, Section 5.5).

| Question | CADS Record | Field | Type |
|---|---|---|---|
| A1 | Questionnaire | `hours_since_noise_exposure` | decimal |
| B1 | Worker | `years_noise_exposed` | integer |
| B2 | Questionnaire | `previous_noise_employment` | boolean |
| C1 | Questionnaire | `recreational_shooting` | boolean |
| C1 follow-up | Questionnaire | `recreational_shooting_frequency` | enum |
| C2 | Questionnaire | `power_tools_use` | boolean |
| C3 | Questionnaire | `motorsports` | boolean |
| C4 | Questionnaire | `music_performance` | boolean |
| D1 | Questionnaire | `hpd_type` | enum |
| D2 | Questionnaire | `hpd_consistency` | enum |
| D3 | Questionnaire | `hpd_fit_training_received` | boolean |
| E1 | Questionnaire | `ear_surgery_history` | boolean |
| E2 | Questionnaire | `ear_infection_history` | boolean |
| E3 | Questionnaire | `ototoxic_medication` | boolean |
| E4 | Questionnaire | `tinnitus_present` | boolean |
| E4 follow-up | Questionnaire | `tinnitus_frequency` | enum |
| E5 | Questionnaire | `self_reported_hearing_difficulty` | boolean |
| F1 | Test | `otoscopy_right`, `otoscopy_notes` | enum, string |
| F2 | Test | `otoscopy_left`, `otoscopy_notes` | enum, string |
| F3 | Questionnaire | `worker_cooperation` | enum |
| F4 | Test | `notes` | string |

---

## 5. Guidance Notes

### On Quiet Period

The 14-hour quiet period prior to audiometric testing is the standard recommended by WorkSafeBC, Alberta OHS, and Saskatchewan OHS, and is consistent with NIOSH guidance. Its purpose is to allow any temporary threshold shift (TTS) caused by recent noise exposure to resolve before testing, so that the audiogram reflects the worker's true hearing status rather than a temporary effect.

When a worker cannot meet the 14-hour quiet period, the test should be rescheduled if operationally possible. When rescheduling is not possible — for example, when a worker is departing employment or the testing schedule cannot be altered — the actual quiet period should be recorded accurately and a note added. Results from tests with shorter quiet periods should be interpreted with caution and the limitation documented.

**Record the actual quiet period. Never falsify this field.**

### On Non-Occupational Noise

Non-occupational noise history does not disqualify a worker from testing and does not change the STS calculation methodology. It provides important context for interpreting threshold changes over time. A worker who hunts regularly and shows a 4000 Hz notch pattern may be experiencing combined occupational and recreational noise exposure — context that matters for the employer's program and for any referral recommendation.

### On Ototoxic Medications

The following medication classes are associated with potential ototoxicity and should be flagged when reported by the worker:

- **Aminoglycoside antibiotics** — gentamicin, tobramycin, amikacin, streptomycin
- **Loop diuretics** — furosemide (Lasix), ethacrynic acid
- **Platinum-based chemotherapy** — cisplatin, carboplatin
- **High-dose salicylates** — ASA (aspirin) in doses above 6–8 g/day
- **Quinine** and related antimalarials

Over-the-counter medications at normal doses are generally not ototoxic. If the worker is uncertain whether their medication affects hearing, record `true` and note the medication name if they can provide it.

### On Tinnitus

The presence of tinnitus does not prevent testing and is not a contraindication. It is documented because tinnitus can be an early indicator of noise-induced cochlear damage, even before threshold shifts appear on the audiogram. Persistent or worsening tinnitus in a noise-exposed worker warrants attention and may support a referral recommendation independent of audiometric thresholds.

### On Worker Cooperation

Worker cooperation is assessed by the technician after completing the audiometric test and reflects the reliability of the results. Factors that may indicate poor cooperation include:

- Inconsistent responses on repeated frequencies (>5 dB difference on retests)
- Unusually consistent responses suggesting anticipatory responses
- Worker distraction, fatigue, or apparent difficulty understanding instructions
- Audiogram pattern inconsistent with history or prior results

A rating of `poor` sets the test outcome to `retest_required` regardless of threshold results.

---

*Canadian Audiometric Data Standard (CADS) — Questionnaire Instrument v1.0*
*© RoadPilotAI — Open specification. See repository for licensing terms.*
