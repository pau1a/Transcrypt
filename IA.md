# **1. Introduction**

This Information Architecture defines the structural model of Transcrypt across the Marketing runtime and the Essentials application. It establishes how the system’s surfaces are organised, how users move between them, and how meaning, hierarchy, and navigability are maintained. The IA sits beneath the behavioural rules in the PDS and the architectural constraints in the SAIS, ensuring every page, path, and transition reflects the product intent described in the PRD. The PDS must treat this IA as authoritative for all navigation tiers, page roles, and structural relationships. No component pattern in the PDS may introduce new navigation categories, alter hierarchy, or reinterpret footer or utility links without this IA being updated first. This document provides the skeletal framework that governs structure, discoverability, and user flow, forming the basis for coherent design, consistent routing, and predictable interaction across the entire platform.

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

This section defines how users move between surfaces within and across the Marketing and Essentials runtimes. It establishes the global, sectional, workflow, and conditional navigation patterns that govern the entire platform. Navigation must always be predictable, reversible, and free of ambiguity. The rules in this section ensure that movement respects hierarchical structure (§4), deterministic workflow boundaries (PDS, SAIS), and the runtime separation model defined in §2. Lateral, non-hierarchical cross-links—such as contextual discovery surfaces—are implemented only through governed partials defined in Appendix D and must never interfere with core navigation behaviour.
The PDS is responsible for implementing the visual and interaction patterns for these navigation tiers, but it may not redefine them. Any header, rail, tab set, or footer construct described in the PDS must be traceable to a Primary, Section, or Utility/Footer tier defined in this IA, and to the page roles and hierarchy described in §2 and §4. If a new navigation behaviour is required, this IA must be updated first and then reflected in the PDS.
In addition to primary and secondary navigation, the platform exposes a third tier: utility/footer navigation. This tier provides access to legal, trust, operational, and subscription-adjacent surfaces (for example privacy, terms, cookies, subprocessors, status, newsletter) without altering hierarchy or workflow. Utility/footer links are defined by the Utility/Footer tier in Appendix B3 and their layout is specified in Appendix A. They must never be treated as secondary navigation and must not participate in workflow or runtime transitions beyond simple, stateless page loads.

## **3.1 Primary Navigation**

Primary navigation defines the top-level frame through which users access major sections of the platform. It is runtime-specific, non-ambiguous, and stable across all Marketing surfaces. Essentials surfaces use their own constrained primary frame that exposes only authorised, task-driven areas. The two runtimes never share a unified navigation bar, preventing expressive Marketing affordances from leaking into deterministic workflows.

Primary navigation must:

* reflect the structural hierarchy defined in §4 without implying pages outside the user’s current runtime
* expose only surfaces whose access conditions, state requirements, and transitions are valid for the user’s context
* maintain full reversibility—users must always be able to return to any previously accessed top-level section without relying on browser behaviours
* remain visually consistent and predictable across all Marketing surfaces, and strictly minimal and state-bound in Essentials
* avoid decorative or suggestive elements; affordances must indicate genuine navigability
* never embed lateral discovery patterns (e.g., “Related Stories,” “For Your Industry”); these are governed exclusively by the partials catalogue in Appendix D and must not appear in primary nav
* degrade predictably on narrow viewports without hiding or reinterpreting structural truth

Some surfaces appear both in primary navigation and in utility/footer regions (for example Contact, selected legal pages, or Status). In these cases, the primary navigation entry is the structural anchor described in §4, and the utility/footer entry is a convenience duplicate only. Utility/footer links must never introduce new primary items, must not circumvent runtime boundaries, and must not present themselves as part of the primary navigation frame.

Primary navigation establishes a clear, trustworthy frame for movement across the platform, ensuring that users can reliably orient themselves regardless of content depth, workflow state, or device.

---

## **3.2 Secondary Navigation**

Secondary navigation (Nav Tier: **Section** in Appendix B3) provides intra-section movement within a defined structural parent. It operates under primary navigation and never competes with it. Where primary navigation exposes the major sections of each runtime, secondary navigation exposes the local spine of a given section (for example within Guides, Blog, Evidence, Billing, or Settings) without altering runtime boundaries or implying new hierarchies. Utility/footer links are not secondary navigation and are governed separately via the Utility/Footer tier in Appendix B3.

Secondary navigation must:

* be scoped to a single structural parent as defined in §4 and Appendix B3 (for example `/guides`, `/blog`, `/app/evidence`, `/app/billing`)
* expose only siblings or direct descendants of that parent whose Nav Tier in Appendix B3 is **Section**
* never include cross-section or cross-runtime links; those are handled by primary navigation, contextual links, or governed partials
* visually read as subordinate to primary navigation in every layout defined in Appendix A and the PDS
* preserve reversibility within the section so users can always return to the sectional entry surface without relying on browser controls
* avoid acting as a workflow controller—deterministic progress is owned by workflow navigation in §3.3, not by secondary menus

In the **Marketing runtime**, secondary navigation is used to reveal structure within content-heavy sections such as Blog, Guides, Resources, Industries, and Comparisons. It may appear as horizontal tabs, vertical side-rails, or in-page sectional menus, provided that:

* the surfaces it exposes remain within the same Marketing section and share the same parent grouping in Appendix B3
* any contextual discovery beyond the section (for example “Related Stories”, “For Your Industry”) is implemented using partials governed by Appendix D and is visually distinct from secondary nav items
* it never suggests access to Essentials, evaluation, or tenant-specific state

In the **Essentials runtime**, secondary navigation is stricter and more constrained. It may appear within Intake, Evidence, Evaluation, Reports, Billing, or Settings, but:

* it can only expose surfaces that are marked as **Section** under the same app cluster in Appendix B3 and that the current user is entitled to access under the state rules in §12
* it must not provide shortcuts that bypass mandatory workflow steps, confirmations, or state transitions defined in §3.3 and §12
* it must not embed Marketing-oriented partials or content-led cross-links; any contextual help in Essentials is deterministic and defined in the PDS, not through Appendix D

Secondary navigation exists solely to make **sectional structure legible**. It may never:

* redefine hierarchy
* cross runtime boundaries
* act as a proxy for workflow progression
* act as a carrier for the lateral mesh that is explicitly governed by the partials in Appendix D
* be conflated with footer or utility navigation, which is handled exclusively through the Utility/Footer tier in Appendix B3.

---

## **3.3 Workflow Navigation**

Workflow navigation controls movement through deterministic, stateful journeys such as signup, intake, evidence submission, evaluation, reporting, and selected billing flows. Unlike primary and secondary navigation, which expose structural surfaces, workflow navigation advances or reverses a user’s position within a defined sequence of steps governed by the SAIS and the Transition Matrix in §12. It is not a separate navigation tier; it is an interaction layer that operates inside the structural framework defined by this IA.

Workflow navigation must:

* exist only where this IA and the PDS define an explicit workflow (for example signup, intake, evidence, evaluation, billing adjustments)
* follow the allowed transitions defined in §12 and the SAIS; it must not introduce new paths that bypass or contradict the Transition Matrix
* respect page roles and hierarchy in §4 and Appendix B (for example step surfaces vs overview surfaces vs completion surfaces)
* present step ordering, current position, and completion state in a way that is unambiguous and reversible
* preserve data integrity when moving forward or backward, with clear rules for draft, save, and discard behaviour (detailed in the PDS)
* honour suppressed navigation rules in §3.4 where critical steps require temporary reduction of escape routes
* be entitlements-aware: only offer forward or backward transitions that the current tenant state and user permissions allow
* remain logically separate from partials in Appendix D; partials may never act as “Next”, “Back”, or “Skip” controls, nor alter workflow state

### **3.3.1 Workflow Navigation in the Marketing Runtime**

In the Marketing runtime, workflow navigation is deliberately minimal. It is limited to short, low-risk flows such as:

* contact and enquiry submissions
* newsletter or other communication opt-ins
* gated resource downloads
* waitlist-style registration flows (where present)

These flows:

* must be linear or near-linear, with a small, finite number of steps
* must not alter tenant-level state; they operate at prospect or lead level only
* may hand off to Essentials via the controlled junctions defined in §2.4 (for example from a “Start Now” or “Sign Up” CTA), but they must not embed Essentials steps or assumptions directly into Marketing pages
* must not rely on primary or secondary navigation to complete the flow; workflow controls are explicit within the surfaces themselves

Where Marketing flows appear to mirror Essentials flows (for example a “guided tour” or “How It Works” walk-through), they must be clearly non-operational demonstrations and must not share state or URLs with the real Essentials workflows.

### **3.3.2 Workflow Navigation in the Essentials Runtime**

In the Essentials runtime, workflow navigation is a core part of the product. It governs:

* signup and onboarding sequences
* intake and organisation setup
* evidence collection and review
* evaluation progression
* report generation and confirmation
* selected billing and subscription changes where multi-step confirmation is required

For these workflows:

* every step surface must be listed in Appendix B (Phase 2 – Essentials) and classified appropriately in §4 (for example parent overview, step surface, completion surface)
* allowed transitions between steps, overviews, and completion surfaces must be explicitly represented in the Transition Matrix in §12; workflow navigation may not create ad hoc shortcuts
* “Next”, “Back”, “Skip”, and similar controls must map one-to-one to valid transitions; any disabled control must correspond to a forbidden or not-yet-available transition
* primary and secondary navigation may be present but must not allow users to bypass mandatory steps, confirmations, or gating conditions; where necessary, §3.4 suppression rules apply
* recovery behaviour (for example resuming a partially completed evaluation) must route the user to a stable, well-defined step or overview surface, as described in §3.6

Workflow navigation in Essentials is deterministic by design: given the same tenant state, role, and step, the set of available transitions and their effects must be identical every time. Any change to the order of steps, available transitions, or completion criteria requires an update to this IA, the Transition Matrix in §12, and the corresponding implementation detail in the PDS and SAIS.

---

## **3.4 Suppressed Navigation States**

Suppressed navigation states are deliberate, temporary reductions of the normal navigation frame. They remove or limit access to Primary, Section (secondary), and/or Utility/Footer navigation on specific surfaces to prevent unsafe escape routes during high-risk, stateful operations. Suppression is never cosmetic; it is a control measure used to protect data integrity, financial actions, or irreversible workflow steps.

Suppressed navigation is **not** a fourth nav tier. It is a conditional mode applied to existing tiers under tightly defined conditions.

### **3.4.1 What Counts as Suppression**

A surface is considered to be in a suppressed navigation state if, compared to its normal template in Appendix A:

* the primary navigation is removed, disabled, or replaced by a reduced shell
* sectional (secondary) navigation is removed or materially reduced
* utility/footer links are removed or materially reduced beyond normal responsive/mobile behaviour
* escape routes that would normally move the user out of the current workflow or structural parent are intentionally withheld

Normal responsive behaviour (collapsing a header into a burger, moving footer items into a drawer) is defined in §3.5 and the PDS and does **not** count as suppression on its own. Suppression is a structural choice, not a viewport side-effect.

### **3.4.2 When Suppression Is Allowed**

Navigation suppression is allowed only for high-risk operations where a full frame of navigation would materially increase the chance of:

* incomplete, inconsistent, or corrupted state
* financial or subscription changes being applied incorrectly
* irreversible workflow actions being taken unintentionally
* security posture being weakened (for example mid-auth flows)

Typical allowed scenarios include:

* **Identity and authentication flows**
  Login, password reset, and multi-factor enrolment/verification where exposing full app navigation would be misleading or unsafe.

* **Critical billing and subscription steps**
  Final confirmation of plan changes, payment method updates that affect future billing, or cancellation flows where escape routes could leave the user in an ambiguous state.

* **Irreversible evaluation or reporting actions**
  Operations that lock evaluation results, freeze evidence for a specific audit cycle, or issue a final readiness report.

* **Evidence operations with destructive potential**
  Limited suppression during destructive edits or deletions where accidental navigation away could lose uncommitted changes.

Suppression must **never** be used simply to “force attention” on marketing copy, to hide alternative navigation for stylistic reasons, or to create dark-pattern traps.

### **3.4.3 Structural Rules for Suppression**

When suppression is applied, the following rules hold:

* **Scope is minimal**
  Suppression is applied to the smallest viable set of surfaces (typically a single step or a short run of steps), not to entire sections or runtimes.

* **Primary vs Section linkage**
  If primary navigation is suppressed for a given surface, secondary navigation that depends on it must not remain as a quasi-primary stand-in. Either:

  * both primary and secondary are suppressed, and workflow controls handle movement; or
  * a reduced shell is present that makes the limited scope obvious.

* **Utility/Footer links**
  Legal and trust obligations must still be met. If footer links are suppressed for regulatory reasons (for example an auth frame controlled by an identity provider), equivalent access to required legal content must exist elsewhere in the journey (for example links on the login page itself or in the hosting Marketing runtime).

* **Clear replacement controls**
  Where suppression removes global escape routes, explicit inline controls must exist: “Cancel”, “Back”, “Return to dashboard”, or equivalent. These controls must map to valid transitions in §12, not ad-hoc redirects.

* **State integrity first**
  Any action that would normally be navigable via primary or secondary nav must either:

  * be temporarily unavailable during the suppressed state; or
  * be reached only by completing or explicitly abandoning the current operation.

Implementation details (for example how suppressed headers render, how modals behave) are defined in the PDS. This IA defines **when** suppression is permitted and what it may and may not remove.

### **3.4.4 Marketing vs Essentials Usage**

In the **Marketing runtime**, suppressed navigation is exceptional. It is limited to:

* short, low-risk forms where primary nav would be visually or cognitively misleading (for example an inline contact overlay), and
* frames controlled by third-party identity or consent tooling, where Transcrypt cannot safely render the full navigation shell.

Marketing suppression must not hide access to core informational, legal, or trust surfaces and must never create pseudo-“app-like” flows that mimic Essentials.

In the **Essentials runtime**, suppression is more common but must still be tightly scoped:

* identity, password, and MFA flows may run with reduced navigation
* critical billing, evaluation, and evidence operations may temporarily narrow escape routes
* complex workflows may suppress primary and secondary nav while a confirmation or irreversible action is in progress

In all cases, suppressed navigation states must:

* correspond to specific surfaces listed in Appendix B (Phase 2)
* have their allowed entry and exit paths explicitly described in the Transition Matrix in §12
* be mirrored in the PDS as specific templates or states, not as ad-hoc component tweaks

