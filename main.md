---
document_type: "Dual-mode PRD"
strategic_sections: [1,2,3,9]
specification_sections: [4,5,6,7,8]
version_control: "Git tracked"
review_cycle: "Quarterly or upon major release"
---

- [Transcrypt Product Requirements Document (PRD)](#transcrypt-product-requirements-document-prd)
  - [0. Prologue - Visionary Statement](#0-prologue---visionary-statement)
  - [1. Vision and Purpose](#1-vision-and-purpose)
    - [Product Definition (MVP)](#product-definition-mvp)
    - [Scope Guardrails (v1)](#scope-guardrails-v1)
    - [1.1 Problem Statement](#11-problem-statement)
    - [1.2 Mission and Guiding Principles](#12-mission-and-guiding-principles)
    - [1.3 Target Users and Stakeholders](#13-target-users-and-stakeholders)
    - [1.4 Success Criteria and Long-Term Impact](#14-success-criteria-and-long-term-impact)
  - [2. Market Context and Competitive Landscape](#2-market-context-and-competitive-landscape)
    - [2.1 Overview of UK SME Cyber and GRC Landscape](#21-overview-of-uk-sme-cyber-and-grc-landscape)
    - [2.2 Key Competitors and Differentiation](#22-key-competitors-and-differentiation)
    - [2.3 Market Share Estimates and Pricing Models](#23-market-share-estimates-and-pricing-models)
    - [2.4 Future Extensibility to Other Nations](#24-future-extensibility-to-other-nations)
    - [2.5 Legislative Environment and Compliance Ecosystem](#25-legislative-environment-and-compliance-ecosystem)
  - [3. Product Architecture and Core Platform Design](#3-product-architecture-and-core-platform-design)
    - [3.1.1 System Overview](#311-system-overview)
    - [3.1.2 Core Components and Interfaces](#312-core-components-and-interfaces)
    - [3.1.3 Data Model (Canonical Contracts)](#313-data-model-canonical-contracts)
    - [3.1.4 Storage and Artifacts](#314-storage-and-artifacts)
    - [3.1.5 Security, Privacy, and Trust Model](#315-security-privacy-and-trust-model)
    - [3.1.6 Extensibility \& Integration Framework](#316-extensibility--integration-framework)
    - [3.1.7 DevEx, QA, and Delivery](#317-devex-qa-and-delivery)
    - [3.1.8 Minimal Viable Slice (MVP cut)](#318-minimal-viable-slice-mvp-cut)
    - [3.1.9 Technology Choices (initial)](#319-technology-choices-initial)
    - [3.1.10 Operational Runbooks (high level)](#3110-operational-runbooks-high-level)
    - [3.2 Core Components and Interfaces](#32-core-components-and-interfaces)
      - [3.2.1 Web App (Next.js @ `https://transcrypt.xyz`)](#321-web-app-nextjs--httpstranscryptxyz)
      - [3.2.2 API Gateway \& Policy Enforcement](#322-api-gateway--policy-enforcement)
      - [3.2.3 Rule Evaluation Service (Deterministic)](#323-rule-evaluation-service-deterministic)
      - [3.2.4 LLM Assist Pipeline (Build-Time Only)](#324-llm-assist-pipeline-build-time-only)
      - [3.2.5 Evidence Services](#325-evidence-services)
      - [3.2.6 Report Service](#326-report-service)
      - [3.2.7 Partner / Integrator API](#327-partner--integrator-api)
      - [3.2.8 Admin Console (Internal)](#328-admin-console-internal)
      - [3.2.9 Data Stores \& Artifacts (Interface Contracts)](#329-data-stores--artifacts-interface-contracts)
      - [3.2.10 Observability \& Audit](#3210-observability--audit)
      - [3.2.11 Public Site \& Content (Marketing, Legal, Support)](#3211-public-site--content-marketing-legal-support)
      - [3.2.12 External Integrations (First-Party)](#3212-external-integrations-first-party)
      - [3.2.13 Non-Functional Interface Contracts](#3213-non-functional-interface-contracts)
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
    - [5.5 Closed-Source Policy and Verifiable Transparency](#55-closed-source-policy-and-verifiable-transparency)
  - [6. Compliance and Governance Framework](#6-compliance-and-governance-framework)
    - [6.1 Alignment with NIS, Cyber Essentials, ISO 27001, and IEC 62443](#61-alignment-with-nis-cyber-essentials-iso-27001-and-iec-62443)
    - [6.2 Risk Management and Assurance](#62-risk-management-and-assurance)
    - [6.3 Policy Library and Evidence Management](#63-policy-library-and-evidence-management)
    - [6.4 Legislative Alignment and Future Adaptation](#64-legislative-alignment-and-future-adaptation)
    - [6.5 Governance of Product Lifecycle](#65-governance-of-product-lifecycle)
  - [7. Security and Infrastructure Requirements](#7-security-and-infrastructure-requirements)
    - [7.1 Authentication, Authorisation, and Identity Management](#71-authentication-authorisation-and-identity-management)
    - [7.2 Network Segmentation and Zero Trust Architecture](#72-network-segmentation-and-zero-trust-architecture)
    - [7.3 Data Encryption and Key Management](#73-data-encryption-and-key-management)
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
    - [9.3 Resource and Budget Planning](#93-resource-and-budget-planning)
    - [9.4 Risk Register and Mitigation](#94-risk-register-and-mitigation)
    - [9.5 Quality Assurance and Acceptance Criteria](#95-quality-assurance-and-acceptance-criteria)
  - [10. Future Outlook and Strategic Extensions](#10-future-outlook-and-strategic-extensions)
    - [10.1 Interoperability with Other National Frameworks](#101-interoperability-with-other-national-frameworks)
    - [10.2 Research and Development Themes](#102-research-and-development-themes)
    - [10.3 Potential Spin-offs and Product Lines](#103-potential-spin-offs-and-product-lines)
    - [10.4 Long-Term Sustainability and Ethical Charter](#104-long-term-sustainability-and-ethical-charter)
    - [10.5 Closing Summary](#105-closing-summary)
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

Strategic content appears in **Sections 1–3** and **9**.  
Specification content appears in **Sections 4–8**.  
Cross-references between the two are deliberate and annotated using inline comments:  
`<!-- strategic -->` or `<!-- specification -->`.

<!-- strategic -->
## 0. Prologue - Visionary Statement

If I sold my company today, I'd start my next multi-million dollar business in 90 days using only AI. 

Here's how:

I'd create 5 AI specialists that work 24/7 for a fraction of what a single employee costs.

Meet my AI dream team:

THE ANALYST

I'd upload a detailed vision document explaining my business model
I'd have it identify emerging market opportunities with hard data
I'd ask: "Find the top 3 underserved problems in profitable industries"
I'd demand specific research on customer behavior and spending patterns
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

**Transcrypt Core (v1)** is a lightweight, approachable compliance assistant for UK SMEs.  
It provides **guided assessments**, a secure **evidence vault**, **auto-generated policies/templates**, and **AI-assisted suggestions** that reduce human effort while keeping costs low.

**Non-goals (MVP):**
- No multi-tenant orchestration layer for external assessors/auditors. [[Post-MVP: see §9 Roadmap]]
- No advanced ML training loops or model fine-tuning pipelines. [[Post-MVP: see §9 Roadmap]]
- No cryptographic provenance ledger or blockchain-style attestations. [[Post-MVP: see §9 Roadmap]]
- No marketplace or collaboration features beyond basic account roles. [[Post-MVP: see §9 Roadmap]]

**Design Principle:** “Automation you don’t feel.” AI is used to remove toil (classification, drafting, gap-spotting), not to introduce operational complexity.

**Naming:**  
- **Transcrypt Core** = MVP (this document’s scope).  
- **Transcrypt Platform** = post-MVP expansion (see Roadmap).

### Scope Guardrails (v1)

- **User:** SME owner/manager or their in-house IT; no external auditor workflows.
- **Jobs-to-be-done (v1):** pass Cyber Essentials quickly, keep up with renewals, store evidence, generate simple reports.
- **AI in v1:** assistive (extract fields from uploads, draft policies, flag gaps); no model training or user data leaving tenant boundary except for inference.
- **Security posture:** tenant-encrypted storage; audit log is append-only (no external ledger—see Roadmap).

Transcrypt exists to turn regulatory obligation into operational confidence for small and mid-sized businesses. The vision is simple to state and hard to execute well: take messy frameworks, translate them into clear actions, and back every claim with evidence. The product is a practical interpreter between law and day-to-day operations. It gives an owner a single session route from intake to a tailored report, then keeps them aligned as rules change. Success is measured in steady outcomes rather than theatre: fewer hours lost to forms, faster audits, cleaner hand-offs to insurers and primes, and a live sense of “what is left to do and why”. Transcrypt builds trust through **verifiable transparency** rather than open code. Audit confidence is achieved by deterministic, cryptographically signed outputs that anyone can verify, even though the software itself remains proprietary.
Transcrypt’s SaaS model delivers cloud convenience without cloud exposure — **users own their data cryptographically, not contractually.**

### Human Role Definition

For v1 (**Transcrypt Core**) all compliance flows are **self-serve**.
AI-driven automation replaces most manual review steps and guides the user end-to-end without external assistance.
Human experts re-enter the loop only in later versions (see §9 Roadmap – Assisted Tier) to deliver optional audit reviews and trust attestations.
This ensures automation is the revenue engine while human expertise remains an opt-in premium service, not a bottleneck.

### Audience and Philosophy

Transcrypt Core is built **for SMEs**, not large enterprises.  
Its architecture borrows security and reliability practices from enterprise systems, but these operate **entirely behind the scenes**.  
The user interacts only with clear guidance, automated actions, and human-readable results—never raw controls or configuration pages.  
In short: *enterprise-grade under the bonnet, SME-simple at the wheel*.

### Design Tenets

1. **Invisible Complexity** – advanced engineering should be felt only as speed or accuracy, never as extra controls.  
2. **Plain Language** – all interfaces, reports, and AI feedback are written for non-specialists.  
3. **Zero Setup** – onboarding requires no infrastructure knowledge; configuration is automatic.  
4. **Guided Autonomy** – users can achieve compliance independently, yet remain on safe rails.

AI is the accelerator, not the decider. The platform uses AI where language is a bottleneck and keeps decisions deterministic where auditability matters. In practice that means AI drafts rule objects from legislative text, proposes equivalences across frameworks, summarises diffs when guidance changes, and turns structured findings into plain English. The rule engine remains authoritative. It evaluates controls, records provenance, and explains outcomes in a way an auditor can follow and a team can act on. This is the disciplined version of the “AI dream team” idea above. The Analyst surfaces gaps in the market and in a customer’s posture. The Growth Hacker tests messaging against real behaviour. The Sales Machine writes only from verified benefits. The System Builder generates runbooks that can be executed. The Brand Builder publishes useful, evidence-led content that earns trust. Each assistant is judged by the same standard as the product itself: clarity, relevance, and the ability to be checked.

The purpose is commercial as well as technical. Year one proves a lean, founder-led business can earn while it learns. Ship an MVP that pays for itself, reach a clean £500 monthly profit by month twelve, and compound value through retention and partner channels rather than ad spend. From there the platform grows by translation, not reinvention: extend Cyber Essentials to NIS2 and ISO mappings, add insurer and MSP views, and make interoperability a feature customers feel rather than see. Everything in this document points at the same outcome. Transcrypt should feel like a quiet, capable companion that makes difficult things understandable, keeps its promises, and leaves a paper trail you can show to anyone.

### 1.1 Problem Statement

The United Kingdom’s small and medium-sized enterprises sit at the fault line of a regulatory and technical collision. Government policy has steadily shifted from voluntary cyber hygiene to mandatory assurance—through schemes such as Cyber Essentials, NIS regulations, and sectoral GRC mandates—without delivering the practical means for SMEs to comply. Compliance requirements are fragmented across frameworks, written in policy language inaccessible to non-specialists, and enforced by overlapping authorities. The result is a widening chasm: businesses that want to do the right thing but lack the time, clarity, or technical depth to interpret and act on those rules. Meanwhile, consultancies and auditors sell expensive engagements that focus on producing paperwork rather than building resilience, and no unified platform exists that continuously translates these shifting requirements into operational reality. For many SMEs, compliance is a once-a-year panic, not a living practice.

At the same time, the threat landscape has matured beyond what small organisations can absorb. Supply chains now link critical infrastructure to modest subcontractors, who are often the weakest link in the chain of trust. These firms handle sensitive data, industrial control interfaces, or remote access into high-value networks, yet their security maturity remains low. The tools they rely on—spreadsheets, generic checklists, or outdated templates—cannot capture the nuance of their risk profile or prove assurance to partners and regulators. They need a system that speaks their language while satisfying the language of auditors. But most available solutions are either enterprise-grade GRC platforms priced out of reach or minimalist certification portals that stop at the questionnaire. The middle ground—the intelligent, affordable, continuously updated compliance layer that bridges governance, risk, and operational action—has yet to be filled.

This gap defines the problem Transcrypt intends to solve. The opportunity is not simply to automate certification but to operationalise trust: to turn regulatory obligations into live, data-backed workflows that evolve with the law and the network. The commercial problem therefore lies in unifying three fractured domains—policy interpretation, compliance execution, and evidence management—into one coherent digital journey for SMEs. By mapping every mandate, advisory, and certification path into structured data and guiding each organisation through it interactively, the system would reduce cost, time, and uncertainty. It would let businesses demonstrate compliance and resilience without needing a consultant at every turn, while creating a sustainable subscription model rooted in ongoing assurance rather than one-off audits.

### 1.2 Mission and Guiding Principles

The mission of Transcrypt is to democratise cybersecurity compliance—turning what is now a burdensome, opaque exercise into a continuous, comprehensible, and measurable practice. The platform’s purpose is to give small and medium-sized enterprises the same clarity and control over their digital risk that large corporations enjoy, but without the cost or bureaucracy. Transcrypt seeks to rebuild trust between business, regulator, and customer by codifying the intent behind legislation into machine-readable logic, making compliance both verifiable and self-sustaining. Its ultimate mission is to make regulatory conformance and real-world security inseparable: compliance not as paperwork, but as proof of resilience.

Guiding this mission is the belief that transparency must be built in, not added later. Every rule, mapping, and control interpretation within Transcrypt should be explainable and inspectable, so users can see why a recommendation exists and trace it back to its regulatory source. Simplicity is another pillar: the system must remove the noise of competing standards by abstracting complexity into natural, human-guided steps that any business owner can follow. Automation is there to support judgement, not replace it—using intelligence to surface insights, reduce toil, and guide decisions, while leaving accountability with the human operator. The product must be relentlessly focused on clarity of purpose: to bridge the gulf between compliance frameworks and practical defence, so users spend their time fixing risks, not formatting evidence.

Finally, Transcrypt’s ethos is shaped by three enduring principles: integrity, adaptability, and accessibility. Integrity means that the system itself should be provable, versioned, and auditable—no hidden scoring or black-box assessments. Adaptability means recognising that cyber regulation evolves constantly, so the platform must update in rhythm with the landscape, ensuring that guidance remains live and relevant rather than static and stale. Accessibility means both cost and comprehension: pricing that scales with the smallest firms and language that avoids consultant jargon. Together, these principles anchor Transcrypt’s ambition to become the trusted digital interpreter between government mandate and business reality—a permanent, evolving companion in the daily work of staying compliant, resilient, and credible.

### 1.3 Target Users and Stakeholders

Transcrypt is built for the small and medium-sized enterprises that form the backbone of the UK economy yet remain the least supported in their cybersecurity obligations. These businesses are often too large to rely on intuition and luck but too small to justify hiring a full-time security officer or external compliance team. They range from manufacturers, logistics providers, and engineering firms operating within regulated supply chains to service-based companies handling customer data under GDPR or critical contracts. Their shared challenge is not ignorance or apathy, but overload: a deluge of acronyms, frameworks, and technical expectations delivered without translation into their operational reality. For these users, Transcrypt serves as an always-on compliance partner—one that interprets mandates, guides remediation, and produces verifiable assurance artefacts, all while fitting seamlessly into the tempo of small-business life.

Beyond the SMEs themselves, a wider ecosystem of stakeholders depends on their compliance. Prime contractors, utilities, and infrastructure operators are under pressure to demonstrate supply chain assurance, yet have no efficient way to measure or validate the cyber posture of hundreds of partners. Transcrypt provides them with standardised evidence formats and live compliance telemetry—replacing annual self-attestation forms with dynamic trust relationships. Insurers and certification bodies gain a richer, continuous view of client risk, reducing underwriting uncertainty and audit fatigue. Meanwhile, regulators, government agencies, and sector-specific authorities benefit indirectly: they gain a more accurate, anonymised landscape view of national cyber readiness without intrusive reporting demands. Transcrypt becomes the connective tissue between oversight and operation.

Internally, Transcrypt’s stakeholders include security practitioners, compliance officers, auditors, and developers who will shape and evolve the platform. For them, the product is not merely a tool but a shared language between disciplines—a codified bridge between law, engineering, and risk. Investors and partners occupy another key role, particularly those who recognise the commercial potential of automating compliance at scale without commodifying it. Each stakeholder group aligns around a common incentive: to transform the static, manual, and reactive world of compliance into a living, intelligent ecosystem. Transcrypt’s value proposition therefore extends from the smallest subcontractor seeking Cyber Essentials certification to the largest supply chain integrator needing to prove collective resilience—all united by a single platform designed to make compliance visible, actionable, and enduring.

### 1.4 Success Criteria and Long-Term Impact

Success for Transcrypt in its early phase will be measured by validation and momentum, not scale. The first six months are about proving that one person can design, build, and run a credible commercial service from a single, elegant site that quietly outclasses the noise of the industry. The aim is to attract a handful of small businesses willing to pay for clarity — not consultancy. Every completed sign-up, trial conversion, and support query will be used to refine the experience, the language, and the trust model. At this stage, success is defined by proof of appetite: that SMEs will part with their own money for a tool that genuinely makes the maze of cyber regulation simpler to navigate. The goal is to exit month six with a working product, a visible trickle of paying users, and operational confidence that the model holds together without outside capital.

From month seven onward, the measure becomes profitability, not revenue. The target is a clean, sustainable profit of around £500 per month by the end of the first year — enough to demonstrate a replicable business model and justify reinvestment. Achieving this means keeping infrastructure lean, automating onboarding and evidence generation, and using founder time surgically where it adds visible value. Marketing will stay tightly focused: a credible web presence, a handful of authority-building articles, and Brian’s approachable public persona as the owner-operator backed by a small team of “techies.” Each subscription and renewal will count more than metrics ever could, and user testimonials — not ad spend — will power growth. By that point, the system should run with minimal human friction: a product that quietly earns while the founder sleeps.

The long-term impact is measured in endurance and credibility rather than investor multiples. If Transcrypt continues beyond its first thousand customers as a stable, self-funded company, it will have proved a much larger idea — that cyber compliance can be made humane, intelligible, and profitable at micro-scale. The goal is a business that never needs to chase venture money or artificial growth curves, but instead becomes a trusted small-business ally whose income compounds steadily year after year. Over time, it can evolve into a platform that represents the lived compliance reality of the UK’s SME sector — a dataset and reputation that regulators, insurers, and primes quietly rely on. The enduring success metric will not be valuation but influence: that the standards of clarity, honesty, and craftsmanship established by Transcrypt subtly raise the bar for how cyber assurance is done across the country.

This PRD is deliberately *hybrid*.  
It records not just requirements but reasoning — both the *what* and the *why*.  
Readers should treat strategic sections as context and technical sections as binding for implementation.

<!-- strategic -->
## 2. Market Context and Competitive Landscape

Transcrypt Core launches with a **UK-first focus**, helping SMEs meet **Cyber Essentials** and **NIS2** obligations. However, the compliance engine is designed to be **framework-agnostic**. Each regulation—Cyber Essentials, NIS2, ISO 27001, SOC 2, or future national schemes—is represented as a **modular control pack** containing:
- control definitions,
- evidence requirements,
- scoring logic, and
- mappings to shared baseline controls.

This design allows Transcrypt to remain rooted in UK mandates while enabling future localisation for other jurisdictions without code rewrite.

The incumbents competing for SME attention are largely transactional rather than relational. Companies like CyberSmart, Bulletproof, IASME, and a growing tier of managed-service providers offer compliance as a bundle — certification plus managed antivirus, plus a vague promise of “peace of mind.” Their strength is marketing polish, but their weakness is depth: they simplify by omission, not by design. Few provide continuous alignment with new legislative changes or transparent mappings between regulations. Even fewer generate the kind of live, data-backed assurance that larger supply-chain partners increasingly demand. This creates an opportunity for a product that combines policy literacy with operational empathy — one that helps a small business understand what compliance means day to day rather than just tick a box. Transcrypt’s proposition is not to undercut them on price but to outperform them on authenticity, clarity, and trust.

Macro conditions reinforce this opportunity. Regulatory tightening under NIS2, increasing supply-chain due diligence, and cyber insurance underwriting pressures are pushing SMEs toward demonstrable, ongoing assurance. Simultaneously, economic strain has made consultant-heavy models unviable for many. The next generation of tools must therefore be lightweight, continuous, and self-service — qualities the current players, with their legacy processes and compliance silos, struggle to deliver. The competitive advantage for Transcrypt lies in agility: it can model the rules as structured data from day one, update them as legislation shifts, and communicate them in plain English. The brand strategy — Brian’s straightforward, engineer’s persona paired with a backroom of credible “techies” — adds a human trust layer absent in most sterile compliance brands. In a market defined by opacity and bloat, success will come from being the product that simply makes sense — and stays current without ever losing its honesty.

### 2.1 Overview of UK SME Cyber and GRC Landscape

The UK’s SME cyber and governance, risk, and compliance (GRC) landscape is defined by contradiction: a national economy increasingly dependent on digital systems, yet serviced by a security market still modelled for enterprises. Small and medium-sized businesses make up 99% of UK private enterprises, yet most lack in-house expertise to interpret, let alone implement, the overlapping frameworks they are expected to comply with. The government’s intent — to raise national resilience through schemes such as Cyber Essentials, NIS, and the incoming NIS2 and DORA regimes — is sound, but its execution leaves SMEs stranded between aspiration and affordability. For most, compliance remains a box-ticking ritual done under duress: an annual scramble to fill out forms for insurers, regulators, or supply-chain primes, without any lasting improvement to their actual defences. This gap between regulation and operational capacity defines the present state of the market.

The supply side of the landscape reflects the same imbalance. Traditional consultancies and managed-service providers dominate, offering compliance as a labour-intensive service with high margins and low transparency. At the lower end, automated portals have proliferated — platforms that sell quick Cyber Essentials certification or security “health checks” with little substance. Neither approach builds enduring capability. Consultancies depend on recurring audits, while the portals stop short of meaningful interpretation or adaptation to live regulatory change. In the middle ground, there are a few promising entrants — firms such as CyberSmart, Bulletproof, and Drata’s UK integrations — yet even these tend to rely on prescriptive templates rather than the dynamic modelling of real controls and evidence. The result is a fragmented, noisy ecosystem in which small businesses must choose between cost and comprehension, never both.

Government direction and market pressure are converging on the need for something better. The National Cyber Strategy 2022 emphasised “secure by default” and “secure by design,” while the updated Cyber Essentials scheme signals a move toward continuous assurance rather than static compliance. Meanwhile, insurers, primes, and regulators increasingly demand demonstrable, ongoing alignment rather than once-a-year attestations. The conditions are therefore set for a shift: from reactive certification to continuous, data-backed assurance delivered digitally at SME scale. The next generation of platforms must not only simplify compliance but also explain it, bridging the literacy gap that has kept SMEs dependent on consultants. The UK SME cyber and GRC landscape is thus ripe for intelligent disruption — a move away from bureaucracy toward comprehension, from form-filling to evidence-based trust. Transcrypt is designed to inhabit that exact gap: the missing interpreter between government mandate, commercial necessity, and operational reality.

### 2.2 Key Competitors and Differentiation

The key competitors in the UK SME cyber and GRC space can be divided into three broad categories: certification brokers, managed-service hybrids, and enterprise-grade compliance platforms. The certification brokers — notably CyberSmart, IASME, Bulletproof, and Tytan — dominate the low-cost, high-volume end of the market. Their offering revolves around rapid Cyber Essentials accreditation, typically using templated questionnaires and automated scoring engines. They appeal to SMEs wanting a quick certificate for tender eligibility or insurance renewal but do little beyond that point. Their differentiator is speed and price; their weakness is superficiality. Once the certificate is issued, the relationship ends, and the client remains as unprepared as before. For a business seeking ongoing understanding or resilience, these providers are a one-night stand rather than a partner.

The managed-service hybrids — such as Littlefish, Redscan (Kroll), and SureCloud — aim higher. They pair compliance management with outsourced SOC and vulnerability monitoring, bundling Cyber Essentials, ISO 27001, and penetration testing into broader “assurance packages.” They sell continuity but not comprehension: the customer pays for coverage rather than insight. Their recurring revenue model depends on a perception of complexity that keeps the client dependent. These players hold solid market share among mid-tier firms but are too costly, jargon-heavy, and opaque for the smaller organisations that make up the bulk of the UK’s 5.5 million SMEs. Finally, at the top end, platforms like Drata, Vanta, and Tugboat Logic have entered the UK market from the US. Their automation and integrations are impressive but tuned for companies with internal IT and security teams — the very resources most SMEs lack. Their tools are powerful but overbuilt, their language foreign, and their price tags misaligned with UK SME economics.

Transcrypt’s differentiation lies in translation, continuity, and credibility. It does not aim to compete on breadth of frameworks or managed services but on the ability to interpret regulation into human guidance and maintain that mapping over time. Where incumbents sell compliance as an event, Transcrypt treats it as a living state. The product is conceived as a low-overhead, plain-language compliance companion that shows why each control exists and how to evidence it in context. It bridges the gulf between policy and practice, continuously aligning with legislative updates and surfacing changes without user intervention. Its personality — fronted by Brian’s straightforward engineer’s voice and supported by a small, skilled backroom — is its brand advantage: trust built through clarity, not jargon. In a market full of transactional portals and consultant echo chambers, Transcrypt will stand apart by being the one that simply makes sense, costs little, and evolves honestly with the law.

### 2.3 Market Share Estimates and Pricing Models

The UK SME cyber and GRC market is crowded but top-heavy, with a small number of well-funded players commanding the lion’s share of paid certifications and managed compliance revenue. CyberSmart is the largest pure-play competitor in the SME automation tier, estimated to hold roughly 35–40% of the automated Cyber Essentials certification market, driven by its partnerships with insurers (notably Hiscox) and MSPs. Its pricing typically runs from £490–£1,200 per year, depending on whether the SME opts for self-assessment or guided support. Bulletproof occupies a similar bracket, though its business model leans more on bundled penetration testing and consultancy than subscription automation. IASME, which oversees the official Cyber Essentials framework, takes around 10–15% of the certification market directly or through licensed partners. The rest of the field is fragmented among dozens of small service providers — often one- or two-person consultancies operating on razor-thin margins — who issue certificates at cost just to sell follow-on services.

Higher up the value chain, managed-service providers and hybrid firms such as SureCloud, Redscan (Kroll), and Littlefish compete for clients turning over £5–50 million, typically charging £5,000–£20,000 per year for managed compliance and SOC monitoring. These firms combine ISO 27001, Cyber Essentials Plus, and penetration testing into a subscription-like service, but they are far too expensive for the average SME with fewer than fifty employees. Meanwhile, US-origin platforms like Drata and Vanta are only beginning to penetrate the UK market, capturing early adopters in fintech and SaaS, with pricing in the range of £4,000–£12,000 per year depending on automation scope and integrations. Collectively, the UK SME cyber assurance market is valued at roughly £400–£600 million annually, but more than half of that spend goes toward human consultancy, not software. The true digital automation layer for small firms remains underdeveloped — a narrow but fertile space for Transcrypt.

Transcrypt’s pricing strategy is deliberately designed to undercut both consultancy and overbuilt automation without signalling cheapness. The base model would operate on a monthly subscription between £25–£45, scaling by organisation size or compliance tier (Cyber Essentials, NIS2 alignment, etc.). The first revenue goal is modest but concrete: £500 per month net profit by month twelve, achieved through low operational overhead and organic customer acquisition. Pricing will remain transparent, all-inclusive, and jargon-free — no hidden “audit support” or upsells. As the product matures, higher tiers could introduce lightweight integrations (insurer reporting, document verification, supply-chain dashboards) at £75–£150 per month, maintaining simplicity while expanding utility. The long-term intent is to keep Transcrypt’s pricing firmly in the “sustainable self-service” bracket — affordable enough for a single-person business, valuable enough for a 50-person firm, and stable enough to generate predictable income without debt or external funding.

### 2.4 Future Extensibility to Other Nations

Transcrypt’s foundation is deliberately architectural rather than parochial. While the initial focus is the UK SME landscape—rooted in Cyber Essentials, NIS2 transposition, and the domestic insurance and supply-chain ecosystem—the underlying logic of the platform is universal: regulation codified into structured data, mapped to evidence workflows, and expressed in plain human language. That framework can be reparameterised for any jurisdiction. Each compliance regime—whether the EU’s NIS2 and DORA, the US’s CISA mandates and CMMC model, or Australia’s Essential Eight—follows the same grammar of obligation, control, and verification. Transcrypt’s model treats these as datasets rather than documents, allowing new territories to be added through translation, not reinvention. In this way, extensibility is engineered from the start: the same compliance engine can ingest a different regulatory schema while preserving the same user experience and logic of assurance.

The first natural expansion path is Europe, where NIS2 and DORA create regulatory convergence across member states. Transcrypt’s UK rulebase already aligns conceptually with NIS2’s emphasis on proportionality and continuous oversight. A multilingual adaptation layer—initially targeting Ireland, the Netherlands, and the Nordics—would enable rapid scaling using localised text and authority references without structural changes to the core. The second phase would target Commonwealth markets such as Canada, Australia, and New Zealand, where cyber regulation shares the same risk-based language but lacks consistent SME tooling. These regions also share cultural affinity for plain-English communication and pragmatic governance, making Transcrypt’s approachable tone and subscription model transferable. By this stage, partnerships with local auditors or insurers could seed presence without needing physical offices, using the product’s credibility in the UK as proof of legitimacy.

In the long term, extensibility is not merely geographic but systemic. The same compliance graph that maps controls to evidence for one nation can support cross-jurisdictional assurance—a single dashboard that shows how a firm’s UK compliance posture maps to EU or US equivalents. This “compliance interoperability” is a major unsolved problem for global SMEs and supply chains. By expressing mandates in a machine-readable form, Transcrypt could evolve into a translation layer between national frameworks, easing the burden for exporters, tech vendors, and managed-service providers who operate across borders. The strategic endgame is to become the Rosetta Stone of small-business compliance: one platform that interprets local laws, aligns overlapping standards, and lets companies operate internationally without drowning in differing paperwork. Extensibility, therefore, is not an afterthought but the defining characteristic of the system’s long-term architecture and commercial ambition.

### 2.5 Legislative Environment and Compliance Ecosystem

The legislative environment shaping UK SME cybersecurity has tightened dramatically over the past five years, driven by both domestic policy and international alignment. At the core sits Cyber Essentials, a government-backed baseline scheme that has evolved from a simple self-assessment into a de facto gatekeeper for public-sector contracts and insurance eligibility. Above it, the Network and Information Systems Regulations (NIS) and its successor NIS2 introduce obligations for operators of essential and digital services, explicitly including their supply chains. That last phrase is where SMEs come under direct pressure: even if they are not “regulated entities,” they must demonstrate compliance to primes who are. The regulatory tone has shifted from encouragement to expectation—reinforced by forthcoming Digital Operational Resilience Act (DORA) obligations in the financial sector and by insurance carriers tightening underwriting criteria around cyber hygiene. Compliance has become a precondition for participation in the modern economy.

This landscape is not managed as a single ecosystem but as a loose federation of schemes, standards, and regulators. The National Cyber Security Centre (NCSC) sets strategy but does not enforce; the Department for Science, Innovation and Technology (DSIT) drives policy; the Information Commissioner’s Office (ICO) enforces data protection; and the IASME Consortium administers Cyber Essentials and NIS certifications under licence. In parallel, insurers, auditors, and large enterprises act as shadow regulators by embedding cyber clauses into contracts. This diffuse structure means there is no single authoritative map for compliance. SMEs must interpret policy statements, scheme updates, and auditor feedback across multiple channels, often with contradictory or outdated guidance. The compliance ecosystem has thus evolved organically rather than by design—an ecosystem of frameworks rather than a frameworked ecosystem. Its by-product is friction, duplication, and unnecessary cost.

The opportunity for Transcrypt emerges directly from this disorder. The direction of travel is clear: continuous, evidence-based assurance will replace annual attestations; supply-chain accountability will extend obligations beyond direct regulators; and machine-readable compliance will become a policy goal as government digitalises its oversight mechanisms. Yet the tools that can operationalise those ambitions at SME scale do not exist. Transcrypt’s purpose is to occupy that emerging layer: the connective tissue between legislation, auditor interpretation, and business execution. By modelling each control as data and linking it to live evidence sources, Transcrypt mirrors the regulatory structure itself—capable of tracking updates, mapping equivalence between frameworks, and translating policy into actionable guidance. As the legislative environment continues to converge with international norms under NIS2 and DORA, Transcrypt can become the practical interpreter that allows SMEs to keep pace, turning compliance from a confusing landscape into a coherent ecosystem they can actually navigate.


<!-- strategic -->
## 3. Product Architecture and Core Platform Design

Transcrypt’s architecture is deliberately simple at the edges and highly structured in the core. At the edge, a clean, low-friction web interface orchestrates an intake pipeline that gathers business context and technical signals; in the core, a rules/ML evaluation layer translates those signals into assured guidance and audit-grade outputs. The platform is organised into clearly bounded subsystems—front-end UI, API gateway, rule/LLM evaluation, evidence collectors, report/export services—each with its own trust boundary and identity, so compromise cannot cascade. This mirrors the philosophy already set elsewhere in the PRD: regulation is treated as structured data, not prose, allowing the engine to map obligations to evidence artifacts and keep those mappings current as frameworks evolve. The same foundation that powers cross-framework equivalence also powers product simplicity: rule logic and evidence relationships live as first-class objects the system can version, test, and explain.

Security and trust are baked into the architecture rather than bolted on. Every human and machine actor is authenticated and authorised before any capability is exposed, with policy-as-code enforcing least privilege across roles, resources, and runtime context; identities (including services and connectors) are unique and cryptographic, enabling short-lived, revocable trust that’s observable end-to-end. Network paths are segmented and verified—no implicit trust, east-west flows are constrained, and all movement is mutually authenticated and encrypted—so the topology itself becomes a living security control. This design aligns the product’s internals with the assurance it sells: evidenceable controls, immutable audit events, and a security posture that can be demonstrated in real time.

Extensibility is a primary property, not a roadmap footnote. Because frameworks are abstracted into portable rule/evidence objects, expansion to new jurisdictions is a data operation—swap in new mappings, keep the engine—and cross-jurisdiction dashboards become feasible without re-architecting. The same decomposition (intake → rule/LLM evaluation → evidence binding → narrative/report) lets us add new collectors, alternative LLMs, and partner connectors without touching the core. Practically, this yields a platform that can start focused on UK SMEs and then scale horizontally into the EU (NIS2/DORA) and Commonwealth markets by adding definitions and localisations while preserving the assurance model and user experience. In short: a composable graph of obligations, controls, and evidence, secured by identity-centric boundaries, and designed to grow by data, not code.

### Framework Modularity

The compliance layer separates **control logic** from **application logic**. Controls, tests, and question sets live as **data-driven schemas**, versioned and loaded from signed configuration bundles. This allows the platform to:
- plug in new regulatory frameworks by adding schema files,
- update existing control logic without redeploying the codebase, and
- map overlapping controls between frameworks (for example, CE → NIS2 → ISO 27001).

All mappings are stored in a normalised meta-model so reporting and dashboards stay consistent across jurisdictions.

### 3.1.1 System Overview

Transcrypt Core’s architecture adopts mature enterprise patterns—segmented networks, signed artifacts, containerised services—but packages them as a managed backbone that the SME user never has to configure. Every component is orchestrated for resilience and assurance while presenting only a guided workflow at the surface.

### Data Ownership and Sovereignty

Transcrypt operates as a **centrally orchestrated, locally encrypted SaaS**.  
Each tenant’s data resides within shared infrastructure but is sealed with **tenant-specific encryption keys** that only the tenant can use.  
Transcrypt Ltd cannot decrypt customer evidence, policies, or logs.  
Backups and replicas are encrypted at rest and in transit, ensuring geographic redundancy without central visibility.  
Data sovereignty follows a “trust by math, not by policy” principle — enforced through cryptography rather than contractual language.

### Automation-First Operating Model

Transcrypt operates on the principle of **Automation First**:
every task that can be safely automated is automated before humans are involved.
Where expert review adds assurance (e.g. external certification, policy vetting), the system supports a future “Assisted Tier” via secure review portals.
v1 contains no human-review workflow.

### Invisible Infrastructure Principle

Complexity in Transcrypt exists only to remove effort for the user.  
Containerisation, encryption layers, and rule engines are hidden beneath a **single guided workflow**.  
Every architectural decision—data isolation, AI pipelines, event hashing—serves one aim: **fewer clicks, clearer answers, faster compliance**.  
The platform never exposes its internal mechanics; it turns them into plain-English outcomes.

**3.1.1.1 Runtime topology (high level)**

* **Edge/UI** → **API Gateway** → **Core Services** (Evaluation, Reporting, Evidence) → **Data Stores** (Rules, Tenants, Artifacts).
* Identity-aware proxy in front of every service; no east–west traffic without mutual auth.

**3.1.1.2 Trust boundaries**

* **Public zone:** Web app + gateway.
* **App zone:** Stateless services (evaluation, reporting, connectors).
* **Data zone:** DB, object storage, KMS; isolated network, access via service identities only.

### User Tiers and Human Interaction Model

| Tier | Name | Description | Human Involvement |
|:----:|:-----|:-------------|:-----------------|
| v1.0 | Transcrypt Core | Full self-serve AI automation for SMEs | None |
| v1.5 | Assisted Tier (β) | Optional human review of AI-generated reports via auditor portal | Limited |
| v2.0 | Platform Tier | Integrated marketplace for auditors, consultants and partners | Extensive |

---

### 3.1.2 Core Components and Interfaces

**3.1.2.1 Web App (Intake & Console)**

* Responsibilities: Guided intake, uploads, status, downloads, billing.
* Interfaces: HTTPS → API Gateway (REST/JSON), OIDC for login.

**3.1.2.2 API Gateway & Policy Enforcement**

* Responsibilities: AuthN (OIDC), AuthZ (OPA/Rego), request signing, rate limiting, audit headers.
* Interfaces: `/auth/*`, `/tenants/*`, `/reports/*`, `/evidence/*`.

**3.1.2.3 Rule Engine (Deterministic)**

* Responsibilities: Load compiled rule artifacts; evaluate applicability/tests; produce findings with provenance.
* Interfaces: `POST /evaluate` (OrgProfile, EvidenceInventory, RulePackID) → Findings JSON; `GET /explain/:rule_id`.

**3.1.2.4 LLM Assist Pipeline (Build-time only)**

* Responsibilities: Draft rules from clauses; suggest equivalences; summarise diffs; generate plain-English copy.
* Interfaces: Offline CLI / worker queue; outputs JSON conforming to Rule Schema; never used at runtime.

**3.1.2.5 Evidence Services**

* Responsibilities: File ingest, hashing, metadata, connector pulls (IdP exports, backups, EDR).
* Interfaces: `POST /evidence/files`, `POST /evidence/assertions`, connector webhooks; stores to object storage with signed URLs.

**3.1.2.6 Report Service**

* Responsibilities: Assemble findings → prioritisation → PDF/HTML; embed citations and evidence links.
* Interfaces: `POST /reports/generate` → report blob; `GET /reports/:id`.

**3.1.2.7 Partner/Integrator API**

* Responsibilities: Multi-tenant management (MSPs/insurers), read-only posture, webhooks.
* Interfaces: `GET /partners/tenants`, `GET /partners/findings`, `POST /webhooks`.

---

### 3.1.3 Data Model (Canonical Contracts)

**3.1.3.1 OrgProfile**

```json
{ "company": {"name":"", "employees":0, "sector":""},
  "it": {"idp":"EntraID|Okta|Google","email":"M365|Google","endpoints":{"count":0,"edr":""}},
  "remote_access":{"vpn":true}, "backups":{"server":"daily","immutable":false},
  "policies":{"password":"exists","incident":"missing"}, "notes":[] }
```

**3.1.3.2 EvidenceInventory**

```json
{ "files":[{"name":"idp_policy.json","type":"config","hash":"..."}],
  "assertions":[{"key":"MFA.enforced.admins","value":true,"source":"idp_policy.json"}] }
```

**3.1.3.3 Rule (compiled)**

```json
{ "id":"CE-AC-001","title":"MFA for admin accounts",
  "applicability":{"if":["ORG.it.idp != null"]},
  "test":{"all":[{"equals":["ASSERT.MFA.enforced.admins", true]}]},
  "evidence":["idp_policy.json"], "citations":[{"doc":"CE-2025","section":"AC.1.1"}] }
```

**3.1.3.4 Finding**

```json
{ "rule_id":"CE-AC-001","status":"pass|fail|partial",
  "reason":"Exact test result…","evidence":["idp_policy.json"],
  "citations":[{"doc":"CE-2025","section":"AC.1.1"}], "priority":1 }
```

**3.1.3.5 Report (envelope)**

```json
{ "tenant":"...", "generated_at":"ISO8601", "summary":"…",
  "top_actions":[ "...", "..." ], "findings":[ ... ], "artifact_hash":"..." }
```

---

### 3.1.4 Storage and Artifacts

**3.1.4.1 Tenant DB (Postgres)**

* Tables: `tenants`, `users`, `org_profiles`, `findings`, `reports`, `audit_events`.
* JSONB for profiles/findings; row-level security per tenant.

**3.1.4.2 Object Storage (Artifacts & Evidence)**

* Buckets: `rule-artifacts/` (immutable, hash-addressed), `evidence/tenant-id/`.
* Server-side encryption + per-object metadata (hash, uploader, rule links).

**3.1.4.3 Artifact Registry**

* Compiled RulePacks indexed by SHA-256; manifest lists versions, diffs, effective dates.

---

### 3.1.5 Security, Privacy, and Trust Model

**3.1.5.1 Identity & Access**

* OIDC login (MFA enforced), short-lived JWTs; service identities via mTLS; policy-as-code (OPA) for AuthZ.

**3.1.5.2 Crypto & Secrets**

* TLS 1.3 everywhere, mTLS service-to-service; AES-256-GCM at rest; KMS-managed KEKs; Vault for secrets; automated rotation.

**3.1.5.3 Network & Isolation**

* Segmented VPC/VNet: public (edge), app (services), data (DB/KMS). Only proxy reaches app; only app reaches data.

**3.1.5.4 Privacy**

* Data minimisation, per-tenant isolation, GDPR DSR endpoints (export/delete), redaction pipeline for AI prompts (build-time only).

**3.1.5.5 Audit & Observability**

* Structured logs with tenant/request IDs; immutable audit trail (write-once store); traces/metrics with SLO alerts.

---

### 3.1.6 Extensibility & Integration Framework

**3.1.6.1 Framework Packs**

* Portable rule/evidence packs for CE, NIS2, ISO 27001; locale text separated; hot-swappable by `RulePackID`.

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

* **Includes:** Core Plan only; 15 CE controls; OrgProfile/Evidence schemas; `/evaluate` + `/reports/generate`; Stripe billing; evidence uploads.
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

### 3.2 Core Components and Interfaces

#### 3.2.1 Web App (Next.js @ `https://transcrypt.xyz`)

* **Purpose:** Guided intake, evidence uploads, posture dashboard, report generation/download, billing.
* **Key routes:**

  * **Marketing:** `/`, `/product`, `/pricing`, `/about`, `/contact`, `/blog/*`, `/changelog`, `/status`, `/roadmap` (optional).
  * **Legal & trust:** `/privacy` → alias to `/legal/privacy`, `/terms` → `/legal/terms`, `/cookies` → `/legal/cookies`, `/dpa`, `/subprocessors`, `/acceptable-use`, `/accessibility`, `/licenses`, `/security`.
  * **App (auth-gated):** `/app/*` – intake `/app/intake/*`, evidence `/app/evidence`, reports `/app/reports/*`, settings `/app/settings`.
  * **Developer (future):** `/developers`, `/docs/api`, `/webhooks` (catalogue).
* **Auth/session:** OIDC (Entra/Okta/Google) via next-auth; short-lived JWT session (`SameSite=Lax`, `Secure`, `HttpOnly`); step-up MFA for admin actions.
* **Interfaces:** HTTPS → `/api/*` (REST/JSON with zod validation). Tenant context from session claim; optional deep links `/t/:tenant/*`.

#### 3.2.2 API Gateway & Policy Enforcement

* **Purpose:** Single ingress for all APIs; central AuthN/AuthZ, rate limiting, audit headers.
* **Responsibilities:** Verify OIDC tokens; attach `X-Tenant-Id`, `X-Request-Id`, `X-Audit-Actor`; enforce **policy-as-code** (OPA/Rego); terminate TLS; mTLS to internal services.
* **Interfaces:**

  * Auth: `POST /api/auth/callback`, `POST /api/auth/logout`.
  * Tenant: `GET /api/tenants/me`, `POST /api/tenants/switch`.
  * Health: `GET /api/healthz` (unauthenticated ping), `GET /api/readyz` (auth, deeper checks).

#### 3.2.3 Rule Evaluation Service (Deterministic)

* **Purpose:** Evaluate controls for a tenant/profile against an **immutable, signed RulePack**.
* **Interfaces:**

  * `POST /api/evaluate`

    * **Request:** `{ "rule_pack": "CE-2025.3#sha256:...", "org_profile": {...}, "evidence": {...} }`
    * **Response:** `{ "findings":[{ "rule_id":"...", "status":"pass|fail|partial", "reason":"...", "evidence":[...], "citations":[...] }], "artifact_hash":"..." }`
  * `GET /api/evaluate/explain/:rule_id` → returns provenance (tests run, inputs, citations).
* **Notes:** Stateless; loads RulePacks by hash; **no LLM** in runtime path.

#### 3.2.4 LLM Assist Pipeline (Build-Time Only)

* **Purpose:** Draft rule objects from clauses; suggest cross-framework equivalences; produce human-readable summaries/diffs.
* **Interfaces (CLI/worker):**

  * `rules draft <source.pdf>` → `rules/*.json` (schema-conformant, citations required).
  * `rules diff <old> <new>` → `diff.json` + `CHANGELOG.md`.
* **Guardrails:** JSON Schema validation; missing citations = build fail; human review before publish.

#### 3.2.5 Evidence Services

* **Purpose:** Ingest and index evidence (files + assertions) with integrity metadata, never orphaned from rules.
* **Interfaces:**

  * `POST /api/evidence/files` (multipart) → `{ id, sha256, url }`.
  * `POST /api/evidence/assertions` → `{ key:"MFA.enforced.admins", value:true, source:"idp_policy.json" }`.
  * Connectors (optional webhooks): `/api/connectors/idp`, `/api/connectors/backup`, `/api/connectors/edr`.
* **Storage contract:** S3-compatible object store `evidence/{tenant}/{uuid}` (server-side encryption, signed URLs) + Postgres metadata.

#### 3.2.6 Report Service

* **Purpose:** Convert findings → prioritised actions → **HTML/PDF** with embedded citations and artifact hash.
* **Interfaces:**

  * `POST /api/reports/generate` → `{ report_id, download_url, summary }`.
  * `GET /api/reports/:id` → full envelope (exec summary, top actions, findings, citations).
* **Rendering:** Jinja2 → HTML → WeasyPrint PDF; SHA-256 of inputs stamped in footer.

#### 3.2.7 Partner / Integrator API

* **Purpose:** MSPs/insurers manage many tenants, receive posture and events.
* **Interfaces (token-scoped, read-majority):**

  * `GET /api/partners/tenants` (list/paginate)
  * `GET /api/partners/tenants/:id/posture` (roll-up posture)
  * `POST /api/partners/webhooks` (subscribe to `report.generated`, `finding.changed`)
* **Notes:** Strict RBAC; no cross-tenant writes; throttled exports.

#### 3.2.8 Admin Console (Internal)

* **Purpose:** RulePack lifecycle, sandbox what-if evaluations, release approvals.
* **Interfaces:**

  * `POST /api/admin/rulepacks/publish`, `GET /api/admin/rulepacks/:hash`.
  * `POST /api/admin/evaluate/simulate` with synthetic OrgProfile/Evidence.

#### 3.2.9 Data Stores & Artifacts (Interface Contracts)

* **Postgres (RLS per tenant):** `tenants`, `users`, `org_profiles(jsonb)`, `evidence_index`, `findings(jsonb)`, `reports`, `audit_events`.
* **Artifact Registry (immutable):** `rulepacks/{hash}.json`, `manifest.json`, `diffs/{from}-{to}.json`.
* **Schemas:** All payloads carry `"schema": "OrgProfileV1" | "EvidenceV1" | "FindingsV1"` for fwd/back compat.

#### 3.2.10 Observability & Audit

* **Purpose:** End-to-end traceability for support and assurance.
* **Interfaces:** OpenTelemetry export (`/otel/v1/*`); structured logs include `tenant_id`, `rule_pack_hash`, `trace_id`; append-only `audit_events` via write-only API from gateway/services.
* **User-visible:** `/app/settings/audit` — filterable per-tenant audit viewer.

#### 3.2.11 Public Site & Content (Marketing, Legal, Support)

* **Primary public routes:**

  * Marketing: `/`, `/product`, `/pricing`, `/about`, `/contact`, `/blog/*`, `/changelog`, `/status`, `/roadmap` (optional).
  * Legal & trust: `/legal/*` with **aliases** `/privacy`, `/terms`, `/cookies`; plus `/dpa`, `/subprocessors`, `/acceptable-use`, `/accessibility`, `/licenses`, `/security`.
  * Support: `/support` (FAQ hub), `/dsr` (Data Subject Requests portal/form).
* **Contact endpoint:** `POST /api/contact` → `{ name, email, subject, message, consent, meta }` (hCaptcha/Turnstile, rate-limited, ack with `ticket_id`).
* **SEO/Discoverability:** `sitemap.xml`, `robots.txt`, JSON-LD, OG/Twitter cards, RSS for blog.

#### 3.2.12 External Integrations (First-Party)

* **Identity Providers:** OIDC flows at `/api/auth/*`.
* **Billing:** Stripe Checkout; webhook `POST /api/billing/webhook` (subscription create/update/cancel).
* **Email (later):** transactional mail; SPF/DKIM/DMARC configured for `transcrypt.xyz`.
* **Well-known:** `/.well-known/security.txt`, `/.well-known/change-password`.

#### 3.2.13 Non-Functional Interface Contracts

* **Security headers:** CSP (nonce’d), HSTS (preload), Referrer-Policy `strict-origin-when-cross-origin`, X-Frame-Options `DENY`, X-Content-Type-Options `nosniff`.
* **Auth requirements:** All `/api/*` require valid JWT with `sub`, `tenant_id`, `scopes`; machine calls use mTLS + token.
* **Rate limits:** Per-IP + per-tenant; stricter on `/api/auth/*`, `/api/evidence/files`, `/api/contact`.
* **Error model:** Problem+JSON → `{ "type": "https://transcrypt.xyz/errors/<code>", "title": "...", "status": 400, "detail": "...", "trace_id": "..." }`.

### 3.3 Security, Privacy, and Trust Model

Transcrypt treats **identity as the perimeter** and **evidence as the arbiter of trust**. Every human and machine action is authenticated (OIDC for users, mTLS for services), authorised by **policy-as-code** (OPA/Rego), and logged with immutable metadata (tenant, actor, rule pack, trace ID). Network paths are **zero-trust by default**: no implicit east–west access, service meshes enforce mutual TLS, and privileges are created just-in-time and discarded immediately after use. Data is encrypted **in transit (TLS 1.3/PFS)** and **at rest (AES-256-GCM)** with keys managed and rotated by a KMS; secrets are injected at runtime via a vault and never committed to source. Runtime environments are ephemeral and reproducible; builds are signed and accompanied by SBOMs and SLSA-style provenance so that what runs can be traced back to who approved it and which inputs it contained. The result is a system where security isn’t a bolted-on checklist but a property of the topology, the pipeline, and the artifacts.

Privacy is engineered as **data minimisation, isolation, and control**. Tenants are logically isolated (row-level security on Postgres plus per-tenant object-store prefixes), and the app collects only what’s needed to evaluate controls and generate reports. Evidence is never “loose”: every file or assertion is bound to a control, version, and citation, with hashes and timestamps for provenance. Users own their data; Transcrypt is a processor under UK GDPR. The platform exposes **self-service Data Subject Rights** (export/delete) and publishes clear retention schedules; AI prompts are **redacted** to avoid sending sensitive content to models, and LLMs are used **only** at build-time for drafting and summarisation—never for runtime scoring. Legal pages (Privacy, DPA, Sub-processors) are versioned in the repo; changes are diffable and linked from the site. Cookie/telemetry loading respects explicit consent, and analytics run in a privacy-preserving mode with PII excluded by design.

Trust is made observable through **transparent operations and verifiable assurances**. A public status page, changelog, and governance notes show uptime, incidents, and remediation; `/.well-known/security.txt` advertises a responsible disclosure path and optional PGP key. Incident response follows a time-boxed playbook (detect → contain → eradicate → recover → RCA), and every RCA is a signed artifact linked to the code/config changes it triggered. Continuous testing covers security (dependency and container scans), functionality (unit/integration/E2E), and drift (policy and posture checks); failed gates block release. Where standards matter, the system maps directly to **Cyber Essentials** hygiene, **ISO 27001** governance, **NIS/NIS2** resilience, and **IEC 62443** zone/conduit separation—so controls aren’t just present, they are **explainable** in the language auditors use. In short: authenticate everything, authorise least, encrypt always, minimise data, and prove it—with artifacts anyone qualified can inspect.

### 3.4 Extensibility and Integration Framework

Transcrypt is designed to grow **by data, not by rewrite**. The core engine treats frameworks, controls, and evidence definitions as portable **RulePacks**—signed JSON artifacts that the runtime loads by hash. Adding NIS2, DORA, or ISO 27001 doesn’t change code paths: you publish a new RulePack with mapped controls, equivalence links, and test clauses; the evaluation service remains deterministic. Textual outputs (headings, rationales, actions) live as locale bundles, so jurisdictional expansion is translation work, not refactoring. Report rendering is a themeable template layer (HTML → PDF) that reads the same Findings schema, allowing new formats or styles without touching evaluation logic.

Integration follows a **connector + event** model. Connectors are small, sandboxed pullers/posters that transform external proofs (IdP exports, backup configs, EDR posture, cloud config snapshots) into **EvidenceInventory** assertions or file artifacts. They run out-of-band via jobs/queues, publish to the evidence API, and never gain direct DB write access. Events from the core—`report.generated`, `finding.changed`, `evidence.added`—are emitted to webhooks with signed payloads, enabling MSP dashboards, insurer ingestion, or customer SIEM correlation. A public **Partner API** exposes read-scoped endpoints (tenant roll-ups, findings, reports) with strict RBAC and pagination, while exports use open, durable formats (JSON/JSON-LD) so downstream systems can store or rehydrate results without vendor lock-in.

Extensibility is governed by **versioned contracts** and forward-compat rules. Every payload carries a `schema` tag (e.g., `OrgProfileV1`, `EvidenceV1`, `FindingsV1`); minor releases add optional fields, major releases ship with a migration manifest and deprecation window. RulePacks and templates are immutable by content hash; new revisions publish as new artifacts with a machine-readable `diff.json` so partners can pre-compute the impact of framework updates. SDKs (lightweight) provide typed models, request builders, webhook verifiers, and a connector scaffold (auth, polling, backoff, signing). LLM use remains a **build-time extension point** only—providers are pluggable, prompts redacted, outputs schema-validated—so runtime determinism and auditability never depend on a model vendor. In combination, RulePacks, connectors, events, and stable schemas make the platform easy to extend, safe to integrate, and boring to operate—the exact temperament you want in compliance infrastructure.

### 3.5 Technical Stack and Dependencies

**Frontend**

* **Framework:** Next.js (App Router) + React. **Styling:** TailwindCSS for app UI, **SCSS tokens** for brand theming/marketing (Dart Sass). Tokens exposed as CSS variables and consumed by Tailwind (single source of truth).
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
* **Object storage:** S3-compatible bucket(s) for evidence/artifacts; server-side encryption; signed URLs.
* **Artifact registry:** Immutable RulePacks (`rulepacks/{sha256}.json`), manifests, diffs; addressed by content hash.
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
* **Determinism & audit:** Fixed prompts with versioned templates; low-variance settings; prompt + response + model/version **persisted as an artifact** tied to the resulting RulePack or text block.
* **Validation:** JSON outputs schema-validated; missing citations or invalid structure = build fail; human review required before publish.
* **Evaluation harness:** Golden-file tests for copy; regression checks to detect drift across model upgrades.
* **Caching:** Content-addressed cache of prompt→response during builds to reduce cost/latency; cache is invalidated on template/model changes.
* **Model registry & provenance:** Track model name, version/commit, licence/usage terms; surface in `/licenses` and internal release notes.
* **Storage:** All AI artifacts stored in the **artifact registry** alongside RulePacks; reproducible by hash.
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
* **Report that stands on its own:** Executive summary, top actions, citations, artifact hash in the footer, printable and shareable.
* **Posture page that changes behaviour:** A small set of “next best actions” that link back to the exact input/evidence needed.

### Copy & interaction tone

Plain English, short sentences, active verbs. Replace abstractions with concrete asks (“Upload your IdP export” not “Provide identity artefacts”). For every required field, a one-line “why this matters” anchored to the framework.

### Where we will *not* compromise

* **No runtime AI decisions.** LLMs help at build-time to draft text or mappings; the user-visible output is deterministic and traceable.
* **No labyrinthine nav.** Five app areas maximum: Dashboard, Intake, Evidence, Reports, Settings. Partner view is separate.
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
* **Correct routing.** Different visitors need different doors: Owner → trial, Tech helper → invite flow, Auditor/Insurer → verifier path, Partner → portfolio & API docs. The site’s IA should route them deliberately.
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

3. **Partner/MSP (portfolio path)**

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
* **/pricing:** Three plans (Core/Pro/Partner) plus “What’s included” map to features the app really ships. No hidden fees. Annual toggle.
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

#### 4.1.1 Public Site Journeys (credibility → correct door → app intent)

* **Cold SME owner (conversion path):** `/` → `/product` → `/pricing` → `/security` → **Start Free Trial**.
  **Promises shown:** “First defensible report in one sitting,” screenshots of **Quick Start / Findings / PDF**, plain-English “no runtime AI” badge, simple pricing.
  **CTA:** `https://transcrypt.xyz/app/signup?intent=trial&rulePack=CE-2025.3`.
  **Acceptance/KPIs:** Hero→Product CTR ≥ 35%; visit→signup ≥ 6–10%; first proof block visible < 30 s.
* **Researcher/validator (assurance path):** `/` → `/security` → `/privacy` (`/legal/privacy`) → `/changelog` → **Request Sample** or **Contact**.
  **Promises shown:** controls overview, responsible disclosure (`/.well-known/security.txt`), DPA/subprocessors, signed build/provenance note.
  **CTA:** `…/app/demo` (read-only sample) or `/contact`.
  **KPIs:** Time on `/security` > 90 s; ≥ 60% touch at least one legal page.
* **Partner/MSP (portfolio path):** `/partners` → `/product#multi-tenant` → `/docs/api` → **Book Partner Call**. [[Post-MVP: see §9 Roadmap]]
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
3. **Partner referral (MSP/insurer):** Referral token sets `plan=partner` and `rulePack=CE-2025.3`; Quick Start copy tuned to insurer context.
4. **Auditor view (read-only):** Time-boxed link → posture + latest report; same identity spine; no write paths.

**Quick Start (same three cards for all)**

* **Card 1 — Tell us about your setup** (≤ 20 required fields, autosave): company size, sector, IdP (Entra/Okta/Google), email platform (M365/Google), endpoints (rough count), backups (y/n + immutable y/n), remote access (VPN y/n), key policies present (password/incident/access control y/n), report contact email.
* **Card 2 — Add proof (optional now, later is fine):** drag-drop **Evidence Tray** (IdP export, backup config). Each file shows SHA-256, duplicate flagging, and **must bind** to a control/citation. Assertions supported (e.g., `MFA.enforced.admins=true`).
* **Card 3 — Run assessment:** choose **RulePack = Cyber Essentials**, show version + effective date, press **Run**. Progress shows “Evaluating 15 controls from CE-2025.3…”.

**Finding & report experience**

* **Finding cards:** Pass/Fail/Partial chip; one-sentence “because…”, **Show trace** (inputs, test, citations), **Fix it** jumps to exact intake/evidence field. Right rail: **Top 5 actions** (effort × impact).
* **Report:** Branded HTML/PDF with exec summary, citations, and artifact hash in footer; **Download PDF** and **Share read-only link** (time-boxed). From report: **Invite tech helper** and **Connect insurer/MSP**.

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

This ties the **public credibility flow** to the **authenticated first-value flow** so visitors become confident users quickly, with proof baked in at every step.

1. **Direct signup (owner/admin):** Email → OIDC → MFA → Tenant name → lands in **Quick Start**.
2. **Invite accept (tech helper):** Magic link pre-fills tenant + role; skips billing; lands straight in **Evidence/Intake** with a “Here’s what we need from you” checklist.
3. **Partner referral (MSP/insurer):** Referral token pre-selects the RulePack and plan; lands in Quick Start with copy tuned to “get your posture for insurer X”.
4. **Auditor view (read-only):** Time-boxed link to posture + latest report; no onboarding, but uses the same identity/magic link spine.

Regardless of lane, everyone hits the same **three-card Quick Start**:

* **1. Tell us about your setup** (≤20 fields, autosave; company size, sector, IdP, endpoints count, backups yes/no, remote access yes/no, key policies yes/no).
* **2. Add proof (optional now, later is fine)** (upload IdP export, backup config; or skip).
* **3. Run assessment** (choose RulePack = Cyber Essentials, show version and effective date, press Go).
  Copy is short, specific, and explains *why* each answer matters. Every required field has a one-line rationale: “This helps us test AC.1.1 (MFA on admin accounts).” No long forms. No jargon soup. If a user leaves, they can resume exactly where they were.

### Screen-by-screen: what good looks like

* **Signup & MFA (≤3 minutes):** OIDC, confirm email, show recovery codes, friendly “You’re done—let’s get your first report.”
* **Quick Start (single page, three cards):** Progress bar + “Time left ~15 min.” Card 1 uses branching (e.g., selecting “Entra ID” unlocks a small panel: “Upload your Conditional Access export or tick ‘we’ll upload later’”). Card 2 is an **Evidence Tray** with drag-and-drop and instant SHA-256 display; duplicates are flagged, and each file must be bound to a control (“Bind to: MFA policy” dropdown). Card 3 is a big primary button: **Run assessment**; we show a 10–30s progress state with a line like “Evaluating 15 controls from CE-2025.3…”.
* **Results (finding cards):** Pass/Fail/Partial chips; one-sentence “because…”, a “Show trace” link (inputs, test, citations), and a **Fix it** CTA that jumps to the exact intake/evidence field. A right-side panel lists the **Top 5 actions** with estimated effort and impact.
* **Report (download/preview):** Branded HTML with exec summary, citations, and artifact hash in the footer; **Download PDF** and **Share read-only link (time-boxed)**. From here: “Invite your tech helper” (precomposed invite) and “Connect insurer/MSP” (partner flow).
* **Return experience (dashboard):** Posture badge, “time since last assessment,” and “What changed” diff if they’ve re-run.

### Guardrails, nudges, and acceptance

* **Guardrails:** Autosave every 3 seconds; client + server validation (tell user *what* broke + *how to fix*); all long actions idempotent with Request-ID; Problem+JSON errors bubble a friendly message and surface a **trace_id** for support.
* **Nudges:** If a user skips evidence, we schedule a gentle nudge (24–72h): “Attach these two items to turn 3 partials into passes.” If a RulePack updates, a banner explains the change and offers a 1-click re-run.
* **Acceptance criteria:** From a fresh browser, **signup→MFA→first report in ≤60 minutes** without docs. Intake ≤20 required fields; first evaluation <2 minutes; PDF in <10s; every finding links to rule, trace, and evidence (if any). Support load target: ≤0.2 tickets/user/month for onboarding.
* **Fields we’ll start with (tight list):** company name/sector/size, IdP (Entra/Okta/Google) + admin MFA yes/no, email platform (M365/Google), endpoints count (rough), backups (y/n + immutable y/n), remote access (VPN y/n), key policies present (password, incident, access control y/n), contact email for reports. That’s it.

If you’re happy with this spine, the next tangible step is to sketch the **Quick Start** and **Finding Card** as wireframes in your doc—the rest of the UX hangs from those two artifacts.


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
* **Acceptance:** account+MFA in <3 minutes; intake ≤20 required fields with autosave; first evaluation <2 minutes; report renders HTML/PDF with citations and artifact hash; dashboard shows “Top 5 actions” linking back to precise inputs; billing works via Stripe; audit trail records major actions.

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
* PDF export preserves tags/structure from HTML; figures have alt text; the artifact hash and citations are text, not images; doc language set; reading order verified.

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
  3. **Report offline:** After generating a report online, user can open the same report offline and print it; artifact hash remains visible and selectable text (not an image).
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

This section defines how information becomes value—how raw inputs (answers, evidence, context) move through deterministic logic to produce findings, actions, and reports—without gambling on opaque AI at runtime. We draw a bright line: runtime = deterministic, auditable, reproducible; build-time = where AI helps draft, summarise, and map. Everything here exists to shorten time-to-truth while preserving provenance: explicit schemas for each payload (OrgProfileV1, EvidenceV1, FindingsV1, ReportEnvelopeV1), content-addressed artifacts (rule packs, templates, AI outputs) addressed by hash, and append-only audit trails that explain “who did what, with which inputs, and when.” The result should be boring in the right way: identical inputs produce identical outputs; every assertion and control links to citations; every report footer carries a verifiable artifact hash.

We also specify the automation backbone that keeps posture fresh and reduces toil. Ingest happens via guided intake, file uploads, or light connectors that transform external proofs (IdP exports, backup configs, endpoint inventories) into bound evidence—never loose files—tagged to controls and citations. A job queue handles long-running work (PDF rendering, export bundles, partner webhooks) with idempotency keys and backoff; schedulers run posture refresh, stale-evidence nudges, and framework update prompts. The offline/PWA lane lets users complete intake, queue evidence, and view the last report without a network; a sync layer replays queued mutations safely on reconnect and surfaces conflicts at field level. Dashboards and reports are just different lenses on the same truth: prioritised actions (effort × impact), diffs since last run, coverage of evidence, and simple roll-ups for partners—always explainable, never theatrical.

Finally, this section codifies our trust guarantees and IP boundary. Privacy is engineered by design (data minimisation, tenant isolation, short-lived tokens, local caching that’s optional and encrypted in “Secure Device Mode”), and AI is constrained to build-time with redaction, citation requirements, and human review. We define what is proprietary (rule-pack curation, prioritisation heuristics, templates, admin tools, connector scaffolds) and what remains standardised (REST/JSON, webhooks, JSON/JSON-LD exports, identity flows). We set measurable targets—time-to-first-report ≤ 60 minutes, ≥ 80% of failing/partial findings bound to evidence within 14 days, ≥ 95% sync success within 2 minutes of reconnect—and we make verification first-class (downloadable traces, re-execution procedure, public status/changelog). In short: clear data contracts, deterministic intelligence, automation that earns trust, and a crisp delineation between open interfaces and protected craft.

### 5.1 Data Flow Architecture (v1)
Input (guided forms/uploads) → Validation → Evidence Vault (tenant-encrypted) → Rules Engine (CE checks) → Insights/Reports.
No cross-tenant processing. All AI calls are stateless inference with minimal PII footprint.
Although Transcrypt employs modern orchestration and automation patterns, these are invisible to the SME user. The only visible surface is the guided flow; all scaling, queueing, and AI orchestration run silently in the background.

> **Tenant Isolation:** All evidence and report objects are encrypted client-side before upload.  
> Processing occurs on ephemeral decrypted copies inside isolated containers that are destroyed after execution.  
> Only encrypted artefacts persist; no plaintext is stored centrally.

> **Framework Agnostic Design:**
> Data ingestion, evidence storage, and rules execution reference control-pack metadata, not hard-coded UK criteria.
> This allows new jurisdictions or standards to be loaded as configuration rather than forked code.

### 5.2 Machine Learning and AI Components (v1)
All compliance logic in v1 is executed autonomously by the rules engine and AI assistants.
Human oversight is not part of the MVP loop; instead the system creates traceable outputs that can later be reviewed by auditors in the Assisted Tier.
AI assists the user rather than overwhelms them—its purpose is to *simplify judgement calls*, not introduce new interfaces or tuning.
- **Extraction:** classify uploads (policy vs invoice vs screenshot), extract dates/covers.
- **Drafting:** first-pass policies/templates; user reviews before saving.
- **Gap prompts:** suggest missing evidence based on CE checklist state.
_No training loops or fine-tuning in v1; models are managed centrally; outputs are user-confirmed. [[Post-MVP: see §9 Roadmap]]_

> **Post-MVP:** External assessor API and auditor portal to be introduced in §9 Roadmap phase v1.5 (Assisted Tier β).

### 5.3 Reporting, Dashboards, and Insights (v1)
- CE readiness score, section breakdown, renewal countdown, evidence completeness.  
- Export: PDF summary and evidence index.

### 5.4 Auditability and Data Provenance (v1)
> **Closed-Source Alignment:**
> The audit layer exposes every state change through signed event hashes.
> Verification tools are open-documented so external auditors can independently confirm integrity without needing code access.

- **Append-only** event log (who/what/when).
- Hashes per evidence file stored in log for tamper detection.
- No external ledger in v1 (see Roadmap v2.0).

### 5.5 Closed-Source Policy and Verifiable Transparency

**Principle:**  
Transcrypt’s source code is proprietary, but its **outputs are cryptographically verifiable** and its **behaviour auditable**.  
We trade *code visibility* for *mathematical verifiability*.

**Implementation (v1):**
- Core logic and AI models are closed-source binaries signed by Transcrypt Ltd.  
- Every system artefact—reports, evidence archives, audit logs—is **hashed and timestamped**.  
- Users can verify integrity via published checksum algorithms and manifest files.  
- No third-party or government has access to unencrypted user data; only the tenant holds decryption keys.  
- A public white-paper describes hashing standards, key management, and evidence verification workflow.

**Post-MVP (v2.0+):**
- Optional “**Proof of Process Ledger**” where audit hashes are notarised to an external distributed log.  
- Independent auditor verification API for attestations without code exposure.  
- Third-party reproducibility review programme for components under NDA.

<!-- specification -->
## 6. Compliance and Governance Framework

Transcrypt’s own credibility rests on the same standards it helps others to meet. Its internal compliance and governance framework is therefore designed as a living system of assurance that mirrors the principles of the product itself: transparency, proportionality, and continuous verification rather than static certification. The platform is engineered and operated within a structure that satisfies legal, ethical, and regulatory obligations from day one but remains light enough for a founder-led company. Governance is treated as architecture, not paperwork — embedded in code, workflows, and data handling policies.

### 6.1 Alignment with NIS, Cyber Essentials, ISO 27001, and IEC 62443

Transcrypt’s governance and assurance model is anchored in alignment with NIS, Cyber Essentials, ISO 27001, and IEC 62443—the four frameworks that together define the contemporary cybersecurity landscape across IT and operational domains. From NIS, Transcrypt inherits the organising principle of proportionate resilience: that security controls must scale with the service’s criticality and threat exposure. The system’s architecture enforces this by separating control logic, customer data, and AI functions into isolated components, ensuring that failure or compromise in one cannot propagate to another. Its logging, monitoring, and recovery workflows map directly to NIS obligations for availability, integrity, and incident management. In practice, the NIS alignment ensures that Transcrypt can one day act not only as a compliance platform for SMEs but also as a trusted node in the wider regulated ecosystem, capable of producing audit-grade evidence recognised by operators of essential services.

Cyber Essentials defines Transcrypt’s day-to-day operational hygiene. The five technical control themes—patching, secure configuration, access control, malware protection, and boundary defence—are embedded directly into the platform’s development and hosting pipelines. Every build undergoes automated vulnerability scanning, dependency patching, and configuration validation before deployment. Access to production systems is limited to MFA-enforced identities on managed devices, and malware prevention is treated as a base condition for participation in the network. This mapping is not theoretical: it underpins Transcrypt’s own certification plan and gives the platform credibility with small businesses who must demonstrate these same controls. The outcome is a product that practises what it preaches—internally compliant with the same framework it helps its customers to achieve.

At the governance layer, ISO 27001 and IEC 62443 together define Transcrypt’s structural DNA. ISO 27001 provides the managerial skeleton—risk management, control review, continual improvement—while IEC 62443 adds the engineering muscle: secure development lifecycle, least-privilege zoning, and explicit separation of safety and control functions. These combined standards shape both the software’s architecture and its operational ethos. Every significant change follows an assess-design-verify-release cycle derived from 62443-4-1, and the network model reflects the zone-and-conduit logic of 62443-3-3. This dual alignment signals that Transcrypt is not merely an IT compliance tool but an automation-aware security product—built to satisfy the same expectations that govern critical infrastructure. By grounding its internal governance in these frameworks, Transcrypt gains not only regulatory credibility but also a blueprint for resilience that will scale with its customers’ complexity.

### 6.2 Risk Management and Assurance

Transcrypt’s approach to risk management and assurance is modelled on engineering discipline rather than corporate ritual. It treats risk as a measurable, evolving system property—one that can be observed, modelled, and reduced through feedback loops. The company’s internal risk framework borrows from ISO 27005 and NIST SP 800-30 methodologies but is implemented as lightweight, living code. Each identified risk—technical, operational, or regulatory—is logged in a structured register stored under version control. Mitigations are tracked as pull requests, tying every control improvement directly to a change in configuration, code, or process. This approach ensures that assurance is demonstrable: every decision can be traced from threat to mitigation to verification, with timestamps and commit signatures forming a continuous audit trail.

Operationally, Transcrypt applies a three-layer model of assurance. At the base layer sits preventive control validation—automated scanning, dependency management, and configuration enforcement that continuously checks the integrity of the code and its environment. The second layer is detective and corrective assurance, achieved through real-time monitoring, error telemetry, and incident logging designed to capture anomalies long before they become incidents. The third layer—strategic oversight—operates on a quarterly cadence, reviewing risk trends, regulatory changes, and user feedback to recalibrate priorities. Each layer feeds the next, creating a self-correcting loop in which evidence of performance is continuously compared with expectations. This multi-layer design borrows from IEC 62443’s concept of defence-in-depth and adapts it to a software service context.

Assurance in Transcrypt is ultimately defined by verifiability—the ability to prove, not claim, that controls are effective. To this end, every key process—deployment, access management, evidence handling, and AI usage—is monitored and logged with immutable metadata. Independent review is built into the cycle: code review for security changes, periodic external penetration testing, and an annual compliance audit once the customer base matures. The company’s own platform acts as its assurance engine, ingesting these artefacts and producing an internal compliance dashboard. By turning its product inward, Transcrypt demonstrates that assurance is not a paperwork exercise but an operational reality—living, measurable, and continuously improved.

### 6.3 Policy Library and Evidence Management

Transcrypt’s Policy Library and Evidence Management system is the backbone of its credibility—where regulatory language becomes structured, verifiable data. The Policy Library is built as a version-controlled repository of all applicable standards, obligations, and internal operating policies. Each entry in the library is expressed as a modular rule object that links a control requirement (for example, “implement MFA for administrative access”) to its legal or framework source, implementation guidance, and verification method. This allows the same dataset to drive both Transcrypt’s internal assurance and the customer-facing product logic. By treating policies as code, every change—be it a regulatory amendment or a configuration tweak—creates a traceable, reviewable diff. In effect, the Policy Library functions as a live map of compliance intent, preserving provenance and change history with the precision of source code management.

Evidence management is designed to be both lightweight and rigorous, mirroring the “show, don’t tell” philosophy at the heart of compliance. Each piece of evidence—whether an uploaded document, configuration file, screenshot, or attestation—is stored as a signed record linked directly to its relevant controls in the Policy Library. Evidence is never orphaned: it always exists in relation to a rule, version, and verification outcome. Metadata such as timestamps, file hashes, and reviewer identifiers are captured automatically, ensuring authenticity without manual bookkeeping. Over time, this creates a longitudinal evidence chain that supports continuous assurance and reduces audit fatigue. For external auditors or customers, evidence can be exported as sealed bundles that contain the rule context, provenance, and cryptographic proofs of integrity.

Together, the Policy Library and Evidence Management subsystems close the loop between regulation, implementation, and proof. The former provides the structured definitions of what must be true; the latter provides the demonstrable artefacts that it is true. This alignment enables Transcrypt’s internal operations to be as auditable as the platform it offers to others. It also creates a self-reinforcing trust model: every control the company enforces on itself strengthens the logic it delivers to customers. By embedding compliance logic and evidence within the same unified data fabric, Transcrypt ensures that assurance is not a bureaucratic overlay but a living, queryable system—transparent to regulators, customers, and itself.

### 6.4 Legislative Alignment and Future Adaptation

Transcrypt’s Legislative Alignment and Future Adaptation strategy is built on the recognition that compliance is never static — regulation evolves faster than most businesses can interpret it. The platform therefore treats legislation as a data source, not a set of documents. Each new law, standard, or directive is decomposed into structured rules within the Policy Library, maintaining direct citations to the originating text. This makes it possible to version legislation in the same way code is versioned: when a clause changes, the affected rules are flagged, the differences are visible, and their operational implications are automatically assessed. The immediate benefit is agility — Transcrypt can track legislative change in near real time and update its compliance logic long before auditors or consultants have translated the new text. This architecture ensures that the product never falls behind the regulatory curve, and that customers inherit this alignment seamlessly through their subscriptions.

In the UK and Europe, Transcrypt’s legislative alignment is anchored to NIS2, DORA, GDPR, and the AI Act, each of which represents a distinct dimension of trust and accountability. NIS2 and DORA set expectations for operational resilience and supply-chain oversight, while GDPR governs data protection and lawful processing. The AI Act introduces obligations for transparency, traceability, and human oversight in algorithmic systems — principles already built into Transcrypt’s AI governance layer. By encoding these requirements as data structures rather than prose, the platform can simultaneously satisfy overlapping mandates, showing where a single control (such as MFA or data retention policy) supports multiple frameworks. This cross-mapping reduces redundancy for both the company and its users, and positions Transcrypt as a compliance translator — one schema capable of reflecting multiple regulatory domains.

Future adaptation extends beyond jurisdictional updates to encompass technological and policy evolution. As governments move toward machine-readable regulation and continuous assurance, Transcrypt’s architecture is already prepared: each rule, citation, and evidence link is structured for automated verification and external API exposure. This will allow regulators, insurers, or primes to consume proof directly from the platform, replacing static attestations with dynamic confidence. The governance process itself is designed for this trajectory — policy updates are treated as code commits, reviewed by humans, validated by the engine, and published with cryptographic signatures. In the long term, this makes Transcrypt a model for adaptive compliance: a living system capable of evolving with the law, maintaining perpetual alignment without manual reinvention, and demonstrating that compliance, like security, is best achieved through continuous measurement rather than periodic paperwork.

### 6.5 Governance of Product Lifecycle

Transcrypt’s Governance of the Product Lifecycle ensures that every stage of development — from concept to decommissioning — is accountable, documented, and secure. The lifecycle is governed by principles derived from ISO 27034 (application security), IEC 62443-4-1 (secure development lifecycle), and ISO 9001 (quality management), but implemented in lightweight, code-centred form. Each development phase — planning, build, test, release, operate — has explicit entry and exit criteria tied to version-controlled artefacts. All commits are signed; every feature or fix must trace back to an issue or requirement in the repository; and automated CI/CD checks enforce dependency scanning, linting, and security validation before merge. This transforms governance from paperwork into process: the discipline of compliance is performed by the toolchain itself.

During operation, lifecycle governance shifts from creation to maintenance and improvement. Continuous telemetry monitors performance, security posture, and error rates, feeding into a live operational logbook. Incidents are recorded with structured metadata — trigger, impact, response, resolution — and each one generates a root-cause analysis (RCA) that is reviewed and versioned alongside the code it concerns. Quarterly governance reviews assess these RCAs, audit change logs, and validate that the system continues to meet its intended security and compliance baselines. This rhythm of evidence generation and review embeds continual improvement into the engineering cadence, ensuring that Transcrypt’s platform and its internal controls evolve in lockstep.

End-of-life governance is treated with the same rigour as initial release. When components, APIs, or dependencies are retired, a formal sunset record is created documenting the reason, data-handling implications, and customer impact. Backward-compatibility layers or migration tools are maintained until all dependent customers have transitioned. Decommissioned data is securely wiped following NCSC and NIST 800-88 guidance, and audit logs are archived under retention policy for future verification. This ensures that even obsolescence is managed transparently — an often-neglected part of compliance that becomes a differentiator when customers or auditors assess maturity. Through this lifecycle discipline, Transcrypt demonstrates that governance is not a static certification badge but an ongoing expression of engineering integrity: every release, every fix, and every retirement leaves a clear, auditable trail of intent and accountability.


<!-- specification -->
## 7. Security and Infrastructure Requirements

Transcrypt’s Security and Infrastructure Requirements define the technical embodiment of its compliance philosophy — security not as an accessory, but as the substrate of the system. Every design decision is anchored in the principle of zero inherent trust: all actions must be authenticated, all data must be verifiable, and all communication must be observable. The architecture assumes compromise and is therefore built to contain and recover, rather than to depend on prevention alone. Infrastructure is designed to be modular, reproducible, and verifiable — every component declared as code, every dependency pinned, and every change logged. This approach transforms infrastructure into an auditable artefact: a living record of security posture rather than a collection of hidden configurations.

> See §5.5 Closed-Source Policy and Verifiable Transparency for details on how proprietary code maintains audit trustworthiness.

Security controls are embedded directly into the development and deployment pipeline. Continuous integration and continuous delivery (CI/CD) systems are instrumented with policy checks, dependency vulnerability scans, and static analysis gates that enforce compliance before a build can proceed. Runtime environments are ephemeral, instantiated from signed container images built only from verified sources. Secrets management, key rotation, and access provisioning are handled centrally through a dedicated identity and policy engine. Network isolation and strict least-privilege access ensure that each subsystem operates within its defined trust boundary. Monitoring, metrics, and logging form a closed assurance loop — data flows are visible, tamper-evident, and retained according to governance policy. This composition of infrastructure and security into a single pipeline reduces the distance between design intent and operational reality, making compliance continuously enforceable rather than periodically tested.

The overarching requirement is resilience — the ability of the platform to withstand, detect, and recover from disruption without loss of integrity or trust. Infrastructure is provisioned for high availability across multiple zones, and failover mechanisms are validated under controlled simulation. Incident response is pre-baked into the operational design: event correlation, alerting, and containment runbooks are codified and version-controlled alongside application code. The same approach extends to supply chain integrity: only signed dependencies are accepted, provenance is recorded, and each component can be traced back to its origin. In aggregate, these security and infrastructure requirements form a self-reinforcing system: one where design, operation, and recovery are governed by the same principle — that assurance must be provable in real time, not declared after the fact.

### 7.1 Authentication, Authorisation, and Identity Management

Transcrypt’s Authentication, Authorisation, and Identity Management architecture is built on the axiom that identity is the new perimeter. Every interaction—human or machine—is authenticated, authorised, and logged before any data or function is exposed. Authentication is federated wherever possible, using standards such as OpenID Connect and OAuth 2.0 to integrate with trusted identity providers (Entra ID, Google Workspace, Okta). This ensures users can employ strong, centrally managed credentials while Transcrypt enforces platform-level controls such as multi-factor authentication, device compliance, and session lifetime policies. Service accounts and automation tokens are never hard-coded; they are short-lived, scoped by purpose, and issued through a policy engine that embeds least privilege into their lifecycle. This foundation treats credentials not as static secrets but as ephemeral attestations of trust that expire by design.

Authorisation within Transcrypt follows a policy-as-code model, where access decisions are expressed as declarative rules stored in version control and enforced in real time by an open-standard engine such as Open Policy Agent. Roles, resources, and permissions are defined through explicit scopes—human-readable, reviewable, and auditable. Each request is evaluated dynamically against context: user identity, device posture, request origin, and sensitivity of the target operation. Administrative actions require step-up authentication and generate immutable audit events signed with cryptographic hashes. This design ensures that privilege escalation cannot occur silently and that every administrative pathway has a recorded lineage.

Identity management extends beyond users to encompass services, APIs, and external integrations. Every component in the ecosystem—database, queue, microservice, or third-party connector—possesses a unique, verifiable identity anchored to a cryptographic keypair. Machine identities are provisioned automatically through the same policy engine, enabling service-to-service authentication without shared secrets. Revocation, rotation, and expiry are managed programmatically, ensuring that stale credentials cannot accumulate. Together, these mechanisms form an identity fabric that unifies human and machine trust, turning authentication and authorisation into a continuous, observable control system. In Transcrypt, identity is not merely a gateway; it is the ongoing assertion that underwrites every action, every log entry, and every assurance claim.

### 7.2 Network Segmentation and Zero Trust Architecture

Transcrypt’s Network Segmentation and Zero Trust Architecture embodies the principle that no path is inherently safe—trust must be earned, not assumed. The platform’s infrastructure is divided into tightly bounded security zones, each defined by function, data sensitivity, and exposure level. Public-facing services reside in demilitarised zones with strict ingress rules, while internal APIs, databases, and build systems are isolated behind authenticated gateways. East–west traffic within the network is explicitly controlled through micro-segmentation policies enforced at the service mesh or container-network level. Every request between zones—whether human or machine—is mutually authenticated and encrypted, ensuring that even within the platform, movement is conditional and observable. This segmentation model mirrors the IEC 62443 zone-and-conduit concept, giving Transcrypt a clear lineage to industrial-grade security design.

The Zero Trust model extends beyond topology into behaviour. Each request, session, or process is continuously evaluated based on context—identity, device health, geolocation, and historical activity—before access is granted or maintained. There are no permanent trusted devices, subnets, or VPNs; only authenticated, policy-driven connections that refresh tokens and re-verify risk. This dynamic posture is implemented through an identity-aware proxy that mediates all service access, performing inline policy enforcement and telemetry capture. Compromise in one segment cannot be used to traverse laterally to another because privileges are issued on demand and discarded immediately after use.

Visibility and verification complete the model. Network events, authentication decisions, and data flows are aggregated into a unified observability stack where anomalies trigger automated correlation and response. Continuous validation tools—synthetic probes, canary requests, and policy audits—ensure that segmentation boundaries behave as intended. No network rule or trust policy is untested; each is verified as code in the CI/CD pipeline before deployment. This approach treats the network not as infrastructure but as a living security graph, constantly tested, attested, and refined. In Transcrypt, Zero Trust is not a slogan—it is the operating assumption: authenticate everything, authorise least, and verify always.

### 7.3 Data Encryption and Key Management

Transcrypt’s Data Encryption and Key Management strategy is built on the premise that data security must be provable at every state — in transit, at rest, and in use. All data flows between services, users, and storage layers are encrypted using TLS 1.3 with perfect forward secrecy, while internal service-to-service communications are mutually authenticated using short-lived certificates issued by an internal Certificate Authority (CA). At rest, all databases, backups, and object stores are protected with AES-256-GCM encryption, using unique per-tenant data keys derived from a central Key Encryption Key (KEK). Every encryption operation is deterministic in configuration but ephemeral in key material — ensuring that compromise of one component cannot reveal another’s secrets. This layered approach to cryptography forms the foundation of Transcrypt’s assurance model: confidentiality enforced by mathematics, not trust.

Key management follows a hierarchical model designed for both automation and auditability. A dedicated Key Management Service (KMS) generates, stores, and rotates master keys, with all operations logged and cryptographically verifiable. Derived keys for encryption, signing, or token issuance are created dynamically and expire automatically. Key lifecycles — creation, rotation, revocation, destruction — are defined as code within governance policies and executed through CI/CD pipelines. Secrets such as API tokens or service credentials are never stored in source code or configuration files; they are injected securely at runtime through a secrets management system such as HashiCorp Vault or a cloud-native equivalent. This approach eliminates persistent secret sprawl and ensures that all cryptographic material can be revoked or rotated without downtime.

Operationally, encryption is not treated as a background function but as an active, testable control. Regular cryptographic health checks verify algorithm strength, configuration drift, and certificate validity across environments. Penetration tests and automated scanners validate that all external endpoints enforce TLS 1.3 and strong cipher suites. Audit logs record every key operation, signed and timestamped, enabling forensic reconstruction of any event involving cryptographic material. For compliance and future-proofing, the cryptographic baseline adheres to FIPS 140-3 and NCSC guidance on cryptographic design, and the architecture is already positioned for migration to post-quantum algorithms as they stabilise. In Transcrypt, encryption and key management are not bolt-ons but embedded assurances — mechanisms that make the platform’s promise of trust verifiable in both code and cryptography.

### Key Management Model

- Each tenant possesses a unique key pair generated during on-boarding.  
- Private keys never leave the tenant’s secure vault (local device or KMS instance).  
- Transcrypt services perform encryption/decryption via tenant-approved ephemeral tokens.  
- Key rotation and revocation are fully tenant-driven.  
- Loss of keys renders data unrecoverable by design — true ownership includes responsibility.

### 7.4 Operational Resilience and Incident Response

Transcrypt’s Operational Resilience and Incident Response framework is designed around one principle: assume failure, prove recovery. The platform’s architecture is intentionally built to absorb shocks—technical, environmental, or human—without loss of integrity or evidence. Core services run in redundant clusters across multiple availability zones, with health monitoring and automatic failover orchestrated through infrastructure-as-code templates. All configuration states are versioned and reproducible, enabling rapid redeployment in the event of a catastrophic incident. Backups are encrypted, immutable, and tested weekly for restoration accuracy. This operational stance turns resilience from an abstract goal into an engineered property: the ability to maintain service continuity even when individual components fail.

Incident response is governed by a structured, time-bound playbook model. Every alert or anomaly automatically creates an incident record containing the event context, system state snapshot, and relevant logs. Severity classification triggers predefined escalation paths—technical triage, containment, eradication, and recovery—all tracked in a shared operations log. The first responder focuses on evidence preservation and containment; post-incident, a root cause analysis (RCA) is generated, peer-reviewed, and committed to version control as a permanent artefact. This ensures that lessons learned are actionable, repeatable, and auditable. Each incident closes with a measurable improvement—either a control hardening, a detection enhancement, or an updated runbook—so that the system continually evolves from experience.

To maintain assurance, Transcrypt conducts resilience testing and response rehearsals on a scheduled cadence. Tabletop exercises, fault injection, and red–blue simulations validate both technical recovery paths and human readiness. Critical scenarios—database compromise, data corruption, API overload, or AI service degradation—are simulated under controlled conditions, with metrics captured for recovery time objective (RTO) and recovery point objective (RPO). These results feed directly into quarterly governance reviews and risk reclassification. Externally, the platform commits to transparent disclosure and customer notification policies in line with NIS2 and GDPR requirements. Operational resilience is thus not just a security function but a business guarantee: a continuously verified capacity to withstand and recover from disruption without sacrificing trust, traceability, or data integrity.

### 7.5 Secure Software Supply Chain

Transcrypt’s Secure Software Supply Chain framework is engineered to guarantee that every component—from third-party library to production binary—can be traced, verified, and trusted. The platform treats software provenance as a compliance obligation, not a convenience. Every dependency, build artefact, and configuration file is accounted for through a Software Bill of Materials (SBOM) generated automatically during CI/CD. This SBOM, aligned with SPDX and CycloneDX standards, forms a cryptographically signed ledger of what enters each release. Only vetted and pinned dependencies are permitted, pulled from internal mirrors where signatures and checksums are verified before inclusion. Build environments are ephemeral and immutable: containers instantiated from read-only base images, never reused across builds, and destroyed immediately after completion. By making the build process deterministic and traceable, Transcrypt ensures that no unreviewed code or dependency can silently enter production.

At the policy level, supply chain integrity is enforced through signed commits, verified provenance, and reproducible builds. Every code contribution must originate from an authenticated developer identity with hardware-backed keys (FIDO2 or GPG). Commits are signed and verified automatically in CI, with unsigned changes rejected by policy. Dependencies are scanned for known vulnerabilities (via tools such as Trivy or Snyk) and for licence compliance before merge. The build pipeline itself is protected using principles from SLSA (Supply-chain Levels for Software Artifacts), targeting Level 3 compliance as the minimum operational standard. Each build step emits attestations—metadata that capture who built what, when, with which inputs—and these attestations are stored immutably in the artefact registry. The result is an unbroken chain of custody from source to deployment, ensuring that every component in production can be cryptographically traced back to its origin and approval.

Transcrypt also extends supply chain assurance to its operational dependencies: hosting infrastructure, AI models, and third-party APIs. External components are continuously inventoried, version-locked, and monitored for CVEs and supplier advisories. For AI systems, model provenance, training data sources, and licensing terms are catalogued with the same rigour as software packages, preventing the introduction of opaque or unlicensed components. Regular third-party reviews and internal red-team exercises validate that the pipeline and its controls remain tamper-proof and effective. In aggregate, this secure supply chain governance provides not just confidence in code integrity but demonstrable compliance with NIS2, ISO 27001, and IEC 62443 expectations for component provenance and update management. In Transcrypt’s model, trust is not implied by reputation—it is earned by signature, enforced by automation, and proven by design.


<!-- specification -->
## 8. Monetisation and Revenue Model

Transcrypt’s Monetisation and Revenue Model is designed to sustain a founder-led business that grows through credibility, not scale at any cost. The model balances accessibility for small businesses with predictability for the company, using a subscription-first approach anchored in recurring monthly revenue. The goal is to create a compounding utility product—one that earns retention through genuine operational value, not lock-in. Pricing is transparent, all-inclusive, and proportionate to the size and complexity of the customer’s organisation. No hidden consultancy, no per-seat penalties, no punitive renewal clauses. The system’s automation and clarity deliver cost efficiency at scale, allowing Transcrypt to compete effectively against both low-cost certification brokers and high-end compliance consultancies while maintaining healthy margins.

Revenue generation is phased deliberately to match the company’s maturity. In the first twelve months, the emphasis is on validation and traction—converting early adopters into paying customers and achieving the target of £500 per month profit by month twelve. As adoption grows, the subscription base becomes self-reinforcing: recurring revenue funds incremental product improvements, which in turn attract more subscribers through word-of-mouth trust. Long-term sustainability rests on progressive value: as new frameworks (NIS2, DORA, ISO 27001) and features (automated evidence mapping, partner dashboards) are added, they expand the platform’s perceived worth without fragmenting its simplicity. Each addition must raise both user value and lifetime revenue per customer while preserving affordability for SMEs.

Strategically, Transcrypt’s monetisation model is built for credibility and optionality. A core subscription service delivers continuous compliance guidance, with optional enterprise features and integrations for supply-chain partners or insurers forming natural upsell paths. Partnerships and white-label arrangements with MSPs, insurers, or professional bodies will provide parallel revenue streams that do not require mass marketing or venture funding. The model’s simplicity—clear value, low churn, low support overhead—makes it robust even at small scale. Profitability, not growth for its own sake, remains the governing metric. Transcrypt’s business design mirrors its technical ethos: lean, transparent, and verifiable. Every pound earned should represent genuine value delivered and demonstrable trust built.

### 8.1 Pricing Strategy

Transcrypt’s Pricing Strategy is intentionally simple, transparent, and grounded in the economic realities of the SME market it serves. It rejects the bloated complexity of enterprise SaaS pricing in favour of a clear value-for-money proposition that customers can understand instantly. The platform operates on a subscription model, priced to deliver affordable, ongoing compliance without the hidden costs of consultancy or renewal audits. The guiding philosophy is that every customer—whether a one-person consultancy or a 50-person manufacturer—should pay for the same capability, scaled by complexity rather than headcount. Pricing is benchmarked to undercut typical Cyber Essentials consultancy bundles by 30–40%, while offering continuous compliance alignment rather than one-off certification support. This low-friction entry point builds trust and supports organic adoption through word of mouth.

The initial focus is on reaching sustainable profitability, not rapid expansion. During the first year, pricing will remain flat and modest—targeting small businesses that need proof of compliance quickly and simply. The goal is to reach a £500 monthly profit by month twelve, a milestone that validates both product-market fit and cost discipline. Once the subscription base and operational costs stabilise, the strategy transitions to a dual objective: improving average revenue per user (ARPU) through tiered offerings and introducing optional paid features such as advanced reporting, audit support, and supply-chain mapping. Each enhancement must directly correspond to tangible customer value, ensuring that every incremental pound earned represents reduced workload or increased assurance.

Long term, the pricing model is designed to support predictable recurring revenue while maintaining accessibility. Subscription renewals will be seamless, annual discounts modest but meaningful, and all pricing published transparently on the website—no opaque quotes or “contact us” gates. The elasticity of demand in the SME compliance market favours predictability over premium, so Transcrypt will rely on volume credibility rather than margin inflation: a large base of smaller, loyal customers rather than a few high-paying clients. Periodic market reviews will adjust pricing only to reflect new features or regulatory expansions, maintaining trust through fairness. In sum, Transcrypt’s pricing strategy reflects its character: honest, lean, and customer-aligned—a product that earns payment because it proves its worth every month.

### 8.2 Subscription Tiers and Value Differentiation

Transcrypt’s Subscription Tiers and Value Differentiation are designed to scale naturally with customer maturity while keeping the onboarding experience frictionless. The entry point is the Core Plan—a single, low-cost subscription that delivers the full compliance journey for Cyber Essentials and NIS alignment. It includes the essentials: guided self-assessment, tailored risk and action reports, automated evidence tracking, and continuous updates when regulatory guidance changes. This tier is aimed at the micro and small-business segment—the backbone of the UK economy—where simplicity and affordability drive adoption. The Core Plan’s value lies in clarity: customers receive ongoing, intelligible compliance without the noise or dependency of external consultants. It establishes Transcrypt as a trusted companion rather than a one-time certificate broker.

Above this sits the Professional Plan, targeting SMEs that handle more sensitive data or operate within regulated supply chains. It builds on the Core features with advanced evidence automation, multi-user role management, and integrations with identity providers, backup systems, and insurers. This tier adds continuous assurance dashboards, showing live compliance posture across multiple frameworks (Cyber Essentials, NIS2, ISO 27001), and includes optional access to quarterly compliance reviews or AI-assisted report drafting for external auditors. The differentiation here is sophistication, not exclusivity—customers upgrade because they outgrow simplicity, not because functionality is paywalled. The pricing delta reflects measurable value: less manual effort, richer insight, and smoother stakeholder reporting.

At the top end, the Enterprise or Partner Plan is designed for MSPs, insurers, and sector bodies who want to use Transcrypt as a managed or white-labelled service for their own clients. It provides [[Post-MVP: see §9 Roadmap]] multi-tenancy controls, API access, and private branding options while maintaining the same underlying rule engine and compliance logic. This tier converts Transcrypt from a standalone platform into a compliance backbone—an engine others can trust and resell. Across all tiers, differentiation is rooted in capability depth and integration, not arbitrary restriction. Every customer, regardless of plan, receives the same data security, transparency, and quality of support. Transcrypt’s subscription structure thus mirrors its engineering ethos: modular, fair, and designed for longevity—each tier a deepening of partnership, not a barrier to entry.

### 8.3 Partner and Reseller Ecosystem

Transcrypt’s Partner and Reseller Ecosystem is a deliberate extension of its business model — a multiplier for reach, trust, and resilience. The ecosystem is built around the idea that compliance is most powerful when distributed through trusted intermediaries who already serve SMEs in adjacent domains: managed service providers (MSPs), insurers, accountants, and sector associations. These partners act as local conduits, embedding Transcrypt into their existing service portfolios to deliver continuous compliance without the need for technical expertise. For them, Transcrypt becomes a plug-in trust layer — an automated tool that enhances their own credibility and customer retention. For the platform, it becomes a cost-efficient growth mechanism that replaces traditional sales and marketing with relationship-driven distribution.

The partnership model operates on a white-label or co-branded basis, depending on the partner’s market position and customer relationship. MSPs and IT support firms can deploy Transcrypt as part of their managed security offering, using the platform’s APIs and [[Post-MVP: see §9 Roadmap]] multi-tenant dashboard to monitor client compliance at scale. Insurers can integrate it as a live assurance layer within cyber insurance policies, using compliance telemetry to adjust premiums or validate claims. Professional bodies and trade associations can offer it as a member benefit — a digital companion that simplifies certification and risk management. Transcrypt handles hosting, updates, and support centrally, while partners focus on client engagement and value delivery. This division of labour keeps operational complexity low and margins healthy for both sides.

To preserve trust and brand integrity, Transcrypt’s partner ecosystem is governed by clear participation criteria and transparent commercial terms. Revenue-sharing agreements are straightforward — a fixed percentage of each subscription sold through the partner channel, with no lock-in or exclusivity clauses. Partners receive technical onboarding, marketing collateral, and access to a sandbox environment to customise workflows and branding. A dedicated partner portal provides analytics, billing visibility, and joint-customer support tools. The ecosystem will evolve selectively, prioritising depth of relationship over volume of participants. By growing through aligned experts rather than resellers, Transcrypt maintains its reputation for clarity and credibility while multiplying its market reach — turning its partners into trusted amplifiers of both product and philosophy.

### 8.4 Licensing and Legal Terms

Transcrypt’s Licensing and Legal Terms framework is designed to be as clear and trustworthy as the product itself—written in plain English, enforceable in law, and comprehensible to non-specialists. The software is licensed on a subscription basis, granting customers the right to use the platform for the duration of their active plan, with all updates, framework mappings, and technical support included. There are no per-seat restrictions or hidden metering clauses: pricing is tied solely to organisational tier, not individual usage. All intellectual property—including the rule engine, policy mappings, and AI-assisted tooling—remains the property of Transcrypt Ltd., but customers retain full ownership of their uploaded data, evidence, and generated reports. Each account operates as a logically isolated tenant; Transcrypt acts as a processor under UK GDPR definitions, with all processing locations and sub-processors transparently listed in the Data Processing Agreement (DPA).

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
|  v1.0 | Transcrypt Core   | MVP Automation  | Full self-serve flows, no human review paths                   |
|  v1.2 | Tenant Vaults     | Security        | Client-side encryption, key management API                     |
|  v1.5 | Assisted Tier (β) | Hybrid Model    | Auditor portal, limited review API, opt-in expert verification |
|  v2.0 | Geo-sovereign Nodes | Scalability    | Regional data anchors, bring-your-own-KMS option               |

Transcrypt’s Roadmap and Delivery Strategy is structured around disciplined iteration: a lean, verifiable path from concept to commercial traction. The strategy reflects a core principle—deliver small, prove value, refine fast. It prioritises the creation of a Minimum Viable Product (MVP) that demonstrates functional credibility and real customer benefit within the first six months, followed by incremental expansions that compound capability rather than complexity. Each phase is defined by a measurable outcome: working software, validated user engagement, and sustainable revenue growth. The emphasis is on building a product that earns trust early, through demonstrable competence and transparency, rather than pursuing scale prematurely.

Delivery is paced deliberately to balance speed with quality. Every milestone is gated by functional completeness and security assurance rather than arbitrary dates. Each release passes through structured acceptance tests—deterministic, documented, and reproducible. Technical progress is managed through a version-controlled development workflow, where all commits, merges, and releases are traceable to defined requirements. The delivery strategy integrates continuous integration and deployment (CI/CD) pipelines from the outset, ensuring that development and compliance are inseparable. In parallel, user testing and feedback loops are embedded into every iteration, capturing behavioural insights that directly inform prioritisation. This approach ensures that Transcrypt evolves with empirical direction, not guesswork.

The roadmap also recognises the constraints and advantages of a founder-led, low-burn operation. Budgets are lean, decisions fast, and infrastructure choices pragmatic. Work is sequenced to avoid technical debt and to reach early self-sustainability, with the initial financial target—£500 monthly profit by month twelve—serving as both proof of viability and validation of market resonance. Partnerships and open collaboration are used to amplify output without expanding payroll: freelance design, modular development contracts, and infrastructure credits substitute for headcount. In total, Transcrypt’s roadmap balances realism and ambition: rapid enough to stay relevant, cautious enough to stay solvent, and methodical enough to create a platform whose quality and credibility become its own form of marketing.

### 9.1 MVP Definition

Transcrypt’s Minimum Viable Product (MVP) is defined not by feature volume but by demonstrable value: the ability to take a small business’s inputs, interpret them intelligently, and return a meaningful, tailored compliance report. The MVP must prove that a single founder can operate and monetise the system end-to-end — from customer intake through to payment and delivery — without external dependencies. Functionally, it consists of three pillars: a clean intake workflow, a rule evaluation engine, and a report generator. The intake captures company profile and control evidence through guided questions. The rule engine — powered by deterministic logic with LLM-assisted interpretation at build time — maps those responses to a set of Cyber Essentials and baseline NIS controls. The report generator returns a clear, actionable summary showing compliance status, gaps, and recommended steps. This is not a prototype; it is the simplest form of the final product, capable of earning revenue from day one.

The MVP must deliver a “one sitting” outcome — a business owner can sign up, complete their intake, and receive a usable compliance assessment within an hour. Automation replaces human consulting, yet the tone and accuracy must equal that of a skilled professional. Output will include a branded, downloadable PDF with executive summary, detailed control mapping, and a prioritised action plan. Data persistence, authentication, and payment collection will be lightweight but production-grade: a managed Postgres database, an OAuth-based login, and Stripe integration for subscriptions. Evidence upload and storage will use secure object storage with file hashing for integrity verification. Each of these features directly underpins monetisation, credibility, and compliance, avoiding any “demo-only” components that would later need to be rewritten.

Success criteria for the MVP are clear and measurable. First, functional validation — a minimum of five real users completing the workflow and receiving reports without manual intervention. Second, performance validation — a complete intake and report cycle in under ten minutes of processing time. Third, economic validation — at least three paying customers and a positive monthly margin. Beyond these metrics, qualitative success is defined by trust: users describing the platform as simple, accurate, and worth paying for. This first iteration forms the commercial and technical nucleus of Transcrypt — a credible, automated compliance companion that proves the concept, pays for its own evolution, and establishes the data and design foundations for all future features.

### 9.2 Phase Milestones and Timelines

Transcrypt’s Phase Milestones and Timelines are structured across a 12-month horizon, divided into four disciplined phases: Foundation, Validation, Expansion, and Stabilisation. Each phase culminates in a tangible, auditable outcome that advances the product’s maturity and commercial footing. The sequencing reflects a single-founder cadence—tight scope, minimal dependency, and cumulative progress—so that each success builds directly on the last. The overarching goal is to evolve from working prototype to profitable, trusted platform within one year, reaching sustained £500 monthly profit by month twelve as the baseline measure of viability.

Phase 1: Foundation (Months 1–3) establishes the core architecture and essential functionality. This includes development of the intake workflow, initial rule engine (Cyber Essentials controls only), basic report generator, and a minimal but secure cloud deployment. Authentication, storage, and CI/CD pipelines are implemented early to prevent technical debt. A soft alpha release with a handful of test users verifies that the compliance logic, data handling, and automation pipeline function as intended. The milestone for this phase is a closed-beta MVP capable of generating accurate reports end-to-end.

Phase 2: Validation (Months 4–6) focuses on real-world proof. Live onboarding of five to ten SME users provides usage data, feedback, and early revenue. Product refinement follows quickly—interface improvements, AI-assisted language clarity in reports, and the first partner trial (an MSP or insurer). The milestone is operational validation: at least three paying customers and one partner pilot, confirming commercial appetite and trust.

Phase 3: Expansion (Months 7–9) broadens scope and deepens capability. The rule engine is extended to include NIS2 alignment, the evidence management module is added, and the first premium “Professional” tier is introduced. Marketing begins through partner channels and case-study storytelling. The milestone: revenue consistency across a month and a proven upgrade path from Core to Professional tier.

Phase 4: Stabilisation (Months 10–12) consolidates reliability and prepares for formal certification (Cyber Essentials Plus). Key focuses include performance tuning, documentation, automated testing coverage, and incident-response rehearsals. The milestone is dual: technical stability (99.9% uptime) and financial validation (sustained profit for two consecutive months). Each phase produces a tagged release, a short post-mortem, and an updated backlog—ensuring that delivery remains evidence-driven, iterative, and fully traceable from inception to commercial maturity.

### 9.3 Resource and Budget Planning

Transcrypt’s Resource and Budget Planning framework is built on lean engineering discipline — the philosophy that constraints drive clarity. As a single-founder venture, resources are allocated with surgical precision to maximise impact per pound. The goal is to prove sustainability before scale: every expense must either accelerate product delivery, enhance credibility, or directly support paying users. The total cash outlay during the first 12 months is intentionally modest, targeting £2,500–£3,000 in total operating spend, excluding the founder’s time. This covers cloud hosting, development tooling, domain and licensing fees, and small discretionary marketing outlay. Infrastructure costs are controlled through reserved credits and usage-based scaling, ensuring that monthly operating costs remain below £100 until profitability. The founder provides engineering, product, and compliance expertise in-house, reducing external dependency to near zero during the first year.

Human resources follow a concentric model. The inner ring consists of the founder’s core engineering and architecture work, supported occasionally by freelance specialists for discrete deliverables—UX design, content editing, and security review—engaged on fixed-price contracts. The second ring comprises strategic collaborators and early partners (e.g., MSPs, insurers, or compliance auditors) who participate in testing and feedback rather than payroll. The outer ring—eventual hires or retained contractors—is deferred until recurring revenue comfortably exceeds operating costs. This model keeps the organisation flat, capital-efficient, and adaptive while enabling expertise injection precisely when needed. All coordination occurs within a lightweight toolchain: GitHub for source control and issues, Trello or Linear for backlog management, and shared documentation through Notion or Markdown repositories.

Budget allocation mirrors this simplicity. Approximately 40% of the initial budget is assigned to cloud infrastructure (DigitalOcean or comparable provider with storage and compute scaling), 30% to professional and legal services (terms of service drafting, insurance, accounting), 20% to content and design polish for launch, and 10% to discretionary marketing and testing incentives. Capital expenditure is avoided entirely—no office space, servers, or permanent staff until profitability. Financial monitoring uses basic but effective metrics: burn rate, monthly recurring revenue, and cash runway, each tracked against a rolling 90-day forecast. Every pound spent must reduce uncertainty or increase revenue potential. In effect, the resource plan is a live experiment in disciplined entrepreneurship—building a serious product within self-imposed limits that enforce both creative focus and long-term viability.

### 9.4 Risk Register and Mitigation

Transcrypt’s Risk Register and Mitigation framework is the operational embodiment of its engineering philosophy: every risk is documented, measurable, and actionable. The register is maintained as a version-controlled artifact, reviewed quarterly, and categorised across four dimensions—technical, operational, financial, and strategic. Each entry defines the risk description, likelihood, potential impact, owner, and mitigation strategy, with real-time updates whenever control effectiveness changes. Risks are ranked on a five-point scale for probability and severity, producing a live heat map that feeds directly into roadmap prioritisation. This approach ensures that mitigation is not reactive or bureaucratic but built into the product’s evolution: risks drive sprints, tests, and design improvements, not afterthoughts or excuses.

Technical risks centre on platform security, AI reliability, and infrastructure integrity. Mitigations include defence-in-depth architecture, automated testing, regular dependency audits, and isolation of AI components from production decision paths. Security posture is verified continuously through penetration tests and red–blue exercises, while cryptographic controls (encryption, signed builds, SBOMs) minimise the blast radius of compromise. Operational risks—such as cloud service disruption or key-person dependency—are reduced through infrastructure-as-code deployments, daily backups, and documented recovery workflows. Critical configurations are mirrored across availability zones, and a part-time external security consultant will periodically validate operational readiness to provide external assurance.

Financial and strategic risks revolve around cash flow volatility, customer acquisition pace, and competitive pressure. These are mitigated through a deliberately low burn rate, revenue diversification via partnerships, and maintaining full intellectual property ownership. Pricing agility ensures the ability to adjust quickly to market conditions without alienating early adopters. Reputational risk—central to a trust-based product—is addressed by embedding transparency into every process: changelogs, incident disclosures, and code provenance are publicly verifiable. Finally, a small number of regulatory risks—such as interpretation errors in compliance frameworks—are managed through continuous dialogue with advisors and the use of verifiable legislative sources. In essence, Transcrypt’s risk register doubles as a design compass: a living record of what could go wrong and the systematic measures ensuring it rarely does, and never without leaving a clear audit trail.

### 9.5 Quality Assurance and Acceptance Criteria

Transcrypt’s Quality Assurance and Acceptance Criteria are designed to ensure that every release—no matter how small—meets the same standards of precision, stability, and integrity that define its compliance ethos. Quality is not treated as a final gate but as a continuous state, achieved through automation, version control, and human review. The QA framework spans the entire lifecycle: requirement definition, code implementation, testing, deployment, and post-release validation. Every requirement is expressed as a verifiable condition—“what done looks like”—and mapped to acceptance tests that run automatically within the CI/CD pipeline. This deterministic approach ensures that compliance, security, and functionality are tested in one integrated process, not as separate afterthoughts. No feature can be released unless it satisfies its acceptance criteria, passes all regression and security tests, and generates reproducible results in staging.

The testing framework combines static and dynamic validation. Unit tests verify logic consistency in the rule engine and evidence mapping; integration tests confirm that authentication, API, and report generation components behave correctly across boundaries. End-to-end tests simulate real customer workflows—from intake to report delivery—executed through scripted environments to ensure predictable behaviour under load. Automated security scans, dependency vulnerability checks, and licence audits run on every build, with failures blocking deployment until resolved. For AI-assisted components, deterministic outputs are compared against stored “golden files” to prevent drift or hallucination. Every build produces a signed test report artifact stored in the project’s audit ledger, creating permanent evidence of compliance with the defined acceptance criteria.

Acceptance criteria themselves follow a simple triad: functional, security, and user validation. Functionally, the product must deliver accurate and complete results under defined inputs; security-wise, all data must remain encrypted, access-controlled, and free from known vulnerabilities; from a user perspective, the experience must remain clear, intuitive, and error-free within a standard use session. Releases are not accepted by date but by evidence—passing tests, verified results, and documented peer review. Post-release telemetry further validates performance, latency, and reliability against service-level targets (e.g., 99.9% uptime, sub-second API response). Any regression automatically reopens its related requirement for correction, closing the loop between QA and roadmap. This framework turns assurance into a living discipline: every accepted release is not only functional but provably compliant with the same rigour Transcrypt will one day automate for its customers.


<!-- strategic -->
## 10. Future Outlook and Strategic Extensions

Transcrypt’s Future Outlook and Strategic Extensions represent the natural evolution of a platform designed from the start to be adaptive — technically, commercially, and ethically. The product’s immediate purpose is to simplify UK SME compliance, but its architecture and data model are intentionally global and extensible. By structuring every rule, evidence item, and report output as interoperable objects, Transcrypt can evolve into a multi-framework, multi-jurisdictional compliance fabric — one that adjusts automatically as new regulations appear or existing ones converge. The long-term strategy is to make compliance continuous, contextual, and border-agnostic: a layer of digital assurance that translates government language into operational reality for businesses of any size.

This forward trajectory rests on measured innovation, not speculation. As AI and automation mature, Transcrypt will expand beyond reactive compliance to predictive governance — identifying emerging risks and recommending pre-emptive controls before regulators demand them. The same mechanisms that interpret rule logic today can later benchmark security posture, simulate audit scenarios, and even validate controls in real time against live telemetry feeds. In parallel, the platform’s foundation in applied cryptography and transparency positions it to integrate with distributed trust infrastructures — from verifiable credentials to [[Post-MVP: see §9 Roadmap]] blockchain-backed attestations — where compliance proofs can be shared securely across supply chains. The future product family thus grows not by bolt-on features but by deepening its capacity to measure, verify, and explain trust.

Strategically, Transcrypt’s outlook is pragmatic and sustainable. Expansion will follow credibility, not hype: first consolidating UK market dominance, then extending into EU, Commonwealth, and allied jurisdictions where data sovereignty and trust frameworks align. Each geographic expansion will be accompanied by localised regulatory mapping, native-language interfaces, and partnership with in-country experts. The company’s structure will remain lean and founder-led, scaling through partnerships, licensing, and white-label channels rather than capital-intensive hiring. Every strategic extension must meet three conditions — technical feasibility, ethical defensibility, and customer relevance. In short, the outlook is neither utopian nor defensive: Transcrypt’s future lies in making regulatory complexity not just manageable but measurable, turning compliance from a burden into a continuous competitive advantage.

### 10.1 Interoperability with Other National Frameworks

Transcrypt’s Interoperability with Other National Frameworks is a core strategic enabler — the bridge between a UK-born compliance engine and a globally adaptable assurance platform. From inception, the system has been designed around framework abstraction, meaning each control, rule, and evidence object exists independently of jurisdiction. A rule in Cyber Essentials (“MFA for administrative accounts”) can map directly to equivalent clauses in NIST 800-53, CIS Controls, or ISO 27001 Annex A, with metadata defining its origin, scope, and equivalence relationships. This architecture allows the same intake and evaluation pipeline to be repurposed for other countries simply by swapping in new framework definitions and legislative mappings, without altering the core logic. The result is a platform that can grow horizontally — serving Canada, Australia, the EU, and beyond — through data, not code.

Operationally, interoperability will begin with regulatory clusters, starting with the EU (NIS2, DORA, GDPR) and the Commonwealth markets that share similar legal and risk management philosophies. Frameworks are imported as structured data packs, each containing control definitions, reference citations, and evidence schemas. A translation layer aligns terminology and severity across frameworks, so that a UK client expanding into the EU can reuse 80–90% of their existing compliance data automatically. This approach doesn’t just enable new markets; it simplifies cross-border certification for businesses operating under multiple regimes. Over time, Transcrypt could offer “compliance compilers” — automatically generated gap analyses showing which controls are satisfied globally and where local divergence remains.

Technically, interoperability is achieved through open schemas and exportable assurance data. All framework definitions, evidence mappings, and reports can be expressed in standardised formats such as JSON-LD or XDR (eXtensible Data Representation), allowing easy exchange with regulators, auditors, and partner platforms. The platform’s REST and GraphQL APIs will support both import and export of compliance data, positioning Transcrypt as the connective tissue between regional ecosystems. Future integrations may include direct alignment with machine-readable legislation repositories and government trust frameworks. By designing for portability from the outset, Transcrypt becomes not merely a UK compliance tool but a universal translator for digital assurance — one capable of understanding and contextualising trust wherever it’s defined.

### 10.2 Research and Development Themes

Transcrypt’s Research and Development Themes define how the platform will evolve intellectually as well as technically — ensuring it stays not just current, but pioneering in its understanding of digital assurance. The guiding principle is that compliance, security, and automation are converging disciplines, and innovation must serve the long game: reducing human toil while increasing verifiability. Research therefore focuses on four intersecting threads — explainable automation, dynamic assurance, applied cryptography, and policy intelligence. Each thread deepens the system’s ability to reason about risk, interpret regulation in context, and prove trust through evidence.

The first major R&D theme is explainable automation, developing methods for making AI-assisted compliance interpretable and defensible. Transcrypt will continue to use deterministic rule evaluation as its foundation, but future models will explore hybrid architectures where machine learning assists in evidence classification, text interpretation, and anomaly detection — all under transparent, auditable logic. Research into natural-language grounding and rule extraction from legislative texts will enable the platform to ingest and structure new regulations automatically. This moves compliance from a manual curation task to a semi-autonomous function that keeps pace with the law.

The second thread, dynamic assurance, aims to transform compliance from static reports into continuous measurement. Future iterations will integrate telemetry from security tooling, cloud configurations, and identity providers, translating real-time signals into live compliance posture updates. Complementary research in applied cryptography will investigate ways to make those attestations verifiable through decentralised proofs, using techniques such as zero-knowledge attestations, Merkle-signed audit trails, and verifiable credentials. The fourth R&D theme, policy intelligence, focuses on pattern discovery across anonymised customer data — identifying systemic weaknesses in SME security postures and feeding them back into the platform’s guidance engine. Collectively, these themes point toward a future where Transcrypt functions as more than a compliance tool — it becomes a living observatory of cyber health, translating raw operational reality into policy insight and regulatory foresight.

### 10.3 Potential Spin-offs and Product Lines

Transcrypt’s Potential Spin-offs and Product Lines represent the natural diversification of a platform that treats compliance data as structured intelligence rather than static paperwork. Once the core engine—rule evaluation, evidence management, and reporting—is established, the same architecture can underpin several adjacent products, each serving a different slice of the trust ecosystem. These extensions allow the company to grow laterally without bloating the core offering, reusing the same underlying data model, and differentiating primarily through interface, integration, and market positioning. The overarching principle is reuse of logic, repackaging of value: one compliance brain, many specialised expressions.

The most immediate spin-off opportunity is Transcrypt for Insurers—a live assurance companion that feeds compliance posture directly into cyber-insurance risk models. SMEs using the base platform could opt-in to share continuous assurance data with underwriters, enabling dynamic premium pricing and faster claims validation. Parallel to this sits Transcrypt Partner Hub, a white-label version for MSPs and auditors who need [[Post-MVP: see §9 Roadmap]] multi-tenant dashboards to manage client compliance portfolios. Over time, a Transcrypt Lite edition could target micro-enterprises and sole traders, offering a guided “compliance in an afternoon” experience with simplified evidence requirements and automated report generation—a low-touch, high-volume product optimised for direct self-service sales.

Longer-term product diversification looks outward to the data economy. A TrustGraph API could expose anonymised, aggregated compliance trends to research institutions, insurers, and policy analysts, creating a data-as-a-service stream that helps quantify SME cyber-maturity across sectors and regions. Another trajectory leads into Transcrypt Verify, a credentials and attestation product that allows suppliers to issue digitally signed proof of compliance—verifiable by customers or regulators without revealing proprietary data. Finally, a developer-facing SDK would let third-party platforms embed Transcrypt’s rule-evaluation logic into their own ecosystems, expanding reach without operational overhead. Each spin-off reinforces the core mission: converting compliance from an administrative burden into an ecosystem of living, portable trust signals.

### 10.4 Long-Term Sustainability and Ethical Charter

Transcrypt’s Long-Term Sustainability and Ethical Charter defines the principles by which it intends to endure—not just financially, but socially and technologically. The platform is built to outlast hype cycles by adhering to three durable commitments: pragmatism, transparency, and proportionality. Pragmatism governs its business model—profitable at small scale, restrained in expenditure, and growing only as utility and reputation justify it. Transparency governs its technology—open schemas, traceable AI decisions, auditable code, and verifiable change histories. Proportionality governs its ethics—automation used to clarify and empower, not to obfuscate or replace human judgement. The charter formalises these as binding operational tenets: Transcrypt will always make its decisions explainable, its data ownership unambiguous, and its use of automation accountable.

Environmental and social sustainability form the second axis of the charter. As a digital-first company with a light physical footprint, Transcrypt’s environmental policy focuses on energy efficiency and responsible compute. Cloud workloads are geographically located to maximise renewable energy use, and model training is minimised through reuse of pre-trained architectures and inference-efficient design. Data retention policies are conservative—storing only what is necessary and deleting when legal or operational value expires. Socially, the company commits to accessibility and inclusion: interfaces readable by non-specialists, content available in plain English (and later, multilingual form), and pricing that keeps compliance attainable for small organisations. Compliance itself becomes a democratizing act—the levelling of security literacy across economic tiers.

Ethically, Transcrypt recognises that the power of automation in compliance must be balanced by human interpretability and moral restraint. The Ethical Charter codifies this balance through explicit prohibitions: no use of AI for deceptive content generation, dark-pattern onboarding, or data resale. AI-generated outputs must always be traceable, reviewable, and reversible. Transparency about model limitations is mandatory; users are told where AI ends and logic begins. Governance of the charter itself is participatory—reviewed annually with input from users, partners, and advisors, and published openly with tracked revisions. In this way, sustainability and ethics are not appendices to the business—they are its scaffolding. Transcrypt’s long-term vision is to be trusted not because it claims virtue, but because its architecture and operations make virtue measurable.

### 10.5 Closing Summary

Transcrypt exists to make compliance intelligible, provable, and continuous for small and mid-sized businesses. The platform converts legislation and frameworks into structured rules, guides users through clear actions, and links every claim to evidence. The result is not a certificate factory but an operating companion: a steady, comprehensible path from obligation to assurance.

The market is noisy and polarised. On one side are low-cost portals that stop at form-filling; on the other, heavyweight GRC suites that few SMEs can afford or run. Transcrypt sits in the missing middle. It interprets rather than obscures, automates without theatrics, and speaks in plain English. Brand credibility comes from quiet competence and transparent mappings, not jargon or fear.

Architecturally, the system is built for trust. Identity is first-class, data is encrypted by default, builds are signed, and every control is testable. Policies live as versioned objects, evidence is anchored to those objects, and changes are traceable. Security, resilience, and supply-chain integrity are not appendices; they are the substrate that lets auditors, partners, and customers accept the output without squinting.

Commercially, the plan is pragmatic. A single founder can deliver an MVP that earns revenue on day one: intake, rule evaluation, and a usable report. Year one is about validation and discipline, not scale. The financial target is simple and explicit: reach a clean £500 monthly profit by month twelve by keeping costs lean and value obvious. Growth follows credibility, then partnerships, not ad spend.

Roadmap execution is iterative and test-led. Each release is gated by acceptance criteria that combine function, security, and user clarity. Evidence of quality is produced as a routine by-product of development. When incidents occur, they leave an audit trail and a permanent improvement. That is how a small company builds large trust.

Strategically, Transcrypt is designed to travel. The rule engine treats frameworks as data, so expansion to NIS2, DORA, and other jurisdictions is translation work, not reinvention. Over time, the same machinery can power insurer attestations, partner dashboards, and verifiable credentials that move along supply chains without exposing raw data.

The ethical stance is explicit: clarity over theatre, proportionality over bloat, and transparency over dark patterns. Users own their data. AI is assistive and explainable. Legal terms are readable. The company remains small, solvent, and accountable.

In short, Transcrypt turns compliance from an annual scramble into a steady state. It lowers the cognitive load, raises the evidential bar, and earns trust by design. Ship the MVP, prove the loop, compound the value.


### Cross-Reference Conventions

To maintain coherence between strategy and specification:

- **(S)** → refers to a strategic concept or intent.
- **(T)** → refers to a technical requirement or implementation detail.
- When both are relevant, use **(S/T)**.

Example: “Automation ensures consistent SME outcomes (S/T).”

## Appendices
### A. Terminology and Abbreviations

**Verifiable Transparency** — A principle where a closed-source system provides mathematically verifiable evidence of integrity (hashes, signatures, deterministic logs) in place of source disclosure.

**Compliance Pack** — A signed configuration bundle defining a specific regulation or framework (controls, scoring logic, mappings, labels).
Enables multi-framework operation without code changes.

**Centrally Orchestrated, Locally Encrypted SaaS** — A deployment pattern where a central service handles coordination and updates but cannot read tenant data because all content is encrypted with tenant-held keys.

### B. Reference Documents
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

**Pricing model**: CyberSmart is sold as a SaaS subscription, priced by company size (number of devices/users). It’s very SME-friendly: starting at around £49 per month [for small organizations](https://www.capterra.co.uk/software/203257/cybersmart#:~:text=Local%20product), with tiers scaling upward for larger user counts (e.g. ~£90/month for 1–9 users in a bundle that includes CE certification and the [Active Protect](https://assets.applytosupply.digitalmarketplace.service.gov.uk/g-cloud-13/documents/707477/951169144457475-pricing-document-2022-05-17-1347.pdf#:~:text=2%20CyberSmart%20CyberSmart%20is%20the,finding%20and%20implementing%20a%20solution) monitoring [service](https://assets.applytosupply.digitalmarketplace.service.gov.uk/g-cloud-13/documents/707477/951169144457475-pricing-document-2022-05-17-1347.pdf#:~:text=,4)). This low entry price makes it affordable for micro and small businesses. (The Cyber Essentials certification fee itself is included in such bundles, which is notable since a basic CE assessment alone typically costs ~£300+VAT for micro companies via [IASME](https://iasme.co.uk/cyber-essentials/frequently-asked-questions/#:~:text=Frequently%20Asked%20Questions%20).)

**Market share and usage**: CyberSmart has gained significant traction in the UK SME market – as of early 2023 it was reported to be protecting [over 4,000 small businesses in the UK](https://www.iqcapital.vc/news/cybersmart-raises-15m-for-an-all-in-one-cybersecurity-and-insurance-solution-targeting-smbs-2#:~:text=regardless%20%E2%80%94%20has%20closed%20a,4%20million). Many of these are at the 10–50 employee size. The company has also partnered with managed service providers (MSPs) and [insurance firms to reach more customers](https://www.iqcapital.vc/news/cybersmart-raises-15m-for-an-all-in-one-cybersecurity-and-insurance-solution-targeting-smbs-2#:~:text=CyberSmart%20currently%20has%204%2C000%20customers,home%20market%20as%20well%20as), indicating a strategy of [scaling through channels](https://www.iqcapital.vc/news/cybersmart-raises-15m-for-an-all-in-one-cybersecurity-and-insurance-solution-targeting-smbs-2#:~:text=called%20in%20the%20U,security%20piece%20of%20that%20offering). With a Series B funding in 2023, CyberSmart is expanding internationally, but the UK remains its core market. [Given ~51,000 total Cyber Essentials certificates were issued in the year to mid-2025](https://www.gov.uk/government/statistical-data-sets/cyber-essentials-management-information#:~:text=Certificates%20awarded%20under%20the%20scheme,are%20valid%20for%2012%20months), CyberSmart’s user base suggests a substantial share of SMEs are opting for its platform (either directly or via consultants) to achieve and maintain certification.

**Key differentiators**: Simplicity and specialization for Cyber Essentials. CyberSmart combines an easy app (no prior security expertise needed) with compliance-as-a-service. [It continuously monitors compliance post-certification to ensure the SME stays secure](https://www.capterra.co.uk/software/203257/cybersmart#:~:text=Born%20in%202017%20from%20a,our%20mobile%20and%20desktop%20apps). This ongoing aspect plus included insurance set it apart from one-off consulting. In essence, CyberSmart is positioned as an affordable “compliance on autopilot” tool for UK small businesses.

##### Drata (US) – Automated GRC Platform with UK Framework Support

**Drata** is a well-known U.S.-based **security compliance automation platform** that expanded into the UK market. It started by automating frameworks like SOC 2 and ISO 27001 for cloud startups, and in September 2023 Drata **added support for the UK Cyber Essentials** [scheme](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=LONDON%2C%20Sept,Plus%2C%20which%20requires%20independent%20verification). This means Drata’s platform now has built-in mappings and controls for CE’s requirements, allowing UK companies to use Drata to prepare for certification. Drata provides **continuous control monitoring, automated evidence collection, policy templates, and an auditor collaboration** [portal](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=Features%20of%20Drata%27s%20Cyber%20Essentials,launch%20include) – essentially replacing spreadsheets and reducing the manual workload of compliance. Notably, it can **monitor compliance with CE controls on an ongoing basis** (e.g. checking that patching is up to date, passwords meet criteria, etc.), which helps ensure the organization [remains compliant year-round](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=Features%20of%20Drata%27s%20Cyber%20Essentials,launch%20include). For the more advanced **Cyber Essentials Plus**, Drata offers guidance but that level still requires an independent [audit outside the tool](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=LONDON%2C%20Sept,Plus%2C%20which%20requires%20independent%20verification).

**Pricing model**: Drata is offered as an annual SaaS subscription, typically priced based on the number of employees and which compliance frameworks are needed. Exact pricing isn’t public (quotes are custom), but it is generally at a higher price point than basic tools – more in line with the value of saving auditor time and combining multiple compliance standards. Many tech SMEs report Drata (and similar rivals) often start in the **low five-figure** range annually for a small company, covering a couple of frameworks. Drata emphasizes the ROI by claiming **automation saves time and costs** (e.g. avoiding the need for dedicated compliance staff or costly audit prep). If a company already uses Drata for ISO 27001 or SOC2, adding Cyber Essentials is streamlined, since Drata will **cross-map overlapping controls so no duplicate effort** [is needed](https://www.vanta.com/products/cyber-essentials#:~:text=Image%3A%20No%20duplicate%20efforts). 


**Market presence**: Drata has grown rapidly worldwide – by late 2023 it served “**thousands of customers** [across 50 countries](https://www.prnewswire.com/news-releases/drata-launches-support-for-cyber-essentials-301918630.html#:~:text=real)”. Its client base tends to be tech-oriented SMEs (e.g. software companies) and mid-market firms who need multiple certifications. In the UK, Drata’s formal launch of Cyber Essentials support and an expanding EMEA team indicate a push into the UK/EU region. Given its strong funding and recognition (often named alongside Vanta as a leader in automated compliance), Drata is becoming a significant competitor for any UK company considering an all-in-one compliance platform rather than local point solutions. 

**Competitors**: Drata’s main competitors in this space are **Vanta, Secureframe, and Hyperproof** – among these, **Vanta** has also targeted UK compliance specifically (see below). Compared to some UK-specific solutions, Drata is more comprehensive (covering dozens of frameworks) but might be more than what a micro-business strictly needs for just Cyber Essentials. It shines for SMEs that anticipate needing international standards (ISO, SOC2, GDPR, etc.) in addition to UK-specific ones.

##### Vanta (US) – Expanding into UK Standards (Cyber Essentials, NIS2)

**Vanta** is another leading compliance automation vendor from the U.S., very similar in concept to Drata. Notably, Vanta has made a strong entry into the UK market by announcing support for **UK Cyber Essentials and CE Plus** requirements. In fact, Vanta’s website touts itself as “**the fastest way to achieve UK Cyber Essentials compliance,**” automating up to **70% of the work** via built-in [controls](https://www.vanta.com/products/cyber-essentials#:~:text=The%20fastest%20way%20to%20achieve,UK%20Cyber%20Essentials%20compliance) and [monitoring](https://www.vanta.com/products/cyber-essentials#:~:text=Time). Like Drata, Vanta connects with a company’s systems (cloud platforms, device management, etc.) to continuously check security settings against the required standards. It provides **integration-driven checks, auto-generated policies, and test evidence** to [simplify passing an audit](https://www.vanta.com/products/cyber-essentials#:~:text=Time). Vanta also highlights that if an organization is already compliant with another framework (say ISO 27001 or SOC 2), it will **automatically map those controls to Cyber Essentials**, [avoiding duplicated work](https://www.vanta.com/products/cyber-essentials#:~:text=No%20duplicated%20efforts). This is useful for SMEs that expand their compliance obligations over time. 

**Pricing model**: Vanta’s pricing is also annual SaaS, generally tied to employee count (since they monitor endpoints and accounts). While not public, it typically has tiered packages (e.g. for startups vs mid-market). Reviews indicate Vanta’s cost is comparable to Drata. For a small business focusing only on CE, Vanta’s offering may be more expensive than a local UK-only solution like CyberSmart, but the value is in covering multiple frameworks in one platform. Vanta often markets heavily to startups by emphasizing scalability – as a company grows, they can add on more standards in Vanta’s interface (the platform supports **25+ frameworks** [including](https://www.vanta.com/products/cyber-essentials#:~:text=frameworks) SOC 2, ISO, **NIS2**, GDPR, [etc. as of 2025](https://www.vanta.com/products/cyber-essentials#:~:text=SOC%202%20%2014GDPR%20,30Custom%20frameworks%20%2032)). 

**Market presence**: Vanta claims to have **thousands of customers** [globally as well](https://www.vanta.com/customers#:~:text=Customer%20Success%20Stories%20,Read%20their%20success%20stories). It’s especially popular among cloud-native companies and has been expanding in Europe (they have an EU data center to accommodate GDPR concerns). While exact UK customer counts aren’t disclosed, Vanta’s inclusion of Cyber Essentials and NIS2 indicates a strategic focus on European markets. [The company has substantial funding (unicorn valuation) and has been recognized in the 2025 Forbes Cloud 100](https://www.businesswire.com/news/home/20250903830360/en/Vanta-Named-to-the-2025-Forbes-Cloud-100-for-Third-Consecutive-Year#:~:text=Vanta%20Named%20to%20the%202025,2025%20Cloud%20100%20list%2C), signaling strong momentum. We can expect Vanta to be in direct competition with Drata for any UK SME that might need a multi-framework compliance automation solution.

##### DataGuard (Germany/UK) – “Compliance-as-a-Service” with Human Expertise

capterra.com
**DataGuard** [is a European provider](https://www.capterra.com/p/219584/DataGuard/#:~:text=Achieve%20your%20security%20and%20compliance,security%20and%20compliance%20objectives%20with) (headquartered in Germany, with a London office) that takes a hybrid approach: **an all-in-one compliance platform coupled with expert consulting support**. This “compliance-as-a-service” model is designed for SMEs that want to outsource much of the complexity. DataGuard’s platform covers a wide range of frameworks – **from ISO 27001 and GDPR to NIS2, SOC 2, TISAX, and even the** [EU Whistleblowing Directive](https://www.capterra.com/p/219584/DataGuard/#:~:text=Achieve%20your%20security%20and%20compliance,security%20and%20compliance%20objectives%20with). It offers modules for information security management (ISMS), data privacy management, vendor risk, etc., all integrated. A key feature is its **iterative risk management** dashboard where companies can document assets, risks, and controls, and track improvements. DataGuard automates evidence collection and control monitoring to ensure continuous compliance ([they claim to cut manual effort by ~40% and speed up certifications by 75%](https://www.capterra.com/p/219584/DataGuard/#:~:text=Achieve%20your%20security%20and%20compliance,tracking%20certification%20by%2075%25.%20Join)). In parallel, each client gets access to DataGuard’s in-house consultants and subject matter experts for guidance – effectively **augmenting the software with on-demand advisory.** 

**Pricing model**: DataGuard is sold in **fixed-price packages** [tailored to the company’s needs](https://www.g2.com/products/dataguard/pricing#:~:text=DataGuard%20Pricing%202025%20Our%20pricing,fit%20your%20company%27s%20compliance%20needs). They emphasize transparent pricing, though actual figures aren’t publicly listed as a simple price sheet. In practice, many DataGuard customers pay an annual subscription in the **low-to-mid five figures** (GBP) which includes the software platform and a set amount of consultation hours or support services. For example, a package might include the ISMS software plus help from a named consultant to achieve ISO 27001 certification over several months. This can be cost-effective compared to [hiring a full-time compliance officer or engaging a big law firm](https://www.dataguard.com/compliance-as-a-service#:~:text=). DataGuard often positions itself as giving “the best of both worlds – [specialist advice plus time-saving technology](https://www.dataguard.com/compliance-as-a-service#:~:text=The%20price%20of%20compliance%20is,saving%20technology)”. 

**Market presence**: DataGuard has grown quickly with this model; as of 2023 they reported **4,000+ companies** [using their platform](https://www.capterra.com/p/219584/DataGuard/#:~:text=scales.%20The%20platform%20combines%20AI,content%20shown%20on%20DataGuard%27s%20website). Initially many clients were using DataGuard for GDPR/data protection compliance (they launched in 2017 in the wake of GDPR). Now they have expanded their security offerings, and notably they’ve been marketing NIS2 compliance solutions in 2024-2025 as that [becomes a hot topic in Europe](https://www.capterra.com/p/219584/DataGuard/#:~:text=Achieve%20your%20security%20and%20compliance,security%20and%20compliance%20objectives%20with). In the UK, DataGuard’s customer base includes lots of SMEs and mid-market firms that lack internal compliance teams. Their partnership with investors like British Patient Capital (UK government’s fund) also raised their profile. While DataGuard competes with pure software platforms, its blend of human+tech service is fairly unique. It likely appeals to organizations that want more hands-on guidance or “outsourced compliance officer” services in addition to software. 

**Use cases**: An SME might use DataGuard to achieve ISO 27001 certification (with DataGuard guiding them step-by-step and providing audit support), maintain a privacy compliance program, and prepare for upcoming NIS2 regulations – all via one vendor. This breadth can be attractive for companies that have to juggle multiple compliance obligations at once.

##### SureCloud (UK) – Integrated GRC Platform with SME Packages

**SureCloud** [is a UK-based Governance](https://www.surecloud.com/foundations#:~:text=Perfect%20for%20organizations%20starting%20their,and%20SOC%202%20with%20ease), Risk & Compliance software provider that has been in the market for about 15+ years. Traditionally, SureCloud’s platform has been used by larger organizations for risk management, compliance tracking, and penetration testing services. Recently, however, SureCloud introduced a **“Foundations” GRC package aimed at small teams and growing businesses**, to make their solution more accessible. SureCloud’s platform is a **no-code, modular GRC system** – it provides applications for Compliance Management, Risk Management, Third-Party Risk, Internal Audit, Incident Management, etc., [all unified](https://www.surecloud.com/foundations#:~:text=19%20years%20of%20expertise%20powers,compliant%20and%20ready%20to%20grow) in one [cloud interface](https://www.surecloud.com/foundations#:~:text=,ecosystem). For compliance, it includes pre-mapped content for various frameworks; out-of-the-box it supports common standards such as **ISO 27001, SOC 2, GDPR**, and even newer ones like **DORA (Digital Operational Resilience Act)** [and NIS2](https://www.surecloud.com/foundations#:~:text=Frameworks). SureCloud emphasizes automation of tasks like evidence collection, control monitoring, and reporting ([they advertise up to 75% reduction in manual effort, similar to peers](https://www.surecloud.com/foundations#:~:text=)). 

**Pricing model**: Unlike some competitors that charge per user, SureCloud’s SME-focused offering is sold as a package with a flat price for a certain scope. It’s reportedly **starting around £15k per year** for the “Foundations” edition (supporting a small compliance team with unlimited users) – significantly cheaper than their enterprise deployments, but still a sizable investment for a smaller SME. The company provides [custom quotes](https://www.surecloud.com/foundations#:~:text=A%20flexible%20package%20no%20matter,your%20size) and even a [downloadable pricing brochure](https://www.surecloud.com/foundations#:~:text=Download%20Pricing%20Brochure) for transparency. Essentially, SureCloud is positioning this as a **mid-tier solution**: more robust than lightweight tools, but with a cost and complexity still within reach of midsize businesses. For very small companies, £15k+ may be too high, but for, say, a 200-employee firm that needs a solid GRC system, it’s an attractive proposition. 

**Market presence**: SureCloud is a recognized name in the UK GRC space (featured in Gartner’s Magic Quadrant for IT Risk Management, etc.). Their clients have included enterprises in financial services, retail, and so on. By launching the Foundations product, they are trying to capture the upper-SME and mid-market segment. They highlight case studies like Specsavers and AutoTrader using SureCloud for [risk and compliance management](https://www.surecloud.com/foundations#:~:text=Specsavers%20choose%20SureCloud%20to%20Streamline,their%20Risk%20and%20Compliance). While those are large companies, the same platform now being scaled down means SMEs can trust that it’s a mature solution. In terms of market share, SureCloud isn’t as ubiquitous among SMEs as the smaller specialist tools (it’s more commonly seen in organizations with dedicated compliance teams). But it provides a path for SMEs that want to invest in a long-term GRC infrastructure that can grow with them. 

**Notable features**: SureCloud offers a unified platform approach – an SME can start with compliance management (e.g. manage their ISO 27001 or Cyber Essentials controls in the tool), and later expand to use it for vendor risk assessments, business continuity planning, etc., all within the same system. It also boasts strong **customizability without coding**, meaning as the business evolves, the tool can be configured to new requirements without expensive development. This flexibility and the **“single source of truth”** concept [(all risk and compliance data in one place) are major selling points](https://www.surecloud.com/foundations#:~:text=,ecosystem).

##### ISMS.online (UK) – Cloud Platform for ISO 27001 and More

**ISMS.online** (often stylized as ISMS.online or simply “IO”) is a UK-based SaaS platform that focuses on helping organizations implement and run an **Information Security Management System (ISMS)**. It started primarily as an ISO 27001 support tool but has expanded to cover multiple frameworks. For SMEs, ISMS.online provides a structured environment to **“kickstart your journey to compliance”** with [pre-built content](https://www.isms.online/plans/#:~:text=Compliance%20Essentials) and [guidance](https://www.isms.online/plans/#:~:text=Onboarding%20%26%20ongoing%20support). Out of the box, it includes what they call **Headstart content** – essentially template policies, controls, and an ISO 27001/other standard mapping that gives you an [“81% head start” on documentation](https://www.isms.online/plans/#:~:text=Our%20market%20leading%20ISMS%20platform%2C,complete%20with). There’s also an **Assured Results methodology** (step-by-step project plan to achieve certification) and a **Virtual Coach** feature to [guide users through tasks](https://www.isms.online/plans/#:~:text=An%2081,configured%20policies%20and%20controls). The platform supports multiple standards; you can choose one or multiple from a list that includes **ISO 27001, ISO 27701 (privacy), ISO 22301 (business continuity), ISO 9001 (quality), GDPR, NIS2, DORA**, etc. [This makes it quite comprehensive for an SME-oriented product](https://www.isms.online/plans/#:~:text=Onboarding%20%26%20ongoing%20support).

**Pricing model**: ISMS.online uses a **subscription model with tiered plans**, but all pricing is bespoke via quotes. They explicitly state that the pricing is flexible based on the customer’s objectives, [scope, and number of users](https://www.isms.online/iso-27001/certification-costs/#:~:text=How%20Much%20Does%20ISO%2027001,15k) – so you only pay for [what you need](https://www.isms.online/plans/#:~:text=Explore%20IO%20pricing%20plans%20designed,and%20maintain%20your%20compliance%20needs). In practice, an SME might purchase a single-framework package (e.g. ISO 27001 compliance package) at a certain annual cost, and later upgrade if they add more frameworks or users. There is no public price list, but anecdotal reports suggest it’s more affordable than enterprise GRC systems, though not as cheap as one-domain tools. It likely falls in the **few thousand pounds per year** range for a small company using it for one standard, going up with additional modules or larger user counts. 

**Market presence**: ISMS.online has a strong presence in the UK among tech SMEs, consultancies, and any organizations pursuing ISO certifications. They also partner with many security consultants and MSPs who use the platform for their clients (the [company has a partner directory](https://www.isms.online/cyber-essentials/#:~:text=Partners) for [advisors who can assist on the platform](https://www.isms.online/cyber-essentials/#:~:text=Back)). While exact user numbers aren’t published, ISMS.online has been around for several years and claims global users. It’s not unusual for companies that want to get ISO 27001 certified quickly to adopt ISMS.online rather than starting from scratch – the selling point is accelerating the process with ready-made tools and keeping the ISMS maintained easily afterward. It may not have the buzz of the VC-funded startups, but it occupies a solid niche for compliance-focused software in the UK. 

**Strengths**: ISMS.online is praised for being **very user-friendly for non-experts** and for its rich library of templates. Essentially it provides a “fill-in-the-blanks” ISMS where an SME can log risks, map controls to requirements, manage improvement actions, and generate audit-ready reports. It’s less about technical integration and automation (compared to Drata/Vanta which auto-check settings); it’s more about documentation management, workflow, and guidance. This makes it ideal for meeting governance requirements and passing audits. It also now [markets support for](https://www.isms.online/nis-2/controls/#:~:text=NIS%202%20Controls%20Explained%3A%20Evidence,ready%20with%20ISMS.online) **NIS2 controls**, [indicating it’s keeping up with new compliance needs](https://www.isms.online/nis-2/controls/#:~:text=,ready%20with%20ISMS.online).

##### OneTrust (US/UK) – Broad Compliance Platform (Privacy-Focused)

**OneTrust** is a big name in compliance software, historically known for privacy and data protection compliance (cookie consents, GDPR management, etc.), but it also offers modules for security, GRC, and ethics. OneTrust is headquartered in the US but has a large London presence and many UK customers. In the context of cybersecurity GRC for SMEs, OneTrust’s relevant offering is its **“Tech Risk & Compliance”** [module](https://www.onetrust.com/solutions/tech-risk-and-compliance/#:~:text=Tech%20Risk%20and%20Compliance%20,and%20mitigate%20risk%20while) – this includes capabilities like policy management, risk registers, control libraries, assessment automation, and vendor risk management. A company can use OneTrust to map their controls to frameworks such as ISO 27001 or NIST CSF and track compliance status. However, **OneTrust’s platform is very comprehensive and can be complex**, as it’s aimed at larger enterprises typically. In fact, OneTrust excels in areas like privacy compliance (e.g. managing subject access requests or cookie tracking) and may not have out-of-the-box depth for some cybersecurity frameworks. A 2025 industry review noted that “OneTrust is highly effective in privacy compliance but lacks the depth required for generic third-party security [management and compliance tracking under NIS-2”](https://www.3rdrisk.com/blog/top-10-tools-for-achieving-nis2-compliance#:~:text=OneTrust). In other words, OneTrust can be part of a security compliance program, but it’s not specialized for things like Cyber Essentials and might require more customization for those needs. 

**Pricing model**: OneTrust is modular – clients can license the pieces they need. It is generally **one of the more expensive solutions**, as it often targets enterprise budgets. Pricing is typically by annual subscription, with cost depending on number of modules, size of data (for privacy modules), and number of users or records. For an SME, OneTrust might be overkill unless they have substantial privacy management needs or already use it for GDPR and want to extend it to security GRC. There have been efforts by OneTrust to offer streamlined packages for smaller businesses (and they do have many mid-market clients too), but it’s safe to say it’s not a low-cost option. There’s no public price; everything is custom quoted. 

**Market presence**: OneTrust has a huge global presence – over 12,000 organizations use some part of its trust platform (privacy, GRC, ethics, etc.). In the UK, many companies adopted OneTrust for GDPR compliance around 2018. As for cybersecurity compliance specifically, OneTrust is often seen in larger firms that want an integrated risk management solution. SMEs might encounter OneTrust through its free tools (they offered free compliance assessments, etc., during earlier days) and then possibly grow into a paid customer. However, given the competition from more focused SME tools, OneTrust is not commonly the first choice for a UK SME trying to get, say, Cyber Essentials – it’s more likely used by a **mid-size or large enterprise that needs a unified platform for privacy and security compliance** together. 

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
 
 **Pricing model**: Kaseya sells this mostly to MSPs via annual licenses (the MSP then might offer “compliance as a service” to end clients). The pricing for an MSP might be based on the number of client organizations or endpoints under management. For an individual SME using it directly, one would license the software similarly to other IT software – typically a yearly subscription scaled by company size. The cost isn’t publicly listed, but given its MSP orientation, it is priced to allow MSPs to margin it in their service bundles (so likely not exorbitant per end-client). Kaseya often bundles it in their broader IT Complete suite for MSPs. 
 
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
| **SureCloud** (UK)                                                    | **Integrated GRC platform** with both Enterprise and new **“Foundations”** edition for smaller teams. Provides modules for compliance, risk, vendor management, etc. Out-of-the-box support for key standards (**ISO 27001, SOC 2, GDPR, NIS2, DORA**, etc.). Emphasizes no-code configurability and eliminating spreadsheets through automation (claims 75% reduction in manual effort). Suitable for organizations looking to scale their GRC program.                                                                                                                                           | **Annual subscription**. The SME Foundations package is a **fixed annual fee (approx. five figures)**, e.g. around **£15K/year** for a baseline package (unlimited users) as hinted by marketing. No per-user charges. Custom quotes for expanded needs.                                                                                                        | **Established vendor (since 2004)** with strong UK client base (enterprise and mid-market). Now targeting SMEs; used by notable UK companies (e.g. parts of Specsavers, AutoTrader) for compliance. Offers credibility and robustness, but higher cost than lightweight tools – tends to attract upper-end SMEs or those with dedicated compliance teams.                                                                                       |
| **ISMS.online** (UK)                                                  | **Cloud ISMS platform** tailored for achieving standards like **ISO 27001** (with guided implementation) and managing ongoing compliance. Comes with pre-written policies, control mappings, and a Virtual Coach for step-by-step progress. Supports multiple frameworks (ISO series, GDPR, NIS2, etc.) in one system. Focuses on documentation, risk assessment, and action tracking to satisfy auditors. Great for formal certification preparation and maintenance.                                                                                                                             | **Subscription-based**, but **pricing is bespoke** (no public tiers). Cost depends on number of frameworks and users. Generally affordable for small organizations compared to big GRC suites, but requires a quotation – e.g. a single-framework package for a small business might be in low **** thousands/year.                                             | **Hundreds of SMEs and tech firms** in the UK use it, especially for **ISO 27001**. It’s also popular among consultants who implement ISMS for clients (IO offers partner programs). Known for its ease-of-use and fast deployment. Not as visible as venture-backed rivals, but a steady player with a solid reputation in compliance circles.                                                                                                 |
| **OneTrust** (US/UK)                                                  | **Comprehensive trust platform** spanning privacy, security, data governance, and more. The **Tech Risk & Compliance** module covers infosec GRC: policy management, control assessments, risk registers, compliance automation to an extent. OneTrust excels in **privacy (UK GDPR, cookie compliance)** and integrates that with security incident and vendor risk management. However, its breadth can make it complex; it’s **geared toward larger orgs**, and some specific cybersecurity frameworks may need custom configuration (e.g. not a turnkey Cyber Essentials solution out-of-box). | **Modular licensing** – enterprise pricing. Clients might purchase a bundle of modules. Prices can run **tens of thousands £/year** for a full suite. They do offer scaled-down packages, but for most SMEs this is a significant investment. Often justified if the company has serious privacy compliance obligations (and then adds security module on top). | **Global leader** with 12k+ customers (many in Fortune 500). In UK, widely used for GDPR and vendor compliance. Less common for SME cyber compliance specifically, but some mid-sized UK firms leverage OneTrust for integrated risk management. Has a strong brand and resources (2700+ employees). **Not typically the first choice for basic CE needs**, but a powerful option for those needing a unified privacy-security-ethics solution. |
| **6clicks** (Australia)                                               | **Modern GRC platform** with a wide library of standards and **rapid deployment** focus. Includes AI features to streamline compliance mapping. Supports **UK frameworks (NIS2, ISO, etc.)** and international ones by default. Offers risk management, audits, incident tracking in one platform. UI is web-based and geared for consultants and internal teams alike. Some limitations in user experience and fewer native integrations, but very comprehensive feature set for the price.                                                                                                       | **SaaS subscription**. Offers flexible options (including a free tier and partner licensing). Likely priced by the number of accounts and modules. Aimed to be cost-effective – e.g. could be a mid-£ thousands/year for an SME deployment, but exact pricing varies.                                                                                           | **Emerging player** – used by a growing number of consulting firms and SMEs globally. Still building UK presence; not as well-known as others yet. Those who use it appreciate the all-in-one approach. Seen as a challenger to older GRC tools, with successful deployments in finance, government, etc., in APAC and expanding in Europe.                                                                                                     |
| **Kaseya Compliance Manager GRC** (RapidFire Tools)                   | **Compliance automation software** often leveraged by MSPs. Covers **UK Cyber Essentials** (latest version) and other standards, with built-in scanning of IT systems to check compliance. Auto-generates policies, reports, and evidence artifacts, and tracks remediation tasks. Designed to allow even non-security-experts (like IT technicians) to deliver compliance assessments. Provides continuous compliance monitoring especially for Windows environments. Ideal for multi-tenant use (managing several businesses’ compliance in one console).                                        | **Annual license** (usually MSP-oriented). MSPs pay per client or per asset; they in turn offer it as a service to SMEs (often bundled, e.g. a monthly fee for “compliance service”). Direct use by SMEs is possible but less common; would be a software subscription likely in the **low thousands £/yr** if sized for one organization.                      | **Widely deployed via MSPs** in the UK/US. Many SMEs indirectly use it through their IT providers. Strong in the niche of IT audit automation. Backed by Kaseya (large MSP software company). Its inclusion of Cyber Essentials content and SMB-specific standards shows commitment to the SME market. Not as visible in direct marketing to end-users, but a significant player through channel.                                               |
| **Enterprise GRC Suites** (e.g. RSA Archer, ServiceNow, MetricStream) | **High-end GRC/IRM systems** with exhaustive capabilities to manage risk and compliance at scale. Can be configured for any standard or regulation (NIS, ISO, internal policies, etc.) and integrated deeply into business processes. Offer advanced analytics, workflows, and enterprise system integrations. However, **not productized for specific SME needs** – require heavy customization and expertise. Reviews note they are **cumbersome and expensive**, with outdated interfaces in some cases.                                                                                        | **Enterprise pricing (very high)**. Typically involve large setup fees and ongoing costs per module/user. Often on-prem or private cloud deployments for security. Not feasible for SME budgets – usually only justified in organizations with dedicated risk departments.                                                                                      | **Dominant in large enterprise** segment (Fortune 500, governments). Virtually **0% market share in SMEs** due to cost/complexity. In context of UK SME compliance, these are mentioned only as theoretical options – in practice SMEs opt for more accessible solutions. Even mid-tier firms find these overly complex for needs like Cyber Essentials.                                                                                        |

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
