# **1. Introduction**

This Information Architecture defines the structural model of Transcrypt across the Marketing runtime and the Essentials application. It establishes how the system’s surfaces are organised, how users move between them, and how meaning, hierarchy, and navigability are maintained. The IA sits beneath the behavioural rules in the PDS and the architectural constraints in the SAIS, ensuring every page, path, and transition reflects the product intent described in the PRD. This document provides the skeletal framework that governs structure, discoverability, and user flow, forming the basis for coherent design, consistent routing, and predictable interaction across the entire platform.

# **2. Full Sitemap**

The sitemap defines every surface the user can reach across both the Marketing runtime and the Essentials application, establishing the structural outline of the platform. It serves as the descriptive map of how pages are grouped and related. The complete, authoritative list of all pages — including identifiers, purpose, and runtime classification — is maintained in Appendix B and should be used alongside this sitemap for implementation and verification.

## **2.1 System Surfaces Overview**

This subsection defines the structural nature and boundaries of all surface types so the sitemap, hierarchy, transitions, and templates have a governed framework to attach to, preventing page-level drift and ensuring the entire IA remains coherent and enforceable.

## **2.1.1 Runtime Domains**

Transcrypt operates across two distinct runtimes: the Marketing runtime and the Essentials runtime. Marketing surfaces are public, expressive, and content-led, while Essentials surfaces are authenticated, task-driven, and deterministic. Each runtime maintains its own structural boundaries, interaction expectations, and page templates.

## **2.1.2 Surface Categories**

Surfaces are grouped into functional classes to clarify their operational purpose. Marketing includes landing pages, informational content, long-form articles, and legal documents. Essentials includes intake steps, evidence submission interfaces, evaluation flows, reporting views, billing surfaces, and system settings. Each category inherits consistent patterns defined in the IA and PDS.

## **2.1.3 Surface Roles**

Each surface carries a defined role within the overall system structure. Roles include entry points, hubs, workflow steps, leaf surfaces, and terminal outputs such as reports. These roles influence navigation availability, breadcrumb rules, and transition validity across the platform.

## **2.1.4 Boundary Surfaces and Transitions**

Boundary surfaces govern controlled movement between the Marketing and Essentials runtimes. These include authentication triggers, handoff surfaces, and subscription-gated entry points. Their behaviour is constrained by the runtime boundaries defined in the SAIS and the transition rules established in §12.

## **2.1.5 Non-Navigable Technical Surfaces**

Certain system surfaces exist for technical reasons but are not part of the navigable IA. These include callback endpoints, authentication results, error handlers, and internal state-transition intermediaries. They are referenced by routing but do not form part of the user-facing sitemap.

## **2.1.6 Out-of-Scope Surfaces**

Surfaces not included in the MVP are explicitly declared out of scope to prevent structural drift. These include auditor consoles, collaboration dashboards, enterprise administration panels, and multi-framework evaluation modules. Their omission preserves IA clarity and prevents premature deepening of the hierarchy.

---

## **2.2 Marketing Runtime Surfaces**

The Marketing runtime contains all public-facing, unauthenticated surfaces responsible for introducing the platform, explaining its value, enabling discovery, and supporting long-form content. These surfaces prioritise clarity, credibility, and controlled expression, and operate independently of the deterministic behaviour that governs the Essentials runtime.

## **2.2.1 Marketing Surface Classes**

Marketing surfaces fall into well-defined classes that each serve a distinct communicative purpose:

* **Landing Surfaces** — High-level introduction points that articulate value and direct users into deeper sections.
* **Informational Surfaces** — Structured content pages covering features, methodology, and problem framing.
* **Long-Form Content Surfaces** — Blog articles, guides, and explanatory material organised through taxonomy rules defined in §7.
* **Legal and Compliance Surfaces** — Public policy documents that must remain independently accessible and crawlable.

## **2.2.2 Navigational Behaviour**

These surfaces use expressive, content-led navigation patterns distinct from Essentials. Global navigation remains persistent, search (if enabled) is optional, and contextual links reinforce topical or thematic discovery. Navigation within the Marketing runtime must not expose authenticated functions or imply interaction modes belonging to Essentials.

## **2.2.3 Expression and Layout Constraints**

Marketing surfaces follow the expressive palette and structural allowances defined in the Brand Identity Guide. They support broader content widths, more flexible hierarchy, and promotional narrative elements. Even so, their layout patterns must still align with the structural templates in Appendix A to ensure consistency across all surfaces.

