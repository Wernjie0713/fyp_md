# Appendix A: Report Scope and Report Specifications

This appendix records the report-scope structure used for the final report and provides a stable reference for the report discussions in the main chapters. Unlike the proposal-stage appendix, this version distinguishes between the historical planning set, the formal implementation/business scope, additional custom reports, and the final delivery classification. This distinction is necessary because the proposal-stage appendix was prepared for planning purposes, whereas the final report must reflect the actual implementation outcome and its documented limitations.

## A.1 Scope Framing Note

The proposal-stage appendix presented a 15-report planning set to support early scheduling, chapter drafting, and incremental implementation tracking. During implementation, the practical report scope was refined against the actual report requirements confirmed through reverse engineering and validation work, together with the additional Finance request. The final report therefore uses the real implementation/business scope as the authoritative basis for outcome reporting, while still preserving the proposal-stage planning set as historical context.

Accordingly, this appendix separates the report scope into four layers:

1. proposal-stage planning set (15 reports)
2. formal implementation/business scope (19 reports)
3. additional custom reports outside the formal 19
4. final delivery classification

## A.2 Proposal-Stage Planning Set (Historical Context)

Table A.1 records the 15-report planning set used in the proposal-stage appendix. This table is preserved only as historical scope context and should not be read as the final authoritative scope table for implementation outcome reporting.

| Planning ID | Report |
| --- | --- |
| P01 | Daily Sales Summary |
| P02 | Payment Type (All Payment) |
| P03 | Sales Return Report |
| P04 | Sales Cancelled Report |
| P05 | DELETED Items Report |
| P06 | Sale Delivery (By Sales Type) Ex Tax Calculation |
| P07 | MB Cash Voucher (with Barcode) Redemption Report |
| P08 | MB Staff E-Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report |
| P09 | Product Mix Report |
| P10 | Discount Remark Report |
| P11 | Delivery-FoodPanda,Grabfood,ShopeeFood |
| P12 | Foodpanda Sales |
| P13 | Foodpanda Discount |
| P14 | Mobile Ordering Sales |
| P15 | Pickup & Declaration Report |

_Table A.1: Proposal-stage planning set (historical context only)_

Important note:

- `Daily Sales Summary` appeared in the proposal-stage planning set but is not part of the final retained report set.
- The proposal-stage planning set was narrower than the later implementation/business scope and should not be used as the sole basis for final outcome discussion.

## A.3 Formal Implementation / Business Scope (Authoritative Final Scope Basis)

Table A.2 records the formal implementation/business scope used as the authoritative baseline for final outcome reporting. This scope comprises the 18 company-requested vendor reports plus 1 additional Finance-requested report.

| Scope ID | Report | Scope category | Final classification | Notes |
| --- | --- | --- | --- | --- |
| S01 | Sale Delivery (By Sales Type) Ex Tax Calculation | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S02 | Payment Type (All Payment) | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S03 | Product Mix Report | Company-requested vendor report | Not fully closed | Reverse engineering and parity validation against the vendor portal were not sufficient to isolate the remaining profit logic required for final closure. |
| S04 | Delivery-FoodPanda,Grabfood,ShopeeFood | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S05 | Pickup & Declaration Report | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S06 | Stock Variance Report (Latest) | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S07 | Discount Remark Report | Company-requested vendor report | Not fully closed | Reverse engineering and parity validation against the vendor portal were not sufficient to isolate the remaining profit logic required for final closure. |
| S08 | Foodpanda Sales | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S09 | DELETED Items Report | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S10 | Sales Return Report | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S11 | [SOK] Each Kiosk Transaction Report | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S12 | Sales Cancelled Report | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S13 | Xilnex - Monthly Checking - COGS by Item (By Sales Type) | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S14 | Foodpanda Discount | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S15 | Mobile Ordering Sales | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S16 | Average SOS Report (New) | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S17 | MB Cash Voucher (with Barcode) Redemption Report | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S18 | MB Staff E-Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report | Company-requested vendor report | Delivered and retained | Implemented, validated, and retained in the final report set. |
| S19 | Product Mix with modifier without ETL | Additional Finance-requested report | Not fully closed | Reverse engineering and parity validation against the vendor portal were not sufficient to isolate the remaining profit logic required for final closure. |

