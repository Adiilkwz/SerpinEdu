# ADR-0005: Store files in S3-compatible object storage (MinIO)

- **Status:** Accepted
- **Date:** 22.10.2026

## Context

Besides videos (ADR-0004), the system stores course covers (FR-AUT-02), lesson attachments and generated PDF certificates (FR-LRN-09). Both the API application and the worker need access to these files.

## Decision

Files are stored in an S3-compatible object storage. MinIO runs as a container in the local environment. The database stores only the object key of each file. The `platform/storage` component uploads files and issues temporary download links after an access check.

## Consequences

- The API and the worker share files without a shared disk.
- The same code can later work with any S3-compatible service.
- One more container has to run locally; it is started together with the others by Docker Compose (NFR-POR-02).
- The `S3_*` variables in `.env.example` are used for this storage.
