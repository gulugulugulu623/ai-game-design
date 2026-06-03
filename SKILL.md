---
name: ai-game-design
description: Create pre-development game design and project management documentation for AI-built games. Use when Codex is asked to design or plan a game before coding, write a one-page GDD, full GDD, AI-facing GDD, split GDDs for context-efficient future implementation, data naming conventions, milestones, task boards, DevGuidelines, test plans, release checklists, changelogs, real-resolution UI visual acceptance gates for game screens/layouts/overlays/settings/stats/audio-art UI changes, or a repeatable documentation workflow for solo AI game development.
---

# AI Game Design

Use this skill to turn an early game idea into an implementation-ready document set before coding starts. The goal is not only to write a creative GDD, but to create a durable operating system for future AI development: clear rules, stable data names, project management, task tracking, and context-efficient split docs.

## Core Workflow

Follow this order unless the user explicitly asks for a smaller subset:

1. Gather context.
2. Research unstable or domain-specific facts.
3. Write human-facing design docs.
4. Write AI-facing implementation docs.
5. Write data and naming conventions.
6. Write project management docs.
7. Split the AI-facing GDD.
8. Validate coverage and update task tracking.

For detailed document blueprints, read `references/document-blueprints.md`. For the full document catalog, including each document's role, generation rules, required content, update rules, and split-GDD coverage, read `references/project-document-catalog.md`. For any UI/game-screen/layout task, read `references/ui-visual-acceptance.md` and make its real-resolution visual acceptance rules part of the completion criteria.

## UI Visual Acceptance Is Mandatory

If a task involves UI, game screens, table layouts, card display, bottom action areas, overlays, settings pages, stats pages, or UI changes caused by audio/art integration, require real-resolution visual acceptance.

Headless smoke tests, scene-load tests, button-existence checks, and logic tests may support validation, but they cannot prove UI completion. If the environment cannot show the running game or produce screenshots at the required resolutions, report the exact incomplete-acceptance phrase defined in `references/ui-visual-acceptance.md`, do not mark the UI task as `Done`, and do not claim UI acceptance passed.

## 1. Gather Context

Identify and preserve:

- Engine, version, target platform, programming language, input method, and output folder.
- The intended game, genre, rules source, target audience, and scope.
- Existing project files, existing GDDs, style guides, or DevGuidelines.
- User constraints such as deletion limits, encoding rules, no-code sections, or required language.

If the user references an external rule set, game genre, software version, legal/license point, product, or anything likely to have changed, verify it with sources before locking design decisions.

## 2. Research The Design Domain

Before writing the design docs, understand the game deeply enough to make tradeoffs. For traditional games, read rules, scoring, variants, terminology, and common house rules. For original games, clarify the loop, constraints, fantasy, player goals, and failure states.

When rules vary, choose a default version and explicitly list optional variants. Do not hide house-rule assumptions inside later code docs.

## 3. Write Human-Facing GDDs

Create these first:

- `One_Pager_GDD.md`: short alignment doc with game intro, design pillars, and core systems.
- Full `GDD.md` or a project-specific name such as `Hanafuda_GDD.md`: comprehensive human-readable design doc. Avoid code details unless the user asks otherwise.

The full GDD should cover at least gameplay, modes, UI/UX, audio, art direction, content/data design, progression or scoring, tutorial/onboarding, accessibility, scope, and acceptance criteria.

## 4. Write AI-Facing GDD

Create `forAI_GDD.md` after the human GDD. This document may and usually should discuss code architecture.

Include:

- Project contract and non-goals.
- Recommended directories.
- Module responsibilities.
- Data models and stable IDs.
- State machines.
- Event/signal or command boundaries.
- Rule edge cases.
- UI presenter responsibilities.
- AI behavior constraints.
- Save/settings/statistics.
- Debug tooling.
- Tests and implementation order.

Keep the AI-facing GDD faithful to the human GDD. If a contradiction appears, document it and ask or choose a clearly labeled default when safe.

## 5. Write Naming And Data Conventions

Create a naming document such as `DataNamingConventions.md`.

Define:

- Directory and file naming.
- Script/class/function/signal naming.
- Static data IDs.
- Runtime instance IDs.
- Localization keys.
- Save fields.
- Test names.
- Forbidden patterns.

Use stable English IDs and separate them from display text. Do not use localized display strings as cross-file references.

## 6. Write Project Management Docs

Create a `ProjectManagement` folder with the minimum operating set:

- `Milestone.md`
- `TaskBoard.md`
- `DevGuidelines.md`
- `TestPlan.md`
- `DefinitionOfDone.md`
- `RiskRegister.md`
- `DocumentMap.md`
- `WorkSessionProtocol.md`
- `ReleaseChecklist.md`
- `Changelog.md`

Use `references/dev-guidelines-template.md` as the reusable DevGuidelines template. Adapt protected data types and high-risk rules to the specific game.

## 7. Split The AI-Facing GDD

Split `forAI_GDD.md` into context-efficient files, usually under `GDD/forAI_Split`.

Split by implementation boundary, not by arbitrary length:

- Project contract and architecture.
- Data model and static data.
- Rules and state machine.
- Scoring/combat/outcome logic.
- UI/UX flow.
- AI/opponent/agent behavior.
- Audio/art/localization/accessibility.
- Save/tutorial/QA/debug.
- Implementation order.

The split must not omit, summarize, or rewrite content unless the user explicitly asks for a condensed version. Prefer mechanical extraction from the source document, then validate by rejoining the split files and comparing them to the original.

## 8. Validate

Before finishing:

- List generated files.
- Confirm required docs exist.
- Confirm task board reflects completed documentation tasks.
- Confirm `DocumentMap.md` points future sessions to the correct GDD split and project management docs.
- If a `Changelog.md` exists, confirm it records implementation progress rather than design speculation.
- For split docs, verify the split reassembles to the source `forAI_GDD.md` after normalizing or preserving line endings.
- Report any docs skipped and why.

## Output Style

Write docs in the user's language unless they request otherwise. Use Markdown. Keep implementation docs specific enough for future coding sessions to act without rereading the full human GDD.