_Table A.2: Formal implementation/business scope and final classification_

## A.4 Additional Custom Reports Outside the Formal 19

In addition to the formal 19-report implementation/business scope, the project also produced custom reports that are not part of the baseline vendor/Finance scope. These are documented separately so they can be recognised as additional implementation work without distorting the formal scope narrative.

| Report | Category | Final classification | Notes |
| --- | --- | --- | --- |
| Roblox Free Chicken Burger Combo Sales | Additional custom report | Implemented and documented | Custom sale-level basket report created for a campaign-specific business question beyond standard vendor-parity reconstruction. |
| Voucher Campaign & Reward Sales | Additional custom report | Implemented and documented | Dynamic custom report family created after the Roblox report to support broader campaign/reward analysis beyond a single fixed campaign. |
| Daily Sales Summary | Historical extra / non-retained report | Implemented historically but not part of the final retained report set | Preserved only as historical traceability material and excluded from the final report set. |

_Table A.3: Additional custom and historical extra reports outside the formal 19_

## A.5 Final Outcome Summary

Based on the formal implementation/business scope in Table A.2, the final outcome can be summarised as follows:

1. Sixteen reports from the formal 19-report scope were delivered and retained as the final validated report set.
2. Three reports from the formal 19-report scope were not fully closed:
   - `Product Mix Report`
   - `Discount Remark Report`
   - `Product Mix with modifier without ETL`
3. Additional custom reports were also implemented outside the formal 19-report scope, including:
   - `Roblox Free Chicken Burger Combo Sales`
   - `Voucher Campaign & Reward Sales`

This classification allows the final report to present the actual project outcome without rewriting the proposal-stage planning history and without understating the extent of the delivered work.

## A.6 Detailed Report Specifications

This section restores the report-by-report specification style used in the proposal appendix, but updates the content into final-report form. The tables below describe the implemented scope, the unresolved reports, and the additional custom reports in academic summary form.

`Daily Sales Summary` is not included in the detailed final-report specification set because it was a historical extra and is not part of the final retained report set.

### A.6.1 Delivered and Retained Reports

#### S01: Sale Delivery (By Sales Type) Ex Tax Calculation

| Field | Description |
| --- | --- |
| Report name | Sale Delivery (By Sales Type) Ex Tax Calculation |
| Business purpose | To analyse delivery-related sales by sales type and delivery platform, including tax-exclusive values required for finance checking and reconciliation. |
| Primary users | Finance and Operations users. |
| Parameters | Date range, outlet/location scope, sales status, payment status, and multi-field search conditions aligned to report usage. |
| Output (summary) | Date- and store-level rows showing delivery type, sales type, transaction quantity, sales totals, tax-exclusive sales, tax amount, and payment-category totals. |
| Data sources | Replicated sales records, payment records, delivery metadata, and location reference data. |
| Key business rules | Payment and sales metrics are combined through aligned grouping; tax-exclusive amounts are derived from validated formulas; filtering is applied before grouped output generation. |
| Validation approach | Reverse engineering and parity validation against vendor portal outputs for matched date, outlet, and filter scopes. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | Advanced search support was included as part of the final validated implementation path. |

_Table A.4: Report specification for Sale Delivery (By Sales Type) Ex Tax Calculation_

#### S02: Payment Type (All Payment)

| Field | Description |
| --- | --- |
| Report name | Payment Type (All Payment) |
| Business purpose | To provide a detailed breakdown of payment collections by store, order source, payment method, device, card type, and reference for reconciliation purposes. |
| Primary users | Finance users, with secondary use by Operations for payment mix checking. |
| Parameters | Date range, outlet/location scope, sales status, and payment status. |
| Output (summary) | Flat grouped rows showing store, order source, payment method, device, reference, and total collection broken down into cash, card, voucher, e-wallet, rounding, and other amounts. |
| Data sources | Replicated payment records, sales headers, and related location and device/reference attributes. |
| Key business rules | Collection totals are grouped by payment dimensions; default scope follows validated completed/saved behaviour; amount subtotals are aligned to portal grouping rules. |
| Validation approach | Reverse engineering and parity validation against vendor portal outputs for matched reporting scopes. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The report reached exact match on validated scopes used during final verification. |

