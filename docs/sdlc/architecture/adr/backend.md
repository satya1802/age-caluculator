<!-- sdlc:auto:start adr -->
# ADR-0002: Use FastAPI 0.115 for Backend

Status: Accepted  
Date: 2026-11-05

## Context and Problem Statement

Which Backend technology does the project use? Decided in architecture v1.

## Considered Options

- FastAPI 0.115
- Flask
- Express

## Decision Outcome

Chosen option: FastAPI 0.115, because The server does very little -- serving the SPA and optionally validating a date -- and FastAPI 0.115 fills that light role as the platform default without added cost or complexity.

## Consequences

Running a backend at all is near-overhead for a fully in-browser calculator, but it keeps the app on the supported, extensible path.
<!-- sdlc:auto:end adr -->