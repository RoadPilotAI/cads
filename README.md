# Canadian Audiometric Data System
## CADS
### Vision & Platform Overview
**Version 1.0 — June 2026**

*Implementing the Canadian Audiometric Data Standard*
*A national platform for hearing conservation data — built by practitioners, for everyone.*

---

## Table of Contents

- [Vision](#vision)
- [The Problem](#the-problem)
  - [Hearing Loss Is Canada's Most Underreported Occupational Injury](#hearing-loss-is-canadas-most-underreported-occupational-injury)
  - [The System Is Fragmented](#the-system-is-fragmented)
  - [The Compliance Gap](#the-compliance-gap)
- [The Canadian Audiometric Data Standard](#the-canadian-audiometric-data-standard-cads)
  - [What the Standard Defines](#what-the-standard-defines)
  - [Why the NOC Integration Matters](#why-the-noc-integration-matters)
  - [Versioning and Governance](#versioning-and-governance)
- [The CADS Platform](#the-cads-platform)
  - [TechTool — The Field Application](#techtool--the-field-application)
  - [Company Admin — Hearing Test Company Management](#company-admin--hearing-test-company-management)
  - [Employer Portal — HCP Management for Industrial Employers](#employer-portal--hcp-management-for-industrial-employers)
  - [Provincial Dashboard — Regulator Intelligence Platform](#provincial-dashboard--regulator-intelligence-platform)
- [Who Benefits and How](#who-benefits-and-how)
- [Time and Cost Savings](#time-and-cost-savings)
- [Business Model](#business-model)
- [Path to National Deployment](#path-to-national-deployment)
- [Repository Structure](#repository-structure)
- [About CADS](#about-cads)
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

## The Canadian Audiometric Data Standard (CADS)

CADS defines the national data exchange format for industrial audiometric testing. It is an open specification — any platform could theoretically implement it — but it was designed from the ground up by a working Industrial Audiometric Technician with deep knowledge of Canadian occupational health regulations across multiple provinces.

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

By tying every test record to a standardized federal occupational code, CADS enables something that has never existed in Canada: cross-provincial hearing health analysis by occupation. Which NOC codes are producing the highest rates of Significant Threshold Shift? Which industries are systematically underprotected? Which employers have effective programs and which do not? CADS answers these questions at population scale.

### Versioning and Governance

The standard is versioned from day one (CADS v1.0). Province-specific requirements are accommodated through configuration extensions without breaking the core standard. As regulations evolve, the standard evolves in a controlled, backward-compatible way.

---

## The CADS Platform

The Canadian Audiometric Data System is the reference implementation of the CADS standard. It is a purpose-built platform with four distinct interfaces, each serving a different stakeholder in the hearing conservation ecosystem.

| TechTool | Company Admin | Employer Portal | Provincial Dashboard |
|---|---|---|---|
| Field Technician | Hearing Test Company | Industrial Employer | Provincial Regulator |

### TechTool — The Field Application

TechTool is an offline-first Progressive Web App designed for use by Industrial Audiometric Technicians on industrial sites. It requires no internet connection during testing and syncs automatically when connectivity is available. TechTool handles the complete audiometric testing workflow including pre-test questionnaire, otoscopy recording, audiogram capture, STS calculation, and report generation.

- Works offline on any device — no app store, no installation
- Packet-based architecture: one packet per employer site, self-contained and resilient
- Province-specific compliance logic built in
- Syncs to the CADS platform when online via configurable sync adapter

### Company Admin — Hearing Test Company Management

Company Admin is the administrative interface for hearing test companies — the businesses that employ technicians and provide audiometric services to industrial clients. It handles technician management, client roster, incoming packet processing, report generation, equipment calibration tracking, and billing reporting.

- Multi-technician management with credential tracking
- Incoming field data review and quality control
- Client and site management
- Automated compliance report generation

### Employer Portal — HCP Management for Industrial Employers

The Employer Portal is the most significant innovation in the CADS platform. It gives industrial employers — the companies with noise-exposed workers — a purpose-built tool for managing their entire Hearing Conservation Program from within the provincial web portal.

- **Guided HCP Builder:** step-by-step wizard to create a compliant written Hearing Conservation Program, pre-populated with province-specific regulatory requirements
- Worker roster management with noise exposure group assignments
- Real-time testing status: who is current, who is due, who is overdue
- STS tracking and referral management — no worker falls through the cracks
- HPD management and adequacy records
- Training records and compliance documentation
- Audit-ready compliance package exportable at any time
- Automated notifications for upcoming testing deadlines, STS follow-ups, and calibration expiries

Accountability is built in. When a threshold shift is flagged and the employer is notified through the portal, there is a timestamped record of that notification. Employers cannot claim they were unaware.

### Provincial Dashboard — Regulator Intelligence Platform

The Provincial Dashboard gives occupational health regulators something they have never had: real-time, population-level intelligence on hearing conservation outcomes across their entire jurisdiction.

- Real-time compliance rates by company, industry, and region
- STS trend analysis by NOC occupational code
- Companies flagged for compliance concerns
- Province-wide hearing health indicators over time
- Exportable reports for ministerial briefings and policy development
- Cross-industry benchmarking

This is not a data portal. It is an occupational health intelligence platform — hosted and designed by CADS, not built by a provincial IT department.

---

## Who Benefits and How

| Stakeholder | What CADS Delivers |
|---|---|
| **Field Technician** | Best-in-class offline tool built by a working IAT. Faster workflow, less paperwork, fewer errors, more tests per day. |
| **Hearing Test Company** | Competitive advantage, efficient multi-technician management, automated reporting, and a platform that grows with the business. |
| **Industrial Employer** | Genuine compliance made simple. Guided HCP creation, real-time worker status, automated notifications, and an audit-ready paper trail. |
| **Provincial Regulator** | Population-level hearing health intelligence for the first time. Data-driven policy, real compliance visibility, and employer accountability built in. |
| **Worker** | A hearing conservation program that actually tracks their health over time, flags changes early, and ensures they get the referrals they need. |

---

## Time and Cost Savings

### For Field Technicians
- Offline-first design eliminates connectivity workarounds and data entry duplication
- Automated STS calculations remove manual computation errors
- Packet-based workflow reduces setup time between sites
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

### For Provinces
- Standardized data ingestion eliminates manual data collection from hearing test companies
- Real-time compliance visibility reduces inspection overhead
- Population-level trend data supports evidence-based regulatory policy
- Reduced administrative burden across the entire hearing conservation system

---

## Business Model

CADS operates on a per-test pricing model. The province hosts the platform infrastructure. CADS provides the complete application stack — TechTool, Company Admin, Employer Portal, and Provincial Dashboard — and charges per audiometric test processed through the system.

> **$1.50 per test**
> Province hosts infrastructure. CADS provides the engine.

### Why Per-Test Pricing Works

- Aligns CADS revenue with actual usage — the province pays for what it gets
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
- TechTool deployed in BC and Saskatchewan with Connect Hearing
- Real-world audiometric data validating the platform under field conditions
- CADS standard defined and documented

### Phase 2 — Commercial Launch
- Multi-tenant architecture supporting multiple hearing test companies
- Company Admin and Employer Portal complete
- BC and Alberta regulatory modules certified
- First commercial customers signed

### Phase 3 — Provincial Contract
- Provincial Dashboard complete
- Per-test billing infrastructure operational
- First provincial contract signed (target: Alberta or BC)
- Provincial platform hosting established on Canadian infrastructure

### Phase 4 — National Expansion
- Saskatchewan, Ontario, and Atlantic provincial modules
- Quebec French-language interface and regulatory module
- CADS standard adopted as the de facto national standard
- Dedicated support and development staff hired

---

## Repository Structure

```
/README.md                          ← Vision & platform overview (this document)
/standard/
    CADS-v1.0.md                    ← The formal CADS data standard specification
    questionnaire.md                ← Standardized pre-test questionnaire
/provincial/
    BC.md                           ← British Columbia regulatory module
    AB.md                           ← Alberta regulatory module
    SK.md                           ← Saskatchewan regulatory module
/docs/
    architecture.md                 ← Platform architecture overview
    data-model.md                   ← CADS data schema reference
```

---

## About CADS

CADS was conceived and built by a working Industrial Audiometric Technician with direct field experience conducting hearing conservation programs at industrial sites across British Columbia and Alberta. The platform was not designed by a software company that researched the problem. It was designed by someone who lives it.

That distinction matters. The regulatory logic is correct because the author knows the regulations. The workflow is efficient because the author has done the work. The Employer Portal is complete because the author has seen what happens when employers lack proper tools. The Provincial Dashboard is powerful because the author understands what data regulators actually need.

---

## Contact

CADS is developed and maintained by **RoadPilotAI**.

For inquiries regarding the Canadian Audiometric Data Standard, platform development, provincial partnerships, or HCP consulting services:

**GitHub:** [github.com/RoadPilotAI](https://github.com/RoadPilotAI)

---

*CADS is built by practitioners. For everyone.*

*Canadian Audiometric Data System • Canadian Audiometric Data Standard*
