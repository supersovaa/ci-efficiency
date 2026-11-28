---
name: test-scope-structure-review
description: Use when reviewing the scope or cost of test execution. Assess whether responsibility boundaries contribute to the testing burden.
---

# Test Scope Structure Review

Apply the structural review below to costly or unusually broad execution. Distinguish necessary integration guarantees from responsibilities that could be verified independently. When a split could reduce the necessary scope, suggest evaluating it and explain the expected saving. Preserve necessary integration checks.

Leave crate or package boundaries, dependency design, and implementation to the relevant structure-design workflow, such as `responsibility-driven-crates` for Rust.
Required test evidence belongs to `requirement-driven-testing`; CI execution configuration belongs to `ci-execution-efficiency`.