_Table A.5: Report specification for Payment Type (All Payment)_

#### S04: Delivery-FoodPanda,Grabfood,ShopeeFood

| Field | Description |
| --- | --- |
| Report name | Delivery-FoodPanda,Grabfood,ShopeeFood |
| Business purpose | To report delivery-app sales rows across the major delivery channels required by the business, while preserving vendor-aligned row structure. |
| Primary users | Finance and Operations users. |
| Parameters | Date range, outlet/location scope, sales status, sales type, item filters, and supported single-rule search fields. |
| Output (summary) | Flat rows containing date, location, client/cashier metadata, delivery type, sales reference fields, order source, and amount fields. |
| Data sources | Replicated sales headers, sales items, item master data, location reference data, and report-supporting pricing/cost fields. |
| Key business rules | Rows with blank delivery type are excluded; scope is aligned to validated portal behaviour; text fields are normalised before grouping and output. |
| Validation approach | Reverse engineering and parity validation against vendor portal outputs and converted export artefacts. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The final implementation includes supported single-rule search behaviour within the validated scope. |

_Table A.6: Report specification for Delivery-FoodPanda,Grabfood,ShopeeFood_

#### S05: Pickup & Declaration Report

| Field | Description |
| --- | --- |
| Report name | Pickup & Declaration Report |
| Business purpose | To reconcile store-level declared cash, payment collections, safe-deposit movements, and register-float values for reporting sessions. |
| Primary users | Finance users, with operational relevance for store-level declaration review. |
| Parameters | Date range, outlet/location scope, sales status, and payment status. |
| Output (summary) | Session-level rows containing sales totals, payment totals, declared amounts, short/excess values, safe-deposit totals, and register-float totals. |
| Data sources | Replicated sales records, payment records, declaration-related data, register-movement data, and location/cashier metadata. |
| Key business rules | Session regrouping follows validated portal behaviour; short/excess is derived from validated movement logic; only visible parity fields are exposed in the final grouped output. |
| Validation approach | Reverse engineering and strict row-level parity validation against vendor portal exports for matched scopes. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The validated implementation retains only the visible report fields required for parity-aligned reporting. |

_Table A.7: Report specification for Pickup & Declaration Report_

#### S06: Stock Variance Report (Latest)

| Field | Description |
| --- | --- |
| Report name | Stock Variance Report (Latest) |
| Business purpose | To report stock variance by location and item so that inventory discrepancies can be reviewed in a structured report format. |
| Primary users | Operations users, with secondary use by Finance and inventory reviewers. |
| Parameters | Date range, outlet/location scope, item type, category, group name, and supported single-rule search fields. |
| Output (summary) | Flat grouped rows showing item identity, stock-opening values, stock movements, expected and physical closing stock, variance quantity, and variance amount. |
| Data sources | Replicated stock-variance records, item master data, and location reference data. |
| Key business rules | Grouping follows the validated vendor output shape; search is applied before grouped output; vendor cost control is accepted but not used in the validated calculation method. |
| Validation approach | Reverse engineering and parity validation against vendor portal outputs and export artefacts. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The validated implementation covers the current reporting scope without relying on the vendor portal cost control. |

_Table A.8: Report specification for Stock Variance Report (Latest)_

#### S08: Foodpanda Sales

| Field | Description |
| --- | --- |
| Report name | Foodpanda Sales |
| Business purpose | To report Foodpanda sales rows with sufficient transaction, item, and customer context for business review and reconciliation. |
| Primary users | Finance and Operations users. |
| Parameters | Date range, outlet/location scope, sales status, sales type, and item-classification filters aligned to current report usage. |
| Output (summary) | Flat sales rows showing date, location, client metadata, item metadata, order source, quantity, and amount fields. |
| Data sources | Replicated sales headers, sales items, item master data, and location reference data. |
| Key business rules | Scope is aligned to validated Foodpanda sales behaviour; report filters follow portal-equivalent behaviour within the validated implementation; row structure is normalised for strict comparison workflows. |
| Validation approach | Reverse engineering and strict parity validation against vendor portal outputs across multiple reporting windows. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The implementation was treated as fully validated for the supported reporting scope. |

