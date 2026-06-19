# CADS Provincial Regulatory Comparison Framework
## Hearing Conservation Requirements: BC, AB, and SK
**Draft v0.1 — June 2026**

---

## Purpose

This document compares industrial hearing conservation regulatory requirements across British Columbia, Alberta, and Saskatchewan. It serves as the foundation for CADS province-specific configuration modules and demonstrates that a single, unified standard can satisfy all three jurisdictions with minimal variation.

The practical takeaway: **the differences are manageable. The common ground is substantial.**

---

## Regulatory Authority by Province

| Element | British Columbia | Alberta | Saskatchewan |
|---|---|---|---|
| **Authority** | WorkSafeBC | Alberta OHS | Saskatchewan OHS |
| **Regulation** | OHS Regulation Part 7 | OHS Code Part 16 | OHS Regulations Part 7 |
| **Considered** | Most stringent in Canada | Employer-friendly framework | Similar to Alberta |

---

## Comparison Matrix

### 1. Noise Exposure Limits

| Element | BC | AB | SK | CADS Approach |
|---|---|---|---|---|
| Action Level (TWA) | 82 dBA | 82 dBA | 82 dBA | Identical — single value |
| Exposure Limit (TWA) | 85 dBA | 85 dBA | 85 dBA | Identical — single value |
| Exchange Rate | 3 dB | 3 dB | 3 dB | Identical |
| Peak Exposure Limit | 140 dBP | 140 dBP | 140 dBP | Identical |

> **CADS note:** Noise exposure limits are effectively identical across all three provinces. No province-specific configuration required for this element.

---

### 2. When a Hearing Conservation Program Is Required

| Trigger | BC | AB | SK | CADS Approach |
|---|---|---|---|---|
| Worker exposed at or above action level | ✓ | ✓ | ✓ | Identical trigger |
| Written HCP required | ✓ | ✓ | ✓ | Identical requirement |
| HCP must be site-specific | ✓ | ✓ | ✓ | Identical |

> **CADS note:** The trigger for a mandatory HCP is consistent. The Employer Portal HCP Builder applies uniformly.

---

### 3. Audiometric Testing Requirements

| Element | BC | AB | SK | CADS Approach |
|---|---|---|---|---|
| Baseline test required | ✓ | ✓ | ✓ | Identical |
| Baseline timing | Prior to or within 6 months of first exposure | Prior to or within 6 months | Prior to or within 6 months | Identical |
| Periodic testing frequency | Annual | Annual | Annual | Identical |
| Exit testing | ✓ Required | Recommended | Recommended | BC = required flag in config |
| Qualified tester required | ✓ IAT or physician | ✓ IAT or physician | ✓ IAT or physician | Identical |
| Audiometer calibration required | ✓ | ✓ | ✓ | Identical |

> **CADS note:** Exit testing is the primary difference. BC config sets exit test as required. AB/SK config sets it as recommended with an optional flag. Minor configuration difference, not a structural one.

---

### 4. Standard Threshold Shift (STS) Definition

| Element | BC | AB | SK | CADS Approach |
|---|---|---|---|---|
| STS definition | 10 dB average shift at 2000, 3000, 4000 Hz | 10 dB average shift at 2000, 3000, 4000 Hz | 10 dB average shift at 2000, 3000, 4000 Hz | Identical |
| Age correction permitted | ✓ | ✓ | ✓ | Identical |
| Comparison to baseline | ✓ | ✓ | ✓ | Identical |
| STS triggers follow-up | ✓ | ✓ | ✓ | Identical |
| STS triggers referral | ✓ | ✓ | ✓ | Identical |

> **CADS note:** STS methodology is identical across all three provinces. Core calculation engine requires no province-specific variation.

---

### 5. Pre-Test Questionnaire

| Element | BC | AB | SK | CADS Approach |
|---|---|---|---|---|
| Questionnaire required | ✓ | ✓ | ✓ | Identical requirement |
| Quiet period prior to test | 14 hours recommended | 14 hours recommended | 14 hours recommended | Identical |
| Non-occupational noise history | ✓ | ✓ | ✓ | Identical |
| Medical history | ✓ | ✓ | ✓ | Identical |
| HPD use history | ✓ | ✓ | ✓ | Identical |
| Standardized format required | Not specified | Not specified | Not specified | CADS provides the standard |

> **CADS note:** All three provinces require a questionnaire but none mandate a specific format. This is the gap CADS fills. A single standardized questionnaire satisfies all three jurisdictions and improves data quality across the board.

---

### 6. Noise Assessment Requirements

