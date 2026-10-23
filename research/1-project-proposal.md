# 1 Project proposal

1 Project proposal

1.1 Topic, Team, and Advisor

Project title: Development of a Unified Digital Platform for Organizing and Managing Student Events.

Authors: Dzhanin Miras (SE-2429) and Turemuratov Galymzhan (SE-2418). Intended pilot: Astana IT University. Supervisor: Sadirmekova Zhanna Bakirbayevna.



1.2 Problem and Target Users

AIQAS addresses fragmented event discovery, registration status, and participant information. An initial student questionnaire collected five responses on October 22–23, 2026: all five selected missing information about available seats; two each reported late discovery, unclear registration success, unclear cancellation, and conflicting information across sources. These are preliminary self-reports from a small student sample. Organizer workload, reporting effort, and the current club process still require organizer discussions and observation; no time saving has been measured.

Student: find a suitable event, register, see status and ticket, save a confirmed participation history.

Club Organizer: publish an event, manage seats and participants, confirm attendance, and receive a report.

University Activity Administrator: manage permissions and view aggregated indicators within the permitted scope.

1.3 Goal, Tasks, and Expected Result

Goal — develop and evaluate a platform that integrates event publication, registration, attendance confirmation, and reporting, maintains data correctness during concurrent actions, and reduces the execution time of selected organizer tasks relative to an agreed manual process.

Identify the needs of three user roles and describe the current process.

Analyze scientific approaches, existing systems, and technical alternatives.

Formulate verifiable requirements, design architecture, and user scenarios.

Implement the main event cycle with access control, capacity limits, and repeated actions.

Verify functionality, load, and usability; compare task completion time with the baseline process.

Document results, limitations, and individual contributions of team members.

Expected results of the final thesis: a working prototype of the main cycle, source code and reproducible launch, requirements specification, architectural materials, test results, and pilot evaluation. Expected result of the first pre-defense: an agreed scope and a documented plan for obtaining them.

1.4 Boundaries and Complexity of the Project

Proposed P0: login and roles, catalog and event card, organizer publication, registration with capacity limit, ticket, attendance confirmation, cancellation, basic notifications, and reports. The pilot is limited to one university; the number of clubs and events will be clarified with the client.

Proposed P1: waitlist, confirmed achievements, student initiatives, and AI assistant for event drafting. P2: personalized recommendations, team matching, second university, payments, and extended gamification. P1/P2 should not block the core cycle.

Engineering complexity lies in access control, atomic registration for limited seats, handling retries, correct attendance tracking, and report consistency. Reducing organizer time and the usefulness of achievements require a separate user evaluation.