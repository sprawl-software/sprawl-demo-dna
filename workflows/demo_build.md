---
name: "Deterministic Verification Build"
type: "workflow"
domain: "engineering"
version: "1.0.0"
description: "Standard execution recipe for validating workspace health, running test suites, and auditing rule boundaries."
activation: "manual"
tags: ["workflow", "build", "verification", "ci"]
---

# 📋 Deterministic Verification Build Workflow

<!-- 
SPRAWL WORKFLOW: Workflows provide deterministic, step-by-step checklists for AI agents.
Instead of allowing the model to hallucinate a build process, it follows this exact verification recipe.
-->

## 1. Overview & Objective
This workflow defines the mandatory sequence for verifying repository integrity, testing code changes, and confirming that no security boundaries were violated during the session.

## 2. Execution Recipe

When triggered to run the verification build, perform these steps sequentially:

### Step 1: Workstation Health & Governance Audit
1. Verify that the workspace root contains `.agents/` and active governance rules.
2. Confirm that no protected credential files (`.env`, `*.pem`, `id_rsa`) were created, modified, or staged for commit.

### Step 2: Code Quality & Constraint Check
1. If Python files were modified, verify compliance with `rules/python_stdlib_only.md` (zero external pip packages introduced).
2. Check that strict type hinting is present on all new public functions and classes.
3. Run code formatting and lint verification commands appropriate for the project.

### Step 3: Test Execution
1. Execute the project's native test suite (e.g. `python3 -m unittest discover tests`).
2. Verify that all test cases pass with an exit code of `0`.
3. If any test fails, halt the build and output the exact stack trace for remediation.

### Step 4: Deterministic Summary
Output a clean, formatted Markdown status table:
- **Governance Audit**: Passed / Failed
- **Protected Files Check**: Clean (No credentials touched)
- **Test Suite Results**: N tests passed, 0 failures
- **Build Status**: Verified & Ready for Git Commit
