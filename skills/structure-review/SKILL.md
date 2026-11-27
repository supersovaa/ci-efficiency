---
name: test-scope-structure-review
description: Review costly or unusually broad test runs to see whether separating responsibilities could reduce the required verification scope.
---

# Test Scope Structure Review

Identify whether the testing burden arises from necessary integration guarantees or from responsibilities that could be verified independently.
If a split could reduce the required test scope, suggest it and explain which verification it would save. A costly run alone does not justify requiring a split. Preserve necessary integration checks.

Leave crate or package boundaries, dependency design, and implementation to the relevant structure-design workflow, such as `responsibility-driven-crates` for Rust.
Required test evidence belongs to `requirement-driven-testing`; CI execution configuration belongs to `ci-execution-efficiency`.
