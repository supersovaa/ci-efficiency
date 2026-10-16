---
name: ci-execution-efficiency
description: Design, change, or review CI test execution, affected-test selection, workflow configuration, and runner-environment reuse across languages and CI services.
---

# CI Execution Efficiency

Use this skill when designing, changing, or reviewing CI test execution, affected-test selection, workflow configuration, or runner-environment reuse.

## Select sufficient execution

1. Inspect the existing CI and the required test evidence established by the repository.
2. Determine affected units and checks from changed files, dependencies, public contracts, shared configuration, and integration paths.
3. Select tests for affected units and relevant dependents, preserving required cross-unit verification. Expand the execution scope when the impact cannot be established reliably.
4. Consolidate repeated CI work only when equivalent required verification remains. Prefer existing mechanisms and straightforward workflow rules.

Use `requirement-driven-testing` for decisions about which test evidence is required or whether tests can be consolidated or retired; this skill selects when and where to execute that evidence.

## Reuse compatible execution environments

Reuse installed toolchains and dependencies on persistent runners; use prepared images or caches for disposable runners when available.
Update or rebuild when toolchain, dependency, or environment requirements change or compatibility is uncertain. Manage environment updates explicitly rather than installing unchanged dependencies on every run.
Keep per-run workspaces and mutable state isolated or reset, with reproducible dependencies and safe cache reuse.

## Hand off structural pressure

When necessary test execution remains costly or broad because of coupling, use `test-scope-structure-review` to consider whether responsibility separation could help.

This skill owns CI execution selection, workflow simplicity, and compatible environment reuse. Structural design and test-evidence definition remain with their respective owners.
