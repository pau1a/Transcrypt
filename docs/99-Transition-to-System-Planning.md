# 99. Transition to System Planning and Architecture

This document records the gating steps required before `main.md` (the Transcrypt Project Requirements Document) advances from the **PRD Phase (v0.4.0)** to the **System Architecture Phase (v0.5.0)**.

The purpose is to ensure that every conceptual, traceability, and verification gap is closed before system-level architecture, wireframing, and build planning begin.

---

## Overview

Completion of the following eleven steps marks the transition point where Transcrypt moves from *design intent* to *design realisation*.  
Each step must have a verified deliverable, an accountable owner, and a linked pull request or commit hash as evidence of completion.

---

## Transition Checklist

| Step | Category | Action / Deliverable | Purpose | Owner | Status | Evidence |
|------|-----------|----------------------|----------|--------|---------|----------|
| **1** | Document hygiene | Perform a full-read audit of `main.md` and resolve all residual placeholders (“TBD”, “later phase”, etc.). | Ensures internal coherence and removes ambiguity before system design. | Paula | ⬜ |  |
| **2** | References & Traceability | Populate **Appendix B – Reference Documents** with all external frameworks, advisories, and standards cited. Add a traceability table linking requirements to source REF-IDs. | Provides an evidence trail and allows later audit of compliance claims. | Ged / Paula | ⬜ |  |
| **3** | Competitive Context | Complete **Appendix C – Competitive Matrix** with 10–12 weighted criteria and scores for key UK SME compliance tools. | Anchors MVP positioning and justifies architectural trade-offs. | Paula | ⬜ |  |
| **4** | Canonical Data Examples | Insert canonical JSON snippets for `OrgProfileV1`, `EvidenceV1`, `FindingV1`, and `RulePackV1` under §§3.1.3 and 3.2.10. | Grounds abstract data-model descriptions in real structures for API planning. | Ged | ⬜ |  |
| **5** | Security Formalisation | Add **§7.6 Threat Model** with STRIDE-style table and two DFD call-outs (web/API and evidence flow). | Converts narrative security principles into testable design artefacts. | Paula | ⬜ |  |
| **6** | UX Definition | Extend §4 with **two golden-path task flows** (new-org onboarding and evidence-upload/report regeneration). | Establishes functional journeys to wireframe in next phase. | Paula | ⬜ |  |
| **7** | Acceptance Criteria | Translate the task flows into **Given/When/Then acceptance tests** under §9.5 or `/tests/acceptance/`. | Provides objective pass/fail for MVP readiness. | Ged | ⬜ |  |
| **8** | Observability Metrics | Populate KPI table in §3.2.10 (e.g., time-to-first-report < 60 min, report p95 < 30 s, uptime ≥ 99.9%). | Aligns engineering telemetry with product intent. | Paula | ⬜ |  |
| **9** | Content Governance | Add table of ownership for `/security`, `/privacy`, `/licenses` pages in §3.2.11; define PR-label policy. | Prevents compliance drift; enforces review cadence. | Ged | ⬜ |  |
| **10** | DR & Runbook Reference | Finalise §3.1.10 Backup/DR section with Runbook ID (ORB-DR-001) and checksum/restore tests. | Completes operational integrity prerequisite before build. | Paula | ⬜ |  |
| **11** | Version Control Milestone | Tag repository `v0.4.0-prd-solid-spine` after all above merge cleanly. | Locks a known-good baseline for hand-off to system design. | Paula | ⬜ |  |

> **Status legend:**  
> ⬜ Not started 🕐 In progress ✅ Complete

---

## Completion Criteria

All eleven steps must reach ✅ status, with each row citing a specific PR or commit hash in the *Evidence* column.

When complete:

1. Merge all related branches into `main`.
2. Tag the repo:
   ```bash
   git tag v0.4.0-prd-solid-spine
   git push origin --tags
