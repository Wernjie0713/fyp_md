# Analysis And Design

## Introduction

This chapter presents the analysis and design of the proposed Sales and Payment Analytics Platform. The chapter translates the problem statement and objectives into concrete requirements and design artefacts, including system analysis, system requirements, current system analysis, and detailed system design. The academic basis for the design choices (replication-first traceability, ELT, semantic layers, reconciliation, and iterative delivery) is grounded in Chapter 2 (see Table 2.3), while Chapter 3 describes the methodology used to execute and validate the proposed design.

## System Analysis

### Case Study Context (Continuity Reporting for Sales and Payments)

The case study concerns sales and payment reporting in a large-scale food and beverage (F&B) retail setting where transaction processing and reporting access are provided through an externally managed POS environment and reporting portal. Continuity reporting is operationally important for Finance (reconciliation and month-end closing) and Operations (outlet-level oversight), particularly when report access is time-sensitive. In this context, the core system problem is that reporting access is mediated through vendor-managed interfaces and exports, which can constrain ad hoc investigation and introduce operational risk when the portal is unavailable (see Chapter 2, Section 2.2.1).

### Stakeholders and Role-Based View

Stakeholders are represented in a role-based manner to clarify reporting needs without asserting an official organisation chart.

| Stakeholder group | Primary activities | Reporting needs (examples) |
| --- | --- | --- |
| Finance users | Reconciliation, month-end closing, audit preparation | Daily totals, payment breakdowns, returns/adjustments visibility, export for reconciliation |
| Operations users | Outlet performance monitoring, operational oversight | Outlet-level daily summaries, trend visibility, payment mix, exception/return checks |
| Internal technical team | Platform maintenance and enhancements | Traceability, logging/monitoring, rerun support, controlled release of report rule changes |

*Table 4.1: Stakeholder groups and reporting needs (role-based view)*

### System Requirements Gathering Techniques

Requirements are derived through document analysis of vendor portal reports and exported files, together with stakeholder feedback and clarification sessions with Finance and Operations users. This approach is consistent with a black-box reporting environment where proprietary report rules must be inferred from observable inputs and outputs (see Chapter 2, Section 2.2.6). No survey instruments or formal interviews are claimed; the emphasis is on traceable artefacts (exports, parameter settings) and acceptance criteria agreed for continuity reporting.

## System Requirements

### Functional Requirements (FR)

The functional requirements are summarised in Table 4.2.

| ID | Functional requirement |
| --- | --- |
| FR1 | The system shall replicate relevant sales and payment transactional datasets from the external POS environment into a company-owned database on a scheduled basis. |
| FR2 | The system shall generate the targeted sales and payment reports based on the replicated datasets. |
| FR3 | The system shall provide report filtering by report-specific parameters (at minimum outlet and date range). |
| FR4 | The system shall support exporting report outputs (e.g., tabular export) to support reconciliation workflows. |
| FR5 | The system shall expose report logic through an API layer to decouple the frontend from database schema changes. |

*Table 4.2: Functional requirements for the proposed platform*

### Non-Functional Requirements (NFR)

The non-functional requirements are summarised in Table 4.3.

| ID | Non-functional requirement |
| --- | --- |
| NFR1 | Data fidelity and traceability: report outputs shall remain traceable to replicated source records and support reconciliation checks. |
| NFR2 | Availability: the platform shall provide an alternative reporting path when the vendor portal is unavailable. |
| NFR3 | Performance (operational usability): report responses shall be delivered within an acceptable time for user workflows during reporting-intensive periods (e.g., month-end closing). |
| NFR4 | Security: the system shall operate as a read-only reporting platform and implement appropriate access controls. |
| NFR5 | Maintainability: report logic shall be structured to support iterative updates when edge cases or rule changes are discovered. |

*Table 4.3: Non-functional requirements for the proposed platform*

### Constraints and Assumptions

The platform is designed under several constraints and assumptions. Access to the external POS environment is restricted and may be read-only. The current project phase targets sales and payment reporting for a defined set of high-priority reports, and the platform does not implement write-back to the vendor POS system. The replication cadence is designed to support operational reporting needs rather than real-time transactional processing. Design decisions in this chapter therefore prioritise traceability, repeatability, and operational controls for continuity reporting (see Chapter 2, Sections 2.2.3闁?.2.7).

## Current System Analysis

The current reporting workflow relies on a vendor-managed reporting portal as the primary interface for sales and payment reports. Users typically select a report, apply parameters (e.g., outlet and date range), and export results for reconciliation activities. This workflow can constrain ad hoc analysis because users cannot freely query underlying transactional records, and operational reporting can be disrupted if portal access is degraded during reporting-intensive periods. Issue resolution is also dependent on vendor support processes, which can misalign with internal reporting timelines (see Chapter 2, Section 2.2.1).

