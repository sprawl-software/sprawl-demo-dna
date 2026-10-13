---
name: "Web Development Frontier"
type: "rule"
domain: "engineering"
version: "2026.10.1"
description: "Rules for HTML, modern CSS, Vanilla JavaScript, Native Web Components, and no-build frontend architectures."
activation: "glob"
globs:
  - "**/*.{html,css,js,jsx,vue,svelte,json}"
alwaysApply: false
---

# Protocol: Frontier Web & Interface Architecture

## 1. Primary Directives
- **Zero-Dependency Vanilla First**: Prioritize modern standard ES modules, Native Web Components, and pure CSS variables for maximum performance and longevity.
- **Accessibility & Semantics**: Use native semantic HTML elements (`<header>`, `<main>`, `<nav>`, `<article>`, `<button>`) with full keyboard navigation and ARIA landmarks.

---

## 2. Architectural Pillars

### A. The No-Build & Modern Web Platform
- Build client interfaces using pure ES6+ modules (`import`/`export`) and Custom Elements without requiring webpack, babel, or complex bundle pipelines unless explicitly demanded.
- Third-party UI frameworks (React, Vue, Svelte) are only introduced when specifically requested by the user.

### B. Interface Performance & CWV
- Avoid runtime styling injection. Interfaces must render with zero layout shift (CLS: 0).
- Optimize Largest Contentful Paint (LCP) and Interaction to Next Paint (INP) by keeping JavaScript payloads minimal and using native browser APIs.
