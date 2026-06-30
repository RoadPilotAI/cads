# CADS Standardized Pre-Test Questionnaire
## Canadian Audiometric Data Standard — Questionnaire Instrument v1.0

**Status:** Draft
**Version:** 1.0.2
**Date:** June 2026
**Maintainer:** AudioPilot

---

## Table of Contents

- [1. Overview](#1-overview)
- [2. Administration Guidelines](#2-administration-guidelines)
  - [Worker Pre-Completion via CADS Worker](#worker-pre-completion-via-worker-pwa)
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

The CADS Standardized Pre-Test Questionnaire is the instrument used to collect worker health and noise exposure history before conducting an industrial audiometric test. It is administered by the technician at the start of each test session, or pre-completed by the worker via the CADS CADS Worker before arriving at the test site.

**Purpose:**

- Identify pre-test conditions that may affect audiometric results (particularly recent noise exposure)
- Document non-occupational noise exposures that provide context for interpreting threshold changes
- Record hearing protection practices relevant to program effectiveness
- Capture medical history that may affect hearing or indicate referral need
- **Establish the occupational attribution record** used in workers' compensation and hearing aid coverage decisions
- Generate a standardized, comparable dataset across all CADS-participating providers and provinces

**Attribution and Compensation**

The questionnaire serves a critical legal and financial function beyond clinical documentation. In all supported provinces, workers' compensation boards may cover the cost of hearing aids and audiological treatment when hearing loss can be attributed to occupational noise exposure. The questionnaire record is primary evidence in this determination.

Non-occupational noise exposures documented in the questionnaire become relevant when attributing the source of a worker's hearing loss. A worker with significant unprotected recreational noise exposure presents a more complex attribution picture than one with purely occupational exposure.

Equally, a worker who consistently reported using hearing protection, who has no significant non-occupational exposures, and who developed a Standard Threshold Shift over time has a well-documented basis for an occupational attribution claim.

**Every answer must be recorded accurately. The questionnaire is a legal document.**

**Design principles:**

- Every question maps to a defined field in the CADS Questionnaire Record (see Section 5.5 of CADS-v1.0)
- Questions are designed to elicit accurate answers through activity-type framing rather than frequency thresholds — reducing the opportunity for strategic answering by workers or advocacy bias by technicians
- Professional proxy estimation by the technician is an accepted and documented practice where direct answers are unavailable or unreliable
- The technician notes field exists to capture context that checkboxes cannot

---

## 2. Administration Guidelines

### Worker Pre-Completion via CADS Worker

The CADS CADS Worker allows workers to complete the questionnaire before arriving at the mobile clinic, using any smartphone or tablet browser. The employer distributes a unique link or QR code to workers in advance of the testing day — no account creation or password is required.

**Pre-completable sections (Sections B through E)** contain questions about occupational history, non-occupational noise exposure, hearing protection habits, and medical history. These answers are stable and do not change from day to day. When a worker pre-completes these sections, the technician simply reviews and confirms the answers on arrival rather than collecting them verbally.

**Day-of sections (Sections A and F)** must be completed at the time of testing. Section A captures recent noise exposure, which is time-sensitive. Section F is completed by the technician and requires physical presence.

**Time savings:** Pre-completion typically reduces per-worker questionnaire time from 5–7 minutes to under 60 seconds at the mobile clinic. Across a 50-worker testing day this recovers two to three hours of testing capacity.

When workers have pre-completed Sections B through E, the technician:
1. Opens the worker's record in CADS Field — the pre-completed questionnaire is displayed
2. Briefly reviews answers with the worker and confirms nothing has changed
3. Collects Section A (recent noise exposure — time sensitive)
4. Proceeds to otoscopy and testing
5. Completes Section F after testing

### Before You Begin

- Confirm the worker's identity and locate or create their Worker Record
- Confirm the test type (baseline, periodic, exit, or retest)
- Check whether the worker has pre-completed Sections B–E via the CADS Worker
- If no pre-completion: administer the full questionnaire verbally or allow the worker to self-complete
- All questions must be answered before proceeding to otoscopy and audiometric testing
- Record answers directly into the CADS system; do not rely on paper transcription

### Quiet Period and Recent Noise Exposure

The most clinically significant pre-test condition is recent noise exposure within the previous two hours. Exposure that ended more than four hours ago is unlikely to produce meaningful temporary threshold shift in most workers.

In industrial testing environments, workers routinely arrive at the mobile clinic directly from their work stations. True quiet periods meeting the 14-hour regulatory ideal are uncommon in practice. Record actual conditions accurately — not the regulatory target.

**When a worker cannot accurately estimate their exposure duration**, the technician may apply a reasonable estimate based on time of day and known shift schedule. For example: a worker tested at 8am one hour into their shift is estimated at under 2 hours; a worker tested at lunch is estimated at 2–4 hours; a worker tested mid-afternoon is estimated at over 4 hours. Document the basis for any estimate in the technician notes field.

**Record actual conditions. Never record the regulatory ideal when actual conditions were different.**

### Worker Instructions

Read or display the following to the worker before beginning:

> *"I'm going to ask you a few questions about your hearing health and noise exposure before we do your hearing test. There are no right or wrong answers — we just want to make sure we have an accurate picture of your situation. This information is kept confidential within your hearing conservation program and may be relevant if you ever make a workers' compensation claim related to your hearing."*

---

## 3. The Questionnaire

Section labels indicate when each section is completed:

- 🕐 **Day-of** — must be collected at the time of testing
- 📱 **Pre-completable** — may be completed in advance via the CADS Worker

Question labels indicate data handling:

- 🔵 **Contextual** — proxy estimation by the technician is acceptable; document basis in notes
- 🔴 **Clinical** — worker's actual answer is required; do not estimate or substitute

---

### Section A — Pre-Test Conditions
🕐 **Day-of — collect at the mobile clinic**

---

**A1.** 🔵 **Have you been exposed to noise today at work or elsewhere?**

- [ ] No
- [ ] Yes

*If Yes:* **How long has it been since you were last in a noisy environment?**

- [ ] Less than 2 hours
- [ ] 2 to 4 hours
- [ ] More than 4 hours

*CADS fields: `recent_noise_exposure`, `recent_exposure_duration`*
*Technician note: If the worker cannot estimate, use time of day and shift schedule as a proxy. Document the basis in the notes field.*

---

### Section B — Occupational Noise History
📱 **Pre-completable via CADS Worker**

---

**B1.** 🔵 **How many years have you worked in noise-exposed roles overall?**

> Years: ______

*CADS field: Worker Record `years_noise_exposed`*

---

**B2.** 🔵 **Have you had previous employment in noisy environments outside of your current employer?**

- [ ] Yes
- [ ] No

*CADS field: `previous_noise_employment`*

---

### Section C — Non-Occupational Noise Exposure
📱 **Pre-completable via CADS Worker**

*Questions in this section use activity-type framing to reduce strategic answering. Ask questions neutrally. Do not suggest answers or apply arbitrary frequency thresholds. Use the technician notes field to document context where a checkbox answer does not fully capture the worker's situation.*

---

**C1.** 🔵 **Do you use firearms recreationally?**

- [ ] No — skip to C2
- [ ] Yes — hunting or casual shooting
- [ ] Yes — competitive or sport shooting (regular range use)

*If Yes:* **Do you wear hearing protection when shooting?**

- [ ] Always
- [ ] Sometimes
- [ ] Never

*CADS fields: `recreational_shooting`, `recreational_shooting_type`, `recreational_shooting_hpd`*

---

**C2.** 🔵 **Do you regularly use loud power tools outside of work** *(woodworking, yard equipment, construction, etc.)*?

- [ ] No — skip to C3
- [ ] Yes

*If Yes:* **Do you wear hearing protection?**

- [ ] Always
- [ ] Sometimes
- [ ] Never

*CADS fields: `power_tools_use`, `power_tools_hpd`*

---

**C3.** 🔵 **Do you participate in or attend motorsports events** *(motorcycle riding, racing, snowmobiling, etc.)*?

- [ ] No — skip to C4
- [ ] Yes — I operate a motorcycle, snowmobile, or race vehicle
- [ ] Yes — I attend events as a spectator

*If Yes:* **Do you wear hearing protection?**

- [ ] Always
- [ ] Sometimes
- [ ] Never

*CADS fields: `motorsports`, `motorsports_type`, `motorsports_hpd`*

---

**C4.** 🔵 **Do you play music or perform in a band?**

- [ ] No — skip to C5
- [ ] Yes — casual (home practice, jam sessions, occasional)
- [ ] Yes — regular performances or gigs

*If Yes:* **Do you wear hearing protection while playing?**

- [ ] Always
- [ ] Sometimes
- [ ] Never

*CADS fields: `music_performance`, `music_performance_type`, `music_performance_hpd`*

---

**C5.** 🔵 **Do you regularly attend loud concerts or live music events?**

- [ ] No
- [ ] Yes — occasionally (a few times per year)
- [ ] Yes — regularly (monthly or more)

*CADS field: `concert_attendance`*

---

**C — Technician Observation**

> Non-occupational exposure context: _______________________________________________
> ________________________________________________________________________________

*Use this field to document any relevant context that checkboxes do not capture — for example: "Competitive trap shooter, reports consistent HPD use, audiogram pattern consistent with this history" or "Hunter, reports no HPD use during hunting season."*

*CADS field: Questionnaire `non_occupational_notes`*

---

### Section D — Hearing Protection
📱 **Pre-completable via CADS Worker**

---

**D1.** 🔵 **What type of hearing protection do you use at work?**

- [ ] Foam earplugs (disposable)
- [ ] Pre-moulded earplugs (reusable)
- [ ] Earmuffs
- [ ] Custom-moulded earplugs
- [ ] Combination (plugs and muffs together)
- [ ] None

*CADS field: `hpd_type`*

---

**D2.** 🔵 **How consistently do you wear your hearing protection when working in noisy areas?**

- [ ] Always — I wear it whenever I am in a noisy area
- [ ] Usually — I wear it most of the time but occasionally forget
- [ ] Sometimes — I wear it some of the time
- [ ] Never — I do not wear hearing protection
- [ ] Not applicable — I am not exposed to hazardous noise levels

*CADS field: `hpd_consistency`*

---

**D3.** 🔵 **Have you received training or instruction on how to properly fit your hearing protection?**

- [ ] Yes
- [ ] No

*CADS field: `hpd_fit_training_received`*

---

### Section E — Medical History
📱 **Pre-completable via CADS Worker**

---

**E1.** 🔴 **Have you ever had surgery on either ear?**

- [ ] Yes
- [ ] No

*CADS field: `ear_surgery_history`*

---

**E2.** 🔴 **Do you have a history of chronic or recurring ear infections?**

- [ ] Yes
- [ ] No

*CADS field: `ear_infection_history`*

---

**E3.** 🔴 **Are you currently taking any medications that may affect your hearing?**

- [ ] Yes
- [ ] No
- [ ] Unsure

*CADS field: `ototoxic_medication`*
*Record `true` if the worker indicates medications that may affect hearing. Common ototoxic medications include certain antibiotics (aminoglycosides), loop diuretics, high-dose ASA, and some chemotherapy agents. If unsure, record `true` and note the medication name if available.*

---

**E4.** 🔴 **Do you experience ringing, buzzing, or other sounds in your ears (tinnitus)?**

- [ ] Yes
- [ ] No

*CADS field: `tinnitus_present`*

*If Yes:* **How often do you notice it?**

- [ ] Constant — I hear it all the time
- [ ] Frequent — I hear it most days
- [ ] Occasional — I hear it sometimes
- [ ] Rare — I only notice it occasionally

*CADS field: `tinnitus_frequency`*

---

**E5.** 🔴 **Do you feel you have difficulty hearing in your daily life** — for example, in conversation, on the phone, or in noisy environments?

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

*CADS field: Test Record `notes`*

---

## 4. CADS Field Mapping

| Question | CADS Record | Field | Type | Pre-completable | Type |
|---|---|---|---|---|---|
| A1 | Questionnaire | `recent_noise_exposure` | boolean | No | 🔵 Contextual |
| A1 follow-up | Questionnaire | `recent_exposure_duration` | enum | No | 🔵 Contextual |
| B1 | Worker | `years_noise_exposed` | integer | Yes | 🔵 Contextual |
| B2 | Questionnaire | `previous_noise_employment` | boolean | Yes | 🔵 Contextual |
| C1 | Questionnaire | `recreational_shooting` | boolean | Yes | 🔵 Contextual |
| C1 type | Questionnaire | `recreational_shooting_type` | enum | Yes | 🔵 Contextual |
| C1 HPD | Questionnaire | `recreational_shooting_hpd` | enum | Yes | 🔵 Contextual |
| C2 | Questionnaire | `power_tools_use` | boolean | Yes | 🔵 Contextual |
| C2 HPD | Questionnaire | `power_tools_hpd` | enum | Yes | 🔵 Contextual |
| C3 | Questionnaire | `motorsports` | boolean | Yes | 🔵 Contextual |
| C3 type | Questionnaire | `motorsports_type` | enum | Yes | 🔵 Contextual |
| C3 HPD | Questionnaire | `motorsports_hpd` | enum | Yes | 🔵 Contextual |
| C4 | Questionnaire | `music_performance` | boolean | Yes | 🔵 Contextual |
| C4 type | Questionnaire | `music_performance_type` | enum | Yes | 🔵 Contextual |
| C4 HPD | Questionnaire | `music_performance_hpd` | enum | Yes | 🔵 Contextual |
| C5 | Questionnaire | `concert_attendance` | enum | Yes | 🔵 Contextual |
| C notes | Questionnaire | `non_occupational_notes` | string | Yes | 🔵 Contextual |
| D1 | Questionnaire | `hpd_type` | enum | Yes | 🔵 Contextual |
| D2 | Questionnaire | `hpd_consistency` | enum | Yes | 🔵 Contextual |
| D3 | Questionnaire | `hpd_fit_training_received` | boolean | Yes | 🔵 Contextual |
| E1 | Questionnaire | `ear_surgery_history` | boolean | Yes | 🔴 Clinical |
| E2 | Questionnaire | `ear_infection_history` | boolean | Yes | 🔴 Clinical |
| E3 | Questionnaire | `ototoxic_medication` | boolean | Yes | 🔴 Clinical |
| E4 | Questionnaire | `tinnitus_present` | boolean | Yes | 🔴 Clinical |
| E4 follow-up | Questionnaire | `tinnitus_frequency` | enum | Yes | 🔴 Clinical |
| E5 | Questionnaire | `self_reported_hearing_difficulty` | boolean | Yes | 🔴 Clinical |
| F1 | Test | `otoscopy_right`, `otoscopy_notes` | enum, string | No | 🔵 Contextual |
| F2 | Test | `otoscopy_left`, `otoscopy_notes` | enum, string | No | 🔵 Contextual |
| F3 | Questionnaire | `worker_cooperation` | enum | No | 🔵 Contextual |
| F4 | Test | `notes` | string | No | 🔵 Contextual |

---

## 5. Guidance Notes

### On Questionnaire Integrity

The questionnaire record is a legal document. It may be reviewed in workers' compensation proceedings, regulatory inspections, or litigation. Two forms of bias can compromise its integrity:

**Worker strategic answering.** Workers naturally answer in ways they believe serve their interests — reporting HPD use as "always" because that sounds like the right answer, or downplaying recreational noise exposure they believe might affect their claim eligibility. The activity-type framing used in Section C is designed to reduce this. Questions about *what kind* of activity the worker does are harder to game than questions about *how often*, because the attribution implications of specific answers are not obvious to most workers.

**Technician advocacy bias.** Some technicians frame questions in ways designed to produce answers they believe will benefit the worker — applying arbitrary frequency thresholds ("do you shoot at least six times a year?") or omitting activities they consider insignificant. This is a form of record falsification regardless of intent. A technician who documents "no recreational shooting" for a hunter who shoots twice a year without protection has produced an inaccurate attribution record.

The distinction between advocacy bias and legitimate proxy estimation matters. **Proxy estimation** uses available contextual information — time of day, shift schedule, visual observation, worker statements — to produce the best available estimate when a direct answer is unavailable or unreliable. The basis for the estimate is documented in the notes field. This is professional judgment and is an accepted practice under this standard. **Advocacy bias** selectively omits or frames information to steer an outcome. It is not.

Accurate documentation protects everyone. A clean, honestly documented record is harder to challenge than one that appears coached. Workers with legitimate occupational claims are better served by accurate records than by records that look manipulated.

### On Proxy Estimation

Proxy estimation is accepted practice for all Contextual (🔵) questions in this questionnaire. When a worker cannot or will not provide an accurate answer, the technician uses available information to produce a reasonable estimate. Examples:

- Recent noise exposure duration estimated from time of day and shift schedule
- Recreational shooting frequency inferred from regional context, season, or worker appearance and statements
- HPD consistency cross-referenced against audiogram pattern and plug condition

Document the basis for any estimate in the technician notes field or the non-occupational notes field. "Estimated based on shift time — worker 3 hours into afternoon shift" is a defensible note. An unchallenged checkbox with no supporting context is not.

Clinical (🔴) questions require the worker's actual answer. Do not estimate or substitute for Section E questions.

### On Non-Occupational Noise and Attribution

Activity type is a stronger predictor of attribution significance than frequency alone. Field experience indicates:

- **Competitive and sport shooters** typically wear adequate hearing protection and represent lower attribution risk. Consistent HPD use in recreational shooting is also a positive indicator of HPD compliance at work.
- **Hunters** typically do not wear hearing protection due to the practical impossibility of rapid insertion. Even infrequent hunting represents meaningful unprotected exposure, particularly to high-impulse rifle noise.
- **Casual musicians** (home practice, jam sessions) rarely wear hearing protection. Regular performers at gigs may wear musician-grade protection.
- **Power tool users** most commonly report wearing hearing protection. Lower attribution significance in most cases.
- **Motorsports operators** (motorcycle, snowmobile) are approximately half protected, half unprotected. Spectators at events typically do not wear protection but exposure duration varies.

The technician observation field at the end of Section C exists specifically to capture this kind of nuance. A sentence of context — "competitive trap shooter, consistent HPD use reported and supported by audiogram pattern" — is more useful to an attribution determination than any combination of checkboxes.

### On Attribution and Compensation

Workers' compensation boards assess hearing loss claims by weighing evidence for occupational versus non-occupational causation. The questionnaire data informs this assessment in both directions.

Data that supports an occupational attribution claim includes consistent HPD non-use at work, absence of significant non-occupational exposure, and progressive STS documented over time. Data that complicates attribution includes significant unprotected recreational noise exposure and ototoxic medication use coinciding with threshold shifts.

Technicians must not coach workers toward answers that support or undermine a compensation outcome. Administer the questionnaire neutrally and record answers accurately.

### On Recent Noise Exposure

The 14-hour quiet period is the regulatory ideal. In industrial testing environments — where workers typically arrive at the mobile clinic directly from their work stations — it is rarely achieved in practice. The questionnaire captures the actual situation using a practical two-hour threshold rather than asking workers to estimate hours since last exposure, which produces unreliable answers and invites falsification.

Tests conducted with recent noise exposure under two hours should be noted. Where this affects a borderline STS result, a retest under better conditions should be recommended.

### On Ototoxic Medications

The following medication classes are associated with potential ototoxicity:

- **Aminoglycoside antibiotics** — gentamicin, tobramycin, amikacin, streptomycin
- **Loop diuretics** — furosemide (Lasix), ethacrynic acid
- **Platinum-based chemotherapy** — cisplatin, carboplatin
- **High-dose salicylates** — ASA at doses above 6–8 g/day
- **Quinine** and related antimalarials

Record `true` if the worker indicates any of these. If uncertain, record `true` and note the medication name.

### On Tinnitus

Tinnitus does not prevent testing. It is documented because it can be an early indicator of noise-induced cochlear damage before threshold shifts appear on the audiogram, and because it is a recognized compensable condition in some provincial workers' compensation frameworks.

### On Worker Cooperation

Worker cooperation is assessed after testing. A rating of `poor` sets the test outcome to `retest_required` regardless of threshold results. Factors indicating poor cooperation include inconsistent responses on repeated frequencies (greater than 5 dB difference on retests), unusually consistent responses suggesting anticipatory button pressing, and audiogram patterns inconsistent with history.

---

*CADS/Standard — Questionnaire Instrument v1.0.2*
*© AudioPilot — Open specification. See repository for licensing terms.*
