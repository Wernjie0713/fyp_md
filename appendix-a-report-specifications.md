# Appendix A: Report Specifications

This appendix summarises the report specifications for the Marrybrown Sales and Payment Analytics Platform. The formal implementation and business scope comprised 19 sales and payment reports. Of these, 16 reports were implemented and validated for the retained final scope, while 3 reports were not fully closed after reverse engineering and parity validation against the vendor portal. In addition, 3 customised reports were implemented based on company requests beyond the formal 19-report scope.

## A.1 Formal Implementation and Business Scope Report Index

*Table A.1: Formal implementation and business scope report index*

| ID | Report | Report group | Final status | Notes |
| --- | --- | --- | --- | --- |
| R01 | Sale Delivery (By Sales Type) Ex Tax Calculation | Delivery and ordering channels | Implemented and validated | Delivered as a vendor-aligned delivery sales and ex-tax reporting module. |
| R02 | Payment Type (All Payment) | Payment and voucher reconciliation | Implemented and validated | Delivered as a payment-method reconciliation report. |
| R03 | Product Mix Report | Product, stock, and cost analysis | Not fully closed | Reverse engineering and parity validation were not sufficient to isolate the remaining profit logic required for final closure. |
| R04 | Delivery - FoodPanda, Grabfood, ShopeeFood | Delivery and ordering channels | Implemented and validated | Delivered as a delivery-channel sales reporting module. |
| R05 | Pickup & Declaration Report | Sales and exception control | Implemented and validated | Delivered as a session-level sales, declaration, and collection control report. |
| R06 | Stock Variance Report (Latest) | Product, stock, and cost analysis | Implemented and validated | Delivered as an inventory variance monitoring report. |
| R07 | Discount Remark Report | Discount monitoring | Not fully closed | Reverse engineering and parity validation were not sufficient to isolate the remaining profit logic required for final closure. |
| R08 | Foodpanda Sales | Delivery and ordering channels | Implemented and validated | Delivered as a channel-specific item-level sales report. |
| R09 | DELETED Items Report | Sales and exception control | Implemented and validated | Delivered as a void-item audit report. |
| R10 | Sales Return Report | Sales and exception control | Implemented and validated | Delivered as an item-return review and reconciliation report. |
| R11 | [SOK] Each Kiosk Transaction Report | Sales and exception control | Implemented and validated | Delivered as a kiosk transaction monitoring report. |
| R12 | Sales Cancelled Report | Sales and exception control | Implemented and validated | Delivered as a cancelled-sales audit report. |
| R13 | Xilnex - Monthly Checking - COGS by Item (By Sales Type) | Product, stock, and cost analysis | Implemented and validated | Delivered as an item-level monthly cost-of-goods checking report. |
| R14 | Foodpanda Discount | Delivery and ordering channels | Implemented and validated | Delivered as a discount-focused Foodpanda reporting module. |
| R15 | Mobile Ordering Sales | Delivery and ordering channels | Implemented and validated | Delivered as a mobile-ordering sales report. |
| R16 | Average SOS Report (New) | Service and operational timing | Implemented and validated | Delivered as a store-level service-duration monitoring report. |
| R17 | MB Cash Voucher (with Barcode) Redemption Report | Payment and voucher reconciliation | Implemented and validated | Delivered as a barcode voucher redemption report. |
| R18 | MB Staff E - Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report | Payment and voucher reconciliation | Implemented and validated | Delivered as a staff and cash voucher redemption control report. |
| R19 | Product Mix with modifier without ETL | Product, stock, and cost analysis | Not fully closed | Reverse engineering and parity validation were not sufficient to isolate the remaining profit logic required for final closure. |

## A.2 Additional Customised Reports

*Table A.2: Additional customised reports implemented beyond the formal 19-report scope*

| ID | Customised report | Reporting purpose | Final status |
| --- | --- | --- | --- |
| C01 | Roblox Free Chicken Burger Combo Sales | Tracks a company-requested promotional sales scenario for campaign monitoring and checking. | Implemented and validated |
| C02 | Voucher Campaign & Reward Sales | Tracks campaign- and reward-related voucher sales activity requested during implementation. | Implemented and validated |
| C03 | Promotion Item Additional Purchase Report | Analyses additional-purchase behaviour for selected promotion items requested by the company. | Implemented and validated |

## A.3 Detailed Report Specifications for the Formal 19-Report Scope

### R01: Sale Delivery (By Sales Type) Ex Tax Calculation

*Table A.3: Detailed specification for R01*

