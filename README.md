# AIQAS

Development of a Unified Digital Platform for Organizing and Managing Student Events.

Probationary period 1, 24 October 2026. Intended pilot: Astana IT University.

## Submission

- [Consolidated PDF report](docs/SE-2429_Dzhanin_ProbPeriod1.pdf)
- [Editable report](docs/SE-2429_Dzhanin_ProbPeriod1.docx)
- [Editable Winter diagram originals](diagrams/src/)
- [Readable diagram exports](diagrams/exports/)
- [Editable P0 scenario drawings](prototype/src/)
- [Prototype exports](prototype/exports/)
- [Survey evidence and report sections](research/)
- [Verification and evaluation plan](verification/verification-and-evaluation-plan.md)
- [Submission checklist](project-management/submission-checklist.md)

Required submission tag: [prob-period-1](https://github.com/StarwinM/aiqas-platform/tree/prob-period-1).

## Problem and users

AIQAS connects event discovery, publication, registration, personal tickets,
attendance confirmation and reports for students, club organizers and activity
administrators. Initial student evidence is a five-response questionnaire from
22–23 October 2026. Five respondents selected missing seat information;
two each selected late discovery, unclear registration status/cancellation, and
conflicting information. This is preliminary self-report evidence, not completed
interviews, a representative university survey, or a measured platform effect.

## Scope and expected outcomes

P0: login and scoped roles, catalog and filters, event creation, capacity-limited
registration, duplicate protection, cancellation, tickets, attendance, notifications,
and reports. Planned evaluation checks permissions, capacity correctness, repeated
actions, report consistency, mobile usability and organizer task time.
P1: waitlist, achievements, initiatives and assisted event drafts. P2: recommendations,
team matching, additional universities, payments and extended gamification.

## Current status

Analysis and design materials are prepared. There is no runnable application yet.
The package contains a literature review with 8 scientific publications and
additional sources, 4 systems compared on 8 criteria, 3 technical decisions with
alternatives, 14 FR and 9 NFR, 3 original Winter diagrams, 3 original Paper screen
exports, 5 added P0 scenario sheets, and an evaluation/test plan with explicit
planned conditions. Actual benchmark, pilot and usability results are not claimed.
Organizer/client validation, supervisor feedback and real peer review remain open.

## Team

| Member | Group and GitHub | Responsibilities |
|---|---|---|
| Dzhanin Miras | SE-2429, [StarwinM](https://github.com/StarwinM) | Backend/data direction; requirements, existing systems, Use Case, UX, coordination and packaging |
| Turemuratov Galymzhan | SE-2418, [bananapie228](https://github.com/bananapie228) | Frontend/UX direction; literature, technology, context/components, verification and evaluation planning |

Supervisor: Sadirmekova Zhanna Bakirbayevna. Task ownership and actual Git authorship
are distinct. Packaging commits made under StarwinM belong to Miras. They do not
constitute contributions from Galymzhan's GitHub account or review by another member.

## Technologies

Next.js, React and TypeScript; Go modular monolith; PostgreSQL with pgx/sqlc;
River background jobs; OpenAPI-described HTTP API; SSE with polling fallback;
S3-compatible file storage; planned container deployment and CI.

## Project links

- [YouTrack](https://aiqas.youtrack.cloud/agiles/204-0/current), DEMO-20–DEMO-39
- [Working Google Doc](https://docs.google.com/document/d/1IEr8V1fHB9v3cV7hidazmEBiEvvjuFPQE_3FLrPYPiE/edit)
- [Original Paper designs](https://app.paper.design/file/01M4N0NETW9ZS7E1S9XRYVX5NA/p-1-0)

## Running and testing

No application commands exist at this stage. Launch instructions, dependencies,
example environment, migrations and automated test commands will be added when
runnable code exists. The current verification plan is in verification/.
Winter .excalidraw files can be opened in Excalidraw-compatible drawing tools;
editable SVG scenario drawings can be opened in an SVG design editor.

## Development record

Keep this repository throughout the project. Use identifiable personal accounts,
task branches, meaningful commits and PRs linked to YouTrack. The other member
reviews significant changes before merge; record actual comments and revisions.
Do not manufacture historical commits, user interviews, test results or approvals.
Keep previous submitted snapshots available and record any correction to a
preliminary submission tag transparently.
