# Final Report Memory Note

Date: 2026-05-14

Updated: 2026-06-03

Purpose: record the agreed writing-style rules, terminology decisions, and report-scope arrangement decisions for the Marrybrown final report so later AI handoff, audit, or revision work stays aligned. All future changes should directly produce final-version academic FYP report content, not internal project handover content.

## 1. Source Basis Reviewed

The following materials were reviewed before making the decisions in this note:

- `fypi_md_split/proposal-writing-style-guide.md`
- `fypi_md_split/abstract.md`
- `fypi_md_split/chapter-1-introduction.md`
- `fypi_md_split/chapter-3-methodology.md`
- `fypi_md_split/chapter-4-analysis-and-design.md`
- `fypi_md_split/appendix-a-report-specifications.md`
- `fypi_md_split/FYPi Proposal - YONG WERN JIE A22EC0121.docx`
- `README.md`
- `FINAL_HANDOVER.md`
- `SYSTEM_OVERVIEW_FOR_HANDOVER.md`
- `marrybrown_api/DOCUMENTATION_INDEX.md`
- `marrybrown_api/docs/PROJECT_CONTEXT.md`
- `marrybrown_etl/docs/REPLICA_HANDOVER.md`
- `19_reports_queries_from_vendor.txt`
- `marrybrown_api/docs/PRODUCT_MIX_WITH_MODIFIER_WITHOUT_ETL_REPORT_API.md`
- `marrybrown_api/docs/PRODUCT_MIX_WITH_MODIFIER_WITHOUT_ETL_REPORT_JOURNEY.md`
- `marrybrown_api/docs/ROBLOX_FREE_CHICKEN_BURGER_COMBO_SALES_REPORT_JOURNEY.md`
- `marrybrown_api/docs/VOUCHER_CAMPAIGN_REWARD_SALES_REPORT_JOURNEY.md`
- `marrybrown_api/docs/PROMOTION_ITEM_ADDITIONAL_PURCHASE_REPORT_API.md`
- `marrybrown_api/archive/docs/DAILY_SALES_SUMMARY_API.md`
- `marrybrown_api/archive/docs/DISCOUNT_REMARK_REPORT_API.md`

## 2. Writing Style, Tone, and Format To Preserve

The final report should preserve the same authorial voice already established in the proposal draft, but update the status language from proposal-stage phrasing to final-report phrasing.

Important overriding rule:

- every revision should read as final academic writing suitable for university submission
- do not write as if preparing company handover notes, internal runbooks, engineering playbooks, or repository-maintenance instructions
- internal project documentation may be used as source material for facts, but must not control the tone or structure of the submitted FYP report

### 2.1 Voice and Tone

- Use formal academic English.
- Maintain a neutral, impersonal, professional tone.
- Do not use first-person narration such as `I`, `we`, `our`, or `my`.
- Prefer subjects such as `the project`, `the system`, `the platform`, `this chapter`, and `the implementation`.
- Keep claims measured, traceable, and evidence-led.
- Avoid promotional wording such as `innovative`, `cutting-edge`, `powerful`, or similar overclaiming language.

### 2.2 Language Conventions

- Keep British/Commonwealth spelling where the draft already uses it, such as `organisation`, `prioritise`, `behaviour`, and `authorisation`.
- Keep vendor and technology names exactly as written by their owners, such as `FastAPI`, `React`, `SQL Server`, and `Microsoft SQL Server`.
- Reuse established terminology where still appropriate, especially:
  - `company-owned reporting platform`
  - `1:1 replication`
  - `semantic/API layer`
  - `schema-on-read`
  - `parity validation`
  - `reconciliation`
  - `read-only reporting environment`
  - `Finance and Operations users`

### 2.3 Paragraph Style

- Keep paragraphs compact but information-dense.
- Follow the same pattern already visible in the proposal:
  1. introduce the context,
  2. explain its relevance to this project,
  3. qualify the point with scope, limitation, or implication.
- Avoid filler sentences and abrupt topic jumps.
- Preserve the current chapter-opening pattern, where sections begin with a short orienting paragraph before details, tables, or figures.

### 2.4 Tables and Figures

