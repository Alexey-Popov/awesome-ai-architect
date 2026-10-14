---
name: save-project-memory
description: Save verified repository facts, decisions, working commands, risks, and handoff notes in durable project memory. Use after investigation or implementation so a later agent session can resume with less context loss.
---

# Save Project Memory

Store small, verified facts that will help the next session. Do not store a transcript.

## Workflow

1. Read the existing memory file before any update.
2. Extract only facts confirmed by code, tests, tool output, or an approved decision.
3. Add the source, repository revision, date, and confidence for each important entry.
4. Update the smallest relevant section. Remove duplicates.
5. Keep unresolved items separate from verified facts.
6. Use `assets/project-memory-template.md` when no memory file exists.

## Safety Rules

* Never store secrets, access tokens, personal data, or copied logs with sensitive data.
* Never convert an assumption into a fact.
* Mark stale information and revalidate it before reuse.
* Preserve user edits and unrelated entries.
* Default to `docs/ai-context/project-memory.md` unless the repository defines another path.

## Completion Gate

The update is ready only when another engineer can see what was confirmed, what changed, how it was verified, and what remains unknown.
