# FYP Final Presentation Slide Plan

## Presentation Strategy

- Target length: 13 slides, around 22 to 28 minutes.
- Safe speaking mode: English slides, explain mainly in Mandarin, keep English technical terms such as `API`, `ETL`, `validation`, `replication`, and `React portal`.
- Slide rule: short bullets only. Do not put report-style paragraphs on slides.
- Main narrative: problem -> solution -> architecture -> implementation -> validation -> outcome -> limitation -> conclusion.

## Important Wording Rules

- Always use `Marrybrown Sales and Payment Analytics Platform` as the main system name.
- Do not frame the project mainly as a `redundancy` project.
- Do not mention the old proposal `15 reports` scope.
- Do not mention `Daily Sales Summary`.
- For unresolved reports, say `not fully closed` or `remaining profit logic could not be isolated conclusively`.
- Do not say the platform replaced every vendor function. Say it is a `validated internal reporting platform for the agreed report scope`.

## Recommended Deck Structure

### Slide 1 - Title

**Title**
Marrybrown Sales and Payment Analytics Platform

**Subtitle**
Final Year Project Final Presentation

**On-slide content**
- Name
- Matric number
- Supervisor
- Industry supervisor
- Date

**What to say**
- Introduce yourself.
- State that this is the final presentation for the implemented platform.
- Give one-line summary: the project built an internal reporting platform for selected sales and payment reports.

### Slide 2 - Presentation Overview

**Title**
Presentation Overview

**On-slide content**
- Problem background
- Project objectives
- System design and architecture
- Implementation and key functions
- Validation and testing
- Results, limitations, and conclusion

**What to say**
- This slide helps you control the flow.
- Keep it short, around 20 to 30 seconds.

### Slide 3 - Problem Background

**Title**
Vendor Dependency Created Reporting Risk

**On-slide content**
- Reporting depended on vendor portal
- Limited internal control over report logic
- Hard to investigate underlying transactions
- Downtime or delay affected reconciliation work

**Visual**
- Use the idea from `Figure 1.1`: old vendor-dependent path vs internal platform path

**What to say**
- Finance and Operations users depended on the vendor portal.
- When the portal was slow or unavailable, reporting work was affected.
- The company also had limited visibility into how the reports were generated.
- This created operational risk, especially during reconciliation and month-end closing.

### Slide 4 - Project Aim and Objectives

**Title**
The Project Goal Was Company-Controlled Reporting

**On-slide content**
- Replicate selected transactional data
- Reconstruct vendor-aligned report logic
- Deliver reports through an internal web portal
- Validate outputs against vendor results

**What to say**
- The aim was not only to build pages.
- The real goal was to reproduce selected reports using company-controlled data and logic.
- Validation was important because the output had to be trustworthy for operational use.

### Slide 5 - Proposed Solution

**Title**
The Solution Was an Internal Reporting Platform

**On-slide content**
- SQL Server reporting database
- FastAPI semantic/API layer
- React-based reporting portal
- Admin support for sync, automation, and data quality

**Visual**
- Use the idea from `Figure 4.3`

**What to say**
- Explain the platform in one simple flow:
- source data -> replicated database -> FastAPI backend -> React portal -> internal users
- Emphasise that the system gives the company a controlled reporting path.

### Slide 6 - Development Approach

**Title**
Iterative Development With Parity Validation

**On-slide content**
- Analyse vendor report behaviour
- Trace source data and business rules
- Implement report logic incrementally
- Compare platform output with vendor output
- Refine until acceptable parity is achieved

**Visual**
- Simple loop diagram based on Chapter 3

**What to say**
- Because vendor logic was not fully exposed, the project used reverse engineering.
- Each report was built and checked iteratively.
- The core idea was evidence-based validation, not assumption-based coding.

### Slide 7 - Core System Architecture

**Title**
Three Main Layers Formed the Platform

**On-slide content**
- Data layer: 1:1 replicated reporting database
- Backend layer: FastAPI semantic/API logic
- Frontend layer: React portal for report access

**Optional side notes**
- Read-only reporting environment
- Portal-triggered sync
- Scheduled ETL automation

**What to say**
- The data layer preserved source fidelity.
- The backend handled report rules and response shaping.
- The frontend gave users a practical report workflow with search, filters, view, and export.

### Slide 8 - Key Implemented Functions

**Title**
The Platform Delivered More Than Report Pages

**On-slide content**
- Report catalogue and query interface
- Export support for operational use
- User management
- Data sync administration
- Automation control
- Data-quality checking

**Visual**
- Use selected screenshots from `Figure 5.1` to `Figure 5.6`

**What to say**
- This proves the project is a usable internal platform, not just a backend prototype.
- Mention that admins can trigger sync, review status, and check data quality.

### Slide 9 - Report Scope and Final Outcome

**Title**
Most of the Formal Report Scope Was Delivered

**On-slide content**
- Formal scope: 19 reports
- Implemented and retained: 16 reports
- Not fully closed: 3 reports
- Additional customised reports: 3

**Table suggestion**
- 4 columns: scope type, count, status, note

**What to say**
- Be direct and confident here.
- The project delivered most of the agreed formal scope.
- The 3 unresolved reports were not simple missing pages.
- They remained open because profit-related logic could not be isolated conclusively.

