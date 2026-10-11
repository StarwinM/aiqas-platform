# AIQAS

AIQAS is a diploma project by **Dzhanin Miras** and **Turemuratov Galymzhan**. We are building a platform for university events that connects event publication, student registration, attendance confirmation, and reporting. Astana IT University is the intended pilot location; participation by the university and its clubs still needs to be agreed.

## Problem and users

Our starting assumption is that event announcements, registration forms, participant lists, and attendance records are spread across separate tools. This can mean repeated data entry, unclear registration statuses, and extra work when preparing reports. We will check these assumptions through interviews and observation of the actual process.

AIQAS is intended for three groups:

- **Students:** find events, register, access their tickets, and view confirmed participation.
- **Club organizers:** publish events, manage capacity and participants, confirm attendance, and prepare reports.
- **University administrators:** manage permissions and view activity data within their authorized scope.

## Scope and expected results

The first version follows one main flow:

**Publish an event → register → receive a ticket → confirm attendance → produce a report.**

The proposed core scope (P0) includes:

- Login and server-side access control for students, organizers, and administrators.
- An event catalog, filters, and event details.
- Event creation, publishing, updates, and cancellation.
- Registration with capacity limits, cancellation, and protection against duplicate requests.
- Personal tickets and attendance confirmation by QR code.
- Participant lists, notifications about important changes, and event reports.

Registration must remain correct when several students request the last seat at once. Repeated registration, cancellation, or QR scans must not create duplicate records or change capacity twice. Reports must agree with the saved registrations and attendance records.

Waitlists, achievements, student initiatives, and an AI assistant for event drafts are proposed for the next phase (P1). Personalized recommendations, team matching, payments, additional universities, and extended gamification are outside the first version. The official topic and scope need supervisor approval; if AI is mandatory for the topic, its feature and acceptance criteria must be included in the required scope. AITU SSO integration depends on access to the university's integration parameters.

The final diploma deliverables are a working core event flow, source code, reproducible setup, design documentation, and evaluation results. We will compare the time organizers spend on equivalent tasks in AIQAS and their existing process. We will also check data correctness, permissions, and usability on mobile devices. There are no measured results yet.

## Current status

**Updated October 12, 2026. First pre-defense: October 24, 2026.**

The repository has been created, but there is no runnable application yet. Prepared materials include:

- An English project document with the proposal, initial requirements and acceptance criteria, evaluation plan, milestones, and risks.
- A literature review with eight scientific publications and additional supporting sources, a comparison of four existing systems, and alternatives for three key technical decisions.
- System Context, Use Case, and draft Component diagrams created in Winter, with editable `.excalidraw` files and PNG exports.
- Three static Paper mockups: Events, Profile, and Admin Panel.
- Twenty assigned and prioritized YouTrack tasks, split equally between the team members.

Next, we need relevance evidence from 3–5 user discussions or a substantive client agreement, refined requirements, the remaining UX flows and states, agreed evaluation conditions, and substantive supervisor feedback followed by revisions. Repository access, material uploads, individual contribution history, and peer review still need to be verified. Initial drafts and checklist progress do not mean the corresponding tasks are fully complete.

A complete application is not required for October 24. The submission must demonstrate the analysis, design, planning, supervision, and contributions made so far.

## Team

| Member | First pre-defense responsibilities |
| --- | --- |
| **Dzhanin Miras** | Proposal, interviews, existing-system comparison, requirements, Use Case Diagram, UX mockups, responsibilities and risks, revisions after supervisor feedback, and presentation. |
| **Turemuratov Galymzhan** | Literature review, technology decisions, System Context and Component diagrams, baseline and evaluation method, test plan, repository and README, Git traceability, supervisor review coordination, and submission package. |

Each member owns ten preparation tasks, covering both research and technical work. For implementation, Miras leads backend and data work; Galymzhan leads frontend and UX work. Both contribute to requirements and evaluation, and review each other's significant changes.

**Supervisor:** Zhanna Sadirmekova.

## Selected technologies

