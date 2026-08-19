---
name: archiving-work
description: Use when substantial discussion, research, planning, design, prototypes, or related work needs to be archived, saved for later, preserved, stashed, or packaged for resuming after a long pause or in a future session.
---

# Archiving Work

## Purpose

Create or update a durable, repository-local capsule for one paused effort. The archive succeeds when a future agent with no conversation context can quickly recover the goal, state, decisions, open questions, artifacts, canonical sources, and next action.

The entry document is a **resume map**, not a transcript or a second source of truth.

## Boundaries and reuse

- Archive only the effort-level recovery capsule.
- Use the repository's existing durable effort-directory convention. Otherwise use `.archive/<effort-slug>/README.md`.
- Use `domain-modeling` when a decision deserves a formal ADR, and use an existing planning skill such as `superpowers:writing-plans` or `planning-and-task-breakdown` when a plan must be created or revised. Link their outputs; do not reproduce their workflows here.
- Use `handoff` separately for session-to-session transfer. If an existing handoff contains unique durable state, preserve only that state; never use its temporary file as the archive.
- Treat existing specs, plans, ADRs, trackers, source files, issues, PRs, and commits as canonical at their existing locations.
- Do not plan, author ADRs, manage a tracker, or scan the whole repository as part of archiving.

## Workflow

### 1. Locate the effort

Prefer an explicit effort name or archive path. Before creating a directory, inspect only the established archive root and the artifacts named in the current work. Match an existing archive by goal and canonical references.

Update a unique match in place. If multiple archives could match, ask the user. Never create suffixes such as `-2`, `-final`, or `-v2` for another round of the same effort.

### 2. Extract working state

Use only the current conversation and explicitly related artifacts. Classify every relevant statement as:

- **Settled**: explicitly decided; include concise rationale when it prevents rework.
- **Open**: unresolved and still relevant.
- **Rejected / Superseded**: retain only when the outcome or rationale remains useful.

Never infer a decision from discussion. Move resolved questions out of Open Questions.

### 3. Apply the artifact policy

| Artifact | Treatment |
|---|---|
| Existing canonical artifact | Reference its repository-relative path or URL; do not copy it. |
| Ephemeral but necessary artifact | Persist it under the archive using the smallest useful structure, such as `artifacts/` or `research/`. |
| Noise | Omit it. |

Ephemeral artifacts include useful content that otherwise exists only in conversation, an OS temporary directory, a scratch file, or transient agent output. Persist only what a future agent needs. Do not save transcripts, raw debugging logs, repeated arguments, or superseded intermediate output.

For external research, record the stable URL, access date, and recovery-relevant finding. Persist a necessary excerpt or synthesis only when the source is ephemeral or inaccessible. Redact secrets and sensitive data.

### 4. Write or update the entry document

Use this semantic contract, adapting labels to repository conventions:

```markdown
# <Effort title>

Last updated: <date>
Status: Paused

## Goal
<Problem and intended outcome.>

## Current State
<What exists, what was completed, and where work stopped.>

## Settled Decisions
- **<Decision>** — <short rationale when useful>

## Open Questions
- **<Question>** — <missing input or smallest resolution step>

## Rejected / Superseded
- **<Option or former decision>** — <why it no longer applies, if worth retaining>

## Artifacts
| Artifact | Location | Role |
|---|---|---|
| <name> | `<path-or-url>` | <canonical, prototype, research, etc.> |

## References
- Spec: `<path-or-url>`
- Plan: `<path-or-url>`
- ADR / source / issue / PR / commit: `<path-or-url>`

## Resume
1. Read <first canonical document or artifact>.
2. Treat <settled scope> as decided; do not reopen it without new evidence.
3. Resolve <specific open question>.
4. Next action: <smallest concrete continuation step>.
```

Omit empty optional rows or sections. Keep `README.md` short enough to serve as the first read; move durable detail into a necessary artifact or canonical document.

### 5. Update an existing archive

Edit the original capsule in place:

1. Recompute Current State.
2. Add newly settled decisions.
3. Move resolved questions out of Open Questions and link them to their resolution.
4. Add new artifacts and references without copying canonical files.
5. Remove stale recovery instructions and update Resume.
6. Preserve only history that still prevents confusion or repeated mistakes.

Rely on Git history for chronology unless the repository already requires a changelog.

## Verification

Before finishing, verify that a context-free agent can answer:

1. What is this effort and why does it exist?
2. Where did work stop?
3. What is settled?
4. What remains open?
5. Which artifacts matter?
6. Where are the canonical documents?
7. What should happen next?

Also verify that referenced paths resolve, no item is both settled and open, temporary artifacts needed for recovery were persisted, canonical files were not copied, no transcript or unrelated repository content was saved, and no duplicate effort directory was created.

Do not commit or push the archive unless the user asks.

## Red flags

- A full conversation transcript or raw log appears in the archive.
- A canonical spec, plan, ADR, or source file was copied.
- The README summarizes history but lacks a concrete Resume section.
- An update created a timestamped or version-suffixed sibling directory.
- Archiving expanded into planning, ADR authoring, tracker management, or repository-wide collection.

If any red flag is present, fix the capsule before reporting completion.
