---
name: map-legacy-codebase
description: Map the smallest safe change surface in a large or unfamiliar repository. Use before planning or editing a brownfield system, when documentation may be stale, or when the agent needs evidence about rules, execution paths, tests, and risks.
---

# Map Legacy Codebase

Build a task-specific map from repository evidence. Do not try to summarize the full repository.

## Workflow

1. Restate the requested change and the stop boundary.
2. Read local instructions first. Check `AGENTS.md`, `CLAUDE.md`, `CONTRIBUTING.md`, AI policies, and files in the task path.
3. Inspect manifests, package boundaries, test configuration, and the nearest similar implementation.
4. Trace one execution path from entry point to state change and test.
5. List only files that can affect the task. Give evidence for each file.
6. Record commands that are safe and relevant. Do not run broad or destructive commands.
7. Write the map with the format in `references/map-format.md`.

## Evidence Rules

* Cite file paths and line numbers when possible.
* Label an inference as an inference.
* Put unknown facts in `Open questions`.
* Do not edit code unless the user asks for implementation.
* Stop when repository policy blocks autonomous action.
* Revalidate the map when the repository revision changes.

## Completion Gate

The map is ready only when it names the repository revision, local rules, change surface, execution path, tests, risks, and open questions.
