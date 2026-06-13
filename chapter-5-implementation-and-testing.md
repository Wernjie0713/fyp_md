# Implementation And Testing

## Introduction

This chapter presents the implementation and testing of the Marrybrown Sales and Payment Analytics Platform. Whereas Chapter 4 described the analysis and design of the platform, this chapter records how the implemented platform was developed across the reporting database and ETL layer, the FastAPI semantic/API layer, and the React-based portal layer. It also documents the validation and testing activities used to confirm report accuracy, user-facing behaviour, and internal processing reliability.

The chapter focuses on the completed implementation rather than on design intent alone. Accordingly, attention is given to the reporting-database replication process, report reconstruction workflow, frontend report delivery, administrative functions, report implementation coverage, and the testing approach used to evaluate the retained report set and additional customised reports. To keep the chapter academically appropriate and public-safe, implementation details are presented at technical level without exposing credentials, secret configurations, or operationally sensitive access instructions.

## System Development

### Development Overview

The implemented platform was developed as a multi-layer internal reporting system intended to reduce operational dependence on a vendor-managed reporting portal while preserving report traceability and validation discipline. The completed implementation consists of three primary layers. First, selected source-system data were replicated into a company-managed Microsoft SQL Server reporting database through controlled ETL processes. Second, report logic was reconstructed in a FastAPI backend that acted as a semantic/API layer over the replicated data. Third, a React-based reporting portal was implemented to provide authenticated report access, filtering, export functions, and selected administrative tools.

The development process followed the iterative and incremental methodology described in Chapter 3. This was necessary because several report modules could not be treated as straightforward query transcription tasks. In practice, report development involved repeated cycles of source-data tracing, semantic rule reconstruction, mismatch investigation, validation against vendor outputs, and refinement of the reporting workflow in both backend and frontend layers.

### Reporting Database and ETL Development

The reporting-database implementation centred on a company-managed Microsoft SQL Server environment that preserved selected source tables through a 1:1 replication strategy. This replica design was chosen to retain source fidelity for parity validation and reconciliation, while allowing report logic to be rebuilt independently of the external portal. Rather than flattening all logic into the database layer, the implementation preserved transactional and reference data close to source structure and left report-specific grouping, derivation, and presentation logic to the semantic/API layer.

The ETL implementation did not rely on a single loading path. Instead, it evolved into a controlled replication model with separate but coordinated operational modes. Manual utilities were retained for broad baseline loading, historical backfill, and targeted recovery work, especially for dated tables that required replay across defined time windows. In parallel, a staged daily ETL orchestrator was implemented for routine dated-table maintenance and reference-data refreshes. This staged design used boundary-based replacement logic so that repeated execution of the same reporting window could safely refresh the replica without introducing duplicate or drifting rows.

In the final implemented state, the ETL layer also supported portal-triggered manual sync requests and scheduled automation. Portal-triggered sync allowed authorised administrators to request dated-table or reference-table refreshes from the portal without executing ETL commands directly on the database host. Scheduled ETL automation was also implemented as an operational feature for unattended daily dated refreshes and nightly retained-reference refreshes, with administration performed through the platform's automation-management workflow. This arrangement gave the platform both controlled manual recovery capability and operational automation capability, without requiring ordinary report users to interact with the ETL layer directly.

### Backend API Development

The backend was implemented using FastAPI and functioned as the semantic/API layer of the platform. Its principal role was to reconstruct vendor-aligned report logic over the replicated database and expose the resulting report outputs through stable, parameter-driven endpoints. This design avoided direct frontend dependence on raw database structures and made it possible to keep report logic versioned and maintainable within the backend layer.

Backend development involved several recurring tasks across report modules. These included request-parameter definition, outlet and date-range filtering, shared handling of sales-status or payment-status filters where relevant, structured row output, and export-oriented response shaping. Reports that required grouped behaviour in the portal also needed backend outputs that could be normalised reliably for frontend grouping, subtotal rendering, advanced search, and export generation. In this way, the backend was not merely a database wrapper; it became the primary location where report-specific business rules, derived fields, and stable response contracts were implemented.

