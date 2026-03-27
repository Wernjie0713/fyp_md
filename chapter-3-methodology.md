# Methodology

## Introduction

This chapter describes the methodology used to develop the proposed Sales and Payment Analytics Platform. The project combines report logic reconstruction from a vendor-managed POS reporting portal, a 1:1 replication workflow and ELT process (currently executed using manual scripts, with automation planned), and report-level parity validation through iterative comparison and reconciliation. As the underlying report logic is not fully documented, the methodology prioritises incremental delivery with frequent validation cycles and retained evidence artefacts.

## Methodology Choice and Justification

The project adopts an iterative and incremental development approach aligned with Agile principles, where functionality is delivered in small increments and continuously validated against expected outputs (Beck et al., 2001; Schwaber & Sutherland, 2020). This choice is suitable for report reconstruction because requirements and edge cases emerge progressively during parity validation, and the cost of rework is reduced when changes are applied in smaller, validated iterations (Pressman & Maxim, 2014; Sommerville, 2015). The academic rationale for iterative delivery, ELT, replication-first traceability, and reconciliation-driven validation is synthesised in Chapter 2 (see Table 2.3).

## Phases within the Chosen Methodology

Work is organised as an iterative cycle that repeats for each targeted report module. The phases are designed to maintain traceability from requirements to validation evidence, while keeping a clear separation between stabilising report logic through parity validation and introducing operational automation after parity is established. Table 3.1 summarises typical inputs, activities, and evidence artefacts produced in each phase.

