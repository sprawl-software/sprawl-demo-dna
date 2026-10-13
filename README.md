<div align="center">

<img src="https://sprawl.software/assets/sprawl-logo-emerald (2).svg" alt="Sprawl.software" width="480">

**Developer infrastructure for AI agent containment, telemetry, and workspace governance.**

# Demo DNA Repository

A ready-to-use reference DNA for learning Sprawl CLI's configuration architecture.

[Sprawl CLI](https://github.com/sprawl-software/sprawl-cli) · [Documentation](https://sprawl.software/docs/) · [Website](https://sprawl.software)

---

</div>

## Overview

A **DNA repository** is a Git-hosted registry of reusable agent configurations - rules, skills, personas, atoms, molecules, and workflows - that Sprawl compiles into native IDE settings and MCP schemas.

This demo DNA provides a working suite of standard configurations in the Sprawl ecosystem. Use it to test `sprawl init`, `sprawl add`, and `sprawl sync` without building a full governance architecture from scratch.

## What's Inside

| Type | File | Purpose |
|---|---|---|
| **Atom** | `atoms/user_profile.json` | A structured data template defining a standard user profile schema |
| **Molecule** | `molecules/local-filesystem-mcp.json` | An MCP server configuration granting scoped local filesystem access |
| **Rule** | `rules/engineering.md` | Standard software engineering principles, double-diamond planning, and verification gates |
| **Rule** | `rules/python.md` | Pythonic core operations: structural typing, protocols, and stdlib-first architecture |
| **Rule** | `rules/web_development.md` | Modern web frontend architecture: semantic HTML5, pure CSS variables, and Native Web Components |
| **Rule** | `rules/security.md` | Zero-trust workstation containment, credential protection, and path fencing |
| **Rule** | `rules/protocol_devops_release.md` | DevOps and release protocol: strict SemVer, hermetic container builds, and CI verification |
| **Rule** | `rules/epistemic_integrity.md` | Anti-sycophancy, banned conversational filler, and empirical pushback defense |
| **Rule** | `rules/react_reasoning_loop.md` | Strict ReAct paradigm (Thought, Action, Pause, Observation) and MCP discovery tool selection |
| **Skill / Scaffolding** | `skills/create-rule/SKILL.md` | Autonomous rule scaffolder for creating new prescriptive and descriptive rules |
| **Skill / Scaffolding** | `skills/create-skill/SKILL.md` | Autonomous skill scaffolder for building and extending agent capabilities |
| **Skill / Scaffolding** | `skills/create-architecture-doc/SKILL.md` | Repository analyzer generating Architecture.md with Mermaid diagrams |
| **Skill / Persona** | `skills/persona-demo_engineer/SKILL.md` | Platform enablement persona verifying governance injection and diagnostics |
| **Skill / Persona** | `skills/persona-master-engineer/SKILL.md` | Framework-agnostic Master Engineer persona enforcing first-principles architecture |
| **Skill / Persona** | `skills/persona-devops-architect/SKILL.md` | DevOps and SRE Architect persona overseeing containerization and pipeline automation |
| **Skill / Persona** | `skills/persona-sec-agent/SKILL.md` | Security and Enterprise Compliance Auditor persona (vulnerability analysis and regulatory compliance) |
| **Workflow** | `workflows/demo_build.md` | Deterministic verification build and test execution checklist |

These map directly to the [Atomic Agentic Fabric (AFF)](https://github.com/sprawl-software/atomic-agentic-fabric-specification) specification.

## Quick Start

### 1. Initialize the Demo DNA

Clone this registry into your local Sprawl hub (or simply run `sprawl init` with no arguments):

```bash
sprawl init https://github.com/sprawl-software/sprawl-demo-dna.git
```

### 2. Create a Test Workspace

```bash
sprawl create demo-workspace
cd demo-workspace
```

### 3. Add Components

Select which configurations to inject into your workspace:

```bash
sprawl add user_profile.json local-filesystem-mcp.json engineering.md security.md persona-master-engineer
```

### 4. Compile & Bind

```bash
sprawl sync
sprawl bind
```

Your workspace is now governed. Run `sprawl status` to inspect the active configuration.

## Next Steps

Once you've explored the demo, build your own DNA:

1. Remove the demo workspace: `sprawl ws remove demo-workspace --delete`
2. Create a new Git repository for your team's DNA registry
3. Run `sprawl init <YOUR_GIT_URL>` to register it
4. Write your own rules, skills, and personas - see the [documentation](https://sprawl.software/docs/) for the full schema reference

## Part of the Sprawl Ecosystem

- **[Sprawl CLI](https://github.com/sprawl-software/sprawl-cli)** - Core engine for workspace sandboxing and configuration governance
- **Demo DNA** (reference repository)
- **[Atomic Agentic Fabric](https://github.com/sprawl-software/atomic-agentic-fabric-specification)** - Open-source specification this DNA implements
- **[Website](https://github.com/sprawl-software/website-sprawl-software)** - Product site at [sprawl.software](https://sprawl.software)

## License

[MIT](LICENSE) - Free to use, fork, and extend.

---

<div align="center">
<sub>Part of the <a href="https://github.com/sprawl-software">Sprawl.software</a> platform · Built in Antwerp 🇧🇪</sub>
</div>
