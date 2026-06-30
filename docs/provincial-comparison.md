# CADS Provincial & Territorial Regulatory Comparison
## Hearing Conservation Requirements Across Canada
**Draft v0.2 — June 2026**
**Source:** CCOHS, OHS Insider, WorkSafeBC, Alberta OHS, and jurisdiction-specific regulations
**Verification status:** Research draft — regulatory references noted for independent verification

---

## Table of Contents

- [1. Purpose](#1-purpose)
- [2. Key Findings](#2-key-findings)
- [3. Complete Comparison Matrix](#3-complete-comparison-matrix)
- [4. What Belongs in the CADS Core Standard](#4-what-belongs-in-the-cads-core-standard)
- [5. What Belongs in Provincial Profiles](#5-what-belongs-in-provincial-profiles)
- [6. Jurisdiction Reference Cards](#6-jurisdiction-reference-cards)
- [7. Verification Checklist](#7-verification-checklist)

---

## 1. Purpose

This document maps hearing conservation regulatory requirements across all Canadian provinces and territories. It serves as the research foundation for the CADS Core Standard and Provincial Profile architecture.

The goal is not to identify which provinces do it best. The goal is to identify what every jurisdiction has in common — that becomes the core — and what differs between jurisdictions — that becomes a province-specific profile.

The CADS standard makes no judgment about regulatory frameworks. It captures the common ground and honours jurisdictional authority.

---

## 2. Key Findings

**Finding 1 — The exposure limit is effectively universal.**
Every province and territory uses 85 dBA TWA as the occupational exposure limit, with 140 dBC or dB peak. The sole exception is the Federal jurisdiction at 87 dBA. This is the most harmonized element of hearing conservation regulation across Canada.

**Finding 2 — The STS definition is consistent where defined.**
All jurisdictions that define Standard Threshold Shift use the same definition: an average shift of 10 dB or more at 2000, 3000, and 4000 Hz in either ear. This is aligned with NIOSH 1998 and CSA Z107.6.

**Finding 3 — Five jurisdictions have no specific HCP requirement.**
Ontario, Quebec, New Brunswick, Nova Scotia, and Yukon do not specifically require a formal Hearing Conservation Program. Employers in these provinces rely on general duty of care. This is a significant gap in national hearing conservation coverage.

**Finding 4 — Three jurisdictions have no specific audiometric testing requirement.**
Federal, Ontario, and Nova Scotia do not specifically require audiometric testing. New Brunswick requires it only for underground mine workers.

**Finding 5 — Testing frequency is not uniform.**
Where audiometric testing is required, frequency varies: annual (BC, NL, PEI, Yukon) versus biennial (AB, MB, SK, NWT, Nunavut). This is the most significant operational difference across jurisdictions.

**Finding 6 — Baseline timing has one meaningful variation.**
Newfoundland and Labrador requires baseline audiometric testing within 3 months of first exposure. All other provinces specify 6 months. This is a notable and verifiable difference.

**Finding 7 — Exit testing is only specifically required in BC.**
WorkSafeBC is the only Canadian jurisdiction that specifically requires an exit audiometric test. Other provinces may recommend it but do not mandate it.

**Finding 8 — The CADS standard applies regardless of whether testing is mandated.**
The standard governs how audiometric data is captured when testing occurs. Whether testing is mandated by regulation or conducted as best practice under general duty of care is a provincial profile matter, not a standard matter. In Ontario and Nova Scotia, CADS-compliant testing demonstrates due diligence beyond the regulatory minimum.

---

## 3. Complete Comparison Matrix

### 3.1 Noise Exposure Limits

| Jurisdiction | Exposure Limit | Peak Limit | Exchange Rate | Action Level |
|---|---|---|---|---|
| Federal | **87 dBA** | — | 3 dB | 84 dBA |
| British Columbia | 85 dBA Lex | 140 dBC | 3 dB | 82 dBA |
| Alberta | 85 dBA | 140 dBC | 3 dB | 82 dBA |
| Saskatchewan | 85 dBA Lex | — | 3 dB | 80 dBA |
| Manitoba | 85 dBA Lex | — | 3 dB | 80 dBA |
| Ontario | 85 dBA Lex | — | 3 dB | — |
| Quebec | 85 dBA | 140 dB | 3 dB | — |
| New Brunswick | 85 dBA | 140 dBC | 3 dB | 80 dBA |
| Nova Scotia | 85 dBA | — | 3 dB | — |
| Prince Edward Island | 85 dBA | — | 3 dB | — |
| Newfoundland & Labrador | 85 dBA | **140 dBA** | 3 dB | — |
| Northwest Territories | 85 dBA Lex | — | 3 dB | 80 dBA |
| Nunavut | 85 dBA Lex | — | 3 dB | 80 dBA |
| Yukon | 85 dBA | 140 dB | 3 dB | **80 dBA** |

> **CADS Core conclusion:** 85 dBA TWA and 3 dB exchange rate are effectively universal. Federal at 87 dBA is the sole exception and becomes a Federal Profile configuration item.

---

### 3.2 Hearing Conservation Program Requirements

| Jurisdiction | HCP Required | Trigger | Worker Threshold | Written HCP |
|---|---|---|---|---|
| Federal | No specific requirement | General duty | — | — |
| British Columbia | ✓ Yes | Above 85 dBA Lex or 140 dBC | None | ✓ Required |
| Alberta | ✓ Yes | Hazardous noise exposure | None | ✓ Required |
| Saskatchewan | ✓ Yes | Above 85 dBA Lex | **10+ workers** | ✓ Required |
| Manitoba | No specific requirement | General duty | — | — |
| Ontario | No specific requirement | General duty | — | — |
| Quebec | No specific requirement | General duty | — | — |
| New Brunswick | No specific requirement | General duty | — | — |
| Nova Scotia | No specific requirement | General duty | — | — |
| Prince Edward Island | ✓ Yes | Hazardous noise exposure | None | ✓ Required |
| Newfoundland & Labrador | ✓ Yes | Above 85 dBA | None | ✓ Required |
| Northwest Territories | ✓ Yes | Above 85 dBA Lex | **20+ workers** | ✓ Required |
| Nunavut | ✓ Yes | Above 85 dBA Lex | **20+ workers** | ✓ Required |
| Yukon | No specific requirement | General duty | — | — |

> **CADS Core conclusion:** Written HCP is required in seven of fourteen jurisdictions. Five have no specific requirement. This cannot be a core standard requirement — it becomes a provincial profile field: `hcp_required` (boolean) and `hcp_worker_threshold` (integer).

---

### 3.3 Audiometric Testing Requirements

| Jurisdiction | Testing Required | Trigger | Baseline | Periodic Frequency | Exit Test |
|---|---|---|---|---|---|
| Federal | No | — | — | — | — |
| British Columbia | ✓ Yes | Above 85 dBA Lex | Within 6 months | **Annual** | **Required** |
| Alberta | ✓ Yes | Hazardous noise | Within 6 months | 12 months then **biennial** | Recommended |
| Saskatchewan | ✓ Yes | Above 85 dBA Lex | Not specified | **Biennial** | Recommended |
| Manitoba | ✓ Yes | Above 85 dBA Lex | Within 6 months | **Biennial** | Not specified |
| Ontario | No | — | — | — | — |
| Quebec | ⚠️ Verify | Above 85 dBA | Not specified | Not specified | — |
| New Brunswick | ⚠️ Mines only | Underground mines | Not specified | Bi-annual | — |
| Nova Scotia | No | — | — | — | — |
| Prince Edward Island | ✓ Yes | Hazardous noise | Within 6 months | **Annual** | Not specified |
| Newfoundland & Labrador | ✓ Yes | Above 85 dBA | **Within 3 months** | **Annual** | Not specified |
| Northwest Territories | ✓ Yes | Above 85 dBA Lex | Not specified | **Biennial** | Not specified |
| Nunavut | ✓ Yes | Above 85 dBA Lex | Not specified | **Biennial** | Not specified |
| Yukon | ✓ Yes | **Above 80 dBA** | Within 6 months | **Annual** | Not specified |

> **⚠️ Note on Quebec:** CCOHS lists Quebec as requiring audiometric testing above the OEL. OHS Insider lists it as "not specifically required." This discrepancy requires direct regulatory verification before the Quebec profile is finalized.

> **CADS Core conclusion:** Testing frequency and baseline timing are not uniform. These become provincial profile fields: `testing_frequency` (enum: annual/biennial), `baseline_months` (integer), `exit_test_required` (boolean).

---

### 3.4 Standard Threshold Shift Definition

| Jurisdiction | STS Defined | Definition | Age Correction |
|---|---|---|---|
| Federal | Not specifically defined | — | — |
| British Columbia | ✓ Yes | 10 dB average at 2000, 3000, 4000 Hz | Permitted |
| Alberta | ✓ Yes | 10 dB average at 2000, 3000, 4000 Hz | Permitted |
| Saskatchewan | ✓ Yes | 10 dB average at 2000, 3000, 4000 Hz | Permitted |
| Manitoba | ✓ Yes | 10 dB average at 2000, 3000, 4000 Hz | Permitted |
| Ontario | Not specifically defined | — | — |
| Quebec | ⚠️ Verify | — | — |
| New Brunswick | Not specifically defined | — | — |
| Nova Scotia | Not specifically defined | — | — |
| Prince Edward Island | ✓ Yes | 10 dB average at 2000, 3000, 4000 Hz | Permitted |
| Newfoundland & Labrador | ✓ Yes | 10 dB average at 2000, 3000, 4000 Hz | Permitted |
| Northwest Territories | ✓ Yes | 10 dB average at 2000, 3000, 4000 Hz | Permitted |
| Nunavut | ✓ Yes | 10 dB average at 2000, 3000, 4000 Hz | Permitted |
| Yukon | ✓ Yes | 10 dB average at 2000, 3000, 4000 Hz | Permitted |

> **CADS Core conclusion:** The STS definition is identical across every jurisdiction that defines it. **This is the strongest candidate for the CADS Core Standard.** The definition, methodology, and age correction permission are universal. No provincial profile flag needed.

---

### 3.5 Hearing Protection Requirements

| Jurisdiction | HPD Required At | HPD Standard Referenced |
|---|---|---|
| Federal | Above 87 dBA | CSA Z94.2-M1984 |
| British Columbia | Above 85 dBA Lex | CSA Z94.2-02 |
| Alberta | Above 85 dBA | CSA Z94.2-02 |
| Saskatchewan | Above 85 dBA Lex | CSA Z94.2 |
| Manitoba | Above 85 dBA Lex | CSA Z94.2-14 |
| Ontario | Above 85 dBA Lex | Not specified |
| Quebec | Above 85 dBA | CSA Z94.2-2014 |
| New Brunswick | Above 85 dBA | Not specified |
| Nova Scotia | Above 85 dBA | Not specified |
| Prince Edward Island | Above 85 dBA | CSA Z94.2-02 |
| Newfoundland & Labrador | Above 85 dBA | CSA Z94.2 |
| Northwest Territories | Above 85 dBA Lex | Not specified |
| Nunavut | Above 85 dBA Lex | Not specified |
| Yukon | Above 85 dBA | Not specified |

> **CADS Core conclusion:** HPD is required above 85 dBA universally. CSA Z94.2 is the referenced standard in most jurisdictions. HPD type and selection documentation captured in the questionnaire record is appropriate for core.

---

### 3.6 Record Retention

| Jurisdiction | Retention Requirement |
|---|---|
| Federal | Not specifically defined |
| British Columbia | Duration of employment + 10 years |
| Alberta | **As long as employer operates** |
| Saskatchewan | Not specifically defined |
| Manitoba | Not specifically defined |
| Ontario | Not specifically defined |
| Quebec | Not specifically defined |
| New Brunswick | Not specifically defined |
| Nova Scotia | Not specifically defined |
| Prince Edward Island | Not specifically defined |
| Newfoundland & Labrador | Duration of employment + 10 years |
| Northwest Territories | Not specifically defined |
| Nunavut | Not specifically defined |
| Yukon | Not specifically defined |

> **CADS Core conclusion:** Record retention is not uniformly defined. BC and NL have the most specific requirements. Alberta's requirement (as long as employer operates) is uniquely open-ended. Retention period becomes a provincial profile field. CADS recommends a minimum of 10 years as best practice regardless of jurisdiction.

---

### 3.7 Language Requirements

| Jurisdiction | Primary Language | Secondary Language |
|---|---|---|
| Federal | English | French (bilingual) |
| British Columbia | English | — |
| Alberta | English | — |
| Saskatchewan | English | — |
| Manitoba | English | French |
| Ontario | English | French |
| Quebec | **French** | English |
| New Brunswick | English | **French (bilingual province)** |
| Nova Scotia | English | — |
| Prince Edward Island | English | — |
| Newfoundland & Labrador | English | — |
| Northwest Territories | English | French + Indigenous languages |
| Nunavut | English | Inuktitut + Inuinnaqtun |
| Yukon | English | French |

> **CADS Core conclusion:** Language is a provincial profile field. Quebec requires French as the primary language. New Brunswick is bilingual. The Federal jurisdiction and Manitoba/Ontario require bilingual capability. French-language support is essential for full national deployment.

---

## 4. What Belongs in the CADS Core Standard

Based on the complete national comparison, the following elements are universal across all Canadian jurisdictions where audiometric testing occurs. These belong in the CADS Core Standard and do not vary by province.

**4.1 Audiometric Test Data**
- Test types: baseline, periodic, exit, retest
- Audiometric frequencies: 500, 1000, 2000, 3000, 4000, 6000, 8000 Hz
- Threshold values in dB HL per frequency per ear
- Test method (manual, microprocessor, automated)

**4.2 Standard Threshold Shift Calculation**
- Definition: 10 dB average shift at 2000, 3000, and 4000 Hz in either ear
- Age correction methodology (NIOSH 1998 reference tables)
- Baseline comparison rules
- Outcome classification

**4.3 Pre-Test Conditions**
- Recent noise exposure documentation
- Quiet period estimation

**4.4 Equipment Identification**
- Audiometer make, model, serial number
- Calibration status (biological and acoustic)
- Audiometer type

**4.5 Technician and Provider Identification**
- Credential type and certification number
- Province of certification

**4.6 Worker Record**
- Anonymized unique identifier
- Date of birth (for age correction)
- Sex (for normative data)
- NOC 2021 occupational code
- Province of employment

**4.7 Pre-Test Questionnaire**
- Occupational noise history
- Non-occupational noise exposure (type, frequency, HPD use)
- Hearing protection practices
- Medical history relevant to hearing

**4.8 Record Metadata**
- CADS version
- Province code
- Record UUID
- Timestamps

**4.9 Outcome and Follow-Up**
- Outcome classification
- Referral type
- Follow-up interval

---

## 5. What Belongs in Provincial Profiles

The following elements vary between jurisdictions and belong in province-specific configuration profiles rather than the core standard.

| Configuration Field | Type | Notes |
|---|---|---|
| `province_code` | string | ISO 3166-2 CA |
| `regulatory_authority` | string | Name of regulator |
| `regulation_reference` | string | Specific regulation citation |
| `exposure_limit_dba` | integer | 85 for most; 87 for Federal |
| `action_level_dba` | integer | Varies 80–84 dBA |
| `hcp_required` | boolean | Not required in 5 jurisdictions |
| `hcp_worker_threshold` | integer | SK=10, NWT/NU=20, others=0 |
| `audiometric_testing_required` | boolean | Not required in 4 jurisdictions |
| `testing_trigger_dba` | integer | Yukon=80, others=85 |
| `baseline_months` | integer | NL=3, others=6 |
| `testing_frequency` | enum | annual / biennial |
| `exit_test_required` | boolean | BC only |
| `hcp_selection_documentation_required` | boolean | BC only |
| `retention_years_minimum` | integer | 10 recommended; AB indefinite |
| `language` | enum | en / fr / bilingual |
| `api_endpoint` | string | Provincial system endpoint |
| `billing_webhook` | string | CADS billing event endpoint |

---

## 6. Jurisdiction Reference Cards

### Federal
- **Authority:** Employment and Social Development Canada
- **Regulation:** Canada OHS Regulations Part VII
- **Exposure Limit:** 87 dBA (unique — higher than all provinces)
- **HCP Required:** No specific requirement
- **Audiometric Testing:** No specific requirement
- **Language:** Bilingual (English/French)
- **Notes:** Federal jurisdiction covers federally regulated industries (banking, telecommunications, inter-provincial transport, aviation). Employees in these industries are covered by federal rather than provincial OHS law.

---

### British Columbia
- **Authority:** WorkSafeBC
- **Regulation:** OHS Regulation Part 7, Sections 7.2–7.9
- **Exposure Limit:** 85 dBA Lex, 140 dBC peak
- **Action Level:** 82 dBA
- **HCP Required:** Yes — above 85 dBA Lex or 140 dBC peak
- **Audiometric Testing:** Yes — baseline within 6 months, annual thereafter
- **Exit Test:** Required
- **HPD Documentation:** Required
- **Language:** English
- **Notes:** Most comprehensive hearing conservation regulation in Canada. Serves as the benchmark for the CADS Core Standard.

---

### Alberta
- **Authority:** Alberta OHS
- **Regulation:** OHS Code Part 16, Sections 218–224
- **Exposure Limit:** 85 dBA, 140 dBC peak
- **Action Level:** 82 dBA
- **HCP Required:** Yes — written noise management program
- **Audiometric Testing:** Yes — baseline within 6 months, second at 12 months, biennial thereafter
- **Exit Test:** Recommended
- **Record Retention:** Duration of employer operations (indefinite)
- **Language:** English
- **Notes:** Biennial testing after the first year is a meaningful difference from BC's annual requirement.

---

### Saskatchewan
- **Authority:** Saskatchewan OHS
- **Regulation:** OHS Regulations 2020, Part 8, Sections 111–114
- **Exposure Limit:** 85 dBA Lex
- **Action Level:** 80 dBA
- **HCP Required:** Yes — if 10 or more workers exposed above 85 dBA Lex. Program must be reviewed every 3 years.
- **Audiometric Testing:** Yes — biennial for workers exposed above 85 dBA Lex
- **Exit Test:** Recommended
- **Language:** English
- **Notes:** 10-worker threshold for HCP is unique. Small employers with fewer than 10 exposed workers have no specific HCP requirement.

---

### Manitoba
- **Authority:** Manitoba Workplace Safety and Health
- **Regulation:** WSH Regulation Part 12, Sections 12.1–12.8
- **Exposure Limit:** 85 dBA Lex
- **Action Level:** 80 dBA
- **HCP Required:** No specific requirement
- **Audiometric Testing:** Yes — baseline within 6 months, biennial thereafter
- **Exit Test:** Not specified
- **Language:** English/French
- **Notes:** Manitoba requires audiometric testing but not a specific HCP. This is an unusual combination — testing requirements exist without a program framework requirement.

---

### Ontario
- **Authority:** Ontario Ministry of Labour
- **Regulation:** O. Reg. 381/15 (Noise)
- **Exposure Limit:** 85 dBA Lex
- **Action Level:** Not specified
- **HCP Required:** No specific requirement
- **Audiometric Testing:** No specific requirement
- **Exit Test:** Not applicable
- **Language:** English/French
- **Notes:** Canada's largest industrial province has the least specific hearing conservation requirements. General duty of care applies. CADS implementation in Ontario represents best practice documentation beyond the regulatory minimum — a strong due diligence argument.

---

### Quebec
- **Authority:** CNESST
- **Regulation:** Regulation respecting OHS, Division XV, Sections 130–141.5
- **Exposure Limit:** 85 dBA, 140 dB peak
- **Action Level:** Not specified
- **HCP Required:** No specific requirement
- **Audiometric Testing:** ⚠️ Requires verification — conflicting sources
- **Exit Test:** Not specified
- **Language:** **French primary** — English secondary
- **Notes:** Unique regulatory structure under CNESST. French-language interface is mandatory for Quebec deployment. Discrepancy between CCOHS and OHS Insider on audiometric testing requirement must be resolved through direct regulatory review.

---

### New Brunswick
- **Authority:** WorkSafeNB
- **Regulation:** OHS Act, General Regulations 91-191
- **Exposure Limit:** 85 dBA, 140 dBC peak
- **Action Level:** 80 dBA
- **HCP Required:** No specific requirement (code of practice required where noise exceeds PEL)
- **Audiometric Testing:** Required for underground mine workers. General requirement unconfirmed — requires verification.
- **Exit Test:** Not specified
- **Language:** English/French (bilingual province)
- **Notes:** WorkSafeNB publishes guidance on audiometric testing that suggests broader application than the regulations strictly require. Bilingual province — both official languages required.

---

### Nova Scotia
- **Authority:** Nova Scotia OHS
- **Regulation:** OHS Act
- **Exposure Limit:** 85 dBA
- **Action Level:** Not specified
- **HCP Required:** No specific requirement
- **Audiometric Testing:** No specific requirement
- **Exit Test:** Not applicable
- **Language:** English
- **Notes:** Along with Ontario, Nova Scotia has the least specific hearing conservation requirements in Canada. General duty of care applies.

---

### Prince Edward Island
- **Authority:** PEI Workers Compensation Board / OHS Division
- **Regulation:** OHS Act General Regulations, Part 8, Sections 8.4–8.10
- **Exposure Limit:** 85 dBA
- **Action Level:** Not specified
- **HCP Required:** Yes — written noise control and hearing conservation program
- **Audiometric Testing:** Yes — baseline within 6 months, annual thereafter
- **Exit Test:** Not specified
- **Language:** English
- **Notes:** PEI's requirements closely mirror BC's framework. Annual testing and written HCP required. Small industrial base but regulation is more complete than most Atlantic provinces.

---

### Newfoundland and Labrador
- **Authority:** Newfoundland and Labrador OHS
- **Regulation:** OHS Regulations 2012, Part VI, Section 68
- **Exposure Limit:** 85 dBA, 140 dBA peak
- **Action Level:** Not specified
- **HCP Required:** Yes — above 85 dBA
- **Audiometric Testing:** Yes — **baseline within 3 months**, annual thereafter
- **Exit Test:** Not specified
- **Worker Rights:** Workers may request noise exposure records after employment ends
- **Language:** English
- **Notes:** **The 3-month baseline requirement is unique in Canada.** All other jurisdictions specify 6 months. This becomes a specific NL profile configuration. Strong mining and offshore industrial base makes hearing conservation highly relevant.

---

### Northwest Territories & Nunavut
- **Authority:** NWT/Nunavut Workers' Safety and Compensation Commission
- **Regulation:** OHS Regulations, Part 8, Sections 114–117
- **Exposure Limit:** 85 dBA Lex
- **Action Level:** 80 dBA
- **HCP Required:** Yes — if **20 or more workers** exposed above 85 dBA Lex. Program reviewed every 3 years.
- **Audiometric Testing:** Yes — biennial for workers exposed above 85 dBA Lex
- **Exit Test:** Not specified
- **Language:** English; Inuktitut and Inuinnaqtun for Nunavut
- **Notes:** 20-worker threshold for HCP is the highest in Canada. Remote industrial sites (mining, resource extraction) are the primary context. Nunavut language requirements are unique and would require specialized consideration for full deployment.

---

### Yukon
- **Authority:** Yukon OHS
- **Regulation:** OHS Act, Occupational Health Regulations, Section 6
- **Exposure Limit:** 85 dBA, 140 dB peak
- **Action Level:** **80 dBA** (lower trigger for audiometric testing)
- **HCP Required:** No specific requirement
- **Audiometric Testing:** Yes — within 6 months, annual thereafter. **Triggered at 80 dBA** — lower than any other jurisdiction.
- **Exit Test:** Not specified
- **Language:** English/French
- **Notes:** Yukon has the lowest audiometric testing trigger in Canada (80 dBA vs 85 dBA elsewhere). No specific HCP requirement despite this. Remote mining and resource extraction industries are the primary context.

---

## 7. Verification Checklist

The following items require direct regulatory verification before provincial profiles are finalized:

- [ ] **Quebec audiometric testing requirement** — resolve discrepancy between CCOHS (required above OEL) and OHS Insider (not specifically required). Review CNESST Regulation Division XV Section 136 directly.
- [ ] **New Brunswick general audiometric testing** — confirm whether General Regulations 91-191 Part V applies broadly or only to underground mines. Review WorkSafeNB guidance against regulation text.
- [ ] **STS definition for Quebec** — confirm STS definition and whether age correction is addressed in regulation.
- [ ] **Saskatchewan baseline timing** — confirm whether baseline timing is specified in OHS Regulations 2020 Part 8.
- [ ] **NWT/Nunavut STS definition** — confirm STS definition in Part 8 Sections 116–117.
- [ ] **Alberta exit testing** — confirm recommended vs. required status.
- [ ] **Newfoundland 3-month baseline** — verify against OHS Regulations 2012 Part VI Section 68(3) directly.
- [ ] **Federal STS definition** — confirm whether any STS definition exists in federal OHS regulations.
- [ ] **Manitoba language requirements** — confirm French-language interface requirement for Manitoba deployment.
- [ ] **Nunavut language requirements** — confirm which Indigenous languages are required and in what context.

---

*CADS/Standard — Provincial Regulatory Comparison v0.2*
*Research draft — for internal use pending regulatory verification*
*© AudioPilot — Not for distribution*
