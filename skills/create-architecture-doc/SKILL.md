---
name: "create-architecture-doc"
description: "Analyze a codebase repository and generate a comprehensive Architecture.md document with Mermaid.js diagrams, tech stack inventory, and component maps."
type: "skill"
domain: "engineering"
version: "2026.10.1"
activation: "manual"
alwaysApply: false
globs:
  - "skills/create-architecture-doc/**/*"
author: "Sprawl Software"
tags: ["architecture", "mermaid", "documentation"]
---
# Skill: create-architecture-doc

Analyze a codebase and produce a complete Architecture.md system map with Mermaid.js diagrams. The output should read like documentation written by a senior architect for an engineering team during onboarding or a design review: precise, structural, and free of filler.

## Trigger Shortcuts

Activate this skill when a user:
- Says `/create-architecture-doc`, `/arch-doc`, `/architecture`, or "generate architecture doc"
- Asks "how is this codebase structured?" or "give me an overview of this project"
- Requests a system diagram, data model map, or codebase walkthrough
- Mentions needing onboarding documentation for a repository
- Wants to understand a new or unfamiliar codebase

## Inputs

1. **`codebase_path`** (required): The root directory of the repository to analyze. If the user doesn't specify one, check whether they have an active project open and confirm it with them.
2. **`entry_points`** (optional): Specific files that serve as the main execution or routing hubs (e.g., `main.py`, `app.ts`, `index.js`, `manage.py`). If not provided, discover them automatically during Phase 1.

## Output

A single Markdown file: `Architecture.md`, written to the root of `codebase_path`. The file serves as a descriptive rule mapping the terrain of the project and follows the template defined in Phase 4.

---

## Execution State Machine

Complete each phase fully before proceeding to the next. Do not skip phases.

### Phase 1: Intelligent Ingestion (Token Optimization)

The goal is to build a mental model of the codebase without exhausting the context window. Read strategically: like an architect doing a site survey, not a compiler parsing every line.

**Step 1.1: Directory Scan**
Scan the full directory tree from `codebase_path`. This gives you the skeleton.

**Step 1.2: Noise Filtering**
Strictly ignore these directories and files during all subsequent reads. They contain no architectural signal:
- `node_modules`, `venv`, `.venv`, `env`, `.git`, `dist`, `build`, `out`, `target`
- `__pycache__`, `.pytest_cache`, `.mypy_cache`, `.tox`, `.eggs`
- `*.lock` files, `*.min.js`, `*.min.css`, `*.map` files
- Any directory that is clearly compiled output, cached artifacts, or vendored dependencies

**Step 1.3: Stack Discovery (Read Config Files First)**
Read these files to identify the technology stack before touching any source code:
- `package.json`, `requirements.txt`, `pyproject.toml`, `Cargo.toml`, `go.mod`
- `docker-compose.yml`, `Dockerfile`
- `tsconfig.json`, `.babelrc`, `webpack.config.*`, `vite.config.*`
- `Makefile`, `justfile`, `Taskfile.yml`
- Any CI/CD config (`.github/workflows/`, `.gitlab-ci.yml`)

**Step 1.4: Architectural Reads (Imports, Exports, Signatures Only)**
Now read the source code, but only for structural understanding. For each file, extract:
- Import/export statements (what depends on what)
- Class definitions and their inheritance/composition
- Function/method signatures (name, parameters, return type)
- Decorator patterns (`@app.route`, `@Injectable`, `@Entity`, etc.)
- Database model/schema definitions

Do NOT read line-by-line algorithmic logic, test assertions, or UI template markup. You are mapping the skeleton, not reading the flesh.

**Step 1.5: Entry Point Discovery**
If `entry_points` were not provided, identify them by looking for:
- Files named `main.*`, `app.*`, `index.*`, `server.*`, `manage.*`
- Files containing `if __name__ == "__main__"`, `createApp()`, `express()`, `FastAPI()`, `Flask(__name__)`
- Router/controller registration files
- The `"main"` or `"scripts.start"` field in `package.json`

**Step 1.6: Size Gate**
If the scanned directory tree contains more than ~200 source files (excluding tests and ignored dirs), pause and ask the user:
> "This codebase has [N] source files. To keep the analysis focused and accurate, would you like me to analyze a specific sub-directory or module? If not, I'll focus on the top-level architecture and the most connected modules."

---

### Phase 2: Structural Analysis

With the ingested data, perform the following analysis:

**Step 2.1: Framework & Language Identification**
Identify the primary language(s) and framework(s). Note versions where config files specify them.

**Step 2.2: Data Flow Mapping**
Trace how a request (or command, or event) flows through the system:
1. Where does execution begin? (HTTP server, CLI entrypoint, event listener, cron job)
2. What middleware, guards, or interceptors does it pass through?
3. Which service/controller/handler processes the logic?
4. How does it interact with the data layer? (ORM, raw queries, API calls)
5. What gets returned or emitted?

**Step 2.3: External Integration Inventory**
Identify all external dependencies and integrations:
- Databases (PostgreSQL, MongoDB, Redis, SQLite)
- Message queues / event buses (RabbitMQ, Kafka, Redis Pub/Sub)
- External APIs (REST, GraphQL, gRPC endpoints called by the code)
- Cloud services (S3, SQS, Lambda, etc.)
- Authentication providers (OAuth, JWT issuers, SAML)

**Step 2.4: Module Boundary Mapping**
Identify the major modules or bounded contexts. What are the 3-7 core "chunks" of this system that a new engineer needs to understand?

---

### Phase 3: Mermaid.js Diagram Generation

Generate two diagrams using valid, non-deprecated Mermaid.js syntax. Wrap all diagrams in standard mermaid code blocks.

**Diagram 1: System Architecture (Flowchart)**
Show the high-level relationship between:
- Client/User interface
- API Gateway or Server
- Core services/modules
- Data stores
- External integrations

Use `graph TD` or `graph LR` depending on what reads better for the specific system. Use subgraphs to group related components. Label all edges with the interaction type (HTTP, gRPC, SQL, Pub/Sub, etc.).

Guidelines for clean diagrams:
- Quote node labels containing special characters like parentheses, brackets, or ampersands
- Avoid HTML tags in labels
- Keep node IDs short and labels descriptive
- Use subgraphs to reduce visual noise

**Diagram 2: Data Model / Entity Relationship (ER Diagram)**
Show the core domain models and their relationships, derived from schema files, ORM models, or migration files. Use `erDiagram` syntax.

If no formal schema or ORM models exist (e.g., a pure frontend app or a script-based tool), skip this diagram and note why in the output.

---

### Phase 4: Output Generation

Write the `Architecture.md` file to the root of `codebase_path` using this exact structure:

```markdown
# System Architecture

> Auto-generated by the Generate Architecture Doc skill.
> Last generated: [ISO timestamp]

## Tech Stack Overview

- **Language(s):** [e.g., Python 3.11, TypeScript 5.x]
- **Framework(s):** [e.g., FastAPI, Next.js 14]
- **Database:** [e.g., PostgreSQL 15 via SQLAlchemy]
- **Infrastructure:** [e.g., Docker, GitHub Actions CI]
- **Key Libraries:** [Top 5-8 notable dependencies]

## Directory Structure

[Simplified tree view: max 3 levels deep, core directories only. Annotate what each directory contains.]

## System Flow

[Insert Mermaid.js System Architecture diagram]

[1-2 paragraphs describing the primary request/data flow in plain English]

## Core Components

[For each major module/service, provide:]
### [Module Name]
- **Purpose:** [One sentence]
- **Key Files:** [2-4 most important files]
- **Depends On:** [Other modules it imports from]
- **Exposes:** [What it exports or serves]

## Data Models

[Insert Mermaid.js ER diagram, or note "No formal data models detected" if applicable]

[Brief description of the core entities and their relationships]

## Entry Points & Routing

[List each entry point with its purpose and how routing is configured]

| Entry Point | Type | Description |
|---|---|---|
| `src/main.py` | CLI | Primary execution entrypoint |
| `src/api/routes.py` | HTTP | FastAPI router definitions |
```

---

## Guardrails

- **Rule Connection**: The generation of this architecture map must adhere to the modular naming conventions and directory standards defined in active workspace Engineering rules.
- **Token Budget**: If a codebase exceeds the size gate in Phase 1, prompt the user before continuing. Do not silently produce a shallow or incomplete analysis.
- **Mermaid Syntax**: Always validate that Mermaid syntax uses standard, non-deprecated constructs. Quote labels with special characters. No HTML in labels.
- **Objectivity**: Maintain a technical, objective tone. Do not editorialize about code quality, tech choices, or architecture decisions unless the user explicitly asks for a review.
- **Non-Destructive**: If an `Architecture.md` already exists, ask the user before overwriting it.