_Table A.9: Report specification for Foodpanda Sales_

#### S09: DELETED Items Report

| Field | Description |
| --- | --- |
| Report name | DELETED Items Report |
| Business purpose | To report item-level void activity, including void quantity, reason, performer, and void amount, for audit and exception review. |
| Primary users | Finance and Operations users. |
| Parameters | Date range and outlet/location scope. |
| Output (summary) | Flat grouped rows showing location, sales number, void time, item code, item name, void performer, void reason, perform type, void quantity, and void amount. |
| Data sources | Replicated void sales-item records, joined sales-item data, item master data, and location reference data. |
| Key business rules | Scope is restricted to the validated void-item perform type; void quantity and amount are grouped deterministically; ordering is normalised for repeatable parity comparison. |
| Validation approach | Reverse engineering and strict content-level parity validation against vendor portal exports. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The validated implementation intentionally preserves the narrower perform-type scope required to match the portal output. |

_Table A.10: Report specification for DELETED Items Report_

#### S10: Sales Return Report

| Field | Description |
| --- | --- |
| Report name | Sales Return Report |
| Business purpose | To report return transactions for audit, reconciliation, and exception review. |
| Primary users | Finance users, with secondary use by store-operations reviewers. |
| Parameters | Date range, outlet/location scope, sales status, and item-classification filters. |
| Output (summary) | Flat rows showing location, item identity, date, sales number, return quantity, net return price, and original sales number. |
| Data sources | Replicated sales headers, sales-item return lines, item master data, and related return-supporting reference tables. |
| Key business rules | Return scope is identified through negative sales-item behaviour and validated return logic; grouped output behaviour is aligned to vendor portal behaviour; item filters follow portal-aligned semantics. |
| Validation approach | Reverse engineering and strict parity validation against vendor portal outputs. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The report was closed with parity-validated grouped output behaviour for the supported scope. |

_Table A.11: Report specification for Sales Return Report_

#### S11: [SOK] Each Kiosk Transaction Report

| Field | Description |
| --- | --- |
| Report name | [SOK] Each Kiosk Transaction Report |
| Business purpose | To report kiosk transaction rows with item, payment, and order-source context for operational and finance review. |
| Primary users | Operations users, with secondary use by Finance. |
| Parameters | Date range, outlet/location scope, sales status, sales type, item filters, and kiosk-only checkbox behaviour. |
| Output (summary) | Flat item-level sales rows showing date, location, order source, table number, sales type, payment method, sales reference, item reference, quantity, and amount fields. |
| Data sources | Replicated sales headers, sales items, payment-related fields, item master data, and location reference data. |
| Key business rules | The report preserves kiosk-only versus all-order-source behaviour; payment-method formatting follows validated visible text rules; date and scope behaviour were refined through parity validation. |
| Validation approach | Reverse engineering and broad parity validation against vendor portal outputs across multiple windows and filter conditions. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The report was broadly validated for the supported scope, including kiosk-specific filtering behaviour. |

_Table A.12: Report specification for [SOK] Each Kiosk Transaction Report_

#### S12: Sales Cancelled Report

| Field | Description |
| --- | --- |
| Report name | Sales Cancelled Report |
| Business purpose | To provide an audit-focused view of cancelled sales transactions and their related metadata. |
| Primary users | Finance and Operations users. |
| Parameters | Date range, outlet/location scope, and item-classification filters. |
| Output (summary) | Flat rows showing location, displayed sales date, sales number, quantity, net sold price, cancelled by, cancelled remark, cancelled date, and cancelled location. |
| Data sources | Replicated sales headers, sales-item records, cancellation metadata, item reference data, and location reference data. |
| Key business rules | Business-date scoping is preserved while displaying the sales-date field; grouped output shape follows validated vendor behaviour; cancellation text fields were normalised for parity. |
| Validation approach | Reverse engineering and strict parity validation against vendor portal exports. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The report reached parity for the supported cancelled-sales scope and retained the required cancellation-text normalisation rules. |

_Table A.13: Report specification for Sales Cancelled Report_

#### S13: Xilnex - Monthly Checking - COGS by Item (By Sales Type)

