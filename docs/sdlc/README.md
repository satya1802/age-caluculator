# Age caluculator — SDLC Documentation

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start overview -->
Build an age calculator app

**Documentation version:** v1
<!-- sdlc:auto:end overview -->

## Contents

<!-- sdlc:auto:start contents -->
| Document | State |
|---|---|
| [Requirements](requirements/README.md) | v1 approved |
| [Architecture](architecture/README.md) | 1 entry |
| [Development](development/README.md) | 1 entry |
| [Testing](testing/README.md) | 1 entry |
| [Deployment](deployment/README.md) | 1 entry |
| [Maintenance](maintenance/README.md) | 1 entry |
| [Data model](architecture/data-model.md) | not generated yet |
| [API (OpenAPI)](architecture/api/openapi.yaml) | not generated yet |
| [Decisions (ADRs)](architecture/adr/README.md) | 0 decisions |
| [Sprint plan](development/sprint-plan.md) | not generated yet |
| [Developer guide](development/developer-guide.md) | not generated yet |
| [API reference](development/api-reference.md) | 0 routes |
| [Test report](testing/test-report.md) | not run yet |
| [Tests](testing/test-cases.md) | 0 tests |
| [Deployment guide](deployment/deployment-guide.md) | not deployed yet |
| [Runbook](deployment/runbook.md) | not deployed yet |
| [Release notes](deployment/release-notes.md) | 0 releases |
| [Traceability matrix](traceability-matrix.md) | 8 requirements |
| [Changelog](CHANGELOG.md) | 1 version |
<!-- sdlc:auto:end contents -->

## Open gaps

<!-- sdlc:auto:start open-gaps -->
### Requirements

- pgvector is listed as an approved runtime service but nothing in the functional or non-functional requirements uses a vector store -- purpose is unclear and should be confirmed with the product owner.
- No stated rationale ties PostgreSQL/pgvector usage to any in-scope capability; the requirements text itself says the database 'will sit empty.'
- No architecture or implementation detail yet confirms the mechanism (e.g. in-memory only, no cookies/localStorage) used to guarantee non-retention.

### Architecture

- Architecture phase has not started; no design docs, diagrams, screen inventory, or component/technology mapping available.
- No confirmation yet of how the approved stack (especially PostgreSQL/pgvector, which the requirements say will largely sit empty) is actually structured for this lightweight, stateless app.

### Development

- Development phase has not started or no development records have been shared; nothing to document regarding implementation of REQ-001 through REQ-008.

### Testing

- Testing phase has not started; no test plans or results exist yet to verify any acceptance criteria (AC-001 through AC-016).

### Deployment

- No deployment recorded yet; nothing to document about hosting on AWS or release of the React/FastAPI application.

### Maintenance

- No maintenance phase has begun; nothing to document because no deployment has occurred.
<!-- sdlc:auto:end open-gaps -->
