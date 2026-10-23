# 5 Technology comparison

5 Technology comparison

Three key decisions are compared against the data model, concurrent operations, frontend integration, and maintenance effort. The selected baseline is Go for the API, PostgreSQL for storage, and HTTP with SSE for server-to-browser updates; polling remains a fallback. The team chose Go for a stable server foundation and concurrent API/worker processing, accepting a separate OpenAPI contract with the TypeScript frontend. Elysia/Bun remains a capable alternative, particularly for shared TypeScript types; it is not rejected as inherently unreliable. No comparative performance measurements have been made.



Solution and Option | Strong Side | Considerations | Decision

API — Go | Concurrent processing and unified API/worker code [T1] | Separate language from frontend; maintain contract and client via OpenAPI. | Selected main API; validate the implementation against FR/NFR.

API — Elysia/Bun | TypeScript and typed Eden client [T2] | Check team libraries, operations, and test scenarios. | Reasonable alternative when shared TS is prioritized.

API — FastAPI | Python and proximity to ML; async I/O [T3] | CPU tasks require separate execution structure. | Separate ML service if need arises.

DB — PostgreSQL | Relations, constraints, and locks [T4, T5] | Requires indexes, migrations, and concurrency tests. | Main DB for events, registrations, and reports.

DB — MySQL/InnoDB | Transactional relational alternative [T6] | Drivers, SQL, and operations need alignment. | Possible if team has experience; measure benefits.

DB — MongoDB | Document model and multi-document transactions [T7] | Explicitly design relations, uniqueness, and transaction boundaries. | Not selected for current relational model.

Updates — Polling | Periodic HTTP request; clear fallback path | Request frequency sets latency and extra load. | Fallback if persistent connection is unavailable.

Updates — SSE | Server-to-browser stream and reconnection [T8] | Stream authorization, reconnect, and state alignment. | For slots and attendance panel; write via HTTP API.

Updates — WebSocket | Two-way communication [T9] | Requires connection state and protocol maintenance. | No mandatory two-way scenario yet.

