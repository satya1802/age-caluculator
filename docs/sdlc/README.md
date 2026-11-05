# Age caluculator — SDLC Documentation

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start overview -->
Build an age calculator app

**Documentation version:** v3
<!-- sdlc:auto:end overview -->

## Contents

<!-- sdlc:auto:start contents -->
| Document | State |
|---|---|
| [Requirements](requirements/README.md) | v1 approved |
| [Architecture](architecture/README.md) | 13 entries |
| [Development](development/README.md) | 11 entries |
| [Testing](testing/README.md) | 1 entry |
| [Deployment](deployment/README.md) | 1 entry |
| [Maintenance](maintenance/README.md) | 1 entry |
| [Data model](architecture/data-model.md) | generated |
| [API (OpenAPI)](architecture/api/openapi.yaml) | generated |
| [Decisions (ADRs)](architecture/adr/README.md) | 4 decisions |
| [Sprint plan](development/sprint-plan.md) | 1 sprint |
| [Developer guide](development/developer-guide.md) | generated |
| [API reference](development/api-reference.md) | 1 route |
| [Test report](testing/test-report.md) | not run yet |
| [Tests](testing/test-cases.md) | 0 tests |
| [Deployment guide](deployment/deployment-guide.md) | not deployed yet |
| [Runbook](deployment/runbook.md) | not deployed yet |
| [Release notes](deployment/release-notes.md) | 0 releases |
| [Traceability matrix](traceability-matrix.md) | 8 requirements |
| [Changelog](CHANGELOG.md) | 3 versions |
<!-- sdlc:auto:end contents -->

## Open gaps

<!-- sdlc:auto:start open-gaps -->
### Requirements

- pgvector is listed as an approved runtime service but nothing in the functional or non-functional requirements uses a vector store -- purpose is unclear and should be confirmed with the product owner.
- No stated rationale ties PostgreSQL/pgvector usage to any in-scope capability; the requirements text itself says the database 'will sit empty.'
- No architecture or implementation detail yet confirms the mechanism (e.g. in-memory only, no cookies/localStorage) used to guarantee non-retention.

### Architecture

- Input does not state which requirement IDs (US-001..US-008) this architecture satisfies -- explicit traceability from requirements to architecture is missing and should be confirmed with the requirements author.
- No schema, tables, or migration plan defined yet since the database is intentionally empty in this version -- flag if/when future anonymous usage-count feature is scoped.
- No explicit requirement ID link provided in input; likely maps to a core 'calculate age' requirement but this is not confirmed.
- No explicit requirement ID link provided in input; likely maps to a validation/error-handling requirement but this is not confirmed.
- Request/response schema and auth requirements for this endpoint are not specified in the input.
- Input does not clarify when/whether the frontend actually calls this endpoint versus relying solely on client-side validation -- this should be confirmed during development.

### Development

- No ticket status data provided for any item in Sprint 1 -- cannot confirm what, if anything, has been implemented.
- No commits, PRs, or code artifacts referenced.
- No developer notes or implementation decisions provided.
- No development status reported for this epic or its child stories.
- No development execution status (not started / in progress / done) provided for this story.
- No code or UI implementation details available to document.
- No development execution status provided for this story.
- No details on the calculation logic or algorithm actually implemented.
- No details on the result display format actually implemented.
- No details on the specific error message or validation logic actually implemented.
- No details on how/whether data non-retention was actually implemented (e.g. no backend storage, no local storage persistence) -- cannot confirm this was built as specified.
- No details on breakpoints, layout, or responsive implementation actually built.

### Testing

- Testing phase has not started; no test plans or results exist yet to verify any acceptance criteria (AC-001 through AC-016).

### Deployment

- No deployment recorded yet; nothing to document about hosting on AWS or release of the React/FastAPI application.

### Maintenance

- No maintenance phase has begun; nothing to document because no deployment has occurred.
<!-- sdlc:auto:end open-gaps -->
