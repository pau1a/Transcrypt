# **1. Introduction**

This Information Architecture defines the structural model of Transcrypt across the Marketing runtime and the Essentials application. It establishes how the system’s surfaces are organised, how users move between them, and how meaning, hierarchy, and navigability are maintained. The IA sits beneath the behavioural rules in the PDS and the architectural constraints in the SAIS, ensuring every page, path, and transition reflects the product intent described in the PRD. This document provides the skeletal framework that governs structure, discoverability, and user flow, forming the basis for coherent design, consistent routing, and predictable interaction across the entire platform.

# **2. Full Sitemap**

The sitemap defines every surface the user can reach across both the Marketing runtime and the Essentials application, establishing the structural outline of the platform. It serves as the descriptive map of how pages are grouped and related. The complete, authoritative list of all pages — including identifiers, purpose, and runtime classification — is maintained in Appendix B and should be used alongside this sitemap for implementation and verification. **Lateral, cross-page connective elements (such as contextual or semantic cross-links) are implemented through governed partials defined in Appendix D.**

## **2.1 System Surfaces Overview**

This subsection defines the structural nature and boundaries of all surface types so the sitemap, hierarchy, transitions, and templates have a governed framework to attach to, preventing page-level drift and ensuring the entire IA remains coherent and enforceable. **Cross-surface relationships that do not form part of the structural hierarchy (e.g., contextual recommendations, industry pivots, related-content meshes) are governed separately through the partials catalogue in Appendix D.**

## **2.1.1 Runtime Domains**

Transcrypt operates across two distinct runtimes: the Marketing runtime and the Essentials runtime. Marketing surfaces are public, expressive, and content-led, while Essentials surfaces are authenticated, task-driven, and deterministic. Each runtime maintains its own structural boundaries, interaction expectations, and page templates.

## **2.1.2 Surface Categories**

Surfaces are grouped into functional classes to clarify their operational purpose. Marketing includes landing pages, informational content, long-form articles, and legal documents. Essentials includes intake steps, evidence submission interfaces, evaluation flows, reporting views, billing surfaces, and system settings. Each category inherits consistent patterns defined in the IA and PDS.

## **2.1.3 Surface Roles**

Each surface carries a defined role within the overall system structure. Roles include entry points, hubs, workflow steps, leaf surfaces, and terminal outputs such as reports. These roles influence navigation availability, breadcrumb rules, and transition validity across the platform. **Non-hierarchical, lateral relationships between surfaces—such as related content or thematic pivots—are deliberately excluded from these roles and instead follow the governed partial mechanisms in Appendix D.**

## **2.1.4 Boundary Surfaces and Transitions**

Boundary surfaces govern controlled movement between the Marketing and Essentials runtimes. These include authentication triggers, handoff surfaces, and subscription-gated entry points. Their behaviour is constrained by the runtime boundaries defined in the SAIS and the transition rules established in §12.

## **2.1.5 Non-Navigable Technical Surfaces**

Certain system surfaces exist for technical reasons but are not part of the navigable IA. These include callback endpoints, authentication results, error handlers, and internal state-transition intermediaries. They are referenced by routing but do not form part of the user-facing sitemap.

## **2.1.6 Out-of-Scope Surfaces**

Surfaces not included in the MVP are explicitly declared out of scope to prevent structural drift. These include auditor consoles, collaboration dashboards, enterprise administration panels, and multi-framework evaluation modules. Their omission preserves IA clarity and prevents premature deepening of the hierarchy.

---

## **2.2 Marketing Runtime Surfaces**

The Marketing runtime contains all public-facing, unauthenticated surfaces responsible for introducing the platform, explaining its value, enabling discovery, and supporting long-form content. These surfaces prioritise clarity, credibility, and controlled expression, and operate independently of the deterministic behaviour that governs the Essentials runtime. **Marketing surfaces may embed cross-referential partials as defined in Appendix D to support controlled lateral discovery and guided progression.**

### **2.2.1 Marketing Surface Classes**

Marketing surfaces fall into well-defined classes that each serve a distinct communicative purpose:

* **Landing Surfaces** — High-level introduction points that articulate value and direct users into deeper sections.
* **Informational Surfaces** — Structured content pages covering features, methodology, and problem framing.
* **Long-Form Content Surfaces** — Blog articles, guides, and explanatory material organised through taxonomy rules defined in §7. **These surfaces rely heavily on partials such as Related Stories, Starter Kit Promo, and Research Highlight as governed in Appendix D.**
* **Legal and Compliance Surfaces** — Public policy documents that must remain independently accessible and crawlable.

### **2.2.2 Navigational Behaviour**

These surfaces use expressive, content-led navigation patterns distinct from Essentials. Global navigation remains persistent, search (if enabled) is optional, and contextual links reinforce topical or thematic discovery. **All such contextual or thematic cross-links must comply with the partial definitions and placement rules defined in Appendix D.** Navigation within the Marketing runtime must not expose authenticated functions or imply interaction modes belonging to Essentials.

### **2.2.3 Expression and Layout Constraints**

Marketing surfaces follow the expressive palette and structural allowances defined in the Brand Identity Guide. They support broader content widths, more flexible hierarchy, and promotional narrative elements. Even so, their layout patterns must still align with the structural templates in Appendix A to ensure consistency across all surfaces.

### **2.2.4 Interaction Boundaries**

Marketing surfaces do not alter user state and do not expose deterministic workflows. Any transition toward authenticated or task-driven behaviour must occur cleanly through controlled entry points defined in §2.1.4. This prevents leakage of application-state assumptions into public content.

### **2.2.5 Search and Discoverability Considerations**

If Marketing search is provided, it operates strictly over public content types and uses taxonomy and metadata rules defined in §7 and Appendix C. Discovery mechanisms must reinforce, not duplicate, the internal logic of cross-linking defined in §9 and implemented via the partials catalogue in Appendix D.

