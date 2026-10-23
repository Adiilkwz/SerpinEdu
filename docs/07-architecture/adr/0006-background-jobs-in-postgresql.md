# ADR-0006: Run background jobs from a PostgreSQL job table in a worker

- **Status:** Accepted
- **Date:** 22.10.2026

## Context

Some work should not block the user's request: generating PDF certificates (NFR-PERF-04) and sending emails (FR-NOT-02). Such jobs must not be lost if the application restarts, and they must be created only if the business transaction succeeds. Alternatives were: a worker with a PostgreSQL job table, a worker with Redis, and goroutines inside the API process.

## Decision

Jobs are rows in a job table in PostgreSQL. A module writes a job in the same transaction as its business data (`platform/queue`). A separate program, the worker (`backend/cmd/worker`), takes jobs from the table, runs them and retries failed jobs a limited number of times. Redis is not used.

## Consequences

- A job exists only if the business change was committed, and it survives restarts.
- No additional infrastructure: the job table is in the existing database.
- Jobs are not processed instantly; a delay of a few seconds is acceptable for emails and certificates.
- The `REDIS_*` variables are removed from `.env.example`.