Any new proposal to suppress navigation on additional surfaces must update this section, Appendix B, the Transition Matrix in §12, and the PDS.

---

## **3.5 Mobile Navigation Behaviour**

Mobile navigation adapts the presentation of existing navigation tiers to constrained viewports without altering their underlying structure, hierarchy, or meaning. Collapsing, drawers, accordions, or stacked layouts are **responsive treatments**, not new navigation tiers. Mobile patterns must never be used to re-interpret primary navigation as secondary, or to hide the existence of structural sections defined elsewhere in this IA.

Any mobile-specific behaviour is an implementation detail of the PDS. This IA defines what must remain structurally true when screen size changes.

### **3.5.1 Core Principles**

On mobile and other narrow viewports:

* **Structure is invariant**
  All sections exposed in desktop primary navigation must remain reachable on mobile, even if they are presented via different controls (for example a drawer or “More” menu). Responsive hiding of specific components is allowed; removing an entire section from mobile is not.

* **Tiers remain distinct**
  Primary, Section (secondary), and Utility/Footer navigation retain their roles. A burger menu, drawer, or sheet is a container for primary or secondary items, not a new tier.

* **No structural lies**
  Mobile cannot present a different hierarchy to desktop (for example, treating a Section item as if it were a primary peer, or burying a primary item inside a random submenu).

* **Responsive ≠ Suppressed**
  Responsive behaviour (collapsing into a menu) is governed here and in the PDS. Structural suppression is governed by §3.4 and must not be triggered purely by viewport size.

### **3.5.2 Primary Navigation on Mobile**

Primary navigation on mobile:

* may collapse into a header menu control (burger, “Menu” button, or equivalent)
* must expose the same primary destinations as desktop, subject only to role-based or state-based access rules, not viewport
* must keep the distinction between runtimes clear; Marketing and Essentials must not appear to share a single unified “mega-menu”
* must make it obvious when the user is opening the **main site/app navigation** versus interacting with local or workflow controls

Where space is tight:

* prioritisation of primary items is allowed (for example a “More” grouping), but **only** if:

  * all primary sections remain reachable within one interaction from the main menu, and
  * their labels are not changed to ambiguous or generic alternatives.

Any mobile-specific animation, gestures, or transitions for primary navigation are defined in the PDS but must not alter which items are considered primary.

### **3.5.3 Secondary (Section) Navigation on Mobile**

Secondary navigation (Section tier):

* may render as:

  * a horizontal chip/tabs strip
  * a vertical rail that becomes an in-page accordion
  * a secondary drawer or nested list inside the main nav shell
* must always be visually and interactionally subordinate to primary navigation, even when both are in drawers or stacked menus
* must continue to expose only the siblings/descendants of its structural parent as defined in §4 and Appendix B

On mobile:

* secondary navigation may be collapsed by default to preserve screen space, but:

  * the user must have a clear way to reveal the section spine, and
  * current location within that spine must remain visible (for example active state, label, or breadcrumb).

Section navigation must not be silently dropped on mobile for structurally complex areas (Blog, Guides, Evidence, Billing, Settings). If the section exists, its local spine must remain discoverable; only the visual pattern may change.

### **3.5.4 Utility and Footer Navigation on Mobile**

Utility/Footer navigation:

* may be:

  * rendered as a stacked list at the bottom of the page
  * folded into a “Legal & Trust” collapsible block
  * partially exposed in a compact footer with a “More” expansion
* must still provide access to all required legal and trust surfaces (Privacy, Terms, Cookies, Accessibility, Subprocessors, DPA, Status, etc.)

On mobile:

* it is acceptable to reduce visual weight (smaller text, collapsible sections), but not to remove mandatory items
* utility/footer links must not be promoted into apparent primary or secondary nav items purely to “fill space” in the header; if a page is utility/footer, its role remains that, regardless of viewport
* any integrations with third-party frames (for example hosted auth or consent views) must ensure that legal obligations remain met even where the standard footer cannot render identically

### **3.5.5 Interaction and State Considerations**

For all runtimes and tiers on mobile:

* **State indicators**
  Current location (active page) must remain clear, even when items live inside drawers or accordions. Users must be able to tell where they are in both the global structure and the section.

* **Workflow vs nav controls**
  Workflow controls (“Next”, “Back”, “Save and exit”) must remain visually distinct from navigation controls, especially when both appear in constrained headers or sticky bars. Mobile layout must not blur the distinction between progressing a workflow and changing section.

* **Consistency across devices**
  A user switching between desktop and mobile should see the same structural options, expressed differently, not a different IA. Differences must be explainable as presentation only.

Any mobile-specific changes that would alter which surfaces are reachable, how tiers are perceived, or how workflow and navigation interact must be reflected here first and then implemented in the PDS.

---

## **3.6 Navigation Fail-Safes**

Navigation fail-safes define how the system behaves when navigation goes wrong: invalid URLs, expired or forbidden transitions, broken links, or users re-entering workflows from bookmarks or history. Fail-safes are the last line of defence to keep users oriented and data safe when the normal Primary, Section, Utility/Footer, and workflow patterns cannot complete as intended.

Fail-safes are **structural guarantees**, not visual flourishes. They constrain where users may be redirected, which surfaces may act as recovery points, and how much context can be preserved without re-creating unsafe states.

### **3.6.1 Core Principles**

All navigation fail-safes obey these principles:

* **No dead ends**
  Users must never be left on a surface from which no valid navigation action is possible. Every user-facing error or recovery surface must provide at least one clear, valid exit.

* **Scope-constrained recovery**
  Recovery should return the user to the closest stable structural parent (section entry, overview, or dashboard) rather than a random “global home”.

* **Runtime integrity**
  Recovery must not silently cross runtimes in ways that violate §2.

  * Marketing errors recover to Marketing entry points.
  * Essentials errors recover to Essentials entry points or dashboards, subject to auth/state.

* **State safety over convenience**
  Where there is a choice between preserving a dubious state and resetting to a safe baseline, the system must choose the safe baseline. Partial state preservation is allowed only when it cannot create contradictions in the Transition Matrix (§12).

* **Predictable patterns**
  The same type of failure must recover in the same way, regardless of entry path (direct URL, bookmark, internal link, or expired session).

### **3.6.2 Invalid or Unknown Routes**

Invalid or unknown routes (for example mistyped URLs, stale bookmarks after IA changes) must resolve to:

* a **runtime-appropriate error surface** (Marketing or Essentials), not a generic “404” that ignores context
* a surface explicitly listed in Appendix B as a recovery page, not an ad-hoc template

For Marketing:

* invalid Marketing URLs route to a Marketing-scoped “Not Found” or “No Longer Available” surface, which:

  * states clearly that the page does not exist
  * offers safe links back to Home, key sections (Blog, Guides, Resources, Pricing), and any relevant category or index pages
  * does not pretend the missing page is still part of the structure

For Essentials:

* invalid Essentials URLs route to an Essentials-scoped recovery surface, which:

  * checks authentication and, if necessary, re-routes via login
  * then returns the user to a stable dashboard or section overview (for example Evidence Dashboard, Evaluation Overview, or App Home)
  * never reconstructs an arbitrary workflow step from an invalid URL

These recovery surfaces must not invent new hierarchy; they are simple, clearly labelled structural exits.

### **3.6.3 Forbidden or Expired Transitions**

Some transitions are structurally valid in the IA but forbidden in specific circumstances (for example lack of entitlement, expired evaluation window, revoked subscription, or partially completed prerequisites). In these cases:

* the system must **not** present broken pages or vague errors
* the user must be redirected to a **stable, allowed surface** that explains the condition in context

Examples:

* Attempt to open `/app/evaluation/{step}` without completing required intake:
  → redirect to Evaluation Overview or Intake surface with a clear statement that prerequisites must be completed.

* Attempt to access billing pages with an inactive or cancelled subscription:
  → redirect to Billing Dashboard or a dedicated subscription recovery surface, not an empty or broken page.

* Attempt to access Essentials surfaces with an expired session:
  → redirect to login, then after auth return to a stable Essentials entry (not to an arbitrary deep link unless that link is still valid under §12).

These behaviours must be aligned with the Transition Matrix in §12; any forbidden state must have a defined recovery mapping.

### **3.6.4 Recovery from Suppressed and Workflow States**

Suppressed navigation states (§3.4) and workflow navigation (§3.3) require tighter guarantees:

* **From suppressed states:**

  * Every suppressed surface must expose explicit recovery controls (for example “Cancel and return to dashboard”, “Back to settings”).
  * If a suppressed surface cannot safely return to the immediate previous state, it must return to a higher-level parent (for example Settings Overview, Evidence Dashboard).

* **From workflow steps:**

  * If a user re-enters a step via bookmark or history and the step is no longer valid (state changed, step removed, prerequisites altered), the system must route them to:

    * the nearest valid step in the same workflow, or
    * the workflow overview or completion surface, with an explanation where necessary.
  * “Save and exit” patterns must always provide a predictable return point (for example Evaluation Overview), which becomes the default recovery destination.

Workflow and suppressed-state recovery surfaces must be explicitly listed in Appendix B and their entry/exit paths captured in the Transition Matrix (§12). They are not generic error pages.

### **3.6.5 Marketing vs Essentials Fail-Safe Patterns**

In the **Marketing runtime**:

* Fail-safes prioritise **orientation and discovery**.
* Recovery surfaces push users toward safe, high-value structural parents: Home, Blog/Guides indexes, Resources, Pricing, or Why Transcrypt.
* No Marketing fail-safe may imply that the user is logged in, changing tenant state, or part-way through a compliance workflow.

In the **Essentials runtime**:

* Fail-safes prioritise **state integrity and auditability**.
* Recovery surfaces favour dashboards and overviews (Evidence, Evaluation, Reports, Billing, Settings) and must maintain clear separation from Marketing.
* Any recovery path that might affect evaluation, evidence, or billing must be reflected in state machine definitions and SAIS runtime rules.

### **3.6.6 User-Level Guarantees**

Across both runtimes, navigation fail-safes must guarantee that:

* Users can always reach:

  * a clear runtime entry (public Home or Essentials entry)
  * a relevant overview/dashboard in Essentials, if authenticated and entitled
* No link, bookmark, or expired state can strand the user indefinitely on a dead surface with no valid exits.
* Any change to IA (new sections, removed pages, updated workflows) is accompanied by updated fail-safe mappings in this section, Appendix B, and §12.

The PDS defines the visual and interaction treatment of fail-safe surfaces (copy, components, tone). This IA defines **which structural exits must exist and when they must be invoked**.

---

## **3.7 Utility and Footer Navigation**

Utility and footer navigation expose a constrained set of links that sit outside the primary and secondary navigation tiers. Their purpose is to provide predictable access to legal, trust, operational, and subscription-adjacent surfaces without altering hierarchy or workflow.

Utility/footer navigation:

* is limited to pages marked as **Utility/Footer** in Appendix B3
* may duplicate certain primary navigation destinations (for example Contact, About, Security, Status) as convenience links, but may not introduce new primary sections
* must not be used to expose section-level spines, workflows, or authenticated-only surfaces
* must not cross runtime boundaries in ways that primary navigation does not already permit
* must render as visually subordinate to both primary and secondary navigation in all layouts defined in Appendix A and the PDS

In the **Marketing runtime**, utility/footer navigation is the canonical location for:

* legal pages (Privacy, Terms, Cookies, Accessibility, Acceptable Use, Data Protection Addendum)
* trust surfaces (Security Overview, Responsible Disclosure, Subprocessors, Status)
* low-friction subscription/communication entry points (Newsletter, non-critical resource links)

In the **Essentials runtime**, utility/footer navigation is minimal. It may expose only:

* required legal and trust links, where jurisdiction or certification demands in-app access
* non-stateful informational surfaces that do not interfere with workflows or tenant context

Utility/footer navigation is never considered **secondary navigation** in this IA. It does not participate in section-level spines, does not express hierarchy, and must not be used to control or represent workflow progression. Its sole role is to provide a stable, low-noise access path to legal, trust, and operational information.

> All footer and utility components described in the PDS must implement these rules rather than reinterpret them. In particular, PDS footer layouts must not:
>
> * present Utility/Footer items as if they were Section (secondary) navigation
> * introduce authenticated or workflow surfaces that do not already appear in this IA
> * create additional navigation tiers beyond Primary, Section, and Utility/Footer
>
> Any requirement to expand footer behaviour or introduce new utility destinations must be reflected in this IA first and then propagated into the PDS.

---

# **4. Page Hierarchy**

This section defines the structural hierarchy of Transcrypt: how surfaces are grouped, which pages act as parents, and how structural weight is assigned. It prevents unnecessary flattening, avoids deep or confusing nesting, and ensures users always understand where they are in the system. Hierarchical groupings here map directly to the templates in Appendix A and the page inventory in Appendix B. Non-hierarchical, lateral connections between surfaces—such as contextual recommendations, industry pivots, or cross-content meshes—are outside the hierarchy and are governed exclusively by the partial mechanisms defined in Appendix D.

## **4.1 Structural Tiers**

Transcrypt’s IA uses a small, fixed set of structural tiers. Every user-facing surface in Appendix B must be assigned to exactly one tier. These tiers describe **where a surface sits in the hierarchy**, not how it is styled or which navigation tier exposes it. Navigation tiers in §3 (Primary, Section, Utility/Footer) are implementations of these structural tiers, not additional levels.

### **4.1.1 Runtime Tier**

The **Runtime Tier** is the top of the hierarchy and divides the platform into:

* the **Marketing runtime** (public, content-led surfaces), and
* the **Essentials runtime** (authenticated, task-driven surfaces).

Every surface belongs to exactly one runtime. No page may exist “between” runtimes, and no navigation pattern may imply a shared blended runtime. All hierarchical diagrams and sitemap views must root at a runtime node before introducing sections or pages.

### **4.1.2 Section Parent Tier**

The **Section Parent Tier** contains the primary structural anchors under each runtime. These are the surfaces that:

* act as the entry point to a coherent area (for example `/blog`, `/guides`, `/resources`, `/compare`, `/industries`, `/case-studies`, `/pricing`, `/why` in Marketing; `/app/evidence`, `/app/evaluation`, `/app/report`, `/app/billing`, `/app/settings`, `/app/intake` in Essentials)
* are eligible to host **secondary (Section) navigation** as defined in §3.2
* commonly appear as the second segment in breadcrumbs after the runtime-level entry.

