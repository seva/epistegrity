# epistegrity

**episteme + integrity** — a context-agnostic methodology scaffold for AI-assisted software development.

This repo is not a framework or a library. It is a set of six files that, when copied into a new project, give an AI agent (or a human) a consistent operating protocol: how to start a session, how to track work, how to document decisions, how to handle failure, and how to leave a legible record for the next session.

---

## The six files

| File | Purpose |
|---|---|
| `METHODOLOGY.md` | The rules. Session protocol, commit discipline, failure handling, WaLRuS-DATA format, TDD, artifact taxonomy. Copy verbatim — no project-specific content. |
| `ARCHITECTURE.md` | Universal principles + placeholder sections for system diagram, components, design decisions, and constraints. Fill in as the system takes shape. |
| `IMPLEMENTATION.md` | Phase gate structure. Phase 0 = discovery. Phase N = implementation with test-first tasks and a verification statement. |
| `CLAUDE.md` | Session bootstrap. One sentence describing the system, the four-step start protocol, and a slot for project conventions. |
| `docs/walrus-TEMPLATE.md` | Blank WaLRuS-DATA template. Copy to `docs/walrus-YYYY-MM-DD.md` at the end of any significant session. |
| `README.md` | This file. Replace with your project's README once instantiated. |

---

## How to instantiate

1. Copy all six files into the root of your project (create `docs/` if it doesn't exist).
2. Edit `CLAUDE.md`: replace `[Project Name]` and the one-line description. Fill in the Conventions section.
3. Edit `IMPLEMENTATION.md`: replace Phase 0 and Phase N placeholders with your actual phases and tasks.
4. Edit `ARCHITECTURE.md`: fill in the System Diagram, Components, and Constraints sections as you discover them.
5. Leave `METHODOLOGY.md` and `docs/walrus-TEMPLATE.md` verbatim — they are shared protocol, not project-specific content.

From that point: every session starts with step 2 of `CLAUDE.md`. Every session ends with a WaLRuS-DATA file.

---

## Origin

Distilled from [`grok-research-mcp`](https://github.com/seva/grok-research-mcp) — a completed MCP server project that developed this methodology organically across its implementation phases. The patterns here are what worked: what kept sessions coherent, what kept the failure record legible, and what kept an AI agent on track across context boundaries.