The backend layer also supported non-report operational functions required by the completed system. These included authentication, admin-managed user functions, portal-triggered sync control, automation-management support, and quality-check workflows linked to selected sync operations. Although these supporting features were not the central academic contribution of the project, they were necessary to make the implemented platform operationally usable in a real company environment.

### Frontend Portal Development

The frontend portal was implemented using React and was designed to provide authenticated internal access to reports through a workflow-oriented rather than dashboard-oriented interface. The implemented report experience followed a common pattern: users sign in, access the report catalogue, select a report, define parameters, query the report, review the resulting table and totals, and export the output where needed. This structure was intentionally aligned with the practical behaviour expected by Finance and Operations users, especially for reconciliation and operational checking tasks.

Frontend development relied on shared report architecture rather than isolated page-specific implementations. A report registry, shared page shell, shared filters panel, grouped-table component, export toolbar, and supporting hooks were reused across report modules. This reduced duplication and made it feasible to add new formal-scope reports and additional customised reports through a consistent frontend pattern. The report-list view, report-query view, grouped-table behaviour, advanced search support, and export actions were therefore developed as reusable platform capabilities rather than as unrelated page fragments.

This user-facing reporting pattern is reflected in Figure 5.1 through a sanitised composite view that combines the Reports Hub with a representative report-query page. The figure represents the actual portal flow retained in the implementation: users begin from the catalogue of available reports, move into the selected module to define the required parameters, and then review grouped output through the shared query interface. Read in this way, the figure supports the main implementation point of this subsection, namely that the portal was developed as a consistent report-execution surface rather than as a collection of unrelated dashboard screens.

