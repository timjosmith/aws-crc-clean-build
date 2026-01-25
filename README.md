# aws-crc-clean-build

Clean, self-contained Cloud Resume Challenge implementation using AWS CloudFormation and GitHub Actions with OIDC.  Demonstrates reproducible deployment of a small serverless architecture, with an emphasis on Infrastructure as Code, CI/CD, and safe destroy-and-rebuild workflows.

## Purpose

This repository is a clean, self-contained implementation of the Cloud Resume Challenge.  It demonstrates practical AWS delivery using CloudFormation and GitHub Actions with OIDC-based authentication.

The project provisions a small serverless AWS stack that is fully destroyable and redeployable without manual intervention.  It is intentionally isolated from any existing live infrastructure and is not intended to replace a production website.

The live site includes additional functionality (for example, a Lambda-backed contact form).  This demonstration stack instead focuses on a single minimal dynamic element (a visitor counter), in order to keep the architecture intentionally simple, auditable, and easy to review.

## CI/CD bootstrap approach

To avoid circular IAM dependencies when introducing OIDC-based deployments, the CI/CD pipeline was established using a staged bootstrap pattern.

A temporary bootstrap role with broader permissions was used only to create the initial CloudFormation stack and a new CloudFormation-managed OIDC deploy role.  Once the new role had the minimum permissions required to manage the stack, the workflow was switched to assume it and the bootstrap role was removed.

All long-term deployment permissions are therefore defined and managed exclusively through Infrastructure as Code.  CloudFormation deployments are executed using a dedicated execution role passed from GitHub Actions via `--role-arn`, enforcing a strict deploy-role → execution-role control-plane boundary and avoiding IAM self-mutation.

## Scope (intentional)

- Single environment  
- Infrastructure as Code using CloudFormation  
- CI/CD via GitHub Actions with OIDC  
- Short-lived credentials only  
- Safe destroy-and-rebuild workflow  

## Out of scope

- Reuse of existing production resources  
- Multi-environment deployment  
- Feature parity with the live site  
- Advanced security hardening or optimisation  

## Current status

See `STATUS.md` for the stack’s current deployment state and known limitations.

## Notes

This repository is a demonstration created for learning and assessment purposes.  It prioritises clarity, safety, and reproducibility over completeness.