Section parents define the **main branches of the tree** inside each runtime. The authoritative list of Section Parent surfaces is maintained in Appendix B and cross-labelled in Appendix B3.

### **4.1.3 Cluster / Index Tier**

The **Cluster / Index Tier** groups related content or tasks under a Section Parent without introducing a new top-level branch. Typical examples are:

* indices and listing pages (for example `/blog`, `/blog/categories`, `/guides/categories`, `/resources`, `/case-studies`, `/industries`)
* taxonomy or archive views (for example `/blog/category/{slug}`, `/blog/tag/{slug}`, `/blog/{yyyy}`, `/blog/{yyyy}/{mm}`)
* overview pages inside Essentials (for example Evidence Dashboard, Evaluation Overview, Billing Dashboard).

Cluster/Index surfaces:

* sit directly under a Section Parent in the hierarchy
* provide **structured access** to many child pages or tasks
* do not change the underlying hierarchy; they reflect and expose it.

They may be exposed by primary or secondary navigation depending on their role, but structurally they always remain children of a Section Parent.

### **4.1.4 Content / Task Page Tier**

The **Content / Task Page Tier** contains the main working surfaces of the system:

* individual content pages (blog posts, guides, case studies, industry pages, report hubs, glossary A–Z)
* individual task pages in Essentials (evidence entry for a control, evaluation steps, report view, settings pages, billing detail screens).

These surfaces:

* sit under a Cluster/Index or Section Parent
* are typically the target of search results, internal links, and most external deep links
* carry the primary informational or operational payload for the user.

Content/Task pages may participate in lateral meshes via partials (Appendix D), but those lateral connections do not change their position in the hierarchy.

### **4.1.5 State / Ephemeral Tier**

The **State / Ephemeral Tier** contains short-lived or highly contextual surfaces that exist only as part of a flow:

* confirmations and “thanks” pages (`/resources/{slug}/thanks`, waitlist or newsletter thanks)
* password reset completion, email verification confirmation, signup complete
* download endpoints and other single-purpose state confirmations
* narrow, non-indexed operational views where the URL is incidental to the action.

State/Ephemeral surfaces:

* always sit **under** a Content/Task or Cluster/Index surface in the hierarchy
* are never treated as Section Parents
* must not appear as primary navigation destinations or in generic structural diagrams, even if they have stable URLs.

They may be used as recovery or completion points in the Transition Matrix (§12) but do not introduce new branches into the tree.

---

## **4.2 Sectional Parents**

Sectional Parents are the **Tier-1 anchors** under each runtime. They define the primary structural branches of the system and act as the entry point into coherent areas of content or application behaviour. Every Sectional Parent is a concrete surface listed in Appendix B and is cross-labelled there as a Section Parent; no other surface may claim that role.

Sectional Parents serve three main purposes:

* they are the **first-level children** of a runtime in the hierarchy
* they provide the **attachment point** for Section (secondary) navigation defined in §3.2
* they act as **default structural recovery points** for navigation fail-safes in §3.6

### **4.2.1 Role of Sectional Parents**

A surface qualifies as a Sectional Parent only if it:

* acts as the canonical entry into a logical area (for example Blog, Guides, Resources, Comparisons, Industries in Marketing; Evidence, Evaluation, Reports, Billing, Settings, Intake in Essentials)
* owns a subtree of Cluster/Index and Content/Task pages that inherit its structural context
* is eligible to appear as the second segment in breadcrumbs after the runtime-level entry
* can safely act as a recovery destination for related child pages and workflows (for example returning to Evidence Dashboard from any evidence item)

Sectional Parents do **not** have to be exposed directly in primary navigation, but most will be. Some Sectional Parents may be reached via other anchors (for example an Industries landing discovered from Features), yet structurally they remain Tier-1 nodes under their runtime.

### **4.2.2 Relationship to Appendix B (Page Inventory)**

Appendix B is the authoritative list of all user-facing surfaces. Within that inventory:

* every Sectional Parent is explicitly marked as **Structural Tier: Section Parent**
* each child page references its Sectional Parent as part of its recorded hierarchy
* any change to the set of Sectional Parents (addition, removal, re-scoping) must be reflected in Appendix B before being implemented in navigation or templates

Appendix B3 (Navigation Exposure) further records, for each Sectional Parent:

* whether it is exposed in Primary navigation, Section navigation, Utility/Footer, or only via contextual links
* which Cluster/Index and Content/Task pages sit directly under it in the hierarchy

No page may be treated as a Sectional Parent in navigation, breadcrumbs, or diagrams unless it is recorded as such in Appendix B and Appendix B3.

### **4.2.3 Sectional Parents and Navigation**

Sectional Parents directly constrain how navigation may behave:

* **Primary Navigation (§3.1)**

  * may expose Sectional Parents as top-level items (for example `/blog`, `/guides`, `/resources`, `/app/evidence`, `/app/billing`)
  * must not expose child pages as if they were peers of Sectional Parents, unless an explicit Edge-Case Elevation Rule in §4.5 allows it

* **Secondary (Section) Navigation (§3.2)**

  * may only be mounted within the subtree of a Sectional Parent
  * must treat the Sectional Parent as its root; all items in a given secondary nav spine must be descendants of the same Sectional Parent

* **Utility/Footer Navigation (§3.7)**

  * may link to Sectional Parents (for example `/status`, `/privacy`, `/terms`) but does not change their structural tier
  * must not introduce new Sectional Parents not already defined in this section and Appendix B

* **Fail-Safes and Recovery (§3.6)**

  * when a child page cannot be restored, the preferred recovery destination is its Sectional Parent or a designated Cluster/Index page directly under that parent
  * cross-runtime recovery must never promote a child page to act as a Sectional Parent

Any proposal to create a new major area of the platform (for example a new Guides-like section, a new Essentials module) is, structurally, a proposal to add or rename a Sectional Parent. Such changes must be:

1. recorded in this section;
2. added to Appendix B and Appendix B3; and
3. only then implemented in navigation and templates via the PDS and SAIS.

---

## **4.3 Page-Level Weighting**

Page-level weighting classifies surfaces by **structural importance**, independent of their tier. Two pages may sit at the same structural tier but carry very different weight in terms of navigation exposure, fallback behaviour, and change impact. Every surface in Appendix B must be assigned a single weight class from the set below.

Weight is not a styling hint; it is a structural property that influences how navigation, fail-safes, and future changes are handled.

### **4.3.1 Anchor Pages**

**Anchor** pages are the highest-weight surfaces below the runtime. They:

* act as primary entry or orientation points (for example Home, key Sectional Parents, core dashboards)
* commonly appear in Primary navigation or as canonical “start here” surfaces
* are preferred recovery targets in fail-safe scenarios (§3.6)
* require explicit IA consideration and redirect planning if renamed, relocated, or removed

Typical examples include:

* Marketing: `/` (Home), `/features`, `/pricing`, `/blog` (if treated as the main content anchor), `/guides`, `/resources`, `/industries`, `/case-studies`, `/why`, `/security`
* Essentials: `/app/evidence`, `/app/evaluation`, `/app/report`, `/app/billing`, `/app/settings`, `/app/intake`

Anchor pages usually coincide with Sectional Parents (§4.2), but some high-value Cluster/Index pages may also be classed as Anchor when they function as de facto starting points for journeys.

### **4.3.2 Hub Pages**

**Hub** pages sit one level down from Anchors in importance. They:

* aggregate or organise a meaningful subset of content or tasks under an Anchor or Sectional Parent
* provide structured access to multiple Content/Task pages (for example indices, category lists, dashboards)
* are strong candidates for secondary navigation roots or prominent in-page link blocks
* are common targets for internal links and SEO focus but are not the primary brand or product anchors

Typical examples include:

* Marketing: `/blog/overview`, `/blog/categories`, `/blog/tags`, `/guides/categories`, `/resources`, `/case-studies`, `/industries`, `/compare`, `/reports/state-of-sme-cybersecurity`
* Essentials: Evidence Dashboard, Evaluation Overview, Billing Dashboard, Settings Overview (if implemented as a distinct surface)

When a Hub page changes, the IA, Appendix B, and cross-link mesh in Appendix D must be updated to prevent orphaning large content/task clusters.

### **4.3.3 Standard Pages**

**Standard** pages are the main working surfaces of the system:

* individual articles, guides, case studies, industry pages, resource downloads, glossary A–Z, and similar content surfaces
* individual task pages in Essentials such as evidence entry for a specific control, evaluation steps, report view, and settings subpages

Standard pages:

* sit under Anchors or Hubs within the hierarchy
* are common targets for organic search, internal linking, and user bookmarks
* may be promoted in cross-links or partials, but such promotion does not change their structural tier or weight

Standard pages can be added, evolved, or deprecated with less structural upheaval than Anchors or Hubs, but:

* removals still require redirects and updates to Appendix B
* any Standard page that becomes a persistent navigation or recovery destination may need to be reclassified as Hub or Anchor in a future IA revision.

### **4.3.4 Ephemeral and Utility Pages**

**Ephemeral/Utility** pages are structurally light-weight surfaces that exist to confirm, complete, or support actions rather than to anchor journeys:

* confirmations and “thanks” pages (for example waitlist or newsletter confirmations, `/resources/{slug}/thanks`)
* password reset confirmation, email verification confirmation, signup complete
* narrow operational views such as certain download endpoints or consent confirmations

These pages:

* always sit under a Standard or Hub parent in the hierarchy
* are never exposed in Primary navigation and should not normally appear in breadcrumbs
* may be used as explicit end-points in workflow navigation (§3.3) or the Transition Matrix (§12) but must not act as general-purpose recovery targets for unrelated flows

Ephemeral/Utility pages can be added or removed with minimal IA impact, provided:

* related workflows and transitions are updated in §3.3 and §12
* Appendix B remains accurate and any public URLs are covered by redirects where appropriate.

### **4.3.5 How Weight Interacts with Navigation and Change**

Page weight has direct consequences for navigation and change management:

* **Primary navigation**

  * should favour Anchors, with selected Hubs where justified
  * must not expose Ephemeral/Utility pages as primary items

* **Secondary (Section) navigation**

  * typically roots at a Sectional Parent (often Anchor-weight) and lists Hubs and Standard pages beneath it
  * must not list Ephemeral/Utility pages as peers of Hubs or Standard pages

* **Fail-safes and recovery (§3.6)**

  * when in doubt, recovery should prefer Anchors first, then Hubs, then Standard pages
  * Ephemeral/Utility pages should not be used as recovery destinations except for the specific flows they complete

* **IA changes**

  * changes to Anchors or Hubs require explicit IA, Appendix B, and navigation review
  * Standard and Ephemeral/Utility changes can be handled more locally but still require inventory updates and redirect hygiene

Every page in Appendix B must carry both:

* a **Structural Tier** (from §4.1), and
* a **Weight Class** (Anchor, Hub, Standard, Ephemeral/Utility) from this subsection.

Any proposal to introduce a new weight class must update this section first and then be propagated into Appendix B, navigation rules in §3, and the PDS.

---

## **4.4 Hierarchical Exceptions**

Hierarchical exceptions are surfaces that must exist for the platform to function but do not fit neatly into the standard parent–child patterns described in §4.1–§4.3. They are exceptions **to presentation**, not to structure: every exception is still assigned a Runtime, a Structural Tier, and a Weight Class in Appendix B. This section defines how these pages behave so they cannot be misinterpreted as new branches of the tree or as hidden navigation tiers.

Exceptions fall into a small set of classes: authentication and signup surfaces, search and archive views, glossary anchors and similar pseudo-structure, and legacy/redirect-only URLs.

### **4.4.1 Authentication and Signup Surfaces**

Authentication and signup flows (for example `/auth/login`, `/auth/reset`, `/auth/reset/{token}`, `/signup/...`) are structurally part of the **Essentials runtime**, but they do not behave like normal Sectional Parents, Hubs, or Standard pages.

Rules:

* **Runtime and tier**

  * Always belong to the Essentials runtime.
  * Typically live in the **Cluster/Index** or **State/Ephemeral** tiers, depending on whether they act as a reusable hub (for example login) or a single-use confirmation step (for example `/signup/complete`).

* **Hierarchy and breadcrumbs**

  * Must not appear as Sectional Parents.
  * Normally do **not** appear in breadcrumbs; if breadcrumbs are shown at all in these flows, they should be minimal and non-structural (for example “Sign in → Confirm”).

* **Navigation exposure**

  * May be linked from primary navigation (for example a “Log in” button) but are never treated as peer sections to Evidence, Evaluation, etc.
  * Never host secondary (Section) navigation.
  * Utility/Footer links may appear in a reduced form where required by regulation, but this does not change their structural tier.

* **Appendix B recording**

  * Each auth/signup surface must be explicitly recorded in Appendix B as:

    * Runtime: Essentials
    * Structural Tier: Cluster/Index or State/Ephemeral
    * Weight Class: Hub (for login) or Ephemeral/Utility (for confirmations)
  * Any special navigation suppression behaviours are cross-referenced to §3.4.

Authentication and signup screens are **transit surfaces**, not new IA branches.

### **4.4.2 Search, Archive, and Result Surfaces**

Search and archive views (for example `/blog/search`, `/blog/search/page/{n}`, `/blog/{yyyy}`, `/blog/{yyyy}/{mm}`) expose content that already exists elsewhere in the hierarchy. They provide alternative entry paths but do not create new parents.

Rules:

* **Hierarchy**

  * Belong to the same Runtime and Sectional Parent as the content they expose (for example Blog in Marketing).
  * Sit in the **Cluster/Index** tier and carry **Hub** or **Standard** weight depending on their role.

* **Breadcrumbs**

  * Breadcrumbs, where used, must show them as children of their Sectional Parent (for example `Home → Blog → Search results`) and never as new parents.

* **Navigation exposure**

  * May be reachable from primary or secondary nav as a **mode** (for example a search entry within Blog), but:

    * they must not appear as separate sections; and
    * they must not become the sole route to underlying content.

* **Appendix B recording**

  * All search and archive surfaces are recorded under the relevant Sectional Parent, with clear indication that they are alternative access modes, not new IA branches.

