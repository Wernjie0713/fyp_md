# Appendix A: Report Specifications

## Appendix A: Report Specifications

This appendix organises report-level specifications for the 15 targeted sales and payment reports. As of Week 28 of the internship, seven report APIs have been implemented and validated, while the remaining reports are planned for subsequent iterations. Where a specification is incomplete, fields are marked as [TBD] and will be completed iteratively as the corresponding module is implemented and validated.

### A.1 Specification Template (per report)

| Field | Description |
| --- | --- |
| Report name | [TBD] |
| Business purpose | [TBD] |
| Primary users | [TBD] |
| Parameters | [TBD] (required/optional, defaults) |
| Output (summary) | [TBD] (key fields, totals/subtotals) |
| Data sources | [TBD] (replicated tables/modules) |
| Key business rules | [TBD] (filters, inclusion/exclusion, edge cases) |
| Validation approach | [TBD] (parity checks, reconciliation rules, acceptance criteria) |
| Implementation status | [TBD] (e.g., planned; implemented and validated) |
| Evidence artefacts | [TBD] (e.g., vendor export filenames, internal API documentation) |

*Table A.1: Report specification template fields*

### A.2 Target Report Index (15 reports)

This index lists the 15 targeted reports and provides a convenient place to track implementation and validation status during iterative development.

| ID | Report | Status (Week 28) | Notes / Evidence |
| --- | --- | --- | --- |
| R01 | Daily Sales Summary | Implemented and validated | Internal API documentation (confidential; not included in this report). |
| R02 | Payment Type (All Payment) | Implemented and validated | Internal API documentation (confidential; not included in this report). |
| R03 | Sales Return Report | Implemented and validated | Internal API documentation (confidential; not included in this report). |
| R04 | Sales Cancelled Report | Implemented and validated | Validation artefacts retained (baseline exports and comparison outputs). |
| R05 | DELETED Items Report | Planned | [TBD] |
| R06 | Sale Delivery (By Sales Type) Ex Tax Calculation | Implemented and validated | Validation artefacts retained (baseline exports and comparison outputs). |
| R07 | MB Cash Voucher (with Barcode) Redemption Report | Implemented and validated | Validation artefacts retained (baseline exports and comparison outputs). |
| R08 | MB Staff E-Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report | Implemented and validated | Validation artefacts retained (baseline exports and comparison outputs). |
| R09 | Product Mix Report | Planned | [TBD] |
| R10 | Discount Remark Report | Planned | [TBD] |
| R11 | Delivery-FoodPanda,Grabfood,ShopeeFood | Planned | [TBD] |
| R12 | Foodpanda Sales | Planned | [TBD] |
| R13 | Foodpanda Discount | Planned | [TBD] |
| R14 | Mobile Ordering Sales | Planned | [TBD] |
| R15 | Pickup & Declaration Report | Planned | [TBD] |

*Table A.2: Target report index (15 reports) and status summary (Week 28)*

### A.3 Report Specifications (to be completed iteratively)

#### R01: Daily Sales Summary

| Field | Description |
| --- | --- |
| Report name | Daily Sales Summary |
| Business purpose | To provide a daily, outlet-level summary of sales and profit figures for operational monitoring and finance reconciliation, supporting continuity when the vendor portal is unavailable. |
| Primary users | Finance and Operations (reporting and reconciliation users). |
| Parameters | Business date range (required); optional outlet/location filter list; optional sales status filters aligned with baseline portal behaviour. |
| Output (summary) | Per business date and outlet: sales total and profit total, with optional grand totals across the selected scope. |
| Data sources | Replicated sales transactions and cost/profit attributes (where available), plus outlet/location reference data. |
| Key business rules | Business date is used for scoping; status selection follows baseline portal logic; returns and cancellations are treated consistently with baseline behaviour; totals are computed over the filtered set. |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Implemented and validated (Week 28). |
| Evidence artefacts | Internal API documentation and validation artefacts retained (confidential; not included in this report). |

*Table A.3: Report specification fields for R01 (Daily Sales Summary)*

#### R02: Payment Type (All Payment)

| Field | Description |
| --- | --- |
| Report name | Payment Type (All Payment) |
| Business purpose | To summarise collections by payment method for the chosen period and outlets, supporting cash-up and payment reconciliation activities. |
| Primary users | Finance and Operations (payment reconciliation users). |
| Parameters | Business date range (required); optional outlet/location filter list; optional sales status filters; optional payment status filter (defaults to saved/posted payments). |
| Output (summary) | Collection totals grouped by payment method (and optionally by outlet), including overall total collection for the selected scope. |
| Data sources | Replicated payment transactions linked to sales and outlet/location records, plus payment method reference or mapping logic. |
| Key business rules | Split payments are allocated per sale; only qualifying payment statuses are included; sales status filters exclude void/cancelled records as appropriate; payment method categories are normalised to match baseline portal groupings. |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Implemented and validated (Week 28). |
| Evidence artefacts | Internal API documentation and validation artefacts retained (confidential; not included in this report). |

