---
name: ci-execution-efficiency
description: Design, change, or review CI test execution, affected-test selection, workflow configuration, and runner-environment reuse across languages and CI services.
---

# CI Execution Efficiency

Use this skill when designing, changing, or reviewing CI test execution, affected-test selection, workflow configuration, or runner-environment reuse.

## Select sufficient execution

1. Inspect the existing CI and the required test evidence established by the repository.
2. Determine affected units and checks from changed files, dependencies, public contracts, shared configuration, and integration paths.
3. Select tests for affected units and relevant dependents, preserving required cross-unit verification. When impact is uncertain, investigate likely dependencies and select bounded checks; a CI configuration change or uncertainty alone does not justify running every check.
4. Consolidate repeated CI work only when equivalent required verification remains. Prefer existing mechanisms and straightforward workflow rules.

Use `test-evidence-planning` to determine required test evidence and `test-evidence-implementation` to consolidate or retire tests; this skill selects when and where to execute the required evidence.

For single-developer projects, prioritize fast feedback and runner capacity over speculative extra coverage. Reserve full-suite runs for explicit verification requirements or deliberate scheduled/manual execution rather than using them as a fallback.

When reviewing a CI change, inspect the checks and jobs its selection rules would actually run for the proposed change, including unrelated jobs. Treat substantially unnecessary execution that defeats the change's goal or imposes significant recurring cost as a material review finding, even when the checks pass.

## Reuse compatible execution environments

When setting up or migrating self-hosted CI, inspect the actual runners' OS, architecture, capacity, concurrency, installed tools and dependencies, and shared build/cache paths. Resolve missing facts or choices that materially affect setup, placement, or performance with the user at this stage.
For provider-hosted runners, use the provider's documented images and preinstalled tools as the starting point; prepare project-specific dependencies as needed.
Reuse installed toolchains and dependencies on persistent runners; use prepared images or caches for disposable runners when available.
Update or rebuild when toolchain, dependency, or environment requirements change or compatibility is uncertain. Manage environment updates explicitly rather than installing unchanged dependencies on every run.
Keep per-run workspaces and mutable state isolated or reset, with reproducible dependencies and safe cache reuse.
When investigating CI slowness, distinguish queue time, environment preparation, builds, and test execution before changing test coverage or adding recurring checks.

## Hand off structural pressure

When necessary test execution remains costly or broad because of coupling, use `test-scope-structure-review` to consider whether responsibility separation could help.

This skill owns CI execution selection, workflow simplicity, and compatible environment reuse. Structural design and test-evidence definition remain with their respective owners.