| Field | Description |
| --- | --- |
| Report name | Xilnex - Monthly Checking - COGS by Item (By Sales Type) |
| Business purpose | To report raw-material consumption and cost by sold item and sales type for periodic checking and reconciliation. |
| Primary users | Finance users, with operational relevance for item-level cost review. |
| Parameters | Date range, outlet/location scope, sales status, sales type, item filters, and supported single-rule search fields. |
| Output (summary) | Grouped rows showing location, business date, sold item name, sales type, raw-material item identity, total raw-material quantity, and total cost amount. |
| Data sources | Replicated sales records, staged sales-item business-date data, item master data, and raw-material / cost-supporting data paths. |
| Key business rules | Grouping aligns sold-item and raw-material item dimensions; search is applied before final grouping; the vendor portal cost control was excluded from the validated calculation method. |
| Validation approach | Reverse engineering and parity validation against vendor portal outputs and vendor export artefacts. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The report was completed for the validated scope, including supported search and export behaviour. |

_Table A.14: Report specification for Xilnex - Monthly Checking - COGS by Item (By Sales Type)_

#### S14: Foodpanda Discount

| Field | Description |
| --- | --- |
| Report name | Foodpanda Discount |
| Business purpose | To report discount rows associated with Foodpanda sales so that discount behaviour can be checked against vendor-aligned output. |
| Primary users | Finance and Operations users. |
| Parameters | Date range, outlet/location scope, sales status, sales type, item filters, item department, brand, and stock-type filters. |
| Output (summary) | Grouped discount rows showing location, sales number, discount remark, discount-related amount fields, and report-supporting metadata. |
| Data sources | Replicated sales headers, sales items, item master data, discount-related fields, and location reference data. |
| Key business rules | Non-empty discount remarks are required for scope alignment; item and stock-type filters follow the validated portal behaviour; the vendor portal cost control does not affect validated output. |
| Validation approach | Reverse engineering and strict parity validation against vendor portal outputs across multiple scopes. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The report was fully validated for the supported discount-reporting scope. |

_Table A.15: Report specification for Foodpanda Discount_

#### S15: Mobile Ordering Sales

| Field | Description |
| --- | --- |
| Report name | Mobile Ordering Sales |
| Business purpose | To report mobile-ordering sales activity with sufficient payment, customer, and order-source detail for operational review and reconciliation. |
| Primary users | Finance and Operations users. |
| Parameters | Date range, outlet/location scope, sales status, sales type, and item-classification filters. |
| Output (summary) | Grouped sales rows showing date, location, client/contact metadata, sales reference, payment method, sales status, sales type, order source, and amount fields. |
| Data sources | Replicated sales headers, sales items, payment-related fields, item master data, and location reference data. |
| Key business rules | Scope is restricted to validated mobile-ordering order sources; payment-method text formatting follows the validated vendor shape; filters follow aligned portal behaviour within the supported scope. |
| Validation approach | Reverse engineering and strict parity validation against vendor portal outputs across multiple windows and status conditions. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The report was treated as fully validated for the current mobile-ordering reporting scope. |

_Table A.16: Report specification for Mobile Ordering Sales_

#### S16: Average SOS Report (New)

| Field | Description |
| --- | --- |
| Report name | Average SOS Report (New) |
| Business purpose | To measure store-level SOS performance through order count and preparation-duration metrics derived from KDS-backed order timing. |
| Primary users | Operations users, with secondary use by performance-review stakeholders. |
| Parameters | Date range, outlet/location scope, sales status, sales type, and limited supported search fields. |
| Output (summary) | Store-level rows showing store name, weighted order count, and preparation-duration totals. |
| Data sources | Replicated KDS order-item data, sales-item linkage, sales headers, and location reference data. |
| Key business rules | Only KDS-backed scope is included; store-level SOS metrics are derived from order-level KDS timing aggregation; unsupported portal controls are intentionally excluded from the implemented scope. |
| Validation approach | Reverse engineering and parity validation against vendor portal behaviour across validated January and July scopes. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | Base aggregation logic was validated for the current scope; some supported search behaviour remained earmarked for a later parity pass. |

_Table A.17: Report specification for Average SOS Report (New)_

#### S17: MB Cash Voucher (with Barcode) Redemption Report