### **2.2.6 Surface Exclusions**

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

This hierarchy defines how all surfaces relate to one another, assigning structural weight and ordering pages into clear parent–child relationships. It prevents unnecessary flattening, avoids deep or confusing nesting, and ensures users always understand where they are in the system. Hierarchical groupings in this section correspond to the structural templates illustrated in Appendix A. Non-hierarchical, lateral connections between surfaces—such as contextual recommendations, industry pivots, or cross-content meshes—are not represented in the hierarchy and are instead governed by the partial mechanisms defined in Appendix D.

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

This section defines the distinct classes of content used across the platform, from marketing pages and long-form articles to intake forms, evaluation steps, reports, and legal surfaces. Each type carries its own structural requirements and behavioural expectations. The foundational templates for these content types are represented in Appendix A, ensuring consistency, predictability, and long-term maintainability. Certain content types may embed governed cross-page partials for lateral discovery (e.g., related content, industry pivots, workflow guidance), and these partials are defined and constrained in Appendix D.

## **6.1 Marketing Types**

## **6.2 Application Types**

## **6.3 Evidence & Report Types**

## **6.4 Structural Requirements Per Type**

# **7. Taxonomy**

The taxonomy defines the classification system used across content, including tags, categories, and thematic groupings. It ensures consistent organisation, improves discoverability, and supports internal search behaviours. Taxonomy also powers several cross-referential partials—such as Related Stories, For Your Industry, and Research Highlight—whose behaviour and placement rules are governed in Appendix D. Any taxonomy-driven partial must reflect the authoritative taxonomy structures defined in this section.

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

This establishes when and how surfaces should link to each other to reinforce navigation, improve SEO, and reduce isolating “dead-end” pages. It ensures crosslinks are purposeful, not decorative, and always contextually appropriate. All lateral cross-links—including contextual recommendations, thematic pivots, industry-based suggestions, and SEO-driven surfacing—must be implemented exclusively through the governed partial mechanisms defined in Appendix D. No page may introduce an unmanaged or ad-hoc cross-link.

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

---

## **Appendix B — Page Inventory (Split by Phase)**

This appendix lists all user-facing surfaces for both Phase 1 (Marketing) and Phase 2 (Essentials).
Each entry includes its phase ID, name, runtime, and URL pattern.
Partials will be assigned later once Appendix D is fully populated.

---

# **B.1 Phase 1 — Marketing / Blog / Guides / Resources / Waitlist**

### **B.1.1 Home** — `/`

### **B.1.2 About** — `/about`

### **B.1.3 Features** — `/features`

### **B.1.4 Pricing** — `/pricing`

### **B.1.5 Contact / Support** — `/contact`

### **B.1.6 Why Transcrypt** — `/why`

### **B.1.7 Security Overview** — `/security`

### **B.1.8 Case Studies (Index)** — `/case-studies`

### **B.1.9 Case Study (Template)** — `/case-studies/{slug}`

---

### **Blog**

### **B.1.10 Blog Landing / Overview** — `/blog/overview`

### **B.1.11 Blog Index** — `/blog`

### **B.1.12 Blog Article Template** — `/blog/{slug}`

---

### **Blog Taxonomy**

### **B.1.13 Blog Categories Overview** — `/blog/categories`

### **B.1.14 Blog Category Page** — `/blog/category/{slug}`

### **B.1.15 Blog Tags Overview** — `/blog/tags`

### **B.1.16 Blog Tag Page** — `/blog/tag/{slug}`

### **B.1.17 Blog Author Page** — `/blog/author/{slug}`

### **B.1.18 Blog Search** — `/blog/search`

### **B.1.19 Blog Pagination** — `/blog/page/{n}`

### **B.1.20 Blog Category Pagination** — `/blog/category/{slug}/page/{n}`

### **B.1.21 Blog Tag Pagination** — `/blog/tag/{slug}/page/{n}`

### **B.1.22 Blog Search Pagination** — `/blog/search/page/{n}`

### **B.1.23 Blog Date Archive (Year)** — `/blog/{yyyy}`

### **B.1.24 Blog Date Archive (Month)** — `/blog/{yyyy}/{mm}`

---

### **Guides**

### **B.1.25 Guides Index** — `/guides`

### **B.1.26 Guide Article Template** — `/guides/{slug}`

### **B.1.27 Guides Categories Overview** — `/guides/categories`

### **B.1.28 Guide Category Page** — `/guides/category/{slug}`

---

### **Resources**

### **B.1.29 Resource Library** — `/resources`

### **B.1.30 Resource Download** — `/resources/{slug}`

### **B.1.31 Resource Download Confirmation** — `/resources/{slug}/thanks`

---

### **Conversions**

### **B.1.32 Waitlist** — `/waitlist`

### **B.1.33 Waitlist Confirmation** — `/waitlist/thanks`

### **B.1.34 Newsletter Signup** — `/newsletter`

### **B.1.35 Newsletter Confirmation** — `/newsletter/confirm`

### **B.1.36 Newsletter Thanks** — `/newsletter/thanks`

---

### **Legal & Trust**

### **B.1.37 Privacy Policy** — `/privacy`

### **B.1.38 Terms of Service** — `/terms`

### **B.1.39 Cookie Policy** — `/cookies`

### **B.1.40 Accessibility Statement** — `/accessibility`

### **B.1.41 Responsible Disclosure** — `/security/disclosure`

### **B.1.42 Acceptable Use Policy** — `/aup`

### **B.1.43 Subprocessors List** — `/subprocessors`

### **B.1.44 Data Protection Addendum** — `/dpa`

---

### **Operational**

### **B.1.45 Status Page** — `/status`

---