![Figure 5.1: Reports Hub and representative report-query interface](#)

*Figure 5.1: Reports Hub and representative report-query interface*

The implemented portal also included role-restricted supporting features beyond ordinary report retrieval. Admin-only views were developed for data sync, automation control, and user management. These pages extended the platform beyond passive report viewing and reflected the fact that the delivered system functioned as an internal reporting platform with controlled operational administration, not only as a collection of static report pages.

### Administrative and Operational Functions

Several administrative and operational functions were implemented to make the platform sustainable for real use after report delivery. The first was admin-managed user control under the authentication model, where normal user access to report pages was separated from admin-only access to management functions. The second was the portal-triggered manual sync workflow, through which administrators could request sales-window or reference refreshes and review request history and progress. The third was automation management, where authorised administrators could review scheduled-task status and request enable, disable, or schedule-change actions for routine ETL automation.

An additional operational enhancement was the data-quality checking layer for portal-triggered replication. This feature allowed administrators to review source-to-replica quality outcomes for selected reporting windows, perform re-check actions, and trigger repair-oriented follow-up where required. This function was relevant academically because it showed that report continuity depended not only on endpoint implementation, but also on the trustworthiness of the replicated data used by those endpoints.

The administrative layer described above was implemented as three coordinated portal surfaces, each tied to a distinct governance responsibility. Figure 5.2 corresponds to user administration, where authorised staff review accounts and maintain role-controlled access. Figure 5.3 corresponds to data-sync administration, where replication requests, execution histories, and related follow-up actions are managed from the portal. Figure 5.4 corresponds to automation administration, where scheduled ETL activity is reviewed and change requests are handled under controlled access. Considered together, these figures reinforce that the delivered platform supported governed internal operations in addition to ordinary report retrieval.

![Figure 5.2: User Management page](#)

*Figure 5.2: User Management page*

![Figure 5.3: Data Sync page](#)

*Figure 5.3: Data Sync page*

![Figure 5.4: Automation Control page](#)

*Figure 5.4: Automation Control page*

### Report Implementation Coverage

Within the formal implementation and business scope, the platform was developed to support 19 sales and payment reports. Of these, 16 reports were successfully implemented and retained in the delivered active reporting surface. Three reports were not fully closed within the project boundary and are documented as limitations rather than omitted outcomes. In addition to the formal 19-report scope, three additional customised reports were also developed based on company requests during implementation.

The retained formal-scope reports covered several reporting groups, including sales and exception control, payment and voucher reconciliation, delivery and ordering channels, and product-, stock-, or cost-related operational analysis. The additional customised reports extended the implemented platform beyond the original formal scope and demonstrated that the shared ETL, backend, and portal architecture could support company-requested report families without requiring a separate system. Detailed per-report specifications, statuses, and classifications are documented in Appendix A.

The three formal-scope reports that were not fully closed were Product Mix Report, Discount Remark Report, and Product Mix with modifier without ETL. These were not left unresolved due to a simple lack of page development. Rather, they remained unresolved after reverse engineering and parity validation because the remaining logic required for full closure, especially profit-related behaviour in the product-mix area, could not be isolated conclusively within the available project boundary.

## Coding of the system's main functions/Process

### Data Replication and Refresh Process

The main data-process function of the platform was the movement of selected source data into the reporting database in a form suitable for report reconstruction. This process followed a staged boundary-based refresh pattern. For dated-table maintenance, the ETL process identified a defined reporting window, extracted source rows for that window, staged the refreshed data, replaced the corresponding live rows in the reporting database, and then recorded run metadata and progress information. This approach ensured that rerunning the same reporting window remained deterministic and that failed or incomplete windows could be retried without depending on ad hoc manual cleanup.

This process was important because reporting mismatches were not caused only by query logic. In several cases, mismatches were associated with late source edits, historical incompleteness, or replica-state inconsistencies. The implemented refresh model therefore had to support not only normal data movement but also controlled replays and focused correction work. For broad historical loading, manual utilities were used for baseline and backfill operations. For routine maintenance, scheduled daily ETL and portal-triggered sync requests used the staged orchestrator path. This split between baseline loading and operational refresh was necessary to balance reliability, recoverability, and maintainability.

The implemented process also included quality-oriented follow-up for selected portal-triggered sync windows. After a successful sales-window refresh, a source-to-replica quality check could be launched for the same window. Where mismatches were identified, re-check or repair-oriented follow-up could be requested. This meant that the data process for the platform was not limited to extraction and loading alone; it also included mechanisms for checking whether the reporting replica remained trustworthy enough for subsequent report reconstruction.

This two-path refresh model is summarised in Figures 5.5 and 5.6. Figure 5.5 represents the retained reference-table refresh path, in which a full refresh request is initiated from the portal and then monitored through staged execution and per-table progress review. Figure 5.6 represents the dated sales-data refresh path, where a bounded sync request moves through queued execution, post-run data-quality review, and repair-oriented follow-up for the selected reporting window. Presented in this order, the figures support the subsection's argument that portal-triggered replication was implemented as a controlled and auditable administrative process rather than as an opaque background task.

![Figure 5.5: Portal-triggered reference-table refresh and execution tracking](#)

*Figure 5.5: Portal-triggered reference-table refresh and execution tracking*

![Figure 5.6: Portal-triggered dated sales-data replication and data-quality review](#)

*Figure 5.6: Portal-triggered dated sales-data replication and data-quality review*

### Report Reconstruction Process

The main report-building process began with identifying the report behaviour expected from the vendor portal, including required parameters, visible output fields, grouping behaviour, totals, and export structure. From that baseline, the contributing datasets were traced in the replicated database and the required relationships were reconstructed at query level. This process was repeated across reports, even though the exact grouping and metric logic differed from one report family to another.

Once the contributing data paths were understood, the report logic was implemented in the FastAPI semantic/API layer. This typically included parameter validation, date-window scoping, outlet filtering, sales-status or payment-status handling where relevant, grouping and aggregation rules, and output formatting suitable for frontend rendering and export. The portal did not simply render raw SQL output. Instead, the backend response contracts were shaped to support tabular display, grouped subtotal behaviour, advanced search, and export actions in a stable and repeatable way.

Although each report had unique business rules, the implemented process remained consistent at high level. All report modules followed the same core pattern of source tracing, semantic reconstruction, parameter-driven querying, structured output shaping, and parity-oriented validation. This shared process allowed the project to scale from the retained formal report set to additional customised reports without abandoning the same platform architecture.

This reconstruction pattern is summarised in Figure 5.7. The figure represents the general backend process through which a report request moves from user parameter selection to semantic validation, replicated-data retrieval, dataset joining, grouping and derived-field handling, and final response shaping for portal display and export. Although the detailed query logic differs across report modules, the same high-level reconstruction sequence was retained throughout the implementation. This consistency was important because it allowed the platform to support multiple formal-scope and customised reports within the same semantic/API architecture while preserving traceability for parity validation.

![Figure 5.7: Sanitised illustration of report reconstruction logic](#)

*Figure 5.7: Sanitised illustration of report reconstruction logic*

### Selected Implementation Example: Payment Type (All Payment)

The Payment Type (All Payment) report is a suitable formal-scope example because it was operationally important, highly sensitive to row-level grouping behaviour, and representative of the reverse-engineering work required by the project. The purpose of this report was to provide a detailed breakdown of payment collections by store, order source, payment method, device, card type, and reference. The challenge was not merely to total payment rows, but to reconstruct the same grouping and display behaviour expected from the vendor portal with exactness sufficient for reconciliation work.

Implementation began by identifying the required payment-, sales-, and location-level source relationships in the replicated database. The main data sources were payment rows, sales status and order-source fields, and location-name mappings. Parameter handling was then defined around the selected date range, optional outlet scope, sales-status filtering, and payment-status behaviour. Because the report was intended for parity-sensitive operational use, the backend response also had to preserve a stable flat-row structure that could later support frontend grouped rendering and export processing.

The more difficult part of the implementation lay in the reference-grouping behaviour. Payment references could appear in multiple case variants, while portal output would still present them under a single preferred display value. Additional care was also required for payment-method categorisation, exclusion of return-sales behaviour, handling of zero-time anomalies, and consistent inclusion of payment rows in the correct collection totals. These issues made the report representative of the wider project challenge: the output could not be matched reliably through naive grouping alone, and several rounds of reverse engineering and refinement were required before parity could be accepted.

### Selected Implementation Example: Voucher Campaign & Reward Sales Report

The Voucher Campaign & Reward Sales Report is a suitable customised-report example because it demonstrates that the implemented platform supported not only vendor-aligned report reconstruction, but also additional company-requested analysis built on the same architecture. This report was developed as a dynamic report family for eligible voucher campaigns and points rewards, while keeping the earlier Roblox-specific report intact as a separate implemented report.

The implementation process began with investigation of how voucher campaign and reward data could be represented reliably using the replicated data model. Rather than anchoring the report on a fixed voucher name, the implemented design used a selectable redemption-type identity so that the report could be applied to multiple campaign or reward families. The backend then reconstructed sale-level voucher scope, basket rows, derived bundle grouping, and additional-purchase indicators. This required not only data retrieval, but also interpretation of basket structure so that the final output could distinguish between the target bundle itself, other vouchers in the same sale, and additional paid items.

On the portal side, the customised report reused the shared report architecture but introduced a selector-driven reporting flow before ordinary date and outlet filtering. This illustrates a key implementation result of the project: once the shared ETL, semantic/API, and portal architecture was stable, it became feasible to add company-requested customised reports without changing the overall platform model. The report therefore serves as evidence that the delivered system functioned as an extensible internal reporting platform rather than only as a one-time replication exercise.

### Query Performance Observation

During implementation, selected report modules also underwent query-shape refinement and warehouse-side tuning to improve practical response time without changing validated business output. This work was documented through before-and-after timing checks on representative report scopes and was supported by later portal-side timing observations under real usage-style parameter sets.

One of the clearest examples was the Payment Type (All Payment) report, where the implementation logs recorded both application-side query-path refinement and later warehouse-side index recovery.

Table 5.1 summarises the strongest recorded timing observations for the Payment Type (All Payment) report.

| Tested scope | Before optimisation | After optimisation | Observation |
|---|---:|---:|---|
| Single-store, single-day, 4-row case | approximately 63s | approximately 3.3s | substantial reduction after backend query-path refinement |
| Single-store, single-day, 608-row case | timed out beyond 120s | approximately 8.9s | timeout path removed after backend query-path refinement |
| Busy single-store, one-day sample after index recovery | not restated in the later log pass | approximately 1.1s | strong practical result after rebuilding disabled sales indexes |
| All-store, one-day sample after index recovery | not restated in the later log pass | approximately 12.2s | acceptable all-store one-day timing after warehouse-side tuning |

*Table 5.1: Recorded timing observations for Payment Type (All Payment)*

The Payment Type observations indicate that performance improvement was achieved not only through report-query restructuring, but also through supporting warehouse maintenance and index recovery work.

Additional implementation logs recorded similar timing checks for other report families. Table 5.2 presents a compact summary of selected supporting observations.

| Report | Tested scope | Recorded timing change or practical timing | Interpretation |
|---|---|---|---|
| Mobile Ordering Sales | All stores, 2025-01-01 to 2025-01-05 | approximately 4.83s to 4.38s | modest improvement after query-shape refinement |
| Delivery-FoodPanda,Grabfood,ShopeeFood | All stores, 2025-01-01 to 2025-01-05 | approximately 29.63s to 27.39s; later portal-side timing almost 20s | moderate backend improvement with usable portal-side outcome |
| Foodpanda Discount | All stores, 2025-01-01 to 2025-01-05 | approximately 37.91s to 25.90s; later portal-side timing around 40+s | broad-window improvement, though still relatively heavy in portal use |
| Sales Return Report | All stores, 2025-01-01 to 2025-01-05 | approximately 5.53s to 6.04s; later portal-side timing around 10s | timing was recorded and operationally acceptable, but not a strong improvement case |
| Sales Cancelled Report | All stores, 2025-01-01 to 2025-01-05 | approximately 9.86s to 10.56s; later portal-side timing almost 20+s | timing was recorded and operationally acceptable, but not a strong improvement case |
| Deleted Items | All stores, 2025-01-01 to 2025-01-05 | approximately 8.21s to 7.41s; later portal-side timing almost 8s | small but measurable improvement with acceptable practical timing |

*Table 5.2: Selected supporting timing observations across optimised report modules*

Taken together, the recorded outcomes show that some report paths improved materially, while others improved more modestly or remained relatively heavy for broad all-store reporting windows. Practical portal-side timing checks were also recorded after optimisation to ensure that the observed improvements remained meaningful from the user perspective rather than only at backend execution level.

These observations should be interpreted as implementation evidence of operational tuning rather than as a formal benchmark against the vendor portal. Within the project boundary, the main purpose of this work was to reduce timeout risk, improve response consistency, and keep validated report modules usable in the internal reporting workflow.

### Report Accuracy Validation

The strongest testing evidence for the project was the report-accuracy validation process. This process was distinct from UAT because its purpose was not merely to confirm that a page loaded or exported correctly, but to confirm that the rebuilt report output was sufficiently aligned with the vendor portal under the same report conditions. The general validation approach was to run the platform report and the vendor portal report using the same date range, outlet scope, and other relevant filters, then compare row-level output, grouping behaviour, totals, subtotals, and exported results.

For the Payment Type (All Payment) report, this validation process was especially important because the report was sensitive to grouping precision at payment-reference level. The validation work therefore involved repeated comparison between platform output and vendor export output, investigation of mismatched rows or totals, and refinement of the reconstructed query logic until acceptable parity was achieved. Where anomalies remained, the investigation distinguished between logic faults and data-quality issues in the replica state, so that the report logic itself was not altered incorrectly to compensate for replica-specific data problems.

The same validation pattern was applied across the wider retained report surface. For each report module, parity validation used traceable filter conditions and visible output comparison rather than unsupported assumptions about hidden vendor logic. This validation discipline was a defining characteristic of the project because it anchored report acceptance to evidence rather than to superficial interface completion. The detailed validation evidence is represented by the `PV` test cases shown in Figures 5.8 to 5.15.

![Figure 5.8: PV01 Payment Type (All Payment) report accuracy validation](#)

*Figure 5.8: PV01 Payment Type (All Payment) report accuracy validation*

![Figure 5.9: PV02 Sales Return Report accuracy validation](#)

*Figure 5.9: PV02 Sales Return Report accuracy validation*

![Figure 5.10: PV03 Sales Cancelled Report accuracy validation](#)

*Figure 5.10: PV03 Sales Cancelled Report accuracy validation*

![Figure 5.11: PV04 Sale Delivery Ex Tax report accuracy validation](#)

*Figure 5.11: PV04 Sale Delivery Ex Tax report accuracy validation*

![Figure 5.12: PV05 MB Cash Voucher redemption accuracy validation](#)

*Figure 5.12: PV05 MB Cash Voucher redemption accuracy validation*

![Figure 5.13: PV06 Voucher Campaign and Reward Sales accuracy validation](#)

*Figure 5.13: PV06 Voucher Campaign and Reward Sales accuracy validation*

![Figure 5.14: PV07 Portal-triggered data quality validation](#)

*Figure 5.14: PV07 Portal-triggered data quality validation*

![Figure 5.15: PV08 Product Mix and discount profit logic validation boundary](#)

*Figure 5.15: PV08 Product Mix and discount profit logic validation boundary*

### Black-Box Testing and User Acceptance Testing

Black-box testing and User Acceptance Testing (UAT) were treated together because, in the context of this project, both evaluated the system from the user-facing perspective rather than from the internal code path. These tests focused on whether users could sign in, access reports, enter parameters, retrieve outputs, inspect totals, export data, and use role-restricted administrative functions appropriately. The intent was to verify that the implemented platform supported realistic operational workflows rather than merely exposing technically correct endpoints.

The test scenarios were structured as test cases using the `TC` prefix, such as `TC01`, `TC02`, and subsequent cases. Core user-facing scenarios included authentication, report-catalogue access, report retrieval with valid filters, export behaviour, access to customised report modules, manual sync submission, data-quality follow-up visibility, automation-control access, and role-restricted administrative behaviour. This structure provided a clear and traceable record of functional acceptance across the implemented user workflows.

The UAT and black-box testing outcomes were intended to show that the implemented platform could be used coherently by both ordinary reporting users and authorised administrative users. This was especially relevant for the data-sync and automation functions, because these features extended the platform beyond simple report viewing and into controlled reporting operations. By structuring these tests around user-observable behaviour, the testing section complements the report-accuracy validation process rather than duplicating it.

The detailed UAT and black-box test cases are shown in Figures 5.16 to 5.31.

![Figure 5.16: TC01 user login with valid credentials](#)

*Figure 5.16: TC01 user login with valid credentials*

![Figure 5.17: TC02 Reports Hub access](#)

*Figure 5.17: TC02 Reports Hub access*

![Figure 5.18: TC03 report parameter loading](#)

*Figure 5.18: TC03 report parameter loading*

![Figure 5.19: TC04 Payment Type report query](#)

*Figure 5.19: TC04 Payment Type report query*

![Figure 5.20: TC05 report totals review](#)

*Figure 5.20: TC05 report totals review*

![Figure 5.21: TC06 report output export](#)

*Figure 5.21: TC06 report output export*

![Figure 5.22: TC07 advanced search behaviour](#)

*Figure 5.22: TC07 advanced search behaviour*

![Figure 5.23: TC08 Sales Return Report query](#)

*Figure 5.23: TC08 Sales Return Report query*

![Figure 5.24: TC09 customised report query](#)

*Figure 5.24: TC09 customised report query*

![Figure 5.25: TC10 normal-user admin restriction](#)

*Figure 5.25: TC10 normal-user admin restriction*

![Figure 5.26: TC11 admin Data Sync access](#)

*Figure 5.26: TC11 admin Data Sync access*

![Figure 5.27: TC12 manual sync request submission](#)

*Figure 5.27: TC12 manual sync request submission*

![Figure 5.28: TC13 sync progress review](#)

*Figure 5.28: TC13 sync progress review*

![Figure 5.29: TC14 data-quality re-check workflow](#)

*Figure 5.29: TC14 data-quality re-check workflow*

![Figure 5.30: TC15 Automation Control review](#)

*Figure 5.30: TC15 Automation Control review*

![Figure 5.31: TC16 User Management workflow](#)

*Figure 5.31: TC16 User Management workflow*

### White-Box Testing

White-box testing was used to evaluate selected internal processing logic that could not be assessed fully through user-facing behaviour alone. In this project, white-box testing did not aim to provide exhaustive code-coverage measurement. Instead, it focused on the internal logic that had direct impact on report trustworthiness and operational safety, such as request-parameter validation, boundary-based refresh handling, source-to-replica quality-check flow, grouping and aggregation logic in report reconstruction, export-structure consistency, and role-restricted access handling.

This form of testing was relevant because a report can appear correct from the interface while still containing internal weaknesses in parameter interpretation, refresh-window replacement logic, or grouped output construction. By checking selected internal logic paths explicitly, the implementation could be reviewed not only at output level but also at process level. In academic terms, this strengthened the credibility of the completed system because it demonstrated that testing attention was given to both visible behaviour and the underlying logic that produced that behaviour. The detailed white-box test cases are shown in Figures 5.32 to 5.40.

![Figure 5.32: WB01 API parameter validation](#)

*Figure 5.32: WB01 API parameter validation*

![Figure 5.33: WB02 Payment Type grouping logic](#)

*Figure 5.33: WB02 Payment Type grouping logic*

![Figure 5.34: WB03 boundary-based ETL rerun](#)

*Figure 5.34: WB03 boundary-based ETL rerun*

![Figure 5.35: WB04 staged refresh safety](#)

*Figure 5.35: WB04 staged refresh safety*

![Figure 5.36: WB05 source-to-replica data quality check](#)

*Figure 5.36: WB05 source-to-replica data quality check*

![Figure 5.37: WB06 quality repair request flow](#)

*Figure 5.37: WB06 quality repair request flow*

![Figure 5.38: WB07 report export mapping](#)

*Figure 5.38: WB07 report export mapping*

![Figure 5.39: WB08 role-based access restriction](#)

*Figure 5.39: WB08 role-based access restriction*

![Figure 5.40: WB09 automation-control request handling](#)

*Figure 5.40: WB09 automation-control request handling*

## Summary

This chapter documented the implementation and testing of the Marrybrown Sales and Payment Analytics Platform. It described the completed development of the reporting-database and ETL layer, the FastAPI semantic/API layer, the React portal layer, and the supporting administrative functions that made the platform operationally usable. It also outlined the formal report implementation coverage, the selected implementation examples, the recorded query-performance observation work, and the testing approach used to evaluate report accuracy, user-facing behaviour, and selected internal logic.

Taken together, the implementation and testing outcomes show that the project moved beyond conceptual design and delivered a real internal reporting platform with validated report modules, controlled refresh capability, role-based access, and company-requested extensions. The next chapter discusses the platform's contribution, remaining constraints, and future suggestions.
