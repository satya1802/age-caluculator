<!-- sdlc:auto:start adr -->
# ADR-0001: Use React 19 for Frontend

Status: Accepted  
Date: 2026-11-05

## Context and Problem Statement

Which Frontend technology does the project use? Decided in architecture v1.

## Considered Options

- React 19
- Vue
- Svelte

## Decision Outcome

Chosen option: React 19, because The entire product is one screen -- date picker, calculate button, instant result -- and React 19 updates the displayed age in-browser the moment a date is chosen, handles the future-date error state, and renders responsively on mobile and desktop.

## Consequences

Slightly heavier than a vanilla-JS script for such a small app, but aligns with the platform default and keeps future extension straightforward.
<!-- sdlc:auto:end adr -->