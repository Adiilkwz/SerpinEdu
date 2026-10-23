# ADR-0003: Process learning events synchronously in one transaction

- **Status:** Accepted
- **Date:** 22.10.2026

## Context

Completing a lesson or submitting a test attempt changes course progress, XP, level, streak and achievements, and may complete the course (driver D1). These changes must be all-or-nothing (NFR-REL-01), must not award XP twice (NFR-REL-02), and the student should see the result immediately, within 1 second (NFR-PERF-02).

## Decision

The `learning` module processes a learning event in one database transaction and calls the `gamification`, `certificate` and `notification` modules inside it. Only work that leaves the database (PDF generation, emails) is written as a job to the job table in the same transaction and done later by the worker (ADR-0006). A unique key on the XP source makes a repeated event harmless.

## Consequences

- The response to the student already contains the new XP, level, streak and achievements.
- There is no message broker and no partial state after a failure.
- The transaction becomes longer as more gamification rules are added; NFR-PERF-02 is checked by performance tests.