| Field | Description |
| --- | --- |
| Report name | Sale Delivery (By Sales Type) Ex Tax Calculation |
| Business purpose | To analyse delivery-related sales by sales type and delivery channel while presenting tax-exclusive values required for finance checking and channel reconciliation. |
| Primary users | Finance and Operations users. |
| Parameters | Start date and end date (required); optional outlet scope; optional sales status and payment status filters; optional advanced search conditions where detailed transaction filtering is needed. |
| Output summary | Returns grouped rows by date, store, sales type, sales return type, and delivery type, with transaction quantity, sales totals, tax-exclusive amounts, tax amount, payment-bucket amounts, and summary totals. |
| Data scope | Replicated sales records, payment records, location data, and supporting customer-search metadata where relevant to advanced search. |
| Key business rules | Delivery and payment metrics are reconstructed through merged sales-side and payment-side logic; grouping follows vendor-aligned delivery hierarchy; monetary totals are normalised after aggregation; all-zero rows are suppressed from the final output. |
| Validation approach | Report output was validated through parity comparison against vendor portal exports using matched reporting windows and filter selections. |
| Final status | Implemented and validated. |

### R02: Payment Type (All Payment)

*Table A.4: Detailed specification for R02*

| Field | Description |
| --- | --- |
| Report name | Payment Type (All Payment) |
| Business purpose | To provide a detailed breakdown of sales collections by payment method for reconciliation, outlet review, and month-end checking. |
| Primary users | Finance and Operations users. |
| Parameters | Start date and end date (required); optional outlet scope; optional sales status filter; optional payment status filter. |
| Output summary | Returns rows grouped by store, order source, payment method, device, card type, and reference, with total collection and payment-bucket amounts. |
| Data scope | Replicated payment records, sales records, and outlet reference data. |
| Key business rules | Payment rows are grouped to reproduce portal payment presentation; payment-method categories are normalised into cash, card, voucher, e-wallet, and other buckets; return sales and non-qualifying records are excluded according to report rules. |
| Validation approach | Report output was validated through parity comparison against vendor portal exports across selected date ranges and store scopes. |
| Final status | Implemented and validated. |

### R03: Product Mix Report

*Table A.5: Detailed specification for R03*

| Field | Description |
| --- | --- |
| Report name | Product Mix Report |
| Business purpose | To present item-level product sales composition for management review, quantity checking, and profit-related analysis. |
| Primary users | Finance and Operations users. |
| Parameters | Start date and end date (required); expected outlet scope and item-related optional filters consistent with product-level reporting requirements. |
| Output summary | Intended to return item-level grouped sales rows with quantity, value, and profit-related measures. |
| Data scope | Replicated sales records, sales item records, item master data, and supporting reference data required for product-level grouping and profit-related calculations. |
| Key business rules | The report depends on correct product-level grouping, item classification, and profit-related derivation consistent with portal behaviour. |
| Validation approach | Reverse engineering and parity validation were performed against vendor portal behaviour, but the remaining profit-related logic could not be isolated conclusively within the project boundary. |
| Final status | Not fully closed. |

### R04: Delivery - FoodPanda, Grabfood, ShopeeFood

*Table A.6: Detailed specification for R04*

| Field | Description |
| --- | --- |
| Report name | Delivery - FoodPanda, Grabfood, ShopeeFood |
| Business purpose | To provide delivery-channel sales visibility across the main third-party ordering platforms used in the reporting scope. |
| Primary users | Finance and Operations users. |
| Parameters | Start date and end date (required); optional outlet scope; optional sales status filter; optional item-related filters such as type, category, group name, item division, and brand where applicable. |
| Output summary | Returns delivery-channel sales rows and totals aligned to platform-specific sales activity across FoodPanda, GrabFood, and ShopeeFood. |
| Data scope | Replicated sales records, sales item records, item master data, outlet reference data, and delivery-related sales attributes. |
| Key business rules | Channel classification must follow delivery-type logic consistent with portal output; item filters must behave consistently across channels; rows outside the required delivery scope are excluded. |
| Validation approach | Report output was validated through parity comparison against vendor portal exports for selected channels, date ranges, and outlet scopes. |
| Final status | Implemented and validated. |

### R05: Pickup & Declaration Report

*Table A.7: Detailed specification for R05*

