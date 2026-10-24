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

Use `test-evidence-planning` to determine required test evidence and `test-evidence-implementation` to consolidate or retire tests; this skill selects when and where to execute the required evidence.

## Reuse compatible execution environments

Before introducing or migrating CI, inspect the actual runners' OS, architecture, capacity, concurrency, installed tools and dependencies, and shared build/cache paths. Surface missing setup facts and choices to the user at this stage, before settling the recurring workflow.
Provision and verify compatible environments during initial setup and when their requirements change. Reuse installed toolchains and dependencies on persistent runners; use prepared images or caches for disposable runners. Keep routine jobs focused on required tests and isolated or reset per-run mutable state.
When investigating CI slowness, distinguish queue time, environment preparation, builds, and test execution before changing test coverage or adding recurring checks.

## Hand off structural pressure

When necessary test execution remains costly or broad because of coupling, use `test-scope-structure-review` to consider whether responsibility separation could help.

This skill owns CI execution selection, workflow simplicity, and compatible environment reuse. Structural design and test-evidence definition remain with their respective owners.
