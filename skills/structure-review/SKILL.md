---
name: test-scope-structure-review
description: Review expensive or broad tests, or code organization, for opportunities to narrow necessary verification through responsibility separation.
---

# Test Scope Structure Review

Use this skill when reviewing expensive or broad tests, or reviewing code organization for opportunities to reduce the scope of required verification.

Identify whether the testing burden arises from necessary integration guarantees or from responsibilities that could be verified independently.
When separating responsibilities could reduce the necessary test scope, suggest considering a split and explain the expected testing benefit.
Treat a heavy test run as a prompt for consideration, not a reason to require splitting. Preserve necessary integration verification.

Leave crate or package boundaries, dependency design, and implementation to the relevant structure-design workflow, such as `responsibility-driven-crates` for Rust.
Required test evidence belongs to `requirement-driven-testing`; CI execution configuration belongs to `ci-execution-efficiency`.
