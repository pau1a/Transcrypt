# System Architecture & Interface Specification (SAIS)

## 1. Purpose and Scope

Defines the intent, relationship to PRD `v0.3.0-prd-complete`, document ownership, and version control. Clarify what this document covers (v1 / MVP only), its relationship to the PRD, and what’s out of scope.

---

### 1.1 Document Intent

Establishes that this specification translates the Transcrypt PRD (v0.3.0-prd-complete) into implementable architectural artefacts.
Defines the SAIS as the single authoritative source for component boundaries, data contracts, and runtime behaviour for the MVP release.

### 1.2 Relationship to PRD

Explains traceability between PRD requirement IDs and this document’s sections.
States that every functional, non-functional, and security requirement in the PRD must map to one or more technical elements here.

### 1.3 Version and Control Mechanism

Specifies version tag format (`v1.x.y-sais`), branch naming conventions, and Git repository location.
Notes how milestone tags align with PRD versions and CI/CD promotion gates.

### 1.4 Ownership and Maintenance

Identifies the accountable owner (Product Lead), responsible maintainers (Engineering Lead + Security Lead), and review cadence (quarterly or upon major release).
Defines approval and sign-off workflow for any structural change.

### 1.5 Scope of Coverage

Declares what is in scope for MVP: Transcrypt Essentials App, Evidence Services, Report Generation, Billing, and Marketing↔Essentials handshake.
States explicitly what is out of scope: partner APIs, NIS2 Pack, advanced connectors, and assisted-tier collaboration.

### 1.6 Intended Audience

Lists audiences and their expectations:

* Engineering and DevOps teams → implementation reference
* Product and UX teams → design and acceptance alignment
* Compliance and Security → control verification
* External partners → interface boundaries only

### 1.7 Document Change Log Linkage

Indicates that all edits are recorded in Appendix 15, Change Log.
Each commit references a PRD section ID in its Git message for bidirectional traceability.

---

This makes Section 1 both authoritative and auditable — the anchor for the rest of the SAIS.


## 2. System Overview

Summarises the full system: philosophy, major layers, and the MVP boundary of delivery. Summarise the full system at a bird’s-eye level — major layers, runtime context, and guiding design principles (automation-first, invisible infrastructure, etc.).

## 3. Component Architecture

Outlines every subsystem — services, clients, SDKs, external integrations — with clear boundaries, roles, and dependencies. Define each subsystem: boundaries, roles, dependencies, and whether they’re internal, external, or partner-facing.

## 4. Data and Storage Model

Canonical schemas, entity relationships, encryption, retention, and provenance. Includes schema versioning and ownership.

## 5. Interface Specifications

Formal contracts: APIs, authentication flows, webhooks, event topics, and partner connectors.
Includes request/response examples and error semantics.Detailed contracts for each interface:

API endpoints and payloads

Authentication and authorisation

Error semantics and versioning

Example requests/responses

## 6. User Experience and Wireframes

Functional UI definition — navigation spine, screen-by-screen wireframes, UX–API bindings, accessibility guarantees, and responsive behaviour.
Wireframes embedded (Mermaid/Figma links) and tied to acceptance criteria. 

## 7. Sequence and Runtime Behaviour

System-level and user-journey diagrams showing how components, APIs, and UI interact at runtime. Includes async/event patterns.

## 8. Deployment and Environment Architecture

Describes environments (dev, staging, prod), configuration, secrets handling, and network topology. Defines IaC linkage and environment parity rules.

## 9. Security, Privacy, and Compliance Alignment

Maps architecture to controls in IEC 62443, NIS2, and Cyber Essentials. Details key management, isolation, audit logging, and redaction pipelines.

## 10. Observability and Telemetry

Defines metrics, traces, structured logs, and SLOs. Specifies tenant/request correlation IDs and alert thresholds.

## 11. Build and Delivery Pipeline

CI/CD architecture — linting, test suites, security scans, release gating, artefact signing, and promotion between environments.

## 12. Operational Runbooks

Day-two procedures: monitoring, backup cadence, rotation, incident response, recovery validation, and change windows.

## 13. Non-Functional Requirements

Quantitative targets: performance, scalability, reliability, and resource budgets. Links directly to observability metrics.

## 14. Traceability and Acceptance Mapping

Table mapping PRD requirements and acceptance criteria to implementing components, APIs, and tests.

## 15. Appendices and Change Log

Supporting material — schema dumps, diagram sources, glossary, environment variables, revision history.
