---
name: "Engineering Core Alignment"
type: "rule"
domain: "engineering"
version: "2026.10.1"
description: "Standard software engineering principles, double-diamond planning artifacts, atomic limits, and verification workflows."
activation: "model_decision"
globs:
  - "**/*.{py,js,ts,go,rs,cpp,c,h,sh}"
  - "**/package.json"
  - "**/requirements.txt"
  - "**/pyproject.toml"
  - "**/Cargo.toml"
alwaysApply: false
---

# ENGINEERING ALIGNMENT PROTOCOLS

## 1. Execution & Lifecycle

All codebase modifications and engineering operations must follow a strict, linear pipeline: **Understand -> Plan -> Implement -> Verify -> Finalize**.

- **Double-Diamond Planning**: For non-trivial structural or logical changes, enter Planning Mode before editing code. Maintain three sequential markdown artifacts:
  1. `implementation_plan.md`: Architectural design, proposed file diffs, test strategy, and open questions (requires user approval before code mutation).
  2. `task.md`: Atomic checklist tracking progress with `[ ]` (pending), `[/]` (in-progress), and `[x]` (completed).
  3. `walkthrough.md`: Post-execution summary detailing verified changes, test results, and follow-up notes.
- **Atomic Edits Constraint**: Restrict modifications to a maximum of 5 files per plan to prevent context bloat and logical fragmentation.
- **Diagnostics First**: If encountering an unfamiliar codebase or debugging an issue, execute read-only diagnostic commands before proposing changes.

---

## 2. Architectural Principles

- **Standard Library First**: Prioritize the runtime's standard library before adding external third-party packages or heavy frameworks.
- **Loose Coupling & High Cohesion**: Design modular, isolated components with explicit interfaces. Avoid deep inheritance trees.
- **Zero-Trust Input Validation**: Validate all inputs at domain boundaries using structural type validation (`Pydantic` or standard dataclasses in Python, JSON Schema in JS/TS).
- **Idempotency & Determinism**: Build operations and deployment scripts to be safely repeatable without side effects.

---

## 3. Testing & Verification Gates

- **No Code Without Tests**: Every functional logic change must include unit or integration tests verifying happy path, edge cases, and error handling.
- **Deterministic Execution**: Tests must run fast, in isolation, without depending on live external networks or unmocked third-party APIs.
- **Regression Verification**: Always execute test suites and verify exit code `0` before finalizing any engineering task.
