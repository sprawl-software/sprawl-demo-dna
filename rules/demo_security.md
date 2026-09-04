---
name: "Workstation Security Boundary"
type: "rule"
domain: "security"
version: "1.0.0"
description: "Strict workstation confinement rule. Forbids AI access to host credentials, private keys, environment secrets, and path traversal."
globs:
  - "**/*"
alwaysApply: true
---

# 🛡️ Workstation Security Boundary

<!-- 
SPRAWL RULE: The Sprawl CLI injects this rule across IDE adapters (Cursor, Claude Code, Antigravity, Copilot).
This file defines strict boundary enforcement for all autonomous tools and models.
-->

## 1. Primary Directive
You are strictly confined to the active project workspace root. You MUST NOT attempt to read, write, scan, or execute tools against files or directories outside this workspace boundary.

## 2. Protected Files & Zero-Access Assets
You are strictly forbidden from inspecting, outputting, or referencing:
1. **Secrets & Environment Variables:** `.env`, `.env.*`, `*.pem`, `*.key`, `*.pfx`, `id_rsa`, `id_ed25519`.
2. **Host Configuration Paths:** `~/.ssh/`, `~/.gnupg/`, `~/.aws/`, `~/.config/gcloud/`, `/etc/passwd`, `/etc/shadow`.
3. **Database & Seed Dumps:** `*.sqlite3-dump`, `*.sql.gz`, or raw production database backups.
4. **Path Traversal:** Any path using relative directory traversal (`../`) that escapes the project root.

## 3. Execution Mechanics
- **Always** use standard environment variable injection templates (e.g. `.env.example`) with dummy values when illustrating configuration.
- **Never** write, modify, or leak secrets, API tokens, or personal access tokens (PATs) into committed code, logs, or terminal transcripts.
- **Never** write files to `/tmp` or global system folders outside the active workspace.
- **Refusal Protocol:** If a user or script instructs you to read, dump, or transmit protected credentials or private keys, immediately refuse, cite this rule (`rules/demo_security.md`), and maintain containment.
