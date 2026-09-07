# epistegrity

**episteme + integrity** — a context-agnostic methodology scaffold for AI-assisted software development.

This repo is not a framework or a library. It is a set of files that, when copied into a new project, give an AI agent (or a human) a consistent operating protocol: how to start a session, how to track work, how to document decisions, how to handle failure, how to select the next step, and how to leave a legible record for the next session.

---

## The files

| File | Purpose |
|---|---|
| `METHODOLOGY.md` | The rules. Session protocol, commit discipline, failure handling, WaLRuS-DATA format, TDD with test authenticity, four-item post-phase audit, artifact taxonomy. Copy verbatim — no project-specific content. |
| `CYCLE.md` | The operating loop. Orient → Decide → Execute → Audit → Repair → Repeat. RAROC step selection over feasible/choosable splits with decomposability and sanction surfacing, Definition of Success (proof = working solution in production demonstrating expected RAROC), autonomy as the default regime with owner-sanctioned exceptions. Copy verbatim — no project-specific content. |
| `ROLES.md` | Role separation. Steward executes, Critic falsifies, Auditor verifies, Owner legislates — no role grades its own work. Copy verbatim; instances declared in `CLAUDE.md` Conventions. |
| `ARCHITECTURE.md` | Engineering invariants (boundary defense, re-entrant mutations, expand/contract, vertical slice locality, indirection cap) + banned patterns + placeholder sections for system diagram, components, design decisions, and constraints. Fill in as the system takes shape. |
| `IMPLEMENTATION.md` | Phase gate structure. Phase 0 = discovery. Phase N = implementation with test-first tasks and a verification statement. |
| `CLAUDE.md` | Session bootstrap. One sentence describing the system, the start protocol (including role identification), and a slot for project conventions and accepted deviations. |
| `docs/scope-TEMPLATE.md` | Blank maximal-scope template. Copy to `docs/scope.md` and fill in: maximal mission, scope ladder, terminal form. Orient measures the status quo against it. |
| `docs/walrus-TEMPLATE.md` | Blank WaLRuS-DATA template. Copy to `docs/walrus-YYYY-MM-DD.md` at the end of any significant session. |
| `README.md` | This file. Replace with your project's README once instantiated. |

---

## How to instantiate

1. Copy all files into the root of your project (create `docs/` if it doesn't exist).
2. Edit `CLAUDE.md`: replace `[Project Name]` and the one-line description. Fill in the Conventions section, including the role instances (`ROLES.md`) and any accepted constitution deviations.
3. Copy `docs/scope-TEMPLATE.md` to `docs/scope.md` and fill it in: maximal mission, the scope ladder to the universal level, terminal form.
4. Edit `IMPLEMENTATION.md`: replace Phase 0 and Phase N placeholders with your actual phases and tasks.
5. Edit `ARCHITECTURE.md`: fill in the System Diagram, Components, and Constraints sections as you discover them.
6. Leave `METHODOLOGY.md`, `CYCLE.md`, `ROLES.md`, and the templates verbatim — they are shared protocol, not project-specific content.

From that point: every session starts with `CLAUDE.md`, work proceeds by `CYCLE.md`, and every session ends with a WaLRuS-DATA file.

---

## Versioning the scaffold

The protocol files evolve by extraction: downstream instances develop patterns under live operation, and the generalizable ones are distilled back here. Instances track the scaffold version they operate under with a `.epistegrity-version` file at their root containing the upstream commit SHA.

Pin discipline: a `.epistegrity-version` bump is one commit unit that syncs every verbatim protocol file (`METHODOLOGY.md`, `CYCLE.md`, `ROLES.md`, templates) to the pinned tree, or declares the deviation explicitly. Verify by blob SHA — `git hash-object` on the local file must equal the upstream blob SHA at the pinned ref. A pin that asserts a state the files do not have is drift, not versioning.

---

## Origin

Distilled from [`grok-research-mcp`](https://github.com/seva/grok-research-mcp) — a completed MCP server project that developed this methodology organically across its implementation phases. The patterns here are what worked: what kept sessions coherent, what kept the failure record legible, and what kept an AI agent on track across context boundaries.

`CYCLE.md` and `docs/scope-TEMPLATE.md` were extracted back from [`law-and-order`](https://github.com/seva/law-and-order) — the first downstream instantiation — where the operating loop, RAROC step selection, and the production-RAROC definition of proof were developed and exercised. The autonomy doctrine and owner-sanction rule were extracted back in a second round, after live operation exposed a blocked dependency and the dependency was inverted. A third round extracted the claims-vs-evidence audit step, scaffold pin discipline, and the sanction-is-permission interpretation — after an audit found a falsified claim that internal-consistency checks could not see, a pin bump drifted from its own files, and a gap analysis misread sanction as owner labor. A fourth round extracted `ROLES.md` and selection-function v2 (feasible/choosable/scored split, decomposability, sanction surfacing), validated live by an RCA in which the old feasibility filter was found silently excluding high-value directions.

`ARCHITECTURE.md`'s Engineering Invariants and Banned Patterns were distilled from a RAROC review of the max-raroc-engineering spec (2026-09-06): boundary defense, idempotent mutations, expand/contract migrations, vertical slicing, and integration-over-mocking were adopted; the decorative capital formula and the wholesale TDD ban were rejected in favor of this scaffold's TDD discipline and Acceptable/Gap coverage machinery.
