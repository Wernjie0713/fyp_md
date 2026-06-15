# FYP Final Presentation Slide Content

This version is written in simple English for presentation use.

Recommended deck size: `13 slides`

Main rule:
- Keep the slide text short.
- Do not read every bullet word by word.
- Use the bullets as guide points.

---

## Slide 1 - Title Slide

**Title**
Marrybrown Sales and Payment Analytics Platform

**Subtitle**
Final Year Project Final Presentation

**Content**
- Name: YONG WERN JIE
- Matric No: A22EC0121
- Programme: Final Year Project
- Supervisor:
- Industry Supervisor:
- Date:

**Simple opening line**
Good morning and thank you for attending my final year project presentation. Today I will present my project, which is the Marrybrown Sales and Payment Analytics Platform.

---

## Slide 2 - Presentation Overview

**Title**
Presentation Overview

**Content**
- Problem background
- Project aim and objectives
- System design and architecture
- Implementation and key functions
- Validation and testing
- Final result, limitation, and conclusion

**Simple transition line**
First, I will explain the problem background. Then I will show the system design, the implementation, the testing, and the final result.

---

## Slide 3 - Problem Background

**Title**
Vendor Portal Dependency Caused Reporting Problems

**Content**
- The company depended on the vendor reporting portal
- Internal users had limited control over report logic
- It was hard to trace the source data and investigate issues
- Portal delay or downtime affected reconciliation and month-end work

**Suggested visual**
- A simple comparison diagram:
  - Old flow: Vendor POS -> Vendor portal -> Finance and Operations users
  - New flow: Vendor POS -> Internal platform -> Finance and Operations users

**Simple speaking points**
- Before this project, the company mainly used the vendor portal for sales and payment reports.
- This created dependency on the vendor side.
- If the portal was slow or unavailable, users could not get reports on time.
- It was also difficult to understand the report logic or check the raw transaction data.

---

## Slide 4 - Problem Statement

**Title**
Main Problems in the Existing Reporting Process

**Content**
- Limited control over important reports
- Limited visibility into data and report logic
- Difficult to extend or maintain reports internally
- Reporting disruption could affect business work

**Simple speaking points**
- The first problem was limited internal control.
- The second problem was limited visibility into how the reports were produced.
- The third problem was that the company could not easily maintain or extend the reports by itself.
- The last problem was that reporting delay could affect important business processes.

---

## Slide 5 - Project Aim and Objectives

**Title**
Project Aim and Objectives

**Content**
**Aim**
- To develop an internal platform for selected sales and payment reports

**Objectives**
- Replicate selected transaction data into SQL Server
- Reconstruct vendor-aligned report logic
- Build a web portal for report access and export
- Validate the report output against vendor results

**Simple speaking points**
- The aim of this project was to build an internal reporting platform.
- The platform uses replicated data, reconstructed report logic, and a web portal.
- Another important objective was validation, because correct output was very important.

---

## Slide 6 - Proposed Solution

**Title**
Company-Controlled Internal Reporting Platform

**Content**
- SQL Server reporting database
- FastAPI semantic and API layer
- React-based web portal
- Admin support for sync, automation, and data quality check

**Suggested visual**
- One clean architecture diagram with 4 blocks:
  - Source system
  - Reporting database
  - FastAPI backend
  - React portal

**Simple speaking points**
- The solution was to build an internal reporting platform.
- First, selected source data is replicated into a company-managed SQL Server database.
- Then the FastAPI backend reconstructs the report logic.
- Finally, the React portal allows users to search, view, and export reports.

---

## Slide 7 - Development Method

**Title**
Iterative Development and Validation

**Content**
- Analyse vendor report behaviour
- Trace the source data
- Rebuild the report logic step by step
- Compare platform output with vendor output
- Refine until the result is acceptable

**Suggested visual**
- A cycle diagram:
  - Analyse
  - Design
  - Implement
  - Validate
  - Improve

**Simple speaking points**
- This project did not use a one-time development approach.
- It used an iterative method.
- For each report, I studied the vendor behaviour, traced the data, implemented the logic, and then validated the result.
- If the output was still not correct, I refined the logic again.

---

## Slide 8 - System Architecture

**Title**
Three Main Layers of the Platform

**Content**
- Data layer: replicated SQL Server reporting database
- Backend layer: FastAPI report logic and API services
- Frontend layer: React portal for users and admins

**Optional small note**
- Read-only reporting environment

**Simple speaking points**
- The system has three main layers.
- The first layer is the data layer, which stores the replicated reporting data.
- The second layer is the backend layer, which handles report logic and API responses.
- The third layer is the frontend layer, which gives users access through a web portal.

