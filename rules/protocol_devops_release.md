---
name: "DevOps & Release Protocol"
type: "rule"
domain: "devops"
version: "2026.5.2"
description: "Strict directives for Continuous Integration, semantic versioning, and secure open-source publishing (e.g., PyPI, Docker)."
activation: "glob"
globs:
  - "**/.github/workflows/*"
  - "**/Dockerfile"
  - "**/docker-compose.yml"
  - "**/deploy/*"
  - "**/pyproject.toml"
  - "**/setup.py"
alwaysApply: false
---

# DevOps & Release Protocol

## Mandate
A project is not "done" when the code works locally. It is done when it is securely, predictably, and autonomously packaged and distributed to the end user. This protocol governs release mechanics and packaging.

---

## 1. Versioning & Semantic Strictness
All releases MUST follow rigid Semantic Versioning (`MAJOR.MINOR.PATCH`), mapped directly to the delivery hierarchy:
- **MAJOR (vX.0.0)**: Breaking API changes, architectural rewrites, or deprecated interface removals.
- **MINOR (v0.X.0)**: New features, atomic skills, or backward-compatible capabilities.
- **PATCH (v0.0.X)**: Bug fixes, performance patches, security patches, or documentation corrections.

---

## 2. CI/CD Pipeline Standards
- **Hermetic Builds**: Build artifacts inside isolated container environments (Docker) with pinned dependencies.
- **Automated Verification**: Every pull request must trigger automated linting, type-checking, and unit test suites before merge approval.
- **Zero-Secret CI**: Never expose deployment keys or tokens in CI logs. Use environment secrets exclusively.

---

## 3. Packaging & Distribution
- **Docker Images**: Use multi-stage builds and slim base images (e.g. `alpine` or `distroless`) with non-root execution users.
- **Python / Node Packages**: Verify clean wheel builds and license inclusion before publishing to PyPI or npm registries.
