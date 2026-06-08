# CHANGELOG

This changelog records major final-report drafting changes made inside `fypi_md_split`.

## 2026-06-03

### abstract.md

- Rewrote the abstract from proposal-stage wording into final-report wording.
- Changed the main system framing to `Marrybrown Sales and Payment Analytics Platform`, following the updated supervisor-aligned naming direction.
- Kept `redundancy` as a supporting architecture concept rather than presenting the project as a simple duplicate of the vendor portal.
- Removed the old proposal-specific report count and described the report scope more generally as selected sales and payment reports.
- Added final implementation content covering the SQL Server reporting environment, FastAPI semantic/API layer, React reporting portal, portal-triggered replication, data-quality checking, and ETL automation management.
- Added a concise public-safe limitation statement for report areas that were not fully closed because the remaining profit-related logic could not be isolated through completed validation work.

### abstrak.md

- Rewrote the Malay abstract to align with the updated English abstract.
- Converted the content from proposal-stage wording into final-report wording.
- Used formal Bahasa Melayu Malaysia and avoided Indonesian-style phrasing.
- Preserved the system name `Marrybrown Sales and Payment Analytics Platform` for consistency with the English version.
- Reflected the same architecture, implementation, validation, and limitation points as the English abstract.
- Removed the old proposal-specific report count and replaced it with general wording about selected sales and payment reports.
- Polished several Malay phrases to improve academic formality while preserving the same meaning as the English abstract.

### chapter-1-introduction.md

- Rewrote Chapter 1 from proposal-stage wording into final-report wording while preserving the existing academic structure.
- Changed the main system framing to `Marrybrown Sales and Payment Analytics Platform` and reduced `redundancy` to a supporting continuity concept instead of the main identity of the project.
- Revised the problem framing to emphasise vendor dependency, limited internal control over report logic, and the need for a company-controlled reporting platform.
- Updated the project aim and objectives to remove exact report-count commitments and keep the chapter at a general introductory level.
- Rebuilt the project scope section to describe the final platform boundary, included components, and exclusions instead of internship progress tracking.
- Replaced the old Week 28 progress table with a final-report scope-boundary table.
- Updated the figure wording from a proposed architecture comparison to a comparison between the original vendor-dependent arrangement and the implemented internal platform.
- Updated the report organisation section to include Chapter 5 `Implementation & Testing` and Chapter 6 `Conclusion`.

### chapter-2-literature-review.md

- Revised Chapter 2 from proposal-oriented wording to final-report wording while preserving the literature review structure.
- Changed the main framing from a `proposed` redundancy system to the implemented `Marrybrown Sales and Payment Analytics Platform` as a company-owned reporting platform.
- Reduced the use of `redundancy` as the main system identity and kept continuity language as supporting architectural context.
- Updated the comparative discussion and table wording so they refer to the architecture adopted in the project rather than a proposed platform.
- Retitled `Related Previous Researches/Systems and Comparative Discussion` to `Related Studies/Systems and Comparative Discussion` for more natural academic phrasing.
- Retitled `Technology Used` to `Technology Selection Considerations` and rewrote the section so it supports the literature-grounded architecture without becoming an implementation chapter.
- Fixed the duplicated ending heading by keeping `Synthesis and Rationale Map` for Table 2.3 and renaming the final section to `Summary`.

### chapter-3-methodology.md

- Rewrote Chapter 3 from proposal-stage methodology wording into final-report methodology wording.
- Changed the main framing to the implemented `Marrybrown Sales and Payment Analytics Platform` and removed outdated proposal-era references to a `proposed` platform.
- Updated the iterative phase descriptions so they describe the executed development and validation approach rather than planned future work.
- Replaced outdated manual-only and future-automation wording with final-report descriptions of controlled sync, scheduled ETL, administrative automation control, and data-quality checking support.
- Revised the testing and validation section to reflect parity validation, reconciliation, source-to-replica quality checks, black-box comparison, white-box review, and operational acceptability checks in final-report tense.
- Rebuilt the project schedule section into a detailed 40-week Gantt-style schedule aligned to the iterative and incremental methodology, replacing the old Week 28 tracking and forbidden `15 reports` planning references.
- Renamed `System Requirement Analysis: Hardware and Software` to `Implementation Environment Requirements` and rewrote the section to describe the actual project environment more appropriately for a final report.
