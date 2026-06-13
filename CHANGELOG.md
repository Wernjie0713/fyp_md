# CHANGELOG

This changelog records major final-report drafting changes made inside `fypi_md_split`.

## 2026-06-13

### chapter-5-implementation-and-testing.md

- Revised the Chapter 5 implementation-figure arrangement so the implementation evidence now uses `Figure 5.1` to `Figure 5.7`, while the testing evidence continues from `Figure 5.8` onward.
- Renamed the implementation figures to use formal descriptive captions and removed the earlier `workflow evidence` phrasing from the implementation-figure treatment.
- Rewrote the figure-reference paragraphs for `Figure 5.1` to `Figure 5.6` so they read as continuous subsection content rather than as detached image-description sentences.
- Refined the `Figure 5.7` explanation so it functions as part of the `Report Reconstruction Process` discussion instead of sounding like an isolated AI-style description of the image itself.
- Updated the administrative and replication-process wording so the figure references support the academic argument of each subsection more directly.
- Swapped the `Figure 5.5` and `Figure 5.6` ordering so the chapter now matches the revised intended sequence: reference-table refresh first, followed by dated sales-data replication and data-quality review.

### table-of-contents.md, list-of-figures.md, list-of-tables.md

- Rebuilt the table of contents so it matches the current report structure, including the latest Chapter 5 subsection headings and the current Appendix A layout.
- Rebuilt the list of figures so it reflects the current figure captions and numbering used across the report, including `Figure 4.9`, the Chapter 5 implementation figures `Figure 5.1` to `Figure 5.7`, and the testing figures through `Figure 5.40`.
- Rebuilt the list of tables so it remains aligned with the current table captions used across Chapters 1 to 5 and Appendix A.
- Removed page numbers from the markdown front-matter index files so they no longer preserve stale values before the final document pagination is refreshed in Word.

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

### chapter-4-analysis-and-design.md

- Rewrote Chapter 4 from proposal-stage design framing into final-report design framing.
- Changed the chapter to use `Marrybrown Sales and Payment Analytics Platform` as the implemented system name and removed outdated `proposed platform` wording.
- Revised the stakeholder, requirement, and constraint sections so they reflect the implemented reporting platform rather than an earlier planning-stage scope.
- Added a report-coverage overview that summarises the formal implementation/business-scope reports by functional group and separately identifies the additional customised reports, while keeping detailed specifications in Appendix A.
- Removed forbidden old-scope references such as the proposal-stage `15 reports`, `Daily Sales Summary`, and the internal appendix filename reference.
- Reworked the replication and refresh design sections to reflect controlled refresh processes, scheduled ETL support, portal-triggered operations, and data-quality checking at design level without turning the chapter into an implementation diary.
- Replaced the earlier representative-example treatment with a shorter report-reconstruction overview so Chapter 4 remains at design level and leaves detailed implementation examples to Chapter 5.
- Updated the interface design section so it briefly acknowledges role-restricted administrative views such as user administration and refresh-related operational oversight without over-expanding the admin implementation details.
- Updated the interface and summary sections so the chapter now transitions correctly into Chapter 5 `Implementation & Testing` instead of describing future implementation work.
- Added a separate `Service and operational timing` report group for `Average SOS Report (New)` so the Chapter 4 report-classification table matches the implemented API behaviour more accurately.

### chapter-5-implementation-and-testing.md

- Created a new Chapter 5 markdown file from scratch using the university development-project structure: `5.1 Introduction`, `5.2 System Development`, `5.3 Coding of the system's main functions/Process`, and `5.4 Summary`.
- Wrote the chapter in final-report academic style and positioned it as the main implementation and testing chapter rather than a design-overview chapter.
- Documented the implemented system across the SQL Server reporting database and ETL layer, the FastAPI semantic/API layer, the React portal layer, and the supporting admin and operational functions.
- Recorded the formal report implementation coverage, including the retained formal-scope reports, the not-fully-closed report areas, and the additional customised reports.
- Included two selected implementation examples: `Payment Type (All Payment)` as the formal-scope example and `Voucher Campaign & Reward Sales Report` as the customised-report example.
- Added a `5.3.5 Query Performance Observation` subsection to document performance tuning as an implementation outcome rather than as a vendor-benchmark claim.
- Added compact timing comparison tables under the performance subsection, using `Payment Type (All Payment)` as the strongest main example and selected supporting observations from other report families.
- Added separate testing subsections for report accuracy validation, combined black-box testing and User Acceptance Testing, and white-box testing.
- Inserted placeholder figure references for the planned Chapter 5 testing workbook so the later Excel artifact and the markdown chapter can be kept aligned.
- Updated the testing evidence plan to use detailed one-sheet-per-test-case workbook evidence, with `PV` IDs for report accuracy validation, `TC` IDs for UAT/black-box test cases, and `WB` IDs for white-box test cases.
- Replaced the earlier three broad testing placeholders with detailed figure placeholders from `Figure 5.1` to `Figure 5.33`, matching the detailed testing workbook structure.
- Added under-table captions for the Chapter 5 timing tables and updated the chapter summary so it now mentions recorded performance-tuning observations explicitly.