---

## Slide 9 - Key Functions of the Platform

**Title**
Main Functions Implemented in the Platform

**Content**
- Report list and report query page
- Parameter input and grouped result view
- Export function
- User management
- Data sync management
- Automation control
- Data quality checking

**Suggested visual**
- 3 screenshots only:
  - report page
  - data sync page
  - automation or user management page

**Simple speaking points**
- The platform provides more than report pages only.
- Users can search for reports, enter parameters, and export results.
- Admin users can also manage data sync, automation, and user access.
- Data quality checking was also added to support trust in the reporting data.

---

## Slide 10 - Report Scope and Final Outcome

**Title**
Final Report Delivery Outcome

**Content**
| Scope | Count | Result |
| --- | ---: | --- |
| Formal report scope | 19 | Main project report scope |
| Implemented and retained | 16 | Successfully delivered |
| Not fully closed | 3 | Remaining profit logic issue |
| Additional customised reports | 3 | Delivered based on company request |

**Simple speaking points**
- The formal project scope included 19 reports.
- Out of these 19 reports, 16 were successfully implemented and retained.
- Three reports were not fully closed.
- In addition, three customised reports were also developed based on company requests.

---

## Slide 11 - Example Report Implementation

**Title**
Example: Payment Type (All Payment) Report

**Content**
- Important for reconciliation work
- Uses payment, sales, and outlet data together
- Needs correct grouping and reference handling
- Required multiple rounds of refinement and validation

**Suggested layout**
- Left side: small flow
  - source data
  - query logic
  - grouped output
  - validation
- Right side: short bullets above

**Simple speaking points**
- I use the Payment Type report as one implementation example.
- This report is important because it supports reconciliation.
- It is not only about summing payment values.
- The challenge was to reproduce the same grouping and report behaviour as the vendor portal.

---

## Slide 12 - Validation and Testing

**Title**
Validation Was the Main Proof of Correctness

**Content**
- Parity validation against vendor output
- Black-box and user acceptance testing
- White-box testing for important internal logic
- Testing covered both correctness and usability

**Suggested visual**
- 3 boxes:
  - Parity Validation
  - UAT / Black-Box Testing
  - White-Box Testing

**Simple speaking points**
- Validation was one of the most important parts of this project.
- I compared the platform output with vendor output under the same conditions.
- I also tested the user functions such as report access, filtering, and export.
- For internal logic, I used white-box testing on important processing paths.

---

## Slide 13 - Performance, Limitation, and Conclusion

**Title**
Final Result and Conclusion

**Content**
- The platform delivered a usable internal reporting workflow
- Query tuning improved response time for key report paths
- 16 formal-scope reports were retained successfully
- 3 reports were not fully closed because remaining profit logic could not be isolated conclusively
- The project delivered a validated internal reporting platform for the agreed scope

**Closing line on slide**
Thank you. Q and A session.

**Simple speaking points**
- Overall, this project successfully delivered an internal reporting platform for selected sales and payment reports.
- The system included replicated data, reconstructed logic, a web portal, and validation support.
- Most of the formal scope was delivered successfully.
- The remaining unresolved reports were related to profit logic, not simple missing page development.

---

## Optional Backup Slide A - Limitations

**Title**
Project Limitations

**Content**
- Some report parity depends on data completeness in the replica
- Vendor logic was treated as a black box
- Some profit-related logic could not be isolated clearly
- The platform is not a full replacement for every vendor function

**Use**
- Use this only if you want one more slide before conclusion, or keep it as backup for Q and A.

---

## Optional Backup Slide B - Future Improvement

**Title**
Future Improvement

**Content**
- Continue investigation on unresolved report logic
- Improve historical data quality coverage
- Further optimise heavier report queries
- Expand validated report coverage when needed

**Use**
- Use this only if your supervisor likes future work slides, or keep it as backup.

---

## Simple English Sentences You Can Reuse

Use these during presentation if you need easy sentence patterns:

- This slide shows the main problem.
- The company depended on the vendor portal.
- The key issue was limited internal control.
- The system has three main layers.
- The backend reconstructs the report logic.
- The portal allows users to view and export reports.
- This project used iterative development.
- The output was validated against vendor results.
- Sixteen reports were successfully retained.
- Three reports were not fully closed.
- The main remaining issue was profit-related logic.
- Overall, the project achieved its main goal.

---

## Best Speaking Advice For You

- Keep your slides in simple English.
- Speak in short sentences.
- Pause after each key point.
- Do not try to sound too advanced.
- Clear and steady speaking is better than difficult vocabulary.
- If you forget a word, use a simpler word and continue.

