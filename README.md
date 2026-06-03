# AI Game Design Skill

## How to Use

Invoke this skill when you want Codex to prepare a game project before code implementation begins.

Example prompts:

```text
Use $ai-game-design to create pre-development GDD and project management docs for this game.
```

```text
Use $ai-game-design to turn this game idea into a one-page GDD, full GDD, AI-facing GDD, task board, milestones, and split implementation docs.
```

```text
Use $ai-game-design to optimize the project documentation workflow for an AI-led game project.
```

The skill is especially useful when:

- The game is still in design/planning stage.
- The project will be implemented mostly or entirely by AI.
- Future coding sessions should avoid rereading one huge GDD.
- The project needs clear milestones, task tracking, test gates, and development rules.
- UI tasks must include real-resolution visual acceptance rather than relying only on headless tests.

## Documents This Skill Generates

### `One_Pager_GDD.md`

A short alignment document covering the game intro, design pillars, core systems, and first-version success criteria.

### Full Human-Facing GDD

Usually named `GDD.md` or `[ProjectName]_GDD.md`. This is the readable design source for humans, covering gameplay, UI/UX, audio, art direction, modes, progression, content, tutorial, accessibility, scope, and acceptance criteria.

### `forAI_GDD.md`

An implementation-facing GDD for future AI coding sessions. It may include architecture, data models, state machines, module boundaries, signals/events, rules, edge cases, tests, debug tools, and implementation order.

### `DataNamingConventions.md`

A naming and ID guide for directories, files, scripts, resources, static data, localization keys, save fields, and tests.

### `GDD/forAI_Split/*.md`

Context-efficient split documents extracted from `forAI_GDD.md`. These are organized by implementation area, such as architecture, data, rules, scoring, UI, AI, audio/art/localization, save/tutorial/QA, and implementation order.

### `Milestone.md`

A phase roadmap that divides development into clear milestones with goals, required work, and acceptance criteria.

### `TaskBoard.md`

A live task tracker grouped by milestone, using statuses such as `Todo`, `Doing`, `Blocked`, `Review`, and `Done`.

### `DevGuidelines.md`

A project-specific AI development contract covering encoding, deletion limits, rule authority, code conventions, protected data, batch modification rules, testing expectations, UI constraints, and exception handling.

### `TestPlan.md`

A verification plan covering automated tests, manual tests, smoke tests, regression checkpoints, blocking bugs, and platform/export checks.

### `DefinitionOfDone.md`

Completion criteria for tasks, rule systems, UI work, data work, AI behavior, and milestones.

### `RiskRegister.md`

A risk tracking document with risk IDs, probability, impact, mitigation, and status.

### `DocumentMap.md`

A navigation guide explaining which documents exist and which ones future AI sessions should read for each task type.

### `WorkSessionProtocol.md`

A repeatable workflow for future AI coding sessions: what to read, how to implement, how to verify, and how to close out.

### `ReleaseChecklist.md`

A release-readiness checklist for rules, data, UI, AI, audio/art, platform export, and build records.

### `Changelog.md`

An append-only implementation history recording completed tasks, changed systems, tests run, important fixes, and known verification gaps.

## UI Visual Acceptance Requirement

For any UI-related game task, this skill requires real-resolution visual acceptance. This applies to game screens, table layouts, card display, bottom action areas, overlays, settings pages, stats pages, and UI changes caused by audio or art integration.

Required checked resolutions:

- Default window size
- `1280x720`
- `1366x768`
- `1600x900`
- `1920x1080`

Headless tests, scene-load checks, button-existence checks, and logic tests cannot replace visual inspection. If the environment cannot show the running game or produce screenshots, the task must report the incomplete visual acceptance state and cannot be marked `Done`.

## Included References

- `references/document-blueprints.md`: concise generation rules for the main documents.
- `references/project-document-catalog.md`: full document catalog with purpose, content, and update rules.
- `references/dev-guidelines-template.md`: reusable DevGuidelines template for AI-led game projects.
- `references/ui-visual-acceptance.md`: mandatory real-resolution UI visual acceptance standard.

## Notes

- Keep human-facing design docs readable and avoid code details unless requested.
- Keep AI-facing docs specific enough for implementation without rereading the full GDD.
- Separate stable English IDs from localized display text.
- For split GDDs, avoid omission or summarization when the user asks for exact splitting; validate by rejoining the split files.
- Do not mark UI work as complete unless real-resolution visual acceptance is complete.
