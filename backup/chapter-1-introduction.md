# Introduction

## Introduction

In contemporary retail operations, timely access to trusted transaction data is essential for operational oversight and informed decision-making. In practice, many organisations consolidate operational data into analytical repositories (e.g., data warehouses) to support reporting, governance, and performance monitoring (Inmon, 2005; Kimball & Ross, 2013). Large-scale food and beverage (F&B) enterprises such as Marrybrown generate high volumes of sales and payment transactions across multiple outlets, which increases the importance of reliable reporting and data accessibility.

In the current setting, the organisation relies on a third-party cloud point-of-sale (POS) vendor for both transaction processing and analytical reporting. Sales and payment information is primarily accessed through vendor-managed portal views and exported files, which are used by Finance and Operations stakeholders for daily review, reconciliation activities, and month-end closing. While this arrangement can reduce initial implementation effort, cloud computing guidance highlights that reliance on external service providers can introduce availability, control, and security considerations that must be actively managed (Badger et al., 2012; Jansen & Grance, 2011).

Accordingly, the existing sales and payment reporting environment is characterised by high transaction volume, dependence on vendor-managed access channels, and the need for timely, trusted outputs for operational and financial workflows. This context establishes the basis for examining the practical limitations of the current reporting arrangement, which are discussed in the following sections.

## Problem Background

The organisation currently relies on a third-party POS service provider for operational data storage and reporting. This creates a single point of failure for critical Finance and Operations reporting activities: when the vendor's cloud services experience downtime or latency, internal stakeholders may be unable to access required transaction data and reports.

A practical constraint is limited internal visibility and control over the sales and payment datasets. Access is typically mediated through the vendor interface, which restricts flexible querying and reduces the organisation's ability to perform ad hoc investigations or rapid enhancements. When disruptions occur, incident resolution is dependent on vendor support processes, which may not align with internal operational timelines.

Internal observations further indicate that report generation may fail or become unavailable during month-end closing periods, when reporting load is typically higher. Even short periods of reporting unavailability during such critical windows can disrupt verification workflows and delay financial reconciliation activities, potentially affecting downstream audit preparation.

As illustrated in Figure 1.1, the current reporting arrangement provides a direct but vendor-dependent path from the external POS and reporting portal to Finance and Operations users, whereas the proposed redundancy architecture introduces an alternative reporting path through replication and ELT, a company-owned SQL Server replica, a semantic layer, and an internal reporting portal. This comparison highlights how the existing arrangement concentrates reporting access within vendor-managed services, while the proposed design shifts reporting delivery into components under organisational control.

![Figure 1.1: Comparison of Current Vendor Dependency vs. Proposed Redundancy Architecture](#)

_Figure 1.1: Comparison of Current Vendor Dependency vs. Proposed Redundancy Architecture_

## Problem Statement

Based on the organisational context described above, this project addresses four interrelated problems. First, reliance on a single third-party reporting portal creates a single point of failure for sales and payment reporting activities. Second, limited direct visibility into transactional datasets restricts ad hoc analysis and slows internal investigations. Third, vendor-dependent incident resolution may not meet operational timelines, particularly during critical reporting windows. Finally, report unavailability during month-end closing periods can disrupt reconciliation work and delay downstream audit preparation.

## Project Aim

The aim of this project is to develop a resilient, company-owned Sales and Payment Analytics Platform that serves as a functional redundancy system for the external POS portal, enabling continued access to critical operational reports through a 1:1 database replication architecture.

## Project Objectives

To achieve the stated aim, the following specific objectives have been defined:

- To define stakeholder requirements for continuity sales and payment reporting, including report-level acceptance criteria for parity validation.

- To design a company-owned 1:1 replicated transactional schema in Microsoft SQL Server that ensures data fidelity and traceability for the targeted reporting outputs.

- To reconstruct the business rules for fifteen targeted sales and payment reports within a semantic/API layer, ensuring report-level parity with vendor exports.

- To develop an interactive web-based reporting portal with operational usability, performance monitoring, baseline security controls, and recovery procedures.

## Project Scope

This project covers the end-to-end development of a custom analytics platform, spanning data extraction, replication, report logic reconstruction, and user-facing reporting. The replication scope focuses on sales and payment datasets required to support the targeted reporting outputs.

The core development focus is the logic reconstruction of 15 critical sales and payment reports. The backend service is being developed using a Python-based API layer (FastAPI) to apply schema-on-read transformations and implement report logic in a controlled and auditable manner. The project applies reverse engineering and report-level parity validation to align reconstructed outputs with the vendor portal.

Although fifteen reports are defined as targeted outputs, implementation is scheduled incrementally: initial iterations prioritise a subset of high-impact operational reports for early reconstruction and parity validation, while the remaining reports are completed in subsequent iterations as described in Chapter 3.

System development includes a sales and payment analytics portal being developed using React to support Finance and Operations users in viewing and exporting required reports. The platform is designed as a read-only redundancy system and does not support write-back operations to the vendor POS system. Inventory and customer relationship management (CRM) analytics are excluded from the current scope and are reserved for future work.

| Workstream                           | Status (Week 28)                   | Notes                                                                                            |
| ------------------------------------ | ---------------------------------- | ------------------------------------------------------------------------------------------------ |
| Data warehouse and cloud environment | Deployed (development environment) | Deployed for iterative development and stakeholder review; production hardening remains ongoing. |
| Report APIs                          | 7 of 15 implemented and validated  | Validation performed against vendor exports using parity and reconciliation checks.              |
| Portal frontend                      | 4 reports implemented              | Remaining report views will be implemented as additional APIs are completed.                     |
| Replication and ELT automation       | Manual scripts available           | Scheduling and automation are planned for later iterations.                                      |

_Table 1.1: Current progress summary (as of Week 28 of the internship)_

## Project Importance

This project is significant because it addresses an operational vulnerability arising from dependence on a third-party reporting portal for critical sales and payment information. By establishing a company-owned replica and reporting layer, the organisation is expected to improve continuity of access to reports and reduce exposure to vendor-side service disruptions. From an information quality perspective, the project emphasises reconciliation and report-level parity checks to support the fitness-for-use of reproduced outputs for financial reporting (Wang & Strong, 1996).

In addition, this work provides a structured case study on designing a redundancy reporting platform using replication, ELT practices, and iterative validation. The resulting architecture can serve as a foundation for future analytical enhancements once the core sales and payment reporting requirements are stabilised.

The contribution of this project lies not only in delivering a continuity reporting platform, but also in demonstrating a practical, validation-driven approach for reconstructing vendor-dependent operational reports using replicated transactional datasets.

## Report Organization

Chapter 1 introduces the project context, problem statement, aim, objectives, scope, importance, and the organisation of the report. Chapter 2 reviews relevant literature on vendor dependency risks, replication and ELT approaches, schema-on-read and semantic layers, data quality and reconciliation, and iterative development approaches. Chapter 3 presents the methodology for executing the project, including the parity validation strategy and the project schedule. Chapter 4 documents the analysis and design of the proposed system, including system analysis, requirements, current system analysis, and detailed design artefacts.