Archives and search views are **derivative lenses** over existing content, not new nodes in the tree.

### **4.4.3 Glossary Anchors and In-Page Structures**

The Glossary (`/glossary`) and similar in-page anchor structures (for example A–Z sections, intra-page TOCs) behave like many small “subpages” from the user’s perspective, but structurally they are part of a single page.

Rules:

* **Hierarchy**

  * The Glossary A–Z anchors (`/glossary#a`, `/glossary#b`, etc.) are **not** separate pages in the IA.
  * The glossary as a whole is a single **Content/Task** page under its Sectional Parent (the Marketing runtime, typically grouped with Resources/Guides).

* **Navigation exposure**

  * Primary or secondary nav may link to `/glossary` and, if needed, to specific anchors, but those anchors do not become Sectional Parents or Hubs.

* **Appendix B recording**

  * Appendix B records only `/glossary` as a page; anchors are treated as internal structure, not as separate rows.
  * Any internal nav widgets (A–Z strips, in-page TOCs) are governed by the PDS; they do not change the hierarchy.

Glossary anchors and in-page jumps are **local structure**, not hierarchical tiers.

### **4.4.4 Legacy, Redirect, and Shadow URLs**

Over time, URLs may change while external links and bookmarks remain. To avoid breaking flows and SEO, some legacy or shadow URLs may be retained as redirects.

Rules:

* **Hierarchy**

  * Redirect-only URLs are **not** considered active nodes in the hierarchy.
  * Structurally, they resolve to the target surface and inherit its Runtime, Tier, and Weight.

* **Navigation exposure**

  * Legacy/shadow URLs must never appear in navigation, breadcrumbs, or IA diagrams.
  * They exist solely for compatibility and must always redirect (301/308) to the canonical surface defined in Appendix B.

* **Appendix B recording**

  * Canonical surfaces are listed as normal rows.
  * If legacy URLs are significant, they may be recorded as metadata on the canonical row (for example “Former URLs”), not as separate pages.

Redirect and shadow URLs are **compatibility artefacts**, not part of the live IA.

### **4.4.5 Multi-Role or Hybrid Surfaces**

Some surfaces legitimately play more than one conceptual role—for example:

* the **State of SME Cybersecurity** hub, which acts as both a report anchor and a research hub;
* a **Settings Overview** that both orients and routes to detailed settings pages.

Rules:

* **Single structural identity**

  * Each hybrid surface must still have a **single Structural Tier and Weight Class** in Appendix B (for example Content/Task + Hub), even if the narrative role is mixed.

* **Navigation and mesh**

  * Additional roles (for example being a research hub) must be expressed via:

    * secondary navigation scoped to its Sectional Parent; and/or
    * partials and cross-links governed in Appendix D.
  * Hybrid behaviour must not be implemented by silently treating the surface as a second Sectional Parent.

* **Documentation**

  * Any hybrid surface must be explicitly called out in Appendix B as such (for example “Role: Hybrid – Report anchor + Research hub”) to prevent future misclassification.

Hybrid surfaces are **single nodes with multiple jobs**, not secret branches.

---

Only these exception classes are permitted. Any new pattern that appears to fall “outside” the normal hierarchy must either be mapped into one of the classes above or trigger an explicit update to this section, Appendix B, and any affected navigation rules in §3.

---

## **4.5 Edge-Case Elevation Rules**

Edge-case elevation rules define when a surface may be given **extra visibility** (for example, promoted into primary navigation or Home-page prominence) without changing its underlying structural tier or role in the IA. Elevation is always a **presentation decision**, not a structural edit: the tree defined in §4.1–§4.4 remains unchanged unless this document and Appendix B are explicitly updated.

Elevation exists to support campaigns, key assets, or operational priorities while preventing “one-off hacks” from silently creating new sections or navigation tiers.

### **4.5.1 What Elevation Is (and Is Not)**

For the purposes of this IA:

* **Elevation** means:

  * surfacing an existing page (recorded in Appendix B) more prominently than usual, for example:

    * adding it temporarily to primary nav
    * pinning it in the Home hero
    * giving it a persistent slot in Section navigation
  * without altering:

    * its Runtime
    * its Structural Tier (§4.1)
    * its Sectional Parent (§4.2)
    * its canonical URL (Appendix B)

* **Elevation is not**:

  * creating a new Sectional Parent or runtime
  * introducing a new navigation tier
  * forking a page into “campaign” and “structural” variants with separate URLs

If an elevation requires any of the above, it is not an edge case; it is a structural change and must go through a full IA revision.

### **4.5.2 Eligible Surfaces and Constraints**

The following surfaces may be elevated:

* **Anchor and Hub pages** (§4.3)

  * typical candidates: `/guides`, `/resources`, `/compare`, `/industries`, `/reports/state-of-sme-cybersecurity`, Evidence Dashboard, Evaluation Overview, Billing Dashboard
  * may be given additional prominence in primary nav, Home, or section rails

* **High-value Standard pages**

  * exemplary guides, cornerstone articles, or flagship reports
  * may be given fixed slots in section-level nav or featured positions on parent Hubs

**Constraints:**

* The elevated surface **must already exist** in Appendix B with a canonical URL.
* Elevation must **not**:

  * re-label the page in a way that suggests a new section (for example calling a single guide “Guides” in nav)
  * place Ephemeral/Utility pages (§4.3.4) into primary or section nav
  * change breadcrumb structure; crumbs must still reflect the true hierarchy

If repeated or permanent elevation effectively turns a Standard page into a de facto Hub or Anchor, the IA and Appendix B must be updated to reclassify it rather than treating the elevation as permanent “exception”.

### **4.5.3 Temporary or Campaign Elevations**

Temporary elevations are used for campaigns, launches, or time-bounded initiatives (for example a major report or promo guide).

Rules:

* **Time-bounded by design**

  * Start and end conditions must be defined (for example “Q3 campaign” or “until N+1 report is published”).
  * When the window closes, navigation and Home-page treatments revert to the non-elevated state.

* **No structural promises**

  * Campaign labels must not imply permanent sections (for example “New Module” in nav pointing to a guide).
  * Deep links always use the canonical URL; campaign wrappers (UTM, tracking) do not create alternative structures.

* **Recording**

  * Campaign elevations are recorded outside the IA (for example in marketing ops), but:

    * any temporary use of primary or Section navigation must still respect the constraints of §3 and §4
    * Appendix B must not be altered to represent campaign-only prominence.

Temporary elevations are front-end concerns implemented via the PDS. The IA’s role is to define what is *allowed* to be temporarily lifted, and what must remain structurally untouched.

### **4.5.4 Persistent Elevations Without Tier Change**

Some elevations are intended to be long-lived but still **must not** alter the underlying hierarchy. Typical examples:

* a “hero” guide from `/guides/{slug}` that is always pinned under `/guides`
* a particular comparison page (`/compare/consultancy`) always listed under `/compare`
* a Settings subpage surfaced as a quick-link from a dashboard

Rules:

* The elevated page remains a **child** of its Sectional Parent in all structural representations.

* Primary navigation may link to the page **by its real label** if justified, but:

  * it must be clear which Sectional Parent it belongs to; and
  * it must not displace the Sectional Parent entirely unless the IA is formally revised.

* If a persistent elevation:

  * is expected to last across major releases, and
  * materially changes how users understand the shape of the product,
    then the IA should be updated to reflect that reality (for example, promote a Hub to Anchor, or an existing Anchor to explicit Sectional Parent) rather than treating it as a permanent exception.

Persistent elevation is acceptable as long as **structure and documentation are kept honest**.

### **4.5.5 Documentation and Governance**

All elevations must respect the following governance rules:

* **Source of truth**

  * Appendix B remains the canonical list of surfaces, their Structural Tier, Weight Class, and Sectional Parent.
  * Elevations must reference these existing entries; they do not create new rows.

* **Navigation mapping**

  * Appendix B3 (Navigation Exposure) records, for each page:

    * its baseline nav exposure (Primary, Section, Utility/Footer, or contextual only)
    * any documented elevation patterns (for example “may appear in Primary during campaigns”, “pinned under Guides as featured guide”).

* **Change control**

  * Any change that:

    * promotes a new Surface into primary nav on a permanent basis, or
    * demotes an existing Anchor/HUB so that it no longer functions as a structural entry
      must trigger an IA review:

      * update §4.1–§4.3 if tiers or weight are affected
      * update §4.2 if Sectional Parents change
      * update Appendix B/B3 and any affected navigation rules in §3.

Elevation rules allow the product and marketing layers to spotlight important surfaces **without corrupting the underlying IA**. When those spotlights become the new normal, the IA must be updated explicitly rather than letting exceptions accumulate.

---

# **5. SEO Keyword Mapping**

This section defines how search intent is mapped onto the IA so that each indexable surface has a clear, non-competing role in organic discovery. It ties together content types (§6), taxonomy (§7), URL structure (§8), and cross-linking (§9). The goal is to avoid keyword cannibalisation, keep topic ownership explicit, and ensure that SEO decisions never distort the underlying IA.

All SEO intent assignments and canonical keyword sets must be reflected in Appendix C (Metadata Schema) and Appendix E (Taxonomy Catalogue). No new SEO-driven surface, category, or tag may be introduced without first being modelled here and recorded in those appendices.

## **5.1 Pillar Topics and Anchor Ownership**

Pillar topics are the highest-level themes the platform wants to rank for. Each pillar topic must be owned by a specific **Anchor or Hub** page defined in §4.3 and Appendix B. No other page is allowed to compete directly for the same primary query family.

Principles:

* Each pillar topic is mapped to **exactly one** primary surface (for example Home, Features, Guides Index, Blog Landing, Compare Hub, Industries Index, State-of Report Hub).
* Pillar owners carry broad, high-level queries (for example “Cyber Essentials readiness platform”, “SME cyber compliance guides”).
* Supporting pages (guides, blog posts, case studies) target *subsets* or *long-tail variants* of the pillar’s topic, not the same head terms.

Appendix E must list the pillar topics, their owning pages (by Appendix B ID), and their permitted semantic neighbourhoods.

## **5.2 Page-Level Intent Assignment**

Every indexable page must have a single, explicit **primary search intent** and, where needed, one or two **secondary intents**. These intents determine:

* which queries the page is designed to answer
* which taxonomy categories/tags are appropriate
* how internal links and partials should reference it

Rules:

* One page → one primary intent.
* Secondary intents must be strictly compatible with the primary; no “two different pages in one” behaviour.
* Pages with no organic discovery role (for example login, evidence steps, billing) are explicitly marked **Non-SEO** in Appendix B and must not be optimised or exposed for search.

Appendix B and Appendix C together form the authoritative mapping from page → primary intent → meta title/description → canonical URL.

## **5.3 Semantic Neighbourhoods and Clusters**

Each pillar topic defines a **semantic neighbourhood**: a cluster of related queries and subtopics that can be handled by the pillar surface and its supporting content.

For each pillar:

* The **Anchor/Hub** page owns the broad, generic queries.
* **Guides and case studies** sit directly under the pillar, targeting deeper, how-to, or verticalised queries.
* **Blog posts** explore narrower, time-bound, or opinionated angles within the same neighbourhood.
* **Resources and templates** capture highly action-oriented queries (for example “checklist”, “template”, “download”).

Semantic clusters must be:

* reflected in taxonomy (categories and tags in Appendix E)
* supported by internal link structures defined in §9 and Appendix D
* designed to avoid multiple pages competing for the same head term

Where clusters become too large or diffuse, the IA (not just SEO) must be revisited to consider creating additional Hubs or restructuring categories.

## **5.4 Cannibalisation and Conflict Boundaries**

To prevent keyword cannibalisation and confusing SERP behaviour:

* No two pages may share **identical** primary search intent.
* If two pages appear to target the same query family:

  * one becomes the canonical owner (typically a Guide or Hub),
  * the other is reframed as supportive, retargeted to a narrower intent, or folded/redirected.

Specific rules:

* **Guides vs Blog**

  * Guides own evergreen, authoritative “how to” and “what is” topics.
  * Blog posts on the same subject must either:

    * take a news/tactical angle, or
    * address a distinct sub-problem.

* **Marketing Pages vs Guides/Blog**

  * Marketing Landings (Home, Features, Why, How It Works) own high-intent commercial queries.
  * Editorial surfaces (guides/blog) own informational queries.
  * If overlap occurs, the marketing page keeps the commercial angle; the editorial page is adjusted toward education.

Any cannibalisation decision must be reflected by:

* updating Appendix B’s SEO Intent column,
* updating Appendix E if categories or tags are changed, and
* adjusting internal links in line with §9.

## **5.5 Long-Tail Capture Strategy**

Long-tail queries are captured primarily through:

* blog posts
* guides with specific scopes
* case studies with clear industry and problem framing
* resource pages tied to concrete artefacts (templates, checklists, etc.)

Rules:

* Long-tail pages must still map back to a semantic cluster; they are not allowed to become orphaned fragments.
* Each long-tail page must:

  * reference its owning pillar (via internal links and taxonomy),
  * have tightly scoped intent reflected in title, heading, and metadata,
  * avoid generic titles that collide with pillar-level or other long-tail pages.

Partial-driven listings (for example “Related Stories”, “For Your Industry”) are allowed to surface long-tail material more prominently, but they must not violate the underlying intent or cluster assignments.

## **5.6 Deprioritised and Excluded Keywords**

Not every plausible keyword is worth targeting. To prevent IA and content bloat:

* Some keywords and themes are explicitly **deprioritised** (for example overly broad “cyber security” with no SME/compliance focus, or regimes the product does not support).
* Other keywords are explicitly **excluded** because they misrepresent the product (for example “free Cyber Essentials certification”, if that is not offered).

Appendix E must maintain:

* a list of **deprioritised themes** – allowed to appear incidentally, but not used to drive page creation or optimisation;
* a list of **excluded themes** – avoided in titles, headings, core copy, and metadata.

Content creators must not create new pages or rewrite existing ones to chase deprioritised or excluded terms. If business strategy changes, this section and Appendix E must be updated before content or navigation is altered.

---

# **6. Content Types**

