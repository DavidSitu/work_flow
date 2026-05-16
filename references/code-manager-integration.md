# Code Manager Integration

Use this reference when `$po` implementation coordination needs detailed code organization or refactor execution.

`$po` owns project workflow and memory:

- active session selection
- `TODO.md` and `LOG.md`
- `ARCHITECTURE/current/`
- subsystem docs as the canonical contract
- milestone direction
- ADR triggers

The separate `code-manager` skill owns coding execution details:

- physical file layout
- file naming
- subsystem public APIs
- internal file boundaries
- import cleanup
- test placement
- TDD loops
- diagnosis loops
- safe file moves and large-file splits
- focused verification

## When Project Orchestrator Should Hand Off

Use or suggest `code-manager` when a `$po` task involves:

- moving or splitting code files
- organizing code by subsystem
- fixing messy imports
- defining or tightening a public API
- deciding where tests should live
- applying TDD to a new behavior
- diagnosing a bug with reproduction and regression tests
- cleaning shallow modules or pass-through wrappers
- refactoring without changing behavior

## Shared Contract

Project Orchestrator subsystem docs define the contract.

Code layout implements the contract.

Tests prove the contract.

Milestones become code through verified TODO sessions, but TODO sessions do not define file boundaries. A session is one testable capability slice. A module or file is one coherent ownership boundary. Functions are implementation details inside that boundary.

Do not create one file per function or one file per checklist item. Split files by subsystem ownership, data ownership, dependency direction, lifecycle, independently testable behavior, or repeated reasons to change. Prefer compact deep modules over many shallow pass-through files.

The intended flow:

1. `$po` identifies the active milestone when relevant.
2. `$po` derives or selects the current TODO session.
3. `$po` identifies the affected subsystem.
4. `code-manager` aligns files, imports, public APIs, and tests to that subsystem contract.
5. `code-manager` implements the session inside the correct module boundaries.
6. `code-manager` verifies the session outcome.
7. `$po` records completed outcomes and updates docs only when project truth changes.

Do not duplicate the full code-manager rules inside Project Orchestrator. Keep Project Orchestrator focused on planning, architecture truth, and session tracking.