## **2.2.4 Interaction Boundaries**

Marketing surfaces do not alter user state and do not expose deterministic workflows. Any transition toward authenticated or task-driven behaviour must occur cleanly through controlled entry points defined in §2.1.4. This prevents leakage of application-state assumptions into public content.

## **2.2.5 Search and Discoverability Considerations**

If Marketing search is provided, it operates strictly over public content types and uses taxonomy and metadata rules defined in §7 and Appendix C. Discovery mechanisms must reinforce, not duplicate, the internal logic of cross-linking defined in §9.

## **2.2.6 Surface Exclusions**

No authenticated, multi-step, or data-bearing surfaces appear in the Marketing runtime. Evaluation, Reporting, Evidence, Billing, and Settings structures are completely excluded to maintain runtime purity and prevent user confusion.

---

## **2.3 Essentials Runtime Surfaces**

The Essentials runtime contains all authenticated, task-driven surfaces responsible for intake, evidence handling, evaluation, reporting, billing, and account administration. These surfaces operate under deterministic behavioural rules defined in the PDS and SAIS, with controlled navigation, predictable state transitions, and strict separation from the expressive patterns of the Marketing runtime.

### **2.3.1 Core Functional Surface Classes**

Essentials surfaces fall into discrete functional classes reflecting the structure of the compliance workflow:

* **Intake Surfaces** — Establish baseline organisational data.
* **Evidence Surfaces** — Submit, validate, and review artefacts per control family.
* **Evaluation Surfaces** — Structured progression through readiness and compliance calculations.
* **Reporting Surfaces** — Snapshot-driven summaries and outputs.
* **Billing & Subscription Surfaces** — Payment, renewal, and subscription state management.
* **Settings & Profile Surfaces** — User identity, organisational data, and configuration.

### **2.3.2 Deterministic Navigation Rules**

Navigation is restricted by workflow state, access rights, and evaluation progress. Forward and backward movement must adhere to the rules in §12, and global navigation must never expose Marketing-only pathways.

### **2.3.3 State Constraints and Persistence Requirements**

Many surfaces operate under persistent tenant state. All interactions must be reversible, traceable, and aligned to the state boundaries defined in the SAIS, with no hidden side-effects or silent transitions.

### **2.3.4 Behavioural and Layout Restrictions**

Essentials avoids expressive marketing patterns. Components, spacing, and interaction behaviour follow the constrained palette defined in the PDS. Layouts must conform to the templates in Appendix A.

### **2.3.5 Compliance and Audit Considerations**

All Essentials surfaces support auditability: enforcing data integrity, consistent presentation of required fields, strict progression rules, and fully observable user actions suitable for certification scrutiny.

### **2.3.6 Surface Exclusions**

Exploratory content, narrative marketing material, or non-deterministic informational pages are never displayed in Essentials. Long-form guides, promotional pages, and blog content remain strictly within the Marketing runtime.

---

## **2.4 Cross-Runtime Junctions**

Cross-runtime junctions are the controlled points of movement between the public Marketing runtime and the authenticated Essentials runtime. These junctions enforce strict boundaries so that expressive, content-led surfaces never leak into deterministic workflows, and task-driven behaviours remain inaccessible from public pages. Each junction must follow the runtime separation rules defined in the SAIS and the transition constraints in §12.

### **2.4.1 Authentication Entry Points**

These are the primary routes through which users transition from public content into the authenticated environment. They include login triggers, sign-up paths, and subscription-gated entry flows. All authentication entry points must initiate clean runtime handoff, with no residual Marketing-state assumptions carried into Essentials.

### **2.4.2 Subscription and Access-Gated Transitions**

Some transitions require an active subscription or specific evaluation access. These junctions gate progression based on tenant state, subscription tier, or billing validity. They ensure that users enter Essentials only when authorised and prevent access to task-driven surfaces from the public domain.

### **2.4.3 Evaluation Workflow Initiation Surfaces**

Initiation points for intake, evidence submission, or evaluation workflows originate at controlled surfaces that bridge the Marketing promise (value proposition) and the Essentials task environment. These junctions must maintain consistent messaging while shifting from expressive to deterministic behaviour.

### **2.4.4 Return Paths to Marketing**

Some surfaces in Essentials allow controlled return paths to public content, typically via navigation rails or contextual links. These transitions must never break workflow state or expose partial internal process context. Any return path must restore the user to a clean view of public information without leaking authenticated state.

### **2.4.5 Disallowed or Forbidden Runtime Crossings**