| Area | Selected approach |
| --- | --- |
| Frontend | Next.js, React, TypeScript; planned PWA |
| Backend | Go API, organized as a modular monolith |
| Database | PostgreSQL, pgx, sqlc |
| Background jobs | Go worker with River |
| API and live updates | HTTP API described with OpenAPI; SSE for server updates, with polling as a fallback |
| File storage | S3-compatible storage |
| Deployment and checks | Docker Compose and CI |

The backend will contain identity, clubs, events, registrations, attendance, notifications, and reporting modules. Registration changes and their notification jobs will be saved in the same database transaction; a worker will deliver notifications with safe retries. Python/FastAPI will be added only if a concrete custom ML or data-processing task requires it.

The project document explains the technology choices and alternatives. Hosting, integration details, and the pilot environment remain to be agreed. These are design decisions, not implemented or benchmarked capabilities.

## Documentation and design

- [GitHub repository](https://github.com/StarwinM/aiqas-platform): the shared project repository.
- [Project document](https://docs.google.com/document/d/1IEr8V1fHB9v3cV7hidazmEBiEvvjuFPQE_3FLrPYPiE/edit): proposal, research, comparisons, requirements, architecture, verification plan, responsibilities, milestones, and risks.
- [YouTrack board](https://aiqas.youtrack.cloud/agiles/204-0/current): preparation tasks `DEMO-20` through `DEMO-39`. AIQAS task titles start with `AIQAS`.
- [Paper mockups](https://app.paper.design/file/01M4N0NETW9ZS7E1S9XRYVX5NA/p-1-0): Events, Profile, and Admin Panel. These are static concepts; event forms, registration outcomes, cancellation, QR scanning, and other states still need detailed design and user review.
- **Architecture diagrams:** editable sources and PNGs are included in the materials package and attached to YouTrack tasks `DEMO-27`, `DEMO-28`, and `DEMO-29`.

## Planned repository structure

Folders will be added as their contents become available:

```text
frontend/       Application interface
backend/        API, business rules, and background jobs
docs/           Proposal, research, requirements, decisions, and evaluation plan
diagrams/       Editable diagram sources and readable exports
ux/             Mockup exports and design notes
tests/          Automated tests, test data, and supporting materials
config/         Configuration examples and deployment files
```

Dependency definitions will be versioned alongside the relevant components. A suitable `.gitignore` must exclude local configuration, generated files, and secrets. Configuration examples will use placeholder values; test data will be synthetic or approved and anonymized.

## Setup, running, and testing

There is no runnable code yet. Once an executable version is available, this section will include required dependency versions, environment configuration, installation and startup commands, database migrations, and test commands. We will check the instructions in a clean environment.

The verification plan already covers business rules, database and access integration, the main user flow, concurrent registration, repeated QR scans, notification retries, load, mobile usability, and backup recovery. Test results will be recorded with the application version, environment, data, and known limitations.

## Working with Git and YouTrack

We use the same repository throughout the project. Each student contributes through their own account with identifiable commit details. We record coherent changes as work is completed, including documentation and design changes.

Each meaningful work item has a YouTrack task with an owner, expected result, acceptance criteria, and deadline. We use its ID in the branch name and commit message or pull/merge request description, for example:

```text
Branch: DEMO-26-requirements
Commit: DEMO-26: Clarify registration acceptance criteria
```

Changes are developed in task branches and submitted through a pull/merge request. Each request explains the change, links the task, and describes how the work was checked. The other team member reviews it before merging into `main`, our reviewed baseline. We link the resulting commit or request back to YouTrack and mark the task complete only when its acceptance criteria are met.

We will check access for both team members and the supervisor, and provide committee access before each pre-defense. Passwords, tokens, API keys, and confidential student data must not be committed.

Submission versions will use the tags `pre-defense-1`, `pre-defense-2`, and `final-pre-defense`. Each submission will include the repository link, exact tag, completed work, known limitations, and outstanding tasks. Submitted tags will not be moved or replaced.