| Field | Description |
| --- | --- |
| Report name | MB Cash Voucher (with Barcode) Redemption Report |
| Business purpose | To report barcode-based cash-voucher redemption activity for voucher monitoring and finance reconciliation. |
| Primary users | Finance users, with secondary use by promotion or campaign owners. |
| Parameters | Date range, outlet/location scope, and checkbox behaviour for MB10-filtered versus full redemption scope. |
| Output (summary) | Flat voucher-redemption rows showing location, owner client ID, date, voucher number, voucher type, sales number, redemption amount, voucher value, quantity, redemption name, and redemption code. |
| Data sources | Replicated payment and sales-item records, voucher records, redemption-type data, loyalty/customer mappings, and location reference data. |
| Key business rules | The report supports both checked and unchecked checkbox modes; voucher-type classification follows validated business logic; searchable redemption identifiers are preserved for report usage. |
| Validation approach | Reverse engineering and parity validation against vendor portal behaviour for the supported checkbox modes and verified scopes. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The report remains dependent on the validated redemption-scope behaviour used during final comparison and checking. |

_Table A.18: Report specification for MB Cash Voucher (with Barcode) Redemption Report_

#### S18: MB Staff E-Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report

| Field | Description |
| --- | --- |
| Report name | MB Staff E-Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report |
| Business purpose | To report redemption activity for staff e-vouchers and the related MB10 cash-voucher family in a vendor-aligned reporting format. |
| Primary users | Finance users, with secondary use by programme administrators. |
| Parameters | Date range, outlet/location scope, and checkbox behaviour for MB20/MB10-filtered versus full redemption scope. |
| Output (summary) | Flat voucher-redemption rows showing location, owner client ID, date, voucher number, voucher type, sales number, redemption amount, voucher value, quantity, redemption name, and redemption code. |
| Data sources | Replicated payment and sales-item records, voucher records, redemption-type data, customer/loyalty mappings, and location reference data. |
| Key business rules | The report preserves the portal checkbox behaviour; voucher classification and union logic follow the validated implementation path; searchable redemption identifiers remain available for report use. |
| Validation approach | Reverse engineering and parity validation against vendor portal behaviour for the supported voucher-reporting scopes. |
| Final implementation status | Delivered and retained. |
| Notes / limitation | The report was finalised for the supported voucher-reporting scope used during implementation and validation. |

_Table A.19: Report specification for MB Staff E-Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report_

### A.6.2 Reports Not Fully Closed

#### S03: Product Mix Report

| Field | Description |
| --- | --- |
| Report name | Product Mix Report |
| Business purpose | To reproduce the vendor Product Mix hierarchy for item-level sales, price, and cost analysis across store and sales-type groupings. |
| Primary users | Finance and Operations users. |
| Parameters | Date range, outlet/location scope, sales status, sales type, item type, category, brand, item division, group name, and cost selection. |
| Output (summary) | Hierarchical grouped output organised by store, sales type, category, device name, item name, total cost amount, unit sold price, and derived metrics. |
| Data sources | Replicated sales headers, sales items, item master data, location pricing, recipe summary, menu mapping data, and price-log support fields. |
| Key business rules | Cost and price logic depends on sales-type-sensitive source selection, menu mapping, price fallback paths, and combo-line suppression rules. |
| Validation approach | Reverse engineering and parity validation against vendor portal outputs for matched reporting scopes. |
| Final implementation status | Not fully closed. |
| Notes / limitation | The remaining profit logic required for final parity closure could not be isolated within the project boundary. |

_Table A.20: Report specification for Product Mix Report_

#### S07: Discount Remark Report

| Field | Description |
| --- | --- |
| Report name | Discount Remark Report |
| Business purpose | To report discount-related rows and remarks required for finance checking and discount review. |
| Primary users | Finance users, with secondary use by Operations when investigating discount behaviour. |
| Parameters | Date range, outlet/location scope, and the report-specific filters required to align discount rows with the visible output behaviour. |
| Output (summary) | Discount-related rows with location, sales reference, discount-remark fields, and associated amount values needed for review and reconciliation. |
| Data sources | Replicated sales headers, sales items, discount-related fields, item reference data, and location reference data. |
| Key business rules | Discount-row scope, grouping, and value derivation must align to the vendor portal's visible output behaviour and remark handling. |
| Validation approach | Reverse engineering and parity validation against vendor portal outputs for matched scopes. |
| Final implementation status | Not fully closed. |
| Notes / limitation | The remaining profit logic required for final closure could not be isolated through the completed reverse-engineering and validation work. |

