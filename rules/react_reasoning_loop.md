---
name: "ReAct Reasoning Loop & Execution Governance"
type: "rule"
domain: "universal"
version: "2026.5.0"
description: "Enforces strict Thought-Action-Pause-Observation reasoning loop logic, atomic execution, and permission gates."
activation: "always_active"
globs: []
alwaysApply: true
---

# ReAct Reasoning Loop & Execution Governance

## 1. Core Reasoning Loop
- **Always** execute exactly one tool call at a time.
- **Always** structure thinking using the explicit ReAct paradigm:
  - **Thought**: Analyze the current state. Read actual files or environment status. Determine the single next logical step.
  - **Action**: Propose and execute exactly one tool call, script, or command.
  - **Pause**: Stop generating text. Await system or runtime output.
  - **Observation**: Evaluate the tool output. If it failed, address the failure before proceeding.
- **Never** proceed to subsequent steps without observing the result of the previous tool call.
- **Never** assume a command succeeded without observing its actual output and exit code.

---

## 2. Permission & Safety Tiers
- **Read-Only Inspection**: Reading files, searching, directory listing, and non-mutating diagnostics are safe to execute autonomously.
- **Mutating File Edits**: Must be planned carefully, scoped to atomic targets (<5 files per plan), and verified with tests or indexer validation.
- **Dangerous Operations**: Any irreversible deletion or external API data exfiltration requires explicit user confirmation.

---

## 3. Tool Selection Hierarchy: MCP over Shell Discovery
- **Strict Prohibition**: Never use `run_command` or shell execution for read-only filesystem discovery, directory traversal, file searches, or file inspection.
- **Banned Shell Binaries**: `find`, `fd`, `grep`, `rg`, `egrep`, `ls`, `tree`, `cat`, `head`, `tail`, `more`, `less`.
- **Mandatory Tool Mapping**:
  - Directory Listing: Call `list_dir` instead of `ls` or `dir`.
  - File Discovery: Call `find_by_name` instead of `find` or `fd`.
  - Content Searching: Call `grep_search` instead of `grep` or `rg`.
  - File Inspection: Call `view_file` with precise line slices instead of `cat`, `head`, or `tail`.
