# Technology Comparison

## 1. Purpose

This document compares alternatives for the key technology decisions of the project and justifies the selected options by the project requirements. Five decisions are covered:

1. Server platform
2. Data storage
3. Interaction between the frontend and the backend
4. Frontend framework
5. Backend architecture style

## 2. Requirement drivers

The decisions are evaluated against drivers taken from the project scope and engineering complexity described in the [project proposal](../01-proposal/project-proposal.md). Detailed requirements will be specified in `docs/06-requirements/`.

| ID | Driver | Source in the proposal |
|---|---|---|
| D1 | **Chained processing of learning events.** One action (e.g. a completed lesson) updates progress, XP, level, streak, achievements and notifications | Engineering complexity |
| D2 | **Relational domain with consistent data.** Users and roles, courses → modules → lessons, tests and attempts, enrolments, payments, reviews, certificates | Scope: users, catalog, authors, learning |
| D3 | **Data-driven achievements.** Achievement conditions are stored in the database and can be added without code changes | Scope: gamification |
| D4 | **Leaderboards.** Weekly (reset every Monday) and all-time rankings; each student sees their own position, even outside the top | Scope: gamification |
| D5 | **Time-zone-aware streaks.** Study days are counted by the student's local date | Scope: gamification |
| D6 | **Public catalog and course pages; English and Russian interface** | Scope: catalog; expected outcomes |
| D7 | **Team of two students and a fixed academic timeline** | General information |

## 3. Evaluation method

For each decision, 2–3 realistic alternatives were compared against criteria derived from the drivers. Each criterion is rated **High / Medium / Low** with a short reason. Ratings are qualitative and based on official documentation (section 9) and the documented characteristics of each technology; they are not benchmark results. Performance-related assumptions will be checked in the verification and evaluation plan.

## 4. Decision 1 — Server platform

**Alternatives:** Go, Node.js (TypeScript), Java (Spring Boot).

| Criterion | Driver | Go | Node.js (TypeScript) | Java (Spring Boot) |
|---|---|---|---|---|
| Concurrent processing of events and background work | D1 | **High** — goroutines are lightweight and built into the language [R1] | **Medium** — non-blocking I/O on a single JavaScript thread by default; long-running callbacks delay other work [R2] | **High** — multi-threaded runtime |
| Performance and resource use | D1, D4 | **High** — compiled to a native binary | **Medium** — JIT-compiled JavaScript running on one main thread by default [R2] | **Medium** — runs on the JVM, which typically uses more memory and starts slower than a native binary |
| Static typing and maintainability | D2 | **High** — statically typed | **Medium** — static types only at compile time via TypeScript | **High** — statically typed |
| Deployment simplicity | D7 | **High** — single executable | **Medium** — requires the Node.js runtime and dependencies | **Medium** — requires the JVM and build tooling |
| Libraries for HTTP APIs and PostgreSQL | D2 | **High** — standard `net/http`, mature PostgreSQL drivers | **High** | **High** |
| Team experience | D7 | **High** — existing team experience | Not evaluated | Not evaluated |

**Decision: Go.** Go fits the event-driven gamification logic (D1) through lightweight concurrency, is statically typed and is deployed as a single executable, which keeps operations simple for a two-person team (D7). The team already has experience with Go. Node.js was rejected mainly because event processing and ranking calculations run on a single thread by default; Java (Spring Boot) is a strong option but adds runtime and tooling overhead without a clear benefit for this project.

## 5. Decision 2 — Data storage

**Alternatives:** PostgreSQL, MySQL, MongoDB.

