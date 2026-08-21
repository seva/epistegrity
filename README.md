# epistegrity

**episteme + integrity** — a context-agnostic methodology scaffold for AI-assisted software development.

This repo is not a framework or a library. It is a set of files that, when copied into a new project, give an AI agent (or a human) a consistent operating protocol: how to start a session, how to track work, how to document decisions, how to handle failure, how to select the next step, and how to leave a legible record for the next session.

---

## The files

| File | Purpose |
|---|---|
| `METHODOLOGY.md` | The rules. Session protocol, commit discipline, failure handling, WaLRuS-DATA format, TDD, artifact taxonomy. Copy verbatim — no project-specific content. |
| `CYCLE.md` | The operating loop. Orient → Decide → Execute → Audit → Repair → Repeat. RAROC step selection, Definition of Success (proof = working solution in production demonstrating expected RAROC). Copy verbatim — no project-specific content. |
| `ARCHITECTURE.md` | Universal principles + placeholder sections for system diagram, components, design decisions, and constraints. Fill in as the system takes shape. |
| `IMPLEMENTATION.md` | Phase gate structure. Phase 0 = discovery. Phase N = implementation with test-first tasks and a verification statement. |
| `CLAUDE.md` | Session bootstrap. One sentence describing the system, the start protocol, and a slot for project conventions. |
| `docs/scope-TEMPLATE.md` | Blank maximal-scope template. Copy to `docs/scope.md` and fill in: maximal mission, scope ladder, terminal form. Orient measures the status quo against it. |
| `docs/walrus-TEMPLATE.md` | Blank WaLRuS-DATA template. Copy to `docs/walrus-YYYY-MM-DD.md` at the end of any significant session. |
| `README.md` | This file. Replace with your project's README once instantiated. |

---

## How to instantiate

1. Copy all files into the root of your project (create `docs/` if it doesn't exist).
2. Edit `CLAUDE.md`: replace `[Project Name]` and the one-line description. Fill in the Conventions section.
3. Copy `docs/scope-TEMPLATE.md` to `docs/scope.md` and fill it in: maximal mission, the scope ladder to the universal level, terminal form.
4. Edit `IMPLEMENTATION.md`: replace Phase 0 and Phase N placeholders with your actual phases and tasks.
5. Edit `ARCHITECTURE.md`: fill in the System Diagram, Components, and Constraints sections as you discover them.
6. Leave `METHODOLOGY.md`, `CYCLE.md`, and the templates verbatim — they are shared protocol, not project-specific content.

From that point: every session starts with `CLAUDE.md`, work proceeds by `CYCLE.md`, and every session ends with a WaLRuS-DATA file.

---

## Origin

Distilled from [`grok-research-mcp`](https://github.com/seva/grok-research-mcp) — a completed MCP server project that developed this methodology organically across its implementation phases. The patterns here are what worked: what kept sessions coherent, what kept the failure record legible, and what kept an AI agent on track across context boundaries.

`CYCLE.md` and `docs/scope-TEMPLATE.md` were extracted back from [`law-and-order`](https://github.com/seva/law-and-order) — the first downstream instantiation — where the operating loop, RAROC step selection, and the production-RAROC definition of proof were developed and exercised.
