## 2025-11-06 – Decision: MVP scope lock (Transcrypt Core)

- **Problem:** Vision drift between “lightweight assistant” and “full automation platform”.
- **Decision:** v1 is **Transcrypt Core** (lightweight assistant). Platform features are post-MVP.
- **Consequences:** Section 5 constrained to assistive AI; provenance ledger and auditor marketplace deferred to v2.0; Roadmap section added.

## 2025-11-07 – Decision: Closed-Source Policy and Transparency Alignment

- **Problem:** PRD implied both full transparency (open auditing) and a closed-source codebase.
- **Decision:** Transcrypt remains **closed-source**, but implements **verifiable transparency** through cryptographically signed, user-verifiable outputs.
- **Consequences:**
  - §5.5 rewritten to define this principle.
  - §5.4 cross-references it.
  - Vision updated to describe transparency via verifiable outputs, not open code.
  - Future roadmap (v2.0+) includes external notarisation ledger.

## 2025-11-07 – Decision: Framework-Agnostic Compliance Architecture

- **Problem:** PRD implied a fixed UK scope (Cyber Essentials/NIS2) but hinted at future expansion without structural basis.
- **Decision:** Core compliance logic is **framework-agnostic** using pluggable **Compliance Packs**.
- **Consequences:**
  - Market Context now states UK-first but extensible design.
  - System Overview adds “Framework Modularity.”
  - §5.1 adds extensibility note.
  - Roadmap updated to include multi-framework evolution.
- **Outcome:** Removes contradiction between UK-specific narrative and scalable architecture.

## 2025-11-08 – Decision: SME Audience vs Enterprise-Grade Architecture

- **Problem:** PRD implied enterprise-level complexity for an SME audience, risking feature overreach.
- **Decision:** Maintain enterprise security and automation internally while presenting an SME-focused, plain-language experience.
- **Consequences:**
  - Vision and System Overview updated with "Invisible Infrastructure Principle".
  - Section 5 clarified to show advanced components as background automation.
  - Design Tenets added to codify simplicity.
  - Roadmap entry added for UX refinement phase.
- **Outcome:** Product narrative aligns technical depth with SME usability—complexity hidden, results simple.

## 2025-11-09 – Decision: Automation vs Human Expertise Clarification

- **Problem:** PRD blurred self-serve automation and human-assisted models.
- **Decision:** v1 (Transcrypt Core) is 100% automated. Human expertise enters only in future Assisted Tier and Marketplace phases.
- **Consequences:**
  - Vision updated with Human Role Definition.
  - System Overview expanded with Automation-First Operating Model.
  - §5.2 clarified for self-serve loop.
  - Roadmap now includes Assisted Tier and Marketplace stages.
- **Outcome:** Removes confusion between automation and manual review while preserving a scalable future for expert involvement.

## 2025-11-09 – Decision: Data Ownership and SaaS Alignment

- **Problem:** PRD created tension between “data sovereignty” and “centralised SaaS.”
- **Decision:** Transcrypt remains a cloud service but uses **centrally orchestrated, locally encrypted architecture**.
  Each tenant controls their own encryption keys and data cannot be decrypted by Transcrypt Ltd.
- **Consequences:**
  - System Overview and §5.1 updated with tenant isolation and encryption model.
  - Vision clarified for cryptographic ownership.
  - Glossary and Roadmap updated for Tenant Vaults and Geo-sovereign Nodes.
- **Outcome:** Eliminates philosophical contradiction — data remains private within shared infrastructure.

## 2025-11-10 – Decision: Document Duality (Strategy vs Specification)

- **Problem:** PRD blended strategic vision with technical specification without explicit structure, creating ambiguity of authority.
- **Decision:** Establish clear dual-mode structure — strategic (why) and specification (how) — with markers and guidance table.
- **Consequences:**  
  - Added “Document Scope and Usage” section near top.  
  - Tagged sections using `<!-- strategic -->` and `<!-- specification -->` comments.  
  - Added YAML front-matter metadata and Cross-Reference Conventions.  
  - Updated introduction to explain hybrid purpose.  
- **Outcome:** Readers now understand which sections are directional versus binding; document retains flexibility without confusion.

## 2025-11-11 – Decision: Cross-Reference and Traceability Framework

- **Problem:** Several sections (notably §5) referenced undefined or future components, creating ambiguity.
- **Decision:** Implement a structured cross-reference and traceability system using tags [↩ S#], [↩ A#], [[Post-MVP: §9]], and [→ UX#].
- **Consequences:**
  - Added “Cross-Referencing Framework” section.
  - Annotated all §5 dependencies with proper tags.
  - Introduced Traceability Table in §5.
  - Updated intro to describe new system.
  - Marked unfinished sections with [[Placeholder]] notice.
- **Outcome:** Full internal coherence; every feature can now be traced backward to strategy or forward to roadmap.