| Criterion | Driver | PostgreSQL | MySQL | MongoDB |
|---|---|---|---|---|
| Relational integrity (foreign keys, constraints) | D2 | **High** | **High** | **Low** — document model without foreign keys |
| Consistent updates across several entities (e.g. progress + XP + achievement in one transaction) | D1, D2 | **High** — ACID transactions | **High** — ACID transactions | **Medium** — multi-document transactions are supported, but the documentation recommends designing the schema to minimise them [R6] |
| Flexible storage and querying of achievement rules | D3 | **High** — `jsonb` with GIN indexes on the whole document [R3] | **Medium** — native JSON type, but JSON columns are not indexed directly; indexes are built on generated columns [R4] | **High** — native document storage |
| Ranking queries for leaderboards | D4 | **High** — window functions [R5] | **High** — window functions [R7] | **Medium** — requires aggregation pipelines |

**Decision: PostgreSQL.** Most of the domain is relational and must stay consistent (D2), and one learning event changes several entities at once (D1), which requires reliable transactions. PostgreSQL also covers the flexible part of the data: achievement conditions can be stored as `jsonb` and indexed (D3), and leaderboard positions can be calculated with window functions (D4). MySQL is close, but its JSON support is weaker for this use case. MongoDB fits the flexible achievement rules, but most of the domain is relational and depends on multi-entity consistency.

## 6. Decision 3 — Interaction between the frontend and the backend

**Alternatives:** REST + OpenAPI, GraphQL, gRPC (via gRPC-Web).

| Criterion | Driver | REST + OpenAPI | GraphQL | gRPC-Web |
|---|---|---|---|---|
| Works directly from the browser | D6 | **High** — plain HTTP + JSON | **High** — HTTP | **Low** — requires a special proxy between the browser and the gRPC service [R8] |
| Implementation and debugging effort | D7 | **High** — simple, widely supported tooling | **Medium** — schema, resolvers and query-complexity control | **Medium** — code generation and proxy setup |
| Explicit API contract and documentation | D7 | **High** — OpenAPI specification [R9] | **High** — schema [R10] | **High** — Protocol Buffers |
| HTTP caching of public pages (catalog, course pages) | D6 | **High** — standard caching of `GET` requests | **Low** — queries are commonly sent as `POST` to a single endpoint | **Low** |
| Flexible client-side queries | — | **Medium** | **High** | **Medium** |

**Decision: REST with an OpenAPI specification.** The main client is a browser (D6), the API is mostly resource-oriented (courses, lessons, enrolments, reviews), and the team needs a simple, well-documented contract that both members can work against in parallel (D7). The specification will be kept in `backend/api/openapi.yaml`. GraphQL's query flexibility is not needed for this domain and adds complexity; gRPC is better suited for service-to-service communication and requires a proxy for browsers.

## 7. Decision 4 — Frontend framework

**Alternatives:** React with Next.js, Vue with Nuxt, Angular.

| Criterion | Driver | React + Next.js | Vue + Nuxt | Angular |
|---|---|---|---|---|
| Server-side rendering for public catalog and course pages | D6 | **High** — server rendering and Server Components [R11] | **High** — server rendering | **High** — server rendering supported |
| Adoption among developers (indicator of available libraries and learning materials) | D6, D7 | **High** — React 44.7%, Next.js 20.8% of respondents [R13] | **Medium** — Vue.js 17.6%, Nuxt 4% [R13] | **Medium** — Angular 18.2% [R13] |
| Learning and development effort | D7 | **Medium** | **High** | **Low** — more concepts and boilerplate |
| TypeScript support | D2 | **High** | **High** | **High** |

**Decision: React with Next.js.** The public catalog and course pages benefit from server-side rendering (D6), and React is the most widely used web framework among the three (44.7% of respondents in the Stack Overflow Developer Survey 2025 [R13]), which means more ready components and learning materials for the features in scope, such as video players, forms and internationalisation for English and Russian. Vue with Nuxt is a reasonable alternative with a lower learning curve; the team selected React and Next.js. Angular was rejected because of higher development effort for a two-person team.

## 8. Decision 5 — Backend architecture style

**Alternatives:** modular monolith, microservices.

