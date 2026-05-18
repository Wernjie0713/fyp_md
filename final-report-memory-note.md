# Final Report Memory Note

Date: 2026-05-14

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

The word `redundancy` is too narrow to be the main label for the final report.

Primary framing term to use:

- `company-owned reporting continuity and report reconstruction platform`

Shorter acceptable fallback term:

- `vendor-aligned report reconstruction platform`

Guidance:

- `redundancy` may still appear secondarily when explaining continuity benefits, but it should not be the main descriptor of the project.
- The final report should emphasise that the work involved replicated data, reverse engineering, report reconstruction, validation against vendor outputs, and a better internal portal, not mere copying of the vendor system.

Recommended framing sentence:

`This project developed a company-owned reporting continuity and report reconstruction platform for Marrybrown by replicating selected source-system data into an internal SQL Server reporting warehouse, reconstructing vendor-aligned report logic through a FastAPI semantic layer, and delivering validated report access through a web portal.`

Academic-use reminder:

- this framing is for the university report itself
- do not surround it with handover-oriented wording such as `runbook`, `operational ownership`, or `maintenance mode` unless a specific chapter requires concise discussion of deployment or support context

## 4. Report-Scope Arrangement Decision

Do not flatten all reports into one list. The final report should separate report scope into four layers:

1. `Proposal-stage planning set (15 reports)`
2. `Formal implementation/business scope (19 reports)`
3. `Additional custom/internal reports outside the formal 19`
4. `Final delivery classification`

This separation is required because:

- the proposal appendix used a 15-report planning set that included `Daily Sales Summary`
- the real implementation/business scope is the 19-report vendor/Finance set
- the active API surface later also included custom reports such as Roblox and Voucher Campaign
- rewriting the history of the scope after the fact would be weaker than documenting the scope evolution clearly

## 5. Proposal-Stage Planning Set (15 Reports)

This list is historical only. It should be described as the proposal-stage planning set, not as the final authoritative scope table.

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

- This proposal-stage 15 was a planning set and does not match the final formal business scope exactly.
- `Daily Sales Summary` was used in the proposal planning appendix but is not part of the final retained active handover surface.

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

- Reports 1 to 18 reflect the company-requested vendor scope.
- Report 19 is the additional Finance request and is part of the formal implementation/business scope.

## 7. Additional Custom / Internal Reports Outside The Formal 19

These should be documented separately from the formal 19:

- Roblox Free Chicken Burger Combo Sales
- Voucher Campaign & Reward Sales

Historical / non-retained extra:

- Daily Sales Summary

Guidance:

- `Roblox Free Chicken Burger Combo Sales` and `Voucher Campaign & Reward Sales` should be described as additional custom reports developed beyond the baseline vendor-parity scope.
- `Daily Sales Summary` should not be mixed back into the formal final scope table. If mentioned, it should be described only as a historical extra / early internal implementation that was later removed from the final retained active handover surface.

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

These should be positioned as additive work beyond the baseline vendor/Finance scope, not mixed into the formal 19.

### 8.4 Historical extra not part of final retained active surface

- Daily Sales Summary

## 9. How The Reports Should Be Arranged In The Final Report

Recommended arrangement:

### In the main body

- explain the proposal-stage 15 only briefly as historical planning context
- explain that implementation-stage business scope was confirmed against the real 19-report set
- state the final outcome using the actual delivery classification, not the old Week 28 planning table
- mention additional custom reports separately as extra implemented work

### In the appendix

Do not keep the old 15-report appendix structure as the final authoritative status table, but do keep report-by-report academic specification tables.

Recommended appendix arrangement:

1. short note on the proposal-stage 15-report planning set
2. main table for the formal 19-report implementation/business scope with final classification
3. separate short subsection for additional custom/internal reports
4. report specification tables for the formal-scope reports in final-report style
5. optional short note that `Daily Sales Summary` was a historical extra and is not part of the final retained active scope

Appendix rule:

- per-report detail tables like the proposal appendix are still needed
- however, they must be rewritten as final-report specification tables, not Week 28 planning placeholders
- avoid sections whose only purpose is to tell the reader which internal repo docs to consult

## 10. Final Drafting Guardrails

When updating the final report:

- preserve the proposal's author voice
- convert status wording to final-report tense
- use `company-owned reporting continuity and report reconstruction platform` as the main framing term
- write every section as final academic FYP content suitable for university submission
- do not write in internal handover, runbook, or repository-governance style
- do not quietly rewrite the proposal history
- do not hide unresolved reports, but describe them precisely as documented limitations
- do not let `Daily Sales Summary` distort the formal final scope
- do not mix custom reports such as Roblox or Voucher Campaign into the formal 19 unless the scope model is intentionally changed and this note is updated first

If future scope decisions change any report classification again, update this note before continuing any large-scale final-report rewrite.