_Table A.21: Report specification for Discount Remark Report_

#### S19: Product Mix with modifier without ETL

| Field | Description |
| --- | --- |
| Report name | Product Mix with modifier without ETL |
| Business purpose | To report product-mix rows with modifier-sensitive values, including quantity, net sold price, profit, and tax-adjusted item-value metrics. |
| Primary users | Finance users, with relevance for item-level performance checking. |
| Parameters | Date range, outlet/location scope, sales status, sales type, item filters, item department, brand, stock type, and supported advanced-search conditions. |
| Output (summary) | Flat aggregated rows containing category, item code, item name, quantity, net sold price, net sold profit, sold item price ex. tax, and net sold price ex. MGST tax. |
| Data sources | Replicated sales headers, sales-item records, item master data, location reference data, and supporting tax / pricing fields. |
| Key business rules | Filter normalisation, stock-type derivation, and amount calculations were reconstructed to align with validated report behaviour for the supported scopes. |
| Validation approach | Reverse engineering and parity validation against vendor portal outputs across completed, cancelled, and filtered scenarios. |
| Final implementation status | Not fully closed. |
| Notes / limitation | One remaining profit-related column logic could not be isolated sufficiently for final closure, so the report is documented as unresolved in the final outcome. |

_Table A.22: Report specification for Product Mix with modifier without ETL_

### A.6.3 Additional Custom Reports

#### C01: Roblox Free Chicken Burger Combo Sales

| Field | Description |
| --- | --- |
| Report name | Roblox Free Chicken Burger Combo Sales |
| Business purpose | To analyse whether Roblox voucher redemptions occurred as voucher-only transactions or alongside additional paid purchases and other basket activity. |
| Primary users | Business stakeholders responsible for campaign monitoring, with finance-review relevance. |
| Parameters | Campaign-specific voucher scope, date range, outlet/location scope, and the report controls needed to inspect basket-level transaction behaviour. |
| Output (summary) | Sale-level rows showing Roblox voucher usage together with same-sale basket context and additional-purchase visibility. |
| Data sources | Voucher records, voucher master and redemption-type data, sales headers, sales items, and location reference data. |
| Key business rules | The report is voucher-driven rather than payment-driven and reconstructs basket context from Roblox-linked voucher activity. |
| Validation approach | Reverse engineering, source inspection, and implementation validation against the intended business question. |
| Final implementation status | Implemented as an additional custom report. |
| Notes / limitation | This report extends beyond the standard vendor-parity scope and addresses a custom campaign-analysis use case. |

_Table A.23: Report specification for Roblox Free Chicken Burger Combo Sales_

#### C02: Voucher Campaign & Reward Sales

| Field | Description |
| --- | --- |
| Report name | Voucher Campaign & Reward Sales |
| Business purpose | To generalise the campaign-basket analysis model beyond Roblox by allowing the user to examine additional voucher campaign or reward-linked sales behaviour. |
| Primary users | Business stakeholders responsible for campaign and reward review. |
| Parameters | Campaign or reward selection, date range, outlet/location scope, and the report controls needed to analyse basket behaviour after redemption. |
| Output (summary) | Sale-level rows showing the selected campaign or reward event together with same-sale bundle and additional-purchase context. |
| Data sources | Voucher records, voucher master data, redemption-type mappings, sales headers, sales items, and location reference data. |
| Key business rules | Selector logic is restricted to campaign/reward families that behave as basket anchors; money-like and discount-only voucher families are intentionally excluded from this report family. |
| Validation approach | Reverse engineering, source inspection, and implementation validation for the intended custom business-analysis use case. |
| Final implementation status | Implemented as an additional custom report. |
| Notes / limitation | This report family was developed as an additional custom implementation and is not part of the formal 19-report business scope. |

_Table A.24: Report specification for Voucher Campaign & Reward Sales_