| Field | Description |
| --- | --- |
| Report name | Pickup & Declaration Report |
| Business purpose | To monitor cashier session-level sales, collection, declaration, and short/excess behaviour for operational and reconciliation control. |
| Primary users | Finance, Operations, and supervisory users involved in cash-control checking. |
| Parameters | Start date and end date (required); optional outlet scope; optional sales status filter; optional payment status filter. |
| Output summary | Returns session-level rows containing sales totals, payment collections, declaration amounts, short/excess values, safe-deposit totals, and register-float totals. |
| Data scope | Replicated sales records, payment records, register-log records, denomination-related records, and outlet/session reference data. |
| Key business rules | Multiple source branches are regrouped into the portal-visible session shape; short/excess is derived from internal movement and declaration totals; zero-only grouped rows are suppressed from the final output. |
| Validation approach | Report output was validated through strict parity comparison against vendor workbook exports for matched date ranges and status scopes. |
| Final status | Implemented and validated. |

### R06: Stock Variance Report (Latest)

*Table A.8: Detailed specification for R06*

| Field | Description |
| --- | --- |
| Report name | Stock Variance Report (Latest) |
| Business purpose | To present outlet-level inventory variance by item so that stock discrepancies can be reviewed and followed up operationally. |
| Primary users | Operations, inventory, and Finance users. |
| Parameters | Start date and end date (required); optional outlet scope; optional type, category, and group-name filters; optional advanced search over item and store attributes. |
| Output summary | Returns grouped rows by store and item, including opening stock, received quantity, purchase return, wastage, transfer, staff meal, expected sold quantity, expected and physical closing stock, variance quantity, and variance amount. |
| Data scope | Replicated stock, stock-take, stock-received, sales, sales item, item master, vendor, and outlet-related records. |
| Key business rules | Inventory movement, stockcheck, and sold-quantity logic are combined to produce the latest variance view; grouping follows vendor-visible item hierarchy; advanced search is applied before final grouping. |
| Validation approach | Report output was validated against vendor workbook exports and cross-checked across source, replica, API, and frontend output for the validated scope. |
| Final status | Implemented and validated. |

### R07: Discount Remark Report

*Table A.9: Detailed specification for R07*

| Field | Description |
| --- | --- |
| Report name | Discount Remark Report |
| Business purpose | To provide visibility into discount usage and associated remarks for checking, review, and exception follow-up. |
| Primary users | Finance and Operations users. |
| Parameters | Start date and end date (required); expected outlet scope and discount-related optional filters consistent with discount-level reporting. |
| Output summary | Intended to return discount-related rows with sales context, discount information, remarks, and profit-related measures. |
| Data scope | Replicated sales records, sales item records, discount-related fields, and supporting item and outlet reference data. |
| Key business rules | The report depends on accurate discount-level grouping, remark handling, and profit-related derivation consistent with portal behaviour. |
| Validation approach | Reverse engineering and parity validation were performed against vendor portal behaviour, but the remaining profit-related logic could not be isolated conclusively within the project boundary. |
| Final status | Not fully closed. |

### R08: Foodpanda Sales

*Table A.10: Detailed specification for R08*

| Field | Description |
| --- | --- |
| Report name | Foodpanda Sales |
| Business purpose | To provide item-level Foodpanda sales visibility for channel-specific operational checking and reconciliation. |
| Primary users | Finance and Operations users. |
| Parameters | Start date and end date (required); optional outlet scope; optional sales status filter; optional sales type, type, category, group name, item division, and brand filters. |
| Output summary | Returns item-level Foodpanda sales rows including date, location, customer and cashier metadata, delivery type, sales reference, quantity, and net and gross sold amounts. |
| Data scope | Replicated sales records, sales item records, item master data, location data, and supporting recipe or package-related reference paths needed by the validated logic. |
| Key business rules | Only rows within the intended Foodpanda delivery scope are retained; delivery-type and item-filter behaviour is aligned to portal semantics; row structure remains item-level for checking and export purposes. |
| Validation approach | Report output was validated through strict parity comparison against vendor portal exports across multiple windows and filtered scenarios. |
| Final status | Implemented and validated. |

### R09: DELETED Items Report

*Table A.11: Detailed specification for R09*

| Field | Description |
| --- | --- |
| Report name | DELETED Items Report |
| Business purpose | To provide an audit view of deleted or voided items for operational control and exception review. |
| Primary users | Finance, Operations, and supervisory users. |
| Parameters | Start date and end date (required); optional outlet scope. |
| Output summary | Returns item-level void rows including location, sales number, void time, item code, item name, void person, void reason, perform type, void quantity, and void amount. |
| Data scope | Replicated void-item records, sales item records, sales records, item master data, and outlet reference data. |
| Key business rules | The report is constrained to the portal-aligned void-item scope; void quantity and amount are aggregated at the report-row level; ordering is stabilised to keep consistent row presentation. |
| Validation approach | Report output was validated through strict parity comparison against vendor portal export output for matched date windows. |
| Final status | Implemented and validated. |

