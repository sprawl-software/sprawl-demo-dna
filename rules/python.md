---
name: "Pythonic Core Operations"
type: "rule"
domain: "engineering"
version: "2026.5.0"
description: "Language-specific directives for Python design, structural typing, stdlib-first architecture, and testing."
activation: "glob"
globs:
  - "**/*.{py,pyi,ipynb}"
  - "**/requirements.txt"
  - "**/pyproject.toml"
alwaysApply: false
---

# PYTHONIC CORE OPERATIONS

## 1. Primary Directives
- **Standard-Library-First**: Leverage Python's standard library (`pathlib`, `json`, `dataclasses`, `typing`, `asyncio`, `unittest`) before introducing external dependencies.
- **System Craftsmanship**: Ensure every line of Python is modular, high-performance, cleanly formatted, and fully type-annotated.

---

## 2. Architectural Pillars

### A. Loose Coupling & Structural Subtyping (`typing.Protocol`)
- Favor structural subtyping (`typing.Protocol` / `abc.ABC`) over rigid class inheritance. Define minimal, specialized behavior interfaces (e.g. `Reader`, `Writer`, `Syncable`).
- Never introduce cyclic imports. Structure code with clean unidirectional dependency flow.

### B. Strict Data Validation (`Pydantic` / Dataclasses)
- Use `Pydantic` (or `@dataclass(frozen=True)` with stdlib) for parsing external JSON, YAML, and environment configurations.
- Fail fast on malformed inputs with descriptive error messages.

### C. Type Hints & MyPy Compliance
- All public functions and methods MUST include full type annotations (`def parse_node(path: Path) -> NodeMetadata:`).
- Avoid `Any`. Use `Union`, `Optional`, `TypeVar`, or `Protocol`.

---

## 3. Testing Standards
- Write clean `unittest` or `pytest` suites verifying functional correctness, edge cases, and failure modes.
