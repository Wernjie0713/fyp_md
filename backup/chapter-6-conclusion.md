# Conclusion

## 6.1 Introduction

This chapter concludes the final report for the Marrybrown Sales and Payment Analytics Platform. Whereas Chapter 5 focused on the implemented development and testing work, this chapter interprets the overall project outcome through the platform's contribution, achievement, remaining constraints, and future suggestions. The discussion therefore moves from implementation detail to final evaluation of what the project delivered within its defined academic and business boundary.

The chapter does not repeat the detailed report-construction, ETL, or testing procedures already documented earlier. Instead, it summarises the practical significance of the completed platform, explains the main limitations that remained at project closure, and identifies reasonable directions for future improvement if the platform is extended further in the company environment.

## 6.2 System Contribution/Achievement

The project successfully delivered the Marrybrown Sales and Payment Analytics Platform as a real internal reporting system deployed in a company environment rather than as a purely academic prototype. Its first major contribution was the establishment of a company-controlled reporting architecture that reduced operational dependence on the vendor portal for selected sales and payment reporting needs. By replicating selected source-system data into a Microsoft SQL Server reporting database, reconstructing report logic in a FastAPI semantic/API layer, and providing authenticated access through a React-based portal, the project created a practical internal reporting path that could be managed and extended within Marrybrown's own operating context.

The second major contribution was report reconstruction with evidence-based validation. The project did not treat report development as simple page creation. Instead, it involved tracing source data, rebuilding vendor-aligned logic, testing parameter behaviour, and validating outputs against vendor-visible results. This gave the delivered platform traceable reporting behaviour for the retained report surface and demonstrated that operational reporting continuity can be achieved through disciplined reverse engineering and parity validation rather than through unsupported approximation.

The third contribution was operational usability. The implemented system provided more than report retrieval alone. Internal users were supported through report search, filtering, tabular review, grouped output, and export functions, while authorised administrative users were supported through user management, portal-triggered sync, automation-management visibility, and data-quality checking workflows. These features made the platform usable as an internal reporting environment rather than as a set of isolated backend endpoints or static output pages.

An additional achievement was architectural extensibility. Beyond the formal implementation scope, the project also demonstrated that the shared reporting architecture could support further company-requested report families without requiring a separate system model. This indicates that the platform functioned not only as a continuity solution for existing report needs, but also as a reusable internal base for future reporting extensions.

Taken together, these achievements show that the project delivered a validated internal reporting platform with practical business value. It addressed the company's reporting continuity problem, produced a company-usable deployed system, and documented a repeatable approach for report reconstruction, operational control, and controlled extension.

## 6.3 System Constraint

Despite the achieved outcome, several important constraints remained at project closure. The first constraint was that report parity depended not only on application logic, but also on the completeness and consistency of the replicated reporting data. In practice, some mismatches arose from historical incompleteness, late source updates, or replica-state conditions rather than from backend logic alone. This meant that accurate report delivery required both valid query logic and trustworthy underlying replicated data.

The second constraint was the black-box nature of the vendor reporting behaviour. The project reconstructed report outputs through observable behaviour, available datasets, and iterative validation, but the full underlying logic of the vendor portal was not directly exposed for all report areas. As a result, reverse engineering was necessarily evidence-led and iterative rather than fully specification-driven. This limitation increased the time required for validation and made some report areas more difficult to conclude with certainty.

The third constraint was that not every formal-scope report area was fully closed within the project boundary. Product Mix Report, Discount Remark Report, and Product Mix with modifier without ETL remained unresolved after reverse engineering and parity validation because the remaining profit-related logic could not be isolated conclusively. These unresolved areas should therefore be understood as genuine logic-boundary constraints rather than as simple page-development omissions.

Another constraint concerned performance variation across report families. Query tuning and supporting warehouse maintenance improved the practical response time of several reports, and the system reached an operationally usable level for the retained report surface. However, some broader all-store report windows still remained relatively heavy compared with narrower scopes. This means that, although the platform became usable and materially improved in several paths, performance optimisation remained dependent on report shape, replica condition, and warehouse-side factors.

A final constraint is that the delivered platform should not be interpreted as a complete functional replacement for every capability of the vendor portal. The project was scoped around selected sales and payment reporting requirements requested by the company. Accordingly, the platform should be understood as a validated internal reporting solution for the agreed report surface, not as an exhaustive reimplementation of the external vendor ecosystem.

## 6.4 Future Suggestion

Several future suggestions follow naturally from the completed implementation. The first is continued investigation of unresolved profit-related report logic, especially in the product-mix-related report areas. If additional observable business evidence, validated reference behaviour, or clearer supporting data becomes available, these report modules may be revisited for further reconstruction and final parity validation.

The second suggestion is continued improvement of historical completeness and replicated-data reliability. Since report trustworthiness depends partly on source-to-replica consistency, future work may focus on stronger historical validation coverage, more efficient repair handling for incomplete windows, and continued operational refinement of sync and data-quality workflows.

The third suggestion is selective performance refinement for heavier report scopes. Although the implemented platform reached an operationally acceptable level for current use, some broad all-store report windows remained comparatively heavy. Future improvement may therefore focus on deeper warehouse-side tuning, query-plan refinement, and scope-specific optimisation where repeated operational demand justifies further effort.

The fourth suggestion is controlled expansion of validated report coverage. The established architecture already demonstrated that additional company-requested reports could be incorporated into the same platform model. Future work may therefore extend the platform by adding new report modules, provided that the same discipline of source tracing, logic reconstruction, and parity-oriented validation is maintained.

The fifth suggestion is continued enhancement of administrative monitoring and operational support. Over time, if internal adoption increases, the platform could benefit from richer operational visibility for replication health, automation status, and report-readiness monitoring, so long as these additions remain aligned with the platform's company-controlled reporting purpose.

These future suggestions should not be read as evidence that the delivered platform is incomplete in its core purpose. Rather, they reflect the natural next steps for a system that has already reached a usable and validated internal reporting state and now provides a foundation for further controlled development.

## 6.5 Summary

This chapter concluded the final report by evaluating the Marrybrown Sales and Payment Analytics Platform in terms of its contribution, achievement, remaining constraints, and future suggestions. The project successfully delivered a deployed internal reporting platform that reconstructed and validated selected vendor-aligned sales and payment reports, supported operational reporting access through a web portal, and provided controlled administrative functions for replication and report-readiness management.

At the same time, the project also documented real constraints, especially those related to replicated-data trustworthiness, black-box vendor logic, unresolved profit-related report behaviour, and uneven performance across some broad report scopes. These limitations do not negate the platform's contribution; rather, they define the realistic boundary within which the delivered system should be understood.

Overall, the project achieved its core purpose as an enterprise reporting continuity and reconstruction effort conducted in a real company environment. It delivered a company-usable internal reporting platform, validated a substantial retained reporting surface, and established a practical foundation for further extension and refinement where future business needs require it.
