# WF

`WF` is an explicit project-mode skill for Codex. It is designed for repository work that needs structured catch-up, planning, architecture maintenance, implementation discipline, and lightweight tracking without making that workflow always-on.

The explicit trigger is `$wf`.

## Why It Exists

This skill keeps normal chat and writing unstructured by default, then adds a predictable project workflow only when you ask for it.

Use it when you want Codex to:

- bootstrap docs and tracking for a new project
- catch up on an existing repo
- update architecture docs
- plan tracked work
- implement scoped changes
- review or debug current behavior

## Install

Copy this folder to:

```text
~/.codex/skills/wf/
```

The internal skill name is lowercase `wf` for validator compatibility. The UI display name can still appear as `WF`.

## Usage

Examples:

```text
use $wf, I'm starting a new project for ...
use $wf and review this repo
use $wf and plan feature X
use $wf and update the architecture for subsystem Y
use $wf and debug the current check-in flow
```

## Common Use Cases

- New project bootstrap
  - `use $wf, I'm starting a new project for ...`
- Existing project catch-up
  - `use $wf and review this repo`
  - `use $wf and catch me up on this project`
- Planning
  - `use $wf and plan feature X`
  - `use $wf and break this into tasks`
- Implementation
  - `use $wf and implement feature X`
  - `use $wf and fix bug Y`
- Architecture updates
  - `use $wf and update the architecture for subsystem Y`
  - `use $wf and document this repo structure`
- Review and debugging
  - `use $wf and review this change`
  - `use $wf and debug the current check-in flow`

## What It Does

- treats `ARCHITECTURE/current/` as canonical
- avoids `ARCHITECTURE/archive/` by default
- reads only the relevant docs and code for the task
- uses `TODO.md` for active tasks and near-next work
- uses `LOG.md` only for milestones, decisions, and handoff notes
- prefers subsystem-level architecture docs over overly fragmented micro-docs

## What It Does Not Do

- it is not a permanent always-on mode
- it does not read the full architecture tree by default
- it does not replace code inspection with documentation
- it does not encourage per-function architecture docs by default

## Recommended Architecture Doc Model

Use a two-layer architecture model:

- top-level docs for cross-cutting truth
- subsystem docs for bounded behavior areas

For a focused task, the ideal read set is usually:

- `01-project-intent.md` only if product intent matters
- one relevant top-level doc
- one relevant subsystem doc
- `04-repo-map.md` only when code location is needed

If one task repeatedly needs many scattered top-level docs, consolidate the detailed behavior into a subsystem doc instead.

## Example Subsystem Taxonomy

These are examples of good subsystem slicing, not required filenames:

- `auth-session-and-timezone`
- `wake-flow-and-checkin`
- `room-risk-and-atonement`
- `companion-lifecycle-and-reveal`
- `offline-queue-and-lifecycle`
- `room-membership-and-joins`

The naming principle is to describe the bounded behavior a contributor actually needs to understand, not to create vague buckets or one doc per tiny unit.
