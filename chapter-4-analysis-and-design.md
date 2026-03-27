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

The platform is designed under several constraints and assumptions. Access to the external POS environment is restricted and may be read-only. The current project phase targets sales and payment reporting for a defined set of high-priority reports, and the platform does not implement write-back to the vendor POS system. The replication cadence is designed to support operational reporting needs rather than real-time transactional processing. Design decisions in this chapter therefore prioritise traceability, repeatability, and operational controls for continuity reporting (see Chapter 2, Sections 2.2.3鈥?.2.7).

## Current System Analysis

The current reporting workflow relies on a vendor-managed reporting portal as the primary interface for sales and payment reports. Users typically select a report, apply parameters (e.g., outlet and date range), and export results for reconciliation activities. This workflow can constrain ad hoc analysis because users cannot freely query underlying transactional records, and operational reporting can be disrupted if portal access is degraded during reporting-intensive periods. Issue resolution is also dependent on vendor support processes, which can misalign with internal reporting timelines (see Chapter 2, Section 2.2.1).

![Figure 4.1: Current vendor-dependent reporting workflow (simplified)](#)

*Figure 4.1: Current vendor-dependent reporting workflow (simplified)*

## System Design

### System Architecture

The proposed system is organised into four logical layers: a source layer (external POS environment), a replication layer (ELT extraction and load), a semantic/API layer (reconstructed report logic exposed via RESTful endpoints), and a presentation layer (web portal for report access and export). This layered design supports traceability and governance by centralising report rules at the semantic layer and operating on replicated data under organisational control (see Chapter 2, Sections 2.2.4鈥?.2.5).

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

The replication scope focuses on transactional datasets required to reconstruct targeted sales and payment reports, including sales headers, sales line items, payment tenders, outlet/location reference, and item/product reference. Replication boundaries are defined to support operational reporting windows while allowing late corrections to be refreshed during subsequent runs.

#### Refresh Cadence and Idempotent Load Pattern

The ELT workflow is designed to refresh operational data on a scheduled basis and to account for late corrections (e.g., late voids, adjustments, and return postings). To support safe reruns, the proposed approach applies an idempotent pattern per refresh boundary: existing records within the boundary are deleted from the replica and then re-inserted from a fresh extract. This ensures that repeating a boundary yields a consistent replicated state and supports recovery when extraction or load failures occur (see Chapter 2, Section 2.2.3).

![Figure 4.3: Proposed boundary-based refresh and report-serving sequence (illustrative)](#)

*Figure 4.3: Proposed boundary-based refresh and report-serving sequence (illustrative)*

#### Error Handling, Logging, and Monitoring

Operational controls are designed to support reliability and recovery. These controls include logging extraction and load outcomes (record counts, durations, and errors), post-load validation checks (e.g., row-count comparisons and sampling-based checks), and rerun capability for specific tables or boundaries without manual cleanup. Monitoring is intended to surface failed runs and to support repeatable recovery steps (see Chapter 3, Section 3.3.4).

#### API Endpoint Pattern and Semantic Layer Responsibilities

The API layer acts as a semantic layer that encapsulates reconstructed business rules and provides a stable interface to the reporting portal. Endpoints follow a consistent report pattern (illustrative), such as:

GET /reports/<report_name>
?start_date=YYYY-MM-DD
&end_date=YYYY-MM-DD
&location_keys=...(optional)
&... (other optional parameters)

For each endpoint, the design specifies required and optional parameters (including defaults aligned to the portal workflow), the output schema (fields, totals/subtotals, and formatting rules), and the validation approach (parity checks against vendor exports and cross-report reconciliation). The API adopts a RESTful interface style to support standardised access and decouple report consumption from storage design (see Chapter 2, Section 2.2.5).

#### Security Considerations

The platform is designed as a read-only reporting environment. The API should enforce authentication and authorisation appropriate to organisational policy. Access control is intended to ensure that only authorised users can retrieve reports and that query parameters are validated to prevent unintended exposure of data.

#### Report Logic Reconstruction Pattern and Representative Examples

Report reconstruction follows a repeatable workflow: define inputs (parameters and filters), identify contributing replicated datasets, implement vendor-aligned business rules at the semantic layer, aggregate and format outputs into a stable schema, and validate parity against vendor exports (Chapter 3, Sections 3.3.1 and 3.3.4). To keep the main chapter concise, only three representative examples are summarised below. Detailed report specification templates for the full set of fifteen targeted reports are consolidated in Appendix A (AppendixA-ReportSpecifications.md) and are completed iteratively as modules are implemented and validated.

Example 1: Daily Sales Summary (representative). This report aggregates sales totals for a selected outlet and business date range. Key reconstruction concerns include transaction inclusion criteria (e.g., completed vs voided), granularity (daily and outlet totals), and consistent handling of adjustments such as refunds.

Example 2: Payment Type (All Payment) (representative). This report provides a breakdown of payment collections by store and period, grouped by dimensions such as order source, payment method, device, card type, and reference. Key reconstruction concerns include split payments, mapping payment records to the correct sales identifiers and dates, and ensuring totals reconcile under defined rules.

Example 3: Sales Return Report (representative). This report retrieves return transactions (negative sales) for a selected date range and outlet scope. Key reconstruction concerns include return identification criteria, consistent computation of return amounts, traceability fields (e.g., sales number and original sales reference), and portal-equivalent filter behaviour.

### Database Design

The data design adopts a 1:1 replication strategy, where the company-owned database mirrors relevant transactional tables from the external POS environment. This strategy prioritises fidelity and traceability to support reconciliation and parity validation (see Chapter 2, Sections 2.2.2鈥?.2.4).

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

### Interface Design

The portal is designed to mirror the existing user workflow for continuity reporting while providing consistent filtering and export behaviour. The primary interaction is: authenticate, select report, set parameters (outlet/date range and report-specific filters), view results with totals/subtotals, and export for reconciliation.

![Figure 4.5: Portal navigation and report workflow (illustrative)](#)

*Figure 4.5: Portal navigation and report workflow (illustrative)*

Interface design requirements prioritise consistent parameter controls across reports (with report-specific extensions), tabular presentation aligned to expected vendor export structures, and export outputs that support downstream reconciliation. These priorities are consistent with the workflow and interface considerations for operational reporting portals discussed in Chapter 2, Section 2.4. Portal design details are refined iteratively based on stakeholder feedback during validation cycles (see Chapter 3, Section 3.3.6).

### Summary

This chapter presented the system analysis, requirements, current system workflow, and the proposed design for the analytics platform. The design emphasises traceability, parity validation, and continuity reporting through replication-first data management, a semantic/API layer for report logic, and a portal interface that supports export-driven reconciliation. The next stage of work is to continue implementing and validating the remaining targeted reports and to introduce replication automation and operational monitoring as described in Chapter 3.
