# Verification and evaluation plan

9 Verification and evaluation plan

9.1 Methodology and test data

Verification covers unit tests of business rules, integration tests of DB and access, end-to-end main cycle, concurrency and load scenarios, manual UX/PWA check, and recovery. Staging data is synthetic: 1,000 students, several clubs, events of various statuses, full and available events. Real pilot data will be used only after university approval.



Test | Related Requirements | Scenario | Expected Evidence

V-01 | FR-01, FR-02; NFR-02 | Login, logout, foreign roles and objects | Permissions/rejections log; unauthorized request rejected.

V-02 | FR-03, FR-04 | Catalog, filters, creation, and validation | Data and results match control set.

V-03 | FR-05, FR-06; NFR-01 | 1,000 unique valid attempts for 100 seats; duplicates | Exactly 100 confirmations; no duplicates or overbooking.

V-04 | FR-07, FR-12 | Repeated cancellation; under P1 — waitlist competition | Seat released once; order maintained.

V-05 | FR-08, FR-09 | Foreign and cancelled QR; 10 scan retries | Invalid ticket rejected; single attendance.

V-06 | FR-10 | Report for set with known numbers | CSV/PDF and UI match DB.

V-07 | FR-11 | Worker failure after write and before send | Registration saved; task retries safely.

V-08 | NFR-03 | 100 RPS for 5 minutes; separate peak 300 RPS for 10 seconds | p95/p99, 5xx, CPU/RAM, queue, locks; peak characterized separately.

V-09 | NFR-04, NFR-07 | Clean start and backup recovery | Launch log, RPO/RTO, and integrity of restored data.

V-10 | NFR-05, NFR-09 | Mobile cycle, keyboard, weak network, and logout | Defect list and confirmed fixes.



9.2 Baseline process and experiment

The proposed reference baseline is Google Forms registration, a participant spreadsheet, manual attendance marking, and a manually assembled report. Three survey records mention Google Forms, but that does not confirm a club’s full workflow. Before comparison, a participating organizer must confirm the actual tools, steps, participant count, report fields, and access conditions. If the real process differs, document and use it. Both conditions use equivalent tasks, event data, and report definitions.

A later field pilot targets three clubs and five events after implementation and agreement on access/data. It is separate from the five questionnaire records and formative UX study. For the paired time study, plan three organizers completing equivalent tasks in both baseline and AIQAS, with alternating order and equivalent practice. Record experience, help, interruptions, and failed tasks. Report paired values and medians; a small pilot does not demonstrate a university-wide causal effect.



Indicator | Definition and Collection | Proposed Target | Limitation

Organizer Time | Publishing time + list processing + reporting; identical tasks; compare medians. | Reduction ≥30%; 50% from technical doc is an ambitious additional target. | Baseline measurements needed; training impacts time.

Accounting Errors | Duplicates and report discrepancies against control DB. | 0 duplicates and 0 discrepancies in required tests. | Does not characterize all possible production failures.

UX Success Rate | Core scenarios completed without assistance / initiated scenarios. | Tentatively ≥80%; align after test format. | Small sample; report numbers of participants and tasks.

Attendance and Repeat Participation | Attendees / active registrations; repeat participation over specific window. | First measure baseline; growth target after pilot. | Diverse events and self-selection hamper causal conclusion.

AI when enabling P1 | Drafting time, share of corrected required fields, cost of accepted output. | No auto-publishing; align utility and budget before launch. | Model failure should not block manual creation.



The final evaluation must contain application version, environment, participants, methods, actual values, identified defects, and limitations. Prior to testing, the results section remains unpopulated. For each mandatory FR/NFR, the report references a test and proof link.

9.3 Planned technical measurement conditions

Planned reference staging: API/Go worker on a 2-vCPU/4-GiB Linux host; PostgreSQL on a separate 2-vCPU/4-GiB SSD-backed host; load generator on another machine. Before testing, record actual CPU/RAM/disk, OS, network path, image digests, dependency versions, database settings, migrations, and Git commit. These are planned conditions, not an already provisioned environment. Record any change and rerun the compared conditions.

Synthetic data: 1,000 students, 10 clubs, and 50 events spanning controlled published, full, draft, and cancelled cases. Fix the generator seed and initial registrations/attendances; reset between runs. The capacity test starts with 100 free places and 1,000 distinct eligible students; duplicate-request tests are separate.

Load protocol: 60-second warm-up, then 100 RPS for five minutes, repeated three times after reset. Planned mix: 60% catalog, 25% event details, 10% registration, 5% owner ticket/status. Keep sufficient seats outside the separate saturation test. Record offered/completed throughput, actual mix, active connections, timeouts, p50/p95/p99, 5xx, CPU/RAM, locks, and queue depth. Test 300 RPS for 10 seconds separately. Record SSE connections separately from HTTP request rate.

Apply NFR-03 by endpoint class: p95 reads ≤300 ms, registration ≤700 ms, technical errors <1% at 100 RPS. Separate expected business/capacity rejections from technical failures. Report every run and the worst observed p95; do not hide failures in averages. Measure API latency independently of frontend rendering, notification delivery, and optional AI.

Add V-11 for NFR-06: inspect public/protected responses, exports, logs, sample configuration, and repository secrets. Add V-12 for NFR-08: check time-zone/date boundaries and each agreed language. V-01 includes scoped role changes; V-07 includes notification retries; V-09 includes clean launch and timed backup restoration. Preserve requirement IDs, data version, commands, and evidence logs.

9.4 Planned UX and outcome measurement conditions

Formative study target: six representatives—three students, two club organizers, one activity administrator. Recruitment and dates remain to be confirmed. The five questionnaire records are not completed usability sessions. Give common orientation and predefined tasks; provide help only after recording an unassisted failure.

Student tasks: find by topic/date and check seats; register and locate confirmation/ticket; cancel and recognize an invalid ticket. Organizer tasks: publish and recover from validation; check valid, repeated, and cancelled/wrong-event tickets; export a correct report. Administrator task: grant a scoped organizer role and verify cross-club rejection. Walk through full, empty, loading, access-denied, and connection-error states.

Per attempt record participant code/role, task, device/browser, unassisted success, errors, help, elapsed time, and comments. Proposed formative target: ≥80% unassisted completion, reported as numerator/denominator overall and by task/role. Record desktop viewport and 360-px mobile viewport, keyboard navigation, focus, 200% zoom, and phone check-in once implemented. A static walkthrough cannot validate device behavior.

Paired organizer-time study: the same publication task, 100-participant list, attendance decisions, and report template in both conditions. Start when instructions/data are available; stop on a correct deliverable. Include correction time and record failures. Compute reduction as (baseline time − AIQAS time) / baseline time × 100%; report every pair and median paired reduction. The ≥30% target is a planned criterion, not an observed result.

The result register records version, environment, participants/tasks, baseline, raw observations, calculations, defects, and limitations. Until tests/sessions run, label results Not measured. Participation history, repeat attendance, and AI benefit remain separate P1 evaluations.