# **1. Introduction**

This Information Architecture defines the structural model of Transcrypt across the Marketing runtime and the Essentials application. It establishes how the system’s surfaces are organised, how users move between them, and how meaning, hierarchy, and navigability are maintained. The IA sits beneath the behavioural rules in the PDS and the architectural constraints in the SAIS, ensuring every page, path, and transition reflects the product intent described in the PRD. This document provides the skeletal framework that governs structure, discoverability, and user flow, forming the basis for coherent design, consistent routing, and predictable interaction across the entire platform.

# **2. Full Sitemap**

The sitemap defines every surface the user can reach across both the Marketing runtime and the Essentials application, establishing the structural outline of the platform. It serves as the descriptive map of how pages are grouped and related. The complete, authoritative list of all pages — including identifiers, purpose, and runtime classification — is maintained in Appendix B and should be used alongside this sitemap for implementation and verification.

## **2.1 System Surfaces Overview**

## **2.2 Marketing Runtime Surfaces**

## **2.3 Essentials Runtime Surfaces**

## **2.4 Cross-Runtime Junctions**

## **2.5 Hidden or Technical Surfaces (non-navigable)**

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