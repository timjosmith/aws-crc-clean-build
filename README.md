# aws-crc-clean-build

Clean, self-contained Cloud Resume Challenge implementation using AWS CloudFormation and GitHub Actions with OIDC.  Demonstrates reproducible deployment of a small serverless architecture, focusing on Infrastructure as Code, CI/CD, and safe destroy-and-rebuild workflows.

## Purpose
This repository is a clean, self-contained implementation of the Cloud Resume Challenge.  It demonstrates practical AWS delivery using CloudFormation and GitHub Actions with OIDC-based authentication.

The project provisions a small serverless AWS stack that is fully destroyable and redeployable without manual intervention.  It is intentionally isolated from existing live infrastructure and is not intended to replace a production website. 

The live site includes an additional Lambda-backed contact form. This demonstration stack instead focuses on a minimal dynamic element (visitor counter) in order to keep the architecture intentionally simple and reviewable.

## Scope (intentional)
- Single environment
- Infrastructure as Code using CloudFormation
- CI/CD via GitHub Actions with OIDC
- Short-lived credentials only
- Safe destroy-and-rebuild workflow

## Out of scope
- Reuse of existing production resources
- Multi-environment deployment
- Feature parity with live site
- Advanced security hardening or optimisation

## Current status
See `STATUS.md` for the current deployment state and known limitations.

## Notes
This repository is a demonstration artefact created for learning and assessment purposes.  It prioritises clarity, safety, and reproducibility over completeness.