*Table A.4: Report specification fields for R02 (Payment Type (All Payment)*

#### R03: Sales Return Report

| Field | Description |
| --- | --- |
| Report name | Sales Return Report |
| Business purpose | To list returned items and transactions within the selected period, enabling audit, inventory adjustment support, and reconciliation of return values against baseline exports. |
| Primary users | Finance and Operations (exception review and reconciliation), with secondary use by store operations. |
| Parameters | Business date range (required); optional outlet/location filter list; optional sales status filters; optional item classification filters (type, category, group, division). |
| Output (summary) | Row-level return entries including outlet, date, return document or sale reference, original sale reference (where applicable), item identifier and name, quantity, and net return amount. |
| Data sources | Replicated return transactions linked to original sales where applicable, plus item master and outlet/location reference data. |
| Key business rules | Only return-type transactions are included; item filters follow baseline portal semantics; row grouping and merge behaviour is aligned with the portal output; net return amount follows the baseline calculation and normalisation rules. |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Implemented and validated (Week 28). |
| Evidence artefacts | Internal API documentation and validation artefacts retained (confidential; not included in this report). |

*Table A.5: Report specification fields for R03 (Sales Return Report)*

#### R04: Sales Cancelled Report

| Field | Description |
| --- | --- |
| Report name | Sales Cancelled Report |
| Business purpose | To provide an audit trail of cancelled or voided sales within the selected period, supporting internal control checks and exception review. |
| Primary users | Finance and Operations (audit and exception review users). |
| Parameters | Business date range (required); optional outlet/location filter list; optional item classification filters (type, category, group, division). |
| Output (summary) | Cancelled sale entries including outlet, date, sale reference, quantity, net sold value, and cancellation metadata (cancelled by, remark, cancellation date and location). |
| Data sources | Replicated sales transactions with cancellation markers and related metadata, plus outlet/location and item reference data (where required by filters). |
| Key business rules | Only cancelled/voided transactions within the scoped business date range are included; text fields are normalised for strict parity (e.g., blank and trimming behaviour); filter behaviour mirrors baseline portal semantics. |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Implemented and validated (Week 28). |
| Evidence artefacts | Validation artefacts retained (baseline exports and comparison outputs). |

*Table A.6: Report specification fields for R04 (Sales Cancelled Report)*

#### R05: DELETED Items Report

| Field | Description |
| --- | --- |
| Report name | DELETED Items Report |
| Business purpose | [TBD] |
| Primary users | [TBD] |
| Parameters | [TBD] |
| Output (summary) | [TBD] |
| Data sources | [TBD] |
| Key business rules | [TBD] |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Planned (as of Week 28). |
| Evidence artefacts | [TBD] |

*Table A.7: Report specification fields for R05 (DELETED Items Report)*

#### R06: Sale Delivery (By Sales Type) Ex Tax Calculation

| Field | Description |
| --- | --- |
| Report name | Sale Delivery (By Sales Type) Ex Tax Calculation |
| Business purpose | To break down delivery-related sales by sales type and delivery category, and to report tax-exclusive (ex-tax) totals required for finance checking and reconciliation. |
| Primary users | Finance and Operations (periodic delivery sales checking). |
| Parameters | Business date range (required); optional outlet/location filter list; optional sales status filters; optional payment status filter (defaults aligned with baseline portal behaviour). |
| Output (summary) | Hierarchical breakdown by date and outlet, with further grouping by sales type and delivery category, reporting sales totals and tax-exclusive (ex-tax) metrics for each group. |
| Data sources | Replicated sales transactions and payment records, delivery channel indicators, outlet/location reference data, and tax-related fields needed for ex-tax computation. |
| Key business rules | Ex-tax is computed from tax-inclusive values using the baseline formula; grouping levels match the baseline report structure; merge logic avoids double-counting when multiple sources overlap; default status filters follow baseline portal behaviour. |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Implemented and validated (Week 28). |
| Evidence artefacts | Validation artefacts retained (baseline exports and comparison outputs). |

*Table A.8: Report specification fields for R06 (Sale Delivery (By Sales Type) Ex Tax Calculation)*

#### R07: MB Cash Voucher (with Barcode) Redemption Report

| Field | Description |
| --- | --- |
| Report name | MB Cash Voucher (with Barcode) Redemption Report |
| Business purpose | To track redemption of barcode-based cash vouchers, supporting voucher liability monitoring and reconciliation against baseline exports. |
| Primary users | Finance and Operations (voucher reconciliation users), with secondary use by marketing or promotion owners. |
| Parameters | Business date range (required); optional outlet/location filter list; optional filter to include or exclude specific voucher variants to mirror baseline portal checkbox behaviour. |
| Output (summary) | Voucher redemption entries including redemption date, outlet, voucher identifier (barcode), voucher category, and linked sale or reference identifiers, with summary counts and totals for reconciliation. |
| Data sources | Replicated voucher and payment/redemption records linked to sales, plus outlet/location reference data. |
| Key business rules | Voucher types and identifiers are normalised to match baseline categories; portal checkbox behaviour is reproduced; deduplication prevents fan-out duplicates caused by joins; legacy and null-date edge cases are handled consistently with baseline behaviour. |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Implemented and validated (Week 28). |
| Evidence artefacts | Validation artefacts retained (baseline exports and comparison outputs). |

*Table A.9: Report specification fields for R07 (MB Cash Voucher (with Barcode) Redemption Report)*

#### R08: MB Staff E-Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report

| Field | Description |
| --- | --- |
| Report name | MB Staff E-Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report |
| Business purpose | To track redemption of staff e-vouchers and selected cash voucher variants that use barcodes, supporting controlled staff benefit monitoring and finance reconciliation. |
| Primary users | Finance and Operations (voucher reconciliation), with secondary use by HR or administrators responsible for staff voucher programmes. |
| Parameters | Business date range (required); optional outlet/location filter list; optional filter to include or exclude specific voucher variants to mirror baseline portal checkbox behaviour. |
| Output (summary) | Voucher redemption entries including redemption date, outlet, voucher identifier (barcode), voucher type (staff e-voucher vs cash voucher), and linked sale or reference identifiers, with summary counts and totals for reconciliation. |
| Data sources | Replicated voucher and payment/redemption records linked to sales, plus outlet/location reference data. |
| Key business rules | Voucher codes and types are normalised (including format and casing) to match baseline categories; portal checkbox behaviour is reproduced; deduplication prevents fan-out duplicates caused by joins; historical and legacy records follow baseline date-scope behaviour. |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Implemented and validated (Week 28). |
| Evidence artefacts | Validation artefacts retained (baseline exports and comparison outputs). |

*Table A.10: Report specification fields for R08 (MB Staff E-Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report)*

#### R09: Product Mix Report

| Field | Description |
| --- | --- |
| Report name | Product Mix Report |
| Business purpose | [TBD] |
| Primary users | [TBD] |
| Parameters | [TBD] |
| Output (summary) | [TBD] |
| Data sources | [TBD] |
| Key business rules | [TBD] |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Planned (as of Week 28). |
| Evidence artefacts | [TBD] |

*Table A.11: Report specification fields for R09 (Product Mix Report)*

#### R10: Discount Remark Report

| Field | Description |
| --- | --- |
| Report name | Discount Remark Report |
| Business purpose | [TBD] |
| Primary users | [TBD] |
| Parameters | [TBD] |
| Output (summary) | [TBD] |
| Data sources | [TBD] |
| Key business rules | [TBD] |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Planned (as of Week 28). |
| Evidence artefacts | [TBD] |

*Table A.12: Report specification fields for R10 (Discount Remark Report)*

#### R11: Delivery-FoodPanda,Grabfood,ShopeeFood

| Field | Description |
| --- | --- |
| Report name | Delivery-FoodPanda,Grabfood,ShopeeFood |
| Business purpose | [TBD] |
| Primary users | [TBD] |
| Parameters | [TBD] |
| Output (summary) | [TBD] |
| Data sources | [TBD] |
| Key business rules | [TBD] |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Planned (as of Week 28). |
| Evidence artefacts | [TBD] |

*Table A.13: Report specification fields for R11 (Delivery-FoodPanda,Grabfood,ShopeeFood)*

#### R12: Foodpanda Sales

| Field | Description |
| --- | --- |
| Report name | Foodpanda Sales |
| Business purpose | [TBD] |
| Primary users | [TBD] |
| Parameters | [TBD] |
| Output (summary) | [TBD] |
| Data sources | [TBD] |
| Key business rules | [TBD] |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Planned (as of Week 28). |
| Evidence artefacts | [TBD] |

*Table A.14: Report specification fields for R12 (Foodpanda Sales)*

#### R13: Foodpanda Discount

| Field | Description |
| --- | --- |
| Report name | Foodpanda Discount |
| Business purpose | [TBD] |
| Primary users | [TBD] |
| Parameters | [TBD] |
| Output (summary) | [TBD] |
| Data sources | [TBD] |
| Key business rules | [TBD] |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Planned (as of Week 28). |
| Evidence artefacts | [TBD] |

*Table A.15: Report specification fields for R13 (Foodpanda Discount)*

#### R14: Mobile Ordering Sales

| Field | Description |
| --- | --- |
| Report name | Mobile Ordering Sales |
| Business purpose | [TBD] |
| Primary users | [TBD] |
| Parameters | [TBD] |
| Output (summary) | [TBD] |
| Data sources | [TBD] |
| Key business rules | [TBD] |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Planned (as of Week 28). |
| Evidence artefacts | [TBD] |

*Table A.16: Report specification fields for R14 (Mobile Ordering Sales)*

#### R15: Pickup & Declaration Report

| Field | Description |
| --- | --- |
| Report name | Pickup & Declaration Report |
| Business purpose | [TBD] |
| Primary users | [TBD] |
| Parameters | [TBD] |
| Output (summary) | [TBD] |
| Data sources | [TBD] |
| Key business rules | [TBD] |
| Validation approach | Parity validation against vendor exports (see Chapter 3 Section 3.3.4). |
| Implementation status | Planned (as of Week 28). |
| Evidence artefacts | [TBD] |

*Table A.17: Report specification fields for R15 (Pickup & Declaration Report)*
