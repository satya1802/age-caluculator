<!-- sdlc:auto:start adr -->
# ADR-0004: Use AWS for Cloud

Status: Accepted  
Date: 2026-11-05

## Context and Problem Statement

Which Cloud technology does the project use? Decided in architecture v1.

## Considered Options

- AWS
- Azure
- GCP

## Decision Outcome

Chosen option: AWS, because A free public utility needs reliable hosting that absorbs traffic spikes cheaply; AWS does this comfortably at this tiny footprint via S3/CloudFront for the SPA and small managed services for the rest.

## Consequences

More services and configuration than a single static host would require, but it keeps the project on the platform default.
<!-- sdlc:auto:end adr -->