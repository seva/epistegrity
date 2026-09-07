# Architecture

---

## Principles

**Separation of concerns** — auth, storage, transport, business logic, and interface layers are separate modules. No cross-cutting logic.

**Isolation of fragility** — unstable dependencies (external APIs, undocumented interfaces, third-party services) are contained in a single module. When they change, only that module updates. Nothing else knows about their internal shape.

**Security** — sensitive data never in plaintext on disk or in logs. Secrets never surfaced in tool or API output.

---

## Coding Hygiene

Guard clauses. Graceful degradation. No silent failures. Explicit error types.

Code as documentation — names and structure must be self-explanatory. Comments explain why, not what. Maximize semantic and cognitive ROI.

---

## Engineering Invariants

Enforced at audit (METHODOLOGY.md Post-Phase Audit, item 5). Deviations must be declared in `CLAUDE.md` Conventions with rationale — undeclared violations are gaps.

**Boundary defense** — all untrusted input (HTTP parameters and bodies, queue messages, environment variables, files from other systems) passes a runtime schema parser at the ingestion boundary. Internal code trusts validated contracts and omits redundant defensive checks for guaranteed fields. Never pass unvalidated dynamic types into domain functions.

**Re-entrant mutations** — every state-altering operation (write endpoints, queue consumers, scheduled jobs) accepts an idempotency key or deterministic deduplication token, checked atomically before execution, with the result written back on completion. Financial and counter mutations never execute without an explicit transaction lock or idempotency guard.

**Non-destructive schema evolution** — migrations run Expand → dual-write → backfill → Contract, each in a distinct deployment; forward- and backward-compatible with N−1 running instances. Substrates that cannot contract (deployed smart contracts, append-only stores) substitute versioned parallel deployment; the substitution is recorded under Constraints.

**Vertical slice locality** — code grouped by domain feature, not technical layer. A feature slice co-locates its route, schema, domain rules, and queries. A single business-capability change touching more than three distinct folders is a design smell — reject or document the exception.

**Indirection cap** — at most three hops within a feature domain: handler → domain rule → persistence. Abstractions generalize only after the same logic occurs at ≥3 production call-sites (Rule of Three).

---

## Banned Patterns

| Pattern | Replacement |
|---|---|
| Generic repository abstraction over the ORM | Native ORM queries or type-safe compiled SQL directly in the slice |
| Premature microservices | Modular monolith with language-enforced visibility boundaries |
| Global DRY across bounded contexts | Context-local duplication; integrate through contracts, not shared models |
| Speculative OOP (AbstractFactory, Strategy/Visitor classes for one implementation) | Functions, guard clauses, native pattern matching |
| Unstructured logging | Structured logs with correlation/trace/tenant IDs propagated across async boundaries |
| Mock-testing internal boundaries; tautological tests asserting mock calls | Real ephemeral dependencies (Testcontainers or local instances); mocks only for external third-party APIs |

---

## System Diagram

<!-- Draw your system here. Show: external actors (users, services, APIs), internal modules, and the data flows between them. Arrows should indicate direction of data or control. -->

```
[replace this block with your diagram]
```

_Last verified: YYYY-MM-DD_

---

## Components

<!-- One row per module or major component. Name = the file or package. Responsibility = what it owns, in one sentence. Key interface = the public surface other modules call. -->

| Component | Responsibility | Key interface |
|---|---|---|
| | | |

_Last verified: YYYY-MM-DD_

---

## Design Decisions

<!-- Record decisions here as they are made. Each row is a choice that was non-obvious or that trades off competing concerns. Rationale should be specific enough that a future contributor understands why the alternative was rejected. -->

| Decision | Choice | Rationale |
|---|---|---|
| | | |

_Last verified: YYYY-MM-DD_

---

## Constraints

<!-- Non-negotiable limits on the system. Examples: platform requirements, runtime environment, compliance rules, external service dependencies, licensing. -->

-

_Last verified: YYYY-MM-DD_