| Criterion | Driver | Modular monolith | Microservices |
|---|---|---|---|
| Development and deployment effort for a team of two | D7 | **High** — one application, one deployment | **Low** — several services, inter-service communication, separate deployments |
| Consistency of the event chain (progress → XP → streak → achievements) | D1 | **High** — one database transaction | **Medium** — requires distributed coordination between services |
| Clear boundaries between features | — | **High** — separate modules with defined interfaces | **High** — separate services |
| Independent scaling of components | — | **Medium** — the whole application is scaled | **High** |

**Decision: modular monolith.** The backend is one application divided into modules with clear boundaries (auth, catalog, course, quiz, enrolment, payment, learning, gamification, notification and others), as already reflected in `backend/internal/`. This keeps the gamification event chain inside one transaction (D1) and keeps development and deployment manageable for two people (D7). This follows the common recommendation to start with a monolith and extract services only when boundaries are well understood [R12]. Independent scaling is not required for the expected scale of a diploma project.

## 9. Selected stack

| Area | Selected technology |
|---|---|
| Server platform | Go |
| Data storage | PostgreSQL |
| Frontend–backend interaction | REST API with OpenAPI specification |
| Frontend | React + Next.js (TypeScript) |
| Architecture | Modular monolith |

**Related constraints from the proposal**
- Payments work only in test mode (simulated payments in USD); no external payment gateway is compared.
- The approach to video storage and delivery will be decided during design.

**Traceability: drivers → decisions**

| Driver | Covered by |
|---|---|
| D1 Event chain | Go, PostgreSQL, modular monolith |
| D2 Relational domain | PostgreSQL, Go |
| D3 Data-driven achievements | PostgreSQL (`jsonb`) |
| D4 Leaderboards | PostgreSQL (window functions), Go |
| D5 Time-zone-aware streaks | Implemented in the backend; time zone stored per student |
| D6 Public pages, EN/RU interface | Next.js, REST |
| D7 Team of two, fixed timeline | Go, REST + OpenAPI, modular monolith |

## 10. Limitations

- Ratings are qualitative and based on documentation, not on benchmarks run for this project.
- The decisions may be revisited after the requirements specification and the performance tests described in the verification and evaluation plan.

## 11. References

Accessed on 20 October 2026.

- [R1] The Go Authors. *Effective Go — Concurrency*. https://go.dev/doc/effective_go#concurrency
- [R2] OpenJS Foundation. *The Node.js Event Loop*. https://nodejs.org/en/learn/asynchronous-work/event-loop-timers-and-nexttick
- [R3] PostgreSQL Global Development Group. *JSON Types* (PostgreSQL documentation). https://www.postgresql.org/docs/current/datatype-json.html
- [R4] Oracle. *The JSON Data Type* (MySQL 8.0 Reference Manual). https://dev.mysql.com/doc/refman/8.0/en/json.html
- [R5] PostgreSQL Global Development Group. *Window Functions* (PostgreSQL tutorial). https://www.postgresql.org/docs/current/tutorial-window.html
- [R6] MongoDB. *Transactions* (MongoDB Manual). https://www.mongodb.com/docs/manual/core/transactions/
- [R7] Oracle. *Window Functions* (MySQL 8.0 Reference Manual). https://dev.mysql.com/doc/refman/8.0/en/window-functions.html
- [R8] gRPC Authors. *gRPC-Web* (README). https://github.com/grpc/grpc-web
- [R9] OpenAPI Initiative. *OpenAPI Specification*. https://spec.openapis.org/oas/latest.html
- [R10] The GraphQL Foundation. *Learn GraphQL*. https://graphql.org/learn/
- [R11] Vercel. *Next.js Documentation*. https://nextjs.org/docs
- [R12] Fowler, M. (2015, June 3). *Monolith First*. https://martinfowler.com/bliki/MonolithFirst.html
- [R13] Stack Overflow. *2025 Developer Survey — Technology: Web frameworks and technologies*. https://survey.stackoverflow.co/2025/technology