### **Expanded High-Value Additions**

### **B.1.46 Comparison Hub** — `/compare`

### **B.1.47 Transcrypt vs Traditional Consultancy** — `/compare/consultancy`

### **B.1.48 Transcrypt vs Self-Assessment** — `/compare/self-assessment`

### **B.1.49 How It Works** — `/how-it-works`

### **B.1.50 Industries Overview** — `/industries`

### **B.1.51 Industry Landing Template** — `/industries/{slug}`

### **B.1.52 Glossary** — `/glossary`

### **B.1.53 Starter Kit** — `/starter-kit`

### **B.1.54 Roadmap** — `/roadmap`

### **B.1.55 State of SME Cybersecurity Report Hub** — `/reports/state-of-sme-cybersecurity`

---

# **B.2 Phase 2 — Essentials (Product Runtime)**

### **Identity**

### **B.2.1 Log In** — `/auth/login`

### **B.2.2 Password Reset Request** — `/auth/reset`

### **B.2.3 Password Reset Confirm** — `/auth/reset/{token}`

---

### **Signup / Onboarding**

### **B.2.4 Signup Start** — `/signup`

### **B.2.5 Signup Email Verification** — `/signup/verify`

### **B.2.6 Signup Email Verified** — `/signup/verified`

### **B.2.7 Subscription Checkout** — `/signup/checkout`

### **B.2.8 Onboarding Complete → Intake** — `/signup/complete`

---

### **Intake**

### **B.2.9 Organisation Setup** — `/app/intake`

### **B.2.10 Organisation Details** — `/app/org`

---

### **Evidence**

### **B.2.11 Evidence Dashboard** — `/app/evidence`

### **B.2.12 Evidence Submission** — `/app/evidence/{control}`

### **B.2.13 Evidence Review** — `/app/evidence/{control}/review`

---

### **Evaluation**

### **B.2.14 Evaluation Overview** — `/app/evaluation`

### **B.2.15 Evaluation Step** — `/app/evaluation/{step}`

### **B.2.16 Evaluation Complete** — `/app/evaluation/complete`

---

### **Reporting**

### **B.2.17 Report View** — `/app/report`

### **B.2.18 Report Download** — `/app/report/download`

---

### **Billing**

### **B.2.19 Billing Dashboard** — `/app/billing`

### **B.2.20 Subscription Management** — `/app/billing/subscription`

### **B.2.21 Payment Methods** — `/app/billing/payment-methods`

### **B.2.22 Billing History** — `/app/billing/history`

---

### **Settings**

### **B.2.23 User Profile** — `/app/settings/profile`

### **B.2.24 Security Settings** — `/app/settings/security`

### **B.2.25 Notification Preferences** — `/app/settings/notifications`

### **B.2.26 Organisation Profile** — `/app/settings/org`

---

## **Appendix B2 — Page Inventory Tables**

### **B.1 Phase 1 — Marketing / Blog / Guides / Resources / Waitlist**