### R10: Sales Return Report

*Table A.12: Detailed specification for R10*

| Field | Description |
| --- | --- |
| Report name | Sales Return Report |
| Business purpose | To list returned items and related values for reconciliation, outlet review, and exception control. |
| Primary users | Finance and Operations users. |
| Parameters | Start date and end date (required); optional outlet scope; optional sales status filter; optional item-related filters such as type, category, group name, and item division where applicable. |
| Output summary | Returns item-level return rows containing sales and return references, item details, quantities, and monetary return values. |
| Data scope | Replicated sales records, return-related sales item records, item master data, and outlet reference data. |
| Key business rules | Only return-scope transactions are included; item filtering and row grouping must reproduce portal behaviour; return values are presented in export-ready tabular form. |
| Validation approach | Report output was validated through parity comparison against vendor portal exports for matched scopes and item-filter conditions. |
| Final status | Implemented and validated. |

### R11: [SOK] Each Kiosk Transaction Report

*Table A.13: Detailed specification for R11*

| Field | Description |
| --- | --- |
| Report name | [SOK] Each Kiosk Transaction Report |
| Business purpose | To present kiosk transaction records for channel monitoring, transaction review, and operational follow-up. |
| Primary users | Operations and Finance users. |
| Parameters | Start date and end date (required); optional outlet scope; optional transaction or item-related filters where applicable to kiosk-report usage. |
| Output summary | Returns kiosk transaction rows aligned to the required portal transaction view, including kiosk-related transaction context and monetary values. |
| Data scope | Replicated sales records, payment records where required, outlet reference data, and kiosk-related transactional attributes. |
| Key business rules | Kiosk transactions are isolated according to the defined channel logic; output retains the required transaction-level visibility for checking and export. |
| Validation approach | Report output was validated through parity comparison against vendor portal exports for the retained kiosk-report scope. |
| Final status | Implemented and validated. |

### R12: Sales Cancelled Report

*Table A.14: Detailed specification for R12*

| Field | Description |
| --- | --- |
| Report name | Sales Cancelled Report |
| Business purpose | To provide an audit trail of cancelled sales for exception control, follow-up, and reconciliation review. |
| Primary users | Finance and Operations users. |
| Parameters | Start date and end date (required); optional outlet scope; optional item-related filters where applicable. |
| Output summary | Returns cancelled-sales rows containing outlet, date, sales reference, quantity, sold value, and cancellation-related details such as cancelling user and remarks. |
| Data scope | Replicated sales records, cancellation metadata, item-related records where required by filtering, and outlet reference data. |
| Key business rules | Only cancelled or voided sales within the selected date scope are included; output ordering and textual normalisation follow portal display behaviour. |
| Validation approach | Report output was validated through parity comparison against vendor portal exports for matched scopes. |
| Final status | Implemented and validated. |

### R13: Xilnex - Monthly Checking - COGS by Item (By Sales Type)

*Table A.15: Detailed specification for R13*

| Field | Description |
| --- | --- |
| Report name | Xilnex - Monthly Checking - COGS by Item (By Sales Type) |
| Business purpose | To support monthly checking of item-level cost of goods sold by sales type for Finance review and cost monitoring. |
| Primary users | Finance users. |
| Parameters | Start date and end date (required); optional outlet scope; optional sales type and item-related filters where applicable. |
| Output summary | Returns item-level rows grouped by sales type, with quantity, value, and cost-related fields required for monthly COGS checking. |
| Data scope | Replicated sales records, sales item records, item master data, cost-related attributes, and outlet reference data. |
| Key business rules | Cost and sales-type grouping must remain consistent with the validated monthly-checking view; item-level output is retained for checking rather than reduced to a dashboard summary. |
| Validation approach | Report output was validated through parity comparison against vendor portal exports for the retained monthly-checking scope. |
| Final status | Implemented and validated. |

### R14: Foodpanda Discount

*Table A.16: Detailed specification for R14*

