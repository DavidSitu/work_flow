# Project Orchestrator

`Project Orchestrator` is an explicit accepted-plan-to-repo skill for Codex. It adds structured repository workflow only when invoked with `$po`.

Use it for:

- bootstrapping `ARCHITECTURE/`, `TODO.md`, and `LOG.md`
- retrofitting an existing repo into the Project Orchestrator structure
- catching up on current repo state
- converting accepted product, function, and UI direction into architecture docs
- planning milestones and session-sized work
- coordinating implementation handoff to `code-manager`
- reviewing or debugging current behavior

Do not use it as a general chat, product exploration, or business strategy mode.

## Install

This README is source-repo documentation. Do not include it in the installed skill payload.

Install only:

```text
SKILL.md
agents/openai.yaml
references/
```

Copy the payload to:

```text
~/.codex/skills/po/
```

The skill name is `po`; the user-facing trigger is `$po`.

## Usage

```text
use $po, I'm starting a new project for ...
use $po retrofit
use $po arche
use $po arche and plan the V1 milestones
use $po and catch me up on this repo
use $po and split this into sessions
use $po and plan feature X
use $po and implement feature X
use $po and review this change
use $po and debug the current check-in flow
```

## Workflow Model

```text
accepted direction -> ARCHITECTURE/current/ -> milestones -> TODO sessions -> implementation coordination -> LOG
```

Ownership split:

- `$po` owns project direction, architecture truth, milestones, `TODO.md`, `LOG.md`, and session coordination.
- `code-manager` owns file layout, code changes, imports, APIs, tests, refactors, diagnosis, and focused verification.
- Runtime code remains the source of truth for actual behavior.

## Standard Project Files

```text
ARCHITECTURE/
  README.md
  current/
    01-project-intent.md
    02-milestones.md
    03-overall-system-design.md
    04-overall-ui-design.md
    05-repo-map.md
    subsystems/
  decisions/
  archive/
TODO.md
LOG.md
```

`ARCHITECTURE/current/` is canonical. `TODO.md` is the active session queue. `LOG.md` is the completed-session record.

## Reference Map

- `architecture-structure.md`: standard architecture folder contract
- `doc-update-rules.md`: which architecture doc should change
- `milestone-planning.md`: MVP/V1/Post-MVP/Future/final-product direction
- `session-tracking.md`: `TODO.md` and `LOG.md` format
- `planning-rules.md`: session slicing and review shape
- `retrofit-rules.md`: existing repo adoption and preservation
- `subsystem-planning-rules.md`: subsystem boundaries, ownership, imports, and tests
- `subsystem-doc-template.md`: subsystem doc template
- `code-manager-integration.md`: handoff to `code-manager`
