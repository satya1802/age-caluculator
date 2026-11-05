# Deployment Guide

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start how-it-deploys -->
Pushes to `main` run `.github/workflows/deploy.yml`, which builds the API image (if there is a backend) and deploys the SPA to AWS Amplify. Commits touching only `docs/sdlc/**` don't deploy. Deployments can also be started from the platform's Deployment tab.
<!-- sdlc:auto:end how-it-deploys -->

<!-- sdlc:auto:start environments -->
| Name | Service | Runtime | Scaling | Environment |
|---|---|---|---|---|
| SPA Static Hosting | AWS S3 + CloudFront | Static assets (React 19 build) | CDN edge caching, absorbs traffic spikes | dev |
| API Service | FastAPI container | FastAPI 0.115 on Python | Single small instance, horizontally scalable | dev |
| Database | AWS RDS for PostgreSQL | PostgreSQL 16 with pgvector | Single small instance (empty in this version) | dev |
<!-- sdlc:auto:end environments -->

<!-- sdlc:auto:start live -->
_Not deployed yet._
<!-- sdlc:auto:end live -->

<!-- sdlc:auto:start topology -->
```mermaid
graph LR
  n_SPA_Static_Hosting["SPA Static Hosting<br/>AWS S3 + CloudFront"]
  n_API_Service["API Service<br/>FastAPI container"]
  n_Database["Database<br/>AWS RDS for PostgreSQL"]
  n_SPA_Static_Hosting -->|"HTTPS"| n_API_Service
  n_API_Service -->|"TCP/TLS"| n_Database
```
<!-- sdlc:auto:end topology -->
