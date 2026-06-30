# Canadian Audiometric Data System
## CADS
### Vision & Platform Overview
**Version 1.1 — June 2026**

*An AudioPilot initiative*

---

## Naming and Disambiguation

**AudioPilot** is the organization that owns, maintains, and develops the CADS initiative.

**CADS/Standard** — the Canadian Audiometric Data Standard. An open specification for industrial audiometric data capture, exchange, and analysis. Any system, developer, or organization may implement the standard. Provinces, hearing conservation programs, and software developers adhere to it.

**CADS/System** — the infrastructure for adoption, development, and governance of the CADS/Standard. Architecture requirements, provincial profiles, data residency rules, and billing models are defined here.

**CADS/App** — the integrated software application built by AudioPilot. The reference implementation of CADS/Standard running on CADS/System infrastructure. CADS/App consists of five integrated interfaces, each serving a distinct stakeholder.

Where context requires disambiguation, CADS/Standard, CADS/System, and CADS/App are used explicitly. CADS alone refers to the initiative as a whole.

---

## Table of Contents

- [Vision](#vision)
- [The Problem](#the-problem)
  - [Hearing Loss Is Canada's Most Underreported Occupational Injury](#hearing-loss-is-canadas-most-underreported-occupational-injury)
  - [The System Is Fragmented](#the-system-is-fragmented)
  - [The Compliance Gap](#the-compliance-gap)
- [The Canadian Audiometric Data Standard](#the-canadian-audiometric-data-standard-cadsstandard)
  - [What the Standard Defines](#what-the-standard-defines)
  - [Why the NOC Integration Matters](#why-the-noc-integration-matters)
  - [Versioning and Governance](#versioning-and-governance)
- [CADS/App](#cadsapp)
  - [CADS Field — Field Technician Application](#cads-field--field-technician-application)
  - [CADS Admin — Hearing Test Company Management](#cads-admin--hearing-test-company-management)
  - [CADS Employer — HCP Management for Industrial Employers](#cads-employer--hcp-management-for-industrial-employers)
  - [CADS Province — Regulator Intelligence Platform](#cads-province--regulator-intelligence-platform)
  - [CADS Worker — Pre-Test Questionnaire](#cads-worker--pre-test-questionnaire)
- [Who Benefits and How](#who-benefits-and-how)
- [Time and Cost Savings](#time-and-cost-savings)
- [Business Model](#business-model)
- [Path to National Deployment](#path-to-national-deployment)
- [Repository Structure](#repository-structure)
- [About AudioPilot](#about-audiopilot)
- [Contact](#contact)

---

## Vision

Workplace hearing loss is preventable. Yet it remains one of the most common occupational injuries in Canada — not because the science is unclear, but because the systems supporting hearing conservation are fragmented, inconsistent, and difficult to use.

**CADS exists to change that.**

For the field technician — the best tool available, built by someone who does the work.

For the employer — a clear, guided path to genuine compliance, not just paperwork compliance.

For the province — real population-level data on occupational hearing health, for the first time.

For the worker — a hearing conservation program that actually works.

The result: fewer noise-induced hearing loss claims, lower costs across the system, and a national standard that every province can stand behind.

---

## The Problem

### Hearing Loss Is Canada's Most Underreported Occupational Injury

Noise-induced hearing loss (NIHL) develops slowly and silently. By the time a worker notices it, the damage is permanent and irreversible. Canada's industrial workforce — miners, millwrights, heavy equipment operators, oil and gas workers — faces daily noise exposure levels that make hearing loss an occupational certainty without effective prevention programs.

### The System Is Fragmented

Hearing conservation in Canada today looks like this:

- 50–75 mobile hearing test companies operating independently across the country
- Each using different software, different data formats, different reporting standards
- Employers maintaining paper-based or spreadsheet HCP records with no standardization
- Provinces receiving no aggregate data — no visibility into trends, compliance rates, or outcomes
- Workers falling through the cracks when threshold shifts go untracked across job changes

### The Compliance Gap

Provincial regulations require employers to maintain Hearing Conservation Programs, conduct regular audiometric testing, and take action when significant threshold shifts occur. In practice, compliance is inconsistent. Employers find the requirements complex, documentation burdensome, and the consequences of non-compliance abstract until a WorkSafeBC inspection or a compensation claim makes it real.

No province currently has the data infrastructure to know whether hearing conservation programs are actually working.

---

## The Canadian Audiometric Data Standard (CADS/Standard)

CADS/Standard defines the national data exchange format for industrial audiometric testing. It is an open specification — any platform, developer, or organization may implement it. It was designed from the ground up by a working Industrial Audiometric Technician with deep knowledge of Canadian occupational health regulations across multiple provinces.

The standard applies whenever industrial audiometric testing is conducted in Canada — whether mandated by provincial regulation or conducted as best practice under employer duty of care. It makes no determination about when testing is required. It governs how data is captured when testing occurs.

### What the Standard Defines

- Worker record fields (anonymized identifiers, demographics, exposure group)
- Audiometric test results (frequencies, thresholds, test method, per ear)
- Compliance calculations (Standard Threshold Shift methodology, age correction, baseline comparison)
- Equipment and calibration records (audiometer identification, calibration dates)
- Technician and provider identification (credential type, certification number, province)
- Pre-test conditions and questionnaire responses
- Outcome classifications and referral flags
- Occupational codes using the federal National Occupational Classification (NOC 2021)
- Record metadata (CADS version, province code, submission timestamp, UUID)

### Why the NOC Integration Matters

By tying every test record to a standardized federal occupational code, CADS/Standard enables something that has never existed in Canada: cross-provincial hearing health analysis by occupation. Which NOC codes are producing the highest rates of Significant Threshold Shift? Which industries are systematically underprotected? Which employers have effective programs and which do not? CADS/Standard answers these questions at population scale.

### Versioning and Governance

The standard is versioned from day one (CADS/Standard v1.0). Province-specific requirements are accommodated through configuration extensions without modifying the core standard. As regulations evolve, the standard evolves in a controlled, backward-compatible way. AudioPilot maintains the standard and its provincial profiles.

---

## CADS/App

CADS/App is the integrated software application built by AudioPilot — the reference implementation of CADS/Standard. It consists of five purpose-built interfaces, each serving a different stakeholder in the hearing conservation ecosystem.

| CADS Field | CADS Admin | CADS Employer | CADS Province | CADS Worker |
|---|---|---|---|---|
| Field Technician | Hearing Test Company | Industrial Employer | Provincial Regulator | Worker |

### CADS Field — Field Technician Application

CADS Field is an offline-first Progressive Web App designed for use by Industrial Audiometric Technicians on industrial sites. It requires no internet connection during testing and syncs automatically when connectivity is available. CADS Field handles the complete audiometric testing workflow including pre-test questionnaire review, otoscopy recording, audiogram capture, STS calculation, and report generation.

- Works offline on any device — no app store, no installation
- Packet-based architecture: one packet per employer site, self-contained and resilient
- Province-specific compliance logic built in
- Syncs to CADS/System when online via configurable sync adapter

### CADS Admin — Hearing Test Company Management

CADS Admin is the administrative interface for hearing test companies — the businesses that employ technicians and provide audiometric services to industrial clients. It handles technician management, client roster, incoming packet processing, report generation, equipment calibration tracking, and billing reporting.

- Multi-technician management with credential tracking
- Incoming field data review and quality control
- Client and site management
- Automated compliance report generation

### CADS Employer — HCP Management for Industrial Employers

CADS Employer gives industrial employers — the companies with noise-exposed workers — a purpose-built tool for managing their entire Hearing Conservation Program from within the provincial web portal.

- **Guided HCP Builder:** step-by-step wizard to create a compliant written Hearing Conservation Program, pre-populated with province-specific regulatory requirements
- Worker roster management with noise exposure group assignments
- Real-time testing status: who is current, who is due, who is overdue
- STS tracking and referral management — no worker falls through the cracks
- HPD management and adequacy records
- Training records and compliance documentation
- Audit-ready compliance package exportable at any time
- Automated notifications for upcoming testing deadlines, STS follow-ups, and calibration expiries

Accountability is built in. When a threshold shift is flagged and the employer is notified through the portal, there is a timestamped record of that notification. Employers cannot claim they were unaware.

### CADS Province — Regulator Intelligence Platform

CADS Province gives occupational health regulators something they have never had: real-time, population-level intelligence on hearing conservation outcomes across their entire jurisdiction.

- Real-time compliance rates by company, industry, and region
- STS trend analysis by NOC occupational code
- Companies flagged for compliance concerns
- Province-wide hearing health indicators over time
- Exportable reports for ministerial briefings and policy development
- Cross-industry benchmarking

This is not a data portal. It is an occupational health intelligence platform — hosted and designed by AudioPilot, not built by a provincial IT department.

### CADS Worker — Pre-Test Questionnaire

CADS Worker is a smartphone-optimized Progressive Web App that allows workers to complete the CADS/Standard pre-test questionnaire before arriving at the mobile clinic.

- Accessed via a unique link or QR code — no account creation or password required
- Works on any smartphone browser, no app download required
- Available in English and French
- Large touch targets and plain language — designed for the industrial worker
- Estimated completion time: 2–3 minutes

The employer distributes the link or QR code to workers before testing day. When workers arrive at the mobile clinic, their questionnaire is already complete. The technician reviews answers, confirms the quiet period, performs otoscopy, and proceeds directly to testing.

**Time savings across a 50-worker testing day: 2–3 hours of recovered testing capacity.**

---

## Who Benefits and How

| Stakeholder | What CADS Delivers |
|---|---|
| **Field Technician** | Best-in-class offline tool built by a working IAT. Faster workflow, less paperwork, fewer errors, more tests per day. |
| **Hearing Test Company** | Competitive advantage, efficient multi-technician management, automated reporting, and a platform that grows with the business. |
| **Industrial Employer** | Genuine compliance made simple. Guided HCP creation, real-time worker status, automated notifications, and an audit-ready paper trail. |
| **Provincial Regulator** | Population-level hearing health intelligence for the first time. Data-driven policy, real compliance visibility, and employer accountability built in. |
| **Worker** | A hearing conservation program that actually tracks their health over time, flags changes early, ensures referrals when needed, and provides documented evidence for compensation claims. |

---

## Time and Cost Savings

### For Field Technicians
- Offline-first design eliminates connectivity workarounds and data entry duplication
- Automated STS calculations remove manual computation errors
- Packet-based workflow reduces setup time between sites
- CADS Worker pre-completion recovers 2–3 hours of testing capacity per 50-worker day
- Faster testing throughput means more tests per day at the same quality

### For Hearing Test Companies
- Automated compliance reporting eliminates hours of manual document preparation
- Centralized technician and client management reduces administrative overhead
- Standardized data format eliminates custom integration work for each client

### For Employers
- Guided HCP Builder replaces expensive consultant-drafted programs
- Automated testing reminders eliminate missed compliance deadlines
- Digital audit trail replaces paper-based record management
- Early STS intervention reduces long-term compensation claim costs
- CADS Worker reduces time workers spend away from their stations on testing day

### For Provinces
- Standardized data ingestion eliminates manual data collection from hearing test companies
- Real-time compliance visibility reduces inspection overhead
- Population-level trend data supports evidence-based regulatory policy
- Reduced administrative burden across the entire hearing conservation system

---

## Business Model

CADS/App operates on a per-test pricing model. The province provides hosting infrastructure. AudioPilot provides the complete CADS/App stack and charges per audiometric test processed through the system.

> **$1.50 per test**
> Province provides hosting. AudioPilot provides the engine.

### Why Per-Test Pricing Works

- Aligns revenue with actual usage — the province pays for what it gets
- Easy to budget: provinces estimate volume from prior year data
- Scales naturally as the workforce grows
- Low enough per unit to be invisible in the cost of a hearing conservation program
- High enough at population scale to sustain a world-class platform

### Alberta Illustrative Projection

Assuming 15 hearing test companies, 5 technicians each, 150–180 testing days per year, 30–50 tests per day:

| Scenario | Annual Tests | Annual Revenue |
|---|---|---|
| Conservative | 337,500 | $506,250 |
| Mid-range | 540,000 | $810,000 |
| High | 675,000 | $1,012,500 |

Alberta is one province. BC, Saskatchewan, Ontario, Quebec, and the Atlantic provinces represent additional contracts of comparable or greater scale.

---

## Path to National Deployment

### Phase 1 — Field Proven (Current)
- CADS Field deployed in BC and Saskatchewan
- Real-world audiometric data validating the platform under field conditions
- CADS/Standard defined and documented

### Phase 2 — Commercial Launch
- Multi-tenant architecture supporting multiple hearing test companies
- CADS Admin and CADS Employer complete
- BC and Alberta regulatory modules certified
- First commercial customers signed

### Phase 3 — Provincial Contract
- CADS Province and CADS Worker complete
- Per-test billing infrastructure operational
- First provincial contract signed (target: Alberta or BC)
- Provincial hosting established on Canadian infrastructure

### Phase 4 — National Expansion
- Saskatchewan, Ontario, and Atlantic provincial modules
- Quebec French-language interface and regulatory module
- CADS/Standard adopted as the de facto national standard
- Dedicated support and development staff hired

---

## Repository Structure

```
/README.md                          ← Vision & platform overview (this document)
/standard/
    CADS-v1.0.md                    ← The formal CADS/Standard specification
    questionnaire.md                ← Standardized pre-test questionnaire
/provincial/
    BC.md                           ← British Columbia regulatory profile
    AB.md                           ← Alberta regulatory profile
    SK.md                           ← Saskatchewan regulatory profile
/docs/
    architecture.md                 ← CADS/System architecture guidance
    data-model.md                   ← CADS/Standard data model reference
    provincial-comparison.md        ← BC, AB, SK and national regulatory comparison
```

---

## About AudioPilot

AudioPilot is the organization behind the CADS initiative. CADS/Standard was conceived and developed by a working Industrial Audiometric Technician with direct field experience conducting hearing conservation programs at industrial sites across British Columbia and Alberta.

The standard was not designed by a software company that researched the problem. It was designed by someone who lives it.

That distinction matters. The regulatory logic is correct because the author knows the regulations. The workflow is efficient because the author has done the work. CADS Employer exists because the author has seen what happens when employers lack proper tools. CADS Worker exists because the author has stood at a mobile clinic with 50 workers in line and understood exactly where the time goes.

---

## Contact

For inquiries regarding CADS/Standard, CADS/App, provincial partnerships, or HCP consulting services:

**GitHub:** [github.com/RoadPilotAI/cads](https://github.com/RoadPilotAI/cads)

> *Note: The GitHub organization will migrate to AudioPilot upon incorporation. The repository URL will be updated at that time.*

---

*CADS is built by practitioners. For everyone.*

*Canadian Audiometric Data Standard • Canadian Audiometric Data System • AudioPilot*
