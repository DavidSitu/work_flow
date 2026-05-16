# Doc Update Rules

Use this file to decide which architecture doc should change. Use `references/architecture-structure.md` as the source of truth for the standard `ARCHITECTURE/` folder contract and file responsibilities.

## Architecture Shape

Use a two-layer architecture model by default:

- top-level docs for cross-cutting truth
- subsystem docs for bounded behavior areas

Use `references/subsystem-planning-rules.md` for subsystem granularity, ownership, import, and test decisions. Do not duplicate those rules here.

## Top-Level Docs

- Use `ARCHITECTURE/current/01-project-intent.md` for rich stable product intent: cleaned idea summary, product goals, target customer or users, core problem, value proposition, product principles, scope, non-goals, constraints, current phase, and success direction.
- Use `ARCHITECTURE/current/02-milestones.md` for MVP/V1, Post-MVP/V1.x, optional Future/V2+, roadmap direction, milestone direction, phase direction, final-product direction, MVP user journey flow, page capability scope, required buttons/controls, required states, and acceptance signals.
- Use `ARCHITECTURE/current/03-overall-system-design.md` for system boundaries and architecture flow.
- Use `ARCHITECTURE/current/04-overall-ui-design.md` for UI design direction, visual language, navigation model, layout patterns, interaction conventions, responsive/accessibility expectations, and screenshot/prompt-derived UI decisions; mark it `N/A` for projects without a UI.
- Use `ARCHITECTURE/current/05-repo-map.md` for codebase layout and doc-to-code mapping.
- Add an ADR under `ARCHITECTURE/decisions/` only when a decision materially constrains future architecture work.

## Product And UI Routing

- Accepted product/function/UI input: distill accepted project truth into `01-05`; keep rich cleaned product intent in `01`; do not store the raw full brief by default.
- Do not create business strategy, GTM, PMF analysis, pricing, or promotion docs during normal Project Orchestrator architecture updates.
- Product idea, product-market-fit hypothesis, target customer, user motivation, product principles, scope, and non-scope belong in `01`.
- MVP/Post-MVP functional scope, MVP user journey, required pages, page logic, buttons/controls, required states, and acceptance signals belong in `02`.
- System boundaries, data flow, integrations, runtime shape, and subsystem responsibilities belong in `03`.
- Visual style, navigation, layout, interaction conventions, responsive/accessibility rules, and decisions from screenshots, images, Figma-like prompts, or UI prompts belong in `04`.
- Folder ownership, entrypoints, module responsibilities, generated code, and doc-to-code mapping belong in `05`.
- Deep workflow internals, state machines, data contracts, API contracts, lifecycle behavior, and cross-layer behavior belong in subsystem docs.

Keep the `02` and `04` split clear: `02` says what the MVP UI must functionally include; `04` says how the UI should be designed and experienced.

## Subsystem Docs

Use `references/subsystem-planning-rules.md` when deciding whether a subsystem doc should exist or how its code/test boundaries should work.

Create or update a subsystem doc when a change affects one specific area's:

- purpose or scope
- boundary contract, public API, or internal ownership
- flows and transitions
- states and rules
- APIs, RPCs, jobs, or data dependencies
- code map
- import rules or test strategy
- known gaps
- safe extension points

Name subsystem docs by bounded behavior, not vague buckets. Do not create subsystem docs for individual functions, hooks, helpers, widgets, or pages unless `references/subsystem-planning-rules.md` justifies the boundary.

For a focused task, the ideal documentation read set is usually:

- `01-project-intent.md` only if product intent matters
- `02-milestones.md` only if roadmap, phase, milestone, or session planning depends on it
- one relevant top-level doc
- one relevant subsystem doc
- `05-repo-map.md` only when code location is needed

If a focused task keeps requiring many scattered top-level docs, move the detailed behavior into a subsystem doc instead of fragmenting the top-level set further.

For global architecture requests, including "global view," overall architecture, whole project direction, MVP plan, final product direction, repo structure, or broad subsystem boundaries, read enough `ARCHITECTURE/current/` context to preserve project-level judgment instead of forcing the focused-task read set.

## Archive Rules

- Do not update `ARCHITECTURE/archive/` during normal current-state work.
- Move a document into `archive/` only when it is no longer current but still valuable for history.
- Consult `archive/` only for historical comparison, migration context, or explicit user requests.
- During retrofit, merge still-current facts from old docs into the current docs before archiving useful historical material.
- Do not blindly rename existing numbered architecture files unless the user asked for retrofit or normalization and references can be updated cleanly.

## Drift Handling

If code and current docs disagree:

- treat code as runtime truth for what currently happens
- update `current/` if the runtime behavior is intentional and should become the new documented truth
- otherwise, record the mismatch in the relevant current doc and add a task in `TODO.md`
