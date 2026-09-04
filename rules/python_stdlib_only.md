---
name: "Python Standard Library Only"
type: "rule"
domain: "engineering"
version: "1.0.0"
description: "Strict architectural constraint forbidding third-party pip dependencies in favor of Python standard library primitives."
globs:
  - "**/*.py"
alwaysApply: false
---

# 🐍 Python Standard Library Only Constraint

<!-- 
SPRAWL RULE: When Sprawl binds this rule, the AI permanently restricts its Python implementation patterns.
It will refuse third-party packages and construct performant, zero-dependency alternatives.
-->

## 1. Primary Directive
Our environment is strictly locked down to eliminate external attack surfaces, supply-chain risks, and environment drift. You are strictly forbidden from generating code that requires `pip install` or external package dependencies.

## 2. Standard Library Mapping Protocol
Implement all system functionality using Python Standard Library modules exclusively:
- **Networking & HTTP:** Use `urllib.request`, `urllib.parse`, and `http.client` (never `requests` or `httpx`).
- **Data Models & Schemas:** Use `@dataclasses.dataclass` and native `typing` (never `pydantic` or `attrs`).
- **Testing:** Use `unittest` and `unittest.mock` (never `pytest`).
- **JSON & Data Structures:** Use `json`, `csv`, `sqlite3`, and `collections`.
- **Async & Concurrency:** Use `asyncio`, `concurrent.futures`, and `threading`.

## 3. Refusal & Alternative Protocol
If a user or prompt explicitly asks you to import or install a third-party library, you must:
1. Respectfully refuse the external package installation.
2. Cite this rule: `rules/python_stdlib_only.md`.
3. Provide the full, working drop-in replacement using the Python Standard Library.