### Slide 10 - Example of Report Reconstruction

**Title**
Payment Type Report Shows the Reconstruction Process

**On-slide content**
- Operationally important for reconciliation
- Required payment, sales, and outlet data linkage
- Needed precise grouping and reference handling
- Multiple refinements were required before parity was accepted

**Optional compare block**
- Problem
- Investigation
- Logic refinement
- Final validated outcome

**What to say**
- Use `Payment Type (All Payment)` as your main example.
- It is concrete, easy to explain, and already supported strongly in Chapter 5.
- Explain that the challenge was grouping and business-rule behaviour, not only data retrieval.

### Slide 11 - Validation and Testing Evidence

**Title**
Validation Was the Strongest Evidence of Success

**On-slide content**
- Parity validation against vendor outputs
- UAT and black-box testing
- White-box testing of critical logic
- Validation covered both accuracy and usability

**Visual**
- Mention figure groups:
- `Figure 5.8` to `Figure 5.15` for parity validation
- `Figure 5.16` to `Figure 5.31` for UAT and black-box
- `Figure 5.32` to `Figure 5.40` for white-box

**What to say**
- Explain that you did not stop at page completion.
- The report outputs were checked against vendor outputs under matched conditions.
- This made the platform academically stronger and practically more credible.

### Slide 12 - Operational Result and Performance

**Title**
The Platform Reached Practical Operational Usability

**On-slide content**
- Query tuning reduced timeout risk
- Response time improved for key report paths
- Portal supports internal reporting workflow
- Platform can be extended for company-requested reports

**Table suggestion**
- Show only 2 to 4 strongest timing examples
- Focus on `Payment Type (All Payment)` first

**What to say**
- Do not oversell performance.
- Say the goal was operational usability, not vendor benchmarking.
- Mention that improvements reduced timeout risk and improved response consistency.

### Slide 13 - Limitations, Future Work, and Conclusion

**Title**
The Project Delivered a Validated Platform With Clear Boundaries

**On-slide content**
- Delivered a company-controlled reporting platform
- Retained most of the formal report scope
- 3 reports remained not fully closed
- Future work: unresolved logic, stronger data quality coverage, further optimisation

**Closing line**
Thank you. Q and A session.

**What to say**
- Summarise the project in 3 sentences:
- the problem was vendor-dependent reporting access
- the solution was an internal platform with replica database, API layer, and portal
- the outcome was a validated reporting platform with honest documented limitations

## Recommended Slide Design Rules

- Use English on slides, but keep wording very short.
- Use 1 main message per slide.
- Prefer diagrams, tables, and screenshots over long bullets.
- Avoid heavy literature review slides.
- Avoid too many screenshots on one slide.
- Use large fonts so you can read and explain comfortably.

## Recommended Timing

- Slide 1: 1 minute
- Slide 2: 0.5 minute
- Slide 3: 2 minutes
- Slide 4: 1.5 minutes
- Slide 5: 2 minutes
- Slide 6: 2 minutes
- Slide 7: 2 minutes
- Slide 8: 2 minutes
- Slide 9: 2 minutes
- Slide 10: 3 minutes
- Slide 11: 3 minutes
- Slide 12: 2 minutes
- Slide 13: 2 minutes

Estimated total: around 23 to 25 minutes before Q and A

## Speaking Strategy For Your Situation

- Best option: slides in English, explanation mainly in Mandarin.
- Keep English technical keywords as-is.
- Memorise the first sentence and last sentence for each slide.
- For the middle explanation, speak naturally in Mandarin.
- If you want to speak more English, use short sentence patterns:
  - `This slide shows the main problem.`
  - `The key point is internal control.`
  - `The system has three main layers.`
  - `This report was validated against vendor output.`
  - `The final outcome was 16 retained reports out of 19.`
  - `Three reports were not fully closed due to remaining profit logic issues.`

## Likely Q and A

### Why did you build this platform instead of continuing to use the vendor portal?

**Answer**
The main issue was operational dependency. The company needed a more controlled internal reporting path for selected reports, especially for reconciliation and month-end work.

### Why did you use SQL Server, FastAPI, and React?

**Answer**
SQL Server supported the reporting replica, FastAPI was suitable for structured report APIs, and React supported a reusable internal portal workflow.

### Why were only 16 of 19 reports retained?

**Answer**
Three reports were not fully closed because the remaining profit-related logic could not be isolated conclusively through reverse engineering and parity validation within the project boundary.

### How did you know the platform output was correct?

**Answer**
The main approach was parity validation. The platform output was compared with vendor outputs under matched date range, outlet scope, and report conditions.

### Is this a full replacement of the vendor system?

**Answer**
No. It is a validated internal reporting platform for the agreed report scope, not a complete replacement for every vendor capability.

### What is the main contribution of this project?

**Answer**
The main contribution is a company-controlled reporting platform with replicated data, reconstructed report logic, validation evidence, and operational admin support.

### What can be improved in future?

**Answer**
Future work can continue the unresolved report logic, improve historical data-quality coverage, and further optimise heavy report paths.

## Recommended Final Message

`This project successfully delivered the Marrybrown Sales and Payment Analytics Platform as a validated internal reporting platform for selected sales and payment reports, while also documenting clear limitations for the few report areas that were not fully closed.`