- Continue using tables for structured items such as scope summaries, requirement lists, report classifications, and implementation outcomes.
- Keep figure captions formal and descriptive.
- Do not suddenly change the document into a narrative-only style; the proposal already relies on structured tables heavily.
- In appendix sections, academic summary tables are appropriate; internal reference-management sections are not.

### 2.5 Final-Report Tense Conversion Rules

The proposal voice should remain, but proposal-stage status wording must be converted to final-report wording.

Use these final-stage words where appropriate:

- `implemented`
- `validated`
- `deployed`
- `delivered`
- `retained`
- `documented`
- `not successfully closed`
- `remained unresolved after reverse engineering and parity validation against the vendor portal`
- `implemented and validated for current agreed scope`

Avoid proposal-only wording outside historical explanation or future-work sections:

- `will be implemented`
- `is being developed`
- `planned for subsequent iterations`
- `expected outcome`
- `as of Week 28`
- `in progress`
- `to be completed iteratively`

Future-tense wording should appear only in a dedicated future enhancement / future work section if required by the university format.

Also avoid internal-handover phrasing such as:

- `official technical handover guide`
- `production cautions`
- `active API surface`
- `route`
- `frontend-only`
- `paired project documentation`
- `archived from the active handover path`

When such ideas are needed in the final report, rewrite them into academic forms such as:

- `implemented report module`
- `validated implementation`
- `documented limitation`
- `excluded from the final retained scope`
- `additional internal report developed during implementation`

### 2.6 Limitation Language

When discussing unresolved reports, do not use casual wording such as `failed` unless explicitly required. Preferred wording:

- `not fully closed`
- `not successfully validated to final parity`
- `remained unresolved after reverse engineering and parity validation against the vendor portal`
- `could not be concluded within the project boundary because the required profit logic could not be isolated`

This keeps the final report honest without making the wording sound careless or self-contradictory.

## 3. Primary Framing Decision

The previous plan to replace `redundancy` with `company-owned reporting continuity and report reconstruction platform` as the main label has been superseded after supervisor feedback.

Current supervisor-aligned naming decision:

- use a specific system name as the main label:
  - `Marrybrown Sales and Payment Analytics Platform`

Guidance:

- Use `Marrybrown Sales and Payment Analytics Platform` when referring to the implemented system.
- The term `redundancy` may still be used where it describes continuity or alternative-access purpose, but it should not make the system sound like a simple copy of the vendor portal.
- The report should explain that the platform was implemented as a new internal system with replicated data, reconstructed backend report logic, customised report modules, and a web portal.
- Avoid overcorrecting by removing every use of `redundancy`. Instead, anchor the project around the named platform and use `redundancy` only as a supporting architectural concept where appropriate.

Recommended framing sentence:

`This project developed the Marrybrown Sales and Payment Analytics Platform, an internal reporting system that replicates selected source-system data into a Microsoft SQL Server reporting database, reconstructs vendor-aligned sales and payment report logic through a FastAPI backend, and provides report search, viewing, export, and administration functions through a React-based web portal.`

Academic-use reminder:

- The named platform should make clear that the project produced a real implemented system, not only a redundancy copy.
- Do not present the project mainly as generic BI, machine learning, or exploratory analytics.
- Do not use internal handover wording such as `runbook`, `operational ownership`, or `maintenance mode` unless a specific chapter requires concise discussion of deployment or support context.

## 4. Report-Scope Arrangement Decision

The previous concern about changing the appendix from the proposal 15-report list has been superseded by supervisor feedback. Because the proposal main chapters did not individually name the 15 reports and referred readers to the appendix, the appendix can be updated freely to reflect the final implementation scope.

Current appendix/report-scope decision:

- keep the final appendix centred on the 19-report implementation scope
- state that 16 of the 19 reports were successfully implemented
- state that 3 of the 19 reports were not fully closed
- explain the reason for the 3 unresolved reports in academic limitation language
- separately mention that 3 additional customised reports were implemented based on company requests

Important:

- It is no longer necessary to preserve the proposal-stage 15-report planning set as a major appendix layer.
- It is acceptable to update the appendix to the final 19-report scope because the proposal main chapters only referred to the appendix for report details.
- The final report should still remain honest about the 3 unresolved reports and should avoid wording such as `failed`.

