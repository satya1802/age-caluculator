<!-- sdlc:auto:start adr -->
# ADR-0003: Use PostgreSQL 16 for Database

Status: Accepted  
Date: 2026-11-05

## Context and Problem Statement

Which Database technology does the project use? Decided in architecture v1.

## Considered Options

- PostgreSQL 16
- SQLite
- MySQL

## Decision Outcome

Chosen option: PostgreSQL 16, because A database layer is required by the platform; PostgreSQL 16 is the default and is provisioned ready to hold future anonymous usage counts, though it stays empty because no personal data is stored.

## Consequences

Pure overhead for the current scope since nothing is persisted, but it avoids a migration later if anonymous metrics are added.
<!-- sdlc:auto:end adr -->