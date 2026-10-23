# 10 Project management and risks

10 Project management and risks

10.1 Distribution of responsibility

Responsibility is assigned in YouTrack: 20 tasks, with 10 owned by Dzhanin Miras and 10 by Turemuratov Galymzhan. The implementation directions below are retained, while research, technical design, and preparation tasks are shared. Each member works under their own account, understands the core event cycle, and reviews the other member's significant changes.

Frontend and UX direction: interface, prototype, student interviews, and user scenario testing. Responsible: Turemuratov Galymzhan.

Backend and data direction: API, data model, integrations, concurrency tests, and deployment. Responsible: Dzhanin Miras.

Jointly: organizer and administration interviews, literature and analog review, requirements and architecture approval, final evaluation, and defense preparation. Each reviews significant changes by the other.

10.2 Milestones and task ownership

The deadlines below match the current YouTrack plan for the October 24 pre-defense. They are planned checkpoints, not evidence that interviews, approvals, or tests have happened.

October 13: proposal and interview preparation; responsibilities, risks, repository basics, and access (DEMO-20, DEMO-21, DEMO-33, DEMO-34).

October 16–17: actual relevance evidence, literature review, analog comparison, and technology decisions (DEMO-22–DEMO-25). Prepared reviews still need peer review and Git traceability.

October 19–20: refine requirements after interviews; review the three diagrams; complete UX scenarios and the evaluation/test plan (DEMO-26–DEMO-32).

October 21–22: obtain substantive feedback from Zhanna Sadirmekova and record resulting decisions and revisions (DEMO-36, DEMO-37).

October 23: verify progressive contributions and reviews, package the exact submission under pre-defense-1, and rehearse the presentation (DEMO-35, DEMO-38, DEMO-39).

Miras owns DEMO-20, 21, 22, 24, 26, 28, 30, 33, 37, and 39: proposal, relevance, analogs, requirements, use cases, UX, coordination, revisions, and presentation.

Galymzhan owns DEMO-23, 25, 27, 29, 31, 32, 34, 35, 36, and 38: literature, technology decisions, context/components, evaluation/testing, repository work, supervisor review, and submission.

Dependency follow-up: Miras coordinates the client/club contacts and confirms baseline and data requirements by October 16 (contact names pending). Galymzhan follows up with the supervisor by October 21 and identifies the university SSO contact by October 13 (name and protocol pending). A delayed external dependency must be recorded in YouTrack and reflected in the scope.

10.3 Risks and dependencies



Risk | Probability / Impact | Mitigation | Trigger and Action

No access to SSO | Medium / High | Identify integration owner early; agree on fallback. | No params by dev start — test SSO for demo, revise plan.

Demand not confirmed | Medium / High | 3–5 interviews; align pilot and baseline. | No recurring problem — clarify goal and P0.

Scope creep | High / High | Core cycle first; separate P1/P2. | P0 falls behind — defer achievements, AI, and 2nd university.

Seat and QR errors | Medium / High | Transactions, uniqueness, and concurrency tests. | Duplicate or overbooking exists — pause registration pilot until fixed.

Data not aligned | Medium / High | Align composition, roles, storage, and retention; demo on synthetic data. | No resolution — do not use real profiles.

Environment unavailability | Medium / Medium | Backups, recovery, monitoring, and assigned lead. | Outage before event — agreed fallback process and incident log.



Probabilities are preliminary qualitative team estimates. External dependencies: advisor, client representative, SSO parameters, data alignment, pilot clubs, and infrastructure. Assign a contact person and response date for each dependency.

10.4 Git and YouTrack traceability

The AIQAS board contains DEMO-20–DEMO-39, covering proposal, interviews, literature, analogs, technologies, requirements, three diagrams, UX, evaluation, repository work, supervisor review, and submission. Tasks have assignees, priorities, acceptance criteria, dependencies, and deadlines in their descriptions. Prepared deliverables are recorded separately from remaining approval, review, and Git publication steps.

YouTrack: https://aiqas.youtrack.cloud/agiles/204-0/current

Repository [E2]: https://github.com/StarwinM/aiqas-platform

Initial Git evidence: README commit 18e9190ba0622230cfba0bb7f3b57dc45aa5d8d5 by Miras / StarwinM. This publication remains part of the history. The current packaging work adds the consolidated report and supporting sources under DEMO-38; the commit/PR and tag are traceable through the repository history.

Commit evidence: https://github.com/StarwinM/aiqas-platform/commit/18e9190ba0622230cfba0bb7f3b57dc45aa5d8d5

Task ownership and Git authorship are distinct. DEMO-34 is assigned to Galymzhan, while the initial README commit was published by Miras. Materials attributed in YouTrack retain their task ownership; packaging commits made through StarwinM belong to Miras. Actual peer review and contributions from Galymzhan’s account remain to be evidenced.

Use personal identifiable accounts, task branches, descriptive commits with DEMO IDs, and pull requests explaining changes and checks. The other member performs real review before merge; record revisions and link the PR/commit back to YouTrack. Mark Done only when acceptance criteria are met.

10.5 Submission version and materials manifest

Submission identifier: prob-period-1. The consolidated PDF and accompanying source materials form one versioned package. The first README-only preparation commit remains available in Git history; the release candidate adds the research, requirements, original Winter diagrams, UX materials, and evaluation plan. The final submitted tag must resolve to this complete package.

Submission snapshot https://github.com/StarwinM/aiqas-platform/tree/prob-period-1

Package content: docs/SE-2429_Dzhanin_ProbPeriod1.pdf; docs/SE-2429_Dzhanin_ProbPeriod1.docx; diagrams/src/*.excalidraw; diagrams/exports/*; prototype/src/*.svg and prototype/exports/*.png; research/survey-summary.csv; verification/verification-and-evaluation-plan.md; project-management/submission-checklist.md; and the supporting materials index.

Known limitations: no executable application or measured outcomes; organizer/client validation and baseline confirmation remain open; peer review and progressive contributions by both personal accounts must be evidenced separately. Publishing this package under Miras’s account is not a claim that Galymzhan authored its Git commits. Supervisor feedback status is stated in Section 11.