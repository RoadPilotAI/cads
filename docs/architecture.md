# CADS Architecture Guidance
## Implementation Requirements for CADS-Conformant Systems
**Version:** 1.0
**Date:** June 2026
**CADS Core Standard:** v1.0

---

## Table of Contents

- [1. Purpose](#1-purpose)
- [2. Offline-First Requirement](#2-offline-first-requirement)
- [3. Sync Architecture](#3-sync-architecture)
- [4. Multi-Tenant Data Isolation](#4-multi-tenant-data-isolation)
- [5. Record Integrity](#5-record-integrity)
- [6. Province Profile Resolution](#6-province-profile-resolution)
- [7. Billing Event Model](#7-billing-event-model)
- [8. Data Residency](#8-data-residency)
- [9. Security Requirements](#9-security-requirements)
- [10. Conformance Checklist](#10-conformance-checklist)

---

## 1. Purpose

This document provides implementation guidance for developers building CADS-conformant systems. It describes architectural requirements and principles that any conformant system must satisfy — regardless of technology stack, hosting environment, or deployment model.

This document does not prescribe specific technologies. A conformant system may be built on any platform, using any database, with any frontend framework, as long as the principles described here are satisfied.

For the CADS record and field specifications, see `standard/CADS-v1.0.md`. For the data model and JSON examples, see `docs/data-model.md`.

---

## 2. Offline-First Requirement

### 2.1 Rationale

Industrial audiometric testing occurs on active job sites — sawmills, mines, oil and gas facilities, construction sites. These environments frequently have no reliable internet connectivity. A CADS-conformant field application must function completely without network access during testing. Connectivity is required only for synchronization, which may occur at any time after testing is complete.

This is not optional. A system that requires connectivity during testing is not CADS-conformant for field use.

### 2.2 Local Data Storage

A CADS-conformant field application must store all records locally on the device during testing. Locally stored records must be:

- Fully formed CADS records matching the schema in `standard/CADS-v1.0.md`
- Persistently stored across application restarts and browser sessions
- Protected against data loss if the device loses power during a test session

Acceptable local storage approaches include browser OPFS (Origin Private File System) with SQLite, IndexedDB, or equivalent persistent local storage mechanisms. Volatile in-memory storage is not acceptable — records must survive application closure.

### 2.3 Offline Calculation

All CADS compliance calculations defined in Section 6 of the core standard must be executable locally without network access:

- STS calculation (Section 6.1)
- Age correction application (Section 6.2)
- Baseline comparison (Section 6.3)
- Outcome classification (Section 6.4)

A field application that defers calculations to a server is not conformant. The completed test record — including STS values, age correction, and outcome — must be fully calculated and stored locally before any sync attempt.

### 2.4 Offline Questionnaire

The pre-test questionnaire must be completable offline. Where the CADS Worker pre-completion model is used, pre-completed questionnaire data must be available locally in the field application before connectivity is required.

---

## 3. Sync Architecture

### 3.1 Sync Principles

When connectivity is available, a CADS-conformant system synchronizes locally stored records to the platform. The following principles govern sync behaviour:

**Integrity over speed.** A record must be fully valid before it is synced. Partial records must not be transmitted.

**Idempotency.** Syncing the same record twice must not create duplicate records. Record UUIDs are the deduplication key — a system receiving a record UUID it already holds must not create a second record.

**Resumability.** If a sync operation fails partway through, it must be resumable without data loss or duplication. The `sync_status` field tracks the state of each record.

**Audit preservation.** The `created_at` timestamp on every record reflects when the record was created on the field device, not when it was synced to the platform. Sync must not overwrite original timestamps.

### 3.2 Sync Status

Every CADS record carries a `sync_status` field:

| Value | Meaning |
|---|---|
| `pending` | Record created locally, not yet synced |
| `synced` | Record successfully transmitted and acknowledged by the platform |
| `failed` | Sync attempted but failed — retry required |

A record in `pending` or `failed` status must be retained locally until successfully synced. A conformant system must provide the technician visibility into sync status and alert them to unsynced records before they leave a site.

### 3.3 Packet-Based Sync

CADS recommends a packet-based sync model for field applications. A packet is a discrete, self-contained collection of all records associated with a single employer testing event — the provider record, technician record, equipment record, all worker records, all questionnaire records, and all test records from that site visit.

Packet-based sync provides:

- **Resilience** — if one packet fails to sync, others are unaffected
- **Traceability** — all records from a site visit are grouped and can be reviewed together
- **Simplicity** — each packet can be validated for completeness before transmission

Packets are identified by a packet UUID generated at the start of each site visit.

### 3.4 Conflict Resolution

CADS records are append-only by design. A test record, once created, is not edited — corrections are captured as new records referencing the original. This eliminates most conflict scenarios.

Where conflicts do occur (for example, two technicians syncing records for the same worker from different devices), resolution must be based on `created_at` timestamp. The earlier record is treated as authoritative. Systems must log conflict resolution events.

---

## 4. Multi-Tenant Data Isolation

### 4.1 Tenant Isolation Requirement

A CADS-conformant platform serving multiple tenants (hearing test companies, provincial deployments, employer accounts) must ensure complete data isolation between tenants. One tenant must never be able to access, query, or receive data belonging to another tenant.

### 4.2 Tenant Hierarchy

CADS data naturally organizes into a tenant hierarchy:

```
Platform
  └── Province (or top-level tenant)
        └── Provider (hearing test company)
              └── Employer
                    └── Worker
                          └── Test Records
```

Each level of the hierarchy must be isolated. A provider can only access their own workers and test records. A provincial dashboard can only access records where `province` matches their jurisdiction.

### 4.3 Isolation Implementation

Tenant isolation may be implemented through any combination of:

- **Row-level security** in the database (a row is only accessible to the tenant it belongs to)
- **Separate schemas or databases** per tenant
- **Application-level filtering** where every query is scoped to the authenticated tenant

Whichever approach is used, the isolation must be enforced at the data layer — not solely at the application layer. Application-layer-only filtering is insufficient because application bugs can expose cross-tenant data.

### 4.4 Subdomain Routing

Where a conformant system uses subdomain-based tenant routing (e.g., `alberta.example.ca`, `connecthearing.example.ca`), the subdomain must map to a unique tenant identifier that is applied to every database query in that session. A tenant identifier sourced from a subdomain must be validated server-side on every request — it must not be trusted from client-supplied headers or cookies without validation.

---

## 5. Record Integrity

### 5.1 UUID Generation

Record UUIDs must be generated on the field device at the time of record creation, not assigned by the server at sync time. This ensures records are fully formed and traceable before they leave the device.

All UUIDs must be UUID v4 (randomly generated). Sequential or predictable identifiers are not acceptable.

### 5.2 Immutability

CADS records are immutable once created. A test record that has been submitted must not be edited. If an error is identified post-submission, the correct approach is:

- Create a new record of type `retest` referencing the original
- Add a note to the original record's `notes` field documenting the error
- Do not delete or modify the original record

This preserves the complete audit trail and ensures that any provincial submission is not retroactively altered.

### 5.3 Timestamp Integrity

The `created_at` timestamp on every record must reflect the actual time of creation on the field device, expressed in ISO 8601 format with the local UTC offset. Systems must not normalize timestamps to UTC at creation time — the local offset is part of the record and supports audit trail verification.

The `updated_at` timestamp must be updated whenever the record's sync status changes.

### 5.4 Calibration Validation

Before a test record is created, a conformant system must verify that the referenced equipment record has valid calibration dates:

- `last_biological_calibration` must be within 365 days of the test date
- `last_acoustic_calibration` must be within 365 days of the test date

A system must warn the technician and should prevent test creation if calibration is expired.

---

## 6. Province Profile Resolution

### 6.1 Profile Application

Every Test Record includes a `province` field (ISO 3166-2 CA code). A conformant system must resolve the applicable Provincial Profile for this province and apply its parameters to:

- Validation rules (e.g., whether exit test documentation is required)
- UI prompts (e.g., flagging biennial vs annual testing schedules)
- Report generation (regulatory authority name, regulation citation)
- Retention rules

### 6.2 Profile Resolution Rules

1. Resolve the profile using the `province` field of the Test Record
2. If a profile exists for that province, apply all profile parameters
3. If no profile exists for that province, apply the CADS Core Standard only with no profile extension
4. Profile resolution must occur at record creation time, not at sync time

### 6.3 Profile Versioning

Provincial profiles are versioned independently of the core standard. A conformant system must record which profile version was applied at the time of testing. This protects against regulatory changes invalidating historical records.

---

## 7. Billing Event Model

### 7.1 Billable Test Event

A billable event is triggered when a Test Record of type `baseline`, `periodic`, or `exit` is successfully synced and acknowledged by the platform. Retest records do not generate a billing event.

The billing event must fire exactly once per qualifying test record. The record UUID is the deduplication key — a billing event for a given UUID that has already been counted must be rejected.

### 7.2 Billing Event Record

A billing event must capture:

| Field | Description |
|---|---|
| `test_uuid` | UUID of the qualifying test record |
| `province` | Province in which the test was conducted |
| `provider_uuid` | UUID of the hearing test company |
| `test_date` | Date the test was conducted |
| `test_type` | Type of test (baseline, periodic, exit) |
| `billed_at` | Timestamp when the billing event was recorded |
| `billing_period` | Calendar month in which the event was recorded |

### 7.3 Audit and Reconciliation

Billing records must be:

- Append-only — no deletion or modification of existing billing records
- Accessible to the relevant provincial authority for audit
- Reconcilable against submitted test records — every billed test must have a corresponding synced test record

Monthly billing reports must be generated per province and per provider, showing test counts by type.

---

## 8. Data Residency

### 8.1 Conformance Tiers

CADS recognizes two tiers of conformance with respect to data residency:

**Commercial Conformance** applies to privately contracted deployments between a hearing test company and an employer, where both parties agree on data handling terms. Canadian data residency is strongly recommended but not architecturally mandated at this tier. A system hosted outside Canada that correctly implements all other CADS requirements may claim commercial conformance.

**Provincial Conformance** applies to any deployment involving provincial or territorial government data, provincial dashboard access, or per-test billing under a provincial contract. Canadian data residency is mandatory at this tier without exception. A system that cannot guarantee Canadian data residency is not provincially conformant regardless of compliance with all other requirements.

Implementations claiming CADS conformance must declare which tier they conform to. A claim of CADS conformance without qualification implies provincial conformance.

### 8.2 Canadian Data Residency Requirement

Under provincial conformance, all CADS records containing worker health data must be stored on infrastructure physically located in Canada. This applies to:

- Primary databases
- Backup and disaster recovery systems
- Log storage where records may be present

Cloud providers operating Canadian data centres (AWS Canada, Azure Canada, Google Cloud Canada) satisfy this requirement when configured to use Canadian regions exclusively.

### 8.3 Data Sovereignty

Provincial audiometric data submitted under a provincial contract must remain within that province's jurisdiction or within Canada. Cross-border data transfer — including transfer to US-based servers — is not permissible for identified or re-identifiable worker health data under provincial conformance.

### 8.4 Anonymization

Worker records use anonymized UUIDs as primary identifiers. Personally identifiable information (name, employee number) is the responsibility of the employer and hearing test company and must not be transmitted in CADS records submitted to provincial systems.

---

## 9. Security Requirements

### 9.1 Encryption

All CADS data must be encrypted:

- **In transit:** TLS 1.2 minimum for all data transmission. TLS 1.3 recommended.
- **At rest:** AES-256 or equivalent for all stored records, including local device storage where technically feasible.

### 9.2 Authentication

Access to CADS/App interfaces must require authentication. Minimum requirements:

- Unique credentials per user — shared accounts are not acceptable
- Session tokens with defined expiry
- Re-authentication required after session expiry

Field applications (CADS Field) operating offline are exempt from continuous authentication requirements. Authentication must be required at application launch and re-required after configurable inactivity periods.

### 9.3 Audit Logging

All access to CADS records must be logged with:

- User or system identifier
- Action performed (read, create, sync)
- Record UUID accessed
- Timestamp

Audit logs must be retained for a minimum of 7 years and must be accessible to provincial authorities on request.

### 9.4 Vulnerability Management

Conformant systems must:

- Apply security patches to dependencies within 30 days of disclosure
- Conduct annual security review of authentication and data access controls
- Maintain a responsible disclosure process for vulnerability reports

---

## 10. Conformance Checklist

Use this checklist to verify architectural conformance before claiming CADS conformance.

**Offline-First**
- [ ] Field application functions completely without network connectivity during testing
- [ ] All records are persistently stored locally before any sync attempt
- [ ] All compliance calculations are performed locally
- [ ] Sync status is visible to the technician

**Sync**
- [ ] Records are only synced when complete and valid
- [ ] Sync is idempotent — duplicate UUIDs are rejected
- [ ] Sync is resumable without data loss or duplication
- [ ] `created_at` timestamps reflect device creation time, not sync time

**Multi-Tenant Isolation**
- [ ] Tenant isolation is enforced at the data layer
- [ ] Subdomain routing is validated server-side on every request
- [ ] Cross-tenant data access is impossible by design

**Record Integrity**
- [ ] UUIDs are generated on the field device at record creation time
- [ ] Records are immutable after submission
- [ ] Calibration dates are validated before test creation
- [ ] Profile version is recorded at test creation time

**Data Residency and Security**
- [ ] Conformance tier declared — commercial or provincial
- [ ] If provincial: all data is stored on Canadian infrastructure
- [ ] If commercial: data residency terms agreed with contracting parties
- [ ] All data in transit is encrypted with TLS 1.2 minimum
- [ ] All data at rest is encrypted
- [ ] Authentication requires unique credentials per user
- [ ] Audit logging captures all record access

**Billing**
- [ ] Billing events fire exactly once per qualifying test record
- [ ] Billing records are append-only
- [ ] Monthly reconciliation is possible against synced test records

---

*CADS/Standard — Architecture Guidance v1.0*
*© AudioPilot — Open specification. See repository for licensing terms.*