## 5. Proposal-Stage Planning Set (15 Reports)

This proposal-stage planning set must not be mentioned in the final report.

1. Daily Sales Summary
2. Payment Type (All Payment)
3. Sales Return Report
4. Sales Cancelled Report
5. DELETED Items Report
6. Sale Delivery (By Sales Type) Ex Tax Calculation
7. MB Cash Voucher (with Barcode) Redemption Report
8. MB Staff E-Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report
9. Product Mix Report
10. Discount Remark Report
11. Delivery-FoodPanda,Grabfood,ShopeeFood
12. Foodpanda Sales
13. Foodpanda Discount
14. Mobile Ordering Sales
15. Pickup & Declaration Report

Important note:

- Do not mention the proposal-stage 15-report planning set in the final report.
- Do not mention `Daily Sales Summary` in the final report.
- Use the 19-report implementation/business scope as the report-scope basis instead.

## 6. Formal Implementation / Business Scope (19 Reports)

This is the formal report-scope baseline to use when writing the final report.

1. Sale Delivery (By Sales Type) Ex Tax Calculation
2. Payment type (All Payment)
3. Product Mix Report
4. Delivery - FoodPanda, Grabfood, ShopeeFood
5. Pickup & Declaration Report
6. Stock Variance Report (Latest)
7. Discount Remark Report
8. Foodpanda Sales
9. DELETED Items Report
10. Sales Return Report
11. [SOK] Each Kiosk Transaction Report
12. Sales Cancelled Report
13. Xilnex - Monthly Checking - COGS by Item (By Sales Type)
14. Foodpanda Discount
15. Mobile Ordering Sales
16. Average SOS Report (New)
17. MB Cash Voucher (with Barcode) Redemption Report
18. MB Staff E - Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report
19. Product Mix with modifier without ETL

Important note:

- The 19 reports should be presented together as the formal implementation/business scope.
- Do not separate report 19 as an additional Finance request in the final report.

## 7. Additional Custom / Internal Reports Outside The Formal 19

These should be documented separately from the formal 19:

- Roblox Free Chicken Burger Combo Sales
- Voucher Campaign & Reward Sales
- Promotion Item Additional Purchase Report

Guidance:

- `Roblox Free Chicken Burger Combo Sales`, `Voucher Campaign & Reward Sales`, and `Promotion Item Additional Purchase Report` should be described as additional customised reports developed based on company requests.
- These reports should be positioned as extra delivered work beyond the 19-report baseline scope.
- `Promotion Item Additional Purchase Report` includes an admin-managed configuration layer for promotion item categories, but this admin detail is probably too specific for the main FYP narrative unless needed in Chapter 5 implementation details.
- `Daily Sales Summary` should not be mentioned in the final report.

## 8. Final Delivery Classification To Use During Drafting

The working drafting decision as of 2026-05-14 is:

### 8.1 Formal 19 scope: delivered and retained

- Sale Delivery (By Sales Type) Ex Tax Calculation
- Payment type (All Payment)
- Delivery - FoodPanda, Grabfood, ShopeeFood
- Pickup & Declaration Report
- Stock Variance Report (Latest)
- Foodpanda Sales
- DELETED Items Report
- Sales Return Report
- [SOK] Each Kiosk Transaction Report
- Sales Cancelled Report
- Xilnex - Monthly Checking - COGS by Item (By Sales Type)
- Foodpanda Discount
- Mobile Ordering Sales
- Average SOS Report (New)
- MB Cash Voucher (with Barcode) Redemption Report
- MB Staff E - Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report

### 8.2 Formal 19 scope: not fully closed

- Product Mix Report
- Discount Remark Report
- Product Mix with modifier without ETL

These three should be written as unresolved after reverse engineering and parity validation against the vendor portal, not as simple coding omissions.

For `Product Mix with modifier without ETL`, the final decision is:

- classify it as `Not fully closed`
- state that reverse engineering and parity validation against the vendor portal were not sufficient to isolate the remaining profit logic required for final closure
- do not describe it as delivered and retained in the final active outcome summary

### 8.3 Additional custom/internal reports

- Roblox Free Chicken Burger Combo Sales
- Voucher Campaign & Reward Sales
- Promotion Item Additional Purchase Report

