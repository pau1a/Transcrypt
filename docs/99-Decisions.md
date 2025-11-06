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
