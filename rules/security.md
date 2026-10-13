---
name: "Security & Containment Protocol"
type: "rule"
domain: "security"
version: "2026.5.0"
description: "Zero-trust and local-first containment guidelines for credentials, PII, and filesystem sandbox boundaries."
activation: "always_active"
globs: []
alwaysApply: true
---

# Security and Containment Protocol

## 1. Zero-Trust Security Gates
- **Zero Secrets in Code**: Never hardcode API keys, passwords, bearer tokens, or sensitive credentials in source code, configuration files, or documentation.
- **Immediate Halt on Secret Exposure**: If exposed credentials, keys, or unmasked sensitive data are discovered, halt immediately and alert the user.
- **PII & Data Redaction**: Never write unmasked customer PII data to logs, external environments, or untracked scratchpads.
- **Portability & Path Fencing**: Do not hardcode machine-specific absolute paths in distributable code or shared blueprints.

---

## 2. Local-First Sandbox Containment
- **Zero Unauthorized Exfiltration**: Never send proprietary workspace code, configurations, database dumps, or local files to external third-party endpoints without explicit user consent.
- **Local Verification**: Always use local mock data, containerized sandbox environments, or local SQLite/PostgreSQL databases for testing.

---

## 3. Workspace Boundary and Containment Shield
- **Strict Workspace Confinement**: All file reads, writes, mutations, and search traversals must remain bounded strictly within the active workspace root.
- **Authorized External Mounts**: The single authorized exception to workspace confinement is the declared Sprawl DNA Single Source of Truth (SSoT) repository at `~/.sprawl/core`.
- **Prohibited Host Traversal**: Never execute directory traversal (`../..`), inspect parent user directories (`/home/*`), or access temporary host locations (`/tmp/*`, `/etc/*`) without explicit user instruction.
- **Dependency Shield**: Never traverse, index, or search virtual environment directories (`Scripts/venv/`, `**/venv/**`) or internal editor caches (`.obsidian/`, `.idea/`, `.vscode/`). All discovery tools must apply path fencing or scope filters.