| Field | Description |
| --- | --- |
| Report name | Foodpanda Discount |
| Business purpose | To provide discount-level visibility for Foodpanda-related transactions so that channel discount behaviour can be reviewed and reconciled. |
| Primary users | Finance and Operations users. |
| Parameters | Start date and end date (required); optional outlet scope; optional sales status and item-related filters where applicable. |
| Output summary | Returns Foodpanda discount rows and totals aligned to the portal's discount-focused reporting view for the channel. |
| Data scope | Replicated sales records, sales item records, discount-related fields, item master data, and outlet reference data. |
| Key business rules | Only Foodpanda-scope transactions are included; discount grouping and item-filter behaviour must remain aligned to the validated channel-report rules. |
| Validation approach | Report output was validated through parity comparison against vendor portal exports for matched Foodpanda reporting windows. |
| Final status | Implemented and validated. |

### R15: Mobile Ordering Sales

*Table A.17: Detailed specification for R15*

| Field | Description |
| --- | --- |
| Report name | Mobile Ordering Sales |
| Business purpose | To provide sales visibility for mobile-ordering transactions as a distinct ordering channel within the reporting platform. |
| Primary users | Finance and Operations users. |
| Parameters | Start date and end date (required); optional outlet scope; optional sales status and item-related filters where applicable. |
| Output summary | Returns mobile-ordering sales rows and totals aligned to the required portal reporting view for the channel. |
| Data scope | Replicated sales records, sales item records, item master data, outlet reference data, and ordering-channel attributes. |
| Key business rules | Channel classification must distinguish mobile-ordering sales from other sales types; report output remains export-oriented and transaction-traceable. |
| Validation approach | Report output was validated through parity comparison against vendor portal exports for matched mobile-ordering scopes. |
| Final status | Implemented and validated. |

### R16: Average SOS Report (New)

*Table A.18: Detailed specification for R16*

| Field | Description |
| --- | --- |
| Report name | Average SOS Report (New) |
| Business purpose | To monitor average service-order-speed behaviour at store level for operational review of order preparation performance. |
| Primary users | Operations users, with secondary management and Finance use where required for service-performance review. |
| Parameters | Start date and end date (required); optional outlet scope; optional sales status and sales type filters; optional single-rule advanced search on selected sales-item identifiers. |
| Output summary | Returns store-level rows containing order count and preparation-duration measures for the selected reporting scope. |
| Data scope | Replicated KDS-related records, sales records, sales item records, item reference data where required by advanced search, and outlet reference data. |
| Key business rules | Preparation duration is derived from KDS order and collection timestamps; item-level timing rows are first grouped to order level and then rolled up to store level using the validated weighting logic; unsupported portal-option filters remain excluded from active analytical use. |
| Validation approach | Report output was validated through parity comparison against vendor portal output for the retained report scope. |
| Final status | Implemented and validated. |

### R17: MB Cash Voucher (with Barcode) Redemption Report

*Table A.19: Detailed specification for R17*

| Field | Description |
| --- | --- |
| Report name | MB Cash Voucher (with Barcode) Redemption Report |
| Business purpose | To track redemption of barcode-based cash vouchers for voucher control and reconciliation. |
| Primary users | Finance and Operations users. |
| Parameters | Start date and end date (required); optional outlet scope; optional voucher-variant inclusion logic where required by the report behaviour. |
| Output summary | Returns voucher redemption rows including redemption date, outlet, voucher identifier, voucher category, linked sales reference, and reconciliation-related totals or counts. |
| Data scope | Replicated voucher-related payment or redemption records, linked sales records, and outlet reference data. |
| Key business rules | Voucher identifiers and categories are normalised to match portal grouping; duplicated joins are suppressed so that redemption rows remain parity-aligned. |
| Validation approach | Report output was validated through parity comparison against vendor portal exports using matched date ranges and outlet scopes. |
| Final status | Implemented and validated. |

### R18: MB Staff E - Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report

*Table A.20: Detailed specification for R18*

| Field | Description |
| --- | --- |
| Report name | MB Staff E - Voucher RM 20 & MB CASH VOUCHER RM10 (with Barcode) Redemption Report |
| Business purpose | To monitor redemption of staff e-vouchers and selected barcode cash vouchers for controlled checking and reconciliation. |
| Primary users | Finance and Operations users, with secondary administrative interest where staff-benefit monitoring is required. |
| Parameters | Start date and end date (required); optional outlet scope; optional voucher-variant inclusion logic where required by the report behaviour. |
| Output summary | Returns voucher redemption rows including redemption date, outlet, voucher identifier, voucher type, linked sales reference, and reconciliation-related totals or counts. |
| Data scope | Replicated voucher-related payment or redemption records, linked sales records, and outlet reference data. |
| Key business rules | Staff and cash voucher variants must be grouped consistently with portal behaviour; duplicated rows are suppressed and legacy variations are normalised into the retained voucher categories. |
| Validation approach | Report output was validated through parity comparison against vendor portal exports for matched scopes. |
| Final status | Implemented and validated. |

