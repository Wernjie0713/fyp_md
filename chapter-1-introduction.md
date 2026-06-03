# Introduction

## Introduction

In contemporary retail operations, timely access to trusted transaction data is essential for operational oversight, financial control, and informed decision-making. In practice, many organisations consolidate operational data into analytical repositories such as data warehouses to support reporting, governance, and performance monitoring (Inmon, 2005; Kimball & Ross, 2013). Large-scale food and beverage (F&B) enterprises such as Marrybrown generate high volumes of sales and payment transactions across multiple outlets, which increases the importance of reliable report access, traceable report logic, and consistent data availability.

In the original operating arrangement, the organisation relied on a third-party cloud point-of-sale (POS) vendor for both transaction processing and analytical reporting. Sales and payment information was primarily accessed through vendor-managed portal views and exported files used by Finance and Operations stakeholders for routine review, reconciliation activities, and month-end closing. While this arrangement may reduce initial implementation effort, cloud computing guidance highlights that reliance on external service providers introduces availability, control, and security considerations that require active management (Badger et al., 2012; Jansen & Grance, 2011).

Accordingly, the organisational context of this project was defined by high transaction volume, dependence on vendor-managed reporting access, and the need for timely, trusted outputs for operational and financial workflows. This context established the need for a company-controlled reporting platform capable of reproducing required reports from replicated transactional data while improving continuity, traceability, and internal control.

## Problem Background

The organisation's previous reporting arrangement depended heavily on a third-party POS service provider for report access and delivery. This created a practical single point of reporting dependency: when the vendor portal experienced downtime, degraded performance, or delayed report generation, Finance and Operations users could face disruption in obtaining required sales and payment information.

A further constraint was limited internal control over both the underlying datasets and the report logic applied to them. Access was mediated mainly through vendor interfaces and exported outputs, which restricted ad hoc investigation, limited transparency into report derivation, and reduced the organisation's ability to maintain or extend required reporting behaviour internally.

Internal reporting activities placed particular pressure on this arrangement during reconciliation and month-end closing periods, when timely access to trusted outputs was especially important. Delays or unavailability during these windows could interrupt verification workflows, slow issue resolution, and affect downstream financial preparation.

As illustrated in Figure 1.1, the original reporting arrangement provided a direct but vendor-dependent path from the external POS and reporting portal to Finance and Operations users. In contrast, the implemented Marrybrown Sales and Payment Analytics Platform introduced an internal reporting path through controlled data replication, a company-managed SQL Server reporting environment, a semantic/API layer, and a web-based reporting portal. This comparison highlights the shift from vendor-dependent report access to a company-controlled reporting architecture.

![Figure 1.1: Comparison of Original Vendor-Dependent Reporting Arrangement and Implemented Internal Reporting Platform](#)

_Figure 1.1: Comparison of Original Vendor-Dependent Reporting Arrangement and Implemented Internal Reporting Platform_

## Problem Statement

Based on the organisational context described above, this project addressed four interrelated problems. First, reliance on a third-party reporting portal limited organisational control over access to critical sales and payment reports. Second, restricted direct visibility into transactional data and report logic constrained ad hoc analysis, internal validation, and rapid issue investigation. Third, changes or extensions to required reports could not be maintained wholly within the organisation because report behaviour remained dependent on vendor-managed services. Finally, reporting disruption or delay during operationally sensitive periods, particularly reconciliation and month-end closing, could affect the timeliness and reliability of financial workflows.

## Project Aim

The aim of this project was to develop the Marrybrown Sales and Payment Analytics Platform to provide company-controlled access to selected sales and payment reports through replicated transactional data, reconstructed report logic, and an internal web portal.

## Project Objectives

To achieve the stated aim, the following specific objectives have been defined:

- To analyse stakeholder requirements for selected sales and payment reports, including continuity needs and report-level validation expectations.

- To design and implement a company-managed reporting environment in Microsoft SQL Server using 1:1 replication of required transactional data.

- To reconstruct and validate vendor-aligned report logic within a semantic/API layer so that selected reports can be reproduced with traceable business rules.

- To deliver a web-based reporting portal that supports report search, viewing, export, and administrative control for authorised internal users.

## Project Scope

This project covers the end-to-end development of the Marrybrown Sales and Payment Analytics Platform, including data replication, report logic reconstruction, backend service development, portal delivery, and deployment support. The implementation scope focuses on sales and payment data required to reproduce selected operational and financial reports for internal use.

The platform uses a company-managed Microsoft SQL Server reporting environment to store replicated transactional data, a FastAPI backend to reconstruct and deliver report logic, and a React-based portal to provide user access to validated reports. The implementation also includes controlled sync and ETL support, administrative functions for report operations, and validation activities to compare reconstructed outputs against the vendor portal under matched reporting conditions.

Where operational reporting needs evolved during implementation, the same platform architecture also supported additional company-requested reporting modules within the same sales and payment reporting domain.

The platform is intentionally limited to read-only reporting and does not perform write-back operations to the vendor POS environment. Broader enterprise analytics domains beyond the required sales and payment reporting surface, such as customer relationship management (CRM) and non-essential business intelligence extensions, are outside the project boundary. Detailed report specifications are presented in Appendix A.

| Scope Area | Coverage |
| ---------- | -------- |
| Data layer | Replication of selected sales and payment transaction data into a company-managed Microsoft SQL Server reporting environment |
| Report layer | Reconstruction and validation of selected vendor-aligned sales and payment reports through a FastAPI semantic/API layer |
| User layer | Internal web portal for report search, viewing, export, and administrative control |
| Boundary | Read-only reporting only; no write-back to the vendor POS system; broader analytics domains excluded from the current project |

_Table 1.1: High-level project scope boundary_

## Project Importance

This project is significant because it addressed an operational dependency in which access to critical sales and payment reports was mediated largely by vendor-managed services. By implementing a company-controlled reporting platform with replicated data and reconstructed report logic, the organisation gained greater continuity, transparency, and control over required reporting outputs. From an information quality perspective, the project emphasised reconciliation and parity validation to support the fitness-for-use of reproduced outputs for operational and financial reporting (Wang & Strong, 1996).

In addition, this work provides a structured case study on rebuilding vendor-dependent reports through replicated transactional data, a semantic/API delivery layer, and validation-driven implementation rather than treating reporting continuity as a simple interface duplication exercise. The resulting architecture also establishes a maintainable foundation for future internal reporting enhancement once the core sales and payment reporting requirements are stabilised.

The contribution of this project lies not only in delivering an internal reporting platform, but also in demonstrating a practical, validation-driven approach for reconstructing vendor-dependent operational reports using replicated transactional datasets in a real organisational environment.

## Report Organization

Chapter 1 introduces the project context, problem statement, aim, objectives, scope, importance, and the organisation of the report. Chapter 2 reviews relevant literature on vendor dependency risks, replication and ETL approaches, schema-on-read and semantic layers, data quality and reconciliation, and iterative development approaches. Chapter 3 presents the methodology used to execute the project, including the validation approach and project workflow. Chapter 4 documents the analysis and design of the implemented system, including requirements, architecture, report coverage overview, and design artefacts. Chapter 5 presents the implementation and testing of the system, including system development, main functions and processes, selected implementation examples, and validation activities. Chapter 6 concludes the report by summarising the system contribution, constraints, future suggestions, and overall project outcome.
