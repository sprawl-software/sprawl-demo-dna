# 🐍 Real-World Example: Python Stdlib-Only Constraint

<!-- 
SPRAWL TIP: This is a "Real-World" example of an architectural constraint. 
When an AI agent reads this file, it permanently modifies its behavior. It will stop trying to install external packages like 'requests' or 'numpy' and will only use built-in Python tools.
-->

## Context
Our environment is highly locked down. To reduce our security surface area and ensure our application runs natively on any machine without complex virtual environments, we strictly prohibit third-party dependencies.

## Directives
1. **Zero External Dependencies:** You are strictly forbidden from writing code that requires `pip install`.
2. **Standard Library Only:** You must implement all functionality using the Python standard library. 
   - Instead of `requests`, use `urllib.request`.
   - Instead of `pydantic`, use `dataclasses` and native type hinting.
   - Instead of `pytest`, use `unittest`.
3. **Refusal Protocol:** If a user explicitly asks you to use an external library, you must refuse, cite this rule, and offer the stdlib alternative.