| Page Name                             | Purpose                                                        | Runtime   | Template Ref               | Allowed Transitions (Summary)                                                                    | URL Pattern                           | Taxonomy Assignment                                 | Rationale                                                                                  | Possible Partials                                      | SEO Intent                                                                     |
| ------------------------------------- | -------------------------------------------------------------- | --------- | -------------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------- | --------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------------------------------ |
| Home                                  | Primary entry; positioning and core value narrative            | Marketing | MKT.Home.Landing           | From external; global nav to all marketing primaries; CTAs → /how-it-works, /features, /waitlist | `/`                                   | Type: Landing; ContentGroup: Marketing              | Anchor for all marketing flows; first impression and orientation                           | next-best-step, research-highlight, starter-kit-promo  | Broad TOFU: “cyber essentials platform”, “SME cyber compliance”                |
| About                                 | Company story, mission, credibility                            | Marketing | MKT.About.Static           | From nav; links → /why, /security, /responsible-disclosure                                       | `/about`                              | Type: Static; ContentGroup: About                   | Humanises brand; supports trust and due diligence                                          | related-stories, research-highlight                    | Trust / brand queries: “about transcrypt”, founder / company background        |
| Features                              | Describes product capabilities at high level                   | Marketing | MKT.Features.Overview      | From nav, home CTAs; links → /how-it-works, /compare, /industries, /starter-kit                  | `/features`                           | Type: Landing; ContentGroup: Product                | Core explainer for what the product actually does                                          | next-best-step, roadmap-teaser, for-your-industry      | Mid-funnel: “cyber essentials automation features”, “compliance workflow tool” |
| Pricing                               | Shows plans, inclusions, commercial posture                    | Marketing | MKT.Pricing.Plans          | From nav, CTAs on /features, /compare; forward → /waitlist (P1), /signup (P2)                    | `/pricing`                            | Type: Landing; ContentGroup: Pricing                | Aligns perceived value with cost; key decision surface                                     | next-best-step, starter-kit-promo                      | BOFU: “cyber essentials pricing”, “compliance SaaS cost”                       |
| Contact / Support                     | Contact form, support routes, email, minimal FAQs              | Marketing | MKT.Contact.Form           | From footer/nav/CTAs; no deep forward transitions except confirmation                            | `/contact`                            | Type: Utility; ContentGroup: Support                | Gives SMEs a non-automated path; required trust and support channel                        | none                                                   | “contact transcrypt”, “support for cyber essentials readiness”                 |
| Why Transcrypt                        | Differentiation vs status quo and alternatives                 | Marketing | MKT.Why.Landing            | From home, features, compare; onward → /compare, /how-it-works, /waitlist                        | `/why`                                | Type: Landing; ContentGroup: Positioning            | Makes the “why now / why this” case explicit                                               | next-best-step, research-highlight, starter-kit-promo  | “why cyber essentials prep tool”, “transcrypt vs consultant”                   |
| Security Overview                     | High-level security posture, controls, assurances              | Marketing | MKT.Security.Overview      | From footer, about, status; links → legal, responsible disclosure                                | `/security`                           | Type: Static; ContentGroup: Security                | Required for trust and vendor assessment; feeds security-conscious buyers                  | related-stories, research-highlight                    | “security of transcrypt”, “SaaS security posture for SMEs”                     |
| Case Studies (Index)                  | Lists all case studies                                         | Marketing | MKT.CaseStudies.Index      | From nav, home; rows link to individual case studies                                             | `/case-studies`                       | Type: Index; ContentGroup: CaseStudies              | Aggregates proof stories; supports evaluation and risk-averse owners                       | related-stories, next-best-step                        | “cyber essentials case study”, “sme compliance success stories”                |
| Case Study (Template)                 | Individual SME narrative with problem → outcome                | Marketing | MKT.CaseStudies.Detail     | From index, internal links; CTAs → /waitlist, /starter-kit, /how-it-works                        | `/case-studies/{slug}`                | ContentType: CaseStudy; Industry + Topic tags       | Concrete proof that SMEs like them succeed with the platform                               | next-best-step, for-your-industry, starter-kit-promo   | Long-tail: “[industry] cyber essentials case study”, “how x passed audit”      |
| Blog Landing / Overview               | Curated blog entry page, featured content, not just chronology | Marketing | MKT.Blog.Landing           | From nav; links → /blog, categories, state-of report, guides                                     | `/blog/overview`                      | ContentType: BlogHub; Category: Overview            | Gives editorial control over how the blog is presented                                     | research-highlight, related-stories                    | “cyber security blog for SMEs”, “compliance blog”                              |
| Blog Index                            | Chronological index of all posts                               | Marketing | MKT.Blog.Index             | From /blog/overview, header/nav; paginates → /blog/page/{n}                                      | `/blog`                               | ContentType: BlogIndex; Category: All               | Standard browse entry for regular readers                                                  | related-stories                                        | Broad discovery; supports crawler coverage and date-focused queries            |
| Blog Article Template                 | Single article view                                            | Marketing | MKT.Blog.Article           | From index, category, tag, search; forward → related posts, guides, starter kit                  | `/blog/{slug}`                        | ContentType: BlogPost; Category + Tags              | Primary vehicle for ongoing expertise and SEO                                              | related-stories, glossary-inline, for-your-industry    | Long-tail expertise queries around security/compliance topics                  |
| Blog Categories Overview              | Lists all blog categories                                      | Marketing | MKT.Blog.CategoriesIndex   | From blog landing/footer; links → /blog/category/{slug}                                          | `/blog/categories`                    | ContentType: TaxonomyIndex; Taxonomy: Category      | Structural view of themes; helps users and search understand content groupings             | none                                                   | “sme security topics”, “cyber essentials blog categories”                      |
| Blog Category Page                    | Category-scoped post list                                      | Marketing | MKT.Blog.Category          | From overview, article links; paginates; back → blog index                                       | `/blog/category/{slug}`               | Taxonomy: Category={slug}; ContentType: BlogListing | Clusters topical content; strong for mid-tail SEO                                          | related-stories                                        | “[topic] blog posts”, themed SME security searches                             |
| Blog Tags Overview                    | Lists all tags (curated, not junk)                             | Marketing | MKT.Blog.TagsIndex         | From taxonomy UI; links → /blog/tag/{slug}                                                       | `/blog/tags`                          | Taxonomy: TagIndex; ContentType: Utility            | Controlled view of tag space; avoids opaque WordPress-style sprawl                         | none                                                   | “sme cyber glossary tags”, internal join page for bots and power users         |
| Blog Tag Page                         | Tag-scoped post list                                           | Marketing | MKT.Blog.Tag               | From article tag chips, tags overview; paginates                                                 | `/blog/tag/{slug}`                    | Taxonomy: Tag={slug}; ContentType: BlogListing      | Cross-cut views across topics; good for emergent themes                                    | related-stories                                        | Long-tail around specific issues: “password hygiene for SMEs”, etc             |
| Blog Author Page                      | Posts by a given author                                        | Marketing | MKT.Blog.Author            | Linked from article bylines; onward to posts and guides                                          | `/blog/author/{slug}`                 | Taxonomy: Author={slug}; ContentType: Listing       | Builds personal authority; supports Paula / Brian / guest expert branding                  | related-stories                                        | “[author name] security articles”, author-centric discovery                    |
| Blog Search                           | Keyword search results                                         | Marketing | MKT.Blog.Search            | From header search; paginates; links to posts, guides                                            | `/blog/search`                        | ContentType: Search; Taxonomy: none                 | Core discovery tool; prevents content from becoming unfindable as volume grows             | related-stories                                        | Captures wide natural language queries against entire corpus                   |
| Blog Pagination                       | Subsequent pages of index                                      | Marketing | MKT.Blog.IndexPaged        | From /blog; next/prev within blog index                                                          | `/blog/page/{n}`                      | Same as Blog Index                                  | Technical necessity to control scroll depth and crawl; keeps IA orderly                    | none                                                   | Same as /blog; supports proper indexing of older posts                         |
| Blog Category Pagination              | Paged category results                                         | Marketing | MKT.Blog.CategoryPaged     | From category pages; next/prev navigation                                                        | `/blog/category/{slug}/page/{n}`      | Same as Blog Category                               | Allows controlled division of large categories; keeps UX manageable                        | none                                                   | Same as category; ensures deep content indexed                                 |
| Blog Tag Pagination                   | Paged tag results                                              | Marketing | MKT.Blog.TagPaged          | From tag pages; next/prev navigation                                                             | `/blog/tag/{slug}/page/{n}`           | Same as Blog Tag                                    | Same as category pagination but along tag dimension                                        | none                                                   | Same as tag page; supports long-tail crawl                                     |
| Blog Search Pagination                | Paged search results                                           | Marketing | MKT.Blog.SearchPaged       | Within search context; next/prev                                                                 | `/blog/search/page/{n}`               | SearchContext; no taxonomy                          | Allows full result exploration without infinite scroll                                     | none                                                   | Same as /blog/search; keeps search UX usable                                   |
| Blog Date Archive (Year)              | Year-scoped archive                                            | Marketing | MKT.Blog.YearArchive       | From blog filters; links to posts & month archives                                               | `/blog/{yyyy}`                        | ArchiveDim: Year                                    | Conventional browse and historical context; some people think chronologically              | related-stories                                        | “cyber security articles 2025”, “historical SME cyber content”                 |
| Blog Date Archive (Month)             | Month-scoped archive                                           | Marketing | MKT.Blog.MonthArchive      | From year archive; links to posts                                                                | `/blog/{yyyy}/{mm}`                   | ArchiveDim: Year+Month                              | More granular chronological discovery; acceptable because content is curated, not autojunk | related-stories                                        | Same as year archive, finer time resolution                                    |
| Guides Index                          | Entry to structured, evergreen guides                          | Marketing | MKT.Guides.Index           | From nav, CTAs in blog, starter kit, compare; onward → guide articles                            | `/guides`                             | ContentType: GuideIndex; Category: All              | Curated high-value longform content; more structured than blog                             | research-highlight, next-best-step                     | “cyber essentials guide”, “sme cyber compliance guide”                         |
| Guide Article Template                | Single guide                                                   | Marketing | MKT.Guides.Article         | From guides index, resources, blog; cross-links to related guides and starter kit                | `/guides/{slug}`                      | ContentType: Guide; Category + Topic tags           | Deep, evergreen content; strongly supports authority and organic acquisition               | related-stories, glossary-inline, starter-kit-promo    | Long-tail how-to searches around readiness and implementation                  |
| Guides Categories Overview            | Lists guide categories                                         | Marketing | MKT.Guides.CategoriesIndex | From guides index; links to category pages                                                       | `/guides/categories`                  | Taxonomy: GuideCategoryIndex                        | Exposes major guide themes at a glance; supports IA clarity                                | none                                                   | “cyber essentials guides”, category-level SEO                                  |
| Guide Category Page                   | Guide list for a category                                      | Marketing | MKT.Guides.Category        | From overview, internal links; lists guides under theme                                          | `/guides/category/{slug}`             | Taxonomy: GuideCategory={slug}                      | Clusters related guides; improves discoverability for focused initiatives                  | related-stories                                        | “[topic] guide for SMEs”, “password policy guide”                              |
| Resource Library                      | Hub for PDFs, templates, checklists                            | Marketing | MKT.Resources.Index        | From nav, CTAs in content; resource tiles → download pages                                       | `/resources`                          | ContentType: ResourceIndex; ResourceType: Mixed     | Central catalogue of lead magnets; key for waitlist / newsletter conversion                | starter-kit-promo, next-best-step                      | “cyber essentials templates”, “compliance checklist download”                  |
| Resource Download                     | Individual resource download surface                           | Marketing | MKT.Resources.Detail       | From library; triggers email capture / confirmation flows; returns to confirmation               | `/resources/{slug}`                   | ContentType: Resource; Topic + Format tags          | Concrete value delivery in exchange for contact intent                                     | next-best-step, starter-kit-promo                      | Asset-specific searches, e.g. “incident response template SME”                 |
| Resource Download Confirmation        | Confirmation / thank you page                                  | Marketing | MKT.Resources.Thanks       | From download action; onward → related content, starter kit, newsletter                          | `/resources/{slug}/thanks`            | Context: Resource; no taxonomy                      | Closes the loop properly; perfect place to weave the mesh (blog/guides/waitlist)           | next-best-step, related-stories                        | Minimal SEO, but can capture “[name] template downloaded” brand queries        |
| Waitlist                              | Core early-access signup                                       | Marketing | MKT.Conv.Waitlist          | From CTAs across site; submits → confirmation                                                    | `/waitlist`                           | ContentType: Conversion; Goal: EarlyAccess          | Central Phase-1 KPI; primary commitment route before app opens                             | none (keep focused), research-highlight                | “transcrypt waitlist”, “cyber essentials early access”                         |
| Waitlist Confirmation                 | Thank-you + next steps                                         | Marketing | MKT.Conv.WaitlistThanks    | From waitlist submit; onward → blog, guides, starter kit                                         | `/waitlist/thanks`                    | Context: Waitlist; no taxonomy                      | Reassures user, sets expectation; good place for soft cross-links                          | next-best-step, related-stories                        | Light SEO; mostly UX / brand reassurance                                       |
| Newsletter Signup                     | Subscription to ongoing updates                                | Marketing | MKT.Conv.Newsletter        | From footer/partials; submit → confirm/thanks                                                    | `/newsletter`                         | ContentType: Conversion; Goal: Newsletter           | Secondary Phase-1 capture channel; supportive but less critical than waitlist              | none                                                   | “transcrypt newsletter”, “sme cyber newsletter”                                |
| Newsletter Confirmation               | Double-opt-in confirmation                                     | Marketing | MKT.Conv.NewsletterConfirm | From email or submit; onward → thanks / content                                                  | `/newsletter/confirm`                 | Context: Newsletter; no taxonomy                    | Compliance and trust step; prevents bad lists                                              | next-best-step                                         | Negligible SEO, mostly operational                                             |
| Newsletter Thanks                     | Final thank-you page                                           | Marketing | MKT.Conv.NewsletterThanks  | From confirmation; onward → blog, guides, starter kit                                            | `/newsletter/thanks`                  | Context: Newsletter                                 | Tidy close; good point for editorial recommendations and starter kit promotion             | related-stories, starter-kit-promo                     | Minimal SEO; primarily UX                                                      |
| Privacy Policy                        | Legal privacy statement                                        | Marketing | LEG.Privacy                | From footer/legal links; rarely forward except to DPA / subprocessors                            | `/privacy`                            | ContentType: Legal; Jurisdiction: UK/EU             | Regulatory requirement; vendor due-diligence anchor                                        | none                                                   | Legal keywords around “privacy policy”, “data processing”                      |
| Terms of Service                      | Contractual usage terms                                        | Marketing | LEG.Terms                  | From footer; occasionally linked from pricing / signup                                           | `/terms`                              | ContentType: Legal                                  | Defines use, liabilities, and rights; required for SaaS                                    | none                                                   | “terms of service transcrypt”                                                  |
| Cookie Policy                         | Explains cookie usage                                          | Marketing | LEG.Cookies                | From footer and cookie banner                                                                    | `/cookies`                            | ContentType: Legal                                  | Regulatory compliance; cookie consent justification                                        | none                                                   | “cookie policy”, “cookie usage for website”                                    |
| Accessibility Statement               | Accessibility commitment and status                            | Marketing | LEG.Accessibility          | From footer; no special transitions                                                              | `/accessibility`                      | ContentType: Legal/Trust                            | Standard for quality SaaS; especially for public-sector adjacent customers                 | none                                                   | Some minor SEO; mostly compliance / RFP box-ticking                            |
| Responsible Disclosure                | Security vulnerability disclosure policy                       | Marketing | SEC.Disclosure             | Linked from security, footer; may link to email/PGP                                              | `/security/disclosure`                | ContentType: SecurityPolicy                         | Essential for credible security posture; signals maturity                                  | none                                                   | “responsible disclosure policy”, “report vulnerability”                        |
| Acceptable Use Policy                 | Defines acceptable customer behaviours                         | Marketing | LEG.AUP                    | Linked from terms / signup                                                                       | `/aup`                                | ContentType: Legal                                  | Supports abuse handling; important for incident / account actions                          | none                                                   | Standard legal SEO                                                             |
| Subprocessors List                    | Lists data subprocessors                                       | Marketing | LEG.Subprocessors          | From privacy / DPA; links to vendor sites                                                        | `/subprocessors`                      | ContentType: Legal/Trust                            | Required by many organisations before sign-off                                             | none                                                   | “subprocessors list”, “where is data processed”                                |
| Data Protection Addendum (Public)     | DPA view for prospects                                         | Marketing | LEG.DPA                    | From privacy, pricing, security; downloadable version may be linked                              | `/dpa`                                | ContentType: Legal                                  | Lets procurement / legal assess DPA before contract                                        | none                                                   | “data processing agreement”, “dpa for transcrypt”                              |
| Status Page (Public)                  | Current service health + history                               | Marketing | OPS.Status                 | From footer/security; no forward transitions except back to docs                                 | `/status`                             | ContentType: OperationalStatus                      | Required for transparency; signals reliability                                             | research-highlight (optional light usage)              | “system status transcrypt”, “uptime”, “incident history”                       |
| Comparison Hub                        | Entry to all comparison pages                                  | Marketing | MKT.Compare.Hub            | From features, pricing, why; onward → individual comparisons                                     | `/compare`                            | ContentType: ComparisonIndex                        | Sits between abstract features and concrete decision; helps buyers evaluate options        | next-best-step, research-highlight                     | “transcrypt vs alternatives”, “compliance software comparison”                 |
| Compare vs Traditional Consultancy    | Compares Transcrypt vs manual consultant approach              | Marketing | MKT.Compare.Consultancy    | From hub, features, why; CTAs → /pricing, /how-it-works, /starter-kit                            | `/compare/consultancy`                | ContentType: Comparison; Topic: Consultancy         | Addresses main incumbent solution; shapes cost/effort expectations                         | next-best-step, starter-kit-promo                      | “cyber essentials consultant vs software”, “consultant vs platform”            |
| Compare vs Self-Assessment            | Compares Transcrypt vs unguided self-assessment                | Marketing | MKT.Compare.SelfAssess     | From hub, guides; CTAs → /starter-kit, /guides, /waitlist                                        | `/compare/self-assessment`            | ContentType: Comparison; Topic: SelfAssessment      | Speaks directly to DIY SMEs; shows risk and toil of doing everything alone                 | next-best-step, starter-kit-promo                      | “cyber essentials self assessment help”, “self assessment vs tool”             |
| How It Works                          | High-level visual explanation of workflow                      | Marketing | MKT.HowItWorks             | From home, features, compare; onward → /waitlist (P1), /signup (P2), /guides                     | `/how-it-works`                       | ContentType: Explainer; Topic: Workflow             | Bridges marketing promises and product reality; de-mystifies journey                       | next-best-step, glossary-inline, for-your-industry     | “how cyber essentials platform works”, “workflow for readiness”                |
| Industries Overview                   | Lists supported industries                                     | Marketing | MKT.Industries.Index       | From nav/features; onward → each industry page                                                   | `/industries`                         | Taxonomy: IndustryIndex                             | Lets you speak differently to healthcare/retail/etc.; maps product to contexts             | for-your-industry, related-stories                     | “[industry] cyber essentials solution”, “sector-specific security”             |
| Industry Landing Template             | Industry-specific landing                                      | Marketing | MKT.Industries.Detail      | From industries index, campaigns; onward → guides, case studies, waitlist                        | `/industries/{slug}`                  | Taxonomy: Industry={slug}; ContentType: Landing     | Speaks directly to vertical pain; critical for future targeted campaigns                   | for-your-industry, related-stories, next-best-step     | “[industry] cyber compliance”, “[industry] cyber essentials readiness”         |
| Glossary                              | A–Z glossary of key terms                                      | Marketing | MKT.Glossary.AtoZ          | From content hovers/links, footer; anchors within page                                           | `/glossary`                           | ContentType: Glossary; Terms as anchors             | Central reference; supports plain-English explanations; underpins glossary-inline partial  | glossary-inline                                        | “cyber essentials glossary”, “security terms explained for SMEs”               |
| Starter Kit                           | Bundle page for key templates/resources                        | Marketing | MKT.StarterKit.Landing     | From CTAs in compare, guides, blog; onward → individual resources / waitlist                     | `/starter-kit`                        | ContentType: Bundle; ResourceGroup: StarterKit      | High-value lead magnet; turns passive readers into serious evaluators                      | next-best-step, starter-kit-promo                      | “cyber essentials starter kit”, “compliance starter pack download”             |
| Roadmap                               | High-level roadmap / future direction                          | Marketing | MKT.Roadmap.Static         | From features, about; no direct CTAs besides content links                                       | `/roadmap`                            | ContentType: Roadmap                                | Indicates active development and direction without over-committing                         | roadmap-teaser                                         | “product roadmap”, “future of transcrypt”                                      |
| State of SME Cybersecurity Report Hub | Hub for periodic “State of” reports                            | Marketing | MKT.Reports.StateOfSME     | From blog/guides, research highlight partial; onward → report download, related posts            | `/reports/state-of-sme-cybersecurity` | ContentType: ResearchReport; Topic tags             | Big authority anchor; supports PR, backlinks, and deep trust                               | research-highlight, starter-kit-promo, related-stories | “state of sme cyber security”, “sme cyber report”, strong authority term       |