### chapter-5-testing-evidence-detailed.xlsx

- Created a detailed Chapter 5 testing evidence workbook for the Chapter 5 implementation and testing section.
- Added a `Testing_Summary` sheet that maps every evidence case to its testing category, status, retest requirement, and figure number.
- Added `PV01` to `PV08` report accuracy validation sheets using a comparison-oriented reconciliation layout suited to parity validation against vendor portal or approved business reference outputs.
- Added `TC01` to `TC16` UAT/black-box test-case sheets using the university-style user test-case layout and the user's preferred `TC` numbering convention.
- Added `WB01` to `WB09` white-box test-case sheets using an internal-checkpoint layout focused on logic paths, controlled conditions, and boundary-case review.
- Kept the workbook public-safe by using role-based tester labels, general filter descriptions, and no credentials, private server details, or operational secrets.

### final-report-memory-note.md

- Updated the main memory note to include Chapter 5 performance-writing rules.
- Recorded that performance discussion should be framed as implementation evidence of tuning and operational usability improvement, not as a formal vendor-versus-platform benchmark unless controlled side-by-side timing evidence exists.
- Recorded that compact tables are appropriate for the Chapter 5 performance subsection and that `Payment Type (All Payment)` is the strongest supported example.

### chapter-6-conclusion.md

- Created a new Chapter 6 markdown file from scratch using the agreed final-report conclusion structure: `6.1 Introduction`, `6.2 System Contribution/Achievement`, `6.3 System Constraint`, `6.4 Future Suggestion`, and `6.5 Summary`.
- Wrote the chapter as an interpretive conclusion chapter rather than as an implementation repeat of Chapter 5.
- Framed the system contribution around delivery of a real company-usable internal reporting platform, report reconstruction with validation discipline, operational usability, and architectural extensibility.
- Documented the main constraints in academic limitation language, including replicated-data dependence, black-box vendor logic, unresolved profit-related report areas, performance variation across report families, and the fact that the platform should not be treated as a full replacement for every vendor capability.
- Added future suggestions that follow naturally from the delivered system, including further parity work on unresolved logic, stronger historical data reliability, selective performance refinement, controlled report expansion, and continued administrative monitoring improvement.

### appendix-a-report-specifications.md

- Replaced the old proposal-era appendix structure with a final-report appendix structure aligned to the agreed final scope.
- Removed outdated proposal wording such as `15 targeted reports`, `Week 28`, `[TBD]`, and iterative-planning language.
- Rebuilt the appendix around the formal 19-report implementation and business scope, clearly distinguishing the 16 implemented-and-validated reports from the 3 reports that were not fully closed.
- Added a separate section for the 3 additional customised reports implemented beyond the formal 19-report scope.
- Rewrote all per-report specification tables in final-report academic style so they describe business purpose, users, parameters, outputs, data scope, key business rules, validation approach, and final status without internal handover language.
- Kept the appendix public-safe by avoiding confidential file references, internal validation artefact names, runbook instructions, and proposal-stage planning notes.
- Corrected the `Average SOS Report (New)` description during the API-alignment pass so it reflects the implemented store-level service-duration logic rather than an inventory interpretation.
- Updated the report-group classification for `Average SOS Report (New)` to `Service and operational timing` so the appendix index and Chapter 4 grouping stay consistent with the active API implementation.

### table-of-contents.md, list-of-figures.md, list-of-tables.md

- Rebuilt the table of contents so it matches the final chapter headings, subsection names, Chapter 5 and Chapter 6 structure, and the revised Appendix A layout.
- Rebuilt the list of figures so it now reflects the final figure captions used in Chapters 1, 3, 4, and 5 instead of old proposal-stage figure names.
- Rebuilt the list of tables so it now reflects the final table captions used across Chapters 1 to 5 and Appendix A instead of the old proposal-stage table list.
- Removed outdated proposal-era entries such as `proposed platform`, `redundancy architecture`, `Week 28`, `15 reports`, and the earlier Appendix A template/index structure from the front-matter support files.
- Verified that the final front-matter lists now align with the current report body, including the detailed Chapter 5 testing figures and the final 19-report Appendix A specification set.