| Element | BC | AB | SK | CADS Approach |
|---|---|---|---|---|
| Noise assessment required | ✓ When exposure suspected | ✓ When exposure suspected | ✓ When exposure suspected | Identical trigger |
| Qualified assessor required | ✓ | ✓ | ✓ | Identical |
| Written assessment required | ✓ | ✓ | ✓ | Identical |
| Reassessment on process change | ✓ | ✓ | ✓ | Identical |
| TWA measurement method | Dosimetry or area monitoring | Dosimetry or area monitoring | Dosimetry or area monitoring | Identical |

> **CADS note:** Noise assessment requirements are consistent. CADS records reference the assessment but does not replace it.

---

### 7. Hearing Protection Devices (HPD)

| Element | BC | AB | SK | CADS Approach |
|---|---|---|---|---|
| HPD required at action level | ✓ | ✓ | ✓ | Identical |
| HPD required at exposure limit | ✓ Mandatory | ✓ Mandatory | ✓ Mandatory | Identical |
| HPD adequacy assessment | ✓ | ✓ | ✓ | Identical |
| Training on HPD use | ✓ | ✓ | ✓ | Identical |
| HPD selection documented | ✓ | Recommended | Recommended | BC = required flag in config |

> **CADS note:** HPD selection documentation is required in BC, recommended in AB/SK. Minor config flag difference.

---

### 8. HCP Documentation Requirements

| Element | BC | AB | SK | CADS Approach |
|---|---|---|---|---|
| Written HCP required | ✓ | ✓ | ✓ | Identical |
| Worker education/training | ✓ | ✓ | ✓ | Identical |
| Record retention | 10 years or duration of employment + 10 years | Duration of employment + 10 years | Duration of employment + 10 years | BC config = stricter retention flag |
| Records accessible to workers | ✓ | ✓ | ✓ | Identical |
| Annual program review | ✓ | ✓ | ✓ | Identical |

> **CADS note:** Record retention has a minor BC regulatory requirement. Configurable in the data layer. No structural difference.

---

### 9. Worker Rights

| Element | BC | AB | SK | CADS Approach |
|---|---|---|---|---|
| Worker right to test results | ✓ | ✓ | ✓ | Identical |
| Employer must act on STS | ✓ | ✓ | ✓ | Identical |
| Confidentiality of records | ✓ | ✓ | ✓ | Identical |
| Worker must be informed of STS | ✓ | ✓ | ✓ | Identical |

> **CADS note:** Worker rights are consistent across all three provinces.

---

## Summary: Where Provinces Differ

The differences between BC, AB, and SK hearing conservation requirements reduce to three minor configuration flags:

| Difference | BC | AB/SK | Config Solution |
|---|---|---|---|
| Exit audiogram | Required | Recommended | Boolean flag: `exit_test_required` |
| HPD selection documentation | Required | Recommended | Boolean flag: `hpd_selection_required` |
| Record retention | 10 years + employment | Employment + 10 years | Integer field: `retention_years_minimum` |

**That's it.** Three configuration flags cover the meaningful regulatory differences between Canada's three westernmost provinces.

---

## What CADS Standardizes That No Province Mandates

These elements are required by none of the three provinces in a standardized format, yet all would improve hearing conservation outcomes. CADS implements them universally:

- **Standardized pre-test questionnaire** — consistent data across all providers
- **NOC occupational code** — enables cross-provincial population analysis
- **Equipment firmware version** — supports technical audit trails
- **Bilateral audiogram display** — standardized visual format
- **STS trend tracking** — longitudinal analysis across baseline changes
- **HPD adequacy screening flag** — value-added data point

---

## Implications for CADS Architecture

The provincial regulatory comparison confirms the core architectural decision: **one engine, province-specific configuration.**

A single CADS platform satisfies BC, AB, and SK with a JSON configuration file per province. The regulatory logic, the STS calculation, the questionnaire, and the data standard are identical. The configuration file sets the province-specific flags.

Adding a new province is:
1. Review their regulations against this framework
2. Identify any new configuration flags required
3. Write the province config file
4. Test against the regulatory requirements
5. Deploy

This is a measured, repeatable process — not a rebuild.

---

## Next Steps

- [ ] Add Ontario comparison column
- [ ] Add Quebec comparison column (including French-language requirement)
- [ ] Add Atlantic provinces summary
- [ ] Review with regulatory references cited
- [ ] Legal review of regulatory interpretations
- [ ] Publish as CADS Standard supporting document

---

*Canadian Audiometric Data Standard (CADS) — RoadPilotAI*
*Draft for internal review — not for distribution*