This section defines the distinct classes of content used across the platform, from marketing pages and long-form articles to intake forms, evaluation steps, reports, and legal surfaces. Each type carries its own structural requirements and behavioural expectations. The foundational templates for these content types are represented in Appendix A, ensuring consistency, predictability, and long-term maintainability. Certain content types may embed governed cross-page partials for lateral discovery (e.g., related content, industry pivots, workflow guidance), and these partials are defined and constrained in Appendix D.

## **6.1 Marketing Types**

Marketing types cover all public, unauthenticated content surfaces across the site/blog/guides/resources layer. They exist to attract, educate, convert, and reassure prospects, not to execute deterministic workflows.

### **6.1.1 Landing and Explainer Surfaces**

These are high-level entry and framing pages:

* Home
* Features
* Pricing
* Why Transcrypt
* How It Works
* Industries Overview and Industry Detail pages
* Comparison hub and individual comparison pages

Characteristics:

* Own broad, high-intent topics and narrative framing.
* Eligible for Primary navigation exposure (§3.1) and Anchor/Hub weighting (§4.3).
* May host partials such as “Next Best Step”, “For Your Industry”, and “Starter Kit Promo” within the constraints of Appendix D.
* Must not expose authenticated or tenant-specific state.

### **6.1.2 Narrative and Editorial Content Surfaces**

These carry ongoing, editorialised content:

* Blog landing and index views
* Blog articles
* Guides index and guide articles
* Case study index and case study detail pages
* State of SME Cybersecurity report hub and similar research hubs

Characteristics:

* Typically Standard or Hub weight (§4.3).
* Indexed for organic search, with clear primary topics defined in §5 and Appendix B.
* Heavy consumers of taxonomy (§7) and partials (Appendix D) for discovery and clustering.
* Must maintain stable, canonical URLs as defined in §8.

### **6.1.3 Resource and Conversion Surfaces**

These are focused on value exchange and commitment:

* Resource library and individual resource downloads
* Resource download confirmations
* Starter kit page
* Waitlist and newsletter signup flows
* Conversion “thanks” pages

Characteristics:

* Primary intent is conversion, not exploration.
* Messaging must be tightly scoped; cross-links are permitted but must not distract from the primary call to action.
* Conversion forms and their confirmations are generally Ephemeral/Utility weight (§4.3.4), with strict rules about partial usage to avoid clutter.
* URL patterns and form states must be stable enough to support campaigns and tracking without fragmenting IA (§8).

### **6.1.4 Legal, Trust, and Operational Surfaces**

These provide assurance, legal clarity, and operational transparency:

* Privacy, Terms, Cookies, Accessibility, AUP, DPA, Subprocessors
* Security overview and Responsible Disclosure
* Public Status page

Characteristics:

* Primarily Trust / Due Diligence intent (§5).
* Typically accessed via Utility/Footer navigation (§3.7), occasionally from high-level trust hubs (e.g., Security).
* Indexable and linkable, but not part of core marketing funnels.
* Must maintain long-term URL stability; changes require careful redirect planning (§4.4.4, §8.5).

---

## **6.2 Application Types**

Application types cover authenticated, task-driven surfaces within the Essentials runtime. They are deterministic, state-bound, and must respect workflow and suppression rules (§3.3, §3.4, §12).

### **6.2.1 Identity and Onboarding Types**

These surfaces control entry into the Essentials runtime:

* Login
* Password reset request and confirm
* Signup start, verification, verified, checkout, and signup complete

Characteristics:

* IdentityFlow or Onboarding types in Appendix B.
* Structurally part of Essentials, but with special hierarchy and breadcrumb rules (§4.4.1).
* No marketing partials; any contextual help is deterministic and specified in the PDS.
* Frequently subject to navigation suppression (e.g., stripped headers/footers) as per §3.4.

### **6.2.2 Intake and Organisation Context Types**

These initialise and maintain core organisational data:

* Organisation setup / initial intake
* Organisation details / ongoing org profile

Characteristics:

* Intake types in Appendix B.
* Must capture and present tenant context in a reversible, auditable way.
* Accessible from early workflow stages and from appropriate settings surfaces.
* Never indexable, and never exposed via Marketing navigation.

### **6.2.3 Evidence and Evaluation Workflow Types**

These drive the core readiness workflow:

* Evidence dashboard
* Evidence submission and review surfaces
* Evaluation overview
* Evaluation step pages
* Evaluation complete / milestone confirmations

Characteristics:

* Evidence* and Evaluation* types in Appendix B.
* Governed by workflow navigation rules (§3.3) and Transition Matrix constraints (§12).
* Navigation is strictly deterministic: no arbitrary jumping beyond what state allows.
* Cross-runtime or marketing-style partials are prohibited; contextual guidance must be defined in the PDS as workflow-specific components.

### **6.2.4 Reporting, Billing, and Settings Types**

These supply outputs, commercial control, and configuration:

* Report views and downloads
* Billing dashboard, subscription management, payment methods, billing history
* User profile, security settings, notification preferences, organisation profile

Characteristics:

* Report, Billing*, and Settings* types in Appendix B.
* Must expose a consistent, minimal primary frame within Essentials (§3.1).
* Some may be reachable from multiple workflow points (for example billing from error or grace states) but remain structurally under their Sectional Parents (§4.2).
* No marketing cross-links; only deterministic, role-appropriate navigation.

---

## **6.3 Evidence & Report Types**

Evidence and report types are a special subset of application types that directly support certification readiness, auditor interactions, and business decision-making. They have stricter rules for structure, state, and change.

### **6.3.1 Evidence Item Types**

Evidence items are per-control artefacts and attestations:

* Document uploads and file-based artefacts
* Textual attestations and policy statements
* Configuration snapshots or screenshots
* External references (for example links to ticket systems or repositories)

Characteristics:

* Always tenant-scoped and control-scoped (Control ID in Appendix B / SAIS).
* Must be versioned and time-stamped according to SAIS and audit requirements.
* May be grouped in Evidence dashboard views but retain individual identity for reporting.
* Never exposed in Marketing; any references are high-level summaries only.

### **6.3.2 Evidence View and Summary Types**

These are structured, read-oriented views over evidence state:

* Evidence dashboard
* Per-control evidence summaries
* Gap/deficiency views

Characteristics:

* Present aggregated states without altering canonical evidence content.
* May be used as hubs for navigation into individual evidence items.
* Strongly linked to Evaluation overview and steps, but must not silently mutate evaluation state.

### **6.3.3 Report Output Types**

Reports are structured outputs derived from evidence and evaluation:

* Tenant readiness summary views (on-screen)
* Detailed, sectioned reports (on-screen)
* Exported reports (PDF/other formats)

Characteristics:

* On-screen report surfaces are normal application pages (ReportView types) and obey normal IA rules for hierarchy, breadcrumbs, and navigation.
* Exported artefacts are **not** separate IA pages; they are downloads bound to a report surface and described in Appendix B as download endpoints, not as parents.
* Content must be stable enough that auditors and stakeholders can rely on repeatability and traceability over time.

### **6.3.4 Auditor and Third-Party Facing Variants (Future)**

Future work may introduce additional report variants or auditor-oriented views:

* Auditor-friendly report subsets or portals
* Insurance-oriented summaries
* Export formats tuned for specific regimes

Characteristics:

* These are explicitly out-of-scope for the MVP IA but are acknowledged as future extensions.
* When introduced, they must be modelled as derived views or exports of existing report types, not as independent hierarchies.
* Any new surfaces must be added to Appendix B and integrated into §12 Transition Matrix.

---

## **6.4 Structural Requirements Per Type**

This subsection defines the structural properties that apply to each content type family. It ties types to runtime, navigation tiers, indexability, and partial usage so that no component or template in the PDS can invent its own rules.

### **6.4.1 Shared Structural Properties**

Every type defined in §6.1–§6.3 must be assigned, in Appendix B, the following structural properties:

* **Runtime**

  * Marketing or Essentials, as defined in §2.

* **Structural Tier**

  * Runtime Root, Sectional Parent, Cluster/Index, Content/Task, or State/Ephemeral (§4.1).

* **Weight Class**

  * Anchor, Hub, Standard, or Ephemeral/Utility (§4.3).

* **Nav Tier Eligibility**

  * Primary, Section, Utility/Footer, or Flow-only, as captured in Appendix B3 and governed by §3.

* **Indexability**

  * Indexable (intended for public search), Non-Indexable (operational), or Noindex but discoverable (for example certain trust pages in special circumstances).

* **Partial Eligibility**

  * Which governed partials (Appendix D) may appear on that type of surface, if any.

These properties must be treated as authoritative for UI and routing decisions. The PDS may refine presentation, but it may not contradict these assignments.

### **6.4.2 Marketing Type Requirements**

For Marketing types (§6.1):

* **Landing and Explainer Surfaces**

  * Runtime: Marketing
  * Structural Tier: Sectional Parent or Cluster/Index
  * Weight: Anchor or Hub
  * Nav Tier: Eligible for Primary and Section navigation; may also appear in Utility/Footer where appropriate.
  * Indexability: Indexable
  * Partials: Broadest allowance, but must respect intent and avoid overloading pages with unrelated topics.

* **Narrative and Editorial Content Surfaces**

  * Runtime: Marketing
  * Structural Tier: Cluster/Index (hubs) or Content/Task (articles)
  * Weight: Hub (indices/hubs) or Standard (articles/guides/case studies)
  * Nav Tier: Typically Section; rarely Primary.
  * Indexability: Indexable
  * Partials: Allowed, but must follow the contextual rules in Appendix D and the topic boundaries in §5 and §7.

* **Resource and Conversion Surfaces**

  * Runtime: Marketing
  * Structural Tier: Content/Task or State/Ephemeral (for confirmation pages)
  * Weight: Standard or Ephemeral/Utility
  * Nav Tier: Usually Section or contextual links; may be surfaced in Primary only when justified and documented as an elevation (§4.5).
  * Indexability: Case-by-case; some may be indexable (starter kit), others operational only.
  * Partials: Strictly constrained; conversion surfaces should only host partials that reinforce the intended action.

* **Legal, Trust, and Operational Surfaces**

  * Runtime: Marketing
  * Structural Tier: Content/Task
  * Weight: Standard
  * Nav Tier: Utility/Footer by default; rarely in Primary.
  * Indexability: Indexable, with conservative SEO targets.
  * Partials: Normally none; emphasis is on clarity and stability.

### **6.4.3 Application Type Requirements**

For Application types (§6.2–§6.3):

* **Identity and Onboarding Types**

  * Runtime: Essentials
  * Structural Tier: Cluster/Index (login) or State/Ephemeral (reset, verify, complete)
  * Weight: Hub (login) or Ephemeral/Utility (one-shot steps)
  * Nav Tier: Flow-only; may be linked from Marketing via explicit “Log in” calls to action, but not treated as sections.
  * Indexability: Non-indexable.
  * Partials: None; only deterministic help components.

* **Intake and Organisation Context Types**

  * Runtime: Essentials
  * Structural Tier: Content/Task
  * Weight: Standard
  * Nav Tier: Section-level within Essentials; never Primary; no Utility/Footer treatment.
  * Indexability: Non-indexable.
  * Partials: None; guidance is local and workflow-specific.

* **Evidence and Evaluation Workflow Types**

  * Runtime: Essentials
  * Structural Tier: Cluster/Index (dashboards/overviews) or Content/Task (steps, per-control views)
  * Weight: Hub (dashboards/overviews) or Standard (steps, per-control)
  * Nav Tier: Section and Flow-only, tightly bound to workflow navigation (§3.3, §12).
  * Indexability: Non-indexable.
  * Partials: Prohibited; only deterministic inline hints or help patterns as defined in the PDS.

* **Reporting, Billing, and Settings Types**

  * Runtime: Essentials
  * Structural Tier: Content/Task
  * Weight: Standard or Hub depending on scope (for example Billing dashboard as Hub)
  * Nav Tier: Section; may include local secondary navigation where allowed by §3.2.
  * Indexability: Non-indexable.
  * Partials: None; any cross-links are explicit, deterministic navigation to other Essentials surfaces.

### **6.4.4 Evidence and Report Specific Requirements**

Because evidence and reports underpin auditability, they have additional structural rules:

* **Evidence Items and Views**

  * Must always resolve to a single canonical surface per tenant and control; no parallel variants with different URLs.
  * May be referenced from multiple dashboards or evaluation views, but those references must not create apparent “duplicate” pages in navigation or breadcrumbs.
  * Changes to evidence URL patterns require explicit IA and SAIS review and updates to §8 URL Structure.

* **Report Views and Downloads**

  * Report views are standard application pages and must sit cleanly within the hierarchy under their Sectional Parents.
  * Download endpoints are secondary and must be modelled as derivatives of the report views, not as separate branches.
  * Any new report type (for example a different audience or regime) must be added to Appendix B with explicitly documented relationships to existing evidence and evaluation types.

No content type may be introduced in the PDS, CMS, or implementation without first being mapped into one of the families above and assigned full structural properties in Appendix B. If a genuinely new type is required, this section must be updated first, then reflected in Appendix A, Appendix B, and any affected rules in §3–§5, §7–§9.

---

# **7. Taxonomy**

The taxonomy defines the classification system used across content, including categories, tags, and other controlled groupings. It ensures consistent organisation, improves discoverability, and supports internal search behaviours. Taxonomy also powers several cross-referential partials—such as Related Stories, For Your Industry, and Research Highlight—whose behaviour and placement rules are governed in Appendix D. Any taxonomy-driven partial must reflect the authoritative taxonomy structures defined in this section and catalogued in Appendix E (Taxonomy Catalogue).

No category or tag may be used in the CMS, content, or partials layer unless it is defined and in an active state in Appendix E.

## **7.1 Core Categories**

Core categories are the small, governed set of top-level themes that describe what a piece of content is fundamentally about. They are the primary way long-form content is organised for humans and for search.

Core categories:

* are few in number and stable over time
* apply primarily to editorial and explanatory content (blog, guides, case studies, research hubs)
* may be used as the basis for navigation groupings in Blog and Guides sections
* are always defined and maintained in Appendix E

### **7.1.1 Definition and Scope**

A core category:

* represents a major conceptual area, not a specific keyword or campaign
* must be understandable to an SME decision-maker without jargon
* must be broad enough to host multiple pieces of content, but narrow enough to be meaningful

Examples of core category families (for illustration; actual values are enumerated in Appendix E):

* Foundations and posture
* Controls and practices
* People and process
* Incidents and resilience
* Vendors and supply chains
* Regulatory and assurance

