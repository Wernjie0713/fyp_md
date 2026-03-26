# Literature Review

## Introduction

This chapter reviews scholarly and standards-based literature that grounds the proposed Sales and Payment Analytics Platform as a company-owned reporting redundancy system for an externally managed point-of-sale (POS) reporting portal. The review is structured to support an evidence-based proposal: fundamental concepts are introduced first, then related work and comparative discussion are synthesised to justify the chosen architecture and validation approach, followed by a brief discussion of the technologies selected for implementation.

## Fundamental Theory and Concepts

### Vendor Dependency, Data Sovereignty, and Continuity Risk

Cloud computing is commonly characterised as an on-demand model for shared and configurable computing resources (Mell & Grance, 2011). In organisational settings, reliance on external cloud services can introduce dependency risks, including reduced control over availability, security controls, and change management processes (Badger et al., 2012; Jansen & Grance, 2011). In operational reporting contexts, dependency on a vendor-managed POS reporting portal is therefore not only a technical decision but also an availability and governance concern for business functions that require timely access to sales and payment information.

The literature also highlights lock-in effects in cloud adoption, where switching providers or rebuilding capabilities can incur high technical and operational costs (Armbrust et al., 2010). These costs are amplified when report logic exists primarily in a vendor portal and is not fully documented or reproducible by the organisation. Consequently, data sovereignty and continuity-oriented initiatives often prioritise ensuring that the organisation retains a usable copy of its own transactional data and can independently generate critical operational and financial reporting outputs.

### Data Warehousing and Replication-Based Analytical Stores

Data warehousing literature frames a data warehouse as an integrated repository designed to support reporting and analysis rather than operational transaction processing (Inmon, 2005; Kimball & Ross, 2013). Traditional designs frequently apply modelling and transformation choices (e.g., dimensional modelling) to optimise analytical queries, but such transformations can increase complexity and may obscure traceability to source records if governance is weak.

For reporting redundancy, an alternative design is a fidelity-first replicated analytical store that preserves the structure and content of source transactional tables. This approach prioritises traceability and simplifies reconciliation by reducing ambiguity about how report outputs relate to replicated source records. In practice, the choice between an optimised dimensional model and a replicated fidelity-first store depends on the primary objective: performance optimisation versus assured traceability and parity with externally generated reports (Inmon, 2005; Kimball & Ross, 2013).

### Data Integration Pipelines: ETL vs ELT and Idempotent Loads

Data integration pipelines are commonly described using ETL (extract-transform-load), where data is transformed prior to loading into the target repository (Kimball & Caserta, 2004). Contemporary data platform practices also adopt ELT patterns, in which raw data is loaded first and transformations are applied in the target environment. This aligns with schema-on-read approaches that preserve raw data while enabling flexible downstream transformations (Azzabi et al., 2024).

For operational reliability, pipeline design must consider rerun safety and operational recovery. Idempotent loading patterns reduce the risk of duplicate records and support repeatable refresh cycles when failures occur or when late data corrections are detected. In practice, idempotency is achieved through controlled load boundaries (e.g., date-range refresh) and deterministic processing rules that yield the same replicated state for the same boundary.

### Replication, Availability, and Consistency Considerations

Replication is used to improve availability and support resilience by maintaining copies of data across systems. In distributed and replicated systems, trade-offs between consistency, availability, and operational complexity are central design considerations (Kleppmann, 2017). For reporting redundancy, strict real-time consistency is typically not required; instead, the practical objective is timely access to sufficiently recent and internally consistent data, supported by a refresh process and validation evidence that stakeholders can trust during reporting-intensive periods.

Accordingly, replication design in reporting contexts is commonly paired with operational controls (e.g., rerun capability, logging, and post-load checks) to manage failure recovery and to provide confidence in the replicated state. These controls support both day-to-day reporting and the investigative workflows that arise when discrepancies are detected.

### Schema-on-Read, Semantic Layers, and Service Interfaces

Schema-on-read practices emphasise preserving raw datasets and applying transformations at consumption time, which supports iterative refinement of business logic while maintaining traceability (Azzabi et al., 2024). A semantic layer operationalises this concept by centralising metric definitions and business rules so that multiple report consumers obtain consistent outputs over time. In this project context, reconstructed report logic is treated as semantic-layer logic and exposed through an API service, which decouples frontend report presentation from database implementation details.