### R19: Product Mix with modifier without ETL

*Table A.21: Detailed specification for R19*

| Field | Description |
| --- | --- |
| Report name | Product Mix with modifier without ETL |
| Business purpose | To extend product-mix analysis with modifier-level detail for checking sales composition and profit-related behaviour at a more detailed reporting level. |
| Primary users | Finance and Operations users. |
| Parameters | Start date and end date (required); expected outlet scope and item-related optional filters consistent with modifier-level product reporting. |
| Output summary | Intended to return modifier-aware product-mix rows with quantity, value, and profit-related measures. |
| Data scope | Replicated sales records, sales item records, modifier-related transactional fields, item master data, and supporting reference data needed for modifier-level grouping. |
| Key business rules | The report depends on correct modifier-level grouping and profit-related derivation consistent with portal behaviour. |
| Validation approach | Reverse engineering and parity validation were performed against vendor portal behaviour, but the remaining profit-related logic could not be isolated conclusively within the project boundary. |
| Final status | Not fully closed. |

## A.4 Detailed Specifications for Additional Customised Reports

### C01: Roblox Free Chicken Burger Combo Sales

*Table A.22: Detailed specification for C01*

| Field | Description |
| --- | --- |
| Report name | Roblox Free Chicken Burger Combo Sales |
| Business purpose | To track a campaign-specific promotional sales scenario requested by the company for monitoring and follow-up. |
| Primary users | Finance, Operations, and campaign-monitoring users. |
| Parameters | Start date and end date (required); optional outlet scope; optional campaign-related or transaction filters where applicable to the implemented report view. |
| Output summary | Returns campaign-related sales rows and totals aligned to the required promotional sales scenario. |
| Data scope | Replicated sales records, sales item records, and supporting item and outlet reference data required for the campaign-specific grouping. |
| Key business rules | Campaign scope is isolated through report-specific selection logic while reusing the shared platform pattern of parameter handling, tabular output, and export-oriented delivery. |
| Validation approach | Report output was validated through comparison against the required business expectations and retained portal-aligned checking workflow for the customised scope. |
| Final status | Implemented and validated. |

### C02: Voucher Campaign & Reward Sales

*Table A.23: Detailed specification for C02*

| Field | Description |
| --- | --- |
| Report name | Voucher Campaign & Reward Sales |
| Business purpose | To provide campaign- and reward-related voucher sales visibility requested by the company beyond the formal report scope. |
| Primary users | Finance, Operations, and campaign-monitoring users. |
| Parameters | Start date and end date (required); optional outlet scope; optional campaign or voucher-related filters where applicable. |
| Output summary | Returns voucher campaign and reward sales rows and totals aligned to the required customised reporting view. |
| Data scope | Replicated sales records, payment or voucher-related records, and supporting outlet and reference data required for campaign grouping. |
| Key business rules | Campaign and reward classification logic is applied within the shared semantic layer while preserving the same parameter, export, and tabular reporting pattern used across the main platform. |
| Validation approach | Report output was validated through comparison against required business expectations and retained checking artefacts for the customised reporting scope. |
| Final status | Implemented and validated. |

### C03: Promotion Item Additional Purchase Report

*Table A.24: Detailed specification for C03*

| Field | Description |
| --- | --- |
| Report name | Promotion Item Additional Purchase Report |
| Business purpose | To analyse additional-purchase behaviour associated with selected promotion items requested by the company. |
| Primary users | Finance, Operations, and business users monitoring promotional sales behaviour. |
| Parameters | Start date and end date (required); optional outlet scope; optional promotion-item or transaction filters where applicable to the implemented view. |
| Output summary | Returns rows and totals showing additional-purchase behaviour linked to the defined promotion-item scope. |
| Data scope | Replicated sales records, sales item records, and supporting item and outlet reference data needed for promotion-item grouping and comparison. |
| Key business rules | The report uses report-specific promotion-item selection logic while retaining the same shared platform pattern of parameter-driven retrieval, tabular results, and export-ready output. |
| Validation approach | Report output was validated through comparison against required business expectations and retained checking artefacts for the customised scope. |
| Final status | Implemented and validated. |
