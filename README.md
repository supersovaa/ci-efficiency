# CI Efficiency

Two lightweight skills for keeping CI verification proportional to the change and prompting structural review when tests are unnecessarily broad.

## Core idea

Preserve required test evidence, select the execution affected by a change, and reuse compatible execution environments while keeping CI configuration simple.
When tests remain costly or broad, consider whether independent responsibilities could be separated; leave the actual structure design to its owner.

## Skills and when to use

- `ci-execution-efficiency` — Use when designing, changing, or reviewing CI test execution, affected-test selection, workflow configuration, or runner-environment reuse.
- `test-scope-structure-review` — Use when test execution is costly or unusually broad and a responsibility split might narrow the necessary verification.

Both skills apply across languages and CI services, independently or together.

## Responsibility boundaries

`ci-execution-efficiency` owns CI test selection, workflow simplicity, and compatible environment reuse.
`test-scope-structure-review` suggests considering responsibility separation when that could reduce necessary test scope; it does not design or implement the split.

[`requirement-driven-testing`](https://github.com/supersovaa/requirement-driven-testing) owns deciding, establishing, and preserving necessary test evidence.
Language-specific structure design belongs to its respective owner, such as [`responsibility-driven-crates`](https://github.com/supersovaa/responsibility-driven-crates) for Rust.

## Installation

Install `skills/execution` and `skills/structure-review` as separate skill directories in an agent environment that supports `SKILL.md` skills, keeping each `SKILL.md` at its skill directory root.
Install either skill independently when only its responsibility is needed.

## Files

- `skills/execution/SKILL.md` — `ci-execution-efficiency`.
- `skills/structure-review/SKILL.md` — `test-scope-structure-review`.
- `LICENSE` — MIT License.
