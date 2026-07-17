

<div align="center">

<img src="https://sprawl.software/assets/sprawl-logo-emerald (2).svg" alt="Sprawl.software" width="480">

**Developer infrastructure for AI agent containment, telemetry, and workspace governance.**

# Demo DNA Repository

A ready-to-use reference DNA for learning Sprawl CLI's configuration architecture.

[Sprawl CLI](https://github.com/sprawl-software/sprawl-cli) · [Documentation](https://sprawl.software/docs/) · [Website](https://sprawl.software)

---

</div>

## Overview

A **DNA repository** is a Git-hosted registry of reusable agent configurations — rules, skills, personas, atoms, molecules, and workflows — that Sprawl compiles into native IDE settings and MCP schemas.

This demo DNA provides a minimal, working example of every configuration type in the Sprawl ecosystem. Use it to test `sprawl init`, `sprawl add`, and `sprawl sync` without building a full governance architecture from scratch.

## What's Inside

| Type | File | Purpose |
|---|---|---|
| **Atom** | `atoms/user_profile.json` | A structured data template defining a standard user profile schema |
| **Molecule** | `molecules/local-filesystem-mcp.json` | An MCP server configuration granting scoped local filesystem access |
| **Skill / Persona** | `skills/persona-demo_engineer/SKILL.md` | A persona definition with activation triggers, tone directives, and evaluation protocols |
| **Rule** | `rules/demo_security.md` | A security boundary rule defining what agents can and cannot access |
| **Workflow** | `workflows/demo_build.md` | A step-by-step execution recipe for deterministic task completion |

These map directly to the [Atomic Agentic Fabric (AFF)](https://github.com/w3bwizart/atomic-agentic-fabric-specification) specification.

## Quick Start

### 1. Initialize the Demo DNA

Clone this registry into your local Sprawl hub:

```bash
sprawl init https://github.com/sprawl-software/atomic-agentic-fabric-demo-dna.git
```

### 2. Create a Test Workspace

```bash
sprawl create demo-workspace
cd demo-workspace
```

### 3. Add Components

Select which configurations to inject into your workspace:

```bash
sprawl add user_profile.json local-filesystem-mcp.json demo_security.md persona-demo_engineer
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
4. Write your own rules, skills, and personas — see the [documentation](https://sprawl.software/docs/) for the full schema reference

## Part of the Sprawl Ecosystem

- **[Sprawl CLI](https://github.com/sprawl-software/sprawl-cli)** — Core engine for workspace sandboxing and configuration governance
- **Demo DNA** ← *you are here*
- **[Atomic Agentic Fabric](https://github.com/w3bwizart/atomic-agentic-fabric-specification)** — Open-source specification this DNA implements
- **[Website](https://github.com/sprawl-software/website-sprawl-software)** — Product site at [sprawl.software](https://sprawl.software)

## License

[MIT](LICENSE) — Free to use, fork, and extend.

---

<div align="center">
<sub>Part of the <a href="https://github.com/sprawl-software">Sprawl.software</a> platform · Built in Antwerp 🇧🇪</sub>
</div>