These should be positioned as customised reports implemented based on company requests beyond the 19-report scope, not mixed into the formal 19.

### 8.4 Reports To Exclude From Final Report Discussion

- Daily Sales Summary
- Proposal-stage planning set (15 reports)

## 9. How The Reports Should Be Arranged In The Final Report

Recommended arrangement:

### In the main body

- use the 19-report implementation scope as the main final-report reporting scope
- state the final outcome as 16 successfully implemented reports out of the 19-report scope
- state the 3 not-fully-closed reports as documented limitations
- mention the 3 customised reports separately as company-requested additional work
- do not mention the proposal-stage 15-report planning set or Daily Sales Summary

### In the appendix

The appendix may be updated from the old 15-report proposal appendix to the final 19-report scope.

Recommended appendix arrangement:

1. main table for the 19-report implementation scope with final status
2. short explanation that 16 reports were successfully implemented and 3 were not fully closed
3. report specification tables for the 19 reports in final-report style
4. separate subsection for the 3 customised reports implemented based on company requests

Appendix rule:

- per-report detail tables like the proposal appendix are still needed
- however, they must be rewritten as final-report specification tables, not Week 28 planning placeholders
- avoid sections whose only purpose is to tell the reader which internal repo docs to consult
- do not include the proposal-stage 15-report planning set
- do not include Daily Sales Summary

## 10. Updated Implementation Context To Carry Forward

The following implementation updates occurred after the earlier planning discussion and should be considered when writing the final report.

### 10.1 Data Quality Check For Portal-Triggered Replication

- A data-quality check layer was added for portal-triggered replication.
- Admin users can trigger or review quality checks for sales sync windows.
- Quality checks compare source and replicated data for the selected window and support quality re-check and repair requests.
- This can be mentioned in the final report as part of implementation, testing, or operational reliability, especially in Chapter 5.
- Avoid exposing internal endpoint names, table names, or worker implementation details unless the chapter specifically requires technical design detail.

### 10.2 Automated ETL And Admin Automation Management

- Daily dated ETL and nightly retained-reference automation were implemented as scheduled ETL capabilities.
- A portal admin automation-management page was also implemented so non-technical admin users can view automation status and request enable, disable, or schedule changes.
- The automation-control worker and Windows Task Scheduler integration are implementation details; they can be summarised academically as scheduled ETL automation with admin portal control.
- This update means the final report should not describe unattended ETL as merely planned unless discussing historical development phases.

### 10.3 Promotion Item Additional Purchase Report

- A third customised report was implemented: `Promotion Item Additional Purchase Report`.
- The report analyses sale-level additional-purchase behaviour for configured promotion items.
- The report includes an admin-managed promotion item category configuration layer.
- For the FYP report, this should usually be described at a higher level as a customised company-requested report, not as a detailed admin configuration implementation unless Chapter 5 needs an example of extended functionality.

## 11. Chapter Planning Rules For Final Report

The final report will include two additional chapters after Chapter 4:

- Chapter 5: `Implementation & Testing`
- Chapter 6: `Conclusion`

The provided university template should be interpreted using the development-project path, not the research-project path.

### 11.1 Chapter 5 Template To Follow

Use the development version of Chapter 5:

1. `5.1 Introduction`
2. `5.2 System Development`
3. `5.3 Coding of the system's main functions/Process`
4. `5.4 Summary`

Ignore the research-style Chapter 5 structure:

- `Results and Analysis`
- `Results`
- `Analysis`

### 11.2 Chapter 6 Template To Follow

Use the conclusion chapter structure:

1. `6.1 Introduction`
2. `6.2 System Contribution/Achievement`
3. `6.3 System Constraint`
4. `6.4 Future Suggestion`
5. `6.5 Summary`

### 11.3 Chapter 1 Boundary

Chapter 1 should remain general and introductory.

Do not mention exact report counts such as `19 reports`, `16 of 19`, or `3 customised reports` in Chapter 1 objectives, aim, or scope.

Preferred general wording for Chapter 1:

- `selected sales and payment reports`
- `company-requested reporting modules`
- `targeted operational reports`
- `vendor-aligned sales and payment reports`

Chapter 1 should frame the problem, aim, objectives, scope boundary, and significance without becoming a report-outcome chapter.