![Figure 3.1: Iterative Workflow for Analytics Platform Development](#)

*Figure 3.1: Iterative Workflow for Analytics Platform Development*

| Phase | Typical inputs | Key activities | Outputs / evidence artefacts (examples) |
| --- | --- | --- | --- |
| Phase 1: Requirement analysis | Vendor portal report views, exported files, parameter settings, stakeholder clarifications | Identify parameters and expected breakdowns; define output fields/totals; catalogue edge cases; draft data-to-report mapping; define acceptance criteria | Parameter matrix; output-field inventory; baseline export pack; acceptance checklist |
| Phase 2: System design | Phase 1 artefacts, replicated schema, constraints and non-functional requirements | Specify replication scope and join paths; define refresh boundary and late-correction handling; define API contract and export behaviour; define validation plan and test cases | Report specification template (Appendix A); API contract; data mapping; test plan; design diagram references |
| Phase 3: Implementation | Design artefacts, replicated datasets, acceptance criteria | Implement version-controlled report queries/rules; build API endpoint; implement parameter validation and formatting; add basic logging and error handling | Endpoint implementation; reproducible queries; sample outputs; execution logs |
| Phase 4: Testing and validation | Baseline exports, platform outputs, acceptance checklist | Compare outputs; investigate discrepancies; refine rules; run regression checks; record acceptance decisions and reconciliation results | Comparison evidence; discrepancy log; updated rule versions; validation sign-off |
| Phase 5: Deployment | Validated module, environment-ready checklist | Deploy to development environment; configure access controls; document release notes and rollback steps | Deployed endpoint/portal view; deployment checklist; release notes |
| Phase 6: Review and feedback | Deployed module, stakeholder feedback | Capture usability gaps and missing cases; triage defects vs enhancements; update acceptance criteria and test scenarios | Feedback log; change requests; revised acceptance criteria |

*Table 3.1: Phase-level inputs, activities, and evidence artefacts (per report module)*

### Phase 1: Requirement Analysis (Document Analysis and Stakeholder Feedback)

Requirements are elicited through document analysis of vendor portal reports and exported files, together with stakeholder feedback and clarification from Finance and Operations users regarding business intent, expected breakdowns, and acceptance criteria for continuity reporting. Because vendor logic is treated as a black box, the project applies a reverse engineering perspective to infer business rules from observable inputs and outputs (Chikofsky & Cross, 1990). Black-box testing practices support this phase by enforcing comparable parameters (e.g., outlet and date range) for subsequent parity checks (Myers et al., 2011). In practical terms, this phase produces a parameter matrix (inputs, defaults, and constraints), an output-field inventory (including totals/subtotals and formatting expectations), and a baseline export pack that serves as the reference set for subsequent comparisons. Edge cases that can materially affect parity (e.g., voids, returns, split tenders, and rounding behaviour) are recorded as test scenarios to support repeatable validation as rules evolve.

Key outputs of Phase 1 therefore include a report-specific parameter list, an output-field inventory, a draft data-to-report mapping (candidate tables and join keys in the replicated schema), and an acceptance checklist describing what constitutes an acceptable parity match for the report. These artefacts provide the basis for both implementation planning and validation evidence retention in later phases.

### Phase 2: System Design

System design translates Phase 1 requirements into design artefacts across the platform layers. This includes specifying replicated datasets and join paths required by the report, clarifying how business dates and time boundaries are interpreted, and defining refresh boundaries and late-correction handling to support repeatable reruns. At the semantic/API layer, the design specifies the report contract in a traceable manner: endpoint naming, required and optional parameters (including defaults aligned to the portal workflow), response schema (fields and data types), totals/subtotals, sorting/formatting rules, and export behaviour. The design also establishes a validation plan by mapping acceptance criteria and edge-case scenarios to concrete test cases and evidence artefacts (e.g., baseline exports and comparison outputs). Design modelling artefacts (e.g., architecture diagrams, data flow, and simplified data model/ERD) are presented in Chapter 4, while detailed per-report templates are consolidated and maintained in Appendix A.

### Phase 3: Implementation

Implementation follows a logic-first sequence: report logic is developed at the semantic/API layer and exercised using controlled parameters aligned to Phase 1 baseline exports. Where feasible, query prototypes are first validated against the replicated schema to confirm data availability, join correctness, and boundary handling, after which logic is stabilised into version-controlled queries and exposed through an API endpoint with a defined request/response contract. Implementation work also includes consistent parameter validation, deterministic output ordering where required for comparison, and export-ready formatting so that parity checks can be performed reliably against vendor exports. Basic logging and error handling are incorporated to support traceability of runs during iterative validation cycles.

Replication automation is treated as an operational enhancement after logic parity is established. In the current project stage, replication is executed using manual scripts; scheduling and automated rerun controls are planned for subsequent iterations.

### Phase 4: Testing & Validation (Parity and Reconciliation)

Testing and validation are performed at both module and system levels. At the module level, parity validation is conducted by generating platform outputs using identical parameters to vendor exports and comparing results at the appropriate granularity (row-level where applicable and aggregate-level where exports group outputs). Comparisons are performed using consistent filtering and boundary rules, and discrepancies are investigated and resolved through iterative refinement of filters, joins, date handling, and edge-case treatment. To reduce regression risk, previously validated scenarios (including recorded edge cases) are rechecked after rule changes so that fixes for one report do not introduce unintended drift in another.

At the system level, reconciliation checks are applied to confirm cross-report consistency (e.g., alignment between sales totals and payment totals for the same reporting windows under defined rules). These checks operationalise data quality perspectives such as accuracy, completeness, and consistency (International Organization for Standardization, 2008; Wang & Strong, 1996). Validation artefacts (baseline exports, comparison outputs, and acceptance decisions) are retained to support repeatability.

In addition to parity and reconciliation validation, a basic operational performance evaluation will be conducted to assess usability under typical usage conditions. Response-time observations will be recorded for representative report queries using selected outlet and date-range parameters, including scenarios aligned with reporting-intensive windows (e.g., month-end reconciliation). Multiple runs will be performed under comparable conditions and observed response times will be compared against practical expectations for routine Finance and Operations workflows. The intent of this evaluation is to confirm operational acceptability rather than to conduct exhaustive benchmarking or load testing.

### Phase 5: Deployment

Upon meeting validation criteria for a module, the corresponding API and portal changes are deployed to the target environment according to an environment-ready checklist. Deployment activities include configuration validation (e.g., database connectivity and access controls), version tagging and release documentation to support traceability of rule changes, and basic rollback considerations for changes that materially affect report outputs. As of Week 28, the warehouse, API service, and portal have been deployed to a cloud-hosted development environment to support iterative testing and stakeholder review. Subsequent deployment activities include introducing scheduled replication runs, configuring monitoring and rerun procedures, and publishing portal updates for intended user groups.

### Phase 6: Review & Feedback

Feedback is collected from Finance and Operations users to identify usability issues, missing data elements, and any residual discrepancies observed during real workflows. Feedback is documented as traceable change requests and triaged into parity defects that require rule correction and enhancements that adjust workflows or presentation without changing core financial meaning. Where feedback changes acceptance criteria or reveals new edge cases, the iteration returns to Phase 1 for the affected module so that requirements artefacts are updated and the revised logic is validated again with retained evidence.

*Figure 3.2: High-level system workflow (data replication to report delivery)*

## Project Schedule (Gantt Plan for FYPi1 and FYPi2)

For planning and tracking purposes, the overall project timeline is expressed as Weeks 1 to 28, where Weeks 1 to 14 correspond to SCSP 4233 (FYPi1) and Weeks 15 to 28 correspond to SCSP 4234 (FYPi2). Table 3.2 summarises the planned sequencing and the current status as of Week 28.

| Work package | Weeks (planned) | Key outputs | Status (as of Week 28) |
| --- | --- | --- | --- |
| Problem formulation and stakeholder alignment | 1–2 | Problem statement, scope draft, acceptance criteria outline | Completed |
| Literature review and synthesis | 1–6 | Chapter 2 draft with evidence-based justification | Completed (draft) |
| Methodology definition and design planning | 3–8 | Chapter 3 methodology; initial Chapter 4 design artefacts | Completed (draft) |
| Replication foundations (manual) | 5–12 | Replicated schema baseline; manual replication scripts | Implemented (manual; automation planned) |
| Report reconstruction iterations (15 reports) | 9–28 | Report APIs; parity validation artefacts | 7 of 15 implemented and validated |
| Portal development and integration | 13–28 | Report views; export workflow | 4 reports integrated |
| Cloud-hosted development deployment | 20–28 | Deployed development environment | Completed |
| Automation, monitoring, and rerun controls | 25–28 | Scheduler, logging, monitoring design | Planned for subsequent iterations |
| Performance evaluation (response-time) | 25–28 | Response-time evaluation plan and test windows | Planned for subsequent iterations |

*Table 3.2: Project schedule and status summary (Weeks 1–28)*

## System Requirement Analysis: Hardware and Software

The platform requirements are described at a practical level to support replication workloads, concurrent report queries, and operational monitoring in a cloud-hosted environment. Final sizing depends on replication scope, refresh cadence, and expected user concurrency and should be validated iteratively during performance evaluation.

### Hardware Requirements

| Resource | Requirement (high-level) | Justification |
| --- | --- | --- |
| Compute | Multi-core CPU capacity | Supports parallel replication/ELT tasks and concurrent API request handling. |
| Memory | Sufficient RAM for database and service workloads | Supports SQL Server caching and in-memory processing during report generation. |
| Storage | Low-latency storage (SSD-backed) with growth headroom | Supports replicated tables, indexes, logs, and export artefacts with predictable query performance. |
| Network | Stable connectivity between source, replica, and services | Required for extraction, loading, and portal access; impacts refresh time and report responsiveness. |
| Availability | Development environment availability aligned to stakeholder review | Supports iterative validation and reduces disruption during reporting windows. |

*Table 3.3: Hardware requirements (high-level)*

### Software Requirements

| Component | Role in the platform | Notes |
| --- | --- | --- |
| Microsoft SQL Server | Hosts the replicated transactional schema | Provides relational storage for replicated tables and report queries. |
| Python | Implements replication/ELT scripts and supporting utilities | Supports iterative development and operational scripting for extraction and loading. |
| SQLAlchemy + `pyodbc` | Database connectivity from Python | Provides a maintainable access layer to SQL Server via ODBC. |
| Microsoft ODBC Driver 17/18 | ODBC connectivity to SQL Server | Driver version depends on host environment configuration. |
| FastAPI | Semantic/API layer for report endpoints | Exposes reconstructed report logic as RESTful services (FastAPI, n.d.). |
| React + Node.js | Reporting portal frontend | Implements report parameter inputs, tabular display, and export workflow (React, n.d.). |
| Git | Version control for code and documentation | Supports traceability of changes to report logic and validation artefacts. |

*Table 3.4: Software requirements (high-level)*

## Summary

This chapter presented an iterative methodology for reconstructing vendor-aligned report logic, executing replication and ELT processes, and validating report-level parity through reconciliation-driven checks. Chapter 4 presents the analysis and design artefacts that operationalise this methodology for the proposed platform.