### **7.1.2 Assignment Rules**

Rules for assigning core categories:

* Each eligible content item (for example guide, blog article, case study, research hub) must have **exactly one** primary core category.
* A small number of secondary categories may be permitted for genuinely cross-cutting pieces, but the primary category is authoritative for hierarchy, navigation, and SEO mapping.
* Legal, trust, conversion, and purely operational surfaces normally do **not** carry core categories unless explicitly justified.

Core category assignments for each surface are recorded in Appendix E and referenced from Appendix B for key pages.

### **7.1.3 Runtime Usage**

Core categories:

* drive category views for Blog and Guides (for example `/blog/category/{slug}`, `/guides/category/{slug}`)
* may inform section-level navigation, filters, and partials such as Related Stories
* must not be used to imply cross-runtime movement; they are a content classification, not a navigation tier

Any change to the core category set (addition, rename, removal) must follow the governance rules in §7.5 and be reflected in Appendix E before being used.

---

## **7.2 Extended Categories**

Extended categories provide additional, orthogonal dimensions for classification. They supplement core categories and are used sparingly to keep the taxonomy understandable and maintainable.

Extended categories include, but are not limited to:

* Industry and sector
* Framework or regime
* Journey stage
* Persona or audience type

All extended categories and their allowed values are listed in Appendix E.

### **7.2.1 Industry and Sector**

Industry categories describe the sectoral context for a piece of content or a page:

* Examples: healthcare, retail, professional services, manufacturing, education
* Primarily used for:

  * Industry landing pages
  * Case studies
  * Guides and articles with strong sector focus
  * For Your Industry partials (Appendix D)

Rules:

* Each piece of content may have zero or more industries, but most should have **at most one or two**.
* Industry tags must match the values defined in Appendix E; new industries cannot be ad hoc.

### **7.2.2 Framework and Regime**

Framework categories capture the regulatory or standard context:

* Examples: Cyber Essentials, NIS2, ISO 27001, UK GDPR
* Framework categories are used to:

  * group content by regime
  * power filters or specialised hubs
  * support partials or navigation that pivot by regime

Rules:

* A piece of content may reference multiple regimes, but should have a **single dominant** regime category where possible.
* Framework categories must align with the product’s actual coverage; speculative regimes are not permitted.

### **7.2.3 Journey Stage and Persona**

Optional extended categories may capture:

* **Journey stage** (for example learn, plan, implement, prove)
* **Persona** (for example owner, operations lead, IT contact, managed service provider)

These are used primarily for:

* internal analytics and editorial planning
* powering more precise partials or recommendations in future phases

They must remain controlled lists in Appendix E and must not explode into dozens of overlapping terms.

---

## **7.3 Tag Architecture**

Tags provide more granular, flexible descriptors than categories. They are used to capture specific topics, techniques, tools, and issues that cut across categories and industries. Tags are more numerous than categories, but still governed; the taxonomy must not degrade into unstructured tag sprawl.

### **7.3.1 Tag Types**

Tags are divided into clear types, each with a specific purpose. Examples:

* **Topic tags** – concrete subjects (for example password policy, backup, incident response).
* **Technique tags** – methods, patterns, or approaches (for example automation, checklists, playbooks).
* **Risk and issue tags** – specific risks or issues (for example phishing, ransomware, insider risk).
* **Audience or context tags** – small, controlled sets only where extended categories are insufficient.

Each tag in Appendix E must be assigned a type. Tag type determines where it may appear (for example Topic tags on blog and guides; Risk tags on certain reports, etc.).

### **7.3.2 Assignment Limits**

To prevent dilution:

* Each piece of content should have:

  * one core category (§7.1)
  * zero or a small number of extended categories (§7.2)
  * a **limited set of tags**, typically no more than five to seven

Rules:

* Tags must be chosen from Appendix E; new tags require governance (§7.5).
* Tags must be relevant to the primary topic of the content; they are not for tangential mentions.
* The CMS must not allow arbitrary free-text tags in production.

### **7.3.3 Namespacing and Hygiene**

To avoid duplication and ambiguity:

* Tags must be unique by canonical form; ambiguous or overlapping tags (for example “MFA” vs “multi-factor authentication”) are handled through synonyms (§7.4).
* “Miscellaneous”, “other”, and similar junk tags are prohibited.
* Plural versus singular, abbreviations, and localised spellings are normalised through canonical forms and synonyms in Appendix E.

---

## **7.4 Synonym Rules**

Synonyms allow the system to recognise different human labels for the same underlying concept without fragmenting the taxonomy.

### **7.4.1 Canonical Terms**

For each category and tag that requires it, Appendix E designates:

* a single **canonical term**, used:

  * in navigation
  * in UI labels
  * in metadata fields (titles, descriptions where applicable)

Only canonical terms may appear in visible navigation and taxonomy UI.

### **7.4.2 Synonym Mapping**

Synonyms are alternative strings that map to the canonical term. They are used for:

* internal search and query expansion
* import or migration from other systems
* editorial guidance

Rules:

* Synonyms must never create new taxonomic rows; they are always mapped to an existing canonical entry.
* Synonyms should capture:

  * common abbreviations (for example MFA → Multi-factor authentication)
  * common misspellings or regional variants where appropriate
* Synonym relationships are recorded in Appendix E and must be one-to-one or many-to-one into a canonical term; many-to-many is prohibited.

### **7.4.3 Forbidden or Discouraged Terms**

Certain terms may be marked in Appendix E as:

* **Forbidden** – must not be used in content or UI (for example vague or misleading jargon).
* **Discouraged** – allowed rarely, with editorial justification.

Forbidden or discouraged terms guide content authors and help keep taxonomy clean and consistent.

---

## **7.5 Taxonomy Governance Lifecycle**

Taxonomy is not static; it evolves as the product and content evolve. That evolution must be controlled so IA, SEO, and partials do not drift into inconsistency.

### **7.5.1 Creation and Proposal**

New categories or tags may be proposed when:

* existing categories and tags cannot accurately describe new, strategically important content
* a repeated pattern emerges across content that is not adequately captured

Proposals must:

* specify type (core category, extended category, or tag type)
* state the rationale and expected usage
* include suggested canonical label and any obvious synonyms

No new term may be used in production content until it has been admitted into Appendix E.

### **7.5.2 Review and Approval**

Proposed taxonomy changes are reviewed for:

* overlap with existing terms
* impact on navigation, IA, and SEO mapping (§5, §9)
* impact on existing partials (Appendix D)

Outcomes:

* **Accepted** – added to Appendix E with canonical form, type, and rules.
* **Rejected** – documented as rejected to avoid repeated proposals.
* **Merged** – handled via synonym mapping into an existing term.

Significant changes to core categories or extended categories may require corresponding IA updates in §2, §4, and Appendix B.

### **7.5.3 Monitoring and Pruning**

Periodically, taxonomy should be reviewed to:

* identify unused or rarely used tags and categories
* detect near-duplicates or drift in naming
* confirm that category and tag distributions remain understandable

Outputs may include:

* deprecation of unused entries (§7.6)
* consolidation of overlapping tags into a single canonical term
* updates to synonym lists in Appendix E

---

## **7.6 Deprecated or Merged Taxonomies**

Over time, some taxonomy entries will be retired or merged. This must be done without breaking IA, navigation, or search.

### **7.6.1 Deprecation Criteria**

A taxonomy entry may be deprecated when:

* it is no longer aligned with the product or content strategy
* it has been effectively replaced by another, more accurate term
* it has become unused across live content for a defined period

Deprecated entries are not deleted; they are marked as **deprecated** in Appendix E with:

* deprecation date
* reason
* replacement term (if any)

### **7.6.2 Merge and Remapping Strategy**

When two or more terms are merged:

* one canonical term is chosen as the survivor
* all affected content is updated to use the canonical term
* the superseded terms are marked as deprecated and recorded as synonyms pointing to the canonical term

If URL structures or dedicated views depend on a merged category (for example a category page being retired), corresponding changes must be reflected in:

* §4 hierarchy rules
* §8 URL Structure and redirect rules
* Appendix B page inventory and, if needed, §9 cross-linking

### **7.6.3 Historical Record and Analytics**

Appendix E must retain a historical record of:

* when entries were created
* when they were deprecated or merged
* what they were merged into

Analytics and reporting may continue to use historical tags for trend analysis, but new content must stop using deprecated entries. Search and partials must treat deprecated terms as synonyms into their replacement canonical terms.

No taxonomy entry may be removed from Appendix E without a clear deprecation or merge trail.

---

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
| Organisation Profile         | Org-wide settings: legal name, addresses, contact   | Essentials | APP.Settings.Org           | From settings; interacts with billing, report headers                          | `/app/settings/org`              | Type: Settings; Entity=Organisation  | Keeps identity details coherent across billing, reports, and evidence         | none                              | None     

---

### Appendix B3 — Navigation Exposure Map

This appendix defines how each page in the inventory is exposed in navigation. It does not introduce new pages or new structures; it normalises, in one place, how the existing surfaces from Appendix B appear (or do not appear) in the global header, in section-level navigation, and in utility/footer areas.

The purpose is threefold:

1. **Remove ambiguity about “what goes in the menus”.**
   The main IA body (§2 Sitemap, §3 Navigation Model, §4 Page Hierarchy) defines structure and behaviour, but does not enumerate menu entries. This appendix is the authoritative mapping from pages to navigation exposure.

2. **Preserve the meaning of “secondary navigation”.**
   In this IA, “secondary navigation” always means **section-level navigation** (rails, spines, tabs, local menus) and never footer or utility links. This appendix keeps that distinction explicit so terminology cannot drift.

3. **Support consistent implementation across runtimes.**
   Both the Marketing runtime and the Essentials runtime use this map to decide which pages are eligible for primary navigation, which belong to sectional/rail navigation, and which remain flow-only or footer-only.

Each row in the table links a page to one of the following **navigation tiers**:

* **Primary**
  Surfaces that appear in the **global primary navigation** of a runtime (e.g. top header in Marketing, main app shell in Essentials). These correspond to the top-level structural anchors in §4 Page Hierarchy and the primary patterns in §3.1 Primary Navigation.

* **Section**
  Surfaces that participate in **section-level navigation** only. This is what the IA calls *secondary navigation*: local rails, left-hand spines, tabs, or in-section menus inside a parent area (e.g. within Blog, Guides, Evidence, Billing, Settings). Section-level items never appear as standalone primary nav entries and never cross runtimes.

* **Utility/Footer**
  Surfaces exposed via **utility or footer areas** (e.g. legal, trust, status, newsletter). These links are navigable but are explicitly **not** “secondary navigation” in IA terms. They sit outside the primary/sectional hierarchy and are treated as utility access.

* **Flow-only (no nav)**
  Surfaces that are only reachable as part of a linear flow (e.g. password reset tokens, thanks/confirmation pages, some pagination endpoints). They do not appear in any navigation control and should not be linked to directly from menus.

The **Nav Tier** column records which of these tiers (if any) applies to the page. The **Nav Placement / Notes** column explains how and where the page is intended to be exposed in practice (e.g. “header item”, “within Blog rail”, “footer legal cluster”, “flow-only confirmation”).

This appendix does **not** define:

* visual layout or geometry of navigation (handled by **Appendix A — Structural Templates**)
* component-level interaction behaviour (hover, focus, suppression, mobile treatment — defined in the **PDS**)
* routing, permission checks, or state guards (defined in the **SAIS** and §12 Transition Matrix)

Any change to which pages appear in primary navigation, which pages gain or lose section-level entries, or which pages are relegated to utility/footer must be made by updating this Navigation Exposure Map and then aligning Appendix A, the PDS, and implementation accordingly.

---

**Columns**

* **Page Name**
* **URL Pattern**
* **Runtime**
* **Nav Tier** (Primary / Section / Utility/Footer / Flow-only)
* **Nav Placement / Notes**

---

#### B3.1 Phase 1 — Marketing / Blog / Guides / Resources / Waitlist