### 11.4 Chapter 4 Boundary

Chapter 4 should include an overview of:

- the formal report set
- the customised reports
- how these reports fit into the system analysis and design

Chapter 4 should be more specific than the current proposal draft, which is too general about report coverage. However, it should remain an overview chapter and should refer detailed report specifications to Appendix A.

Chapter 4 should not duplicate Chapter 5 implementation journeys, validation steps, or testing evidence.

### 11.5 Chapter 5 Boundary

Chapter 5 is the main chapter for detailed implementation and testing.

Chapter 5 should include:

- system development overview
- ETL and replication process
- handling of missing data and report mismatches
- report backend reconstruction process
- frontend portal and admin functionality implementation
- overview of each report, with more detail than Chapter 4 but less than Appendix A
- selected report implementation examples
- backend report accuracy validation
- UAT / system testing
- black-box testing and white-box testing where applicable

For selected report implementation examples, choose 1 to 3 reports. A suitable pattern is:

- one formal-scope report example
- one customised report example
- optionally one ETL/data-quality or unresolved-report example if useful

The selected examples should show how the implementation journey worked without exposing sensitive company information.

When explaining backend report validation, describe one report validation process in detail as an example, then state that the same validation approach was applied across report modules.

Performance-writing rule for Chapter 5:

- a short performance subsection may be included in Chapter 5 as part of implementation outcome
- performance discussion must be written as implementation evidence of query tuning and operational usability improvement
- performance discussion must not be written as a formal benchmark against the vendor portal unless a controlled side-by-side vendor-vs-platform timing record exists
- the strongest supported example is `Payment Type (All Payment)`
- compact comparison tables are appropriate in this subsection
- one main table should show the strongest measured before/after example
- one smaller supporting table may summarise a few additional report timing observations
- the subsection should explicitly state that the purpose of the performance work was to reduce timeout risk, improve response consistency, and keep report workflows operationally usable
- avoid overloading the chapter with too many timing numbers
- avoid claiming that the whole platform is generally faster than the vendor portal
- if a timing result is mixed or regressed for some filter shapes, state that honestly

### 11.6 Chapter 6 Boundary

Chapter 6 should focus on:

- system contribution and achievement
- system constraints
- future suggestions
- final conclusion

Chapter 6 should not repeat detailed implementation steps from Chapter 5. It should interpret the project outcome, limitations, and future direction at a higher level.

### 11.7 Public-Safety Rule For Chapter 5

Chapter 5 may be detailed because it records what was implemented and how it was tested, but it must remain public-safe.

Acceptable details:

- SQL Server reporting database
- FastAPI backend
- React portal
- source-to-replica validation
- report parity validation
- admin-managed ETL automation
- data-quality checks
- high-level mismatch investigation and resolution process

Avoid details such as:

- credentials
- tokens
- VPN details
- passwords
- secret file paths
- exact server access instructions
- operational runbook commands unless academically necessary
- overly specific internal endpoint or database table detail unless needed for design explanation

## 12. Final Drafting Guardrails

When updating the final report:

- preserve the proposal's author voice
- convert status wording to final-report tense
- use `Marrybrown Sales and Payment Analytics Platform` as the main system name
- use `redundancy` only as a supporting architectural/continuity concept where appropriate
- write every section as final academic FYP content suitable for university submission
- keep Chapter 1 general and avoid exact report counts there
- use Chapter 4 for report-category and custom-report overview, with details referred to Appendix A
- use Chapter 5 for detailed implementation, ETL, report-building journey, validation, UAT, black-box testing, and white-box testing
- use Chapter 6 for contribution, constraints, future suggestions, and conclusion
- do not write in internal handover, runbook, or repository-governance style
- do not quietly rewrite the proposal history
- do not hide unresolved reports, but describe them precisely as documented limitations
- use the 19-report scope as the main final-report appendix/report scope
- state that 16 of the 19 reports were implemented successfully and 3 were not fully closed
- mention the 3 customised reports separately as company-requested additional work
- do not mention `Daily Sales Summary` in the final report
- do not mention the proposal-stage 15-report planning set in the final report

If future scope decisions change any report classification again, update this note before continuing any large-scale final-report rewrite.