For service delivery, REST is a widely cited architectural style for network-based systems, emphasising stateless communication, uniform interfaces, and resource-oriented design (Fielding, 2000). A RESTful API therefore provides a standard mechanism to deliver report outputs to a portal while keeping report logic versioned and auditable at the service layer.

### Reverse Engineering and Black-Box Validation of Legacy Reports

When vendor report logic is proprietary and not fully documented, reverse engineering and design recovery provide a structured lens for inferring behaviour from observable artefacts (Chikofsky & Cross, 1990). In such settings, black-box testing methods support parity validation by comparing system outputs against vendor exports under identical parameters (Myers et al., 2011). For reporting platforms, this process extends beyond matching totals; it also requires validating calculation rules and edge-case handling (e.g., returns, voids, split tenders, and rounding behaviour) to reduce operational reconciliation risk.

### Data Quality and Reconciliation for Financial Reporting

Data quality is commonly framed as fitness for use, where suitability depends on the consumer’s needs and the use context (Wang & Strong, 1996). Standards and reference models describe core quality characteristics such as accuracy, completeness, consistency, and timeliness (International Organization for Standardization, 2008). In sales and payment reporting, these characteristics are directly relevant because stakeholders require totals, breakdowns, and reconciliation outputs that are dependable for decision-making and audit preparation.

Data quality management literature discusses practical techniques for assessing and improving data quality, including profiling and validation rules (Batini & Scannapieco, 2006). In replicated reporting contexts, these techniques are operationalised through reconciliation checks (e.g., cross-report consistency of totals) and repeatable parity comparisons against vendor exports for agreed validation windows.

### Iterative Development Approaches for Evolving Requirements

Iterative development approaches emphasise incremental delivery and feedback-driven refinement (Beck et al., 2001). Scrum formalises iterative planning and review through time-boxed cycles and continuous refinement (Schwaber & Sutherland, 2020). In software engineering practice, iterative approaches are commonly recommended when requirements are uncertain or when continuous validation is required to manage risk (Pressman & Maxim, 2014; Sommerville, 2015). In report reconstruction projects, requirements and edge cases often emerge during parity validation, which makes iterative delivery suitable for progressively stabilising business rules while retaining validation evidence.

## Related Previous Researches/Systems and Comparative Discussion

The broader literature provides supporting evidence for the project’s motivation and approach. Cloud computing discussions recognise vendor dependency and lock-in as concerns that can affect cost, portability, governance, and operational control (Armbrust et al., 2010; Badger et al., 2012). Data warehousing literature describes organisational consolidation of data to improve reporting reliability and analytical access (Inmon, 2005; Kimball & Ross, 2013). Survey work on data lakes and schema-on-read practices further discusses the value of preserving raw data and applying transformations flexibly at the consumption layer (Azzabi et al., 2024).

However, fewer sources provide detailed guidance on reconstructing proprietary vendor reporting logic while demonstrating report-level parity through defensible validation artefacts. This creates a practical gap for organisations that require continuity reporting but must operate without full access to vendor calculation definitions.

Table 2.1 provides a comparative discussion between a vendor-managed reporting portal and a company-owned redundancy platform, highlighting the trade-offs that motivate the proposed approach.

| Criterion | Vendor-managed portal only | Company-owned redundancy platform (proposed) |
| --- | --- | --- |
| Availability and continuity | Reporting access depends on vendor service availability and change management (Badger et al., 2012; Jansen & Grance, 2011). | Provides an alternative reporting path by operating on replicated data under organisational control (Kleppmann, 2017). |
| Data transparency and traceability | Users typically interact through portal views and exports; traceability to raw transactions may be limited by vendor interface constraints. | Fidelity-first replication supports traceability from report outputs to replicated source records (Inmon, 2005). |
| Report logic control | Report definitions and changes are vendor-controlled; organisational adaptation is constrained. | Business rules are reconstructed and versioned in a semantic layer, enabling auditable updates. |
| Validation burden | Vendor portal is treated as the reference, but internal validation is limited to exported outputs. | Requires black-box parity validation and reconciliation evidence to build trust in reconstructed logic (Myers et al., 2011; Wang & Strong, 1996). |
| Cost and complexity | Lower internal build complexity, but potential lock-in and dependency costs (Armbrust et al., 2010). | Higher engineering and validation effort initially; benefits depend on sustained operational use and governance. |

