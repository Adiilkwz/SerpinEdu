# ADR-0007: Update the notification counter by polling

- **Status:** Accepted
- **Date:** 22.10.2026

## Context

Users see in-app notifications with an unread counter (FR-NOT-01). The counter can be kept current by periodic requests (polling) or by a permanent connection (Server-Sent Events or WebSocket).

## Decision

The web application requests the unread counter when a page opens and then every 60 seconds. The interval is a configuration value.

## Consequences

- Only ordinary REST endpoints are needed.
- A new notification can appear with a delay of up to the polling interval.
- With 100 concurrent users (NFR-CAP-02) and a 60-second interval, polling adds about 2 requests per second, which is negligible.
