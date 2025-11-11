---
document_type: "Dual-mode PRD"
strategic_sections: [0,1,2,3,9,10]
specification_sections: [4,5,6,7,8]
version_control: "Git tracked"
review_cycle: "Quarterly or upon major release"
---

- [Transcrypt Product Requirements Document (PRD)](#transcrypt-product-requirements-document-prd)
  - [Document Scope and Usage](#document-scope-and-usage)
  - [0. Prologue – Visionary Statement (Non-Technical; Context Setting Only)](#0-prologue--visionary-statement-non-technical-context-setting-only)
  - [1. Vision and Purpose](#1-vision-and-purpose)
    - [Product Definition (MVP)](#product-definition-mvp)
    - [Scope Guardrails (v1)](#scope-guardrails-v1)
    - [Human Role Definition](#human-role-definition)
    - [Audience and Philosophy](#audience-and-philosophy)
    - [Design Tenets](#design-tenets)
    - [1.1 Problem Statement](#11-problem-statement)
    - [1.2 Mission and Guiding Principles](#12-mission-and-guiding-principles)
    - [1.3 Target Users and Stakeholders](#13-target-users-and-stakeholders)
    - [1.4 Success Criteria and Long-Term Impact](#14-success-criteria-and-long-term-impact)
  - [2. Market Context and Competitive Landscape](#2-market-context-and-competitive-landscape)
    - [2.1 Overview of UK SME Cyber and GRC Landscape](#21-overview-of-uk-sme-cyber-and-grc-landscape)
    - [2.2 Key Competitors and Differentiation](#22-key-competitors-and-differentiation)
    - [2.3 Market Share Estimates and Pricing Models](#23-market-share-estimates-and-pricing-models)
    - [✅ Why it could make sense](#-why-it-could-make-sense)
    - [⚠️ What to watch / what needs clear design](#️-what-to-watch--what-needs-clear-design)
    - [🔍 Relevant actors / opportunities](#-relevant-actors--opportunities)
    - [🎯 How you might incorporate it into Transcrypt Essential offering](#-how-you-might-incorporate-it-into-transcrypt-essential-offering)
    - [2.4 Future Extensibility to Other Nations](#24-future-extensibility-to-other-nations)
    - [2.5 Regulatory and Assurance Environment](#25-regulatory-and-assurance-environment)
  - [Tenancy Model (Design Intention)](#tenancy-model-design-intention)
  - [3. Product Architecture and Central Platform Design](#3-product-architecture-and-central-platform-design)
    - [Edge Layer](#edge-layer)
    - [Central Layer ()](#central-layer-)
    - [Security Model](#security-model)
      - [Audit event schema](#audit-event-schema)
    - [Extensibility Model](#extensibility-model)
    - [Architectural Summary](#architectural-summary)
    - [Framework Modularity](#framework-modularity)
  - [3.1 Core Architecture Overview](#31-core-architecture-overview)
    - [3.1.1 System Overview](#311-system-overview)
      - [Data Ownership and Sovereignty](#data-ownership-and-sovereignty)
      - [Automation-First Operating Model](#automation-first-operating-model)
      - [Invisible Infrastructure Principle](#invisible-infrastructure-principle)
      - [User Tiers and Human Interaction Model](#user-tiers-and-human-interaction-model)
    - [3.1.2 Transcrypt Components and Interfaces](#312-transcrypt-components-and-interfaces)
    - [3.1.3 Data Model (Canonical Contracts)](#313-data-model-canonical-contracts)
    - [3.1.4 Storage and Artefacts](#314-storage-and-artefacts)
    - [3.1.5 Security, Privacy, and Trust Model](#315-security-privacy-and-trust-model)
      - [Why this combo](#why-this-combo)
      - [How the flow works](#how-the-flow-works)
      - [What to implement](#what-to-implement)
      - [Pitfalls to avoid](#pitfalls-to-avoid)
    - [3.1.6 Extensibility \& Integration Framework](#316-extensibility--integration-framework)
    - [3.1.7 DevEx, QA, and Delivery](#317-devex-qa-and-delivery)
    - [3.1.8 Minimal Viable Slice (MVP cut)](#318-minimal-viable-slice-mvp-cut)
    - [3.1.9 Technology Choices (initial)](#319-technology-choices-initial)
    - [3.1.10 Operational Runbooks (high level)](#3110-operational-runbooks-high-level)
    - [3.x Technical Constraints \& Conventions (non-normative)](#3x-technical-constraints--conventions-non-normative)
    - [3.2 Core Components and Interfaces](#32-core-components-and-interfaces)
      - [3.2.1 Web App (Next.js @ `https://transcrypt.xyz`)](#321-web-app-nextjs--httpstranscryptxyz)
      - [3.2.2 API Gateway \& Policy Enforcement {#API-Gateway-\&-Policy-Enforcement}](#322-api-gateway--policy-enforcement-api-gateway--policy-enforcement)
      - [3.2.3 Rule Evaluation Service (Deterministic + Runtime Inference)](#323-rule-evaluation-service-deterministic--runtime-inference)
      - [3.2.4 LLM Assist Pipeline (Build-Time Only)](#324-llm-assist-pipeline-build-time-only)
      - [3.2.5 Evidence Services](#325-evidence-services)
      - [3.2.6 Report Service](#326-report-service)
      - [3.2.7 Admin Console (Internal)](#327-admin-console-internal)
      - [3.2.8 Data Stores \& Artefacts (Interface Contracts)](#328-data-stores--artefacts-interface-contracts)
      - [3.2.9 Observability \& Audit](#329-observability--audit)
      - [3.2.10 Public Site \& Content (Marketing, Legal, Support)](#3210-public-site--content-marketing-legal-support)
      - [3.2.11 External Integrations (First-Party)](#3211-external-integrations-first-party)
      - [3.2.12 Non-Functional Interface Contracts](#3212-non-functional-interface-contracts)
    - [3.3 Security, Privacy, and Trust Model](#33-security-privacy-and-trust-model)
    - [3.4 Extensibility and Integration Framework](#34-extensibility-and-integration-framework)
    - [3.5 Technical Stack and Dependencies](#35-technical-stack-and-dependencies)
  - [4. User Experience and Functional Requirements](#4-user-experience-and-functional-requirements)
    - [What this section is for](#what-this-section-is-for)
    - [Top priorities (stack-ranked)](#top-priorities-stack-ranked)
    - [Who we’re designing for (and what they care about)](#who-were-designing-for-and-what-they-care-about)
    - [Minimal journeys we must nail (MVP)](#minimal-journeys-we-must-nail-mvp)
    - [Copy \& interaction tone](#copy--interaction-tone)
    - [Where we will *not* compromise](#where-we-will-not-compromise)
    - [Trade-offs we’ll manage deliberately](#trade-offs-well-manage-deliberately)
    - [Instrumentation that keeps us honest](#instrumentation-that-keeps-us-honest)
    - [What this means for design \& build right now](#what-this-means-for-design--build-right-now)
    - [Why the site matters to UX (not just marketing)](#why-the-site-matters-to-ux-not-just-marketing)
    - [Site journeys (the “public” half of 4.1)](#site-journeys-the-public-half-of-41)
    - [What each top page must guarantee (content promises)](#what-each-top-page-must-guarantee-content-promises)
    - [How the site and app handshake (frictionless routing)](#how-the-site-and-app-handshake-frictionless-routing)
    - [Priorities for the site (stack-ranked)](#priorities-for-the-site-stack-ranked)
    - [What to build first (site)](#what-to-build-first-site)
    - [4.1 User Journeys and Onboarding](#41-user-journeys-and-onboarding)
      - [4.1.1 Public Site Journeys (credibility → correct door → app intent)](#411-public-site-journeys-credibility--correct-door--app-intent)
      - [4.1.2 App Onboarding Spine (four entry lanes, one shared flow)](#412-app-onboarding-spine-four-entry-lanes-one-shared-flow)
      - [4.1.3 Guardrails, Acceptance, and UX KPIs](#413-guardrails-acceptance-and-ux-kpis)
      - [4.1.4 Site↔App Handshake (routing \& truth alignment)](#414-siteapp-handshake-routing--truth-alignment)
    - [Screen-by-screen: what good looks like](#screen-by-screen-what-good-looks-like)
    - [Guardrails, nudges, and acceptance](#guardrails-nudges-and-acceptance)
    - [4.2 Interface Philosophy](#42-interface-philosophy)
    - [4.3 Key User Stories](#43-key-user-stories)
    - [4.4 Accessibility and Usability Standards](#44-accessibility-and-usability-standards)
      - [What this section is for](#what-this-section-is-for-1)
      - [Priorities (stack-ranked)](#priorities-stack-ranked)
      - [Non-negotiable standards (what we target)](#non-negotiable-standards-what-we-target)
      - [Design \& content rules (operationalised)](#design--content-rules-operationalised)
      - [Interaction \& structure patterns](#interaction--structure-patterns)
      - [Reports (HTML \& PDF) accessibility](#reports-html--pdf-accessibility)
      - [Mobile \& low-bandwidth](#mobile--low-bandwidth)
      - [Cognitive load \& clarity](#cognitive-load--clarity)
      - [Testing \& enforcement (make it routine)](#testing--enforcement-make-it-routine)
      - [Acceptance criteria (task-level)](#acceptance-criteria-task-level)
    - [4.5 Offline and Multi-Device Support](#45-offline-and-multi-device-support)
  - [5. Data, Intelligence, and Automation](#5-data-intelligence-and-automation)
    - [5.1 Data Flow Architecture (v1)](#51-data-flow-architecture-v1)
    - [5.2 Machine Learning and AI Components (v1)](#52-machine-learning-and-ai-components-v1)
    - [5.3 Reporting, Dashboards, and Insights (v1)](#53-reporting-dashboards-and-insights-v1)
    - [5.4 Auditability and Data Provenance (v1)](#54-auditability-and-data-provenance-v1)
    - [5.5 Closed-Source Policy and Evidence Integrity](#55-closed-source-policy-and-evidence-integrity)
    - [Traceability Table (Section 5)](#traceability-table-section-5)
  - [6. Compliance and Governance Framework](#6-compliance-and-governance-framework)
    - [6.1 Operating Baseline (Cyber Essentials in Practice)](#61-operating-baseline-cyber-essentials-in-practice)
    - [6.2 Cyber Essentials Alignment (v3.2)](#62-cyber-essentials-alignment-v32)
    - [6.3 Risk Management and Assurance](#63-risk-management-and-assurance)
    - [6.4 Policy Library and Evidence Management](#64-policy-library-and-evidence-management)
    - [6.5 Governance of Product Lifecycle](#65-governance-of-product-lifecycle)
  - [7. Security and Infrastructure Requirements](#7-security-and-infrastructure-requirements)
    - [7.1 Authentication, Authorisation, and Identity Management](#71-authentication-authorisation-and-identity-management)
    - [7.2 Network Segmentation and Zero Trust Architecture](#72-network-segmentation-and-zero-trust-architecture)
    - [7.3 Data Encryption and Key Management](#73-data-encryption-and-key-management)
    - [Managed Key Operations Summary](#managed-key-operations-summary)
    - [7.4 Operational Resilience and Incident Response](#74-operational-resilience-and-incident-response)
    - [7.5 Secure Software Supply Chain](#75-secure-software-supply-chain)
  - [8. Monetisation and Revenue Model](#8-monetisation-and-revenue-model)
    - [8.1 Pricing Strategy](#81-pricing-strategy)
    - [8.2 Subscription Tiers and Value Differentiation](#82-subscription-tiers-and-value-differentiation)
    - [8.3 Partner and Reseller Ecosystem](#83-partner-and-reseller-ecosystem)
    - [8.4 Licensing and Legal Terms](#84-licensing-and-legal-terms)
    - [8.5 Metrics for Financial Sustainability](#85-metrics-for-financial-sustainability)
  - [9. Roadmap](#9-roadmap)
    - [9.1 MVP Definition](#91-mvp-definition)
    - [9.2 Phase Milestones and Timelines](#92-phase-milestones-and-timelines)
      - [Post-MVP: Platform Phase Highlights](#post-mvp-platform-phase-highlights)
      - [Partner/Integrator API (v2.0)](#partnerintegrator-api-v20)
    - [9.3 Resource and Budget Planning](#93-resource-and-budget-planning)
    - [9.4 Risk Register and Mitigation](#94-risk-register-and-mitigation)
      - [9.4.1 Assisted Tier \& Collaboration (Post-MVP) {#assisted-tier}](#941-assisted-tier--collaboration-post-mvp-assisted-tier)
      - [9.4.2 Partner Channel \& Co-Branding (Post-MVP)](#942-partner-channel--co-branding-post-mvp)
    - [9.5 Quality Assurance and Acceptance Criteria](#95-quality-assurance-and-acceptance-criteria)
  - [10. Future Outlook and Strategic Extensions](#10-future-outlook-and-strategic-extensions)
    - [10.1 Interoperability with Other National Frameworks](#101-interoperability-with-other-national-frameworks)
    - [10.2 Research and Development Themes](#102-research-and-development-themes)
    - [10.3 Potential Spin-offs and Product Lines](#103-potential-spin-offs-and-product-lines)
    - [10.4 Long-Term Sustainability and Ethical Charter](#104-long-term-sustainability-and-ethical-charter)
    - [10.5 Closing Summary](#105-closing-summary)
  - [Cross-Referencing Framework](#cross-referencing-framework)
    - [Strategic/Technical Markers (Legacy)](#strategictechnical-markers-legacy)
  - [Appendices](#appendices)
    - [A. Terminology and Abbreviations](#a-terminology-and-abbreviations)
    - [B. Reference Documents](#b-reference-documents)
    - [C. Competitive Matrix](#c-competitive-matrix)
      - [UK SME Cybersecurity Compliance Landscape](#uk-sme-cybersecurity-compliance-landscape)
        - [Introduction: SME Cybersecurity Obligations in the UK](#introduction-sme-cybersecurity-obligations-in-the-uk)
        - [Key Compliance Frameworks \& Requirements for UK SMEs (Context)](#key-compliance-frameworks--requirements-for-uk-smes-context)
        - [Competitive Landscape: Compliance Solution Providers for UK SMEs](#competitive-landscape-compliance-solution-providers-for-uk-smes)
        - [CyberSmart (UK) – Cyber Essentials Compliance Made Easy](#cybersmart-uk--cyber-essentials-compliance-made-easy)
        - [Drata (US) – Automated GRC Platform with UK Framework Support](#drata-us--automated-grc-platform-with-uk-framework-support)
        - [Vanta (US) – Expanding into UK Standards (Cyber Essentials, NIS2)](#vanta-us--expanding-into-uk-standards-cyber-essentials-nis2)
        - [DataGuard (Germany/UK) – “Compliance-as-a-Service” with Human Expertise](#dataguard-germanyuk--compliance-as-a-service-with-human-expertise)
        - [SureCloud (UK) – Integrated GRC Platform with SME Packages](#surecloud-uk--integrated-grc-platform-with-sme-packages)
        - [ISMS.online (UK) – Cloud Platform for ISO 27001 and More](#ismsonline-uk--cloud-platform-for-iso-27001-and-more)
        - [OneTrust (US/UK) – Broad Compliance Platform (Privacy-Focused)](#onetrust-usuk--broad-compliance-platform-privacy-focused)
        - [6clicks (Australia) – Agile GRC with Extensive Framework Library](#6clicks-australia--agile-grc-with-extensive-framework-library)
        - [Kaseya Compliance Manager GRC (RapidFire Tools) – MSP-oriented Compliance Automation](#kaseya-compliance-manager-grc-rapidfire-tools--msp-oriented-compliance-automation)
        - [Enterprise GRC Solutions (RSA Archer, ServiceNow, etc.) – High-End Options (Rarely Used by SMEs)](#enterprise-grc-solutions-rsa-archer-servicenow-etc--high-end-options-rarely-used-by-smes)
        - [Comparison of Key Compliance Solutions for UK SMEs](#comparison-of-key-compliance-solutions-for-uk-smes)
        - [Conclusion](#conclusion)
        - [Citations](#citations)
    - [D. Change Log](#d-change-log)
    - [E. Markdown Codes](#e-markdown-codes)
- [Markdown Syntax Cheatsheet](#markdown-syntax-cheatsheet)
  - [Headings](#headings)
- [H1](#h1)
  - [H2](#h2)
    - [H3](#h3)
      - [H4](#h4)
        - [H5](#h5)
          - [H6](#h6)
  - [Emphasis](#emphasis)
  - [Lists](#lists)
    - [Unordered](#unordered)
    - [Ordered](#ordered)
  - [Links and Images](#links-and-images)
  - [Code](#code)
    - [Code Block](#code-block)
  - [Blockquote](#blockquote)
  - [Horizontal Rule](#horizontal-rule)
  - [Table](#table)
  - [Checkboxes (Task Lists)](#checkboxes-task-lists)
  - [Footnote (if supported)](#footnote-if-supported)
  - [Escaping Characters](#escaping-characters)


# Transcrypt Product Requirements Document (PRD)

## Document Scope and Usage

This document operates dually as both the **Product Requirements Document (PRD)** and the **Project Plan** for Transcrypt.  
It contains two distinct modes of content:

| Mode | Purpose | Audience | Authority |
|:----:|:---------|:----------|:-----------|
| **Strategic** | Defines *why* Transcrypt exists, its market context, vision, and roadmap. | Leadership, stakeholders | Guides direction but not implementation detail. |
| **Specification** | Defines *how* the system functions: architecture, data flows, automation, and user experience. | Engineering, design, QA | Source of truth for build and validation. |

Strategic content is concentrated in **Sections 0–3**, **9**, and **10**, where we set the vision, market stance, and long-range direction for Transcrypt.
Specification content lives in **Sections 4–8**, translating that intent into architecture, UX, security, and monetisation mechanics, with §5 carrying the **[Traceability Table (§5)](#traceability-table-section-5)** that binds strategy to delivery.
Cross-references between the two are deliberate and annotated using inline comments:
`<!-- strategic -->` or `<!-- specification -->`.

Every requirement or component in this PRD can be traced to its origin or future delivery lane via inline cross-reference tags and the **[Traceability Table (§5)](#traceability-table-section-5)**. No orphaned feature references remain; each dependency resolves backward to strategy or forward to roadmap commitments.

<!-- strategic -->
## 0. Prologue – Visionary Statement (Non-Technical; Context Setting Only)

If I sold my company today, I'd start my next multi-million dollar business in 90 days using only AI. 

Here's how:

I'd create 5 AI specialists that work 24/7 for a fraction of what a single employee costs.

Meet my AI dream team:

THE ANALYST

I'd upload a detailed vision document explaining my business model
I'd have it identify emerging market opportunities with hard data
I'd ask: "Find the top 3 underserved problems in profitable industries"
I'd demand specific research on customer behaviour and spending patterns
I'd make it spot trends competitors are missing

THE GROWTH HACKER

I'd ask: "What's the fastest path to 10,000 customers with supporting evidence?"
I'd have it design rapid testing frameworks for every assumption
I'd make it identify the highest-impact growth levers specific to my business
I'd run every strategy through "What would break this?" analysis
I'd demand concrete timelines and success metrics for each test

THE SALES MACHINE

I'd never ask for generic sales copy - too weak
I'd build systematically: pain points → value props → objection handling → close
I'd force it to create sales sequences that convert strangers into buyers
I'd make it design irresistible offers that feel like no-brainers
I'd have it craft follow-up systems that turn one-time buyers into repeat customers

THE SYSTEM BUILDER

I'd make it map out every process needed to scale efficiently
I'd have it create detailed automation workflows for customer onboarding
I'd ask for complete operational frameworks that work without me
I'd make it identify bottlenecks before they become problems
I'd demand step-by-step scaling plans with specific resource requirements

THE BRAND BUILDER

I'd have it create 20+ pieces of authority-building content per week
I'd make it analyze successful competitors and find content gaps
I'd force it to create posts that position me as the obvious expert
I'd have it develop content that builds trust before anyone meets me
I'd make it test messaging until it resonates with my exact audience

AI without direction is worthless. 
AI with basic direction gets basic results. 
AI with elite direction builds empires.

While you're debating AI ethics, I'm building AI empires.

<!-- strategic -->
## 1. Vision and Purpose
 
### Product Definition (MVP)

**Transcrypt Essential (v1)** is a web-based compliance platform for UK SMEs, combining a secure site, progressive web app, and automation engine.
It provides **guided assessments**, encrypted **evidence storage**, **auto-generated policies/templates**, and **AI-assisted suggestions** that reduce human effort while keeping costs low. Within this PRD, a tenant is a customer instance that runs co-resident in a shared runtime with strict logical and cryptographic isolation. Tenants are separated by data boundaries, identity scopes, and policy controls, not by per-customer infrastructure or deployments.

**Non-goals (MVP):**

Within this PRD, a **tenant** represents a single customer instance that lives alongside others inside the shared Transcrypt environment. Tenants remain distinct through logical separation—data boundaries, identity scopes, and policy controls—rather than through separate hardware or deployments. For this phase every tenant is assumed to operate locally, and all tenancy references describe this co-resident but strictly isolated model.

- No multi-tenant orchestration layer for external assessors/auditors. [[Post-MVP: §9.4.1 Assisted Tier & Collaboration]]
- No advanced ML training loops or model fine-tuning pipelines. [[Post-MVP: §9.2 Phase Milestones and Timelines]]
- No cryptographic provenance ledger or blockchain-style attestations. [[Post-MVP: §9.4 Risk Register and Mitigation]]
- No marketplace or collaboration features beyond basic account roles. [[Post-MVP: §9.4.1 Assisted Tier & Collaboration, §9.4.2 Partner Channel & Co-Branding]]

**Design Principle:** “Automation you don’t feel.” AI is used to remove toil (classification, drafting, gap-spotting), not to introduce operational complexity.

**Naming:**  
- **Transcrypt Essential** = MVP (this document’s scope).
- **Transcrypt Platform** = [post-MVP expansion (see Roadmap)](#10-future-outlook-and-strategic-extensions).

### Scope Guardrails (v1)

- **User:** SME owner/manager or their in-house IT; no external auditor workflows.  
- **Jobs-to-be-done (v1):** pass Cyber Essentials quickly, keep up with renewals, store evidence, generate simple reports.   
- **AI in v1:** assistive **and evaluative at runtime** (inference only; **no training/fine-tuning**). Deterministic checks gate issuance; AI provides advisory findings and rationale. 
- **Security posture:** tenant-encrypted storage; audit log is append-only (no external ledger—see Roadmap).

> **Terminology:** Within this PRD, references to “law” mean the published Cyber Essentials scheme documentation and IASME guidance. Broader regulatory alignment is out of scope for Transcrypt Essential.

Transcrypt Essential exists to help **UK SMEs meet and renew Cyber Essentials** without drowning in admin or jargon. The first release is intentionally narrow: translate the scheme’s guidance into the plain-language steps and evidence an in-house team needs, surface what is missing, and keep everything tidy for the next renewal cycle. It is a **framework-to-operations translator**, giving an owner a single place to collect answers, evidence, and reports. Success is measured in hours saved, fewer surprises during certification, and confidence that nothing has fallen through the cracks.

Trust comes from clarity. Every recommendation, reminder, and report is backed by traceable rationale so an SME team can see exactly why Cyber Essentials expects a given action and how they can evidence it. Transcrypt keeps the promise of a simple tool that quietly does the heavy lifting: organise tasks, track progress, and preserve artefacts so renewals feel like a routine health check rather than a yearly scramble.


### Human Role Definition

For v1 (**Transcrypt Essential**) all compliance flows are **self-serve**.
AI-driven automation replaces most manual review steps and guides the user end-to-end without external assistance.
Human experts re-enter the loop only in later versions (see §9.4.1 Assisted Tier & Collaboration) to deliver optional audit reviews and trust attestations.
This ensures automation is the revenue engine while human expertise remains an opt-in premium service, not a bottleneck.
+ Runtime AI produces advisory findings and rationale; only deterministic checks can change pass/fail (issuance).

### Audience and Philosophy

Transcrypt Essential is built **for SMEs**, not large enterprises.
Its architecture borrows security and reliability practices from enterprise systems, but these operate **entirely behind the scenes**.  
The user interacts only with clear guidance, automated actions, and human-readable results—never raw controls or configuration pages.  
In short: *enterprise-grade under the bonnet, SME-simple at the wheel*.

### Design Tenets

1. **Invisible Complexity** – advanced engineering should be felt only as speed or accuracy, never as extra controls.
2. **Plain Language** – all interfaces, reports, and AI feedback are written for non-specialists.
3. **Zero Setup** – onboarding requires no infrastructure knowledge; configuration is automatic.
4. **Guided Autonomy** – users can achieve compliance independently, yet remain on safe rails.

**AI is the accelerator, not the decider.**
The platform uses AI to interpret unstructured customer input against framework expectations and to return a considered view of conformance, expressed in natural language. It identifies which controls appear met, which are uncertain, and which need action—then recommends what to do next. The AI’s reasoning remains visible and explainable. The **rule engine** handles anything that must be verified, logged, or proven: it performs deterministic checks, records provenance, and ensures that what the AI infers can be evidenced and audited.

AI operates within clear boundaries. It can interpret, compare, and advise, but it does not issue binding outcomes. When interpretation involves nuance, it may speak through defined **analyst personas** that provide perspective rather than verdict—human-style reasoning with transparent logic the user can inspect.

This is the disciplined version of the “AI dream team” concept.
The **Analyst** surfaces posture gaps and market opportunities.
The **Growth Hacker** tests language and engagement.
The **Sales Machine** writes only from verified benefit.
The **System Builder** drafts executable runbooks.
The **Brand Builder** publishes evidence-led insights that earn trust.
Each assistant is held to the same test as the product itself: clarity, relevance, and verifiability.

The purpose is commercial as well as technical. Year one proves that a lean, founder-led business can earn while it learns: ship an MVP that pays for itself, reach a clean £500 monthly profit by month twelve, and grow through retention and partnerships rather than advertising. From there the wider Transcrypt Platform expands by *translation rather than reinvention*—re-using the same interpretive core across new frameworks, insurers, and service providers, making interoperability something customers feel rather than see.

Everything in this document points toward a single goal: Transcrypt should feel like a quiet, capable companion—one that makes difficult things understandable, keeps its promises, and leaves a paper trail anyone can trust.

### 1.1 Problem Statement

Small businesses across the UK increasingly treat Cyber Essentials as table stakes for winning work, renewing insurance, or reassuring customers. Yet most teams fit certification duties around already-stretched roles. They juggle spreadsheets, emails, and shared drives to chase the same five control areas year after year, often starting from scratch because last year’s effort vanished with the person who led it. The pain is not a lack of willingness—it is the **time and clarity burden** of translating guidance into the exact tasks, evidence, and sign-offs their organisation needs.

Current tools do little to shrink that burden. Enterprise GRC platforms drown SMEs in configuration and cost; lightweight portals stop at the questionnaire, leaving users to guess what good evidence looks like or how to keep it current. Consultants can help, but fees and scheduling make them impractical for annual renewals. The gap is clear: small businesses need a straightforward system that keeps Cyber Essentials expectations in plain view, organises the work, and holds onto every artefact so the next renewal feels like a continuation, not a restart.

### 1.2 Mission and Guiding Principles

Transcrypt’s mission is to make Cyber Essentials maintenance effortless for small teams. That means turning guidance into ready-made checklists, nudges, and evidence shelves so SMEs can stay on top of the controls without hiring a consultant or reinventing a process every year. The platform exists to remove friction: fewer late nights before a submission, fewer surprises from IASME updates, and more confidence that the basics are consistently covered.

Three principles shape this mission:

1. **Show the why.** Every prompt and policy template links back to the relevant Cyber Essentials control so teams know exactly why a task matters.
2. **Keep it lightweight.** The product assumes an SME reality—limited time, lean tooling, and people wearing multiple hats. Automations focus on the moments that burn time: gathering screenshots, checking device lists, and chasing sign-offs.
3. **Build for continuity.** Everything saved in Transcrypt Essential is versioned and easy to pick up again, so renewals feel like an update, not a restart.

### 1.3 Target Users and Stakeholders

Transcrypt Essential serves **SME owners, directors, and in-house IT leads** who carry the responsibility for Cyber Essentials but not the time to dedicate a full role to it. Typical users include:

- Owner-operators and managing directors who need a clear view of progress toward certification without wading through technical jargon.
- Internal IT managers or trusted generalists who juggle helpdesk, infrastructure, and compliance duties and need a structured checklist that keeps everyone aligned.
- Operations or office managers asked to “own the questionnaire” alongside their day job and who need templates, examples, and reminders to keep momentum.

These users want a self-serve product that respects their time, explains expectations in context, and stores everything needed for next year. Transcrypt Essential deliberately excludes third-party auditors, primes, or external assurance teams from the product surface; they remain out of scope until the wider Transcrypt Platform phases. While third-party auditors and assurance bodies are not direct users of Transcrypt Essential, subscribers can generate and export structured reports, evidence summaries, or assessor-ready bundles in the format most useful to them. This keeps external interactions one step removed yet fully supported.

### 1.4 Success Criteria and Long-Term Impact

Success for Transcrypt in its early phase will be measured by validation and momentum, not scale. The first six months are about proving that one person can design, build, and run a credible commercial platform from a single, elegant site that quietly outclasses the noise of the industry. The aim is to attract a handful of small businesses willing to pay for clarity — not consultancy. Every completed sign-up, trial conversion, and support query will be used to refine the experience, the language, and the trust model. At this stage, success is defined by proof of appetite: that SMEs will part with their own money for a platform that genuinely makes the maze of cyber regulation simpler to navigate. The goal is to exit month six with a working product, a visible trickle of paying users, and operational confidence that the model holds together without outside capital.

Early visibility will come from giving value away. The Transcrypt site will double as a trusted SME resource — hosting plain-English explainers, checklists, and free e-books that demystify Cyber Essentials and wider security hygiene. This “pay-forward” strategy builds credibility before conversion: useful content brings business owners into orbit long before they are ready to buy. A modest advertising budget in the opening months will amplify that reach, then taper as organic reputation and search authority take over. Discovery should feel educational, not promotional; prospects should leave the site wiser even if they never subscribe.

Brian’s personal brand will serve as the human face of that outreach. He will commit to a year-long public sprint — five short videos each week — shared on YouTube and embedded directly into the site. His down-to-earth, older-and-wiser voice as a former motor mechanic turned cyber engineer becomes a distinctive USP: someone who explains complex security ideas without jargon or pretence. These videos will set the tone for Transcrypt itself — practical, humble, and credible — building a recognisable persona that small-business owners trust before they ever meet the product.

From month seven onward, the measure becomes profitability, not revenue. The target is a clean, sustainable profit of around £500 per month by the end of the first year — enough to demonstrate a replicable business model and justify reinvestment. Achieving this means keeping infrastructure lean, automating onboarding and evidence generation, and using founder time surgically where it adds visible value. Marketing will stay tightly focused: a credible web presence, a handful of authority-building articles, and Brian’s approachable public persona as the owner-operator backed by a small team of “techies.” Each subscription and renewal will count more than metrics ever could, and user testimonials — not ad spend — will power growth. By that point, the platform should run with minimal human friction: a product that quietly earns while the founder sleeps.

The long-term impact is measured in endurance and credibility rather than investor multiples. If Transcrypt continues beyond its first thousand customers as a stable, self-funded company, it will have proved a larger idea — that cyber compliance can be made humane, intelligible, and profitable at micro-scale. The goal is a business that never needs to chase venture money or artificial growth curves, but instead becomes a trusted small-business ally whose income compounds steadily year after year. Over time, it can evolve into a platform that represents the lived compliance reality of the UK’s SME sector — a dataset and reputation that regulators, insurers, and primes quietly rely on. The enduring success metric will not be valuation but influence: that the standards of clarity, honesty, and craftsmanship established by Transcrypt subtly raise the bar for how cyber assurance is done across the country.

By automating content creation and evidence generation through AI, Transcrypt competes with venture-backed platforms on quality and reach while operating at a fraction of their cost base — reaching escape velocity before capital becomes a constraint.

This PRD is deliberately *hybrid.*
It records not just requirements but reasoning — both the *what* and the *why.*
Readers should treat strategic sections as context and technical sections as binding for implementation.

<!-- strategic -->
## 2. Market Context and Competitive Landscape

Transcrypt Essential launches with a **UK-first focus**, helping SMEs achieve and maintain **Cyber Essentials** certification — the government-endorsed baseline for cyber hygiene. The compliance engine beneath it is **framework-agnostic**, designed so that each framework can be represented as a **modular control pack** containing:

* control definitions,
* evidence expectations,
* scoring logic, and
* mappings to shared baseline controls.

This architecture keeps Transcrypt grounded in the UK’s most familiar assurance scheme while preparing it for later modules that support regulatory or sectoral frameworks such as **NIS2**, **ISO 27001**, or **SOC 2** — all without code rewrite.

The SME cyber-compliance market today is dominated by **service-heavy, software-light** providers. Firms such as CyberSmart, Bulletproof, IASME, and an expanding tier of managed-service companies sell compliance as a bundle: certification, managed antivirus, and a promise of “peace of mind.” Their strength is marketing polish; their weakness is depth. They simplify by omission rather than by design. Few offer continuous alignment with changing frameworks or transparent mappings between them, and fewer still provide live, data-backed assurance that supply-chain partners and insurers increasingly expect.

This gap creates space for a product that blends **policy literacy with operational empathy** — one that helps small businesses understand what compliance means day-to-day instead of merely ticking boxes. Transcrypt’s proposition is not *just* to undercut on price but to outperform on authenticity, clarity, and trust.

Macro conditions amplify the opportunity. Tightening oversight under instruments such as **NIS2**, rising supply-chain due-diligence requirements, and insurer scrutiny are driving SMEs toward demonstrable, ongoing assurance. At the same time, consultant-led models have become unaffordable. The next generation of tools must therefore be **lightweight, continuous, and self-service** — qualities that legacy providers, bound to manual workflows and compliance silos, cannot easily deliver.

Transcrypt’s advantage lies in **agility and transparency**. From day one, its controls and evidence logic are modelled as structured, reusable knowledge, enabling rapid updates as frameworks evolve while keeping language plain and comprehensible. The brand strategy — Brian’s straight-talking engineer persona supported by a small, credible team of “techies” — adds a human trust layer that sterile compliance brands lack.

In a market defined by opacity and noise, Transcrypt aims to be the product that simply makes sense: a living compliance companion that earns trust the longer it is used.

### 2.1 Overview of UK SME Cyber and GRC Landscape

The UK’s SME cyber and governance, risk, and compliance (GRC) landscape is defined by contradiction: a national economy increasingly dependent on digital systems, yet serviced by a security market still modelled for enterprises. Small and medium-sized businesses make up 99% of UK private enterprises, yet most lack in-house expertise to interpret, let alone implement, the overlapping frameworks they are expected to comply with. The government’s intent — to raise national resilience through schemes such as Cyber Essentials, NIS, and the incoming NIS2 and DORA regimes — is sound, but its execution leaves SMEs stranded between aspiration and affordability. For most, compliance remains a box-ticking ritual done under duress: an annual scramble to fill out forms for insurers, regulators, or supply-chain primes, without any lasting improvement to their actual defences. This gap between regulation and operational capacity defines the present state of the market.

The supply side of the landscape reflects the same imbalance. Traditional consultancies and managed-service providers dominate, offering compliance as a labour-intensive service with high margins and low transparency. At the lower end such as https://www.e-zu.co.uk/, automated portals have proliferated — platforms that sell quick Cyber Essentials certification or security “health checks” with little substance. Neither approach builds enduring capability. Consultancies depend on recurring audits, while the portals stop short of meaningful interpretation or adaptation to live regulatory change. In the middle ground, there are a few promising entrants — firms such as CyberSmart, Bulletproof, and Drata’s UK integrations — yet even these tend to rely on prescriptive templates rather than the dynamic modelling of real controls and evidence. The result is a fragmented, noisy ecosystem in which small businesses must choose between cost and comprehension, never both.

Government direction and market pressure are converging on the need for something better. The National Cyber Strategy 2022 emphasised “secure by default” and “secure by design,” while the updated Cyber Essentials scheme signals a move toward continuous assurance rather than static compliance. Meanwhile, insurers, primes, and regulators increasingly demand demonstrable, ongoing alignment rather than once-a-year attestations. The conditions are therefore set for a shift: from reactive certification to continuous, data-backed assurance delivered digitally at SME scale. The next generation of platforms must not only simplify compliance but also explain it, bridging the literacy gap that has kept SMEs dependent on consultants. The UK SME cyber and GRC landscape is thus ripe for intelligent disruption — a move away from bureaucracy toward comprehension, from form-filling to evidence-based trust. Transcrypt is designed to inhabit that exact gap: the missing interpreter between government mandate, commercial necessity, and operational reality.

### 2.2 Key Competitors and Differentiation

The key competitors in the UK SME cyber and GRC space can be divided into three broad categories: certification brokers, managed-service hybrids, and enterprise-grade compliance platforms. The certification brokers — notably CyberSmart, IASME, Bulletproof, and Tytan — dominate the low-cost, high-volume end of the market. Their offering revolves around rapid Cyber Essentials accreditation, typically using templated questionnaires and automated scoring engines. They appeal to SMEs wanting a quick certificate for tender eligibility or insurance renewal but do little beyond that point. Their differentiator is speed and price; their weakness is superficiality. Once the certificate is issued, the relationship ends, and the client remains as unprepared as before. For a business seeking ongoing understanding or resilience, these providers are a one-night stand rather than a partner.

The managed-service hybrids — such as Littlefish, Redscan (Kroll), and SureCloud — aim higher. They pair compliance management with outsourced SOC and vulnerability monitoring, bundling Cyber Essentials, ISO 27001, and penetration testing into broader “assurance packages.” They sell continuity but not comprehension: the customer pays for coverage rather than insight. Their recurring revenue model depends on a perception of complexity that keeps the client dependent. These players hold solid market share among mid-tier firms but are too costly, jargon-heavy, and opaque for the smaller organisations that make up the bulk of the UK’s 5.5 million SMEs. Finally, at the top end, platforms like Drata, Vanta, and Tugboat Logic have entered the UK market from the US. Their automation and integrations are impressive but tuned for companies with internal IT and security teams — the very resources most SMEs lack. Their tools are powerful but overbuilt, their language foreign, and their price tags misaligned with UK SME economics.

Transcrypt’s differentiation lies in translation, continuity, and credibility. It does not aim to compete on breadth of frameworks or managed services but on the ability to interpret regulation into human guidance and maintain that mapping over time. Where incumbents sell compliance as an event, Transcrypt treats it as a living state. The product is conceived as a low-overhead, plain-language compliance companion that shows why each control exists and how to evidence it in context. It bridges the gulf between policy and practice, continuously aligning with legislative updates and surfacing changes without user intervention. Its personality — fronted by Brian’s straightforward engineer’s voice and supported by a small, skilled backroom — is its brand advantage: trust built through clarity, not jargon. In a market full of transactional portals and consultant echo chambers, Transcrypt will stand apart by being the one that simply makes sense, costs little, and evolves honestly with the law.

### 2.3 Market Share Estimates and Pricing Models

The UK SME cyber and GRC market is crowded but top-heavy, with a small number of well-funded players commanding the lion’s share of paid certifications and managed compliance revenue. CyberSmart is the largest pure-play competitor in the SME automation tier, estimated to hold roughly 35–40% of the automated Cyber Essentials certification market, driven by its partnerships with insurers (notably Hiscox) and MSPs. Its pricing typically runs from £490–£1,200 per year, depending on whether the SME opts for self-assessment or guided support. Bulletproof occupies a similar bracket, though its business model leans more on bundled penetration testing and consultancy than subscription automation. IASME, which oversees the official Cyber Essentials framework, takes around 10–15% of the certification market directly or through licensed partners. The rest of the field is fragmented among dozens of small service providers — often one- or two-person consultancies operating on razor-thin margins — who issue certificates at cost just to sell follow-on services.

Higher up the value chain, managed-service providers and hybrid firms such as SureCloud, Redscan (Kroll), and Littlefish compete for clients turning over £5–50 million, typically charging £5,000–£20,000 per year for managed compliance and SOC monitoring. These firms combine ISO 27001, Cyber Essentials Plus, and penetration testing into a subscription-like service, but they are far too expensive for the average SME with fewer than fifty employees. Meanwhile, US-origin platforms like Drata and Vanta are only beginning to penetrate the UK market, capturing early adopters in fintech and SaaS, with pricing in the range of £4,000–£12,000 per year depending on automation scope and integrations. Collectively, the UK SME cyber assurance market is valued at roughly £400–£600 million annually, but more than half of that spend goes toward human consultancy, not software. The true digital automation layer for small firms remains underdeveloped — a narrow but fertile space for Transcrypt.

Transcrypt’s pricing strategy is deliberately designed to undercut both consultancy and overbuilt automation without signalling cheapness. The base model would operate on a monthly subscription between £25–£45, scaling by organisation size or compliance tier (Cyber Essentials, NIS2 alignment, etc.). The first revenue goal is modest but concrete: £500 per month net profit by month twelve, achieved through low operational overhead and organic customer acquisition. Pricing will remain transparent, all-inclusive, and jargon-free — no hidden “audit support” or upsells. As the product matures, higher tiers could introduce lightweight integrations (insurer reporting, document verification, supply-chain dashboards) at £75–£150 per month, maintaining simplicity while expanding utility. The long-term intent is to keep Transcrypt’s pricing firmly in the “sustainable self-service” bracket — affordable enough for a single-person business, valuable enough for a 50-person firm, and stable enough to generate predictable income without debt or external funding.


**Supplemental**

Good thinking — yes *and* there are indeed interesting possibilities with decentralised insurance models or blockchain-enabled risk pools that could be leveraged in your offering for Transcrypt Essential. Below is a breakdown of how they might fit, what to watch out for, and some short-list of relevant players.

---

### ✅ Why it could make sense

* There’s a recognised gap in the UK SME cyber insurance market: many SMEs don’t have adequate cyber cover or don’t understand the value. ([GOV.UK][1])
* A decentralised or “embedded” insurance layer aligned with your platform could add value for users (and differentiate Transcrypt) by offering risk transfer tied to the compliance engine.
* Such a feature could reinforce your proposition of *authenticity, clarity, and trust* (since insurance is inherently a trust contract) and also open a revenue extension (partnership/licensing) without your core product needing to become an insurance underwriter.
* If structured smartly, it can enhance retention: if a user sees “we help you certify and we help you insure”, that becomes a stronger proposition than “we help you certify only”.
* It meshes well with “living compliance / continuous assurance” narrative rather than one-time tick-box certification.

---

### ⚠️ What to watch / what needs clear design

* Regulatory complexity: Insurance is heavily regulated (in the UK via Financial Conduct Authority/Prudential Regulation Authority). Embedding an insurance offering may expose Transcrypt to heavier regulatory obligations or licensing if you act as a distributor or underwriter.
* Risk alignment: If you claim “better compliance = lower risk” you’ll need enough credible data (or modelling) to satisfy the insurer’s underwriting or risk pool. Your compliance engine outputs may need to feed insurance eligibility criteria.
* Cost/claim exposure: Even with decentralised models, risk still resides somewhere. If you’re participating in risk-sharing, you’ll want to manage how claims and dispute resolution are handled, how evidence is captured, and how control failures are surfaced and tracked.
* Integration complexity: The user experience must remain simple. If the insurance piece becomes overly heavy or complicated, it may clash with your zero-setup / plain-language tenets.
* Brand and trust: You must ensure any insurance partner is credible — if the scheme fails or claim payments are slow, the brand trust you’re cultivating for Transcrypt could be damaged.

---

### 🔍 Relevant actors / opportunities

* Etherisc: A decentralised insurance firm (blockchain-based) that has developed products in other domains (flight delay, crop) and has UK potential. ([Insurance Business][2])
* Standard cyber insurers / cyber insurance brokers targeting SMEs: There is credible demand for tailored SME cyber cover. Eg. the report “Adoption of cyber insurance by UK SMEs” shows the gap. ([GOV.UK][1])
* Embedded insurance models: Your compliance engine could serve as a “data feed” into an insurance product: e.g., user achieves level X then qualifies for premium reduction or faster quote.
* Blockchain / smart-contract enabled “parametric insurance”: While not mainstream for SMEs yet, some research suggests blockchain models for insurance could reduce cost/complexity. ([arXiv][3])

---

### 🎯 How you might incorporate it into Transcrypt Essential offering

You could propose a “Future Tier” or “Insurance-Ready Tier” in your pricing/roadmap where:

* Once a subscriber completes self-assessment and demonstrates controls at a threshold, they become eligible for **preferred access** to a partner cyber insurance product or a discounted/premia-reduced rate.
* The compliance engine produces an “Assurance Certificate” or “Evidence Bundle” certified by Transcrypt that an insurer accepts as underwriting data (i.e., “you’ve done 80% of the controls, thus your risk is lower”).
* A branded partnership with a decentralised/policy-innovation insurer becomes a co-marketing asset (e.g., “Transcrypt & XYZ insurer: aligned SME cyber protection”).
* Down the line, you use the aggregated anonymised data from many SMEs using Transcrypt to feed risk modelling and improve underwriting/claims handling (this becomes a strategic moat).

---

If you like, I can **scan 5-10 current SME cyber insurance products in the UK** to identify which insurers are offering “embedded” or “platform-aligned” deals and then we can propose *which one(s)* to target for partnership (and the terms to negotiate).

[1]: https://www.gov.uk/government/publications/adoption-of-cyber-insurance-by-uk-small-and-medium-sized-enterprises?utm_source=chatgpt.com "Adoption of cyber insurance by UK small and medium ..."
[2]: https://www.insurancebusinessmag.com/uk/news/technology/uk-fertile-ground-for-innovators-says-blockchain-insurance-firm-87947.aspx?utm_source=chatgpt.com "UK fertile ground for innovators, says blockchain insurance ..."
[3]: https://arxiv.org/abs/2001.05273?utm_source=chatgpt.com "BIS- A Blockchain-based Solution for the Insurance Industry in Smart Cities"


**End Supplemental**


### 2.4 Future Extensibility to Other Nations

Transcrypt’s foundation is deliberately architectural rather than jurisdictional. The initial focus is the UK SME landscape—centred on Cyber Essentials, a standards-based assurance framework rather than a legislative regime. Transcrypt Essential, comprising both the hosted site and the compliance tool, codifies Cyber Essentials controls into structured rulebases, links them to evidence workflows, and renders the guidance in plain human language. That same logic is data-driven, not regulation-bound: each framework is expressed as a dataset that defines requirements, controls, and verification paths.

Because Transcrypt Essential treats frameworks as datasets rather than documents, its model can be configured for any jurisdiction without rebuilding the system. Each assurance or regulatory scheme—whether the EU’s NIS2 or DORA, the US’s CMMC model, or Australia’s Essential Eight—follows the same underlying grammar of obligation, control, and verification. Extensibility is therefore engineered from the start: the same compliance engine can ingest a different rulebase and localisation layer while preserving a consistent user experience and assurance logic.

The first natural expansion path is Europe, where NIS2 and DORA create regulatory convergence across member states. Transcrypt’s rulebase design already mirrors NIS2’s modular structure and emphasis on proportionality, even though Transcrypt Essential itself does not implement NIS2 logic. A multilingual adaptation layer—initially targeting Ireland, the Netherlands, and the Nordics—would enable rapid scaling through localised text and authority references without structural change to the core.

The second phase would target Commonwealth markets such as Canada, Australia, and New Zealand, where cyber regulation shares the same risk-based vocabulary but lacks consistent SME tooling. These regions also share cultural affinity for plain-English communication and pragmatic governance, making Transcrypt’s approachable tone and subscription model directly transferable. By this stage, partnerships with local auditors or insurers could seed market presence without the need for physical offices, using the UK deployment as proof of legitimacy.

In the longer term, extensibility extends beyond geography. The same regulatory graph that maps controls to evidence in one framework can support cross-framework assurance—a single dashboard showing how a firm’s Cyber Essentials compliance posture aligns with equivalent controls in other regimes. This “compliance interoperability” remains outside Transcrypt Essential’s MVP but defines the long-term trajectory: a platform where structured assurance data forms a common language across frameworks and nations. Extensibility, therefore, is not an afterthought but a defining characteristic of both the site and tool architecture, shaping Transcrypt’s technical design and commercial ambition.

### 2.5 Regulatory and Assurance Environment

The regulatory environment shaping UK SME cybersecurity has tightened sharply over the past five years, driven by domestic policy and international alignment. At the practical centre sits Cyber Essentials, a government-endorsed baseline assurance scheme that has evolved from simple self-assessment into a de facto prerequisite for many public-sector contracts and insurance policies. Above it, the Network and Information Systems Regulations (NIS) and forthcoming NIS2 directive introduce obligations for operators of essential and digital services, explicitly extending accountability into their supply chains. That is where SMEs come under direct pressure: even if not “regulated entities,” they must demonstrate good practice to primes that are. The policy tone has shifted from encouragement to expectation—reinforced by sectoral initiatives such as the Digital Operational Resilience Act (DORA) in the EU financial domain and by insurers tightening underwriting criteria around cyber hygiene. Compliance has become a practical precondition for market participation.

This landscape functions as a federated assurance system rather than a unified framework. The National Cyber Security Centre (NCSC) sets strategy but does not regulate; the Department for Science, Innovation and Technology (DSIT) sponsors policy; the Information Commissioner’s Office (ICO) enforces data-protection law; and the IASME Consortium administers Cyber Essentials and acts as a licensed certification body under DSIT oversight. Alongside these formal actors, insurers, auditors, and large enterprises act as shadow regulators by embedding cyber clauses in procurement and underwriting. The result is no single authoritative compliance map. SMEs must navigate overlapping schemes, shifting guidance, and inconsistent auditor interpretation—an ecosystem grown organically rather than engineered, producing friction, duplication, and cost.

The opportunity for Transcrypt arises from this fragmentation. The trend is unmistakable: continuous, evidence-based assurance is replacing static annual attestations; supply-chain accountability is extending obligations beyond regulated entities; and policy attention is turning toward machine-readable compliance as government digitalises oversight. Yet the tooling that operationalises those ambitions at SME scale is absent. Transcrypt’s role is to inhabit that connective layer between legislation, certification, and execution—modelling each control as data, linking it to live evidence sources, and maintaining alignment as frameworks evolve. By doing so, it enables SMEs to respond to regulatory change through configuration rather than reinvention. As the UK aligns more closely with international norms under NIS2 and related initiatives, Transcrypt can act as the interpreter between policy and practice—turning a fragmented regulatory environment into a navigable assurance ecosystem.


<!-- strategic -->
## Tenancy Model (Design Intention)

Transcrypt operates as a multi-tenant system in which each customer instance is logically and cryptographically isolated while sharing a common platform runtime. The tenancy boundary applies across all data types:

* **Structured data** — relational and document data such as rulebases, control mappings, evidence metadata, and user records are held within an isolated schema or database namespace unique to each tenant. No cross-tenant queries or joins are permitted, and backups, restores, and migrations must operate solely within that namespace.

* **Binary evidence** — uploaded artefacts such as PDFs, screenshots, and configuration exports are stored in an object store under a dedicated per-tenant namespace. The tenancy ID is embedded in both the storage path and access policy to prevent cross-tenant enumeration or retrieval. Each object is encrypted at rest, checksummed, and retrievable only through short-lived, signed URLs issued under that tenant’s identity.

The architecture is designed so that, when production readiness is achieved, both the database and binary storage layers can be re-homed to managed services (for example PostgreSQL or S3-compatible object storage) without modification to application logic or tenancy abstraction.

This PRD defines the behavioural requirements—strict tenant isolation, verifiable segregation of structured and binary data, and portability of each storage layer—not the infrastructure method by which those requirements are implemented.

## 3. Product Architecture and Central Platform Design

Transcrypt’s platform is built for separation, assurance, and auditability. Its design is intentionally simple at the edges and tightly structured in the core.

### Edge Layer

The platform has two surface experiences that share a design system and analytics instrumentation but operate on separate trust boundaries:

* **Public site** — the publication and community layer for articles, updates, and social engagement. It is publicly readable, cacheable, and instrumented for discoverability, but it has no path to tenant data.
* **Tenant portal** — the authenticated workspace for customers to manage their assurance activities. It communicates through the API gateway using short-lived credentials and tenant-scoped routes. All user actions terminate at this gateway, which enforces authentication, rate limiting, and routing based on tenant context.

### Central Layer ()

Within the heart of the Transcrypt system, an **evaluation pipeline**, known commercially as Transcrypt Essential, processes tenant-scoped inputs from the gateway. This heart is composed of discrete, bounded services:

* **Evaluation (Rules + LLM)** — runs deterministic rule checks and a runtime LLM assessment against the current Cyber Essentials RulePack. Deterministic checks gate objective pass/fail items; the LLM provides reasoned judgements, gap explanations, and next-step guidance. All evaluations are version-pinned (RulePack ID + model/version + prompt template/hash) and emit audited findings tied to the OrgProfile and Evidence set.
* **Evidence binding** — hashes and records artefacts (files, exports, assertions) and maps them to controls inside the tenant’s isolated namespace; issues short-lived, signed retrieval URLs; preserves integrity and provenance.
* **Report and export** — assembles human-readable reports and machine-readable bundles (JSON/CSV/PDF) with control citations, evidence links, and evaluator notes suitable for assessors or automated ingestion.

Each service has its own identity, credentials, and token-scoped access policy. Inter-service communication is mutually authenticated, signed, and logged so that a fault or compromise cannot propagate beyond its trust boundary.

### Security Model

Security is intrinsic to the design. Every human and machine actor authenticates through short-lived cryptographic credentials issued by the identity service. Authorisation is enforced by policy-as-code, evaluated per request, and scoped to a single tenant. All data in transit is encrypted; internal traffic is accepted only from verified service identities. Every request, job, and data mutation emits an immutable audit event containing timestamp, actor identity, tenant ID, and cryptographic hash of the action. These events form a complete, verifiable audit trail.

#### Audit event schema

Every security-relevant action emits an **Audit Event** recorded in an append-only log. Each event must include:

- `tenant_id`
- `actor_id` (human or service identity)
- `timestamp` (ISO8601 Z)
- `org_profile_hash`
- `evidence_bundle_hash`
- `rulepack_hash`
- `model_version` (LLM or rules model identifier)
- `prompt_version` (template/hash)
- `param_set` (seed, temperature, top_p, max_tokens, etc.)
- `llm_input_hash`
- `llm_output_hash`
- `finding_id` (when an evaluation creates or updates a finding)

Events are immutable; corrections are new events that reference the original `event_id`.

Network paths are segmented and verified—no implicit trust. East–west traffic is constrained, mutually authenticated, and encrypted so the topology itself functions as a living security control. This alignment between internal design and external assurance makes every control demonstrable: evidenceable controls, immutable audit events, and a verifiable security posture.

### Extensibility Model

Extensibility is a design property, not a roadmap item. Framework logic and evidence relationships exist as versioned data objects within the rulebase schema. Adding or updating a framework—whether an assurance scheme such as Cyber Essentials or a regulatory mapping introduced later—requires only new data definitions and metadata, not code modification. External connectors, collectors, or alternative LLMs integrate through defined APIs without altering core modules.

The architecture is data-driven and jurisdiction-agnostic. It begins with the UK Cyber Essentials rulebase but will be able to host any other framework as a dataset through configuration and localisation. Jurisdictional alignment occurs entirely in data, not in code.

### Architectural Summary

Transcrypt is a graph of obligations, controls, and evidence objects bound by identity and policy. Its behaviour is defined by data and enforced by cryptography. The system’s two surfaces—the public content site and the tenant portal—operate independently yet share a consistent trust model and design language. Security, auditability, and portability are first-order properties. Growth, new frameworks, new regions, new delivery environments, requires only new data and configuration, never alteration of core logic.

### Framework Modularity

The compliance layer separates **control logic** from **application logic**. Controls, tests, and question sets are defined as **data-driven schemas**, versioned and loaded from signed configuration bundles known as **RulePacks**. 

This design allows the platform to:

* plug in new assurance or regulatory frameworks by adding schema bundles,
* update existing control logic without redeploying the codebase, and
* map overlapping controls between frameworks (for example, Cyber Essentials v3.2 ↔ NIS2 ↔ ISO 27001).

All mappings are stored in a normalised meta-model so reporting and dashboards stay consistent across **frameworks**, regardless of jurisdiction.

## 3.1 Core Architecture Overview

### 3.1.1 System Overview

Transcrypt Essential runs as a set of isolated processes on a single managed host, secured by strict identity and access controls rather than external orchestration. Each service performs one function — API, evaluation, reporting, storage — and communicates only through authenticated local interfaces. Artefacts such as rulepacks and binaries are signed and verified before use. Network segmentation is logical, enforced through policy and service identity, not through container or cluster boundaries.

The system is designed for reliability through simplicity: fewer moving parts, clear process boundaries, and minimal configuration for the SME user. Everything runs under least privilege and produces verifiable audit trails, but the user experiences only a guided workflow at the surface.

For LLM-assisted evaluations, every assessment stores its full reasoning metadata — ModelVersion, PromptVersion, ParamSet (including temperature/seed), input hashes, 
output hash, and per-finding rationale snippets — so explanations can be shown to the user and the run can be fully replayed for audit purposes.

#### Data Ownership and Sovereignty

Transcrypt’s design separates **data ownership** from **data custody**. Customers remain the legal owners of their information and evidence, while Transcrypt provides the secure infrastructure and processes required to store, process, and protect it.

Each tenant’s data lives within shared infrastructure but inside a clearly bounded namespace secured by encryption and access policy. Encryption keys are managed centrally, scoped per tenant, and rotated automatically; no long-term shared secrets exist.

Authorised Transcrypt engineers can access decrypted tenant data only under controlled conditions — for example, to assist in incident investigation, data recovery, or compliance verification — and such access is both **time-bound and fully auditable**. Every administrative session is logged, reviewed, and tied to a ticketed reason.

Backups and replicas are encrypted at rest and in transit, preserving integrity and continuity while maintaining isolation between tenants.

This model delivers sovereignty through **accountable transparency**, not obscurity: customers can export or delete their data at any time, while Transcrypt guarantees that any operator access is deliberate, justified, and traceable.

#### Automation-First Operating Model

Transcrypt is designed around an **automation-first** principle: routine, repeatable compliance work is performed by software, not by people. Data collection, control evaluation, and report generation are deterministic processes executed without human intervention, ensuring consistency, speed, and evidence integrity.

Human expertise enters only where judgement or assurance adds value—such as certification review or independent validation. Those touchpoints will be introduced later through a controlled **Assisted Tier** that provides secure, auditable collaboration spaces between customers and accredited reviewers. [Post-MVP: 9.4.1 Assisted Tier & Collaboration](#assisted-tier)

Version 1 operates entirely self-serve: all evaluation, reporting, and evidence handling are automated end-to-end. The operating model treats human involvement as an exception pathway, not the default workflow.

#### Invisible Infrastructure Principle

Transcrypt hides operational complexity behind a single guided workflow. Encryption, process isolation, and rule evaluation happen automatically and transparently; users never interact with servers, storage, or configuration. Internal mechanics are explainable but not exposed—every layer exists solely to deliver clarity at the surface. Each architectural choice serves one aim: **fewer steps, clearer guidance, faster assurance**.

**3.1.1.1 Runtime topology (high level)**

* **Edge/UI** → **API Gateway** → **Core Services** (Evaluation, Reporting, Evidence) → **Data Stores** (Rules, Tenants, Artefacts).
* Identity-aware proxy in front of every service; no east–west traffic without mutual auth.

**3.1.1.2 Trust boundaries**

* **Public zone:** Web app + [API gateway](#API-Gateway-&-Policy-Enforcement).

- **App zone**
    
    - **Stateless services (evaluation, reporting, connectors).**

    - **What runs here**
        - **Evaluation:** takes `OrgProfile` + `Evidence` + `RulePack` → produces Findings; writes audit events; calls data zone for reads/writes.
        - **Reporting:** renders Findings → HTML/PDF/JSON; no long-lived state; fetches inputs from data zone.
        - **Connectors:** ingest IdP/backup/EDR/cloud configs → normalize → post into Evidence APIs; queue/worker style, but job state is disposable.

    - **What does *not* run here**
        - No primary databases, object stores, or KMS.
        - No public UI or login endpoints (those terminate at the gateway).
        - No long-term secrets beyond short-lived service credentials.

    - **Why stateless**
        1. **Reliability & scale:** instances can be killed/restarted without data loss.
        2. **Security:** minimal blast radius; secrets live in the data/identity layers.
        3. **Ops simplicity:** blue/green or rolling deploys without drains/migrations.

    - **Data flow**
        1. Browser → **Gateway** (AuthN/AuthZ, rate-limit, audit headers)
        2. Gateway → **Evaluation** (tenant-scoped request)
        3. Evaluation ↔ **Data zone** (read profiles/evidence, write findings/audit)
        4. Gateway → client (status) and/or **Reporting** → PDF/HTML export

    - **Access controls**
        - Gateway-only ingress; no direct public access to services.
        - mTLS between services; per-service identity and least-privilege tokens.
        - Policy-as-code (OPA) decisions enforced per request; everything audited.

- **Data zone**
    
    - **What runs here**
        - **DB:** Postgres (RLS per tenant) for org profiles, findings, reports, audit events.
        - **Object storage:** evidence and artefacts (S3-compatible), content-addressed; per-tenant namespace.
        - **KMS/Secrets:** key management, envelope encryption; vault/secret store; automated rotation.

    - **What does *not* run here**
        - No application logic or rendering.
        - No direct public ingress or UI.

    - **Access controls**
        - Only app-zone services with valid service identity can reach data endpoints.
        - Network isolation (app ↔ data) with strict allow-lists.
        - All mutations emit immutable audit events (tenant, actor, hashes, timestamps).

#### User Tiers and Human Interaction Model

| Tier | Name | Description | Human Involvement |
|:----:|:-----|:-------------|:-----------------|
| v1.0 | Transcrypt Essential | Full self-serve AI automation for SMEs | None |
| v1.5 | Assisted Tier (β) | Optional human review of AI-generated reports via auditor portal | Limited |
| v2.0 | Platform Tier | Integrated marketplace for auditors, consultants, and partners (Not in v1; see §9.2 Partner/Integrator API (v2.0)) | Extensive |

---

### 3.1.2 Transcrypt Components and Interfaces

**3.1.2.1 Web App (Intake & Console)**
Responsibilities: Guided intake, evidence uploads, job/status views, report downloads, billing entry points.
Interfaces: Browser → HTTPS → API Gateway (`/api/*`, REST/JSON). Login via OIDC.

**3.1.2.2 API Gateway & Policy Enforcement**
Responsibilities: Ingress for all client traffic; AuthN (OIDC), AuthZ (OPA/Rego), request signing, rate limiting, audit headers.
Interfaces: `/api/auth/*`, `/api/tenants/*`, `/api/reports/*`, `/api/evidence/*` (REST/JSON).

**3.1.2.3 Findings Engine (Rules + Runtime Inference) Rule Evaluation Service (Deterministic)**
Responsibilities: Load compiled rule artefacts; evaluate applicability/tests; emit findings with provenance. Combines deterministic rule checks with runtime LLM inference to produce per-rule findings and rationale; emits a composite verdict per policy.
Interfaces: `POST /api/evaluations` (body: OrgProfile, EvidenceInventory, rule_pack_id) → Findings JSON; `GET /api/rules/:rule_id/explain`.

**3.1.2.4 LLM Inference (Runtime, Evaluative)**

* Responsibilities: At runtime, interpret tenant submissions against Cyber Essentials. Produce findings with plain-English rationale and control references. Identify uncertainties and gaps. No training or fine-tuning on tenant data, inference only. Deterministic checks still run in the Rule Engine and must corroborate any automatic pass.
* Interfaces: `POST /evaluate/ai` (tenant_id, org_profile_hash, evidence_hashes[], rulepack_hash, model_version, prompt_version, param_set) → Findings JSON {control_id, status, confidence, rationale, references[]}. Emits an audit event with all input hashes and model/prompt/parameter versions for replay.
* Guardrails: Pinned model and prompt versions. Token and PII budgets enforced. Outbound calls restricted to approved endpoints. Full request and response traces stored per finding. Objective checks remain in the Rule Engine and override AI when they conflict.

**3.1.2.5 Evidence Services**
Responsibilities: File ingest, hashing, metadata capture, connector pulls (e.g., IdP exports, backups, EDR). Persistence and retrieval of evidence artefacts.
Interfaces: `POST /api/evidence/files`, `POST /api/evidence/assertions`, connector webhooks; stores to object storage with short-lived signed URLs and Transcrypt-managed per-tenant KMS envelope encryption.

**3.1.2.6 Report Service**
Responsibilities: Assemble findings → prioritisation → PDF/HTML; embed citations and links to evidence.
Interfaces: `POST /api/reports` → report blob; `GET /api/reports/:id`.

**3.1.2.7 Service Identity Proxy**
Responsibilities: Enforce mTLS east–west, apply per-service AuthN/Z (OPA sidecar), manage cert/key rotation.
Interfaces: `/healthz`, `/metrics`, SDS/control-plane for certificate distribution.

**3.1.2.8 Front-End Site / Blog**

* Responsibilities: Marketing surface separate from the app; hosts the onboarding funnel (static content, product pages, CTA into the Web App).
* Interfaces: Public GET endpoints (`/`, `/product`, `/pricing`, `/security`, `/blog/*`, `/contact`) and `POST /api/contact` (rate-limited with hCaptcha/Turnstile). 
* SEO/Discoverability: `sitemap.xml`, `robots.txt`, JSON-LD/OG tags; status and changelog are linked but live in their own sections.

---

### 3.1.3 Data Model (Canonical Contracts)

The following canonical contracts define the minimum JSON structure for core Transcrypt data objects. All objects carry schema identifiers, version tags, and deterministic hashes to enable auditability and forward compatibility. Optional fields are omitted when unknown rather than populated with `null`.

`status ∈ { "pass", "fail", "partial" }`

`priority ∈ {1..5}`, with `1` as highest urgency

`file.type ∈ {"config", "screenshot", "export", "log"}`

`backups.server_schedule ∈ {"daily", "weekly", "none"}`

`time format = ISO8601 (Z)`

**3.1.3.1 OrgProfile (V1)**

```json
{
  "schema": "OrgProfile",
  "version": "1.0",
  "tenant_id": "tn_abc123",
  "company": { "name": "Acme Ltd", "employee_count": 42, "sector": "manufacturing" },
  "it": {
    "idp": "entra_id",
    "email": "m365",
    "endpoints": { "endpoint_count": 120, "edr": "defender" }
  },
  "remote_access": { "vpn_enabled": true },
  "backups": { "server_schedule": "daily", "immutable": false },
  "policies": { "password": "exists", "incident": "exists" },
  "notes": [],
  "observed_at": "2025-11-10T10:00:00Z"
}
```

**3.1.3.2 EvidenceInventory (V1)**

```json
{
  "schema": "EvidenceInventory",
  "version": "1.0",
  "tenant_id": "tn_abc123",
  "files": [
    {
      "file_id": "evf_001",
      "name": "idp_policy.json",
      "type": "config",
      "mime": "application/json",
      "size_bytes": 18342,
      "sha256": "…",
      "captured_at": "2025-11-10T09:58:21Z",
      "source": "user_upload",
      "signed_url": { "expires_at": "2025-11-10T10:28:21Z" },
      "retention_class": "1y",
      "control_refs": [
        { "framework": "CE", "version": "3.2", "section": "AC.1.1" }
      ]
    }
  ],
  "assertions": [
    {
      "assertion_id": "ast_001",
      "key": "mfa.enforced.admins",
      "type": "boolean",
      "value": true,
      "source_file_id": "evf_001",
      "source_type": "file_ref",
      "observed_at": "2025-11-10T09:58:21Z"
    }
  ]
}
```

**3.1.3.3 Rule (compiled) (V1)**

```json
{
  "schema": "Rule",
  "version": "1.0",
  "rule_id": "CE-AC-001",
  "title": "MFA for admin accounts",
  "applicability": { "if": ["ORG.it.idp != null"] },
  "test": { "all": [ { "equals": ["ASSERT.mfa.enforced.admins", true] } ] },
  "evidence_ids": ["evf_001"],
  "citations": [
    { "framework": "CE", "version": "3.2", "section": "AC.1.1" }
  ],
  "equivalents": [
    { "framework": "ISO27001", "clause": "A.5.17" }
  ],
  "rule_pack_hash": "sha256:…"
}
```

**3.1.3.4 Finding (V1)**

```json
{
  "schema": "Finding",
  "version": "1.0",
  "tenant_id": "tn_abc123",
  "finding_id": "find_001",
  "rule_id": "CE-AC-001",
  "status": "pass",
  "priority": 1,
  "reason": "Exact test result…",
  "evidence_ids": ["evf_001"],
  "citations": [
    { "framework": "CE", "version": "3.2", "section": "AC.1.1" }
  ],
  "provenance": {
    "rule_pack_hash": "sha256:…",
    "org_profile_hash": "sha256:…",
    "evidence_inventory_hash": "sha256:…",
    "evaluated_at": "2025-11-10T10:01:02Z",
    "evaluator_version": "v1.0"
  }
}
```

**3.1.3.5 Report (envelope) (V1)**

```json
{
  "schema": "Report",
  "version": "1.0",
  "tenant_id": "tn_abc123",
  "report_id": "rpt_001",
  "generated_at": "2025-11-10T10:02:33Z",
  "summary": "…",
  "top_actions": ["…", "…"],
  "finding_ids": ["find_001", "find_002"],
  "artefact_hash": "sha256:…",
  "provenance": {
    "rule_pack_hash": "sha256:…",
    "org_profile_hash": "sha256:…",
    "evidence_inventory_hash": "sha256:…",
    "evaluated_at": "2025-11-10T10:01:02Z",
    "evaluator_version": "v1.0",
    "report_signature": "sig:…",
    "signing_key_id": "key_001"
  }
}
```

### 3.1.4 Storage and Artefacts

**3.1.4.1 Tenant DB (Postgres)**

* Tables: `tenants`, `users`, `org_profiles`, `findings`, `reports`, `audit_events`.
* JSONB for profiles/findings; row-level security per tenant.

**3.1.4.2 Object Storage (Artefacts & Evidence)**

* Buckets: `rule-artefacts/` (immutable, hash-addressed), `evidence/tenant-id/`.
* Server-side encryption + per-object metadata (hash, uploader, rule links).

**3.1.4.3 Artefact Registry**

* Compiled RulePacks indexed by SHA-256; manifest lists versions, diffs, effective dates.

---

### 3.1.5 Security, Privacy, and Trust Model

**3.1.5.1 Identity & Access**

* **OIDC login (MFA enforced)**
  Users sign in through a standard identity provider using OpenID Connect. Think Entra ID, Okta, Google. After username and password, they must pass a second step (app code, hardware key, or SMS) every time policy says so.

* **Short-lived JWTs**
  After login, the app issues a JSON Web Token that proves who the user is and what tenant they belong to. It expires quickly, e.g. 15–30 minutes, and is refreshed with a secure refresh flow. Short life limits damage if a token leaks.

* **Service identities via mTLS**
  Backend services do not use user tokens to talk to each other. Each service has its own identity proved by mutual TLS. Both client and server present certificates. Only named services with valid certs can connect.

* **Policy-as-code (OPA) for AuthZ**
  Authorisation decisions are not hardcoded in the app. They are written as Rego policies and evaluated by Open Policy Agent. Every request is checked against rules like “role X in tenant Y can read finding Z”.

#### Why this combo

* OIDC centralises user auth and MFA. Easy SSO, easy revocation.
* Short-lived JWTs reduce blast radius and make session theft harder.
* mTLS gives a strong, automatic trust boundary between services.
* OPA gives consistent, auditable, testable permission checks.

#### How the flow works

1. User hits the app. Redirect to IdP. Complete MFA.
2. App receives OIDC code, trades it for IdP tokens, then creates a short-lived app JWT with claims like `sub`, `tenant_id`, `roles`, `scopes`.
3. Browser sends the JWT to the API Gateway. Gateway validates signature and expiry, adds audit headers.
4. Gateway calls backend services over mTLS. No public ports on services.
5. For each request, the service asks OPA, passing input like `{ method, path, user.roles, tenant_id, resource.owner }`.
6. OPA returns allow or deny. If allow, the service proceeds. All steps are logged.

#### What to implement

* **IdP**: Configure an OIDC client. Enforce MFA at the IdP.
* **JWT**: Sign with your own key pair. Set exp short. Issue refresh tokens with tight scope and rotation.
* **Gateway**: Validate JWTs, inject `X-Tenant-Id` and `X-Request-Id`. Rate limit.
* **mTLS**: Per-service certs, automatic rotation. Only allow-list known cert subjects.
* **OPA**: Sidecar or local daemon. Define Rego for tenant isolation, roles, and resource ownership. Unit test policies.
* **Audit**: Log `tenant_id`, `actor_id`, `timestamp`, decision, and trace ID for every request.

#### Pitfalls to avoid

* Long-lived tokens. Keep access tokens short and refresh tightly controlled.
* Mixing user JWTs for service-to-service calls. Use mTLS service identities instead.
* Ad-hoc permissions in code. Centralise in OPA or you will drift.
* Skipping audience and issuer checks on JWTs. Validate `iss`, `aud`, `nbf`, `exp`, and signature every time.
* No rotation. Rotate JWT signing keys and service certs on a schedule.


**3.1.5.2 Crypto & Secrets**

**Goals:** Confidentiality, integrity, forward-secrecy, and verifiable provenance with boring, proven primitives.

**In transit (everywhere):**

* **TLS 1.3** with ECDHE for forward secrecy; restrict ciphers to modern AEAD suites.
* **mTLS service-to-service** (Envoy or equivalent): each service presents a short-lived client cert; requests without a valid cert are dropped before app code.
* **Strict transport:** HSTS (preload), TLS only; no plaintext ports open; HTTP→HTTPS redirect at the edge.

**At rest (data, artefacts, backups):**

* **Database (Postgres):** tablespace encryption using **AES-256-GCM** (disk or managed volume) plus **column-level encryption** for sensitive JSONB fields where feasible.
* **Object storage (evidence, reports, RulePacks):** **envelope encryption**:

  * Generate a per-object **DEK** (AES-256-GCM).
  * Encrypt data with DEK client-side; store ciphertext + `aad` (tenant_id, object_id, hash).
  * Wrap DEK with a tenant-scoped **KEK** from KMS; store wrapped DEK alongside the object.
  * Persist **SHA-256** of plaintext as integrity tag in object metadata.
* **Backups/WAL archives:** encrypted before leaving the host; KEKs never co-reside with backup files; verify restore with checksum on a schedule.

**Keys & rotation model:**

* **Hierarchy:** root key (KMS) → tenant **KEKs** → per-object **DEKs**.
* **Rotation:** KEKs rotated **quarterly** or on suspicion/incident; DEKs are one-time per object (rotate by re-encrypt on replace).
* **Separation of duties:** only the KMS/Transit service can unwrap KEKs; app never sees root keys.
* **Deletion:** object delete = delete ciphertext + wrapped DEK; KEK rotation with old KEK destroyed enforces crypto-shred for any missed artefacts.

**Secrets management (runtime):**

* **Vault (or equivalent) as the source of truth**:

  * App secrets (DB creds, API keys) are leased, **short-lived**, auto-rotated.
  * **Dynamic secrets** for Postgres/Redis: per-service ephemeral DB users issued by Vault DB engine with TTLs.
  * **Transit engine** (or cloud KMS) for sign/verify and encrypt/decrypt; app asks Transit to operate on blobs, keys never leave the boundary.
* **Bootstrap:** one machine-identity token per node via cloud-init/user-data; everything else derived via authenticated join.
* **No secrets in images, repos, or env files**; use tmpfs + file descriptors; redact in logs.

**Hashing, signing, and provenance:**

* **Content addressing:** all artefacts (RulePacks, reports, evidence bundles) carry a **SHA-256** content hash; the hash appears in audit events and report footers.
* **Signatures:** release images, RulePacks, and PDFs are signed (sigstore/cosign for images; detached signatures for files). Verification is a gate before use.
* **Audit linkage:** each evaluation stores `org_profile_hash`, `evidence_bundle_hash`, `rulepack_hash`, `llm_input_hash`, `llm_output_hash` (when used) + model/prompt/param versions.

**Certificates & identities:**

* **Service identity:** per-service SPIFFE-like IDs or mTLS SANs; certs issued by an internal CA with **24–72h** lifetimes; automated renewal via SDS/sidecar.
* **User identity:** OIDC (Auth0/Entra/Google). **MFA enforced** on admin roles; step-up auth for sensitive actions (e.g., deleting evidence, rotating keys).

**Operational rules (non-negotiable):**

* **Least privilege everywhere:** RLS per tenant in Postgres; object store policies scoped to tenant prefixes; KMS policies scoped to tenant KEKs.
* **No external egress from app zone** except: OIDC, billing webhooks, and (optionally) LLM inference endpoints listed in an allow-list.
* **Key compromise playbook:** revoke certs, rotate KEKs, invalidate tokens, force re-login, re-sign RulePack manifest, re-issue report signatures; document as an RCA artefact.

**DigitalOcean MVP specifics:**

* **KMS:** DO has no native KMS. Use **Vault (Transit engine)** on the app host (or a small dedicated node) for KEKs and signing. Protect Vault unseal with **Shamir**; keep unseal keys off-box.
* **Object storage:** DO Spaces; perform **client-side envelope encryption** as above; treat Spaces SSE as an extra layer, not the only control.
* **DB volume:** encrypt the block device (e.g., LUKS) if you control the host; still encrypt sensitive columns in-app.
* **Certs:** run Envoy or HAProxy with mTLS between services; automate cert issuance/rotation via small control plane or Vault PKI.

**Parameters & defaults (sane, explicit):**

* AES mode: **AES-256-GCM** only (no CBC).
* Hash: **SHA-256** (no MD5/SHA-1).
* TLS: TLSv1.3 only; disable TLSv1.2 unless a third-party absolutely requires it.
* Token lifetime: access tokens ≤ **15 min**; refresh tokens with rotation; service certs ≤ **72 h**.
* Vault lease TTLs: **60 min** default for dynamic DB creds; renewals handled by sidecars.

**Testing & verification:**

* **Crypto unit tests:** encrypt→decrypt round-trips with AAD; tamper tests must fail.
* **Key rotation drills:** quarterly KEK rotation in staging with data intact; restore drills validate backup decryption.
* **Supply chain:** signed builds, SBOMs generated; rejects unsigned images or modified artefacts at startup.

---

**3.1.5.3 Network & Isolation**

* Segmented VPC/VNet: public (edge), app (services), data (DB/KMS). Only proxy reaches app; only app reaches data.

**3.1.5.4 Privacy**

* Data minimisation, per-tenant isolation, GDPR DSR endpoints (export/delete), redaction pipeline for AI prompts (build-time only).

**3.1.5.5 Audit & Observability**

* Structured logs with tenant/request IDs; immutable audit trail (write-once store); traces/metrics with SLO alerts.

---

### 3.1.6 Extensibility & Integration Framework

**3.1.6.1 Framework Packs**

* Portable rule/evidence packs for Cyber Essentials v3.2, NIS2, ISO 27001; locale text separated; hot-swappable by `rule_pack_id`.

**3.1.6.2 Connectors**

* Pullers for IdP (Entra/Okta), cloud config (AWS/Azure/GCP), EDR/backup. Sandbox SDK for partners.

**3.1.6.3 Export/Interchange**

* JSON/JSON-LD exports; webhooks; optional verifiable credentials for “proof of control” attestations.

---

### 3.1.7 DevEx, QA, and Delivery

**3.1.7.1 CI/CD**

* Signed commits; SCA/linters/tests as gates; image signing; SLSA-style provenance attestations.

**3.1.7.2 Testing**

* Unit: rule evaluation; Integration: auth/report flows; E2E: “intake→report” happy path; Golden files for LLM copy.

**3.1.7.3 Environments**

* `dev` (ephemeral PR envs), `staging` (prod-like), `prod` (IaC controlled). No direct human access to prod DB.

---

### 3.1.8 Minimal Viable Slice (MVP cut)

* **Includes:** Essential Plan only; 15 Cyber Essentials v3.2 controls; OrgProfile/Evidence schemas; `/evaluate` + `/reports/generate`; Stripe billing; evidence uploads.
* **Excludes (stubbed):** NIS2 pack, partner APIs, advanced connectors, VC attestations.

---

### 3.1.9 Technology Choices (initial)

* **Frontend:** Next.js + Tailwind; OIDC client.
* **Backend:** Python (FastAPI) for API/Evaluation; Celery/Redis for async; Jinja2 + WeasyPrint for PDF.
* **Data:** Postgres (JSONB); S3-compatible object store; Vault; OPA sidecar; OpenTelemetry.
* **IaC:** Terraform; container runtime; identity-aware proxy (e.g., oauth2-proxy/Envoy).

---

### 3.1.10 Operational Runbooks (high level)

* **Onboard tenant:** create tenant → OIDC bind → rule pack select → intake link.
* **Rotate keys:** trigger KMS rotation → restart sidecars → verify mTLS → attest.
* **Incident:** declare → capture state → contain → RCA → publish improvement.

### 3.x Technical Constraints & Conventions (non-normative)

These conventions define baseline implementation expectations for the MVP but do not lock in deployment architecture.

**Styling**  
**App UI:** **TailwindCSS**.  
**Brand tokens:** Single source of truth via **CSS variables** (colour, radius, shadow, spacing). Variables are consumed by Tailwind (through arbitrary `[...]` utilities and mapped theme entries) and by SCSS on the marketing site.  
**Marketing site:** SCSS that reads the same CSS variables. **No Bootstrap. No icon webfonts.**

Rules:
1) Utilities-first in components; use `@apply` only for tiny atoms (e.g., `.btn`, `.card`), not page layouts.  
2) State via `group/peer/aria/data` variants; avoid deep selectors and descendant overrides.  
3) Dark mode: `media` (prefers-color-scheme) for v1; tokens must be dual-mode.  
4) Icons: lucide-react (SVG). If FA is ever required, use tree-shaken SVG, feature-flagged.  
5) Component API: prefer composition (props) or a variants helper (e.g., `cva`) over custom CSS hierarchies.

**Database Engine**  
The product uses **PostgreSQL (v15 or higher)** as the primary datastore.  
- Required recovery objectives: RPO ≤ 24h, RTO ≤ 4h.  
- Backups must be encrypted and retained for a minimum of 30 days.  
- Deployment topology (local vs managed instance) is defined separately in system design and **ADR-0007: Database Topology for MVP**.

### 3.2 Core Components and Interfaces

All user interaction occurs through the Transcrypt web platform, which unifies public, tenant, and administrative interfaces.

#### 3.2.1 Web App (Next.js @ `https://transcrypt.xyz`)

* **Purpose:** Guided intake, evidence uploads, posture dashboard, report generation/download, billing.
* **Key routes:**

  * **Marketing:** `/`, `/product`, `/pricing`, `/about`, `/contact`, `/blog/*`, `/changelog`, `/status`, `/roadmap` (optional).
  * **Legal & trust:** `/privacy` → alias to `/legal/privacy`, `/terms` → `/legal/terms`, `/cookies` → `/legal/cookies`, `/dpa`, `/subprocessors`, `/acceptable-use`, `/accessibility`, `/licenses`, `/security`.
  * **App (auth-gated):** `/app/*` – intake `/app/intake/*`, evidence `/app/evidence`, reports `/app/reports/*`, settings `/app/settings`.
  * **Developer (future):** `/developers`, `/docs/api`, `/webhooks` (catalogue).
* **Auth/session:** OIDC (Entra/Okta/Google) via next-auth; short-lived JWT session (`SameSite=Lax`, `Secure`, `HttpOnly`); step-up MFA for admin actions.
* **Interfaces:** HTTPS → `/api/*` (REST/JSON with zod validation). Tenant context from session claim; optional deep links `/t/:tenant/*`.

#### 3.2.2 API Gateway & Policy Enforcement {#API-Gateway-&-Policy-Enforcement}

* **Purpose:** Single ingress for all APIs; central AuthN/AuthZ, rate limiting, audit headers.
* **Responsibilities:** Verify OIDC tokens; attach `X-Tenant-Id`, `X-Request-Id`, `X-Audit-Actor`; enforce **policy-as-code** (OPA/Rego); terminate TLS; mTLS to internal services.
* **Interfaces:**

  * Auth: `POST /api/auth/callback`, `POST /api/auth/logout`.
  * Tenant: `GET /api/tenants/me`, `POST /api/tenants/switch`.
  * Health: `GET /api/healthz` (unauthenticated ping), `GET /api/readyz` (auth, deeper checks).

#### 3.2.3 Rule Evaluation Service (Deterministic + Runtime Inference)

* **Purpose:** Evaluate a tenant’s controls against an **immutable, signed RulePack** using a **composite engine**: deterministic checks for objective controls, plus **runtime LLM inference (inference-only, no training/fine-tuning)** for interpretive text and evidence mapping. Enforces automation thresholds and evidence schema defined in [§6.2 Cyber Essentials Alignment (v3.2)](#62-cyber-essentials-alignment-v32).

* **Interfaces:**

  * `POST /api/evaluate`
    **Request:**

    ```json
    {
      "rule_pack": "CE-2025.3#sha256:<digest>",
      "org_profile": { ... },
      "evidence": { ... },
      "model_version": "llm:vendor:model@rev"   // required when inference paths are enabled
    }
    ```

    **Response:**

    ```json
    {
      "findings": [
        {
          "rule_id": "...",
          "status": "pass|fail|partial",
          "reason": "...",                       // human-readable rationale
          "evidence": [ ... ],                   // bound artefact refs
          "citations": [ ... ],                  // CE clause refs
          "components": {
            "deterministic": { "tests": [ ... ], "verdict": "pass|fail|partial" },
            "ai": { "enabled": true, "verdict": "pass|fail|partial", "model_version": "..." }
          }
        }
      ],
      "artefact_hash": "...",                    // content-addressed bundle of inputs
      "rulepack_hash": "sha256:<digest>"
    }
    ```
  * `GET /api/evaluate/explain/:rule_id` → returns provenance (inputs, tests run, prompts used for that rule’s inference path if applicable, model version, citations).

* **Notes:**

  * **Stateless** service; **loads RulePacks by hash**.
  * **Runtime LLM is inference-only** (no training, no fine-tuning, no external data egress beyond inference).
  * **Deterministic gates** always run; the **final status is a composite** of deterministic checks and AI rationale, per rule policy.
  * **Reproducibility:** same `org_profile` + `evidence` + `rulepack_hash` + `model_version` ⇒ same findings; mismatch triggers rejection and audit log.
  * Emits findings decorated with `ce_ref` identifiers and renewal flags for 14-day vulnerability management, MFA, passwords, device lockout, and software-support rules per [§6.2](#62-cyber-essentials-alignment-v32).

#### 3.2.4 LLM Assist Pipeline (Build-Time Only)

Purpose: Draft rule objects from clauses; suggest cross-framework equivalences; produce human-readable summaries/diffs. Outputs become signed RulePack artefacts.

Interfaces (CLI/worker):
• rules draft <source.pdf> → rules/*.json (schema-conformant, citations required)
• rules diff <old> <new> → diff.json + CHANGELOG.md

Guardrails: JSON Schema validation; missing citations = build fail; human review before publish. No authoring pipeline calls occur during tenant assessments; runtime inference is handled by the Evaluation Service (§3.2.3).

#### 3.2.5 Evidence Services

* **Purpose:** Ingest and index evidence (files + assertions) with integrity metadata, never orphaned from rules.
* **Interfaces:**

  * `POST /api/evidence/files` (multipart) → `{ id, sha256, url }`.
  * `POST /api/evidence/assertions` → `{ key:"MFA.enforced.admins", value:true, source:"idp_policy.json" }`.
  * Connectors (optional webhooks): `/api/connectors/idp`, `/api/connectors/backup`, `/api/connectors/edr`.
* **Storage contract:** Client-side encrypted artefacts (app uses Transcrypt-managed per-tenant KMS keys) are double-wrapped with server-side encryption (SSE) in an S3-compatible store `evidence/{tenant}/{uuid}`; isolated workers decrypt via per-tenant KMS unwrap; signed URLs deliver the already-encrypted blobs. Postgres metadata preserves `ce_ref` tags and scope annotations required for Cyber Essentials v3.2 exports described in [§6.2](#62-cyber-essentials-alignment-v32).

#### 3.2.6 Report Service

* **Purpose:** Convert findings → prioritised actions → **HTML/PDF** with embedded citations and artefact hash.
* **Interfaces:**

  * `POST /api/reports` → `{ report_id, download_url, summary }`.
  * `GET /api/reports/:id` → full envelope (exec summary, top actions, findings, citations).
* **Rendering:** Jinja2 → HTML → WeasyPrint PDF; SHA-256 of inputs stamped in footer.

#### 3.2.7 Admin Console (Internal)

* **Purpose:** RulePack lifecycle, sandbox what-if evaluations, release approvals.
* **Interfaces:**

  * `POST /api/admin/rulepacks/publish`, `GET /api/admin/rulepacks/:hash`.
  * `POST /api/admin/evaluate/simulate` with synthetic OrgProfile/Evidence.

#### 3.2.8 Data Stores & Artefacts (Interface Contracts)

* **Postgres (RLS per tenant):** `tenants`, `users`, `org_profiles(jsonb)`, `evidence_index`, `findings(jsonb)`, `reports`, `audit_events`.
* **Artefact Registry (immutable):** `rulepacks/{hash}.json`, `manifest.json`, `diffs/{from}-{to}.json`.
* **Schemas:** All payloads carry `"schema": "OrgProfileV1" | "EvidenceV1" | "FindingsV1"` for fwd/back compat.

#### 3.2.9 Observability & Audit

* **Purpose:** End-to-end traceability for support and assurance.
* **Interfaces:** OpenTelemetry export (`/otel/v1/*`); structured logs include `tenant_id`, `rule_pack_hash`, `trace_id`; append-only `audit_events` via write-only API from gateway/services.
* **User-visible:** `/app/settings/audit` — filterable per-tenant audit viewer.

#### 3.2.10 Public Site & Content (Marketing, Legal, Support)

* **Primary public routes:**

  * Marketing: `/`, `/product`, `/pricing`, `/about`, `/contact`, `/blog/*`, `/changelog`, `/status`, `/roadmap` (optional).
  * Legal & trust: `/legal/*` with **aliases** `/privacy`, `/terms`, `/cookies`; plus `/dpa`, `/subprocessors`, `/acceptable-use`, `/accessibility`, `/licenses`, `/security`.
  * Support: `/support` (FAQ hub), `/dsr` (Data Subject Requests portal/form).
* **Contact endpoint:** `POST /api/contact` → `{ name, email, subject, message, consent, meta }` (hCaptcha/Turnstile, rate-limited, ack with `ticket_id`).
* **SEO/Discoverability:** `sitemap.xml`, `robots.txt`, JSON-LD, OG/Twitter cards, RSS for blog.

#### 3.2.11 External Integrations (First-Party)

* **Identity Providers:** OIDC flows at `/api/auth/*`.
* **Billing:** Stripe Checkout; webhook `POST /api/billing/webhook` (subscription create/update/cancel).
* **Email (later):** transactional mail; SPF/DKIM/DMARC configured for `transcrypt.xyz`.
* **Well-known:** `/.well-known/security.txt`, `/.well-known/change-password`.

#### 3.2.12 Non-Functional Interface Contracts

* **Security headers:** CSP (nonce’d), HSTS (preload), Referrer-Policy `strict-origin-when-cross-origin`, X-Frame-Options `DENY`, X-Content-Type-Options `nosniff`.
* **Auth requirements:** All `/api/*` require valid JWT with `sub`, `tenant_id`, `scopes`; machine calls use mTLS + token.
* **Rate limits:** Per-IP + per-tenant; stricter on `/api/auth/*`, `/api/evidence/files`, `/api/contact`.
* **Error model:** Problem+JSON → `{ "type": "https://transcrypt.xyz/errors/<code>", "title": "...", "status": 400, "detail": "...", "trace_id": "..." }`.

### 3.3 Security, Privacy, and Trust Model

Transcrypt treats **identity as the perimeter** and **evidence as the arbiter of trust**. Every human and machine action is authenticated (OIDC for users, mTLS for services), authorised by **policy-as-code** (OPA/Rego), and logged with immutable metadata (tenant, actor, rule pack, trace ID). Network paths are **zero-trust by default**: no implicit east–west access, service meshes enforce mutual TLS, and privileges are created just-in-time and discarded immediately after use. Data is encrypted **in transit (TLS 1.3/PFS)** and **at rest (AES-256-GCM)** with keys managed and rotated by a KMS; secrets are injected at runtime via a vault and never committed to source. Runtime environments are ephemeral and reproducible; builds are signed and accompanied by SBOMs and SLSA-style provenance so that what runs can be traced back to who approved it and which inputs it contained. The result is a platform where security isn’t a bolted-on checklist but a property of the topology, the pipeline, and the artefacts.

Privacy is engineered as **data minimisation, isolation, and control**. Tenants are logically isolated (row-level security on Postgres plus per-tenant object-store prefixes), and the app collects only what’s needed to evaluate controls and generate reports. Evidence is never “loose”: every file or assertion is bound to a control, version, and citation, with hashes and timestamps for provenance. Users own their data; Transcrypt is a processor under UK GDPR. The platform exposes **self-service Data Subject Rights** (export/delete) and publishes clear retention schedules; AI prompts are minimised and redacted, and runtime LLM inference is confined to the Evaluation/Findings path with pinned model/prompt/parameter versions and full audit capture. Legal pages (Privacy, DPA, Sub-processors) are versioned in the repo; changes are diffable and linked from the site. Cookie/telemetry loading respects explicit consent, and analytics run in a privacy-preserving mode with PII excluded by design.

Trust is made observable through **transparent operations and verifiable assurances**. A public status page, changelog, and governance notes show uptime, incidents, and remediation; `/.well-known/security.txt` advertises a responsible disclosure path and optional PGP key. Incident response follows a time-boxed playbook (detect → contain → eradicate → recover → RCA), and every RCA is a signed artefact linked to the code/config changes it triggered. Continuous testing covers security (dependency and container scans), functionality (unit/integration/E2E), and drift (policy and posture checks); failed gates block release. Where standards matter, the platform maps directly to **Cyber Essentials** hygiene, **ISO 27001** governance, **NIS/NIS2** resilience, and **IEC 62443** zone/conduit separation—so controls aren’t just present, they are **explainable** in the language auditors use. In short: authenticate everything, authorise least, encrypt always, minimise data, and prove it—with artefacts anyone qualified can inspect.

### 3.4 Extensibility and Integration Framework

Transcrypt is designed to grow **by data, not by rewrite**. The core engine treats frameworks, controls, and evidence definitions as portable **RulePacks**—signed JSON artefacts that the runtime loads by hash. Adding NIS2, DORA, or ISO 27001 doesn’t change code paths: you publish a new RulePack with mapped controls, equivalence links, and test clauses; the evaluation service remains deterministic. Textual outputs (headings, rationales, actions) live as locale bundles, so jurisdictional expansion is translation work, not refactoring. Report rendering is a themeable template layer (HTML → PDF) that reads the same Findings schema, allowing new formats or styles without touching evaluation logic.

Integration follows a **connector + event** model. Connectors are small, sandboxed pullers/posters that transform external proofs (IdP exports, backup configs, EDR posture, cloud config snapshots) into **EvidenceInventory** assertions or file artefacts. They run out-of-band via jobs/queues, publish to the evidence API, and never gain direct DB write access. Events from the core—`report.generated`, `finding.changed`, `evidence.added`—are emitted to webhooks with signed payloads, enabling MSP dashboards, insurer ingestion, or customer SIEM correlation. Post-MVP, a curated **Partner API** exposes read-scoped endpoints (tenant roll-ups, findings, reports) for contracted collaborators with strict RBAC, pagination, and approval workflows—an API-level integration surface for customers and approved partners only. Not in v1; see §9.2 Partner/Integrator API (v2.0). [[Post-MVP: §9.4.2 Partner Channel & Co-Branding]] Exports continue to use open, durable formats (JSON/JSON-LD) so downstream systems can store or rehydrate results without vendor lock-in.

Extensibility is governed by **versioned contracts** and forward-compat rules. Every payload carries a `schema` tag (e.g., `OrgProfileV1`, `EvidenceV1`, `FindingsV1`); minor releases add optional fields, major releases ship with a migration manifest and deprecation window. RulePacks and templates are immutable by content hash; new revisions publish as new artefacts with a machine-readable `diff.json` so partners can pre-compute the impact of framework updates. SDKs (lightweight) provide typed models, request builders, webhook verifiers, and a connector scaffold (auth, polling, backoff, signing). LLM use remains a **build-time extension point** only—providers are pluggable, prompts redacted, outputs schema-validated—so runtime determinism and auditability never depend on a model vendor. In combination, RulePacks, connectors, events, and stable schemas make the platform easy to extend, safe to integrate, and boring to operate—the exact temperament you want in compliance infrastructure.

### 3.5 Technical Stack and Dependencies

**Frontend**

* **Framework:** Next.js (App Router) + React. **Styling:** TailwindCSS for app UI, **SCSS tokens** for brand theming/marketing (Dart Sass). Tokens exposed as CSS variables and consumed by Tailwind (single source of truth). Tailwind theme reads the shared tokens—no duplicated hex values in source.
* **Typography & Icons:** System UI stack for the app; one **self-hosted variable font** (marketing) via `next/font` with tight subsetting. **lucide-react** SVG icons. **No Bootstrap. No icon webfonts.** If Font Awesome is ever required, use tree-shaken SVG packages behind a feature flag.
* **Forms/validation:** Zod + React Hook Form. **State:** server actions + URL state; no global store unless needed.
* **Rendering & content:** MDX/Markdown for marketing/legal/blog; ISR for `/blog` and docs; `next/image` + CDN for assets.
* **Testing:** Playwright (E2E), Vitest/RTL (unit).
* **Telemetry:** OpenTelemetry web SDK → OTEL collector; privacy-first analytics loaded **after consent**.
* **Security headers:** CSP (nonces), HSTS (preload), Referrer-Policy `strict-origin-when-cross-origin`, XFO `DENY`, XCTO `nosniff`.

**Backend & Services**

* **API:** Python **FastAPI** (typed, async) behind an identity-aware proxy (Envoy or oauth2-proxy).
* **Background jobs:** Celery + Redis for report generation, evidence processing, PDF renders.
* **Report rendering:** Jinja2 → HTML → **WeasyPrint** (wkhtmltopdf fallback).
* **Policy/authorisation:** **Open Policy Agent (OPA)** sidecar; Rego policies versioned with code.
* **Rule engine:** Deterministic evaluator reading **RulePacks** (signed JSON loaded by content hash).
* **LLM assist (build-time only):** Provider-pluggable (OpenAI-compatible or local) via offline workers; outputs schema-validated; **never** in the runtime path.
* **Observability:** OpenTelemetry (traces/metrics/logs) → OTEL Collector → Tempo/Loki/Prometheus (or vendor).
* **Notifications:** SMTP provider (later) with SPF/DKIM/DMARC on `transcrypt.xyz`.

**Data & Storage**

* **Primary DB:** **Postgres 15+ (local instance on the app server)** with RLS per tenant; JSONB for OrgProfile/Findings; migrations via Alembic. Listen on `127.0.0.1`; pool with **pgBouncer**; PITR enabled.
* **Object storage:** S3-compatible bucket(s) for evidence/artefacts; server-side encryption; signed URLs.
* **Artefact registry:** Immutable RulePacks (`rulepacks/{sha256}.json`), manifests, diffs; addressed by content hash.
* **Secrets & keys:** **Vault** (or cloud KMS + Secrets Manager) for app secrets; KMS-managed KEKs; automated rotation.
* **Caching:** Redis (ephemeral) for queue/session where necessary; avoid caching sensitive payloads.
* **Backups & DR:** Daily encrypted DB snapshots + WAL archiving; object-store versioning; **quarterly restore drills** into staging with checksum verification.

**Security & Supply Chain**

* **Crypto:** TLS 1.3 everywhere; mTLS service-to-service; AES-256-GCM at rest; FIPS-aligned libraries.
* **Identity:** OIDC for users; mTLS (SPIFFE/SPIRE later if needed) for service identity.
* **Build & provenance:** Containerised builds; **SLSA-style** attestations; image signing with **cosign/sigstore**; SBOMs (**CycloneDX/SPDX**) per release.
* **Scanning:** SCA (Dependabot + **Trivy**/**Snyk**), container scans in CI, IaC scans (tfsec/Checkov).
* **Policies as gates:** CI enforces tests, lint, type checks, SCA, licence policy, OPA packs; rejects unsigned commits/images.

**Infrastructure & Delivery**

* **Runtime:** Start simple—single VM (reverse proxy + API + workers + local Postgres) with systemd; graduate to orchestrator/managed K8s only when partner/API scale demands it.
* **IaC:** **Terraform** for network, compute, storage, DNS, certificates, WAF; per-env workspaces.
* **Environments:** `dev` (ephemeral PR previews), `staging` (prod-like), `prod` (locked); **no direct prod DB access**.
* **CDN/WAF:** Edge caching for static assets; WAF/bot filtering on `/api/*` and auth routes.
* **Domain & topology:** Single origin `https://transcrypt.xyz` (marketing + app at `/app`), easy migration path to `app.transcrypt.xyz` later (cookie domain `.transcrypt.xyz`, shared codebase).

**Payments & Commerce**

* **Billing:** **Stripe Checkout/Customer Portal**; webhook `/api/billing/webhook`; idempotency keys; tax configured in Stripe; minimal PII stored app-side.

**Language, Versions & Tooling (initial pins)**

* **Python** 3.12; **Node** 20 LTS; **Postgres** 15+.
* Formatters/lints: Ruff + Black (Py), ESLint + Prettier (TS/JS).
* Type-check: mypy (Py), TypeScript strict mode.
* Tasking: `just`/Makefile; pre-commit hooks (format, secrets check).

**Dependency Governance**

* **Licences:** OSS allowlist; automatic licence scanning in CI; `THIRD_PARTY_NOTICES.md` published at `/licenses`.
* **Versioning:** SemVer for APIs and schemas (`OrgProfileV1`, `EvidenceV1`, `FindingsV1`); migration manifests on majors.
* **Updates:** Weekly dep refresh PRs; monthly base-image rebuilds; emergency CVE patch lane with post-mortem.
* **Vendor de-risking:** Standards-based abstractions (S3 API, OIDC, SMTP); no hard lock-in; self-hosted fonts/assets; no third-party CDN fonts.

**Rationale & Upgrade Path**

* Bias to **boring, explainable** tech that maps cleanly to compliance claims (Cyber Essentials hygiene, ISO 27001 change control, NIS2 resilience, IEC 62443 zoning).
* Keep LLMs **strictly build-time** for determinism and auditability.
* Scale vertically first (bigger VM, read replica), then horizontally (split app/data zones, orchestrator) as usage proves the need.

**AI Integration (build-time only)**

* **Purpose:** Draft rule objects from legislation, propose cross-framework equivalences, and generate human-readable report copy. **Never** used for runtime scoring or access decisions.
* **Abstraction:** Provider-agnostic via an OpenAI-compatible client (e.g., SDK or lightweight gateway). Pluggable backends: hosted APIs or local models.
* **Redaction & privacy:** Structured redaction pass strips PII/secrets from prompts; opt-in only. Redaction logs keep hashed placeholders for traceability.
* **Determinism & audit:** Fixed prompts with versioned templates; low-variance settings; prompt + response + model/version **persisted as an artefact** tied to the resulting RulePack or text block.
* **Validation:** JSON outputs schema-validated; missing citations or invalid structure = build fail; human review required before publish.
* **Evaluation harness:** Golden-file tests for copy; regression checks to detect drift across model upgrades.
* **Caching:** Content-addressed cache of prompt→response during builds to reduce cost/latency; cache is invalidated on template/model changes.
* **Model registry & provenance:** Track model name, version/commit, licence/usage terms; surface in `/licenses` and internal release notes.
* **Storage:** All AI artefacts stored in the **artefact registry** alongside RulePacks; reproducible by hash.
* **Safety rails:** Blocklist/allowlist filters on inputs; refusal to process unredacted evidence; explicit user consent flags control any external processing.
* **(Optional later)** Embedding/indexing: `pgvector` in Postgres for search over internal docs/policies (still build-time), with the same redaction and audit rules.

<!-- specification -->
## 4. User Experience and Functional Requirements

Here’s how I’d frame **what Section 4 is for** and **what we must prioritise** so the product feels “quietly competent” from the first click.

### What this section is for

It sets the contract between us and the user: what journeys exist, how fast value appears, and which guarantees hold (clarity, repeatability, evidence). It’s not just screens; it’s the behavioural spec for trust. Everything else in the PRD—rule engine, security model, pricing—exists to make these user promises true and boringly reliable.

### Top priorities (stack-ranked)

1. **Time-to-value in one sitting.** A new SME should go from signup → intake → first report in under an hour. This single metric aligns product, tech, and copy.
2. **Deterministic, explainable results.** Every finding must link to the rule, the test, the inputs, and the evidence. No LLM roulette at runtime.
3. **Low cognitive load.** Tight language, progressive disclosure, defaults that match the most common setups. The UI is a guide, not a puzzle.
4. **Evidence never “loose.”** Uploads and assertions are always bound to a control and citation, so the report is defensible.
5. **Accessibility and calm speed.** WCAG 2.2 AA, predictable motion, sub-2s perceived loads on normal 4G.
6. **Privacy by design.** Ask only what’s needed, show why it’s needed, and give obvious controls for export/delete.

### Who we’re designing for (and what they care about)

* **Owner/manager:** Wants to *finish today* without becoming a security expert. Care words: cost, risk, obligations.
* **Tech helper (internal or MSP):** Wants precise asks and fast uploads. Care words: specificity, auditability, “show me where to fix.”
* **Auditor/insurer (read-only):** Wants to verify provenance quickly. Care words: citations, hashes, versioning.

### Minimal journeys we must nail (MVP)

* **Onboard → Quick Start (3 cards only):** “Tell us about your setup,” “Add evidence (or skip),” “Run assessment.” No more than ~20 core fields to start.
* **Intake that feels like a conversation:** Sections with short explanations and examples; autosave; can leave and return.
* **Findings that teach, not scold:** Pass/Fail/Partial with the *because* in one sentence and an expandable trace.
* **Report that stands on its own:** Executive summary, top actions, citations, artefact hash in the footer, printable and shareable.
* **Posture page that changes behaviour:** A small set of “next best actions” that link back to the exact input/evidence needed.

### Copy & interaction tone

Plain English, short sentences, active verbs. Replace abstractions with concrete asks (“Upload your IdP export” not “Provide identity artefacts”). For every required field, a one-line “why this matters” anchored to the framework.

### Where we will *not* compromise

* **No runtime AI decisions.** LLMs help at build-time to draft text or mappings; the user-visible output is deterministic and traceable.
* **No labyrinthine nav.** Five app areas maximum: Dashboard, Intake, Evidence, Reports, Settings. Partner view is deferred (v2.0 – see §9.2 Partner/Integrator API) and stays separate.
* **No vendor theatre.** Fewer animations, more receipts: hashes, timestamps, citations.

### Trade-offs we’ll manage deliberately

* **Speed vs completeness:** Start with a short intake and allow evidence later. The first report may have “partials,” but it must be accurate, not evasive.
* **Guidance vs prescription:** We give ordered actions with rationale; we don’t gatekeep outcomes behind paid consulting.
* **Friction vs assurance:** MFA and consent add clicks, but they are non-negotiable for trust; keep them smooth and explain why.

### Instrumentation that keeps us honest

Track five UX KPIs tied to the business goals: time-to-first-report, completion rate for intake, report regeneration within 90 days, support tickets per user, and the proportion of findings with attached evidence. If these lag, the product—not the user—changes.

### What this means for design & build right now

* Design the **Quick Start** first; make the rest answer only what Quick Start needs.
* Write the **finding card** and **report page** before building more forms—these define the standard of clarity.
* Implement **downloadable traces** and **citations** from day one; retrofitting proof is painful.
* Keep content strings externalised so we can refine language without redeploying logic.

If we hold to these, Section 4 stops being a laundry list and becomes the spine of the product: fast first value, evidence-backed outputs, and a tone that makes people feel calmer after using it than before.

### Why the site matters to UX (not just marketing)

* **Trust before tasks.** No one starts an intake if they don’t believe we’re competent and safe. The site provides the proofs (security posture, legal clarity, transparency) that de-risk clicking “Start.”
* **Correct routing.** Different visitors need different doors: Owner → trial, Tech helper → invite flow, Auditor/Insurer → verifier path, Partner → portfolio & API docs (v2.0 – see §9.2 Partner/Integrator API). The site’s IA should route them deliberately.
* **Expectation setting.** The site promises exactly what the app delivers: “one sitting to first report; deterministic results; evidence-bound findings.” That promise becomes the acceptance bar for onboarding.

### Site journeys (the “public” half of 4.1)

Four top-level journeys, each with a minimum set of proof blocks and a single, obvious CTA.

1. **Cold SME owner (conversion path)**

   * **Landing → Product → Pricing → Security → Trial.**
   * **Proof blocks:** 60-minute first report; screenshots of Quick Start, Findings, and PDF; “No runtime AI” badge; simple pricing; short testimonial or insurer quote; security highlights (MFA, encryption, auditability).
   * **CTA:** “Start Free Trial” (OIDC sign-up).
   * **KPIs:** CTR from hero to Product ≥ 35%; visit→signup ≥ 6–10%; <30s to reach a proof block.

2. **Researcher/validator (credibility path)**

   * **Landing → Security → Privacy/Legal → Changelog/Status → Trial or Contact.**
   * **Proof blocks:** CE/ISO/NIS2 mapping table; /security with responsible disclosure and `security.txt`; /privacy with DPA and subprocessors; changelog & incident history; signed build/provenance note.
   * **CTA:** “View a Sample Report” (gated by email) or “Contact Security.”
   * **KPIs:** Time on /security > 90s; 60% reach at least one legal page link.

3. **Partner/MSP (portfolio path)** *(Not in v1; see §9.2 Partner/Integrator API (v2.0))*

   * **Landing → Partners → Product (Multi-tenant) → API/Webhooks → Contact.**
   * **Proof blocks:** Multi-tenant dashboard screenshot; webhook catalogue; sample JSON export; reseller terms summary.
   * **CTA:** “Book a 20-min Partner Call.”
   * **KPIs:** Partner page → contact ≥ 8%; doc engagement (≥2 API pages viewed).

4. **Auditor/Insurer (assurance path)**

   * **Landing → For Insurers → Sample Attestations → Security/Privacy → Contact.**
   * **Proof blocks:** How findings tie to citations and hashes; export bundle manifest; read-only share link model.
   * **CTA:** “Request a Sample Pack.”
   * **KPIs:** Sample pack requests; follow-on calls booked.

### What each top page must guarantee (content promises)

* **/ (Home):** In 10 seconds: who it’s for, what it does, and a single promise (“From zero to defensible report in one sitting.”) One primary CTA + one secondary (“See how it works”).
* **/product:** 3 anchored sections—Intake, Findings, Reports—each with a screenshot, a 2-line explanation, and one proof (trace, citation, or hash). End with a tiny FAQ about evidence, privacy, and runtime AI.
* **/pricing:** Three plans (Essential/Pro/Partner). Partner is clearly marked as a roadmap preview (Not in v1; see §9.2 Partner/Integrator API). “What’s included” maps only to currently shipped features. No hidden fees. Annual toggle.
* **/security:** Identity, encryption, zero trust, incident process, responsible disclosure, and links to status/changelog. Publish PGP and `/.well-known/security.txt`.
* **/privacy, /terms, /cookies, /dpa, /subprocessors:** Versioned MDX; last-updated stamp; diff links.
* **/changelog & /status:** Plain language, dates, and actions taken.
* **/contact:** Short form with consent, SLA (“we reply within one business day”), and an email address for the old-school.
* **/about:** Why we exist and what we refuse to do (no runtime AI theatre, no lock-in), plus founder credibility signals.

### How the site and app handshake (frictionless routing)

* **CTAs map to app intents**: “Start Free Trial” → `/app/signup` with `intent=trial`; “See a Sample Report” → `/app/demo` (preloaded read-only tenant); “Invite your tech helper” → prefilled `/app/settings/users/invite`.
* **Deep links carry context:** If a visitor chooses “Cyber Essentials” on /product, pass `rulePack=CE-2025.3` into signup so Quick Start is preselected.
* **One origin, one session:** Keeping site and app on `transcrypt.xyz` means OIDC cookies work across both; no CORS faff.

### Priorities for the site (stack-ranked)

1. **Credibility in 30 seconds:** visible security/privacy links; screenshot of the report; one clear promise.
2. **Single CTA per page:** don’t split attention—either trial, contact, or sample.
3. **No surprise after signup:** the first screen in the app should match the last thing the site promised.
4. **Performance & accessibility:** fast images, self-hosted fonts, WCAG 2.2 AA pattern library reused across site and app.

### What to build first (site)

* **Home hero** with the core promise + CTA, and a three-panel strip (Intake, Findings, Report).
* **Security** page skeleton (responsible disclosure + headline controls).
* **Pricing** (even if simple), because it’s a credibility page.
* **Product** with one short looped demo (GIF/WebM) of Quick Start → Findings → PDF.
  Then wire the CTAs to the app’s **Quick Start** so the promise and the first task are perfectly aligned.


### 4.1 User Journeys and Onboarding

The onboarding flow is delivered through the Transcrypt web application.

#### 4.1.1 Public Site Journeys (credibility → correct door → app intent)

* **Cold SME owner (conversion path):** `/` → `/product` → `/pricing` → `/security` → **Start Free Trial**.
  **Promises shown:** “First defensible report in one sitting,” screenshots of **Quick Start / Findings / PDF**, plain-English “no runtime AI” badge, simple pricing.
  **CTA:** `https://transcrypt.xyz/app/signup?intent=trial&rulePack=CE-2025.3`.
  **Acceptance/KPIs:** Hero→Product CTR ≥ 35%; visit→signup ≥ 6–10%; first proof block visible < 30 s.
* **Researcher/validator (assurance path):** `/` → `/security` → `/privacy` (`/legal/privacy`) → `/changelog` → **Request Sample** or **Contact**.
  **Promises shown:** controls overview, responsible disclosure (`/.well-known/security.txt`), DPA/subprocessors, signed build/provenance note.
  **CTA:** `…/app/demo` (read-only sample) or `/contact`.
  **KPIs:** Time on `/security` > 90 s; ≥ 60% touch at least one legal page.
* **Partner/MSP (portfolio path):** `/partners` → `/product#multi-tenant` → `/docs/api` → **Book Partner Call**. Not in v1; see §9.2 Partner/Integrator API (v2.0). [[Post-MVP: §9.4.2 Partner Channel & Co-Branding]]
  **Promises shown:** posture roll-up, webhook catalogue, JSON export sample.
  **CTA:** `/contact?topic=partner`.
  **KPIs:** Partner page→contact ≥ 8%; ≥2 API pages viewed.
* **Auditor/insurer (verification path):** `/insurers` → sample attestations → `/security` → **Request Sample Pack**.
  **Promises shown:** citations + hashes + export manifest.
  **CTA:** `/contact?topic=insurer`.

> **Rule of one CTA:** Each page has one primary CTA (trial, contact, or sample). Copy on the site must exactly match what the app does next.

---

#### 4.1.2 App Onboarding Spine (four entry lanes, one shared flow)

1. **Direct signup (owner/admin):** Email → OIDC → MFA → Tenant name → lands in **Quick Start**.
2. **Invite accept (tech helper):** Magic link carries `tenant` + `role=contributor`; skips billing; lands in **Evidence/Intake** with a checklist, e.g., “Upload IdP export, confirm backups.”
3. **Partner referral (MSP/insurer):** Referral token sets `plan=partner` and `rulePack=CE-2025.3`; Quick Start copy tuned to insurer context. Not in v1; see §9.2 Partner/Integrator API (v2.0).
4. **Auditor view (read-only):** Time-boxed link → posture + latest report; same identity spine; no write paths.

**Quick Start (same three cards for all)**

* **Card 1 — Tell us about your setup** (≤ 20 required fields, autosave): company size, sector, IdP (Entra/Okta/Google), email platform (M365/Google), endpoints (rough count), backups (y/n + immutable y/n), remote access (VPN y/n), key policies present (password/incident/access control y/n), report contact email.
* **Card 2 — Add proof (optional now, later is fine):** drag-drop **Evidence Tray** (IdP export, backup config). Each file shows SHA-256, duplicate flagging, and **must bind** to a control/citation. Assertions supported (e.g., `MFA.enforced.admins=true`).
* **Card 3 — Run assessment:** choose **RulePack = Cyber Essentials**, show version + effective date, press **Run**. Progress shows “Evaluating 15 controls from CE-2025.3…”.

**Finding & report experience**

* **Finding cards:** Pass/Fail/Partial chip; one-sentence “because…”, **Show trace** (inputs, test, citations), **Fix it** jumps to exact intake/evidence field. Right rail: **Top 5 actions** (effort × impact).
* **Report:** Branded HTML/PDF with exec summary, citations, and artefact hash in footer; **Download PDF** and **Share read-only link** (time-boxed). From report: **Invite tech helper** and **Connect insurer/MSP** (Not in v1; see §9.2 Partner/Integrator API (v2.0)).

---

#### 4.1.3 Guardrails, Acceptance, and UX KPIs

* **Guardrails:** Autosave every 3 s; inline + server validation with concrete fixes; long actions idempotent with Request-ID; Problem+JSON errors surface `trace_id`; resume-where-you-left-off works.
* **Acceptance (from a fresh browser):** signup + MFA ≤ 3 min; intake ≤ 20 required fields; first evaluation < 2 min; PDF < 10 s; every finding links to rule, trace, and bound evidence (if present).
* **Nudges:** If evidence skipped, send a gentle prompt at 24–72 h: “Attach these two items to convert 3 partials to passes.” Banner for RulePack updates with one-click re-run.
* **KPIs:** Time-to-first-report ≤ 60 min; intake completion ≥ 90% without support; report regeneration within 90 days ≥ 75%; support load ≤ 0.2 tickets/user/month; ≥ 80% of failing/partial findings have evidence attached within 14 days.

---

#### 4.1.4 Site↔App Handshake (routing & truth alignment)

* **CTAs carry intent:** Site buttons pass `intent`, `rulePack`, and (when known) `plan` params into `/app/signup`.
* **One origin, one session:** `transcrypt.xyz` serves site + app; OIDC cookies are first-party; no CORS friction.
* **No surprise after click:** The first app screen mirrors the last site promise (e.g., the three Quick Start cards shown on `/product` are exactly what appears post-signup).

This ties the **public credibility flow** to the **authenticated first-value flow** so visitors become confident users quickly, with proof baked in at every step. All entry paths—direct signup, invite acceptance, (future) partner referral, and auditor read-only links—share the same handshake, pass intent/context through OIDC, and land in the Quick Start experience (partner referral remains Not in v1; see §9.2 Partner/Integrator API (v2.0)).

Regardless of entry path, everyone hits the same **three-card Quick Start**:

* **1. Tell us about your setup** (≤20 fields, autosave; company size, sector, IdP, endpoints count, backups yes/no, remote access yes/no, key policies yes/no).
* **2. Add proof (optional now, later is fine)** (upload IdP export, backup config; or skip).
* **3. Run assessment** (choose RulePack = Cyber Essentials, show version and effective date, press Go).
  Copy is short, specific, and explains *why* each answer matters. Every required field has a one-line rationale: “This helps us test AC.1.1 (MFA on admin accounts).” No long forms. No jargon soup. If a user leaves, they can resume exactly where they were.

### Screen-by-screen: what good looks like

* **Signup & MFA (≤3 minutes):** OIDC, confirm email, show recovery codes, friendly “You’re done—let’s get your first report.”
* **Quick Start (single page, three cards):** Progress bar + “Time left ~15 min.” Card 1 uses branching (e.g., selecting “Entra ID” unlocks a small panel: “Upload your Conditional Access export or tick ‘we’ll upload later’”). Card 2 is an **Evidence Tray** with drag-and-drop and instant SHA-256 display; duplicates are flagged, and each file must be bound to a control (“Bind to: MFA policy” dropdown). Card 3 is a big primary button: **Run assessment**; we show a 10–30s progress state with a line like “Evaluating 15 controls from CE-2025.3…”.
* **Results (finding cards):** Pass/Fail/Partial chips; one-sentence “because…”, a “Show trace” link (inputs, test, citations), and a **Fix it** CTA that jumps to the exact intake/evidence field. A right-side panel lists the **Top 5 actions** with estimated effort and impact.
* **Report (download/preview):** Branded HTML with exec summary, citations, and artefact hash in the footer; **Download PDF** and **Share read-only link (time-boxed)**. From here: “Invite your tech helper” (precomposed invite) and “Connect insurer/MSP” (partner flow; Not in v1—see §9.2 Partner/Integrator API (v2.0)).
* **Return experience (dashboard):** Posture badge, “time since last assessment,” and “What changed” diff if they’ve re-run.

### Guardrails, nudges, and acceptance

* **Guardrails:** Autosave every 3 seconds; client + server validation (tell user *what* broke + *how to fix*); all long actions idempotent with Request-ID; Problem+JSON errors bubble a friendly message and surface a **trace_id** for support.
* **Nudges:** If a user skips evidence, we schedule a gentle nudge (24–72h): “Attach these two items to turn 3 partials into passes.” If a RulePack updates, a banner explains the change and offers a 1-click re-run.
* **Acceptance criteria:** From a fresh browser, **signup→MFA→first report in ≤60 minutes** without docs. Intake ≤20 required fields; first evaluation <2 minutes; PDF in <10s; every finding links to rule, trace, and evidence (if any). Support load target: ≤0.2 tickets/user/month for onboarding.
* **Fields we’ll start with (tight list):** company name/sector/size, IdP (Entra/Okta/Google) + admin MFA yes/no, email platform (M365/Google), endpoints count (rough), backups (y/n + immutable y/n), remote access (VPN y/n), key policies present (password, incident, access control y/n), contact email for reports. That’s it.

If you’re happy with this spine, the next tangible step is to sketch the **Quick Start** and **Finding Card** as wireframes in your doc—the rest of the UX hangs from those two artefacts.


### 4.2 Interface Philosophy

**It’s the contract for how the product talks and behaves.**
Interface philosophy is our house style for truth-telling: the rules that decide wording, layout, pacing, and how much the product asks of a person at any moment. It turns vague goals (“be clear,” “be trustworthy”) into operational constraints. For Transcrypt that means: every screen answers three questions in this order—**what is this**, **why it matters**, **what to do next**—and every status must be **explainable** with a visible link to the rule, test, input, and evidence. No mysteries, no hand-waving, no “AI says so.” When people feel oriented and in control, they move faster and trust the output.

**Design tenets (non-negotiable, testable).**

* **Plain first, precise second.** Lead with simple phrasing; keep the formal clause in a fold-out. Example: “MFA not enforced for admins” (plain) with “CE AC.1.1, test: ASSERT.MFA.enforced.admins=false” (precise).
* **One decision per view.** If a page asks for more than one meaningful choice, it’s two pages. Primary action is obvious; secondary actions look secondary.
* **Evidence never loose.** Uploads and assertions always bind to a control and citation before the user can continue.
* **Progress over pages.** Show where you are (“Step 2 of 3”) and the impact of finishing (“This will unlock 3 controls”).
* **Determinism on display.** “Show trace” exists everywhere a result appears. Identical inputs → identical outputs; the UI lets users verify that.
* **Calm speed.** Sub-2s perceived loads, subtle motion only when it reduces cognitive load (e.g., focus a just-failed field).
* **Accessibility as default, not garnish.** WCAG 2.2 AA, keyboard-only flows, real contrast, reduced-motion respected.

**Tone, components, and content grammar.**
Tone is **quietly competent**: short sentences, active verbs, no fear-mongering. Components embody that tone: cards with a strong sentence up top, a concise reason, and one primary button. Error messages say what broke **and** how to fix it. Tables have first columns that explain the row in human terms; badges are for state (Pass/Fail/Partial), not decoration. When jargon is unavoidable, define it inline. (You can be technical without being theatrical.)

**Constraints we refuse to break (and why).**

* **No runtime AI decisions.** If it affects a finding, the logic is deterministic and inspectable. This preserves auditability and user agency.
* **No modal labyrinths.** Modals are for small confirmations. If the content needs scrolling or multiple decisions, it’s a page.
* **No invisible requirements.** If you need data, say exactly why and where it will show up in the report. Hidden asks destroy trust.
* **No dead-end states.** Every error offers a forward path—retry, download trace, or jump to the field that fixes it.

**How we prove we’re living it (practical tests).**

* **Five-second scan:** Can a new user tell what the page is about and what to do without scrolling?
* **Breadcrumb of proof:** From any finding, can you reach rule text, test, inputs, and evidence in ≤ 3 clicks?
* **Red-pen edit:** Can legal/compliance folks tighten copy without touching code (strings externalised)?
* **Accessibility pass:** Does the page pass axe/Pa11y and keyboard-only use?
* **Time-to-action:** Does a primary task (upload evidence, re-run assessment) take ≤ 2 obvious clicks from the dashboard?

That’s what “Interface Philosophy” means here: a disciplined, humane protocol for turning regulation into action. It keeps the product boring in the right ways (predictable, verifiable) and sharp where it matters (specific next steps, fast feedback). Next step is to codify this into a tiny UI playbook—component do/don’ts, copy patterns, and acceptance checks—so every new screen inherits the same spine.

### 4.3 Key User Stories

**1) SME Owner/Admin (decision-maker)**

* **As a** small business owner
* **I want** to sign up, answer a short guided intake, upload a couple of key docs, and get a defensible Cyber Essentials assessment with a prioritised action list in one sitting
* **So that** I know exactly what to fix, how urgent it is, and can show progress to my board/insurer.
* **Acceptance:** account+MFA in <3 minutes; intake ≤20 required fields with autosave; first evaluation <2 minutes; report renders HTML/PDF with citations and artefact hash; dashboard shows “Top 5 actions” linking back to precise inputs; billing works via Stripe; audit trail records major actions.

**2) Tech Helper / IT Contributor (in-house or MSP)**

* **As a** technical helper invited by the owner
* **I want** to add precise evidence (IdP export, backup config, endpoint counts), correct intake details, and re-run the assessment
* **So that** findings move from “partial/fail” to “pass” with clear proof.
* **Acceptance:** invite via signed link; role = Contributor (no billing access); upload returns SHA-256 + de-dup; assertions (e.g., `MFA.enforced.admins=true`) are bound to the right control; re-run produces a diff (“what improved”); every finding card shows rule, test trace, and linked evidence; activity log records uploads and edits.

**3) Auditor / Insurer (read-only verifier)**

* **As an** external reviewer
* **I want** time-boxed, read-only access to posture, reports, and referenced evidence with citations
* **So that** I can verify provenance quickly without back-and-forth.
* **Acceptance:** magic link scoped to a tenant and expiry; posture roll-up view + latest report; evidence previews/downloads where permitted; no write paths; Problem+JSON errors with `trace_id`; export bundle (JSON + PDFs + manifest with hashes) available on request.

### 4.4 Accessibility and Usability Standards

#### What this section is for

It’s the contract that every visitor and user—regardless of device, bandwidth, motor control, eyesight, hearing, or cognitive load—can complete core tasks. For Transcrypt, that means: anyone can get from landing page → signup → first report, can understand findings, and can download/hand to an auditor, **without assistance**. No exceptions.

#### Priorities (stack-ranked)

1. **Keyboard-first**: everything works without a mouse, with visible focus and logical order.
2. **Readable by default**: real contrast, scalable text, plain language first, precise clause second.
3. **Predictable & recoverable**: errors say what broke and how to fix; no timeouts that eat work.
4. **Assistive-tech compatible**: correct landmarks, roles, names, and states so screen readers and voice control can operate the app.
5. **Accessible reports**: the generated **PDF/HTML reports** are tagged, navigable, and readable by screen readers.

#### Non-negotiable standards (what we target)

* **WCAG 2.2 AA** across site and app (including PDFs).
* **BSI/EN 301 549** alignment where relevant (maps closely to WCAG, useful for EU/UK buyers).
* **UK Equality Act 2010** spirit: reasonable adjustments baked in.
* **PDF/UA** principles for reports: semantic structure, tagged tables, alt text for figures.

#### Design & content rules (operationalised)

* **Colour & contrast**: 4.5:1 for body text, 3:1 for large text/icons; tokens pre-checked so designers can’t pick non-compliant colours.
* **Typography**: respect OS font scaling; never lock line-height < 1.4; avoid justified text; keep measure ≈ 60–80 chars.
* **Motion**: honour `prefers-reduced-motion`; no essential info conveyed by motion alone; avoid parallax/looped distractions.
* **Language**: short sentences, active verbs; define jargon inline; reading level ≈ secondary school for all user-facing copy.
* **Target sizes**: ≥ 44×44 px hit areas on touch; generous spacing between actions.
* **Timing**: no session timeouts during intake without warning and extend option; autosave on every edit.

#### Interaction & structure patterns

* **Keyboard**: Tab sequence matches visual order; roving tabindex for composite widgets; **skip to content** link; Esc closes non-modal popovers.
* **Focus management**: put focus where the user expects after route change or dialog open; never trap focus; always return focus sensibly on close.
* **Semantics**: use native elements first; ARIA only when necessary. Landmark regions (`header`, `nav`, `main`, `aside`, `footer`) present on every page.
* **Forms**: each input has a **visible label**, programmatic association, helpful hint, and an example; errors are inline, specific, and read by screen readers; don’t rely on colour alone.
* **Tables & charts**: tables have headers (`<th scope>`), captions, and summaries; charts must include data tables or alt text summarising the finding and trend.

#### Reports (HTML & PDF) accessibility

* HTML report uses proper headings, lists, and table semantics; link text is meaningful (“View MFA policy evidence”), not “click here”.
* PDF export preserves tags/structure from HTML; figures have alt text; the artefact hash and citations are text, not images; doc language set; reading order verified.

#### Mobile & low-bandwidth

* First meaningful paint fast on 3G/4G; no third-party font/CDN blockers; images responsive; forms resilient to spotty connections (autosave + retry with backoff).

#### Cognitive load & clarity

* One decision per view; progressive disclosure; show *why* each field is needed (“This helps us test AC.1.1”).
* Provide summaries and “what changed” diffs; avoid modal stacks; always give a safe next step.

#### Testing & enforcement (make it routine)

* **Design-time**: contrast plugin on the token palette; component library examples include keyboard/AT notes.
* **Build-time**: axe/Pa11y CI checks on key routes (home, product, signup, intake, findings, report preview).
* **Manual**: quarterly screen-reader sweeps (NVDA + VoiceOver), keyboard-only task run (signup→report), reduced-motion pass.
* **PDF**: run a tagging validator on sample reports each release.
* **Telemetry**: log “keyboard only” session ratio (heuristic) and error recovery rates; track time-to-first-action for users with larger font settings.

#### Acceptance criteria (task-level)

* From keyboard only, a new user can:
  a) sign up + set MFA,
  b) complete intake,
  c) upload two evidences,
  d) run assessment,
  e) download an accessible PDF—**without touching a mouse**.
* All interactive controls have programmatic names/states; tab order matches visual order; focus is always visible.
* No blocking WCAG 2.2 AA violations on top routes; automated a11y score (axe) ≥ 95 on those pages.
* Report PDFs pass a tag/structure check and a manual NVDA read-through of headings, tables, and citations.

### 4.5 Offline and Multi-Device Support

**What we’re solving.** Users are on flaky Wi-Fi, 4G in a car park, or rural broadband. The product must be usable without a perfect connection and it must “hand off” cleanly between laptop, phone, and tablet. We will ship an **installable PWA** (Progressive Web App) that precaches the app shell and lets people complete intake, queue evidence, and view the most recent report offline—then sync safely when they’re back online. No magical thinking: *evaluation and billing require a network*, but everything leading up to “Run assessment” should work in airplane mode.

**How it works (architecture & behaviour).**

* **PWA & caching:** Web App Manifest + Service Worker (Workbox). Precache: app shell, fonts, icons, and core routes (`/app`, `/app/intake`, `/app/reports`). Runtime cache with stale-while-revalidate for lightweight JSON (feature flags, RulePack metadata). **Never cache secrets** or authenticated API responses longer than the session TTL.
* **Offline data store:** **IndexedDB** (via a tiny helper, e.g., `idb-keyval`) caches *intake form state*, *evidence metadata*, and the **most recent HTML/PDF report**. Every local record carries a UUIDv7, timestamp, and a “sync state” (`pending|synced|conflict`).
* **Queued mutations:** All writes are recorded as idempotent “commands” (e.g., `INTAKE.UPDATE(field,value)`, `EVIDENCE.ADD(meta,sha256,blobRef)`). A Background Sync job (or foreground retry with backoff on iOS) replays them server-side. Conflicts resolve at **field level, last-writer-wins** with a server truth timestamp; conflicts surface a “Review changes” banner and an audit entry.
* **Evidence files offline:** Blobs are stored temporarily in IndexedDB, **SHA-256 computed client-side**, and chunk-uploaded on reconnect with resume support. Size caps: **50 MB/file (MVP)**, total offline cache **200 MB**; users see a usage meter and can clear cache from Settings. Evidence must be explicitly **bound to a control** even offline; binding syncs as metadata before the binary upload.
* **Multi-device handoff:** Session is first-party (one origin), short-lived with silent refresh. “Continue where you left off” loads the last saved intake checkpoint from server if newer than local; otherwise offers “Use local draft” vs “Discard draft”. Device list in Settings shows active sessions; owners can revoke a device.
* **Security of local cache:** By default, we rely on OS user separation. For higher assurance, a **“Secure Device Mode”** encrypts the local cache using WebCrypto (AES-GCM) with a key wrapped by a per-device secret; unlocking requires re-auth (step-up MFA) after 15 minutes of inactivity. Evidence blobs are purged from local storage **immediately after successful upload**.

**What’s in/out, and how we prove it.**

* **Offline supported:** intake edits, evidence **queuing**, report **viewing** (last copy), user invites (queued), and audit entries for local actions (synced later).
* **Online-only:** running evaluations, generating *new* reports, billing changes, connector imports.
* **Acceptance tests:**

  1. **Airplane-mode run:** From a fresh install, user completes all required intake fields, attaches two evidence files (queued), and closes the app. On reconnect, sync completes automatically; user taps **Run assessment**.
  2. **Conflict case:** Field `endpoints.count` edited on phone offline and on desktop online; on reconnect, desktop wins (newer server timestamp). Phone shows non-blocking “Review changes” with a one-click “Apply local edit” (creates a new server write).
  3. **Report offline:** After generating a report online, user can open the same report offline and print it; artefact hash remains visible and selectable text (not an image).
  4. **iOS fallback:** Background Sync unavailable—foreground retry with exponential backoff works; user gets a persistent “X items waiting to upload” indicator.
* **KPIs:** ≥ 95% sync success within 2 minutes of reconnect; ≤ 1% conflicts per 100 edits; < 1 support ticket per 500 offline sessions; median time from reconnect→all uploads complete ≤ 30 s on 4G.

**Device and layout specifics.**

* **Responsive breakpoints:** phone (≤480px), tablet (481–1024px), desktop (≥1025px). Intake and findings adapt to single-column on phone; primary actions stay thumb-reachable; touch targets ≥ 44×44 px.
* **File picker UX:** camera/document sources on mobile; show per-file progress and a checksum tick when complete. **Never** silently retry more than 5 times; surface “Resume upload” clearly.
* **Accessibility in offline mode:** all controls keyboard-operable; offline banners are role=`status` with clear language (“You’re offline. We’ll sync 3 items when you reconnect.”).

**Constraints & hygiene.**

* We do **not** persist access tokens in IndexedDB; only ephemeral session info in memory + cookies.
* We **do not** cache partner/auditor data unless a report was explicitly opened.
* Clearing cache deletes local drafts and queued evidence (with a confirmation). A redaction setting prevents any evidence bytes from being stored locally on shared machines.

This gives you a boring-reliable PWA: complete the work anywhere, carry on across devices, and never lose a byte—even when the network gremlins are doing parkour.

<!-- specification -->
## 5. Data, Intelligence, and Automation

This section covers how Transcrypt Essential collects, organises, and reuses **Cyber Essentials evidence**—the screenshots, logs, inventory exports, and policy documents that prove each control. The platform centres on predictable routines: guided forms capture structured answers, file uploads are immediately tagged to controls, and reminders close the loop when evidence goes stale. Runtime behaviour stays straightforward and reviewable so small teams can trust what the system is doing on their behalf.

Automation focuses on chores that normally consume evenings before certification: gathering proof from devices, checking that required screenshots exist, and packaging everything into the IASME submission order. Background jobs handle PDF creation, evidence bundling, and reminder schedules while keeping the visible experience simple [↩ A3.2.6 – Report Service; A3.2.9 – Observability & Audit]. Offline/PWA support lets users capture photos or notes on-site and sync them later without losing context [↩ UX4.5 – Offline and Multi-Device Support; A3.2.8 – Data Stores & Artefacts]. Dashboards surface action lists, renewal countdowns, and evidence completeness in plain English so teams can act quickly.

Transcrypt Essential keeps privacy practical: collect only what is needed for Cyber Essentials, isolate each tenant, and ensure users can export or delete their own records when required [↩ A3.2.5 – Evidence Services; A3.2.8 – Data Stores & Artefacts]. AI remains a build-time assistant that drafts policies or suggests missing artefacts, with humans confirming every output before it becomes part of the record [↩ A3.2.4 – LLM Assist Pipeline]. The goal is simple—clear data contracts, lightweight automation, and evidence that is always ready for the next renewal.

### 5.1 Data Flow Architecture (v1)
These components operate within the hosted Transcrypt platform integrated with the web app and evidence vault.
Input (guided forms/uploads) → Validation → [Evidence Vault](#325-evidence-services) (tenant-encrypted) [↩ A3.2.5 – Evidence Services] → [Rule Evaluation Service](#323-rule-evaluation-service-deterministic) (Cyber Essentials v3.2 checks) [↩ A3.2.3 – Rule Evaluation Service] → Insights/Reports [↩ A3.2.6 – Report Service].
No cross-tenant processing. All AI calls are stateless inference with minimal PII footprint [↩ A3.2.4 – LLM Assist Pipeline].
Scope evaluation will honour the Cyber Essentials v3.2 Section C definitions listed in [§6.2](#62-cyber-essentials-alignment-v32): every device touching organisational data (corporate or BYOD) will be included, cloud/SaaS/remote assets will be auto-detected under shared responsibility, and explicit “sub-set” exclusions will be captured with justification inside `scope.manifest.json`.
Although Transcrypt employs modern orchestration and automation patterns, these are invisible to the SME user. The only visible surface is the guided flow; all scaling, queueing, and AI orchestration run silently in the background.

> **Tenant Isolation:** All evidence and report objects are encrypted client-side by the app using Transcrypt-managed per-tenant KMS keys before upload, and wrapped again with server-side encryption at rest.
> Processing occurs on ephemeral decrypted copies inside isolated containers that are destroyed after execution.
> Only encrypted artefacts persist; no plaintext is stored centrally.

> **Framework Agnostic Design:**
> Data ingestion, evidence storage, and rules execution reference control-pack metadata, not hard-coded UK criteria.
> This allows new jurisdictions or standards to be loaded as configuration rather than forked code.

### 5.2 Machine Learning and AI Components (v1)
All compliance logic in v1 is executed autonomously by the [Rule Evaluation Service](#323-rule-evaluation-service-deterministic) [↩ A3.2.3 – Rule Evaluation Service] and AI assistants [↩ A3.2.4 – LLM Assist Pipeline].
Human oversight is not part of the MVP loop; instead the platform creates traceable outputs that can later be reviewed by auditors in the Assisted Tier.
AI assists the user rather than overwhelms them—its purpose is to *simplify judgement calls*, not introduce new interfaces or tuning [↩ A3.2.4 – LLM Assist Pipeline].
- **Extraction:** classify uploads (policy vs invoice vs screenshot), extract dates/covers.
- **Drafting:** first-pass policies/templates; user reviews before saving.
- **Gap prompts:** deterministic heuristics suggest missing evidence based on the Cyber Essentials v3.2 (CE) checklist state (no LLM at runtime) [↩ A3.2.4 – LLM Assist Pipeline].
_No training loops or fine-tuning in v1; models are managed centrally; outputs are user-confirmed._ [↩ A3.2.4 – LLM Assist Pipeline]

> **Post-MVP:** External assessor API and auditor portal within the professional Assisted Tier. [[Post-MVP: §9.4.1 Assisted Tier & Collaboration]]

### 5.3 Reporting, Dashboards, and Insights (v1)
- Cyber Essentials v3.2 readiness score, control-family breakdown, renewal countdown, and evidence completeness will be surfaced with pass/fail logic tied to the 14-day remediation, MFA, password, device lockout, and software-support thresholds in [§6.2](#62-cyber-essentials-alignment-v32) [↩ UX4.1 – User Journeys and Onboarding].
- Exports: PDF summary, evidence index, and one-click IASME-ordered Self-Assessment bundles (CSV/JSON) will preserve each `ce_ref` emitted by the [Rule Evaluation Service](#323-rule-evaluation-service-deterministic) [↩ A3.2.3 – Rule Evaluation Service; A3.2.6 – Report Service].

### 5.4 Auditability and Data Provenance (v1)

- **Version history for everything.** Evidence items, questionnaires, and generated reports maintain visible revision histories with author, timestamp, and reason-for-change notes [↩ A3.2.9 – Observability & Audit].
- **Searchable activity log.** Key actions (uploads, edits, submissions, exports) are recorded in chronological order so teams can replay who did what and when without specialist tooling [↩ A3.2.5 – Evidence Services].
- **Downloadable change reports.** Users can export change logs alongside their evidence bundle to satisfy IASME follow-up questions without digging through the UI. [[Post-MVP: §9.4 Risk Register and Mitigation]]

### 5.5 Closed-Source Policy and Evidence Integrity

Users retain contractual ownership of their data. Transcrypt Essential ensures data integrity through versioning, hashing, and audit trails; encryption uses Transcrypt-managed per-tenant KMS keys (not customer-supplied keys).

**Implementation (v1):**
- Core logic and AI models are closed-source binaries signed by Transcrypt Ltd. [↩ A3.2.3 – Rule Evaluation Service; A3.2.4 – LLM Assist Pipeline]
- System artefacts—reports, evidence archives, audit logs—are hashed and timestamped so tampering attempts are detectable. [↩ A3.2.9 – Observability & Audit]
- Integrity manifests and checksum algorithms are published so customers can validate exported packages independently. [↩ A3.2.6 – Report Service]
- Managed encryption controls ensure data at rest follows the baseline described in §7.3. [↩ §7.3 – Data Security Basics]
- Release documentation captures evidence-handling procedures and any changes to audit workflows.

Implementation topology choices are recorded as ADRs (see ADR-0007 for database topology).

### Traceability Table (Section 5)

| ID | Requirement / Feature | Strategic Origin | Specification Anchor | Delivery Path | Status |
|:---|:-----------------------|:-----------------|:---------------------|:--------------|:--------|
| UX-01 | Self-serve onboarding workflow | §1 – Vision and Purpose (Product Definition) | §4.1 User Journeys and Onboarding | §9.1 MVP Definition | **v1.0 Transcrypt Essential (planned)** |
| EV-01 | Tenant evidence vault & secure storage | §1 – Scope Guardrails (v1) | §3.2.5 Evidence Services; §5.1 Data Flow Architecture | §9.1 MVP Definition | **v1.0 Transcrypt Essential (planned)** |
| AI-01 | AI-assisted drafting & gap prompts | §1 – Design Principle “Automation you don’t feel” | §3.2.4 LLM Assist Pipeline; §5.2 Machine Learning and AI Components | §9.2 Phase Milestones and Timelines (Phase 2 – Validation) | **Phase 2 (planned)** |
| RL-01 | Deterministic rule evaluation & control mapping | §1.2 Mission and Guiding Principles | §3.2.3 [Rule Evaluation Service](#323-rule-evaluation-service-deterministic); §3.4 Extensibility and Integration Framework | §9.1 MVP Definition | **v1.0 Transcrypt Essential (planned)** |
| RP-01 | [Compliance reporting & dashboards](#53-reporting-dashboards-and-insights-v1) | §1.4 Success Criteria and Long-Term Impact | §5.3 Reporting, Dashboards, and Insights | §9.1 MVP Definition | **v1.0 Transcrypt Essential (planned)** |
| AP-01 | Auditability & provenance guarantees | §1 – Vision and Purpose (Evidence Integrity) | §5.4 Auditability and Data Provenance; §7.4 Operational Resilience and Incident Response | §9.2 Phase Milestones and Timelines (Phase 4 – Stabilisation) | **Phase 4 (planned)** |
| CP-01 | Closed-source evidence integrity policy | §1 – Vision and Purpose (Evidence Integrity) | §5.5 Closed-Source Policy and Evidence Integrity | §9.4 Risk Register and Mitigation | **Post-MVP (planned)** |
| SC-01 | Zero-trust security baseline | §2.5 Legislative Environment and Compliance Ecosystem | §7 Security and Infrastructure Requirements | §9.2 Phase Milestones and Timelines (Phase 1 – Foundation) | **v1.0 Transcrypt Essential (planned)** |
| CG-01 | Internal governance & policy library | §2.5 Legislative Environment and Compliance Ecosystem | §6.1 Alignment with NIS, Cyber Essentials, ISO 27001, and IEC 62443; §6.4 Policy Library and Evidence Management | §9.2 Phase Milestones and Timelines (Phase 3 – Expansion) | **Phase 3 (planned)** |
| RM-01 | Subscription tiers & monetisation metrics | §1.4 Success Criteria and Long-Term Impact | §8 Monetisation and Revenue Model | §9.2 Phase Milestones and Timelines (Phase 3 – Expansion) | **Phase 3 (planned)** |
| RD-01 | Assisted Tier auditor workflow | §1 – Human Role Definition | §3.2.7 Admin Console (Internal); §5.2 Machine Learning and AI Components (Post-MVP notes) | §9.2 Phase Milestones and Timelines (v1.5 Assisted Tier β) | **Post-MVP (planned)** |
| COL-01 | Assisted Tier collaboration flows (auditor support) | §1 – Non-goals (MVP framing); §2.5 Legislative Environment and Compliance Ecosystem | §5.2 Machine Learning and AI Components (Post-MVP notes) | §9.4.1 Assisted Tier & Collaboration | **Post-MVP (planned)** |
| CHN-01 | Partner channel: co-brand, license, revenue share | §1 – Non-goals (MVP framing); §8.3 Partner and Reseller Ecosystem | §3.4 Extensibility and Integration Framework; §8.3 Partner and Reseller Ecosystem | §9.4.2 Partner Channel & Co-Branding | **Future (planned)** |
| RD-02 | Geo-sovereign nodes & regional deployment | §2.4 Future Extensibility to Other Nations; §10.1 Interoperability with Other National Frameworks | §7.2 Network Segmentation and Zero Trust Architecture; §7.5 Secure Software Supply Chain | §9.2 Phase Milestones and Timelines (v2.0 Geo-sovereign Nodes) | **Future (planned)** |

<!-- specification -->
## 6. Compliance and Governance Framework

Transcrypt Essential earns trust by operating on the same Cyber Essentials practices it promotes to customers. Governance is therefore lightweight, inspectable, and focused on keeping those five control areas healthy without adding bureaucracy that a founder-led company cannot sustain.

### 6.1 Operating Baseline (Cyber Essentials in Practice)

- Keep platform engineering and internal IT on a shared Cyber Essentials checklist reviewed monthly.
- Track scope, device inventory, patch status, and MFA coverage in the same evidence vault users rely on.
- Publish a simple internal timetable for renewal milestones (pre-assessment, submission window, remediation buffer).

### 6.2 Cyber Essentials Alignment (v3.2)

Transcrypt Essential’s features map directly to the control families assessed by IASME. Each module is responsible for collecting the right artefacts and highlighting the most common gaps.

| Cyber Essentials Control | Platform Support | Evidence Focus |
|:--------------------------|:-----------------|:----------------|
| **1. Firewalls & Internet Gateways** | Network Baseline Wizard | Capture screenshots/config exports showing boundary rules and admin access restrictions. |
| **2. Secure Configuration** | Device Policy Library | Provide setup checklists and photo evidence for default settings, account hardening, and service disablement. |
| **3. Security Update Management** | Patch Tracker + [Evidence Vault](#325-evidence-services) | Track outstanding updates, store reports from OS/app stores, and remind teams before the 14-day window closes. |
| **4. User Access Control** | Identity Review Workspace | Maintain privileged user lists, MFA status, and join/leave approvals with sign-off timestamps. |
| **5. Malware Protection** | Endpoint Coverage Dashboard | Document anti-malware status per device and log periodic scan summaries. |

Scope management mirrors the IASME questionnaire: include every device touching organisational data, document justifications for any sub-sets, and re-check cloud services during renewal intake. Reports export in the same order as the submission booklet so teams can go from app to upload without reformatting.

### 6.3 Risk Management and Assurance

Risk handling is pragmatic. The company keeps a short, living register of issues that could delay certification (e.g. unsupported devices, lapsed backups, staffing changes). Each entry carries an owner, mitigation action, and due date. Quarterly reviews close resolved items and promote new ones drawn from customer support trends or incident post-mortems.

### 6.4 Policy Library and Evidence Management

Policy templates within Transcrypt Essential are versioned documents aligned to Cyber Essentials expectations (acceptable use, patching, remote working, bring-your-own-device). Every update records author, reason, and effective date so SMEs can demonstrate policy currency. Evidence storage treats screenshots, config files, meeting minutes, and supplier confirmations equally—each item tagged to its control, renewal cycle, and reviewer. Nothing floats loose; everything has a home tied to the questionnaire reference.

### 6.5 Governance of Product Lifecycle

Feature work, fixes, and operational updates follow a simple gating model: ticket → scoped change → peer review → automated checks → deploy. Releases are logged with what changed, why it matters for Cyber Essentials users, and any follow-up actions. Incident reviews feed directly into backlog items or documentation updates so lessons do not disappear.

> **Future alignment reference:** Broader frameworks (NIS2, GDPR, ISO 27001) will be assessed in the Transcrypt Platform roadmap once multi-framework support moves into scope.

<!-- specification -->
## 7. Security and Infrastructure Requirements

Transcrypt Essential follows **established SaaS security practice** suited to small-business customers: encrypt data in transit and at rest, require MFA for administrative access, keep access logs, and run regular backups. The goal is to deliver a trustworthy service without demanding enterprise-level overhead from the team or the users who rely on it.

Key expectations for v1:

- **Managed hosting with segregation.** Each tenant’s data stays logically separated, access controlled, and monitored for unusual activity.
- **Hygiene by default.** Infrastructure-as-code, patch management, and vulnerability scanning are part of the normal delivery pipeline so environments stay current.
- **Operational readiness.** Backups, restore drills, and basic incident playbooks ensure the service can recover quickly from outages or data loss.
- **Account security.** MFA, role-based access, and periodic access reviews keep administrator accounts tight while keeping the SME user experience simple.

These controls keep pace with Cyber Essentials expectations while leaving room for future hardening when the broader Transcrypt Platform arrives.

### 7.1 Authentication, Authorisation, and Identity Management

- Single sign-on with common SME identity providers (Microsoft 365 and Google Workspace) plus email/password as a fallback.
- Multi-factor authentication required for administrative roles; optional but encouraged for all other users.
- Role-based access with simple presets (Owner, Manager, Contributor) so teams can delegate tasks without over-exposing data.
- Quarterly access reviews built into the admin console with downloadable summaries for Cyber Essentials evidence.

### 7.2 Network Segmentation and Zero Trust Architecture

- Separate environments for production, staging, and development with distinct credentials and access policies.
- Internal services communicate over private networks with firewall rules restricting ingress to necessary ports only.
- No direct database access from the public internet; administrative maintenance occurs via approved bastion hosts with MFA.
- Routine reviews ensure that temporary access (support sessions, debugging) is time-bound and recorded.

### 7.3 Data Encryption and Key Management

- TLS 1.2+ for all user-facing and service-to-service traffic; HSTS enforced on public endpoints.
- Managed database and object storage encryption at rest is handled by cloud services using platform-level key rotation. No customer-managed keys or client-side encryption are used in this phase.
- Secrets stored in a central secrets manager; access limited to service identities with least privilege.
- Annual encryption configuration review to confirm algorithms and certificates meet current NCSC guidance.

### Managed Key Operations Summary

- Platform-operated keys reside in the managed KMS with automated rotation tracked through change management.
- Service components request access via scoped identities and short-lived credentials issued by the hosting provider.
- Key usage and rotation events are logged centrally and included in quarterly security reviews.

### 7.4 Operational Resilience and Incident Response

- Nightly backups with 30-day retention, plus weekly test restores in a sandbox environment.
- Platform monitoring covers uptime, error rates, and security alerts, with on-call rotation for rapid response.
- Incident playbooks cover common SME-impact scenarios (credentials exposed, data deletion, availability outage) and require post-incident reviews within five working days.
- Customer communications templates prepared in advance for outage updates or evidence of remedial action.

### 7.5 Secure Software Supply Chain

- Dependency management through lockfiles and automated security scanning before release.
- CI pipelines build from clean base images, run unit and integration tests, and require peer review before deploy.
- Software Bill of Materials generated for each release and stored with deployment notes for traceability.
- Third-party services documented with ownership, version, and renewal dates so vendors can be reassessed easily.
<!-- specification -->
## 8. Monetisation and Revenue Model

Transcrypt’s Monetisation and Revenue Model is designed to sustain a founder-led business that grows through credibility, not scale at any cost. The model balances accessibility for small businesses with predictability for the company, using a subscription-first approach anchored in recurring monthly revenue. The goal is to create a compounding utility product—one that earns retention through genuine operational value, not lock-in. Pricing is transparent, all-inclusive, and proportionate to the size and complexity of the customer’s organisation. No hidden consultancy, no per-seat penalties, no punitive renewal clauses. The platform’s automation and clarity deliver cost efficiency at scale, allowing Transcrypt to compete effectively against both low-cost certification brokers and high-end compliance consultancies while maintaining healthy margins.

Revenue generation is phased deliberately to match the company’s maturity. In the first twelve months, the emphasis is on validation and traction—converting early adopters into paying customers and achieving the target of £500 per month profit by month twelve. As adoption grows, the subscription base becomes self-reinforcing: recurring revenue funds incremental product improvements, which in turn attract more subscribers through word-of-mouth trust. Long-term sustainability rests on progressive value: Phase 2 (Transcrypt Platform) may introduce additional frameworks (for example, NIS2, DORA, ISO 27001) and features (automated evidence mapping, partner dashboards) once the Transcrypt Essential business is stable. These expansions must lift user value without complicating the simple subscription at the heart of Transcrypt Essential. Each addition must raise both user value and lifetime revenue per customer while preserving affordability for SMEs.

Strategically, Transcrypt’s monetisation model is built for credibility and optionality. The Essential subscription service delivers continuous compliance guidance, with optional enterprise features and integrations for supply-chain partners or insurers forming natural upsell paths. Partnerships and white-label arrangements with MSPs, insurers, or professional bodies will provide parallel revenue streams that do not require mass marketing or venture funding. The model’s simplicity—clear value, low churn, low support overhead—makes it robust even at small scale. Profitability, not growth for its own sake, remains the governing metric. Transcrypt’s business design mirrors its technical ethos: lean, transparent, and verifiable. Every pound earned should represent genuine value delivered and demonstrable trust built.

### 8.1 Pricing Strategy

Transcrypt’s Pricing Strategy is intentionally simple, transparent, and grounded in the economic realities of the SME market it serves. It rejects the bloated complexity of enterprise SaaS pricing in favour of a clear value-for-money proposition that customers can understand instantly. The platform operates on a subscription model, priced to deliver affordable, ongoing compliance without the hidden costs of consultancy or renewal audits. The guiding philosophy is that every customer—whether a one-person consultancy or a 50-person manufacturer—should pay for the same capability, scaled by complexity rather than headcount. Pricing is benchmarked to undercut typical Cyber Essentials consultancy bundles by 30–40%, while offering continuous compliance alignment rather than one-off certification support. This low-friction entry point builds trust and supports organic adoption through word of mouth.

The initial focus is on reaching sustainable profitability, not rapid expansion. During the first year, pricing will remain flat and modest—targeting small businesses that need proof of compliance quickly and simply. The goal is to reach a £500 monthly profit by month twelve, a milestone that validates both product-market fit and cost discipline. Once the subscription base and operational costs stabilise, the strategy transitions to a dual objective: improving average revenue per user (ARPU) through tiered offerings and introducing optional paid features such as advanced reporting, audit support, and supply-chain mapping. Each enhancement must directly correspond to tangible customer value, ensuring that every incremental pound earned represents reduced workload or increased assurance.

Long term, the pricing model is designed to support predictable recurring revenue while maintaining accessibility. Subscription renewals will be seamless, annual discounts modest but meaningful, and all pricing published transparently on the website—no opaque quotes or “contact us” gates. The elasticity of demand in the SME compliance market favours predictability over premium, so Transcrypt will rely on volume credibility rather than margin inflation: a large base of smaller, loyal customers rather than a few high-paying clients. Periodic market reviews will adjust pricing only to reflect new features or regulatory expansions, maintaining trust through fairness. In sum, Transcrypt’s pricing strategy reflects its character: honest, lean, and customer-aligned—a product that earns payment because it proves its worth every month.

### 8.2 Subscription Tiers and Value Differentiation

Transcrypt’s Subscription Tiers and Value Differentiation are designed to scale naturally with customer maturity while keeping the onboarding experience frictionless. The entry point is the Essential Plan—a single, low-cost subscription that delivers the full compliance journey for Cyber Essentials today, with hooks ready for future Platform upgrades. It includes the essentials: guided self-assessment, tailored risk and action reports, automated evidence tracking, and continuous updates when regulatory guidance changes. This tier is aimed at the micro and small-business segment—the backbone of the UK economy—where simplicity and affordability drive adoption. The Essential Plan’s value lies in clarity: customers receive ongoing, intelligible compliance without the noise or dependency of external consultants. It establishes Transcrypt as a trusted companion rather than a one-time certificate broker.

Above this sits the Professional Plan, targeting SMEs that handle more sensitive data or operate within regulated supply chains. It builds on the Essential Plan features with advanced evidence automation, multi-user role management, and integrations with identity providers, backup systems, and insurers. This tier adds continuous assurance dashboards for Cyber Essentials and, once Phase 2 lands, optional modules for other frameworks. It also includes access to quarterly compliance reviews or AI-assisted report drafting for external auditors when the Platform tier launches. The differentiation here is sophistication, not exclusivity—customers upgrade because they outgrow simplicity, not because functionality is paywalled. The pricing delta reflects measurable value: less manual effort, richer insight, and smoother stakeholder reporting.

At the top end, the Enterprise or Partner Plan is designed for MSPs, insurers, and sector bodies who want to use Transcrypt as a managed or white-labelled service for their own clients. It provides [[Post-MVP: §9.4.2 Partner Channel & Co-Branding]] multi-tenancy controls, API access, and private branding options while maintaining the same underlying rule engine and compliance logic. This tier converts Transcrypt from a standalone platform into a compliance backbone—an engine others can trust and resell. Across all tiers, differentiation is rooted in capability depth and integration, not arbitrary restriction. Every customer, regardless of plan, receives the same data security, transparency, and quality of support. Transcrypt’s subscription structure thus mirrors its engineering ethos: modular, fair, and designed for longevity—each tier a deepening of partnership, not a barrier to entry.

### 8.3 Partner and Reseller Ecosystem

Post-MVP channel strategy (not part of MVP). [[Post-MVP: §9.4.2 Partner Channel & Co-Branding]]

Transcrypt’s Partner and Reseller Ecosystem is a deliberate extension of its business model — a multiplier for reach, trust, and resilience. The ecosystem is built around the idea that compliance is most powerful when distributed through trusted intermediaries who already serve SMEs in adjacent domains: managed service providers (MSPs), insurers, accountants, and sector associations. These partners act as local conduits, embedding Transcrypt into their existing service portfolios to deliver continuous compliance without the need for technical expertise. For them, Transcrypt becomes a plug-in trust layer — an automated platform layer that enhances their own credibility and customer retention. For the platform, it becomes a cost-efficient growth mechanism that replaces traditional sales and marketing with relationship-driven distribution.

The partnership model operates on a white-label or co-branded basis, depending on the partner’s market position and customer relationship. MSPs and IT support firms can deploy Transcrypt as part of their managed security offering, using the platform’s APIs and [[Post-MVP: §9.4.2 Partner Channel & Co-Branding]] multi-tenant dashboard to monitor client compliance at scale. Insurers can integrate it as a live assurance layer within cyber insurance policies, using compliance telemetry to adjust premiums or validate claims. Professional bodies and trade associations can offer it as a member benefit — a digital companion that simplifies certification and risk management. Transcrypt handles hosting, updates, and support centrally, while partners focus on client engagement and value delivery. This division of labour keeps operational complexity low and margins healthy for both sides.

To preserve trust and brand integrity, Transcrypt’s partner ecosystem is governed by clear participation criteria and transparent commercial terms. Revenue-sharing agreements are straightforward — a fixed percentage of each subscription sold through the partner channel, with no lock-in or exclusivity clauses. Partners receive technical onboarding, marketing collateral, and access to a sandbox environment to customise workflows and branding. A dedicated partner portal provides analytics, billing visibility, and joint-customer support tools. The ecosystem will evolve selectively, prioritising depth of relationship over volume of participants. By growing through aligned experts rather than resellers, Transcrypt maintains its reputation for clarity and credibility while multiplying its market reach — turning its partners into trusted amplifiers of both product and philosophy.

### 8.4 Licensing and Legal Terms

Transcrypt’s Licensing and Legal Terms framework is designed to be as clear and trustworthy as the product itself—written in plain English, enforceable in law, and comprehensible to non-specialists. The software is licensed on a subscription basis, granting customers the right to use the platform for the duration of their active plan, with all updates, framework mappings, and technical support included. There are no per-seat restrictions or hidden metering clauses: pricing is tied solely to organisational tier, not individual usage. All intellectual property—including the rule engine, policy mappings, and AI-assisted tooling—remains the property of Transcrypt Ltd., but customers retain full ownership of their uploaded data, evidence, and generated reports. Each account operates as a logically isolated tenant; Transcrypt processes customer-submitted compliance artefacts only and does not collect or process end-user personal data, with all processing locations and sub-processors transparently listed in the Data Processing Agreement (DPA).

Legal governance aligns with UK and EU digital service obligations while remaining lightweight and transparent. The Terms of Service establish mutual responsibilities: users must provide accurate information and comply with lawful use policies, while Transcrypt commits to uptime, data security, and fair access. Service availability targets are defined explicitly, with compensation or credit mechanisms in the event of sustained outages. The Privacy Policy adheres to the principles of data minimisation and purpose limitation, and the DPA specifies encryption, deletion, and audit mechanisms for data subject rights. Optional features that involve AI summarisation or analysis require explicit user consent, with clear disclosure of any third-party model processing. There are no dark patterns, opt-outs disguised as opt-ins, or silent data sharing arrangements—compliance integrity begins with legal integrity.

For partners and resellers, licensing terms extend through a Master Services Agreement (MSA) and standardised reseller addendum. These agreements set out branding rights, revenue-sharing terms, and quality obligations while ensuring that end customers receive identical protections regardless of distribution channel. Transcrypt’s legal stack is maintained as a version-controlled repository, allowing all policy changes to be tracked, reviewed, and timestamped for public reference—an embodiment of its own transparency principles. Liability limits are proportionate to the subscription value, and warranties focus on good-faith accuracy, data protection, and continuity of service rather than speculative indemnities. In short, Transcrypt’s legal framework reflects its ethos: fair, readable, and anchored in accountability. Every term exists to protect trust—the customer’s, the partner’s, and the company’s own.

### 8.5 Metrics for Financial Sustainability

Transcrypt’s Metrics for Financial Sustainability are designed to prioritise durability over speed, using clear, measurable indicators that demonstrate stability, efficiency, and steady growth. The central aim is not hyper-scaling but proving that a single, well-run platform can achieve consistent profitability through recurring revenue and low operational overhead. The first critical milestone is achieving £500 monthly profit by month twelve, confirming that the business can self-fund without external capital. Thereafter, the key metric becomes monthly recurring revenue (MRR) growth balanced against support and infrastructure costs, maintaining a gross margin above 75%. Each new subscriber contributes predictable value, and because churn is expected to be low in compliance-driven markets, revenue compounds steadily. Success is defined not by vanity metrics like user counts or traffic but by runway autonomy—the ability to operate indefinitely on earned income alone.

Secondary metrics focus on customer retention, lifetime value (LTV), and acquisition efficiency. A target retention rate of 90% or higher reflects both product usefulness and customer trust, while LTV to customer acquisition cost (CAC) should maintain a ratio above 3:1, ensuring sustainable growth even with modest marketing. Because Transcrypt’s model relies heavily on referrals and partnerships rather than paid advertising, CAC remains intentionally low, with most acquisition spend reinvested in product refinement. The aim is a virtuous cycle: strong retention feeds organic referrals, which lower acquisition cost, which frees resources for development. Other health indicators include support ticket volume per user (kept below 0.2 per month) and time-to-value metrics—the average number of days before a new user produces their first compliance report, which must remain under seven.

Strategically, Transcrypt measures sustainability not just in profit but in operational efficiency and resilience. Key performance indicators such as uptime, incident recovery time, and automation coverage directly correlate to cost control and trust. Annual audits track the ratio of manual to automated tasks, with the goal of achieving at least 85% automation of repeatable workflows by year two. Profitability is reinvested conservatively—split between technical debt reduction, security enhancements, and gradual feature expansion. These metrics combine to form a simple philosophy of financial governance: growth must serve longevity. By focusing on recurring value, low churn, and operational discipline, Transcrypt ensures that its financial model mirrors its engineering one—lean, transparent, and resilient by design.


<!-- strategic -->
## 9. Roadmap

| Phase | Name              | Focus           | Key Adds                                                       |
| ----: | ----------------- | --------------- | -------------------------------------------------------------- |
|  v1.0 | Transcrypt Essential   | MVP Automation  | Full self-serve flows, no human review paths                   |
|  v1.2 | Tenant Vaults     | Security        | Enhanced Encryption (future)                                   |
|  v1.5 | Assisted Tier (β) | Hybrid Model    | Auditor portal, limited review API, opt-in expert verification |
|  v2.0 | Geo-sovereign Nodes | Scalability    | Regional data anchors, bring-your-own-KMS option               |

Rows from **v1.5 onward mark the Transcrypt Platform wave** and begin only after Transcrypt Essential is profitable.

Enhanced Encryption (future) is a roadmap placeholder for the Platform phase; it is not part of the Transcrypt Essential MVP. [[Post-MVP: Platform Phase]]

Transcrypt’s Roadmap and Delivery Strategy is structured around disciplined iteration: a lean, verifiable path from concept to commercial traction. The strategy reflects a core principle—deliver small, prove value, refine fast. It prioritises the creation of a Minimum Viable Product (MVP) that demonstrates functional credibility and real customer benefit within the first six months, followed by incremental expansions that compound capability rather than complexity. Each phase is defined by a measurable outcome: working software, validated user engagement, and sustainable revenue growth. The emphasis is on building a product that earns trust early, through demonstrable competence and transparency, rather than pursuing scale prematurely.

Delivery is paced deliberately to balance speed with quality. Every milestone is gated by functional completeness and security assurance rather than arbitrary dates. Each release passes through structured acceptance tests—deterministic, documented, and reproducible. Technical progress is managed through a version-controlled development workflow, where all commits, merges, and releases are traceable to defined requirements. The delivery strategy integrates continuous integration and deployment (CI/CD) pipelines from the outset, ensuring that development and compliance are inseparable. In parallel, user testing and feedback loops are embedded into every iteration, capturing behavioural insights that directly inform prioritisation. This approach ensures that Transcrypt evolves with empirical direction, not guesswork.

The roadmap also recognises the constraints and advantages of a founder-led, low-burn operation. Budgets are lean, decisions fast, and infrastructure choices pragmatic. Work is sequenced to avoid technical debt and to reach early self-sustainability, with the initial financial target—£500 monthly profit by month twelve—serving as both proof of viability and validation of market resonance. Partnerships and open collaboration are used to amplify output without expanding payroll: freelance design, modular development contracts, and infrastructure credits substitute for headcount. In total, Transcrypt’s roadmap balances realism and ambition: rapid enough to stay relevant, cautious enough to stay solvent, and methodical enough to create a platform whose quality and credibility become its own form of marketing.

### 9.1 MVP Definition

Transcrypt’s Minimum Viable Product (MVP) is defined not by feature volume but by demonstrable value: the ability to take a small business’s inputs, interpret them intelligently, and return a meaningful, tailored compliance report. The MVP must prove that a single founder can operate and monetise the platform end-to-end — from customer intake through to payment and delivery — without external dependencies. Functionally, it consists of three pillars: a clean intake workflow, a rule evaluation engine, and a report generator. The intake captures company profile and control evidence through guided questions. The rule engine — powered by deterministic logic with LLM-assisted interpretation at build time — maps those responses directly to the Cyber Essentials control set. The report generator returns a clear, actionable summary showing compliance status, gaps, and recommended steps. This is not a prototype; it is the simplest form of the final product, capable of earning revenue from day one.

The MVP must deliver a “one sitting” outcome — a business owner can sign up, complete their intake, and receive a usable compliance assessment within an hour. Automation replaces human consulting, yet the tone and accuracy must equal that of a skilled professional. Output will include a branded, downloadable PDF with executive summary, detailed control mapping, and a prioritised action plan. Data persistence, authentication, and payment collection will be lightweight but production-grade: a managed Postgres database, an OAuth-based login, and Stripe integration for subscriptions. Evidence upload and storage will use secure object storage with file hashing for integrity verification. Each of these features directly underpins monetisation, credibility, and compliance, avoiding any “demo-only” components that would later need to be rewritten.

Success criteria for the MVP are clear and measurable. First, functional validation — a minimum of five real users completing the workflow and receiving reports without manual intervention. Second, performance validation — a complete intake and report cycle in under ten minutes of processing time. Third, economic validation — at least three paying customers and a positive monthly margin. Beyond these metrics, qualitative success is defined by trust: users describing the platform as simple, accurate, and worth paying for. This first iteration forms the commercial and technical nucleus of Transcrypt — a credible, automated compliance companion that proves the concept, pays for its own evolution, and establishes the data and design foundations for all future features.

### 9.2 Phase Milestones and Timelines

Transcrypt’s delivery plan runs in two waves:

- **Phase 1 – Transcrypt Essential (Months 1–6):** Build, prove, and monetise the Cyber Essentials-only product.
  - *Foundation (Months 1–3):* Intake workflow, rule engine limited to Cyber Essentials, report generation, secure hosting, and payment plumbing.
  - *Validation (Months 4–6):* Live onboarding of SMEs, UX polish, evidence reminders, and first renewal cycle rehearsals. Success metric: three paying customers and >90% task completion without manual intervention.
- **Phase 2 – Transcrypt Platform (post-MVP):** Heavier features land only after Transcrypt Essential is profitable.
  - *Expansion (target Months 7–12):* Optional Assisted Tier beta, partner experiments, and preparation work for multi-framework mapping. All non-Cyber Essentials controls remain behind feature flags until Platform launch.
  - *Stabilisation (after Transcrypt Essential profitability):* Harden collaboration tooling, explore additional frameworks, and prepare the hosted service for regional deployment. These items are gated until Phase 2 funding and capacity are confirmed.

The split keeps the initial six months laser-focused on making Cyber Essentials effortless while clearly signalling that anything broader belongs to the follow-on Transcrypt Platform programme.

#### Post-MVP: Platform Phase Highlights

- Proof-of-Process Ledger to notarise audit hashes against an external distributed log. [[Post-MVP: Platform Phase]]
- Independent auditor verification API for attestations without code exposure. [[Post-MVP: Platform Phase]]
- Reproducibility review programme for components under NDA. [[Post-MVP: Platform Phase]]

#### Partner/Integrator API (v2.0)

Delegated, read-only posture for MSPs/insurers; outbound webhooks. Not in v1.

### 9.3 Resource and Budget Planning

Transcrypt’s Resource and Budget Planning framework is built on lean engineering discipline — the philosophy that constraints drive clarity. As a single-founder venture, resources are allocated with surgical precision to maximise impact per pound. The goal is to prove sustainability before scale: every expense must either accelerate product delivery, enhance credibility, or directly support paying users. The total cash outlay during the first 12 months is intentionally modest, targeting £2,500–£3,000 in total operating spend, excluding the founder’s time. This covers cloud hosting, development tooling, domain and licensing fees, and small discretionary marketing outlay. Infrastructure costs are controlled through reserved credits and usage-based scaling, ensuring that monthly operating costs remain below £100 until profitability. The founder provides engineering, product, and compliance expertise in-house, reducing external dependency to near zero during the first year.

Human resources follow a concentric model. The inner ring consists of the founder’s core engineering and architecture work, supported occasionally by freelance specialists for discrete deliverables—UX design, content editing, and security review—engaged on fixed-price contracts. The second ring comprises strategic collaborators and early partners (e.g., MSPs, insurers, or compliance auditors) who participate in testing and feedback rather than payroll. The outer ring—eventual hires or retained contractors—is deferred until recurring revenue comfortably exceeds operating costs. This model keeps the organisation flat, capital-efficient, and adaptive while enabling expertise injection precisely when needed. All coordination occurs within a lightweight toolchain: GitHub for source control and issues, Trello or Linear for backlog management, and shared documentation through Notion or Markdown repositories.

Budget allocation mirrors this simplicity. Approximately 40% of the initial budget is assigned to cloud infrastructure (DigitalOcean or comparable provider with storage and compute scaling), 30% to professional and legal services (terms of service drafting, insurance, accounting), 20% to content and design polish for launch, and 10% to discretionary marketing and testing incentives. Capital expenditure is avoided entirely—no office space, servers, or permanent staff until profitability. Financial monitoring uses basic but effective metrics: burn rate, monthly recurring revenue, and cash runway, each tracked against a rolling 90-day forecast. Every pound spent must reduce uncertainty or increase revenue potential. In effect, the resource plan is a live experiment in disciplined entrepreneurship—building a serious product within self-imposed limits that enforce both creative focus and long-term viability.

### 9.4 Risk Register and Mitigation

Transcrypt’s Risk Register and Mitigation framework is the operational embodiment of its engineering philosophy: every risk is documented, measurable, and actionable. The register is maintained as a version-controlled artefact, reviewed quarterly, and categorised across four dimensions—technical, operational, financial, and strategic. Each entry defines the risk description, likelihood, potential impact, owner, and mitigation strategy, with real-time updates whenever control effectiveness changes. Risks are ranked on a five-point scale for probability and severity, producing a live heat map that feeds directly into roadmap prioritisation. This approach ensures that mitigation is not reactive or bureaucratic but built into the product’s evolution: risks drive sprints, tests, and design improvements, not afterthoughts or excuses.

Technical risks centre on platform security, AI reliability, and infrastructure integrity. Mitigations include defence-in-depth architecture, automated testing, regular dependency audits, and isolation of AI components from production decision paths. Security posture is verified continuously through penetration tests and red–blue exercises, while cryptographic controls (encryption, signed builds, SBOMs) minimise the blast radius of compromise. Operational risks—such as cloud service disruption or key-person dependency—are reduced through infrastructure-as-code deployments, daily backups, and documented recovery workflows. Critical configurations are mirrored across availability zones, and a part-time external security consultant will periodically validate operational readiness to provide external assurance.

Financial and strategic risks revolve around cash flow volatility, customer acquisition pace, and competitive pressure. These are mitigated through a deliberately low burn rate, revenue diversification via partnerships, and maintaining full intellectual property ownership. Pricing agility ensures the ability to adjust quickly to market conditions without alienating early adopters. Reputational risk—central to a trust-based product—is addressed by embedding transparency into every process: changelogs, incident disclosures, and code provenance are publicly verifiable. Finally, a small number of regulatory risks—such as interpretation errors in compliance frameworks—are managed through continuous dialogue with advisors and the use of verifiable legislative sources. In essence, Transcrypt’s risk register doubles as a design compass: a living record of what could go wrong and the systematic measures ensuring it rarely does, and never without leaving a clear audit trail.

#### 9.4.1 Assisted Tier & Collaboration (Post-MVP) {#assisted-tier}

- **Milestone:** Targeted for v1.5 “Assisted Tier β” after Transcrypt Essential self-serve reliability is proven.
- **Collaboration scope:** Invite-only auditor and consultant roles operating strictly within tenant boundaries; no cross-tenant visibility. [[Post-MVP: §5.2 Machine Learning and AI Components (v1)]]
- **Workflow additions:** Assignment queues, escalation paths, and reviewer hand-offs that keep ownership clear while preserving audit trails.
- **Shared workspaces:** Controlled comment threads, attest/reject loops, and evidence request prompts surfaced to both SME owners and approved professionals.
- **Access controls:** Time-boxed links, granular permissions, and enforced NDAs with logging to prevent accidental data leakage.
- **Evidence hygiene:** Reviewer uploads and annotations are hashed, versioned, and bound to the originating control—no parallel storage or off-platform exchange.
- **Non-goals:** No open marketplace listings, no unsolicited reviewer access, and no revenue-share matchmaking—participation is contractual and curated.

#### 9.4.2 Partner Channel & Co-Branding (Post-MVP)

- **Milestone:** Planned for v2.0 “Partner Channel GA” once Assisted Tier usage validates collaborative flows.
- **Channel objective:** Enable managed service providers, insurers, and associations to distribute Transcrypt through co-branded experiences without exposing an open marketplace.
- **Provisioning model:** License keys and tenant bundles issued per partner contract, with centralised billing, revoke controls, and audit logs for every activation.
- **Brand controls:** Theme packs and co-branded templates configurable within guardrails—core UX, security posture, and messaging remain consistent.
- **Operational tooling:** Partner portal surfaces aggregated analytics, delegated support tickets, and curated knowledge bases; APIs expose read-only posture data with throttling. [[Post-MVP: §3.4 Extensibility and Integration Framework]]
- **Revenue mechanics:** Transparent revenue-share or referral credits settled monthly, documented in the traceability table and partner agreements.
- **Enablement:** Sandbox environments, certification paths, and launch playbooks provided before go-live to ensure partners uphold compliance standards.
- **Non-goals:** No public app store, no self-signup resellers, and no uncontrolled tier creation—every channel participant is vetted and governed.

### 9.5 Quality Assurance and Acceptance Criteria

Transcrypt’s Quality Assurance and Acceptance Criteria are designed to ensure that every release—no matter how small—meets the same standards of precision, stability, and integrity that define its compliance ethos. Quality is not treated as a final gate but as a continuous state, achieved through automation, version control, and human review. The QA framework spans the entire lifecycle: requirement definition, code implementation, testing, deployment, and post-release validation. Every requirement is expressed as a verifiable condition—“what done looks like”—and mapped to acceptance tests that run automatically within the CI/CD pipeline. This deterministic approach ensures that compliance, security, and functionality are tested in one integrated process, not as separate afterthoughts. No feature can be released unless it satisfies its acceptance criteria, passes all regression and security tests, and generates reproducible results in staging.

The testing framework combines static and dynamic validation. Unit tests verify logic consistency in the rule engine and evidence mapping; integration tests confirm that authentication, API, and report generation components behave correctly across boundaries. End-to-end tests simulate real customer workflows—from intake to report delivery—executed through scripted environments to ensure predictable behaviour under load. Automated security scans, dependency vulnerability checks, and licence audits run on every build, with failures blocking deployment until resolved. For AI-assisted components, deterministic outputs are compared against stored “golden files” to prevent drift or hallucination. Every build produces a signed test report artefact stored in the project’s audit ledger, creating permanent evidence of compliance with the defined acceptance criteria.

Acceptance criteria themselves follow a simple triad: functional, security, and user validation. Functionally, the product must deliver accurate and complete results under defined inputs; security-wise, all data must remain encrypted, access-controlled, and free from known vulnerabilities; from a user perspective, the experience must remain clear, intuitive, and error-free within a standard use session. Releases are not accepted by date but by evidence—passing tests, verified results, and documented peer review. Post-release telemetry further validates performance, latency, and reliability against service-level targets (e.g., 99.9% uptime, sub-second API response). Any regression automatically reopens its related requirement for correction, closing the loop between QA and roadmap. This framework turns assurance into a living discipline: every accepted release is not only functional but provably compliant with the same rigour Transcrypt will one day automate for its customers.


<!-- strategic -->
## 10. Future Outlook and Strategic Extensions

Transcrypt’s Future Outlook and Strategic Extensions represent the natural evolution of a platform designed from the start to be adaptive — technically, commercially, and ethically. The product’s immediate purpose is to simplify UK SME compliance, but its architecture and data model are intentionally global and extensible. By structuring every rule, evidence item, and report output as interoperable objects, Transcrypt can evolve into a multi-framework, multi-jurisdictional compliance fabric — one that adjusts automatically as new regulations appear or existing ones converge. The long-term strategy is to make compliance continuous, contextual, and border-agnostic: a layer of digital assurance that translates government language into operational reality for businesses of any size.

This forward trajectory rests on measured innovation, not speculation. As AI and automation mature, Transcrypt will expand beyond reactive compliance to predictive governance — identifying emerging risks and recommending pre-emptive controls before regulators demand them. The same mechanisms that interpret rule logic today can later benchmark security posture, simulate audit scenarios, and even validate controls in real time against live telemetry feeds. In parallel, the platform’s foundation in applied cryptography and transparency positions it to integrate with distributed trust infrastructures — from verifiable credentials to [[Post-MVP: §9.4 Risk Register and Mitigation]] blockchain-backed attestations — where compliance proofs can be shared securely across supply chains. The future product family thus grows not by bolt-on features but by deepening its capacity to measure, verify, and explain trust.

Strategically, Transcrypt’s outlook is pragmatic and sustainable. Expansion will follow credibility, not hype: first consolidating UK market dominance, then extending into EU, Commonwealth, and allied jurisdictions where data sovereignty and trust frameworks align. Each geographic expansion will be accompanied by localised regulatory mapping, native-language interfaces, and partnership with in-country experts. The company’s structure will remain lean and founder-led, scaling through partnerships, licensing, and white-label channels rather than capital-intensive hiring. Every strategic extension must meet three conditions — technical feasibility, ethical defensibility, and customer relevance. In short, the outlook is neither utopian nor defensive: Transcrypt’s future lies in making regulatory complexity not just manageable but measurable, turning compliance from a burden into a continuous competitive advantage.

### 10.1 Interoperability with Other National Frameworks

Transcrypt’s Interoperability with Other National Frameworks is a core strategic enabler — the bridge between a UK-born compliance engine and a globally adaptable assurance platform. From inception, the platform has been designed around framework abstraction, meaning each control, rule, and evidence object exists independently of jurisdiction. A rule in Cyber Essentials (“MFA for administrative accounts”) can map directly to equivalent clauses in NIST 800-53, CIS Controls, or ISO 27001 Annex A, with metadata defining its origin, scope, and equivalence relationships. This architecture allows the same intake and evaluation pipeline to be repurposed for other countries simply by swapping in new framework definitions and legislative mappings, without altering the core logic. The result is a platform that can grow horizontally — serving Canada, Australia, the EU, and beyond — through data, not code.

Operationally, interoperability will begin with regulatory clusters, starting with the EU (NIS2, DORA, GDPR) and the Commonwealth markets that share similar legal and risk management philosophies. Frameworks are imported as structured data packs, each containing control definitions, reference citations, and evidence schemas. A translation layer aligns terminology and severity across frameworks, so that a UK client expanding into the EU can reuse 80–90% of their existing compliance data automatically. This approach doesn’t just enable new markets; it simplifies cross-border certification for businesses operating under multiple regimes. Over time, Transcrypt could offer “compliance compilers” — automatically generated gap analyses showing which controls are satisfied globally and where local divergence remains.

Technically, interoperability is achieved through open schemas and exportable assurance data. All framework definitions, evidence mappings, and reports can be expressed in standardised formats such as JSON-LD or XDR (eXtensible Data Representation), allowing easy exchange with regulators, auditors, and partner platforms. The platform’s REST and GraphQL APIs will support both import and export of compliance data, positioning Transcrypt as the connective tissue between regional ecosystems. Future integrations may include direct alignment with machine-readable legislation repositories and government trust frameworks. By designing for portability from the outset, Transcrypt becomes not merely a UK compliance platform but a universal translator for digital assurance — one capable of understanding and contextualising trust wherever it’s defined.

### 10.2 Research and Development Themes

Transcrypt’s Research and Development Themes define how the platform will evolve intellectually as well as technically — ensuring it stays not just current, but pioneering in its understanding of digital assurance. The guiding principle is that compliance, security, and automation are converging disciplines, and innovation must serve the long game: reducing human toil while increasing verifiability. Research therefore focuses on four intersecting threads — explainable automation, dynamic assurance, applied cryptography, and policy intelligence. Each thread deepens the platform’s ability to reason about risk, interpret regulation in context, and prove trust through evidence.

The first major R&D theme is explainable automation, developing methods for making AI-assisted compliance interpretable and defensible. Transcrypt will continue to use deterministic rule evaluation as its foundation, but future models will explore hybrid architectures where machine learning assists in evidence classification, text interpretation, and anomaly detection — all under transparent, auditable logic. Research into natural-language grounding and rule extraction from legislative texts will enable the platform to ingest and structure new regulations automatically. This moves compliance from a manual curation task to a semi-autonomous function that keeps pace with the law.

The second thread, dynamic assurance, aims to transform compliance from static reports into continuous measurement. Future iterations will integrate telemetry from security tooling, cloud configurations, and identity providers, translating real-time signals into live compliance posture updates. Complementary research in applied cryptography will investigate ways to make those attestations verifiable through decentralised proofs, using techniques such as zero-knowledge attestations, Merkle-signed audit trails, and verifiable credentials. The fourth R&D theme, policy intelligence, focuses on pattern discovery across anonymised customer data — identifying systemic weaknesses in SME security postures and feeding them back into the platform’s guidance engine. Collectively, these themes point toward a future where Transcrypt functions as more than a static compliance platform — it becomes a living observatory of cyber health, translating raw operational reality into policy insight and regulatory foresight.

### 10.3 Potential Spin-offs and Product Lines

Transcrypt’s Potential Spin-offs and Product Lines represent the natural diversification of a platform that treats compliance data as structured intelligence rather than static paperwork. Once the core engine—rule evaluation, evidence management, and reporting—is established, the same architecture can underpin several adjacent products, each serving a different slice of the trust ecosystem. These extensions allow the company to grow laterally without bloating the core offering, reusing the same underlying data model, and differentiating primarily through interface, integration, and market positioning. The overarching principle is reuse of logic, repackaging of value: one compliance brain, many specialised expressions.

The most immediate spin-off opportunity is Transcrypt for Insurers—a live assurance companion that feeds compliance posture directly into cyber-insurance risk models. SMEs using the base platform could opt-in to share continuous assurance data with underwriters, enabling dynamic premium pricing and faster claims validation. Parallel to this sits Transcrypt Partner Hub, a white-label version for MSPs and auditors who need [[Post-MVP: §9.4.2 Partner Channel & Co-Branding]] multi-tenant dashboards to manage client compliance portfolios. Over time, a Transcrypt Lite edition could target micro-enterprises and sole traders, offering a guided “compliance in an afternoon” experience with simplified evidence requirements and automated report generation—a low-touch, high-volume product optimised for direct self-service sales.

Longer-term product diversification looks outward to the data economy. A TrustGraph API could expose anonymised, aggregated compliance trends to research institutions, insurers, and policy analysts, creating a data-as-a-service stream that helps quantify SME cyber-maturity across sectors and regions. Another trajectory leads into Transcrypt Verify, a credentials and attestation product that allows suppliers to issue digitally signed proof of compliance—verifiable by customers or regulators without revealing proprietary data. Finally, a developer-facing SDK would let third-party platforms embed Transcrypt’s rule-evaluation logic into their own ecosystems, expanding reach without operational overhead. Each spin-off reinforces the core mission: converting compliance from an administrative burden into an ecosystem of living, portable trust signals.

### 10.4 Long-Term Sustainability and Ethical Charter

Transcrypt’s Long-Term Sustainability and Ethical Charter defines the principles by which it intends to endure—not just financially, but socially and technologically. The platform is built to outlast hype cycles by adhering to three durable commitments: pragmatism, transparency, and proportionality. Pragmatism governs its business model—profitable at small scale, restrained in expenditure, and growing only as utility and reputation justify it. Transparency governs its technology—open schemas, traceable AI decisions, auditable code, and verifiable change histories. Proportionality governs its ethics—automation used to clarify and empower, not to obfuscate or replace human judgement. The charter formalises these as binding operational tenets: Transcrypt will always make its decisions explainable, its data ownership unambiguous, and its use of automation accountable.

Environmental and social sustainability form the second axis of the charter. As a digital-first company with a light physical footprint, Transcrypt’s environmental policy focuses on energy efficiency and responsible compute. Cloud workloads are geographically located to maximise renewable energy use, and model training is minimised through reuse of pre-trained architectures and inference-efficient design. Data retention policies are conservative—storing only what is necessary and deleting when legal or operational value expires. Socially, the company commits to accessibility and inclusion: interfaces readable by non-specialists, content available in plain English (and later, multilingual form), and pricing that keeps compliance attainable for small organisations. Compliance itself becomes a democratizing act—the levelling of security literacy across economic tiers.

Ethically, Transcrypt recognises that the power of automation in compliance must be balanced by human interpretability and moral restraint. The Ethical Charter codifies this balance through explicit prohibitions: no use of AI for deceptive content generation, dark-pattern onboarding, or data resale. AI-generated outputs must always be traceable, reviewable, and reversible. Transparency about model limitations is mandatory; users are told where AI ends and logic begins. Governance of the charter itself is participatory—reviewed annually with input from users, partners, and advisors, and published openly with tracked revisions. In this way, sustainability and ethics are not appendices to the business—they are its scaffolding. Transcrypt’s long-term vision is to be trusted not because it claims virtue, but because its architecture and operations make virtue measurable.

### 10.5 Closing Summary

Transcrypt exists to make compliance intelligible, provable, and continuous for small and mid-sized businesses. The platform converts legislation and frameworks into structured rules, guides users through clear actions, and links every claim to evidence. The result is not a certificate factory but an operating companion: a steady, comprehensible path from obligation to assurance.

The market is noisy and polarised. On one side are low-cost portals that stop at form-filling; on the other, heavyweight GRC suites that few SMEs can afford or run. Transcrypt sits in the missing middle. It interprets rather than obscures, automates without theatrics, and speaks in plain English. Brand credibility comes from quiet competence and transparent mappings, not jargon or fear.

Architecturally, the platform is built for trust. Identity is first-class, data is encrypted by default, builds are signed, and every control is testable. Policies live as versioned objects, evidence is anchored to those objects, and changes are traceable. Security, resilience, and supply-chain integrity are not appendices; they are the substrate that lets auditors, partners, and customers accept the output without squinting.

Commercially, the plan is pragmatic. A single founder can deliver an MVP that earns revenue on day one: intake, rule evaluation, and a usable report. Year one is about validation and discipline, not scale. The financial target is simple and explicit: reach a clean £500 monthly profit by month twelve by keeping costs lean and value obvious. Growth follows credibility, then partnerships, not ad spend.

Roadmap execution is iterative and test-led. Each release is gated by acceptance criteria that combine function, security, and user clarity. Evidence of quality is produced as a routine by-product of development. When incidents occur, they leave an audit trail and a permanent improvement. That is how a small company builds large trust.

Strategically, Transcrypt is designed to travel. The rule engine treats frameworks as data, so expansion to NIS2, DORA, and other jurisdictions is translation work, not reinvention. Over time, the same machinery can power insurer attestations, partner dashboards, and verifiable credentials that move along supply chains without exposing raw data.

The ethical stance is explicit: clarity over theatre, proportionality over bloat, and transparency over dark patterns. Users own their data. AI is assistive and explainable. Legal terms are readable. The company remains small, solvent, and accountable.

In short, Transcrypt turns compliance from an annual scramble into a steady state. It lowers the cognitive load, raises the evidential bar, and earns trust by design. Ship the MVP, prove the loop, compound the value.


## Cross-Referencing Framework

Transcrypt’s PRD maintains traceability across strategic intent, technical design, and roadmap phases.

Each reference follows the pattern:  
**[§X.Y – Topic]** for backward links, or **[[Post-MVP: §9.2 Phase Milestones and Timelines]]** for deferred features.

| Tag | Meaning | Example |
|:----|:--------|:--------|
| **[↩ S#]** | Refers back to a Strategic section (Vision, Market Context). | “[↩ S2]” = Vision §2. |
| **[↩ A#]** | Refers back to an Architectural or System section. | “[↩ A3.2.3 – Rule Evaluation Service]”. |
| **[[Post-MVP: §9.2 Phase Milestones and Timelines]]** | Denotes a dependency deferred to Roadmap phase. | “Auditor Portal [[Post-MVP: §9.2 Phase Milestones and Timelines]].” |
| **[→ UX#]** | Points forward to a UX section once drafted. | “Dashboard [→ UX6.3].” |

All future internal links must use these tags so dependencies can be traced programmatically.

### Strategic/Technical Markers (Legacy)

To maintain coherence between strategy and specification:

- **(S)** → refers to a strategic concept or intent.
- **(T)** → refers to a technical requirement or implementation detail.
- When both are relevant, use **(S/T)**.

Example: “Automation ensures consistent SME outcomes (S/T).”

## Appendices
All examples refer to artefacts generated or consumed within the Transcrypt web platform.

### A. Terminology and Abbreviations

**Law (within this PRD)** — References to “law” mean the official Cyber Essentials scheme documentation and IASME guidance; wider legislation is out of scope for Transcrypt Essential.

**Regulation (within this PRD)** — Used interchangeably with the above Cyber Essentials guidance when describing required actions.

**Tenant** — A single SME customer space in the hosted service, logically separated from others but running on the shared Transcrypt Essential infrastructure.

**Audit Confidence** — The ability for an SME to show clear evidence, timestamps, and change history for Cyber Essentials controls without needing external attestations.

**Verifiable Transparency** [[Post-MVP: Platform]] — Future advanced data trust mechanism where a closed-source system provides mathematically verifiable evidence of integrity (hashes, signatures, deterministic logs) in place of source disclosure; not part of Transcrypt Essential.

**Compliance Pack** — A signed configuration bundle defining a specific regulation or framework (controls, scoring logic, mappings, labels).
Enables multi-framework operation without code changes.

**Centrally Orchestrated, Locally Encrypted SaaS** [[Post-MVP: Platform]] — Future deployment pattern where a central service handles coordination and updates but relies on tenant-held keys; not part of Transcrypt Essential.

### B. Reference Documents
> **[[Placeholder]]** Section under development.  \
> Dependencies from §5 and §4 tagged accordingly.  \
> See Traceability Table for cross-section linkage.
### C. Competitive Matrix

#### UK SME Cybersecurity Compliance Landscape

##### Introduction: SME Cybersecurity Obligations in the UK

Small and medium-sized enterprises (SMEs) in the UK face increasing cybersecurity obligations driven by government mandates and industry standards. Key drivers include the government-backed Cyber Essentials scheme, the Network and Information Systems (NIS) Regulations, and evolving guidance for critical infrastructure protection. For example, [Cyber Essentials (a set of five basic security controls) has become a de-facto minimum standard](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=Created%20and%20backed%20by%20the,to%20their%20customers%20and%20stakeholders) – it is even required for vendors handling certain sensitive data in UK government contracts. Meanwhile, the NIS Regulations 2018 impose cybersecurity and breach-reporting duties on operators of essential services and [certain digital service providers](https://legalvision.co.uk/data-privacy-it/nis-compliance/#:~:text=,advice%20to%20manage%20overlapping%20obligations). Upcoming updates (inspired by the EU’s NIS2 Directive) are expected to broaden these requirements to more sectors and mid-sized companies, further raising the compliance bar. Beyond these, SMEs must also heed data protection security requirements (UK GDPR) and industry-specific advisories from the National Cyber Security Centre (e.g. the Cyber Assessment Framework for critical sectors). In short, UK SMEs are under growing pressure to implement governance, risk, and compliance (GRC) measures to manage cyber risks and demonstrate resilience. 

Meeting these obligations can be challenging for resource-constrained businesses. This has fueled a market for tools and services that help SMEs achieve compliance – from attaining Cyber Essentials certification to maintaining ongoing security controls aligned with regulations. Below, we survey the competitive landscape of UK companies (and international players active in the UK) offering such tools and facilities. We’ll cover their offerings, pricing models, market presence, and other relevant info, followed by a summary comparison table.

##### Key Compliance Frameworks & Requirements for UK SMEs (Context)

Before comparing vendors, it’s useful to understand the main frameworks/mandates in play:
 - **Cyber Essentials (CE)** – [A UK Government-backed certification](https://www.isms.online/cyber-essentials/#:~:text=Cyber%20Essentials%20,Certification%20Simplified) with two levels (basic and Plus). [It specifies 5 technical controls (firewalls, secure configuration, access control, malware protection, patch management)](https://www.isms.online/cyber-essentials/#:~:text=Control%20Risk%20Blocked%20Compliance%20Role,Board%20risk%20report%20Contract%20losses). [CE certification is valid for 12 months](https://www.gov.uk/government/statistical-data-sets/cyber-essentials-management-information#:~:text=These%20statistics%20show%20the%20number,CE) and is increasingly seen as a minimum cybersecurity badge. Many SMEs pursue CE to boost trust and because it’s [mandated for certain government supply chain contracts](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=Created%20and%20backed%20by%20the,to%20their%20customers%20and%20stakeholders). CE Plus adds an independent audit of those controls.
 - **NIS Regulations** – UK law (since 2018) implementing the EU NIS Directive, focused on operators of essential services (energy, water, transport, health, etc.) and certain digital service providers. It requires robust cyber risk management, [incident reporting, and auditing by regulators](https://legalvision.co.uk/data-privacy-it/nis-compliance/#:~:text=,advice%20to%20manage%20overlapping%20obligations). While targeted at critical infrastructure (often larger firms), some medium-sized suppliers and IT service providers to those sectors may also fall in scope. The NIS regime is being updated; NIS2 (an EU update) broadens the sectors and lowers size thresholds – the UK is expected to introduce similar enhancements to cover more “important” entities by 2024–2025. This means more mid-size companies (including some SMEs) will need to formalize their cybersecurity GRC (policies, risk assessments, controls, incident response plans, etc.).
 - **Governance and Advisory Frameworks** – Aside from formal mandates, SMEs often choose to adopt standards like ISO/IEC 27001 (information security management) or follow NCSC best practices (such as the 10 Steps to Cyber Security or the NCSC Cyber Assessment Framework for essential services). While not laws, these help meet obligations (e.g. ISO 27001 certification can demonstrate good practice to regulators or partners). The UK government’s Cyber Essentials is essentially a [subset of such controls, aimed at basic cyber hygiene](https://www.isms.online/cyber-essentials/#:~:text=breaches%2C%20customer%20trust%20evaporating%20overnight,any%20policy%20presentation%20ever%20could). Additionally, sectors have specific guidance (e.g. the NHS DSP Toolkit for healthcare, or the Telecom Security Act requirements for telecom providers). SMEs that provide critical products or services must keep an eye on these evolving advisories.

In summary, UK SMEs today may need to certify or demonstrate compliance with one or multiple frameworks to satisfy legal requirements or customer expectations. This has led to a range of solution providers that help businesses manage policies, implement controls, monitor compliance continuously, and pass audits/certifications.

##### Competitive Landscape: Compliance Solution Providers for UK SMEs

A number of companies offer software tools or integrated services to help UK SMEs achieve cyber security compliance and governance objectives. These range from local UK startups focusing on SME needs, to global Software-as-a-Service platforms, to traditional enterprise GRC (Governance, Risk & Compliance) systems (often overkill for SMEs). Below we detail the major players, including their offerings, target market, pricing approach, and any available market share or usage indicators:

##### CyberSmart (UK) – [Cyber Essentials Compliance Made Easy](https://finch-ts.co.uk/top-cybersecurity-risk-management-tools-uk-smes/#:~:text=,and%20Cybersecurity)

**CyberSmart** is a London-based company purpose-built for SMEs’ compliance needs. Founded in 2017 through a GCHQ accelerator, it provides an all-in-one platform that streamlines Cyber Essentials certification and [continuous security monitoring](https://www.capterra.co.uk/software/203257/cybersmart#:~:text=Born%20in%202017%20from%20a,our%20mobile%20and%20desktop%20apps). CyberSmart’s cloud platform deploys lightweight agents on endpoints to continuously scan for security issues (unpatched software, config changes, etc.) and [reports to a dashboard](https://assets.applytosupply.digitalmarketplace.service.gov.uk/g-cloud-13/documents/707477/951169144457475-pricing-document-2022-05-17-1347.pdf#:~:text=CyberSmart%20is%20the%20easiest%20way,to%20get%20you%20ready%20for). It flags what needs fixing to meet the Cyber Essentials controls and even offers in-app guidance or consultant support (via partners) [to remediate gaps](https://assets.applytosupply.digitalmarketplace.service.gov.uk/g-cloud-13/documents/707477/951169144457475-pricing-document-2022-05-17-1347.pdf#:~:text=CyberSmart%20software%20continuously%20scans%20your,Contact%20Us). Uniquely, CyberSmart can facilitate “same-day” Cyber Essentials certification online – they are an IASME-approved certification body, so businesses can get [certified quickly through the app](https://www.capterra.co.uk/software/203257/cybersmart#:~:text=Born%20in%202017%20from%20a,our%20mobile%20and%20desktop%20apps). The solution also bundles perks like cyber insurance (e.g. £25k coverage) for [certified customers as an added incentive](https://finch-ts.co.uk/top-cybersecurity-risk-management-tools-uk-smes/#:~:text=,and%20Cybersecurity).

**Pricing model**: CyberSmart is sold as a SaaS subscription, priced by company size (number of devices/users). It’s very SME-friendly: starting at around £49 per month [for small organisations](https://www.capterra.co.uk/software/203257/cybersmart#:~:text=Local%20product), with tiers scaling upward for larger user counts (e.g. ~£90/month for 1–9 users in a bundle that includes CE certification and the [Active Protect](https://assets.applytosupply.digitalmarketplace.service.gov.uk/g-cloud-13/documents/707477/951169144457475-pricing-document-2022-05-17-1347.pdf#:~:text=2%20CyberSmart%20CyberSmart%20is%20the,finding%20and%20implementing%20a%20solution) monitoring [service](https://assets.applytosupply.digitalmarketplace.service.gov.uk/g-cloud-13/documents/707477/951169144457475-pricing-document-2022-05-17-1347.pdf#:~:text=,4)). This low entry price makes it affordable for micro and small businesses. (The Cyber Essentials certification fee itself is included in such bundles, which is notable since a basic CE assessment alone typically costs ~£300+VAT for micro companies via [IASME](https://iasme.co.uk/cyber-essentials/frequently-asked-questions/#:~:text=Frequently%20Asked%20Questions%20).)

**Market share and usage**: CyberSmart has gained significant traction in the UK SME market – as of early 2023 it was reported to be protecting [over 4,000 small businesses in the UK](https://www.iqcapital.vc/news/cybersmart-raises-15m-for-an-all-in-one-cybersecurity-and-insurance-solution-targeting-smbs-2#:~:text=regardless%20%E2%80%94%20has%20closed%20a,4%20million). Many of these are at the 10–50 employee size. The company has also partnered with managed service providers (MSPs) and [insurance firms to reach more customers](https://www.iqcapital.vc/news/cybersmart-raises-15m-for-an-all-in-one-cybersecurity-and-insurance-solution-targeting-smbs-2#:~:text=CyberSmart%20currently%20has%204%2C000%20customers,home%20market%20as%20well%20as), indicating a strategy of [scaling through channels](https://www.iqcapital.vc/news/cybersmart-raises-15m-for-an-all-in-one-cybersecurity-and-insurance-solution-targeting-smbs-2#:~:text=called%20in%20the%20U,security%20piece%20of%20that%20offering). With a Series B funding in 2023, CyberSmart is expanding internationally, but the UK remains its core market. [Given ~51,000 total Cyber Essentials certificates were issued in the year to mid-2025](https://www.gov.uk/government/statistical-data-sets/cyber-essentials-management-information#:~:text=Certificates%20awarded%20under%20the%20scheme,are%20valid%20for%2012%20months), CyberSmart’s user base suggests a substantial share of SMEs are opting for its platform (either directly or via consultants) to achieve and maintain certification.

**Key differentiators**: Simplicity and specialization for Cyber Essentials. CyberSmart combines an easy app (no prior security expertise needed) with compliance-as-a-service. [It continuously monitors compliance post-certification to ensure the SME stays secure](https://www.capterra.co.uk/software/203257/cybersmart#:~:text=Born%20in%202017%20from%20a,our%20mobile%20and%20desktop%20apps). This ongoing aspect plus included insurance set it apart from one-off consulting. In essence, CyberSmart is positioned as an affordable “compliance on autopilot” tool for UK small businesses.

##### Drata (US) – Automated GRC Platform with UK Framework Support

**Drata** is a well-known U.S.-based **security compliance automation platform** that expanded into the UK market. It started by automating frameworks like SOC 2 and ISO 27001 for cloud startups, and in September 2023 Drata **added support for the UK Cyber Essentials** [scheme](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=LONDON%2C%20Sept,Plus%2C%20which%20requires%20independent%20verification). This means Drata’s platform now has built-in mappings and controls for CE’s requirements, allowing UK companies to use Drata to prepare for certification. Drata provides **continuous control monitoring, automated evidence collection, policy templates, and an auditor collaboration** [portal](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=Features%20of%20Drata%27s%20Cyber%20Essentials,launch%20include) – essentially replacing spreadsheets and reducing the manual workload of compliance. Notably, it can **monitor compliance with CE controls on an ongoing basis** (e.g. checking that patching is up to date, passwords meet criteria, etc.), which helps ensure the organisation [remains compliant year-round](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=Features%20of%20Drata%27s%20Cyber%20Essentials,launch%20include). For the more advanced **Cyber Essentials Plus**, Drata offers guidance but that level still requires an independent [audit outside the tool](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=LONDON%2C%20Sept,Plus%2C%20which%20requires%20independent%20verification).

**Pricing model**: Drata is offered as an annual SaaS subscription, typically priced based on the number of employees and which compliance frameworks are needed. Exact pricing isn’t public (quotes are custom), but it is generally at a higher price point than basic tools – more in line with the value of saving auditor time and combining multiple compliance standards. Many tech SMEs report Drata (and similar rivals) often start in the **low five-figure** range annually for a small company, covering a couple of frameworks. Drata emphasizes the ROI by claiming **automation saves time and costs** (e.g. avoiding the need for dedicated compliance staff or costly audit prep). If a company already uses Drata for ISO 27001 or SOC2, adding Cyber Essentials is streamlined, since Drata will **cross-map overlapping controls so no duplicate effort** [is needed](https://www.vanta.com/products/cyber-essentials#:~:text=Image%3A%20No%20duplicate%20efforts). 


**Market presence**: Drata has grown rapidly worldwide – by late 2023 it served “**thousands of customers** [across 50 countries](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=real)”. Its client base tends to be tech-oriented SMEs (e.g. software companies) and mid-market firms who need multiple certifications. In the UK, Drata’s formal launch of Cyber Essentials support and an expanding EMEA team indicate a push into the UK/EU region. Given its strong funding and recognition (often named alongside Vanta as a leader in automated compliance), Drata is becoming a significant competitor for any UK company considering an all-in-one compliance platform rather than local point solutions. 

**Competitors**: Drata’s main competitors in this space are **Vanta, Secureframe, and Hyperproof** – among these, **Vanta** has also targeted UK compliance specifically (see below). Compared to some UK-specific solutions, Drata is more comprehensive (covering dozens of frameworks) but might be more than what a micro-business strictly needs for just Cyber Essentials. It shines for SMEs that anticipate needing international standards (ISO, SOC2, GDPR, etc.) in addition to UK-specific ones.

##### Vanta (US) – Expanding into UK Standards (Cyber Essentials, NIS2)

**Vanta** is another leading compliance automation vendor from the U.S., very similar in concept to Drata. Notably, Vanta has made a strong entry into the UK market by announcing support for **UK Cyber Essentials and CE Plus** requirements. In fact, Vanta’s website touts itself as “**the fastest way to achieve UK Cyber Essentials compliance,**” automating up to **70% of the work** via built-in [controls](https://www.vanta.com/products/cyber-essentials#:~:text=The%20fastest%20way%20to%20achieve,UK%20Cyber%20Essentials%20compliance) and [monitoring](https://www.vanta.com/products/cyber-essentials#:~:text=Time). Like Drata, Vanta connects with a company’s systems (cloud platforms, device management, etc.) to continuously check security settings against the required standards. It provides **integration-driven checks, auto-generated policies, and test evidence** to [simplify passing an audit](https://www.vanta.com/products/cyber-essentials#:~:text=Time). Vanta also highlights that if an organisation is already compliant with another framework (say ISO 27001 or SOC 2), it will **automatically map those controls to Cyber Essentials**, [avoiding duplicated work](https://www.vanta.com/products/cyber-essentials#:~:text=No%20duplicated%20efforts). This is useful for SMEs that expand their compliance obligations over time. 

**Pricing model**: Vanta’s pricing is also annual SaaS, generally tied to employee count (since they monitor endpoints and accounts). While not public, it typically has tiered packages (e.g. for startups vs mid-market). Reviews indicate Vanta’s cost is comparable to Drata. For a small business focusing only on CE, Vanta’s offering may be more expensive than a local UK-only solution like CyberSmart, but the value is in covering multiple frameworks in one platform. Vanta often markets heavily to startups by emphasizing scalability – as a company grows, they can add on more standards in Vanta’s interface (the platform supports **25+ frameworks** [including](https://www.vanta.com/products/cyber-essentials#:~:text=frameworks) SOC 2, ISO, **NIS2**, GDPR, [etc. as of 2025](https://www.vanta.com/products/cyber-essentials#:~:text=SOC%202%20%2014GDPR%20,30Custom%20frameworks%20%2032)). 

**Market presence**: Vanta claims to have **thousands of customers** [globally as well](https://www.vanta.com/customers#:~:text=Customer%20Success%20Stories%20,Read%20their%20success%20stories). It’s especially popular among cloud-native companies and has been expanding in Europe (they have an EU data center to accommodate GDPR concerns). While exact UK customer counts aren’t disclosed, Vanta’s inclusion of Cyber Essentials and NIS2 indicates a strategic focus on European markets. [The company has substantial funding (unicorn valuation) and has been recognized in the 2025 Forbes Cloud 100](https://www.businesswire.com/news/home/20250903830360/en/Vanta-Named-to-the-2025-Forbes-Cloud-100-for-Third-Consecutive-Year#:~:text=Vanta%20Named%20to%20the%202025,2025%20Cloud%20100%20list%2C), signaling strong momentum. We can expect Vanta to be in direct competition with Drata for any UK SME that might need a multi-framework compliance automation solution.

##### DataGuard (Germany/UK) – “Compliance-as-a-Service” with Human Expertise

capterra.com
**DataGuard** [is a European provider](https://www.capterra.com/p/219584/DataGuard/#:~:text=Achieve%20your%20security%20and%20compliance,security%20and%20compliance%20objectives%20with) (headquartered in Germany, with a London office) that takes a hybrid approach: **an all-in-one compliance platform coupled with expert consulting support**. This “compliance-as-a-service” model is designed for SMEs that want to outsource much of the complexity. DataGuard’s platform covers a wide range of frameworks – **from ISO 27001 and GDPR to NIS2, SOC 2, TISAX, and even the** [EU Whistleblowing Directive](https://www.capterra.com/p/219584/DataGuard/#:~:text=Achieve%20your%20security%20and%20compliance,security%20and%20compliance%20objectives%20with). It offers modules for information security management (ISMS), data privacy management, vendor risk, etc., all integrated. A key feature is its **iterative risk management** dashboard where companies can document assets, risks, and controls, and track improvements. DataGuard automates evidence collection and control monitoring to ensure continuous compliance ([they claim to cut manual effort by ~40% and speed up certifications by 75%](https://www.capterra.com/p/219584/DataGuard/#:~:text=Achieve%20your%20security%20and%20compliance,tracking%20certification%20by%2075%25.%20Join)). In parallel, each client gets access to DataGuard’s in-house consultants and subject matter experts for guidance – effectively **augmenting the software with on-demand advisory.** 

**Pricing model**: DataGuard is sold in **fixed-price packages** [tailored to the company’s needs](https://www.g2.com/products/dataguard/pricing#:~:text=DataGuard%20Pricing%202025%20Our%20pricing,fit%20your%20company%27s%20compliance%20needs). They emphasize transparent pricing, though actual figures aren’t publicly listed as a simple price sheet. In practice, many DataGuard customers pay an annual subscription in the **low-to-mid five figures** (GBP) which includes the software platform and a set amount of consultation hours or support services. For example, a package might include the ISMS software plus help from a named consultant to achieve ISO 27001 certification over several months. This can be cost-effective compared to [hiring a full-time compliance officer or engaging a big law firm](https://www.dataguard.com/compliance-as-a-service#:~:text=). DataGuard often positions itself as giving “the best of both worlds – [specialist advice plus time-saving technology](https://www.dataguard.com/compliance-as-a-service#:~:text=The%20price%20of%20compliance%20is,saving%20technology)”. 

**Market presence**: DataGuard has grown quickly with this model; as of 2023 they reported **4,000+ companies** [using their platform](https://www.capterra.com/p/219584/DataGuard/#:~:text=scales.%20The%20platform%20combines%20AI,content%20shown%20on%20DataGuard%27s%20website). Initially many clients were using DataGuard for GDPR/data protection compliance (they launched in 2017 in the wake of GDPR). Now they have expanded their security offerings, and notably they’ve been marketing NIS2 compliance solutions in 2024-2025 as that [becomes a hot topic in Europe](https://www.capterra.com/p/219584/DataGuard/#:~:text=Achieve%20your%20security%20and%20compliance,security%20and%20compliance%20objectives%20with). In the UK, DataGuard’s customer base includes lots of SMEs and mid-market firms that lack internal compliance teams. Their partnership with investors like British Patient Capital (UK government’s fund) also raised their profile. While DataGuard competes with pure software platforms, its blend of human+tech service is fairly unique. It likely appeals to organisations that want more hands-on guidance or “outsourced compliance officer” services in addition to software. 

**Use cases**: An SME might use DataGuard to achieve ISO 27001 certification (with DataGuard guiding them step-by-step and providing audit support), maintain a privacy compliance program, and prepare for upcoming NIS2 regulations – all via one vendor. This breadth can be attractive for companies that have to juggle multiple compliance obligations at once.

##### SureCloud (UK) – Integrated GRC Platform with SME Packages

**SureCloud** [is a UK-based Governance](https://www.surecloud.com/foundations#:~:text=Perfect%20for%20organisations%20starting%20their,and%20SOC%202%20with%20ease), Risk & Compliance software provider that has been in the market for about 15+ years. Traditionally, SureCloud’s platform has been used by larger organisations for risk management, compliance tracking, and penetration testing services. Recently, however, SureCloud introduced a **“Foundations” GRC package aimed at small teams and growing businesses**, to make their solution more accessible. SureCloud’s platform is a **no-code, modular GRC system** – it provides applications for Compliance Management, Risk Management, Third-Party Risk, Internal Audit, Incident Management, etc., [all unified](https://www.surecloud.com/foundations#:~:text=19%20years%20of%20expertise%20powers,compliant%20and%20ready%20to%20grow) in one [cloud interface](https://www.surecloud.com/foundations#:~:text=,ecosystem). For compliance, it includes pre-mapped content for various frameworks; out-of-the-box it supports common standards such as **ISO 27001, SOC 2, GDPR**, and even newer ones like **DORA (Digital Operational Resilience Act)** [and NIS2](https://www.surecloud.com/foundations#:~:text=Frameworks). SureCloud emphasizes automation of tasks like evidence collection, control monitoring, and reporting ([they advertise up to 75% reduction in manual effort, similar to peers](https://www.surecloud.com/foundations#:~:text=)). 

**Pricing model**: Unlike some competitors that charge per user, SureCloud’s SME-focused offering is sold as a package with a flat price for a certain scope. It’s reportedly **starting around £15k per year** for the “Foundations” edition (supporting a small compliance team with unlimited users) – significantly cheaper than their enterprise deployments, but still a sizable investment for a smaller SME. The company provides [custom quotes](https://www.surecloud.com/foundations#:~:text=A%20flexible%20package%20no%20matter,your%20size) and even a [downloadable pricing brochure](https://www.surecloud.com/foundations#:~:text=Download%20Pricing%20Brochure) for transparency. Essentially, SureCloud is positioning this as a **mid-tier solution**: more robust than lightweight tools, but with a cost and complexity still within reach of midsize businesses. For very small companies, £15k+ may be too high, but for, say, a 200-employee firm that needs a solid GRC system, it’s an attractive proposition. 

**Market presence**: SureCloud is a recognized name in the UK GRC space (featured in Gartner’s Magic Quadrant for IT Risk Management, etc.). Their clients have included enterprises in financial services, retail, and so on. By launching the Foundations product, they are trying to capture the upper-SME and mid-market segment. They highlight case studies like Specsavers and AutoTrader using SureCloud for [risk and compliance management](https://www.surecloud.com/foundations#:~:text=Specsavers%20choose%20SureCloud%20to%20Streamline,their%20Risk%20and%20Compliance). While those are large companies, the same platform now being scaled down means SMEs can trust that it’s a mature solution. In terms of market share, SureCloud isn’t as ubiquitous among SMEs as the smaller specialist tools (it’s more commonly seen in organisations with dedicated compliance teams). But it provides a path for SMEs that want to invest in a long-term GRC infrastructure that can grow with them. 

**Notable features**: SureCloud offers a unified platform approach – an SME can start with compliance management (e.g. manage their ISO 27001 or Cyber Essentials controls in the tool), and later expand to use it for vendor risk assessments, business continuity planning, etc., all within the same system. It also boasts strong **customizability without coding**, meaning as the business evolves, the tool can be configured to new requirements without expensive development. This flexibility and the **“single source of truth”** concept [(all risk and compliance data in one place) are major selling points](https://www.surecloud.com/foundations#:~:text=,ecosystem).

##### ISMS.online (UK) – Cloud Platform for ISO 27001 and More

**ISMS.online** (often stylized as ISMS.online or simply “IO”) is a UK-based SaaS platform that focuses on helping organisations implement and run an **Information Security Management System (ISMS)**. It started primarily as an ISO 27001 support tool but has expanded to cover multiple frameworks. For SMEs, ISMS.online provides a structured environment to **“kickstart your journey to compliance”** with [pre-built content](https://www.isms.online/plans/#:~:text=Compliance%20Essentials) and [guidance](https://www.isms.online/plans/#:~:text=Onboarding%20%26%20ongoing%20support). Out of the box, it includes what they call **Headstart content** – essentially template policies, controls, and an ISO 27001/other standard mapping that gives you an [“81% head start” on documentation](https://www.isms.online/plans/#:~:text=Our%20market%20leading%20ISMS%20platform%2C,complete%20with). There’s also an **Assured Results methodology** (step-by-step project plan to achieve certification) and a **Virtual Coach** feature to [guide users through tasks](https://www.isms.online/plans/#:~:text=An%2081,configured%20policies%20and%20controls). The platform supports multiple standards; you can choose one or multiple from a list that includes **ISO 27001, ISO 27701 (privacy), ISO 22301 (business continuity), ISO 9001 (quality), GDPR, NIS2, DORA**, etc. [This makes it quite comprehensive for an SME-oriented product](https://www.isms.online/plans/#:~:text=Onboarding%20%26%20ongoing%20support).

**Pricing model**: ISMS.online uses a **subscription model with tiered plans**, but all pricing is bespoke via quotes. They explicitly state that the pricing is flexible based on the customer’s objectives, [scope, and number of users](https://www.isms.online/iso-27001/certification-costs/#:~:text=How%20Much%20Does%20ISO%2027001,15k) – so you only pay for [what you need](https://www.isms.online/plans/#:~:text=Explore%20IO%20pricing%20plans%20designed,and%20maintain%20your%20compliance%20needs). In practice, an SME might purchase a single-framework package (e.g. ISO 27001 compliance package) at a certain annual cost, and later upgrade if they add more frameworks or users. There is no public price list, but anecdotal reports suggest it’s more affordable than enterprise GRC systems, though not as cheap as one-domain tools. It likely falls in the **few thousand pounds per year** range for a small company using it for one standard, going up with additional modules or larger user counts. 

**Market presence**: ISMS.online has a strong presence in the UK among tech SMEs, consultancies, and any organisations pursuing ISO certifications. They also partner with many security consultants and MSPs who use the platform for their clients (the [company has a partner directory](https://www.isms.online/cyber-essentials/#:~:text=Partners) for [advisors who can assist on the platform](https://www.isms.online/cyber-essentials/#:~:text=Back)). While exact user numbers aren’t published, ISMS.online has been around for several years and claims global users. It’s not unusual for companies that want to get ISO 27001 certified quickly to adopt ISMS.online rather than starting from scratch – the selling point is accelerating the process with ready-made tools and keeping the ISMS maintained easily afterward. It may not have the buzz of the VC-funded startups, but it occupies a solid niche for compliance-focused software in the UK. 

**Strengths**: ISMS.online is praised for being **very user-friendly for non-experts** and for its rich library of templates. Essentially it provides a “fill-in-the-blanks” ISMS where an SME can log risks, map controls to requirements, manage improvement actions, and generate audit-ready reports. It’s less about technical integration and automation (compared to Drata/Vanta which auto-check settings); it’s more about documentation management, workflow, and guidance. This makes it ideal for meeting governance requirements and passing audits. It also now [markets support for](https://www.isms.online/nis-2/controls/#:~:text=NIS%202%20Controls%20Explained%3A%20Evidence,ready%20with%20ISMS.online) **NIS2 controls**, [indicating it’s keeping up with new compliance needs](https://www.isms.online/nis-2/controls/#:~:text=,ready%20with%20ISMS.online).

##### OneTrust (US/UK) – Broad Compliance Platform (Privacy-Focused)

**OneTrust** is a big name in compliance software, historically known for privacy and data protection compliance (cookie consents, GDPR management, etc.), but it also offers modules for security, GRC, and ethics. OneTrust is headquartered in the US but has a large London presence and many UK customers. In the context of cybersecurity GRC for SMEs, OneTrust’s relevant offering is its **“Tech Risk & Compliance”** [module](https://www.onetrust.com/solutions/tech-risk-and-compliance/#:~:text=Tech%20Risk%20and%20Compliance%20,and%20mitigate%20risk%20while) – this includes capabilities like policy management, risk registers, control libraries, assessment automation, and vendor risk management. A company can use OneTrust to map their controls to frameworks such as ISO 27001 or NIST CSF and track compliance status. However, **OneTrust’s platform is very comprehensive and can be complex**, as it’s aimed at larger enterprises typically. In fact, OneTrust excels in areas like privacy compliance (e.g. managing subject access requests or cookie tracking) and may not have out-of-the-box depth for some cybersecurity frameworks. A 2025 industry review noted that “OneTrust is highly effective in privacy compliance but lacks the depth required for generic third-party security [management and compliance tracking under NIS-2”](https://www.3rdrisk.com/blog/top-10-tools-for-achieving-nis2-compliance#:~:text=OneTrust). In other words, OneTrust can be part of a security compliance program, but it’s not specialized for things like Cyber Essentials and might require more customization for those needs. 

**Pricing model**: OneTrust is modular – clients can license the pieces they need. It is generally **one of the more expensive solutions**, as it often targets enterprise budgets. Pricing is typically by annual subscription, with cost depending on number of modules, size of data (for privacy modules), and number of users or records. For an SME, OneTrust might be overkill unless they have substantial privacy management needs or already use it for GDPR and want to extend it to security GRC. There have been efforts by OneTrust to offer streamlined packages for smaller businesses (and they do have many mid-market clients too), but it’s safe to say it’s not a low-cost option. There’s no public price; everything is custom quoted. 

**Market presence**: OneTrust has a huge global presence – over 12,000 organisations use some part of its trust platform (privacy, GRC, ethics, etc.). In the UK, many companies adopted OneTrust for GDPR compliance around 2018. As for cybersecurity compliance specifically, OneTrust is often seen in larger firms that want an integrated risk management solution. SMEs might encounter OneTrust through its free tools (they offered free compliance assessments, etc., during earlier days) and then possibly grow into a paid customer. However, given the competition from more focused SME tools, OneTrust is not commonly the first choice for a UK SME trying to get, say, Cyber Essentials – it’s more likely used by a **mid-size or large enterprise that needs a unified platform for privacy and security compliance** together. 

**Competitive notes**: In the competitive landscape, OneTrust competes more with enterprise GRC solutions (RSA Archer, ServiceNow, etc.) and with privacy-focused platforms. Its advantage is a one-stop-shop for all “trust” related compliance (security, third-party risk, ethics, privacy, ESG). But for a small business with narrow needs, lighter options typically suffice.

##### 6clicks (Australia) – Agile GRC with Extensive Framework Library

**6clicks** is an Australian-born GRC software platform that has expanded into the UK and other markets. It offers a full suite of compliance and risk management features, and is notable for its **extensive built-in library of standards and controls** – everything from ISO 27001 to NIST, HIPAA, PCI, and yes, **NIS2 and others** are pre-loaded. The platform positions itself as very flexible and quick to deploy (“out-of-the-box” compliance automation). Users can use 6clicks to do risk assessments, track compliance gaps, manage audits, and even handle policy attestations and incident tracking. It also has an AI engine (“Hailey AI”) to assist with compliance mappings and gap analysis. This makes it somewhat similar to traditional GRC tools but with a modern twist. 

For SMEs, 6clicks can be appealing if they need to handle multiple frameworks or if they are serviced by consultants – 6clicks actively promotes use by MSPs and advisors (somewhat like ISMS.online does). In terms of **European/UK focus**, 6clicks supports UK regulations but as one review pointed out, being an Australian company, **its understanding of European legislation might not be as deep** or localized in the [product UI compared to EU-based competitors](https://www.3rdrisk.com/blog/top-10-tools-for-achieving-nis2-compliance#:~:text=6clicks%20offers%20an%20extensive%20GRC,European%20legislation%20is%20less%20developed). Still, it covers the core requirements just fine via its content. 

**Pricing model**: 6clicks is SaaS with subscription pricing. They often tout a no user limit approach in some packages (similar to SureCloud’s angle, focusing on value rather than per-seat cost). There is a free trial and even a free plan with limited features, which can attract small teams to try it out. For full functionality, pricing is custom – likely based on the number of frameworks in use and whether you are an end-company or a partner provider. They have a partner-centric pricing for consultants managing multiple client environments. 

**Market presence**: Globally, 6clicks is a smaller player compared to the likes of OneTrust or Vanta, but it has been growing and making its way into Gartner mentions for IRM (Integrated Risk Management). In the UK, its footprint is still emerging. It does have some UK partners and case studies, but it’s not yet a household name. Given the crowded field, 6clicks often competes on flexibility and cost. A 3rd-party assessment ranked 6clicks highly for a comprehensive feature set and quick setup, but noted it was less intuitive and had fewer ready integrations than [some top competitors](https://www.3rdrisk.com/blog/top-10-tools-for-achieving-nis2-compliance#:~:text=6clicks%20offers%20an%20extensive%20GRC,European%20legislation%20is%20less%20developed). This suggests it might require a bit more training to use effectively. 

In summary, 6clicks offers UK SMEs another option in the GRC platform category – especially if they want a modern tool that they (or their consultant) can tailor extensively. It’s part of the new wave of GRC tools trying to be easier than legacy solutions, but it faces strong competition from both local and US players.

##### Kaseya Compliance Manager GRC (RapidFire Tools) – MSP-oriented Compliance Automation

An important player especially in the MSP (Managed Service Provider) channel is **Compliance Manager GRC** by RapidFire Tools (now part of Kaseya). This product is a bit different in that it’s **often used by IT service providers to manage compliance for their SME clients**, but some larger SMEs use it internally as well. Compliance Manager GRC provides a centralized system to **manage multiple compliance standards and IT security requirements** – it supports a wide array of frameworks such as PCI DSS, HIPAA, GDPR, CMMC, NIST, and notably the **UK Cyber Essentials**. In fact, it quickly updated to include **Cyber Essentials v3.2 requirements (as of April 2025)**, with content to simplify [compliance for IT teams and MSPs](https://www.rapidfiretools.com/products/grc-software/#:~:text=UK%20Cyber%20Essentials%20v3). 

This tool combines automated network and endpoint scanning (especially focused on Windows environments via integrated **CIS benchmark scans** for hardening checks) with compliance documentation workflows. It can automatically generate documents like policies, risk assessment reports, and [evidence of compliance](https://www.rapidfiretools.com/products/grc-software/#:~:text=Deliver%20dynamic%20reports%20and%20documentation), which is [handy for audits](https://www.rapidfiretools.com/products/grc-software/#:~:text=Deliver%20dynamic%20reports%20and%20documentation). The continuous monitoring feature will regularly assess endpoint configurations [against the chosen](https://www.rapidfiretools.com/products/grc-software/#:~:text=Deliver%20dynamic%20reports%20and%20documentation) standard’s [requirements](https://www.rapidfiretools.com/products/grc-software/#:~:text=Deliver%20dynamic%20reports%20and%20documentation) – for example, checking if devices stay configured in line with Cyber Essentials technical controls. The system then produces gap analyses and remediation plans. Essentially, Compliance Manager GRC is like an auditor-in-a-box that maps IT scan data to compliance checklists. 
 
 **Pricing model**: Kaseya sells this mostly to MSPs via annual licenses (the MSP then might offer “compliance as a service” to end clients). The pricing for an MSP might be based on the number of client organisations or endpoints under management. For an individual SME using it directly, one would license the software similarly to other IT software – typically a yearly subscription scaled by company size. The cost isn’t publicly listed, but given its MSP orientation, it is priced to allow MSPs to margin it in their service bundles (so likely not exorbitant per end-client). Kaseya often bundles it in their broader IT Complete suite for MSPs. 
 
 **Market presence**: Compliance Manager (originally by RapidFire) has been around for several years and gained a strong following among MSPs in the US and UK. A lot of SMEs might be benefiting from it without knowing – if their IT provider uses it in the background to run security compliance reports for them. Its inclusion of UK-specific standards like Cyber Essentials shows Kaseya’s commitment to keeping it [relevant for UK regulations](https://www.rapidfiretools.com/products/grc-software/#:~:text=UK%20Cyber%20Essentials%20v3). While it may not be directly advertised to SMEs, it’s a significant competitor in the sense that it enables hundreds of IT providers to offer a competing compliance solution (often under their own branding). For an SME that already has an IT support provider, that provider might say “we’ll take care of your Cyber Essentials using our tool” – that tool very possibly could be Compliance Manager GRC. So, it indirectly grabs a chunk of the SME market via intermediaries. 

**Key points**: The strength of Compliance Manager GRC is in **automated technical assessments and documentation generation**. It may be less user-friendly for a business user (it’s geared toward IT professionals), but it ensures nothing is missed in compliance checks. It also consolidates multiple frameworks, which is good for MSPs who must deal with varied client needs. Its introduction of a proprietary standard [“SMB Security Standard (SMB1001)”](https://www.rapidfiretools.com/products/grc-software/#:~:text=SMB1001%20Cybersecurity%20standard%20for%20SMBs) also shows they are trying to set a baseline specifically for SMB cybersecurity – indicating thought leadership in this niche.

##### Enterprise GRC Solutions (RSA Archer, ServiceNow, etc.) – High-End Options (Rarely Used by SMEs)

No survey of the competitive landscape would be complete without mentioning the traditional **enterprise GRC platforms**. These include **RSA Archer (now Archer IRM), ServiceNow Governance, Risk & Compliance, MetricStream, IBM OpenPages**, and similar heavyweights. These systems are very powerful and configurable, capable of managing compliance across any framework or regulation. In theory, an SME could use Archer or ServiceNow to manage Cyber Essentials, NIS, or any custom control set. However, in practice [these tools](https://www.3rdrisk.com/blog/top-10-tools-for-achieving-nis2-compliance#:~:text=Image) are **expensive, complex, and aimed at large enterprises**, [making](https://www.3rdrisk.com/blog/top-10-tools-for-achieving-nis2-compliance#:~:text=ServiceNow) them **impractical for SMEs**. 

For instance, ServiceNow GRC is typically an add-on for big companies already using ServiceNow IT systems – it requires significant implementation effort (often with third-party consultants) and doesn’t come with out-of-the-box UK compliance content. Archer likewise is [known for](https://www.3rdrisk.com/blog/top-10-tools-for-achieving-nis2-compliance#:~:text=Archer) its **cumbersome interface and heavy customization needs**
3rdrisk.com
. Reviews in the context of NIS2 compliance noted issues such as outdated UI, lack of pre-built templates, reliance on [external consultants](https://www.3rdrisk.com/blog/top-10-tools-for-achieving-nis2-compliance#:~:text=ServiceNow), and [high cost](https://www.3rdrisk.com/blog/top-10-tools-for-achieving-nis2-compliance#:~:text=%2A%20%E2%80%8DPros%3A%20Enterprise,on%20external%20consultants%20for%20implementation). These factors put them out of reach for most SMEs that need quick, cost-effective solutions. 

**Pricing model**: Enterprise GRC platforms usually involve **high annual licensing costs (often six figures in GBP)** plus significant one-time setup costs. They may charge by number of modules and user seats. This is magnitudes above what typical SME budgets allow for compliance tooling. Thus, unless an SME is unusually large or in a very heavily regulated space (and perhaps already has these tools for other reasons), they won’t be using Archer/MetricStream/ServiceNow for Cyber Essentials – it’d be like swatting a fly with a cannon. 

**Market presence**: These platforms dominate in large corporations, financial institutions, and governments. They hold a lot of the market share in GRC overall revenue. But in the SME sector in the UK, their presence is **minimal to none**. Instead, SMEs opt for the lighter platforms and services described earlier. The only scenario an SME might indirectly interface with these is if a **parent company or group uses them** (in which case the SME might have to input some compliance data into a larger Archer system, for example). Or if they hire a consultancy that uses a licensed instance to manage multiple clients. But those are edge cases. 

**Summary of limitations**: In short, while **“you can do anything with Archer/ServiceNow”**, the effort and cost make it a non-starter for SME needs. This is precisely why the newer wave of SME-focused compliance solutions (like CyberSmart, Drata, etc.) has thrived – they filled the gap that these enterprise tools left in the small-business market.

---

Having reviewed the major competitors, we can see the landscape spans from specialized UK-focused solutions to global SaaS platforms and service-driven offerings. The table below summarizes key details for comparison:

##### Comparison of Key Compliance Solutions for UK SMEs

| **Company / Solution**                                                | **Offering & Focus**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | **Pricing Model**                                                                                                                                                                                                                                                                                                                                               | **Market Presence / Notable Info**                                                                                                                                                                                                                                                                                                                                                                                                              |
| --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **CyberSmart** (UK)                                                   | Platform **designed for SMEs**; focuses on **Cyber Essentials** (and IASME Governance) compliance with built-in endpoint scanning and one-click certification. Offers continuous monitoring of devices and security settings, plus cyber insurance inclusion. Very easy-to-use for basic cyber hygiene.                                                                                                                                                                                                                                                                                            | **Subscription SaaS**, starting around **£49/month** for small companies (scales by number of users/devices). Low cost entry, includes certification fee in bundles.                                                                                                                                                                                            | ~**4,000 UK SME customers** as of 2023; backed by UK government initiatives. Often delivered via MSPs and channels. Dominant in Cyber Essentials space for micro and small biz.                                                                                                                                                                                                                                                                 |
| **Drata** (US)                                                        | **Automation-driven GRC** platform supporting **17+ frameworks** (SOC 2, ISO 27001, GDPR, etc.) and now **UK Cyber Essentials**. Provides continuous control monitoring, auto-collection of evidence, auditor collaboration, and cross-mapping of controls to avoid duplicate work. Great for tech-oriented firms needing multi-compliance.                                                                                                                                                                                                                                                        | **Annual SaaS subscription** (custom quoted). Pricing based on company size and frameworks. Typically **four- to five-figure £ per year** for SME range. Emphasizes ROI by reducing audit prep time.                                                                                                                                                            | **Thousands of customers** globally (50+ countries); expanding in UK since 2023 with local sales & support. Strong traction among startups and mid-market companies adopting SOC2/ISO and now CE. Well-funded and rapidly growing.                                                                                                                                                                                                              |
| **Vanta** (US)                                                        | Similar to Drata – a leading **compliance automation** platform. Now explicitly supports **UK Cyber Essentials and CE Plus**, automating ~70% of required checks. Integrates with cloud/IT tools to continuously enforce security controls. Also covers broad frameworks (ISO, **NIS2**, HIPAA, etc.). Focus on usability and fast deployment.                                                                                                                                                                                                                                                     | **Annual SaaS**, pricing typically by number of employees and modules. No public prices; known to be competitive with Drata (in $$ thousands/year for small firms). Offers **free trials** and startup deals often.                                                                                                                                             | **Widely used (4,000+ customers)** – top choice in startup community for SOC2/ISO, now making inroads in UK compliance (CE). Recognized in Cloud 100 list. Some UK companies switching to Vanta for an integrated approach to multiple compliance needs.                                                                                                                                                                                        |
| **DataGuard** (DE/UK)                                                 | **All-in-one “Compliance-as-a-Service”** – combines a comprehensive compliance platform with **expert consultants**. Covers **ISO 27001, GDPR, SOC 2, TISAX, NIS2** and more in one solution. Features risk management dashboards, control tracking, and automated evidence collection. Clients get ongoing support from DataGuard’s team to achieve and maintain certifications (effectively outsourcing compliance).                                                                                                                                                                             | **Fixed-price packages** (annual subscription) tailored to each business’s scope. Pricing is **transparent but custom** – typically includes platform access + allocated expert hours. Often in the **£10k–£50k/yr** range depending on company size/needs.                                                                                                     | **4,000+ companies** use it, largely in UK/EU SME segment. Especially popular for combined **privacy + security** compliance. High customer satisfaction due to hybrid service model. Seen as a one-stop solution for companies with limited in-house expertise.                                                                                                                                                                                |
| **SureCloud** (UK)                                                    | **Integrated GRC platform** with both Enterprise and new **“Foundations”** edition for smaller teams. Provides modules for compliance, risk, vendor management, etc. Out-of-the-box support for key standards (**ISO 27001, SOC 2, GDPR, NIS2, DORA**, etc.). Emphasizes no-code configurability and eliminating spreadsheets through automation (claims 75% reduction in manual effort). Suitable for organisations looking to scale their GRC program.                                                                                                                                           | **Annual subscription**. The SME Foundations package is a **fixed annual fee (approx. five figures)**, e.g. around **£15K/year** for a baseline package (unlimited users) as hinted by marketing. No per-user charges. Custom quotes for expanded needs.                                                                                                        | **Established vendor (since 2004)** with strong UK client base (enterprise and mid-market). Now targeting SMEs; used by notable UK companies (e.g. parts of Specsavers, AutoTrader) for compliance. Offers credibility and robustness, but higher cost than lightweight tools – tends to attract upper-end SMEs or those with dedicated compliance teams.                                                                                       |
| **ISMS.online** (UK)                                                  | **Cloud ISMS platform** tailored for achieving standards like **ISO 27001** (with guided implementation) and managing ongoing compliance. Comes with pre-written policies, control mappings, and a Virtual Coach for step-by-step progress. Supports multiple frameworks (ISO series, GDPR, NIS2, etc.) in one system. Focuses on documentation, risk assessment, and action tracking to satisfy auditors. Great for formal certification preparation and maintenance.                                                                                                                             | **Subscription-based**, but **pricing is bespoke** (no public tiers). Cost depends on number of frameworks and users. Generally affordable for small organisations compared to big GRC suites, but requires a quotation – e.g. a single-framework package for a small business might be in low **** thousands/year.                                             | **Hundreds of SMEs and tech firms** in the UK use it, especially for **ISO 27001**. It’s also popular among consultants who implement ISMS for clients (IO offers partner programs). Known for its ease-of-use and fast deployment. Not as visible as venture-backed rivals, but a steady player with a solid reputation in compliance circles.                                                                                                 |
| **OneTrust** (US/UK)                                                  | **Comprehensive trust platform** spanning privacy, security, data governance, and more. The **Tech Risk & Compliance** module covers infosec GRC: policy management, control assessments, risk registers, compliance automation to an extent. OneTrust excels in **privacy (UK GDPR, cookie compliance)** and integrates that with security incident and vendor risk management. However, its breadth can make it complex; it’s **geared toward larger orgs**, and some specific cybersecurity frameworks may need custom configuration (e.g. not a turnkey Cyber Essentials solution out-of-box). | **Modular licensing** – enterprise pricing. Clients might purchase a bundle of modules. Prices can run **tens of thousands £/year** for a full suite. They do offer scaled-down packages, but for most SMEs this is a significant investment. Often justified if the company has serious privacy compliance obligations (and then adds security module on top). | **Global leader** with 12k+ customers (many in Fortune 500). In UK, widely used for GDPR and vendor compliance. Less common for SME cyber compliance specifically, but some mid-sized UK firms leverage OneTrust for integrated risk management. Has a strong brand and resources (2700+ employees). **Not typically the first choice for basic CE needs**, but a powerful option for those needing a unified privacy-security-ethics solution. |
| **6clicks** (Australia)                                               | **Modern GRC platform** with a wide library of standards and **rapid deployment** focus. Includes AI features to streamline compliance mapping. Supports **UK frameworks (NIS2, ISO, etc.)** and international ones by default. Offers risk management, audits, incident tracking in one platform. UI is web-based and geared for consultants and internal teams alike. Some limitations in user experience and fewer native integrations, but very comprehensive feature set for the price.                                                                                                       | **SaaS subscription**. Offers flexible options (including a free tier and partner licensing). Likely priced by the number of accounts and modules. Aimed to be cost-effective – e.g. could be a mid-£ thousands/year for an SME deployment, but exact pricing varies.                                                                                           | **Emerging player** – used by a growing number of consulting firms and SMEs globally. Still building UK presence; not as well-known as others yet. Those who use it appreciate the all-in-one approach. Seen as a challenger to older GRC tools, with successful deployments in finance, government, etc., in APAC and expanding in Europe.                                                                                                     |
| **Kaseya Compliance Manager GRC** (RapidFire Tools)                   | **Compliance automation software** often leveraged by MSPs. Covers **UK Cyber Essentials** (latest version) and other standards, with built-in scanning of IT systems to check compliance. Auto-generates policies, reports, and evidence artefacts, and tracks remediation tasks. Designed to allow even non-security-experts (like IT technicians) to deliver compliance assessments. Provides continuous compliance monitoring especially for Windows environments. Ideal for multi-tenant use (managing several businesses’ compliance in one console).                                        | **Annual license** (usually MSP-oriented). MSPs pay per client or per asset; they in turn offer it as a service to SMEs (often bundled, e.g. a monthly fee for “compliance service”). Direct use by SMEs is possible but less common; would be a software subscription likely in the **low thousands £/yr** if sized for one organisation.                      | **Widely deployed via MSPs** in the UK/US. Many SMEs indirectly use it through their IT providers. Strong in the niche of IT audit automation. Backed by Kaseya (large MSP software company). Its inclusion of Cyber Essentials content and SMB-specific standards shows commitment to the SME market. Not as visible in direct marketing to end-users, but a significant player through channel.                                               |
| **Enterprise GRC Suites** (e.g. RSA Archer, ServiceNow, MetricStream) | **High-end GRC/IRM systems** with exhaustive capabilities to manage risk and compliance at scale. Can be configured for any standard or regulation (NIS, ISO, internal policies, etc.) and integrated deeply into business processes. Offer advanced analytics, workflows, and enterprise system integrations. However, **not productized for specific SME needs** – require heavy customization and expertise. Reviews note they are **cumbersome and expensive**, with outdated interfaces in some cases.                                                                                        | **Enterprise pricing (very high)**. Typically involve large setup fees and ongoing costs per module/user. Often on-prem or private cloud deployments for security. Not feasible for SME budgets – usually only justified in organisations with dedicated risk departments.                                                                                      | **Dominant in large enterprise** segment (Fortune 500, governments). Virtually **0% market share in SMEs** due to cost/complexity. In context of UK SME compliance, these are mentioned only as theoretical options – in practice SMEs opt for more accessible solutions. Even mid-tier firms find these overly complex for needs like Cyber Essentials.                                                                                        |

Table Source: Compiled from product documentation and industry analyses, including: 
CyberSmart features/pricing
[Link](https://www.capterra.co.uk/software/203257/cybersmart#:~:text=Born%20in%202017%20from%20a,our%20mobile%20and%20desktop%20apps)
[Link](https://www.capterra.co.uk/software/203257/cybersmart#:~:text=Local%20product)
Drata and Vanta announcements
[Link](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=LONDON%2C%20Sept,Plus%2C%20which%20requires%20independent%20verification)
[Link](https://www.vanta.com/products/cyber-essentials#:~:text=Time)
DataGuard description
[Link](https://www.capterra.com/p/219584/DataGuard/#:~:text=Achieve%20your%20security%20and%20compliance,security%20and%20compliance%20objectives%20with)
SureCloud frameworks
[Link](https://www.surecloud.com/foundations#:~:text=Frameworks)
OneTrust and 3rdRisk blog feedback
[Link](https://www.3rdrisk.com/blog/top-10-tools-for-achieving-nis2-compliance#:~:text=OneTrust)
[Link](https://www.3rdrisk.com/blog/top-10-tools-for-achieving-nis2-compliance#:~:text=ServiceNow)
6clicks evaluation
[Link](https://www.3rdrisk.com/blog/top-10-tools-for-achieving-nis2-compliance#:~:text=6clicks%20offers%20an%20extensive%20GRC,European%20legislation%20is%20less%20developed)
Kaseya Compliance Manager release notes
[Link](https://www.rapidfiretools.com/products/grc-software/#:~:text=Compliance%20Manager%20GRC%20now%20supports,manage%20ongoing%20IT%20security%20needs)
TechCrunch/press data on customer counts
[Link](https://www.iqcapital.vc/news/cybersmart-raises-15m-for-an-all-in-one-cybersecurity-and-insurance-solution-targeting-smbs-2#:~:text=regardless%20%E2%80%94%20has%20closed%20a,4%20million)
[Link](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=real)

##### Conclusion

The UK SME cybersecurity compliance market is quite dynamic. On one end, homegrown solutions like CyberSmart have leveraged local knowledge (e.g. of Cyber Essentials requirements) to capture a large chunk of small businesses with affordable, easy tools. On the other end, global SaaS platforms (Drata, Vanta) are bringing Silicon Valley-style automation to UK regulations – a sign of the UK market’s maturity that even US vendors are integrating schemes like CE and NIS2 into their products. 

For SMEs, the choices often boil down to cost vs. breadth vs. support: Smaller companies with limited budgets may start with an inexpensive focused tool (or via an MSP service), while those with slightly more resources or complex needs might invest in a more comprehensive platform or a hybrid service like DataGuard to cover multiple obligations at once. Pricing models vary from per-device monthly fees in the tens of pounds to enterprise subscriptions in the tens of thousands, so SMEs must evaluate what fits their risk appetite and compliance scope. 

It’s also worth noting the legislative trend: as government and regulatory requirements tighten (e.g. potential NIS2-derived laws, supply chain security mandates, etc.), more SMEs will be obliged to formally comply with cybersecurity standards. This will likely expand the market for these compliance solutions further. We can expect competition to increase, possibly driving prices down or spurring innovation (like more AI assistance in compliance, more integration with insurance as CyberSmart and others have done, etc.). 

In summary, UK SMEs have an increasing array of options to help meet cyber GRC obligations. Whether it’s a DIY software platform or a managed compliance service, the competitive landscape outlined above provides solutions for all sizes and budgets. The optimal choice depends on each SME’s specific regulatory requirements, in-house expertise, and financial constraints. But with providers focusing on everything from basic certification to continuous enterprise-grade risk management, even the smallest business can find a path to stay on the right side of UK cybersecurity law and best practice.

##### Citations

[Drata Launches Support for Cyber Essentials](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html)

[NIS Compliance: What UK Businesses Need to Know | LegalVision UK](https://legalvision.co.uk/data-privacy-it/nis-compliance/)

[Cyber Essentials management information - GOV.UK](https://www.gov.uk/government/statistical-data-sets/cyber-essentials-management-information)

[Top Cybersecurity Risk Management Tools and Solutions for UK SMEs | Finch Technical Solutions](https://finch-ts.co.uk/top-cybersecurity-risk-management-tools-uk-smes/)

[CyberSmart Pricing](https://assets.applytosupply.digitalmarketplace.service.gov.uk/g-cloud-13/documents/707477/951169144457475-pricing-document-2022-05-17-1347.pdf)

[CyberSmart Pricing, Cost & Reviews - Capterra UK 2025](https://www.capterra.co.uk/software/203257/cybersmart)

[Frequently Asked Questions - Cyber Essentials - IASME](https://iasme.co.uk/cyber-essentials/frequently-asked-questions/)

[CyberSmart raises $15m for an all-in-one cybersecurity and insurance solution targeting SMBs — IQ Capital](https://www.iqcapital.vc/news/cybersmart-raises-15m-for-an-all-in-one-cybersecurity-and-insurance-solution-targeting-smbs-2)

[Cyber Essentials management information - GOV.UK](https://www.gov.uk/government/statistical-data-sets/cyber-essentials-management-information)

[Drata Launches Support for Cyber Essentials](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html)

[Cyber Essentials compliance automation software | Vanta](https://www.vanta.com/products/cyber-essentials)

[Customer Success Stories - Vanta](https://www.vanta.com/customers)

[Vanta Named to the 2025 Forbes Cloud 100 for Third Consecutive ...](https://www.businesswire.com/news/home/20250903830360/en/Vanta-Named-to-the-2025-Forbes-Cloud-100-for-Third-Consecutive-Year)

[DataGuard Pricing 2025](https://www.g2.com/products/dataguard/pricing)

[Compliance-as-a-Service | DataGuard](https://www.dataguard.com/compliance-as-a-service)

[DataGuard Pricing, Alternatives & More 2025 | Capterra](https://www.capterra.com/p/219584/DataGuard/)

[SureCloud Foundations – GRC Platform for Small Teams](https://www.surecloud.com/foundations)

[How Much Does ISO 27001 Certification Cost? | ISMS.online](https://www.isms.online/iso-27001/certification-costs/)

[Cyber Essentials, Explained, Cyber Security Basics & Certification](https://www.isms.online/cyber-essentials/)

[NIS 2 Controls Explained: Evidence-Driven Compliance and Risk ...](https://www.isms.online/nis-2/controls/)

[Tech Risk and Compliance | Solutions - OneTrust](https://www.onetrust.com/solutions/tech-risk-and-compliance/)

[Top 10 Tools for NIS-2 Compliance: Best Solutions for 2025 | 3rdRisk](https://www.3rdrisk.com/blog/top-10-tools-for-achieving-nis2-compliance)

[GRC Software | IT Compliance Management Software | RapidFire Tools](https://www.rapidfiretools.com/products/grc-software/)

[Cyber Essentials compliance automation software | Vanta](https://www.vanta.com/products/cyber-essentials)

[SureCloud Foundations – GRC Platform for Small Teams](https://www.surecloud.com/foundations)

[IO Plans | ISMS.online](https://www.isms.online/plans/)

[GRC Software | IT Compliance Management Software | RapidFire Tools](https://www.rapidfiretools.com/products/grc-software/)



### D. Change Log
> **[[Placeholder]]** Section under development.  \
> Dependencies from §5 and §4 tagged accordingly.  \
> See Traceability Table for cross-section linkage.
### E. Markdown Codes

# Markdown Syntax Cheatsheet

## Headings
# H1
## H2
### H3
#### H4
##### H5
###### H6

---

## Emphasis
**Bold text**  
*Italic text*  
***Bold and italic text***

---

## Lists

### Unordered
- Item 1  
- Item 2  
  - Sub-item  
  - Another sub-item  

### Ordered
1. First item  
2. Second item  
3. Third item  

---

## Links and Images

[This is a link](https://example.com)

![This is an image](https://via.placeholder.com/150)

---

## Code

Inline `code` example.

### Code Block
```python
def greet(name):
    print(f"Hello, {name}!")
```

---

## Blockquote
> "The cosmos is within us. We are made of star-stuff."  
> — Carl Sagan

---

## Horizontal Rule
---

---

## Table

| Planet | Diameter (km) | Moons |
|--------|----------------|--------|
| Earth  | 12,742         | 1      |
| Mars   | 6,779          | 2      |
| Jupiter| 139,820        | 95     |

---

## Checkboxes (Task Lists)

- [x] Learn Markdown  
- [ ] Build something cool  
- [ ] Conquer the world  

---

## Footnote (if supported)

Here’s a statement with a footnote.[^1]

[^1]: This is the footnote text.

---

## Escaping Characters

Use backslash `\` to escape special characters like \* or \_ if you want them to appear literally.

---

End of file.