![Figure 4.1: Current vendor-dependent reporting workflow (simplified)](#)

*Figure 4.1: Current vendor-dependent reporting workflow (simplified)*

## System Design

### System Architecture

The proposed system is organised into four logical layers: a source layer (external POS environment), a replication layer (ELT extraction and load), a semantic/API layer (reconstructed report logic exposed via RESTful endpoints), and a presentation layer (web portal for report access and export). This layered design supports traceability and governance by centralising report rules at the semantic layer and operating on replicated data under organisational control (see Chapter 2, Sections 2.2.4闁?.2.5).

As shown in Figure 4.2, data flows from the vendor-managed POS environment through the replication and SQL Server layers into the semantic/API layer before being exposed to Finance and Operations users through the reporting portal. The figure therefore illustrates how report delivery is shifted from a vendor-managed reporting path to a company-controlled analytical path while preserving separation between storage, business-rule processing, and presentation.

![Figure 4.2: Proposed logical architecture of the analytics platform](#)

*Figure 4.2: Proposed logical architecture of the analytics platform*

### Component Explanations

Table 4.4 summarises each component's responsibility and key design considerations. These component-level responsibilities are aligned with the literature reviewed in Chapter 2, particularly the discussions on replication-based analytical stores and ELT workflows (Sections 2.2.2-2.2.4), semantic layers and service interfaces (Section 2.2.5), and workflow/interface considerations for operational reporting portals (Section 2.4). Table 2.3 provides the consolidated synthesis linking these design choices to their academic rationale.

| Component | Responsibility | Key design considerations |
| --- | --- | --- |
| External POS environment | Source of transactional records and vendor report exports | Access constraints; parameter consistency; late corrections |
| Replication / ELT scripts | Extract and load source data into the replica | Idempotent refresh boundaries; logging; rerun controls; error handling |
| SQL Server replica | Store 1:1 replicated tables and support report queries | Traceability; indexing strategy; retention boundaries; operational monitoring |
| FastAPI semantic layer | Encapsulate report rules and expose stable report endpoints | Versioned business rules; consistent metric definitions; parameter validation; authentication/authorisation |
| Reporting portal | Provide continuity access to reports and exports | Usability during month-end; consistent filtering; totals/subtotals; export fidelity |

*Table 4.4: Component responsibilities and design considerations*

### Data Engineering and API Design

#### Data Sources and Replication Boundary

The primary data source is the vendor-managed POS transactional database, which is accessed for read-only replication into the company-owned SQL Server environment. At a logical level, the source data required by the targeted reports can be grouped into transaction-header records, line-item records, payment or tender records, and supporting master/reference data. Transaction-header data provides the reporting grain and status context for each sale, line-item data supports item-level analysis and quantity or amount breakdowns, payment data supports payment-type reporting and reconciliation, and master/reference data such as outlet/location and item/product attributes is required to interpret and group transactional records consistently. Because physical table and column names are vendor-specific, the design documents these sources conceptually while preserving a 1:1 structural representation in the replica for traceability. The main conceptual entities used by the targeted reports are summarised later in Table 4.5.

Replication boundaries are defined report by report by tracing required output columns and business rules back to the minimum set of source tables needed for reconstruction. Within the current project scope, transactional data replication is generally bounded from 2025 onward in line with organisational storage constraints, whereas reference and master tables are replicated in full because they are comparatively smaller and are needed to interpret transactional records consistently across reporting periods. This selective but fidelity-preserving boundary supports operational reporting windows while allowing late corrections to be refreshed during subsequent runs.

#### Refresh Cadence and Idempotent Load Pattern

The ELT workflow is designed to refresh operational data on a scheduled basis and to account for late corrections (e.g., late voids, adjustments, and return postings). In the current project stage, refresh execution remains manual, while the planned operational design is to perform scheduled refreshes at midnight each day. This design operationalises the ELT and idempotent-load principles discussed in Chapter 2, Section 2.2.3, where controlled load boundaries and deterministic reruns are identified as the basis for repeatable refresh cycles. Within each refresh boundary, existing rows for the affected window are deleted from the replica and then re-inserted from a fresh extract. This ensures that repeating the same boundary yields a consistent replicated state and supports recovery when extraction or load failures occur.

As illustrated in Figure 4.3, the refresh and report-serving sequence can be described in two stages. During the refresh stage, the ELT process first extracts source transactions from the POS environment for a defined boundary window, then removes previously replicated rows for the same boundary from the SQL Server replica, inserts the refreshed rows, and performs post-load checks such as row-count comparison and sampling-based verification. During the report-serving stage, the portal submits a report request with user-specified parameters, the API queries the refreshed replica and applies semantic rules, and the resulting rows, totals, and export-ready output are returned to the portal. This separation clarifies that replication and report serving are linked operationally but remain distinct responsibilities within the overall platform design.

![Figure 4.3: Proposed boundary-based refresh and report-serving sequence (illustrative)](#)

*Figure 4.3: Proposed boundary-based refresh and report-serving sequence (illustrative)*

#### Error Handling, Logging, and Monitoring

Operational controls are designed to support reliability and recovery. These controls include logging extraction and load outcomes (record counts, durations, and errors), post-load validation checks (e.g., row-count comparisons and sampling-based checks), and rerun capability for specific tables or boundaries without manual cleanup. This design is consistent with the discussion in Chapter 2, Sections 2.2.3 and 2.2.4, where idempotent load boundaries, operational controls, and recovery-oriented replication practices are identified as important for maintaining a trusted replicated state. Monitoring is intended to surface failed runs and to support repeatable recovery steps, which also aligns with the validation and recovery emphasis described in Chapter 3, Section 3.3.4.

#### API Endpoint Pattern and Semantic Layer Responsibilities

The API layer acts as a semantic layer that encapsulates reconstructed business rules and provides a stable interface to the reporting portal. Endpoints follow a consistent report pattern (illustrative), such as:

GET /reports/<report_name>
?start_date=YYYY-MM-DD
&end_date=YYYY-MM-DD
&location_keys=...(optional)
&... (other optional parameters)

For each endpoint, the design specifies required and optional parameters (including defaults aligned to the portal workflow), the output schema (fields, totals/subtotals, and formatting rules), and the validation approach (parity checks against vendor exports and cross-report reconciliation). This design directly reflects the semantic-layer and service-interface concepts discussed in Chapter 2, Section 2.2.5: replicated data are retained close to source structure for traceability, while report-specific business rules, derived fields, and delivery logic are centralised at the API layer. The API adopts a RESTful interface style to support standardised access and to decouple report consumption from underlying storage design, thereby keeping report logic more maintainable, versioned, and auditable.

#### Security Considerations

The platform is designed as a read-only reporting environment. The API should enforce authentication and authorisation appropriate to organisational policy. Access control is intended to ensure that only authorised users can retrieve reports and that query parameters are validated to prevent unintended exposure of data.

#### Report Logic Reconstruction Pattern and Representative Examples

Report reconstruction follows a repeatable workflow: define inputs (parameters and filters), identify contributing replicated datasets, implement vendor-aligned business rules at the semantic layer, aggregate and format outputs into a stable schema, and validate parity against vendor exports (Chapter 3, Sections 3.3.1 and 3.3.4). To keep the main chapter concise, only three representative examples are summarised below. Detailed report specification templates for the full set of fifteen targeted reports are consolidated in Appendix A (AppendixA-ReportSpecifications.md) and are completed iteratively as modules are implemented and validated.

Example 1: Daily Sales Summary (representative). This report aggregates sales totals for a selected outlet and business date range. Key reconstruction concerns include transaction inclusion criteria (e.g., completed vs voided), granularity (daily and outlet totals), and consistent handling of adjustments such as refunds.

Example 2: Payment Type (All Payment) (representative). This report provides a breakdown of payment collections by store and period, grouped by dimensions such as order source, payment method, device, card type, and reference. Key reconstruction concerns include split payments, mapping payment records to the correct sales identifiers and dates, and ensuring totals reconcile under defined rules.

Example 3: Sales Return Report (representative). This report retrieves return transactions (negative sales) for a selected date range and outlet scope. Key reconstruction concerns include return identification criteria, consistent computation of return amounts, traceability fields (e.g., sales number and original sales reference), and portal-equivalent filter behaviour.

### Database Design

The data design adopts a 1:1 replication strategy, where the company-owned database mirrors relevant transactional tables from the external POS environment. This strategy prioritises fidelity and traceability to support reconciliation and parity validation, which is consistent with the replication and consistency considerations discussed in Chapter 2, Sections 2.2.2-2.2.4. It is also aligned with the database-design and schema-on-read discussion in Chapter 2, Section 2.2.5, where duplicated transactional data are retained close to source structure for traceability, while report-specific calculations and derived logic are handled separately at the semantic/API layer.

As illustrated in Figure 4.4, the conceptual model centres on sales headers, sales items, payments, and supporting reference entities such as location and item master data. This model is intended to show the main reporting entities and relationships at a conceptual level rather than to expose vendor-specific physical table names.

![Figure 4.4: Simplified conceptual data model for sales and payment reporting (illustrative)](#)

*Figure 4.4: Simplified conceptual data model for sales and payment reporting (illustrative)*

Table 4.5 summarises the conceptual entities required by the targeted reports. Physical table names and column names in the replicated schema are vendor-specific; the design intent is to preserve a 1:1 representation while documenting join paths and key attributes used in report logic.

| Entity | Purpose in reporting | Representative attributes (conceptual) |
| --- | --- | --- |
| Sales (header) | Defines the reporting grain for sales totals and status handling | Sale identifier; business date; outlet/location key; sales status; totals |
| Sales item (line) | Supports item-level reporting and return/adjustment detection | Sale identifier; item code/name; quantity; net amount; tax fields |
| Payment | Supports payment type breakdown and reconciliation | Sale identifier; payment method; amount; device/reference fields |
| Location | Maps location identifiers to outlet names | Location key; location name; hierarchy attributes (if available) |
| Item master | Provides item metadata and grouping fields | Item code/name; category/group/division attributes |

*Table 4.5: Conceptual data dictionary (summary)*

### Business Rule Reconstruction for the Fifteen Targeted Reports

Although the replicated database preserves source-aligned transactional structures, the business rules for the fifteen targeted sales and payment reports are reconstructed and applied within the semantic/API layer rather than embedded in the storage layer. This separation is consistent with Chapter 2, Section 2.2.5, where duplicated data are retained for traceability while report-specific logic is centralised above the database layer for maintainability and auditability.

The semantic/API design supports the fifteen targeted reports through a common service pattern. Each report is exposed through a dedicated endpoint, but follows a shared response structure based on flat-list outputs, common parameter parsing behaviour, and consistent export handling. Shared parameter logic is reused where reports expose the same option sets, while report-specific extensions allow additional filters such as item division, group name, or department when required.

In this project, business-rule reconstruction refers to inferring vendor-equivalent reporting rules from observed portal outputs and implementing those rules as SQL queries executed by FastAPI over the 1:1 replicated data. The semantic/API layer therefore applies report-specific selection, grouping, aggregation, and formatting logic without changing the underlying replicated structure. Appendix A documents the detailed per-report specifications for the fifteen targeted reports, including rule inputs, parameters, expected outputs, and validation scope. Within the main design chapter, the emphasis is therefore on the shared reconstruction pattern and service-layer responsibilities rather than repeating each individual report specification in full.

### Interface Design

The portal is designed to mirror the existing user workflow for continuity reporting while providing consistent filtering and export behaviour. The primary interaction is: authenticate, select report, set parameters (outlet/date range and report-specific filters), view results with totals/subtotals, and export for reconciliation.

As illustrated in Figure 4.5, the report-list view is designed to support report discoverability and selection through a structured catalogue of available reports. This interface allows users to identify the required report quickly, recognise its reporting purpose from the accompanying description, and navigate into the relevant reporting screen without relying on vendor-managed menus. In this way, the report-list view contributes to the project objective of improving accessibility for Finance and Operations users within a company-controlled reporting environment.

![Figure 4.5: Report list view prototype (illustrative)](#)

*Figure 4.5: Report list view prototype (illustrative)*

As illustrated in Figure 4.6, the reporting view combines parameter controls, query execution, summary indicators, tabular output, and export actions within a single workflow. This design enables users to specify report parameters, retrieve vendor-aligned outputs, inspect key totals or subtotals, and export the result for reconciliation or further review. Rather than prioritising chart-heavy dashboards, the current interface emphasises summary cards and detailed tabular presentation because the project objective is continuity reporting and parity-aligned operational access rather than exploratory visual analytics.

In the current prototype, analytical presentation is therefore centred on summary indicators and tabular results, while chart-based views are treated as secondary because the targeted reports prioritise exact values, parameter-driven retrieval, and exportable outputs for reconciliation.

![Figure 4.6: Reporting view prototype (illustrative)](#)

*Figure 4.6: Reporting view prototype (illustrative)*

Figure 4.7 provides a simplified workflow view of the overall portal interaction, linking login, report discovery, report selection, parameter entry, result inspection, export, and downstream reconciliation. While Figures 4.5 and 4.6 show specific interface states, Figure 4.7 summarises the intended end-to-end navigation path so that the relationship between report selection and report consumption can be understood at a glance.

![Figure 4.7: Portal navigation and report workflow (illustrative)](#)

*Figure 4.7: Portal navigation and report workflow (illustrative)*

Interface design requirements prioritise consistent parameter controls across reports (with report-specific extensions), tabular presentation aligned to expected vendor export structures, and export outputs that support downstream reconciliation. These priorities are consistent with the workflow and interface considerations for operational reporting portals discussed in Chapter 2, Section 2.4. Portal design details are refined iteratively based on stakeholder feedback during validation cycles (see Chapter 3, Section 3.3.6).

### Summary

This chapter presented the system analysis, requirements, current system workflow, and the proposed design for the analytics platform. The design emphasises traceability, parity validation, and continuity reporting through replication-first data management, a semantic/API layer for report logic, and a portal interface that supports export-driven reconciliation. The next stage of work is to continue implementing and validating the remaining targeted reports and to introduce replication automation and operational monitoring as described in Chapter 3.
