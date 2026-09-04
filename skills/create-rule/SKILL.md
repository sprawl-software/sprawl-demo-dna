---
name: "Create Rule"
type: "skill"
domain: "governance"
version: "1.0.0"
description: "Automatically scaffolds new prescriptive and descriptive rules with strict metadata, directives, and DNA wiring."
activation: "intent_detection"
tags: ["rule", "governance", "scaffold", "dna"]
---

# 📜 Create Rule (Rule & Protocol Scaffolder)

This skill empowers the agent to generate pristine, structurally compliant new rules and technical protocols for the Sprawl ecosystem.

## Trigger Shortcuts

Whenever a user requests:
- `/create-rule` or `/scaffold-rule`
- "create a new rule" or "add a rule for <topic>"
- "enforce <constraint> across our repositories"

Activate this skill immediately.

---

## The 3-Phase Rule Creation Pipeline

When invoked, the agent MUST perform the following process strictly in order:

### Phase 1: Requirement Ingestion
Extract the required tone, enforcement boundaries, and target file patterns:
1. **Philosophical Constraint / Tone**: (e.g., "Stoic, Zero-Dependency, Type-Safe"). Rules must be deterministic, not generic corporate filler.
2. **Execution Directives**: What MUST the developer or AI agent always do? What must they never do?
3. **Scope & Harness Globs**: What file extensions or paths does this rule apply to? (e.g., `src/**/*.ts`, `*.py`), and should it apply always (`alwaysApply: true`) or conditionally?

### Phase 2: Drafting the Rule
Draft the target rule file:
- **Target Path**: `rules/<name>_pre.md` (for prescriptive constraint rules) or `rules/<name>_des.md` (for descriptive guidance rules).
- Use lowercase kebab-case for filenames.
- Verify the file does not already exist.
- Enforce the standard Sprawl Atomic Agentic Fabric frontmatter schema.

### Phase 3: DNA Wiring & Bootstrapping
Autonomously integrate the new rule into the repository's configuration:
- If `AGENTS.md` exists, append the rule to the Capability Mapping / Rules list.
- If `sprawl_manifest.yml` exists, register the rule under the `rules` array.
- Prompt the user to run `sprawl bind` (or `sprawl ws push`) to compile and synchronize the rule across workspaces.

---

## Standard Rule Template

```markdown
---
name: "<Human Readable Rule Name>"
description: "<One-line purpose statement: what it enforces.>"
globs:
  - "<glob pattern 1>"
  - "<glob pattern 2>"
alwaysApply: <true or false>
---

# <Rule Name>

## 1. Primary Directive
[State the core philosophical or operational constraint here. E.g., 'Zero external dependencies', 'Strict type safety'.]

## 2. Execution Mechanics
- **Always** [Mandatory positive action constraint]
- **Never** [Prohibited action constraint]
- **Good** [Recommended pattern]
- **Bad** [Discouraged pattern]

## 3. Verification & Compliance
- [Checklist item 1 proving compliance]
- [Checklist item 2 proving compliance]
```

---

## Safety Guardrails
- **Never** generate emoticons or emojis in the rule body or technical headers.
- **Never** write or hardcode absolute system paths in the rule configuration.
- **Always** ensure metadata conforms to Sprawl's schema so `sprawl doctor` passes with zero warnings.