---

### **B.2 Phase 2 — Essentials (Product Runtime)**

| Page Name                    | Purpose                                             | Runtime    | Template Ref               | Allowed Transitions (Summary)                                                  | URL Pattern                      | Taxonomy Assignment                  | Rationale                                                                     | Possible Partials                 | SEO Intent                                        |
| ---------------------------- | --------------------------------------------------- | ---------- | -------------------------- | ------------------------------------------------------------------------------ | -------------------------------- | ------------------------------------ | ----------------------------------------------------------------------------- | --------------------------------- | ------------------------------------------------- |
| Log In                       | Entry to authenticated Essentials                   | Essentials | APP.Auth.Login             | From marketing CTAs; forward → intake/evidence dashboard based on state        | `/auth/login`                    | Type: Identity; Context: Entry       | Core security boundary; mandatory to protect tenant data                      | none                              | Minimal SEO; more direct navigation / bookmarks   |
| Password Reset Request       | Initiate password reset                             | Essentials | APP.Auth.ResetRequest      | From login “forgot password”; forward → reset confirm email link               | `/auth/reset`                    | Type: IdentityFlow                   | Standard account recovery; required for any credential-based login            | none                              | Minimal SEO; operational only                     |
| Password Reset Confirm       | Complete password reset                             | Essentials | APP.Auth.ResetConfirm      | From email link; forward → login                                               | `/auth/reset/{token}`            | Type: IdentityFlow                   | Secure completion of reset; ensures tokens are used in controlled manner      | none                              | None; internal action page                        |
| Signup Start                 | Start paid onboarding (account + subscription path) | Essentials | APP.Signup.Start           | From pricing/how-it-works CTAs (Phase 2); forward → verify, checkout           | `/signup`                        | Type: Onboarding; Context: OrgOwner  | Entry to paid, non-trial subscription; core revenue gateway                   | none (keep focused)               | “sign up transcrypt”, but largely navigational    |
| Signup Email Verification    | Collects / verifies email as part of signup         | Essentials | APP.Signup.VerifyEmail     | From signup; sends verification; forward from email → verified page            | `/signup/verify`                 | IdentityFlow; EmailVerification      | Ensures address control and reduces fraud / mis-address                       | none                              | Not SEO; purely operational                       |
| Signup Email Verified        | Confirms verified email, continues onboarding       | Essentials | APP.Signup.Verified        | From email link; forward → checkout                                            | `/signup/verified`               | IdentityFlow; Context: PostVerify    | Closes loop on email verification and advances user                           | none                              | None; operational                                 |
| Subscription Checkout        | Payment capture and subscription creation           | Essentials | APP.Signup.Checkout        | From verified; forward → signup complete                                       | `/signup/checkout`               | BillingFlow; Plan=Essentials         | Core revenue point; links tenant identity to billing                          | none                              | Not SEO; highly sensitive billing page            |
| Onboarding Complete          | Confirms subscription active, routes to intake      | Essentials | APP.Signup.Complete        | From checkout; forward → /app/intake or /app/evidence                          | `/signup/complete`               | OnboardingComplete                   | Single clear handoff from signup world to operational Essentials              | none                              | None; post-payment UX only                        |
| Organisation Setup (Initial) | First-time intake of organisation context           | Essentials | APP.Intake.Initial         | From onboarding complete or login if no intake; forward → org details/evidence | `/app/intake`                    | Type: Intake; Entity=Organisation    | Gathers minimal data to shape evaluation and scope                            | none                              | Not SEO; internal tenant-scoped                   |
| Organisation Details (Edit)  | Ongoing management of org metadata                  | Essentials | APP.Intake.OrgDetails      | From nav/settings; stays within intake/evidence context                        | `/app/org`                       | Type: Intake; Entity=Organisation    | Keeps core data current; used for dynamic logic                               | none                              | None; only for logged-in users                    |
| Evidence Dashboard           | Overview of all evidence requirements and statuses  | Essentials | APP.Evidence.Dashboard     | From nav or post-intake; forward → per-control evidence pages                  | `/app/evidence`                  | Type: EvidenceOverview               | Single pane to manage progress across controls                                | none                              | No SEO; operational                               |
| Evidence Submission          | Submit/update evidence for a specific control       | Essentials | APP.Evidence.Submit        | From dashboard/evaluation; forward → review or back to dashboard               | `/app/evidence/{control}`        | Type: EvidenceItem; Control={id}     | Core of readiness workflow; without it the product has no function            | none                              | None; deeply tenant-specific                      |
| Evidence Review              | Structured review of evidence for a control         | Essentials | APP.Evidence.Review        | From evidence submit; forward → evaluation progression                         | `/app/evidence/{control}/review` | Type: EvidenceReview; Control={id}   | Enables user to see status vs expectations before evaluation                  | none                              | None                                              |
| Evaluation Overview          | High-level view of evaluation status and scores     | Essentials | APP.Eval.Overview          | From nav or evidence dashboard; forward → steps and report                     | `/app/evaluation`                | Type: EvaluationOverview             | Gives user clarity of where they are in the readiness journey                 | none                              | None                                              |
| Evaluation Step              | Guided step for a subset of controls or section     | Essentials | APP.Eval.Step              | From overview or previous step; forward/back between steps, onward → complete  | `/app/evaluation/{step}`         | Type: EvaluationStep; Step={id}      | Breaks work into coherent chunks; improves psychological and UX manageability | none                              | None                                              |
| Evaluation Complete          | Confirmation of evaluation run; next actions        | Essentials | APP.Eval.Complete          | From final step; forward → report view, evidence dashboard                     | `/app/evaluation/complete`       | Type: EvaluationResult               | Provides a clear milestone before showing report; avoids jarring jump         | next-best-step (internal flavour) | None; internal                                    |
| Report View                  | Rendered readiness report                           | Essentials | APP.Report.View            | From eval complete or overview; forward → download, back to dashboard          | `/app/report`                    | Type: Report; Scope=Tenant           | Delivers the value: structured view of readiness for the SME                  | none                              | None; could mirror marketing copy but not indexed |
| Report Download              | Download report (PDF/HTML)                          | Essentials | APP.Report.Download        | From report view; returns to view or OS download                               | `/app/report/download`           | Context: ReportDownload              | Gives portable artefact for sharing with auditors/insurers                    | none                              | None; mostly binary interaction                   |
| Billing Dashboard            | Overview of subscription state and billing details  | Essentials | APP.Billing.Overview       | From nav/settings; forward → subscription mgmt, payment methods, history       | `/app/billing`                   | Type: BillingOverview                | Central billing control; supports trust and autonomy                          | none                              | None                                              |
| Subscription Management      | Change plan, cancel, renew                          | Essentials | APP.Billing.Subscription   | From billing dashboard; forward → confirmation or checkout                     | `/app/billing/subscription`      | Type: BillingPlan                    | Critical for self-service; reduces support friction                           | none                              | None                                              |
| Payment Methods              | Manage cards/payment instruments                    | Essentials | APP.Billing.PaymentMethods | From billing dashboard or subscription flow; back → billing                    | `/app/billing/payment-methods`   | Type: BillingPayment                 | Required for updating expired cards; supports uninterrupted service           | none                              | None                                              |
| Billing History / Invoices   | List of invoices and receipts                       | Essentials | APP.Billing.History        | From billing dashboard; optionally link to invoice PDFs                        | `/app/billing/history`           | Type: BillingHistory                 | Supports finance/audit; addresses “paper trail” concerns                      | none                              | None                                              |
| User Profile                 | User-level settings (name, email, locale)           | Essentials | APP.Settings.Profile       | From settings; limited onward transitions within settings                      | `/app/settings/profile`          | Type: Settings; Entity=User          | Required to keep contact details & preferences accurate                       | none                              | None                                              |
| Security Settings            | Password, MFA, security options                     | Essentials | APP.Settings.Security      | From settings; onward → auth flows (MFA) or login                              | `/app/settings/security`         | Type: Settings; Domain=Security      | Critical for security posture and regulatory expectations                     | none                              | None; internal only                               |
| Notification Preferences     | Choose what emails/alerts are sent                  | Essentials | APP.Settings.Notifications | From settings; saves preferences; back to settings                             | `/app/settings/notifications`    | Type: Settings; Domain=Notifications | Reduces noise, improves satisfaction; future-proofs rule-based alerts         | none                              | None                                              |
| Organisation Profile         | Org-wide settings: legal name, addresses, contact   | Essentials | APP.Settings.Org           | From settings; interacts with billing, report headers                          | `/app/settings/org`              | Type: Settings; Entity=Organisation  | Keeps identity details coherent across billing, reports, and evidence         | none                              | None                                              |



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

## **Appendix D — Cross-Referential Partials (Skeletal)**

This appendix records the cross-page partials used to create a governed mesh between Marketing, Blog, Guides, and Resource surfaces. It defines what the partials are, why they exist, and where they may appear. Entries will expand once Appendix B (Page Inventory) is finalised.

### **D.1 Partial Definitions**

The following partials have been defined so far:

* Next Best Step
* Related Stories / Articles
* For Your Industry
* Glossary Inline / Key Terms
* Starter Kit Promo
* Roadmap Teaser
* Research Highlight (State-of SME)

### **D.2 Placement Rules**

Defines where each partial is permitted or prohibited.
(To be populated once the final sitemap is fixed.)

### **D.3 Linking Behaviour**

Describes link destinations, priority rules, and fallback logic.
(To be completed after Appendix B stabilises.)

### **D.4 Taxonomy Dependencies**

Outlines dependencies on categories, tags, industries, or other taxonomy structures.
(To be finalised after taxonomy is locked.)

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