# Implementation Plan

---

## Phase 0 — Discovery

Must complete before writing implementation code that depends on external interfaces, APIs, or undocumented contracts.

<!-- List the research tasks required to establish ground truth before building. Each task should produce a concrete, committed output in docs/. -->

- [ ] [research task — e.g. read source, trace requests, cross-reference references]
- [ ] [record findings in `docs/[artifact].md` — this file is the hard gate for Phase N]

**Outputs:** structured discovery artifact committed to `docs/`.

---

## Phase N — [Name]

<!-- Replace N with phase number and give it a short goal-oriented name. -->

**Goal:** [one sentence — what capability exists when this phase is complete]

### Tasks

<!-- TDD order: test task FIRST, then implementation task. -->
<!-- File paths must use the language/runtime declared in CLAUDE.md Conventions. Decide that before filling in paths. -->
<!-- Test file naming follows the test runner convention declared in CLAUDE.md (e.g. *.test.ts for Vitest, test_*.py for pytest). -->

- [ ] `tests/[module]/[test file]`
  - [test case description]
  - [test case description]
- [ ] `[source file]`
  - [implementation note]
  - [implementation note]

**Verification:** [concrete, observable statement that proves this phase is done — e.g. "X tests pass; live call returns Y"]

---

## Open Questions

<!-- Unresolved unknowns that may affect implementation. Move to ARCHITECTURE.md Design Decisions when resolved. -->

1. [question] — [status: open / resolved in Phase N]

---

## Dependencies

<!-- Libraries, runtimes, or services this project requires. -->

```
[paste your dependency manifest here — e.g. package.json, pyproject.toml, go.mod]
```
