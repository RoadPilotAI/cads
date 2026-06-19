# CADS Standardized Pre-Test Questionnaire
## Canadian Audiometric Data Standard — Questionnaire Instrument v1.0

**Status:** Draft
**Version:** 1.0.1
**Date:** June 2026
**Maintainer:** RoadPilotAI

---

## Table of Contents

- [1. Overview](#1-overview)
- [2. Administration Guidelines](#2-administration-guidelines)
  - [Worker Pre-Completion via Worker PWA](#worker-pre-completion-via-worker-pwa)
  - [Before You Begin](#before-you-begin)
  - [Quiet Period](#quiet-period)
  - [Worker Instructions](#worker-instructions)
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

The CADS Standardized Pre-Test Questionnaire is the instrument used to collect worker health and noise exposure history before conducting an industrial audiometric test. It is administered by the technician at the start of each test session, or pre-completed by the worker via the CADS Worker PWA before arriving at the test site.

**Purpose:**

- Identify pre-test conditions that may affect audiometric results (particularly quiet period compliance)
- Document non-occupational noise exposures that provide context for interpreting threshold changes
- Record hearing protection practices relevant to program effectiveness
- Capture medical history that may affect hearing or indicate referral need
- **Establish the occupational attribution record** used in workers' compensation and hearing aid coverage decisions
- Generate a standardized, comparable dataset across all CADS-participating providers and provinces

**Attribution and Compensation**

The questionnaire serves a critical legal and financial function beyond clinical documentation. In all supported provinces, workers' compensation boards (including WorkSafeBC and WCB Alberta) may cover the cost of hearing aids and audiological treatment when hearing loss can be attributed to occupational noise exposure. The questionnaire record is primary evidence in this determination.

Non-occupational noise exposures documented in the questionnaire — recreational shooting, power tool use, motorsports — become relevant when attributing the source of a worker's hearing loss. A worker with significant recreational noise exposure and occupational noise exposure presents a more complex attribution picture than one with purely occupational exposure.

Equally, a worker who consistently reported using hearing protection, who has no significant non-occupational exposures, and who developed a Standard Threshold Shift over time has a well-documented basis for an occupational attribution claim.

**Every answer matters. Every answer must be accurate.**

**Design principle:** Every question maps to a defined field in the CADS Questionnaire Record (see Section 5.5 of CADS-v1.0). No question is included that does not serve a specific data or clinical purpose. No required data element is left uncaptured.

---

## 2. Administration Guidelines

### Worker Pre-Completion via Worker PWA

The CADS Worker PWA allows workers to complete the questionnaire before arriving at the mobile clinic, using any smartphone or tablet browser. The employer distributes a unique link or QR code to workers in advance of the testing day — no account creation or password is required.

**Pre-completable sections (Sections B through E)** contain questions about occupational history, non-occupational noise exposure, hearing protection habits, and medical history. These answers are stable and do not change from day to day. When a worker pre-completes these sections, the technician simply reviews and confirms the answers on arrival rather than collecting them verbally.

**Day-of sections (Sections A and F)** must be completed at the time of testing. Section A captures the quiet period, which is time-sensitive and cannot be collected in advance. Section F is completed by the technician and requires physical presence.

**Time savings:** Pre-completion typically reduces per-worker questionnaire time from 5–7 minutes to under 60 seconds at the mobile clinic. Across a 50-worker testing day this recovers two to three hours of testing capacity.

When workers have pre-completed Sections B through E, the technician:
1. Opens the worker's record in TechTool — the pre-completed questionnaire is displayed
2. Briefly reviews answers with the worker and confirms nothing has changed
3. Collects Section A (quiet period) verbally
4. Proceeds to otoscopy and testing
5. Completes Section F after testing

### Before You Begin

- Confirm the worker's identity and locate or create their Worker Record
- Confirm the test type (baseline, periodic, exit, or retest)
- Check whether the worker has pre-completed Sections B–E via the Worker PWA
- If no pre-completion: administer the full questionnaire verbally or allow the worker to self-complete
- All questions must be answered before proceeding to otoscopy and audiometric testing
- Record answers directly into the CADS system; do not rely on paper transcription

### Quiet Period

The most critical pre-test condition is quiet period compliance. If the worker has been exposed to significant noise within the past 14 hours, the test should be rescheduled where possible. If rescheduling is not possible, document the actual quiet period accurately and note the circumstance. **Do not record 14 hours if the actual period was less — accurate data is the priority.**

### Worker Instructions

Read or display the following to the worker before beginning:

> *"I'm going to ask you a few questions about your hearing health and noise exposure before we do your hearing test. There are no right or wrong answers — we just want to make sure we have an accurate picture of your situation. This information is kept confidential within your hearing conservation program and may be relevant if you ever make a workers' compensation claim related to your hearing."*

---

## 3. The Questionnaire

Section labels indicate when each section is completed:

- 🕐 **Day-of** — must be collected at the time of testing
- 📱 **Pre-completable** — may be completed in advance via the Worker PWA

---

### Section A — Pre-Test Conditions
🕐 **Day-of — collect at the mobile clinic**

---

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
📱 **Pre-completable via Worker PWA**

---

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
📱 **Pre-completable via Worker PWA**

---

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
📱 **Pre-completable via Worker PWA**

---

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
📱 **Pre-completable via Worker PWA**

---

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
🕐 **Day-of — completed by the technician**

*This section is not presented to the worker.*

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

| Question | CADS Record | Field | Type | Pre-completable |
|---|---|---|---|---|
| A1 | Questionnaire | `hours_since_noise_exposure` | decimal | No |
| B1 | Worker | `years_noise_exposed` | integer | Yes |
| B2 | Questionnaire | `previous_noise_employment` | boolean | Yes |
| C1 | Questionnaire | `recreational_shooting` | boolean | Yes |
| C1 follow-up | Questionnaire | `recreational_shooting_frequency` | enum | Yes |
| C2 | Questionnaire | `power_tools_use` | boolean | Yes |
| C3 | Questionnaire | `motorsports` | boolean | Yes |
| C4 | Questionnaire | `music_performance` | boolean | Yes |
| D1 | Questionnaire | `hpd_type` | enum | Yes |
| D2 | Questionnaire | `hpd_consistency` | enum | Yes |
| D3 | Questionnaire | `hpd_fit_training_received` | boolean | Yes |
| E1 | Questionnaire | `ear_surgery_history` | boolean | Yes |
| E2 | Questionnaire | `ear_infection_history` | boolean | Yes |
| E3 | Questionnaire | `ototoxic_medication` | boolean | Yes |
| E4 | Questionnaire | `tinnitus_present` | boolean | Yes |
| E4 follow-up | Questionnaire | `tinnitus_frequency` | enum | Yes |
| E5 | Questionnaire | `self_reported_hearing_difficulty` | boolean | Yes |
| F1 | Test | `otoscopy_right`, `otoscopy_notes` | enum, string | No |
| F2 | Test | `otoscopy_left`, `otoscopy_notes` | enum, string | No |
| F3 | Questionnaire | `worker_cooperation` | enum | No |
| F4 | Test | `notes` | string | No |

---

## 5. Guidance Notes

### On Attribution and Compensation

The questionnaire record is a primary document in workers' compensation proceedings. In all supported provinces, compensation boards assess hearing loss claims by weighing the evidence for occupational versus non-occupational causation. The questionnaire data directly informs this assessment.

**Data that supports an occupational attribution claim:**
- Consistent HPD non-use (`hpd_consistency`: `sometimes` or `never`) over multiple periodic tests demonstrates the employer's program did not achieve adequate worker protection
- Absence of significant non-occupational noise exposure isolates occupational noise as the primary cause
- Progressive STS documented over time in a noise-exposed worker with consistent program participation

**Data that complicates attribution:**
- Significant recreational shooting documented across multiple years of testing
- Multiple non-occupational noise sources in combination
- Ototoxic medication use coinciding with periods of threshold shift

**This is not a reason to alter or omit answers.** Accurate documentation protects all parties. A worker with mixed occupational and non-occupational exposure may still be entitled to partial compensation. Falsified records expose the technician, the hearing test company, and the employer to significant legal liability.

Technicians must not coach workers toward answers that support or undermine a compensation outcome. Administer the questionnaire neutrally and record answers accurately.

### On the Worker PWA

The CADS Worker PWA is a smartphone-optimized Progressive Web App that allows workers to pre-complete Sections B through E before arriving at the mobile clinic. It is accessed via a unique link or QR code distributed by the employer — no account creation or password is required.

**Designed for the industrial worker:**
- Large touch targets, plain language, minimal scrolling
- Estimated completion time: 2–3 minutes
- Works on any smartphone browser, no app download required
- Available in English and French

**Distribution options:**
- QR code posted at the worksite entrance or break room in advance of testing day
- Link sent by the employer via email or SMS with the test appointment notification
- QR code on the technician's mobile clinic door for workers who arrive without pre-completing

**Data handling:**
- Responses are held securely and linked to the worker's unique test session token
- No personally identifiable information is stored on the worker's device
- Pre-completed responses are available in TechTool when the worker arrives
- If a worker does not pre-complete, the full questionnaire is administered verbally as normal — there is no disruption to the workflow

### On Quiet Period

The 14-hour quiet period prior to audiometric testing is the standard recommended by WorkSafeBC, Alberta OHS, and Saskatchewan OHS, consistent with NIOSH guidance. Its purpose is to allow any temporary threshold shift (TTS) caused by recent noise exposure to resolve before testing, so that the audiogram reflects the worker's true hearing status.

When a worker cannot meet the 14-hour quiet period, the test should be rescheduled if operationally possible. When rescheduling is not possible, the actual quiet period should be recorded accurately and a note added. Results from tests with shorter quiet periods should be interpreted with caution.

**Record the actual quiet period. Never falsify this field.**

### On Non-Occupational Noise

Non-occupational noise history does not disqualify a worker from testing and does not change the STS calculation methodology. It provides important context for interpreting threshold changes over time and for attribution determinations. A worker who hunts regularly and shows a 4000 Hz notch pattern may be experiencing combined occupational and recreational noise exposure — context that matters for the employer's program and for any referral or compensation recommendation.

### On Ototoxic Medications

The following medication classes are associated with potential ototoxicity and should be flagged when reported by the worker:

- **Aminoglycoside antibiotics** — gentamicin, tobramycin, amikacin, streptomycin
- **Loop diuretics** — furosemide (Lasix), ethacrynic acid
- **Platinum-based chemotherapy** — cisplatin, carboplatin
- **High-dose salicylates** — ASA (aspirin) in doses above 6–8 g/day
- **Quinine** and related antimalarials

Over-the-counter medications at normal doses are generally not ototoxic. If the worker is uncertain whether their medication affects hearing, record `true` and note the medication name if they can provide it.

### On Tinnitus

The presence of tinnitus does not prevent testing and is not a contraindication. It is documented because tinnitus can be an early indicator of noise-induced cochlear damage, even before threshold shifts appear on the audiogram. Persistent or worsening tinnitus in a noise-exposed worker warrants attention and may support a referral recommendation independent of audiometric thresholds. Tinnitus is also a recognized compensable condition in some provincial workers' compensation frameworks.

### On Worker Cooperation

Worker cooperation is assessed by the technician after completing the audiometric test and reflects the reliability of the results. Factors that may indicate poor cooperation include:

- Inconsistent responses on repeated frequencies (>5 dB difference on retests)
- Unusually consistent responses suggesting anticipatory button pressing
- Worker distraction, fatigue, or apparent difficulty understanding instructions
- Audiogram pattern inconsistent with history or prior results

A rating of `poor` sets the test outcome to `retest_required` regardless of threshold results.

---

*Canadian Audiometric Data Standard (CADS) — Questionnaire Instrument v1.0.1*
*© RoadPilotAI — Open specification. See repository for licensing terms.*