| Page Name                             | URL Pattern                           | Runtime   | Nav Tier           | Nav Placement / Notes                                                                           |
| ------------------------------------- | ------------------------------------- | --------- | ------------------ | ----------------------------------------------------------------------------------------------- |
| Home                                  | `/`                                   | Marketing | Primary            | Global entry; logo and/or “Home” in primary header.                                             |
| About                                 | `/about`                              | Marketing | Primary            | Primary header item or under “Company” style drop-down.                                         |
| Features                              | `/features`                           | Marketing | Primary            | Primary header item.                                                                            |
| Pricing                               | `/pricing`                            | Marketing | Primary            | Primary header item; key commercial entry.                                                      |
| Contact / Support                     | `/contact`                            | Marketing | Primary            | Header item and repeated in utility/footer for trust.                                           |
| Why Transcrypt                        | `/why`                                | Marketing | Primary            | Primary header item or surfaced via prominent CTAs (“Why Transcrypt?”).                         |
| Security Overview                     | `/security`                           | Marketing | Utility/Footer     | Linked from footer “Security”/“Trust” cluster and from key proof blocks.                        |
| Case Studies (Index)                  | `/case-studies`                       | Marketing | Section            | Linked from primary (e.g. under “Resources/Proof”) and local rails inside marketing surfaces.   |
| Case Study (Template)                 | `/case-studies/{slug}`                | Marketing | Section            | Reached from Case Studies index, related-links partials, not listed directly in global nav.     |
| Blog Landing / Overview               | `/blog/overview`                      | Marketing | Primary            | Treated as main “Blog” entry in header; `/blog` redirects or coexists.                          |
| Blog Index                            | `/blog`                               | Marketing | Section            | Within Blog section-level nav (tabs/filters) rather than separate header item.                  |
| Blog Article Template                 | `/blog/{slug}`                        | Marketing | Section            | Reached via Blog index, categories, tags, related-links partials.                               |
| Blog Categories Overview              | `/blog/categories`                    | Marketing | Section            | Section-level taxonomy control inside Blog (rail/tab item).                                     |
| Blog Category Page                    | `/blog/category/{slug}`               | Marketing | Section            | Within Blog section nav; navigated via category lists and chips.                                |
| Blog Tags Overview                    | `/blog/tags`                          | Marketing | Section            | Section-level taxonomy management surface; likely in a subtle blog-utility rail.                |
| Blog Tag Page                         | `/blog/tag/{slug}`                    | Marketing | Section            | Reached via tag chips and tag overview; not a primary header item.                              |
| Blog Author Page                      | `/blog/author/{slug}`                 | Marketing | Section            | Section-level surface; reached from author bylines and internal blog nav.                       |
| Blog Search                           | `/blog/search`                        | Marketing | Section            | Accessed via blog search widget; treated as part of Blog section nav, not a global header item. |
| Blog Pagination                       | `/blog/page/{n}`                      | Marketing | Flow-only (no nav) | Pagination mechanics; controlled by in-page controls, no separate nav exposure.                 |
| Blog Category Pagination              | `/blog/category/{slug}/page/{n}`      | Marketing | Flow-only (no nav) | Same as above, scoped to category pages.                                                        |
| Blog Tag Pagination                   | `/blog/tag/{slug}/page/{n}`           | Marketing | Flow-only (no nav) | Same pattern for tag views.                                                                     |
| Blog Search Pagination                | `/blog/search/page/{n}`               | Marketing | Flow-only (no nav) | Pagination of search results only.                                                              |
| Blog Date Archive (Year)              | `/blog/{yyyy}`                        | Marketing | Section            | Exposed via archive controls within Blog section.                                               |
| Blog Date Archive (Month)             | `/blog/{yyyy}/{mm}`                   | Marketing | Section            | Same, one level deeper; reachable only via Blog’s archive UI.                                   |
| Guides Index                          | `/guides`                             | Marketing | Primary            | Header item (“Guides”/“How-to”) as a main content pillar.                                       |
| Guide Article Template                | `/guides/{slug}`                      | Marketing | Section            | Within the Guides section; reached from index and related-links partials.                       |
| Guides Categories Overview            | `/guides/categories`                  | Marketing | Section            | Section-level taxonomy entry for guides.                                                        |
| Guide Category Page                   | `/guides/category/{slug}`             | Marketing | Section            | Within Guides section; category rails/filters.                                                  |
| Resource Library                      | `/resources`                          | Marketing | Primary            | Header item (“Resources”) and frequent CTAs from content.                                       |
| Resource Download                     | `/resources/{slug}`                   | Marketing | Section            | Reached from Resource Library tiles and in-content CTAs.                                        |
| Resource Download Confirmation        | `/resources/{slug}/thanks`            | Marketing | Flow-only (no nav) | Post-download confirmation; reached only via resource flow.                                     |
| Waitlist                              | `/waitlist`                           | Marketing | Primary            | Primary CTA target across site; treated as high-priority header or persistent CTA.              |
| Waitlist Confirmation                 | `/waitlist/thanks`                    | Marketing | Flow-only (no nav) | Confirmation-only; no direct nav entry.                                                         |
| Newsletter Signup                     | `/newsletter`                         | Marketing | Utility/Footer     | Located in footer and as CTA from blog/guides; not a primary tab.                               |
| Newsletter Confirmation               | `/newsletter/confirm`                 | Marketing | Flow-only (no nav) | Double opt-in endpoint; email-only entry.                                                       |
| Newsletter Thanks                     | `/newsletter/thanks`                  | Marketing | Flow-only (no nav) | Post-confirmation; purely flow-based.                                                           |
| Privacy Policy                        | `/privacy`                            | Marketing | Utility/Footer     | Footer “Legal” cluster and referenced from forms.                                               |
| Terms of Service                      | `/terms`                              | Marketing | Utility/Footer     | Footer “Legal” cluster; not in primary header.                                                  |
| Cookie Policy                         | `/cookies`                            | Marketing | Utility/Footer     | Footer “Legal” cluster; linked from cookie banner.                                              |
| Accessibility Statement               | `/accessibility`                      | Marketing | Utility/Footer     | Footer utility; sometimes linked from alt-text/ARIA help.                                       |
| Responsible Disclosure                | `/security/disclosure`                | Marketing | Utility/Footer     | Linked from `/security` and footer “Security” cluster.                                          |
| Acceptable Use Policy                 | `/aup`                                | Marketing | Utility/Footer     | Footer “Legal” cluster; sometimes linked from signup.                                           |
| Subprocessors List                    | `/subprocessors`                      | Marketing | Utility/Footer     | Footer “Legal/Trust” cluster; linked from privacy/DPA.                                          |
| Data Protection Addendum              | `/dpa`                                | Marketing | Utility/Footer     | Footer “Legal/Trust” cluster; linked from pricing/security/privacy.                             |
| Status Page                           | `/status`                             | Marketing | Utility/Footer     | Footer “Status” link and from `/security`.                                                      |
| Comparison Hub                        | `/compare`                            | Marketing | Primary            | Either header item or strong sub-item under “Why/Compare”; root of comparison cluster.          |
| Compare vs Traditional Consultancy    | `/compare/consultancy`                | Marketing | Section            | Within comparison section; reached from Compare hub and proof CTAs.                             |
| Compare vs Self-Assessment            | `/compare/self-assessment`            | Marketing | Section            | Same pattern; not in global header.                                                             |
| How It Works                          | `/how-it-works`                       | Marketing | Primary            | Primary header item or always-present CTA target from hero blocks.                              |
| Industries Overview                   | `/industries`                         | Marketing | Primary            | Primary or mega-menu entry for verticalised content.                                            |
| Industry Landing Template             | `/industries/{slug}`                  | Marketing | Section            | Within Industries section; reached from industries index and campaign CTAs.                     |
| Glossary                              | `/glossary`                           | Marketing | Utility/Footer     | Linked from inline glossary partials and footer; not a full primary tab.                        |
| Starter Kit                           | `/starter-kit`                        | Marketing | Section            | Prominent CTA target from compare/guides but not a global header anchor in its own right.       |
| Roadmap                               | `/roadmap`                            | Marketing | Utility/Footer     | Typically footer “Product”/“Roadmap” link rather than top-level header item.                    |
| State of SME Cybersecurity Report Hub | `/reports/state-of-sme-cybersecurity` | Marketing | Section            | Within “Reports/Research” cluster; linked from blog/guides/CTAs, not global header on MVP.      |

---

#### B3.2 Phase 2 — Essentials (Product Runtime)

Here Primary navigation is the **main authenticated app header/sidebar**, Section is **within-area rails/tabs**, Utility/Footer is minimal but can include “Status”/“Legal” links exposed inside the app frame. Flow-only pages are accessed only via linear flows or email links.

| Page Name                    | URL Pattern                      | Runtime    | Nav Tier           | Nav Placement / Notes                                                                      |
| ---------------------------- | -------------------------------- | ---------- | ------------------ | ------------------------------------------------------------------------------------------ |
| Log In                       | `/auth/login`                    | Essentials | Utility/Footer     | Exposed from marketing header/footer (“Log in”); outside authenticated primary app nav.    |
| Password Reset Request       | `/auth/reset`                    | Essentials | Flow-only (no nav) | Accessed from “Forgot password?” link on login only.                                       |
| Password Reset Confirm       | `/auth/reset/{token}`            | Essentials | Flow-only (no nav) | Email-token endpoint only; no nav exposure.                                                |
| Signup Start                 | `/signup`                        | Essentials | Primary            | Primary CTA target (from `/pricing`, `/how-it-works`); treated as root of signup spine.    |
| Signup Email Verification    | `/signup/verify`                 | Essentials | Flow-only (no nav) | Intermediate step in signup flow; no persistent nav entry.                                 |
| Signup Email Verified        | `/signup/verified`               | Essentials | Flow-only (no nav) | Landing after email verification; forwarded into checkout.                                 |
| Subscription Checkout        | `/signup/checkout`               | Essentials | Flow-only (no nav) | Billing step in flow; not exposed in nav.                                                  |
| Onboarding Complete          | `/signup/complete`               | Essentials | Flow-only (no nav) | One-time transitional surface; then routes into app primary nav.                           |
| Organisation Setup (Initial) | `/app/intake`                    | Essentials | Primary            | First primary nav destination after signup; appears in main app nav as “Intake”/“Setup”.   |
| Organisation Details (Edit)  | `/app/org`                       | Essentials | Section            | Section-level surface under Intake/Settings; reachable via local tabs/links from Intake.   |
| Evidence Dashboard           | `/app/evidence`                  | Essentials | Primary            | Core primary nav item (“Evidence”); hub for per-control flows.                             |
| Evidence Submission          | `/app/evidence/{control}`        | Essentials | Section            | Section-level within Evidence; navigated via dashboard list/rail, not direct primary item. |
| Evidence Review              | `/app/evidence/{control}/review` | Essentials | Section            | Same section as above; review tab/rail from specific control context.                      |
| Evaluation Overview          | `/app/evaluation`                | Essentials | Primary            | Primary nav item (“Evaluation” or “Readiness Check”).                                      |
| Evaluation Step              | `/app/evaluation/{step}`         | Essentials | Section            | Section-level within Evaluation; reached via stepper/rail, not separate primary entry.     |
| Evaluation Complete          | `/app/evaluation/complete`       | Essentials | Flow-only (no nav) | Terminal step of evaluation flow; no independent nav anchor.                               |
| Report View                  | `/app/report`                    | Essentials | Primary            | Primary nav item (“Report”); central value surface.                                        |
| Report Download              | `/app/report/download`           | Essentials | Flow-only (no nav) | Action endpoint only; invoked from Report View.                                            |
| Billing Dashboard            | `/app/billing`                   | Essentials | Primary            | Primary nav item (“Billing”), usually in a lower cluster of the main app nav.              |
| Subscription Management      | `/app/billing/subscription`      | Essentials | Section            | Section-level inside Billing; tab/rail item below Billing Dashboard.                       |
| Payment Methods              | `/app/billing/payment-methods`   | Essentials | Section            | Section-level inside Billing; switched via local tabs.                                     |
| Billing History              | `/app/billing/history`           | Essentials | Section            | Section-level inside Billing; invoice list tab.                                            |
| User Profile                 | `/app/settings/profile`          | Essentials | Section            | Section-level under Settings; accessed from Settings primary entry or avatar menu.         |
| Security Settings            | `/app/settings/security`         | Essentials | Section            | Section-level under Settings (Security tab/rail).                                          |
| Notification Preferences     | `/app/settings/notifications`    | Essentials | Section            | Section-level under Settings (Notifications tab/rail).                                     |
| Organisation Profile         | `/app/settings/org`              | Essentials | Section            | Section-level under Settings (Organisation tab/rail).                                      |

---

## **Appendix C — Metadata Schema**

This appendix defines the concrete metadata fields used across Marketing and Essentials surfaces. It is the binding contract between:

* the IA (structure, roles, and hierarchy)
* SEO keyword mapping (§5)
* content types (§6)
* taxonomy (§7)
* URL structure (§8)
* and the CMS / Next.js implementation.

No page may invent its own titles, descriptions, canonical URLs, or Open Graph fields outside this schema. All metadata must be derived from:

* the **page’s role and weight** (§4, Appendix B)
* its **SEO role and intent** (§5)
* its **content type** (§6)
* and the **taxonomy entries** defined in Appendix E.

---

### **C.1 Field Inventory**

The following fields define the minimum metadata model for all surfaces.

| Field Name              | Type               | Required | Applies To                           | Source of Truth / Constraints                                                               |
| ----------------------- | ------------------ | -------- | ------------------------------------ | ------------------------------------------------------------------------------------------- |
| `runtime`               | enum               | Yes      | All pages                            | `marketing` or `essentials`, must match §2 and Appendix B                                   |
| `structural_tier`       | enum               | Yes      | All pages                            | One of §4.1: `runtime_root`, `section_parent`, `cluster`, `content`, `state_ephemeral`      |
| `weight_class`          | enum               | Yes      | All pages                            | One of §4.3: `anchor`, `hub`, `standard`, `ephemeral_utility`                               |
| `nav_tier`              | enum               | Yes      | All pages                            | One of: `primary`, `section`, `utility_footer`, `flow_only` per §3 and Appendix B3          |
| `indexable`             | boolean            | Yes      | All pages                            | `true` for search-targeted Marketing surfaces; `false` for Essentials and operational pages |
| `seo_role`              | enum               | Yes*     | All indexable pages                  | One of: `pillar`, `supporting`, `long_tail`, `non_seo` per §5.1–5.5                         |
| `seo_primary_intent`    | string / intent ID | Yes*     | All indexable pages                  | Must reference a defined intent in §5 and Appendix E                                        |
| `seo_secondary_intents` | array<intent ID>   | No       | Indexable pages                      | Max 2; must be in same semantic neighbourhood as primary (§5.3)                             |
| `canonical_url`         | path string        | Yes      | All pages                            | Must match the IA pattern in §8 and the URL in Appendix B                                   |
| `meta_title`            | string             | Yes*     | All indexable pages                  | Patterned off `seo_primary_intent`; length and pattern rules below                          |
| `meta_description`      | string             | Yes*     | All indexable pages                  | Must reflect primary intent, no keyword stuffing                                            |
| `robots_directives`     | enum / string      | No       | Selected pages                       | e.g. `index,follow`, `noindex,nofollow`; must align with `indexable`                        |
| `og_title`              | string             | No       | Key marketing surfaces               | Derived from `meta_title` with optional brand suffix adjustments                            |
| `og_description`        | string             | No       | Key marketing surfaces               | Derived from `meta_description`                                                             |
| `og_type`               | enum               | No       | Key marketing surfaces               | Typically `website` or `article` based on content type (§6)                                 |
| `og_image_key`          | enum / asset key   | No       | Key marketing surfaces               | Must reference an approved asset from the brand system (BIG)                                |
| `taxonomy_categories`   | array<category ID> | Yes*     | Editorial content (blog/guides/etc.) | Must reference Appendix E; one core category required (§7.1)                                |
| `taxonomy_tags`         | array<tag ID>      | No       | Editorial content                    | Must reference Appendix E; limited set per §7.3.2                                           |
| `taxonomy_industries`   | array<industry ID> | No       | Industry-scoped content              | From Appendix E; constrained set (§7.2.1)                                                   |

* Required only when `indexable = true`. When `indexable = false`, `seo_role` must be `non_seo` and `seo_*` fields may be empty.

---

### **C.2 Runtime Metadata Profiles**

Different runtimes and page roles use different subsets of the schema.

#### **C.2.1 Marketing Runtime Profile**