*Table 2.1: Comparative discussion of vendor-managed reporting versus company-owned redundancy reporting*

The literature also motivates a design trade-off between transformation-heavy analytical models and replication-first designs. Dimensional modelling supports analytical performance and standardised business views, whereas replication-first designs prioritise traceability and parity alignment to source representations (Inmon, 2005; Kimball & Ross, 2013). For continuity reporting where parity and reconciliation are primary goals, the proposed approach adopts replication for fidelity and applies transformations at the semantic layer, consistent with schema-on-read principles (Azzabi et al., 2024).

Based on this synthesis, the proposed approach combines a fidelity-first replicated datastore to support traceability and reconciliation, an ELT workflow with idempotent refresh to support safe reruns and late adjustments, a semantic/API layer for centralised business rules and service delivery, reverse engineering with black-box parity validation to infer and validate proprietary behaviour, and iterative development practices to manage emerging edge cases (Azzabi et al., 2024; Beck et al., 2001; Chikofsky & Cross, 1990; Kleppmann, 2017; Myers et al., 2011; Wang & Strong, 1996).

## Technology Used

The proposed platform is implemented using Microsoft SQL Server for the replicated transactional schema and a Python-based ELT workflow for extraction and loading. Report reconstruction is implemented at the service layer using FastAPI to expose RESTful endpoints for report retrieval, while the reporting portal is implemented using React to support user workflows for parameter selection, tabular viewing, and export (FastAPI, n.d.; React, n.d.). The REST architectural style provides the guiding principles for the API interface (Fielding, 2000). These technologies are selected as engineering choices that support maintainability and iterative development within the organisational environment, while the academic justification for the overall architectural approach is grounded in the literature synthesised in Sections 2.2 and 2.3.

## Summary (Synthesis and Rationale Map)

This chapter reviewed key concepts and prior work relevant to dependency risk, replication-based analytical stores, ELT workflows, schema-on-read semantic layers, reverse engineering and black-box validation, data quality and reconciliation, and iterative development. Table 2.2 summarises how these literature-backed concepts justify the proposed approach in an evidence-based manner.

| Method/design choice | Rationale grounded in literature | Key sources |
| --- | --- | --- |
| Iterative development for report reconstruction | Requirements and edge cases emerge during parity validation; iterative delivery supports risk reduction through frequent feedback and refinement. | Beck et al. (2001); Schwaber & Sutherland (2020); Pressman & Maxim (2014); Sommerville (2015) |
| ELT workflow with idempotent refresh | Loading raw data first supports schema-on-read transformations and iterative rule refinement; idempotent boundaries support reruns and recovery. | Kimball & Caserta (2004); Azzabi et al. (2024) |
| Fidelity-first replication for traceability | Preserving source structure supports reconciliation and explainability of outputs, which is central in financial reporting contexts. | Inmon (2005); Kleppmann (2017) |
| Consistency/availability framing for reporting | Reporting prioritises timely, consistent snapshots rather than strict real-time consistency; operational controls improve reliability. | Kleppmann (2017) |
| Semantic layer exposed via API | Centralising business rules reduces metric drift and decouples presentation from storage; supports auditable evolution. | Azzabi et al. (2024); Fielding (2000) |
| Reverse engineering + black-box parity validation | Proprietary vendor logic requires inference from observable behaviour; black-box testing provides empirical parity evidence. | Chikofsky & Cross (1990); Myers et al. (2011) |
| Data quality and reconciliation checks | Fitness-for-use for financial reporting depends on accuracy, completeness, and consistency; reconciliation operationalises quality assurance. | Wang & Strong (1996); International Organization for Standardization (2008); Batini & Scannapieco (2006) |
| Cloud dependency risk and lock-in considerations | Vendor dependence can introduce availability/security/change-management risks and lock-in costs; continuity designs mitigate exposure. | Mell & Grance (2011); Badger et al. (2012); Jansen & Grance (2011); Armbrust et al. (2010) |

*Table 2.2: Synthesis / rationale map linking proposed choices to literature*
