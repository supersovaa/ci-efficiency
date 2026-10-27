# CI Efficiency

Two lightweight skills for keeping CI verification proportional to the change and prompting structural review when tests are unnecessarily broad.

## Core idea

Keep the execution environment premises in one repository file, use them as the starting point for CI work, and separate environment preparation and updates from normal verification runs. Execute the required checks through a directly understandable workflow.
Precise test selection and simple CI structure are joint requirements. Evaluate recurring work and complexity across the environment, workflow, and supporting execution mechanisms together, including tests collected automatically by unchanged workflows.
When necessary execution remains costly or broad because of product coupling, consider whether independent responsibilities could be separated; leave the actual structure design to its owner.

## Skills and when to use

- `ci-execution-efficiency` — Use when designing, changing, or reviewing CI execution, including tests added to CI-collected suites, affected-test selection, workflow configuration, or runner-environment reuse.
- `test-scope-structure-review` — Use when reviewing costly or unusually broad test execution for possible structural improvements.

Both skills apply across languages and CI services, independently or together.

## Responsibility boundaries

`ci-execution-efficiency` owns CI test selection, recurring execution cost, workflow simplicity, and compatible environment reuse, including the boundary between environment maintenance and normal verification runs.
`test-scope-structure-review` suggests considering responsibility separation when that could reduce necessary test scope. Product structure design and implementation belong to the relevant structure-design workflow.

[`requirement-driven-testing`](https://github.com/supersovaa/requirement-driven-testing) owns deciding, establishing, and preserving necessary test evidence.
Language-specific structure design belongs to its respective owner, such as [`responsibility-driven-crates`](https://github.com/supersovaa/responsibility-driven-crates) for Rust.

## Installation

Install `skills/execution` and `skills/structure-review` as separate skill directories in an agent environment that supports `SKILL.md` skills, keeping each `SKILL.md` at its skill directory root.
Install either skill independently when only its responsibility is needed.

## Files

- `skills/execution/SKILL.md` — `ci-execution-efficiency`.
- `skills/structure-review/SKILL.md` — `test-scope-structure-review`.
- `LICENSE` — MIT License.