Certain movements must be explicitly prohibited to preserve structural and behavioural integrity. Examples include direct jumps from deep Essentials workflow steps into Marketing pages, or attempts to bypass authentication barriers. These invalid transitions are defined in detail in §12.4 and exist as enforced constraints at the routing level.

### **2.4.6 Error-State and Recovery Junctions**

When runtime crossings fail due to authentication errors, expired subscriptions, or state corruption, recovery surfaces handle these cases. They guide the user back to a stable runtime boundary without revealing internal system details. These non-expressive, constrained surfaces act as controlled recovery points.

---

## **2.5 Hidden or Technical Surfaces (non-navigable)**

Hidden or technical surfaces are required for system operation but do not form part of the user-facing IA. They are invoked by routing, authentication, subscription logic, or state transitions, and cannot be accessed directly through navigation. Their existence is declared to ensure architectural clarity while preventing them from polluting the sitemap or hierarchical structure.

### **2.5.1 Authentication Callbacks**

These surfaces receive responses from external identity providers and translate them into internal session state. They are never user-visible and must not appear in the sitemap or breadcrumb model. Their behaviour is defined entirely by SAIS authentication boundaries.

### **2.5.2 Error and Recovery Endpoints**

Certain errors require controlled surfaces that capture invalid states, expired sessions, or corrupted transitions. These endpoints are technical safeguards that route users back to stable runtime boundaries without exposing system detail or workflow internals.

### **2.5.3 Subscription and Billing Webhooks**

Automated inbound calls from payment processors or subscription platforms populate tenant state or update entitlement logic. These surfaces cannot be navigated manually and serve only as system integration points.

### **2.5.4 Internal Redirect and Routing Intermediaries**

Some transitions require short-lived intermediary surfaces to handle conditional redirects, workflow validation, or URL canonicalisation. They must never be indexed, linked, or shown to users. Their naming and behaviour follow strict routing constraints defined in the SAIS.

### **2.5.5 Background or System Maintenance Surfaces**

The platform may expose internal-only surfaces related to monitoring, verification, or administrative checks. These exist solely for internal tooling or automation flows. They are explicitly excluded from all navigational, hierarchical, and SEO structures.

---

# **3. Navigation Model**

This section establishes how users move between surfaces: global navigation, secondary navigation, inline navigation, and conditional navigation states. It ensures movement through the product is predictable, reversible, and free of ambiguity.

## **3.1 Primary Navigation**

## **3.2 Secondary Navigation**

## **3.3 Workflow Navigation**

## **3.4 Suppressed Navigation States**

## **3.5 Mobile Navigation Behaviour**

## **3.6 Navigation Fail-Safes**

# **4. Page Hierarchy**

This hierarchy defines how all surfaces relate to one another, assigning structural weight and ordering pages into clear parent–child relationships. It prevents unnecessary flattening, avoids deep or confusing nesting, and ensures users always understand where they are in the system. Hierarchical groupings in this section correspond to the structural templates illustrated in Appendix A.

## **4.1 Structural Tiers**

## **4.2 Sectional Parents**

## **4.3 Page-Level Weighting**

## **4.4 Hierarchical Exceptions**

## **4.5 Edge-Case Elevation Rules**

# **5. SEO Keyword Mapping**

This section defines the primary and secondary keyword targets for organic search and assigns them to specific surfaces within the platform. Its purpose is to ensure that each page carries a distinct search intent, preventing overlap and internal competition. Keyword assignments must align with the metadata fields and constraints defined in Appendix C, which governs how these targets are expressed through canonical tags, descriptive fields, and other SEO-relevant metadata.

## **5.1 Pillar Keyword Targets**

## **5.2 Page-Level Intent Targets**

## **5.3 Semantic Neighbourhoods**

## **5.4 Cannibalisation Boundaries**

## **5.5 Long-Tail Capture Plan**

## **5.6 Deprioritised Keywords**

# **6. Content Types**

This section defines the distinct classes of content used across the platform, from marketing pages and long-form articles to intake forms, evaluation steps, reports, and legal surfaces. Each type carries its own structural requirements and behavioural expectations. The foundational templates for these content types are represented in Appendix A, ensuring consistency, predictability, and long-term maintainability.

## **6.1 Marketing Types**

## **6.2 Application Types**

## **6.3 Evidence & Report Types**

## **6.4 Structural Requirements Per Type**

# **7. Taxonomy**

The taxonomy defines the classification system used across content, including tags, categories, and thematic groupings. It ensures consistent organisation, improves discoverability, and supports internal search behaviours.

