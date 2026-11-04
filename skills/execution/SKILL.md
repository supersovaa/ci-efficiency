---
name: ci-execution-efficiency
description: Design, change, or review CI test execution, affected-test selection, workflow configuration, runner-environment reuse, and recurring cost from automatically collected tests across languages and CI services.
---

# CI Execution Efficiency

Use this skill when designing, changing, or reviewing CI execution, including tests added to suites that existing workflows automatically collect, affected-test selection, workflow configuration, or runner-environment reuse.

Treat required verification and a simple execution structure as joint requirements. Use settled test evidence and existing verification commands as inputs.

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

Minimize recurring test execution while preserving required verification and keeping CI dispatch simple. First use the test runner's or build tool's built-in changed/affected-test selection, filtering, and existing test-group boundaries when available and reliable. Prefer those existing capabilities over creating CI-specific selection logic.
When built-in affected-test selection is unavailable, select a small set of existing packages, crates, suites, or verification commands using simple common rules. Use broader existing suites when finer selection would cost more to maintain than it saves. Account for integration and shared-contract checks when selecting the necessary scope.
Prohibit per-file, per-directory, per-component, or per-change-type lookup tables that enumerate corresponding checks, including equivalent lists embedded in scripts or generated from separately maintained mappings. Avoid custom dependency analysis and change-impact dispatch solely to narrow CI execution.
Choose a small number of understandable jobs from existing execution boundaries. Evaluate the number of tests and recurring runtime alongside configuration complexity and maintenance effort; favor selection that demonstrably reduces repeated work with little added machinery.

When adding or modifying tests, trace whether existing CI discovery and runner commands automatically execute them, including when workflow files stay unchanged. Evaluate additional recurring runtime and resource use across applicable triggers, overlapping existing evidence, and the affected scope that needs the checks. Preserve continuing guarantees; route test-retention and consolidation decisions to `test-evidence-planning` and `test-evidence-implementation`.

Keep dispatch direct: invoke built-in test selection or existing verification commands from CI. Review added conditions, helpers, and special cases against built-in selection and simple suite-level execution.

## Keep the execution structure direct

Choose job boundaries for required environments, isolation, sequencing, or useful parallelism within actual runner capacity.
When jobs share an execution contract, reuse the existing command or workflow step directly.
Compare proposed jobs, flags, branches, helpers, and reuse mechanisms with direct use of existing commands. Choose the simplest whole-path structure that preserves required verification, environment compatibility, and result propagation.

Evaluate workflow configuration, called scripts/actions, environment preparation, state coordination, and supporting checks together. Consolidate repeated work where equivalent required verification remains. Prefer existing mechanisms and straightforward workflow rules.
Keep triggers, job responsibilities, dependencies, environment choice, and verification commands directly understandable from the workflow. Let the executable structure express the execution behavior.

## Verify actual selection and recurring work

Use available run evidence to compare selected test counts and recurring execution cost with broader runs. Check representative affected, unrelated, and mixed changes, including tests automatically collected by unchanged workflows; trace selection, job/step conditions, preparation, and results.
Confirm that execution matches the recorded environment premises, required checks execute, unrelated tests are omitted when safely selectable, compatible environments are reused, and selection, preparation, or verification failures remain visible in the overall result.
Distinguish observed execution from predictions and state any remaining validation needs.

When investigating slowness, distinguish queue time, environment preparation, builds, and test execution before choosing a change.
Treat substantially unnecessary recurring preparation or unrelated execution, including redundant tests automatically selected by unchanged workflows, and complexity that materially defeats the change's goal, as material review findings even when checks pass.

## Responsibility boundary

This skill owns CI execution selection, recurring execution cost, workflow simplicity, and compatible environment reuse.
Use `test-evidence-planning` to determine required test evidence and `test-evidence-implementation` to consolidate or retire tests.
When necessary execution remains costly or broad because of product coupling, use `test-scope-structure-review` to consider responsibility separation; product structure design belongs to its owning workflow.
