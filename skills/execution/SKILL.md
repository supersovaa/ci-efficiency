---
name: ci-execution-efficiency
description: Design, change, or review CI execution, including affected-test selection, workflow configuration, runner-environment reuse, recurring test cost, and CI dependencies imposed on repository verification.
---

# CI Execution Efficiency

Use this skill when designing, changing, or reviewing CI execution, including repository verification coupled to CI-specific configuration, tests automatically collected by existing workflows, affected-test selection, workflow configuration, or runner-environment reuse.

Treat required verification, a simple execution structure, and repository-owned verification interfaces as joint requirements. Use settled test evidence and existing verification commands as inputs.

## Establish execution premises first

At the start of CI design, changes, or review, read the repository's CI environment premises file before choosing jobs or setup steps.
Use an existing file that owns these premises. During CI design or changes, create `ci/environment.md` when needed, consolidate the premises there, and link the file from the repository's CI guidance.
During review, assess the available premises and report material gaps through the surrounding review workflow. Apply file changes only within that workflow's authorized scope.

Record only stable facts that affect execution:

- available runners or images, their selection identifiers, OS, architecture, capacity, and concurrency;
- prepared tools and dependencies, referencing authoritative version declarations and dependency locks;
- reusable build/cache locations, isolation constraints, and the environment preparation/update method and its triggers.

Establish the initial contents from repository, runner, or provider records, resolving material gaps with the user as needed. Distinguish confirmed capabilities from pending preparation and confirm readiness before execution relies on it.
On later work, reuse applicable recorded facts and recheck premises affected by the change or conflicting evidence. Update the record as part of changes to the environment or its authoritative declarations.
Keep this file focused on external execution premises; express job and test-selection behavior in executable configuration.

Separate environment preparation and updates from normal verification runs. Prefer preparing stable tools and dependencies once per compatible environment version and making CI consume that environment.
Reuse installed tools and dependencies on persistent runners; use suitable prepared images or caches on disposable runners. Start provider-hosted environments from the provider's documented image capabilities.
Use existing version declarations and dependency locks to identify compatibility and the conditions for rebuilding or updating the environment. Assign updates explicitly to environment maintenance; keep per-run preparation limited to work required by changed inputs or the actual runner lifecycle.
Keep per-run workspaces and mutable state isolated or reset, with reproducible dependencies and cache/build reuse compatible with the inputs and concurrent access.

## Select required execution

Determine affected checks from changed responsibilities, dependencies, public contracts, shared configuration, and integration paths. Use authoritative build and test metadata; keep any additional stable selection mapping in one place.
Select checks for affected units and relevant dependents, preserving required cross-unit verification. Combine selections for mixed changes. Investigate uncertain dependencies and choose a bounded set covering the affected guarantees.
Reserve full-suite runs for explicit verification requirements or deliberate scheduled/manual execution. For single-developer projects, prioritize fast feedback and runner capacity within the required verification boundary.

When adding or modifying tests, trace whether existing CI discovery and runner commands automatically execute them, including when workflow files stay unchanged. Evaluate additional recurring runtime and resource use across applicable triggers, overlapping existing evidence, and the affected scope that needs the checks. Preserve continuing guarantees; route test-retention and consolidation decisions to `test-evidence-planning` and `test-evidence-implementation`.

Preserve the required selection while simplifying its dispatch. Use common selection rules and existing test commands to achieve both precise execution and simple configuration.

## Keep repository verification independent of CI

Use repository-owned verification commands or standard tooling commands as the interface consumed by CI. Keep those commands invocable outside the CI service through documented inputs and environment prerequisites, including checks requiring a specific OS or hardware.

Keep CI-specific triggers, selection controls, job metadata, environment variables, runner paths, and result publication within CI orchestration. Pass required check selection and environment settings to verification commands as explicit inputs. Let product structure and test definitions follow their owning requirements rather than CI dispatch convenience.

When a CI improvement calls for changing source or test organization, route the design or test-evidence decision to its owning workflow, then adapt CI to the resulting verification interface.

## Keep the execution structure direct

Choose job boundaries for required environments, isolation, sequencing, or useful parallelism within actual runner capacity.
When targets share an execution contract, pass the selected targets as inputs to common execution. Keep selection decisions at their owning boundary and make downstream jobs consume the result directly.
Compare proposed jobs, flags, branches, helpers, and reuse mechanisms with direct use of existing commands. Choose the simplest whole-path structure that preserves the required selection, environment compatibility, and result propagation.

Evaluate workflow configuration, called scripts/actions, environment preparation, state coordination, and supporting checks together. Consolidate repeated work where equivalent required verification remains. Prefer existing mechanisms and straightforward workflow rules.
Keep triggers, job responsibilities, dependencies, environment choice, and verification commands directly understandable from the workflow. Let the executable structure express the execution behavior.

## Verify actual selection and recurring work

Use focused checks and available run evidence to trace representative affected, unrelated, and mixed changes, including tests automatically collected by unchanged workflows, through selection, job/step conditions, preparation, and results.
Confirm that execution matches the recorded environment premises, repository verification commands retain documented independent invocation, required checks execute, unrelated checks are excluded, compatible environments are reused, and selection, preparation, or verification failures remain visible in the overall result.
Distinguish observed execution from predictions and state any remaining validation needs.

When investigating slowness, distinguish queue time, environment preparation, builds, and test execution before choosing a change.
Treat substantially unnecessary recurring preparation or unrelated execution, including redundant tests automatically selected by unchanged workflows, and complexity that materially defeats the change's goal, as material review findings even when checks pass.

## Responsibility boundary

This skill owns CI execution selection, recurring execution cost, workflow simplicity, compatible environment reuse, and the boundary between CI orchestration and repository verification.
Use `test-evidence-planning` to determine required test evidence and `test-evidence-implementation` to consolidate or retire tests.
When necessary execution remains costly or broad because of product coupling, use `test-scope-structure-review` to consider responsibility separation; product structure design belongs to its owning workflow.
