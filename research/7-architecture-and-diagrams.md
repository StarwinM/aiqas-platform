# 7 Architecture and diagrams

7 Architecture and diagrams

7.1 Selected stack and component boundaries

Frontend: Next.js, React, and TypeScript; PWA per Next.js guide [T11]. Main backend: Go; database: PostgreSQL; background tasks: Go worker and River PostgreSQL queue [T12]. Files: S3-compatible storage. HTTP API contract: OpenAPI. Pilot deployment: containers and reproducible configuration; hosting location and budget to be agreed separately.

Modular monolith includes Identity, Clubs, Events, Registrations, Attendance, Notifications, and Reports. Achievements and Proposals are added in P1. Python/FastAPI is not created without a task requiring its own models or data processing. University and membership are part of the access model; checking a second university refers to future expansion.

7.2 Data and integration rules

Seat availability is checked and updated within a single transaction; repeat registration is constrained by uniqueness of participant–event pair. Attendance is unique per registration. A notification is queued together with saving registration and sent after commit; task retries must be safe [T4, T5, T12]. These are designed properties that must be confirmed by tests.

University SSO is an external dependency. Until integration parameters are obtained, a working AITU login cannot be claimed. For demonstration, a test identity provider is acceptable with explicit labeling; the fallback method for real login will be agreed with the university. An email domain does not automatically grant an administrative role.

Core entities: User, University, Membership, Club, Event, Registration, Attendance, NotificationJob, and AuditLog. In P1: Achievement and Proposal. Data of a closed participant list is available only to permitted roles; public event card does not disclose personal history.

7.3 Architecture diagrams

The diagrams describe the planned P0 system. Their editable originals were recovered from the existing AIQAS drawings in Winter. Matching .excalidraw, SVG and PNG files are included in the versioned diagram materials. The use-case export includes the full drawing bounds and all three roles.

Source index [E3]: https://github.com/StarwinM/aiqas-platform/tree/prob-period-1/diagrams

7.3.1 System context

Students, club organizers, and administrators interact with AIQAS within their roles. University SSO and notification delivery are external dependencies. The one-university pilot boundary is explicit; integration parameters have not yet been confirmed.



Figure 1. AIQAS System Context. Winter source aiqas-system-context.excalidraw. Task DEMO-27.

7.3.2 Use case diagram

The diagram maps P0 actions to FR identifiers: discovery, registration, cancellation, ticket access, event management, attendance confirmation, reporting, and scoped role management. FR-01 authentication and FR-02 permissions apply to protected actions. P1/P2 extensions are outside this diagram.



Figure 2. P0 Use Case Diagram. Winter source aiqas-use-case.excalidraw. Task DEMO-28.

7.3.3 Component diagram draft

The frontend calls a Go modular monolith through an OpenAPI-described HTTP interface and receives SSE updates. Identity/Clubs, Events, Registration/Attendance, and Notifications/Reports share the backend and PostgreSQL. Registration changes and durable River jobs are committed in the same transaction. A separate Go worker handles reminders and safe delivery retries. SSO, delivery, and S3-compatible storage are external integrations. Python/FastAPI is optional and requires a concrete ML need.



Figure 3. Draft Component Diagram. Winter source aiqas-components.excalidraw. Task DEMO-29.