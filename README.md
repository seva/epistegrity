# epistegrity

**episteme + integrity** — a context-agnostic methodology scaffold for AI-assisted software development.

This repo is not a framework or a library. It is a set of files that, when copied into a new project, give an AI agent (or a human) a consistent operating protocol: how to start a session, how to track work, how to document decisions, how to handle failure, how to select the next step, and how to leave a legible record for the next session.

---

## The files

| File | Purpose |
|---|---|
| `METHODOLOGY.md` | The rules. Session protocol, commit discipline, failure handling, WaLRuS-DATA format, TDD with test authenticity, four-item post-phase audit, artifact taxonomy. Copy verbatim — no project-specific content. |
| `CYCLE.md` | The operating loop. Orient → Decide → Execute → Audit → Repair → Repeat. RAROC step selection over feasible/choosable splits with decomposability, sanction surfacing, filter-before-rank at the terminal bound, marginal-not-level scoring, allocation-is-Decide (every tool/subagent/human invocation scored, filter-first on irrecoverable media), human-tool interface discipline, Turk decomposition of human dependencies, and Revision escalation from Repair. Definition of Success (proof = working solution in production demonstrating expected RAROC), autonomy as the default regime with owner-sanctioned exceptions, disposition as a legislative act. Copy verbatim — no project-specific content. |
| `HORIZONS.md` | Horizon doctrine — PRAROC-7 (Progressive RAROC; the P is the process, 7 is the ladder's bound: commitment classes run at PRAROC-n, n set by commitment cost). Refinement ladder, checkable claims and expiring readings, the terminal bound derived once and compiled, filter-before-rank on non-convertible denominators, profile-not-total, marginal allocation, set 5/7 mechanics, error signatures as an audit checklist. Copy verbatim; canonical prose in `docs/praroc-paradigm.md`; compiled constraints in `docs/scope.md`. |
| `ROLES.md` | Role separation. Steward executes, Critic falsifies, Auditor verifies, Owner legislates — no role grades its own work. Copy verbatim; instances declared in `AGENTS.md` Conventions. |
| `ARCHITECTURE.md` | Engineering invariants (boundary defense, re-entrant mutations, expand/contract, vertical slice locality, indirection cap) + banned patterns + placeholder sections for system diagram, components, design decisions, and constraints. Fill in as the system takes shape. |
| `IMPLEMENTATION.md` | Phase gate structure. Phase 0 = discovery. Phase N = implementation with test-first tasks and a verification statement. |
| `AGENTS.md` | Session bootstrap. One sentence describing the system, the start protocol (including role identification), and a slot for project conventions and accepted deviations. AGENTS.md is the vendor-neutral standard runners load natively; if your runner only reads its own brand file (`CLAUDE.md`, `GEMINI.md`, …), create that file as a one-line pointer — `Read and follow AGENTS.md — it is this project's session bootstrap.` Never duplicate the content: two bootstrap files is a drift vector. |
| `docs/scope-TEMPLATE.md` | Blank maximal-scope template. Copy to `docs/scope.md` and fill in: maximal mission, scope ladder, terminal form, terminal bound (compiled constraints, irrecoverable margins, refinement level per commitment class). Orient measures the status quo against it. |
| `docs/praroc-paradigm.md` | The Progressive RAROC paradigm (PRAROC-7) in full — reference doctrine behind `HORIZONS.md`: position sets and split signals, cases (codebase, role, enterprise), mnemonic, distilled rules. Copied for reference; never instantiated. |
| `docs/walrus-TEMPLATE.md` | Blank WaLRuS-DATA template. Copy to `docs/walrus-YYYY-MM-DD.md` at the end of any significant session. |
| `docs/pending-owner-TEMPLATE.md` | Blank open-invocation register. Copy to `docs/pending-owner.md`; one row per open human invocation (reserved class, act statement, packet pointer, score line, concurrent motion, surfaced date). An empty register is a valid state. |
| `README.md` | This file. Replace with your project's README once instantiated. |

---

## How to instantiate

1. Copy all files into the root of your project (create `docs/` if it doesn't exist).
2. Edit `AGENTS.md`: replace `[Project Name]` and the one-line description. Fill in the Conventions section, including the role instances (`ROLES.md`) and any accepted constitution deviations. If your runner reads a brand-specific bootstrap file, create it as a one-line pointer to `AGENTS.md`.
3. Copy `docs/scope-TEMPLATE.md` to `docs/scope.md` and fill it in: maximal mission, the scope ladder to the universal level, terminal form, and the terminal bound — derived once, compiled into standing constraints, never consulted at the decision point.
4. Edit `IMPLEMENTATION.md`: replace Phase 0 and Phase N placeholders with your actual phases and tasks.
5. Edit `ARCHITECTURE.md`: fill in the System Diagram, Components, and Constraints sections as you discover them.
6. Leave `METHODOLOGY.md`, `CYCLE.md`, `HORIZONS.md`, `ROLES.md`, `docs/praroc-paradigm.md`, and the templates verbatim — they are shared protocol, not project-specific content.

From that point: every session starts with `AGENTS.md`, work proceeds by `CYCLE.md`, and every session ends with a WaLRuS-DATA file.

---

## Versioning the scaffold

The protocol files evolve by extraction: downstream instances develop patterns under live operation, and the generalizable ones are distilled back here. Instances track the scaffold version they operate under with a `.epistegrity-version` file at their root containing the upstream commit SHA.

Pin discipline: a `.epistegrity-version` bump is one commit unit that syncs every verbatim protocol file (`METHODOLOGY.md`, `CYCLE.md`, `HORIZONS.md`, `ROLES.md`, `docs/praroc-paradigm.md`, templates) to the pinned tree, or declares the deviation explicitly. Verify by blob SHA — `git hash-object` on the local file must equal the upstream blob SHA at the pinned ref. A pin that asserts a state the files do not have is drift, not versioning.

Breaking change: the bootstrap file was renamed `CLAUDE.md` → `AGENTS.md`. Instances pinned before the rename keep `CLAUDE.md` — it stays valid at their pinned tree; the bump that crosses the rename renames the file and updates its references.

---

## Origin

Distilled from [`grok-research-mcp`](https://github.com/seva/grok-research-mcp) — a completed MCP server project that developed this methodology organically across its implementation phases. The patterns here are what worked: what kept sessions coherent, what kept the failure record legible, and what kept an AI agent on track across context boundaries.

`CYCLE.md` and `docs/scope-TEMPLATE.md` were extracted back from [`law-and-order`](https://github.com/seva/law-and-order) — the first downstream instantiation — where the operating loop, RAROC step selection, and the production-RAROC definition of proof were developed and exercised. The autonomy doctrine and owner-sanction rule were extracted back in a second round, after live operation exposed a blocked dependency and the dependency was inverted. A third round extracted the claims-vs-evidence audit step, scaffold pin discipline, and the sanction-is-permission interpretation — after an audit found a falsified claim that internal-consistency checks could not see, a pin bump drifted from its own files, and a gap analysis misread sanction as owner labor. A fourth round extracted `ROLES.md` and selection-function v2 (feasible/choosable/scored split, decomposability, sanction surfacing), validated live by an RCA in which the old feasibility filter was found silently excluding high-value directions. A fifth round extracted the allocation doctrine — Allocation is Decide, human-tool interface discipline, Turk decomposition, and the open-invocation register (`docs/pending-owner-TEMPLATE.md`) — after live operation showed Owner-attention margin repeatedly consumed by bare questions, unscanned inversions, and unscored tool selection; the proposal was Critic-falsified in first draft, repaired against the findings, scored option-ranked, and adopted by Owner ruling before extraction.

`ARCHITECTURE.md`'s Engineering Invariants and Banned Patterns were distilled from a RAROC review of the max-raroc-engineering spec: boundary defense, idempotent mutations, expand/contract migrations, vertical slicing, and integration-over-mocking were adopted; the decorative capital formula and the wholesale TDD ban were rejected in favor of this scaffold's TDD discipline and Acceptable/Gap coverage machinery.

`HORIZONS.md` condenses the Progressive RAROC paradigm (PRAROC-7), preserved in full at `docs/praroc-paradigm.md`. It supplies what the single-scalar selector lacked: the old cycle ranked but never excluded (unbounded terminal position — nothing priced the end of pricing), and its Repair loop had no trigger distinguishing repeated successful repairs from an expired decomposition (Adaptation standing in for Revision, unsignaled by construction). Filter-before-rank, profile-not-total, marginal-not-level allocation, and the error-signature audit entered through this integration.
