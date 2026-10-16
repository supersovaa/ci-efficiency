---
name: test-scope-structure-review
description: Assess costly or unusually broad test execution and suggest responsibility separation when it could narrow necessary verification.
---

# Test Scope Structure Review

Use this skill when test execution is costly or unusually broad and a responsibility split might narrow the necessary verification.

Identify whether the testing burden arises from necessary integration guarantees or from responsibilities that could be verified independently.
When separating responsibilities could reduce the necessary test scope, suggest considering a split and explain the expected testing benefit.
Treat a heavy test run as a prompt for consideration, not a reason to require splitting. Preserve necessary integration verification.

Leave crate or package boundaries, dependency design, and implementation to the relevant structure-design workflow, such as `responsibility-driven-crates` for Rust.
Required test evidence belongs to `requirement-driven-testing`; CI execution configuration belongs to `ci-execution-efficiency`.
