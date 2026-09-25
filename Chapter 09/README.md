# Deployment Pipelines and Governance

## Overview

This folder contains the companion resources for Chapter 9 of *Learning Microsoft Power Automate*.

The chapter focuses on moving Power Platform solutions safely across environments and applying governance practices that keep enterprise automation controlled, supportable, and auditable.

## What You Will Learn

By completing this chapter, you will learn how to:

- Structure development, test, and production environments.
- Package and manage Power Platform solutions.
- Promote changes through deployment pipelines.
- Prepare and validate releases.
- Apply governance controls for enterprise automation.
- Manage ownership, access, dependencies, and lifecycle decisions.

## Recommended Learning Order

```text
Environment Strategy
        ↓
Solution Management
        ↓
Deployment Pipelines
        ↓
Release Management
        ↓
Governance
```

## Repository Structure

```text
Chapter09-Deployment-Pipelines-Governance/
├── README.md
├── DeploymentPipelines/
│   └── README.md
├── EnvironmentStrategy/
│   └── README.md
├── Governance/
│   └── README.md
├── SolutionManagement/
│   └── README.md
├── ReleaseManagement/
│   └── README.md
├── CloudFlows/
└── JSON/
```

## Prerequisites

Before working through the chapter, make sure you have:

- Access to Microsoft Power Automate and the Power Platform environment used by the exercises.
- Appropriate permissions for solution and environment operations used in the chapter.
- Access to any required development, test, and production-style environments.
- Familiarity with basic cloud flows and Power Platform solutions.

> Licensing, environment capabilities, and deployment features can change. Use the latest Microsoft documentation for the requirements that apply to your environment.

## Core Governance Principles

A production-ready automation should have:

- Clear ownership and support responsibility.
- Controlled access to environments and solutions.
- Defined development, testing, and production boundaries.
- Versioned and reviewable changes.
- Dependency awareness before deployment.
- Validation after deployment.
- A recovery or rollback approach appropriate to the process.

## Security Note

Do not commit passwords, API keys, connection secrets, certificates, tokens, or other sensitive values to GitHub. Use approved secrets-management and environment configuration mechanisms.

## Related Resources

- [Deployment Pipelines](DeploymentPipelines/README.md)
- [Environment Strategy](EnvironmentStrategy/README.md)
- [Solution Management](SolutionManagement/README.md)
- [Release Management](ReleaseManagement/README.md)
- [Governance](Governance/README.md)

## Notes

The child folders provide focused companion material for the corresponding Chapter 9 sections. Additional flow assets and JSON examples can be added under `CloudFlows/` and `JSON/` as the chapter exercises are finalized.