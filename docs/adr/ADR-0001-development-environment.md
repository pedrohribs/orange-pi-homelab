# ADR-0001: Development Environment

## Status

Accepted

## Context

A consistent development environment is required before the infrastructure project can begin.

## Decision

Use Windows 11 as the development workstation with:

- Git
- GitHub CLI
- VS Code
- Docker Desktop
- PowerShell

## Rationale

Preparing the development environment first allows every future change to be versioned, documented and tested before being deployed to the Orange Pi.

## Consequences

### Positive

- Reproducible workflow
- Version-controlled project
- Early documentation
- Local Docker testing

### Negative

- Initial setup requires additional time before any infrastructure is deployed.