For **Marketing** pages (`runtime = marketing`):

* `indexable = true` **except** for:

  * pure operational surfaces (for example `/resources/{slug}/thanks`),
  * any page explicitly marked Non-SEO in Appendix B.

* Minimum required fields:

  * `runtime`, `structural_tier`, `weight_class`, `nav_tier`
  * `indexable`
  * `seo_role`, `seo_primary_intent` (if indexable)
  * `canonical_url`, `meta_title`, `meta_description` (if indexable)

* Editorial content (blog, guides, case studies, research hubs) must also include:

  * `taxonomy_categories` (1 core category)
  * `taxonomy_tags` (controlled list)

* High-value surfaces (Home, Features, Pricing, Why, How It Works, Industries, Compare hub, State-of hub) should also set:

  * `og_title`, `og_description`, `og_type`, `og_image_key`.

#### **C.2.2 Essentials Runtime Profile**

For **Essentials** pages (`runtime = essentials`):

* `indexable = false` for all pages.
* `seo_role = non_seo`.
* `seo_primary_intent`, `seo_secondary_intents`, `taxonomy_*` fields are normally empty.

Required:

* `runtime`, `structural_tier`, `weight_class`, `nav_tier`
* `indexable` (must be `false`)
* `canonical_url`
* Minimal `meta_title` / `meta_description` for UX, not SEO.

Identity and onboarding surfaces (login, signup, reset) may additionally specify `robots_directives = "noindex,nofollow"` explicitly.

---

### **C.3 Field-Level Rules and Validation**

This subsection ties the fields directly back to IA rules.

#### **C.3.1 Structural and Navigation Consistency**

* `runtime`, `structural_tier`, `weight_class`, and `nav_tier` must match the values in Appendix B for the corresponding page.
* A page marked as:

  * `nav_tier = primary` must be a **Runtime Root** or **Sectional Parent** (`structural_tier` in §4.1).
  * `nav_tier = utility_footer` must be a **Standard** or **Ephemeral/Utility** weight page and typically legal/trust/operational surfaces.
  * `nav_tier = flow_only` must not appear in any visible navigation and is usually State/Ephemeral (for example reset tokens, confirmations).

Validation rule:

> No change to `nav_tier` is permitted without a corresponding IA change in §3 and Appendix B.

#### **C.3.2 SEO Role and Intent Alignment**

For `indexable = true`:

* `seo_role` must be consistent with `weight_class`:

  * `anchor` or `hub` ⇒ usually `pillar` or `supporting`
  * `standard` ⇒ usually `supporting` or `long_tail`
  * `ephemeral_utility` ⇒ usually `non_seo` or not indexable.

* `seo_primary_intent`:

  * must reference a valid intent ID defined in §5 and Appendix E;
  * must be unique per page; no page may declare more than one primary intent.

* `seo_secondary_intents`:

  * max 2;
  * must belong to the same semantic neighbourhood as the primary intent (§5.3).

Validation rule:

> Any change to `seo_role` or `seo_primary_intent` must be reflected in §5 and Appendix E before being deployed.

#### **C.3.3 Canonical URL and Indexability**

* `canonical_url` must:

  * match the pattern in §8 for the page’s type;
  * match the URL declared for that page in Appendix B.

* For `indexable = true`:

  * `robots_directives` must not contain `noindex`.

* For `indexable = false`:

  * `robots_directives` **may** explicitly include `noindex,nofollow`, especially for Essentials and tokenised flows.

Validation rule:

> No page may have `indexable = true` and `robots_directives` including `noindex`.

#### **C.3.4 Title and Description Patterns**

For indexable Marketing pages:

* `meta_title`:

  * must clearly express the page’s primary intent;
  * must contain either the canonical phrase for `seo_primary_intent` or an approved synonym from Appendix E;
  * may include a brand suffix (for example `" | Transcrypt"`) for pillars and key hubs.

* `meta_description`:

  * must summarise the primary intent in natural language;
  * must not be used as a keyword dump;
  * should be unique per page.

For Essentials pages:

* `meta_title` and `meta_description` are UX labels, not SEO assets; they must describe purpose clearly, but there is no keyword targeting.

---

### **C.4 Implementation Notes for CMS and Next.js**

To prevent drift between IA and implementation:

* The CMS and/or content model must:

  * use enumerated lists for `runtime`, `structural_tier`, `weight_class`, `nav_tier`, `seo_role`;
  * restrict `seo_primary_intent`, `seo_secondary_intents`, `taxonomy_*` fields to IDs defined in Appendix E;
  * automatically set `indexable = false` and `seo_role = non_seo` for Essentials templates.

* The Next.js metadata layer must:

  * derive `<title>`, `<meta name="description">`, `<link rel="canonical">`, and Open Graph tags directly from these fields;
  * refuse to emit canonical URLs that do not match the IA patterns.

Any extension to metadata behaviour (for example new social graph fields, additional SEO special cases) must:

1. be defined here (Appendix C),
2. be wired into §5/§7/§8 as needed, and
3. then be implemented in the CMS / Next.js layer.

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

## **Appendix E — Taxonomy Catalogue**

This appendix defines the authoritative taxonomy used across all editorial and marketing content in the Marketing runtime. It is the lookup table for:

* category and tag IDs used in `taxonomy_categories` and `taxonomy_tags` (Appendix C)
* industry and audience taxonomies for verticalised content
* synonyms and deprecated terms that must be normalised to canonical IDs

No new category, tag, industry, or synonym set may be introduced in content, the CMS, or Tailwind/CSS utility layers unless it is first added here.

---

### **E.1 Category Catalogue (Core vs Extended)**

Core categories describe the primary thematic buckets for content. Extended categories are optional refinements used when the corpus grows.

| Category ID           | Label                       | Type     | Scope              | Description                                                         | Status |
| --------------------- | --------------------------- | -------- | ------------------ | ------------------------------------------------------------------- | ------ |
| `foundations`         | Foundations                 | Core     | Blog, Guides       | Basics of SME security, concepts, terminology, and starting points. | Active |
| `controls`            | Controls & Practices        | Core     | Blog, Guides       | Concrete security and compliance controls, mapped to schemes.       | Active |
| `people-process`      | People & Process            | Core     | Blog, Guides       | Culture, training, roles, and process design for SMEs.              | Active |
| `incidents-response`  | Incidents & Response        | Core     | Blog, Guides       | Preparation, detection, and response to incidents or near-misses.   | Active |
| `vendor-supply-chain` | Vendor & Supply Chain       | Core     | Blog, Guides       | Third-party risk, MSPs, SaaS dependencies, and supplier posture.    | Active |
| `regulation-schemes`  | Regulation & Schemes        | Core     | Blog, Guides       | Cyber Essentials, NIS/NIS2, UK GDPR, ICO expectations, etc.         | Active |
| `strategy-risk`       | Strategy, Risk & Governance | Core     | Blog, Guides       | Risk framing, board communication, prioritisation, and strategy.    | Active |
| `stories-case`        | Stories & Case Studies      | Core     | Blog, Case Studies | Narrative content and case studies, including anonymised examples.  | Active |
| `product-platform`    | Product & Platform          | Extended | Blog               | Product updates, roadmap commentary, and platform deep dives.       | Active |
| `opinion-commentary`  | Opinion & Commentary        | Extended | Blog               | Opinionated takes, commentary on the wider ecosystem.               | Active |
| `how-to-guides`       | How-To Guides               | Extended | Guides             | Task-driven guides with step-by-step structure.                     | Active |
| `templates-toolkits`  | Templates & Toolkits        | Extended | Guides, Resources  | Checklists, templates, and bundles (e.g. Starter Kit content).      | Active |

**Rules**

* Every editorial item (blog, guide, case study, report) must have **exactly one** Core category and may have **zero or one** Extended category.
* New Core categories require an IA update in §7 before being added here.
* Extended categories can be added here but must not overlap semantically with an existing Core.

---

### **E.2 Tag Catalogue (Topic / Technique / Risk / Scheme)**

Tags provide finer-grained classification within categories. Tags are typed so that cross-referential partials (Appendix D) can reason about them.

| Tag ID                 | Label                            | Tag Type  | Suggested Usage                                             | Status |
| ---------------------- | -------------------------------- | --------- | ----------------------------------------------------------- | ------ |
| `ce-basics`            | Cyber Essentials Basics          | Scheme    | Intro content on CE scope, levels, and expectations.        | Active |
| `ce-self-assessment`   | Cyber Essentials Self-Assessment | Scheme    | Content about DIY/self-assessment paths.                    | Active |
| `ce-plus`              | Cyber Essentials Plus            | Scheme    | Content on audited/Plus journeys.                           | Active |
| `backup-recovery`      | Backup & Recovery                | Technique | Controls and practices for backups, restoration, testing.   | Active |
| `mfa-authentication`   | Multi-Factor Authentication      | Technique | Anything focused on MFA setup, policy, and rollout.         | Active |
| `password-policy`      | Password Policy                  | Technique | Password standards, rotation policies, and UX trade-offs.   | Active |
| `patching-updates`     | Patching & Updates               | Technique | OS, application, and firmware patching.                     | Active |
| `endpoint-security`    | Endpoint Security                | Topic     | AV/EDR, hardening, and device management topics.            | Active |
| `network-segmentation` | Network Segmentation             | Topic     | Segmentation, VLANs, zoning, and blast radius.              | Active |
| `phishing-awareness`   | Phishing & Awareness             | Topic     | Human-centric training and simulated phishing.              | Active |
| `incident-playbooks`   | Incident Playbooks               | Topic     | Concrete playbooks and runbooks.                            | Active |
| `board-reporting`      | Board & Leadership Reporting     | Topic     | Communicating risk and posture to non-technical leaders.    | Active |
| `sme-finance`          | SME Finance & Insurance          | Topic     | Insurance, premiums, and financial consequences of posture. | Active |
| `ops-automation`       | Operations & Automation          | Topic     | Automated checks, pipelines, and continuous verification.   | Active |
| `uk-regulation`        | UK Regulation                    | Region    | UK-specific regulatory discussions.                         | Active |

**Rules**

* Maximum tag count per item: **5**, unless explicitly waived in §7.3.
* Tags must be chosen from this catalogue; no ad-hoc tag strings in the CMS.
* New tags must specify `Tag Type` and justify how they avoid duplicating existing tags.

---

### **E.3 Industry and Audience Taxonomy**

Industry and audience taxonomies drive verticalised content (`/industries/{slug}`) and “For Your Industry” partials (Appendix D).

| Industry ID       | Label                       | Description                                              | Status |
| ----------------- | --------------------------- | -------------------------------------------------------- | ------ |
| `healthcare`      | Healthcare                  | Clinics, practices, care providers, small health orgs.   | Active |
| `professional`    | Professional Services       | Legal, accounting, consulting, boutique agencies.        | Active |
| `retail-ecom`     | Retail & eCommerce          | Shops, online stores, multi-channel retailers.           | Active |
| `manufacturing`   | Manufacturing & Engineering | Light manufacturing, fabrication, industrial SMEs.       | Active |
| `charity-third`   | Charity & Third Sector      | Charities, non-profits, community organisations.         | Active |
| `education`       | Education                   | Independent schools, training providers, small colleges. | Active |
| `public-adjacent` | Public-Adjacent SMEs        | Private providers serving public sector / gov contracts. | Active |

Optional **Audience** facets:

| Audience ID     | Label              | Description                                   | Status |
| --------------- | ------------------ | --------------------------------------------- | ------ |
| `owner-founder` | Owner / Founder    | Owner-operators, MDs, founders.               | Active |
| `it-lead`       | IT / Tech Lead     | In-house tech responsible, even if part-time. | Active |
| `ops-manager`   | Operations Manager | Ops/office managers responsible for delivery. | Active |
| `compliance`    | Compliance / Risk  | People tasked with policy, risk, governance.  | Active |

**Rules**

* Industry assignment is optional but recommended for:

  * case studies,
  * industry pages,
  * any content invoked by “For Your Industry” partials.
* Audience facets are used only if they materially shape the advice; otherwise they are omitted.

---

### **E.4 Synonyms and Canonical Mapping**

To avoid fragmented taxonomy caused by near-duplicates or jargon variations, synonyms are explicitly mapped onto canonical terms.

| Synonym / Variant             | Canonical Term ID    | Notes                                           |
| ----------------------------- | -------------------- | ----------------------------------------------- |
| `2fa`                         | `mfa-authentication` | Treat 2FA as a sub-case of MFA.                 |
| `multi factor authentication` | `mfa-authentication` | Normalised to standard spelling.                |
| `cyber essentials plus`       | `ce-plus`            | Case and spacing normalised.                    |
| `incident runbooks`           | `incident-playbooks` | Same conceptual space; use single canonical tag |
| `board reporting`             | `board-reporting`    | Spacing/wording normalised.                     |
| `uk regs`                     | `uk-regulation`      | Informal phrasing mapped to canonical term.     |

**Rules**

* CMS/editor UIs should present only canonical IDs; synonyms are for ingestion/migration and search indexing.
* If content is imported from another system with free-text tags, synonyms must be mapped here before being accepted.

---

### **E.5 Deprecated or Merged Taxonomy Entries**

When taxonomy changes, old IDs must not simply disappear; they are recorded and redirected here.

| Old ID / Label     | Replacement Canonical ID | Reason                        | Effective From | Notes                      |
| ------------------ | ------------------------ | ----------------------------- | -------------- | -------------------------- |
| `general-security` | `foundations`            | Too vague; folded into core.  | TBC            | Existing content remapped. |
| `misc`             | *none*                   | Junk bucket; content cleaned. | TBC            | Must not be reused.        |

**Rules**

* Deprecated IDs must not be used for new content.
* Any change here must be accompanied by a content migration plan (search/replace or manual curation).

---

# **Appendices That Are PROBABLY Needed (but optional until content expands)**

## **Appendix F — Linkage Map (Cross-Link Diagram Set)**

Internal cross-links, especially SEO-driven or journey-critical ones, often need diagrammatic representation.

This appendix is optional until the system has 20+ pages or linked clusters that must be visualised.

## **Appendix G — Search Configuration (If Search Exists in MVP)**

If you add site or blog search (even basic), you will need:

* indexed content types
* stopword lists
* weighting rules
* exclusions
* ranking adjustments

If search is postponed, this appendix is postponed.

---