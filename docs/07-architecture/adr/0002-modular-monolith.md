# ADR-0002: Modular monolith with Go, PostgreSQL, REST and Next.js

- **Status:** Accepted
- **Date:** 22.10.2026

## Context

The technology comparison (`docs/05-technology-comparison/technology-comparison.md`) evaluated alternatives for the server platform, data storage, frontend–backend interaction, frontend framework and backend architecture style against drivers D1–D7. One learning event must update several parts of the system consistently (D1), and the team has two developers (D7).

## Decision

- The backend is one Go application divided into modules in `backend/internal/`, one per business area.
- Data is stored in PostgreSQL.
- The frontend is a React application built with Next.js (TypeScript).
- The frontend and the backend communicate through a REST API described in `backend/api/openapi.yaml`.
- Modules call each other only through their public Go interfaces and do not write to each other's tables (NFR-MNT-01).

## Consequences

- A learning event can be processed in one database transaction (ADR-0003).
- One deployable backend is simpler to build, test and run for a team of two.
- Modules cannot be scaled separately; this is not needed at the scale of the project (NFR-CAP-01).
- Module boundaries must be kept by code review, because the compiler does not prevent a module from using another module's internals.
