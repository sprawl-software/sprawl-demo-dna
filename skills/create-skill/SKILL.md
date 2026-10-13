---
name: "Create Skill"
type: "skill"
domain: "extensibility"
version: "1.0.0"
description: "Create, scaffold, and optimize new agent skills within the repository ecosystem."
activation: "intent_detection"
author: "Sprawl Software"
tags: ["skill", "creator", "scaffold", "dna", "tools"]
---

# 🛠️ Create Skill (Skill Scaffolder)

This skill enables agents and developers to build, extend, and package specialized agentic capabilities into modular, reusable skills within the Sprawl ecosystem.

## Trigger Shortcuts

Whenever a user requests:
- `/create-skill` or `/skill-creator`
- "create a new skill" or "add a skill for <task>"
- "scaffold a tool for <process>"

Activate this skill immediately.

---

## The Anatomy of a Sprawl Skill

Every skill resides in its own self-contained directory under `skills/<skill-name>/`:

```
skills/<skill-name>/
├── SKILL.md (required)
│   ├── YAML frontmatter (name, type, domain, version, description, activation, tags)
│   └── Markdown operational instructions & protocols
├── scripts/    (optional) - Executable Python or Bash scripts for repetitive tasks
├── references/ (optional) - Detailed documentation, schemas, or API docs
└── assets/     (optional) - Static templates, sample payloads, or configs
```

---

## The 4-Step Skill Creation Process

### 1. Intent & Capability Capture
Determine the exact boundary and scope of the skill:
- **Core Capability**: What concrete task does this skill enable the agent to do?
- **Activation Intent**: What exact phrases, slash commands, or keywords should trigger it?
- **Tools Needed**: Does it require shell execution, file parsing, or external CLI commands?

### 2. Scaffold Directory & SKILL.md
Create the directory `skills/<kebab-case-name>/` and draft `SKILL.md`:
- Include clean YAML frontmatter.
- Keep `SKILL.md` focused and actionable. Use **progressive disclosure**: if documentation exceeds 300 lines, extract deep details into `references/`.

### 3. Add Supporting Scripts & Assets
If the skill requires automated actions (e.g. running linters, generating reports, parsing configs):
- Place helper scripts into `skills/<kebab-case-name>/scripts/`.
- Ensure scripts adhere to the **zero-external-dependency rule** (Python Standard Library or standard shell utilities).

### 4. Register & Wire
- If `AGENTS.md` exists, append the skill to the Skills listing.
- If `sprawl_manifest.yml` exists, register the skill under `skills`.
- Run `sprawl bind` or `sprawl ws push` to update IDE bindings.

---

## Standard SKILL.md Template

```markdown
---
name: "<Skill Display Name>"
type: "skill"
domain: "<domain: universal | engineering | sales | ops | design>"
version: "1.0.0"
description: "<Clear, actionable description of what the skill does and when to activate it.>"
activation: "intent_detection"
tags: ["<tag1>", "<tag2>"]
---

# <Skill Name>

[High-level overview of what this capability does.]

## Trigger Shortcuts
- `/<command>`
- "<trigger phrase 1>"
- "<trigger phrase 2>"

## Directives & Execution Protocol
1. **Step 1**: [Actionable instruction]
2. **Step 2**: [Actionable instruction]
3. **Step 3**: [Verification and output]

## Output Specification
[Define the exact formatting, tables, or artifacts expected.]
```

---

## Safety Guardrails
- **Never** hardcode private keys, API secrets, or absolute developer paths in skills.
- **Never** introduce heavy external dependencies when Python standard library functions suffice.
- **Always** ensure scripts handle errors gracefully and output clear diagnostic messages.