## **7.1 Core Categories**

## **7.2 Extended Categories**

## **7.3 Tag Architecture**

## **7.4 Synonym Rules**

## **7.5 Taxonomy Governance Lifecycle**

## **7.6 Deprecated or Merged Taxonomies**

# **8. URL Structure**

This section defines the canonical URL patterns that determine how pages are addressed, indexed, and resolved across the system. It specifies the rules for slug formation, parameter handling, pagination, and reserved paths to ensure clarity, predictability, and long-term stability. URL patterns for key templates follow the structural forms shown in Appendix A, while all canonical, redirect, and metadata-dependent behaviours must conform to the field definitions and constraints set out in Appendix C.

## **8.1 Canonical Paths**

## **8.2 Slug Construction**

## **8.3 Parameter Rules**

## **8.4 Pagination Rules**

## **8.5 Redirect Behaviour**

## **8.6 Legacy URL Handling**

## **8.7 Reserved Paths**

# **9. Cross-Linking Strategy**

This establishes when and how surfaces should link to each other to reinforce navigation, improve SEO, and reduce isolating “dead-end” pages. It ensures crosslinks are purposeful, not decorative, and always contextually appropriate.

## **9.1 Mandatory Internal Links**

## **9.2 Contextual Relevance Links**

## **9.3 SEO-Driven Link Clusters**

## **9.4 Cross-Link Suppression Rules**

# **10. Breadcrumb Rules**

Breadcrumbs provide users with a clear orientation within the site’s hierarchy. This section defines when breadcrumbs appear, how they are structured, and how they reflect the underlying page hierarchy.

## **10.1 Eligibility Criteria**

## **10.2 Hierarchy Mapping Rules**

## **10.3 Breadcrumb Composition**

## **10.4 Responsive/Collapsed Breadcrumbs**

## **10.5 Suppressed Breadcrumb Cases**

# **11. Depth/Flatness Constraints**

This governs how deep the IA is allowed to go before it becomes unwieldy and how flat it may become before meaning collapses. It prevents drift into unnecessary nested structures while preserving clarity and navigability.

## **11.1 Maximum Depth Thresholds**

## **11.2 Minimum Depth Thresholds**

## **11.3 Section-Specific Depth Limits**

# **12. Transition Matrix for User Journeys**

This section defines all valid transitions between surfaces, specifying the preconditions for entry, the states that must be preserved or established, and the conditions under which each path may terminate. It ensures every journey remains deliberate, predictable, and traceable across Marketing, Essentials, Billing, and Reporting. All transitions in this matrix must reference the page identifiers defined in Appendix B to guarantee alignment with the authoritative page inventory.

## **12.1 Valid Transitions**

## **12.2 Forbidden Transitions**

## **12.3 Conditioned Transitions**

## **12.4 Terminal States**

---

# **Appendix A — Wireframes**

## **A.1 Page Templates**

## **A.2 Layout Patterns**

## **A.3 Breakpoint Variants**

## **A.4 Component Sketches**

## **A.5 Interaction States**

---

## **Appendix B — Page Inventory Tables**

A fully tabulated representation of:

* page name
* purpose
* runtime (Marketing / Essentials)
* template reference
* allowed transitions (summary)
* URL pattern
* taxonomy assignment

This is too large for the main IA but essential for implementation, QA, and cross-referencing.

## **Appendix C — Metadata Schema**

Because metadata touches SEO, discoverability, canonical structure, and CMS fields, the schema needs a clear, stable reference outside the IA body.

Includes:

* required fields
* optional fields
* field types
* rules for canonical/OG/meta
* default values
* validation rules

This appendix becomes the binding spec for the CMS and Next.js metadata layer.

---

# **Appendices That Are PROBABLY Needed (but optional until content expands)**

## **Appendix D — Taxonomy Catalogue**

Once the taxonomy grows, a catalogue of all categories, tags, synonyms, and deprecated tags is required.
Initially optional, but it becomes essential as content volume increases.

## **Appendix E — Linkage Map (Cross-Link Diagram Set)**

Internal cross-links, especially SEO-driven or journey-critical ones, often need diagrammatic representation.

This appendix is optional until the system has 20+ pages or linked clusters that must be visualised.

## **Appendix F — Search Configuration (If Search Exists in MVP)**

If you add site or blog search (even basic), you will need:

* indexed content types
* stopword lists
* weighting rules
* exclusions
* ranking adjustments

If search is postponed, this appendix is postponed.

---