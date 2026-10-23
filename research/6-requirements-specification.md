# 6 Requirements specification

6 Requirements specification

Priorities: P0 — mandatory core cycle; P1 — next phase; P2 — further development. Student-side refinements from Section 2 are visible seat availability, explicit registration status, self-service cancellation, and topic/date filters. Organizer/client validation remains required. Acceptance criteria describe intended behavior, not already implemented features.

6.1 Functional Requirements



ID / Priority | Requirement | Acceptance Criteria | Verification

FR-01 / P0 | Login and Logout | Valid identification opens profile; invalid is rejected; protected actions unavailable after logout. | Integration test with test SSO.

FR-02 / P0 | Roles and Access Scopes | Student cannot edit another user's event; organizer manages only permitted clubs; restriction enforced by server. | Matrix of permitted and forbidden requests.

FR-03 / P0 | Catalog and Filters | Published events displayed; combination of tags, date, and status matches test set. | Functional scenarios.

FR-04 / P0 | Creation and Publishing | Event contains title, club, time, location, capacity, and deadline; invalid fields block publishing. | Positive and negative form tests.

FR-05 / P0 | Registration and Capacity | For 100 seats under 1,000 concurrent attempts, max 100 confirmations; with enough unique valid attempts — exactly 100. | Load test and DB check.

FR-06 / P0 | Protection Against Duplicate Registration | Resubmission by same student does not create a second active registration or occupy additional seat. | Repeated and parallel requests.

FR-07 / P0 | Participation Cancellation | Cancellation changes status once and releases seat once; history preserved. | Repeat and concurrent cancellation.

FR-08 / P0 | Ticket and Status | After successful registration ticket accessible to owner; other ticket restricted; cancelled ticket does not confirm attendance. | Owner and status check.

FR-09 / P0 | Attendance Confirmation | Authorized verifier confirms ticket for target event; retry does not create second attendance record. | QR, duplicates, and wrong event.

FR-10 / P0 | List and Report | For permitted event, list and CSV/PDF reflect confirmed registrations and attendances without duplicates. | Reconciliation with control set.

FR-11 / P0 | Notifications on Important Changes | Confirmation, event cancellation, and time change create tasks; sending error does not lose registration. | External service failure and worker retry.

FR-12 / P1 | Waitlist | Freed seat is offered according to agreed order; acceptance does not exceed capacity. | Priority order, deadline, and concurrent acceptance.

FR-13 / P1 | Achievements and Initiatives | Achievement contains rationale and issuer; initiative retains decision and status; re-issuance does not create duplicate. | Permissions, statuses, and uniqueness.

FR-14 / P1 | AI Event Draft | AI generates editable draft; publication only after organizer confirmation; mandatory fields validated. | Control set of inputs; errors and manual check.



6.2 Non-Functional Requirements



ID | Requirement | Target Condition | How to Verify

NFR-01 / P0 | Integrity | No overbooking or duplicate registration/attendance records in test scenarios. | Reconciliation of SQL invariants after tests.

NFR-02 / P0 | Access Control | All protected operations undergo server-side role and scope checks; all access rejection tests pass. | Automated permissions matrix.

NFR-03 / P0 | API Response | Proposed targets: p95 read ≤300 ms, registration ≤700 ms; technical errors <1% at 100 RPS for 5 minutes. | On specified staging; expected capacity rejections not counted as 5xx.

NFR-04 / P0 | Recovery | Proposed RPO ≤24 h and RTO ≤4 h; restored copy passes integrity check. | Practice recovery with time logging.

NFR-05 / P0 | Mobile Usability | Core scenarios accessible at 360 px width and 200% zoom without action loss; keyboard navigation verified. | Manual check on devices and browsers.

NFR-06 / P0 | Privacy | Private data and secrets do not enter public responses, logs, or repository; data composition agreed. | Check responses, export, logs, and config.

NFR-07 / P0 | Reproducibility | New team member launches system and tests per README with sample configuration; versions locked. | Clean environment and CI.

NFR-08 / P0 | Time and Language | Time displayed with event zone; dates and texts do not contradict. RU/KZ/EN — proposed scope for alignment. | Boundary dates, selected languages, and agreed mockups.

NFR-09 / P1 | PWA Behavior | Installation and saved ticket verified; logout clears private cache; registration requires server confirmation. | Weak network, offline, logout, and re-login.



All numerical NFR values are testing targets, not measured performance. Prior to approving NFR-03, lock machine configuration, application version, dataset size, request distribution, and active connection count. Measure frontend and AI separately; do not mix their latencies with the API.