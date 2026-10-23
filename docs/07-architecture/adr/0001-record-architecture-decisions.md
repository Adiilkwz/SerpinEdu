# ADR-0001: Record architecture decisions

- **Status:** Accepted
- **Date:** 22.10.2026

## Context

Architecture decisions are made over the whole diploma project by a team of two. Reviewers and the team itself need to know later why a decision was made and which alternatives were considered.

## Decision

Every significant architecture decision is recorded as a short architecture decision record (ADR) in `docs/07-architecture/adr/`. Each ADR has a number, a title, a status (Proposed, Accepted, Superseded), a date, the context, the decision and its consequences. An accepted ADR is not rewritten; a changed decision gets a new ADR that supersedes the old one.

## Consequences

- The reasons for decisions stay in the repository next to the code and are reviewed in pull requests.
- The architecture description (section 10) lists all ADRs.
