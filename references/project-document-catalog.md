# Project Document Catalog

Use this catalog when the user wants a complete, reusable documentation system for AI-led game development. The catalog expands the short workflow in `SKILL.md` and the blueprint list in `document-blueprints.md`.

## General Generation Rules

- Write in the user's requested language.
- Prefer Markdown unless the user asks for another format.
- Place design docs under `GDD/`.
- Place execution docs under `ProjectManagement/`.
- Keep human-facing docs readable without code knowledge.
- Keep AI-facing docs implementation-ready and explicit about architecture, IDs, data, state, tests, and validation.
- Separate stable IDs from display text.
- Record assumptions, variants, and rule choices instead of burying them in later implementation.
- For documents meant to be updated during development, include clear status values, dates, or append-only sections.
- For split documents, do exact extraction when the user asks for no omission; validate by rejoining.

## GDD/One_Pager_GDD.md

Function: align the project quickly before detailed design.

Generate when:

- Starting a new game project.
- The user needs fast agreement on direction before writing a full GDD.

Include:

- Version/date/platform/engine/language if known.
- Game intro.
- Primary rules version or gameplay format.
- Design pillars and how they resolve tradeoffs.
- Core systems and loop.
- Scoring, progression, or win/loss summary.
- First playable success criteria.
- Research references when used.

Update rule:

- Keep short. If it becomes long, move detail into the full GDD.

## GDD/[ProjectName]_GDD.md Or GDD/GDD.md

Function: full human-facing design document.

Generate when:

- The project needs a readable design source for humans.
- The user asks for a complete GDD without code.

Include:

- Overview and target experience.
- Rule/gameplay version choices and optional variants.
- Design pillars.
- Game modes.
- Core gameplay loop.
- UI/UX flow and screens.
- Audio and BGM design.
- Visual/art direction.
- Content/data design such as cards, items, levels, units, roles, enemies, maps, or skills.
- Scoring, balance, economy, or progression.
- AI/NPC/opponent behavior at design level.
- Tutorial/onboarding.
- Accessibility and localization.
- Scope: must-have and can-delay.
- Acceptance criteria.
- References.

Update rule:

- Treat as the human design authority. If implementation reveals conflicts, report them and update deliberately.

## GDD/forAI_GDD.md

Function: implementation-facing design document for future AI coding sessions.

Generate after:

- One-pager and full human GDD.

Include:

- Source design document reference.
- Engine/version/platform/language.
- Project contract and non-goals.
- Engineering constraints.
- Recommended directories.
- Module responsibilities.
- Core data models.
- Stable IDs and enums.
- Static data schemas.
- Runtime state structures.
- State machines.
- Commands/events/signals/presenter boundaries.
- Rule edge cases.
- Scoring/outcome/combat/economy logic.
- UI implementation notes.
- AI behavior constraints and fairness boundaries.
- Audio/art/localization/accessibility implementation notes.
- Save/settings/statistics.
- Tutorial/debug tools.
- Tests and implementation order.

Update rule:

- Keep faithful to the full GDD. If the full GDD changes, update this document or record a conflict.

## GDD/DataNamingConventions.md

Function: prevent ID, file, localization, save, and test naming drift.

Generate when:

- The project will use structured data, assets, localization, saves, or tests.

Include:

- General ID principles.
- Directory naming.
- Scene/resource/script naming.
- Code naming.
- Domain-specific ID tables.
- Category/tag enums.
- Rule/config field names.
- Localization key patterns.
- Save field names.
- Test naming rules.
- Forbidden patterns.

Update rule:

- Treat stable IDs as migration-sensitive. Avoid renaming after data, saves, or tests depend on them.

## GDD/forAI_Split/00_Index.md

Function: entry point for split AI GDD usage.

Include:

- Source `forAI_GDD.md` context.
- Split map.
- Which split file to read for each task type.
- No independent design decisions that are not in `forAI_GDD.md`, unless explicitly marked as navigation metadata.

## GDD/forAI_Split/01_Project_Contract_Architecture.md

Function: project constraints and architecture boundary.

Include:

- Product scope.
- Non-goals.
- Engine/platform/language constraints.
- Recommended directories.
- Module responsibilities.
- Command/event/signal conventions.
- UI/rules/data ownership boundaries.

## GDD/forAI_Split/02_Data_Model_Static_Data.md

Function: data model and static data authority for coding sessions.

Include:

- Core enums.
- Static data schemas.
- Runtime instance/state data structures.
- ID lists.
- Rule set fields.
- Localization key expectations.
- AI evaluation context data if relevant.

## GDD/forAI_Split/03_Rules_Turn_State_Machine.md

Function: gameplay state machine and turn/phase logic.

Include:

- Match/session flow.
- Round/level/encounter setup.
- Turn or phase sequence.
- Legal action resolution.
- Edge cases.
- Structured logs or events.
- Failure, draw, reset, or retry rules.

## GDD/forAI_Split/04_Scoring_Outcome.md

Function: scoring, outcome, combat, yaku, economy, or win/loss rules.

Rename for the domain when useful, such as `04_Yaku_Scoring.md` for a Koi-Koi game or `04_Combat_Balance.md` for a battle game.

Include:

- Evaluation inputs.
- Category counts or stat calculations.
- Default scoring/outcome rules.
- Optional rule switches.
- Stacking/exclusivity.
- Multipliers/modifiers.
- Required examples and tests.

## GDD/forAI_Split/05_UI_UX_Flow.md

Function: implementation-ready UI and UX guidance.

Include:

- Screen flow.
- Primary screen layout.
- Interaction states.
- Inputs.
- Overlays/modals.
- Accessibility expectations.
- Required UI validation.
- Real-resolution visual acceptance requirements from `ui-visual-acceptance.md`, especially for game screens, table layouts, card display, bottom action areas, overlays, settings pages, stats pages, and audio/art-driven UI changes.

## GDD/forAI_Split/06_AI_Behavior.md

Function: AI/NPC/opponent behavior design for implementation.

Include:

- Fairness constraints.
- Visible and forbidden information.
- Decision inputs.
- Evaluation weights or heuristics.
- Difficulty tiers.
- Personality variants.
- Logging and validation needs.

## GDD/forAI_Split/07_Audio_Art_Localization.md

Function: asset, audio, localization, and accessibility implementation guidance.

Include:

- Audio event keys.
- BGM layers.
- SFX categories.
- Asset naming and paths.
- Art generation or import constraints.
- Localization rules.
- Accessibility requirements.

## GDD/forAI_Split/08_Save_Tutorial_QA.md

Function: persistent data, onboarding, tests, and debug support.

Include:

- Save fields.
- Settings.
- Statistics/progression.
- Tutorial order and fixed scenarios.
- Debug tools.
- Data/rule/UI test expectations.

## GDD/forAI_Split/09_Implementation_Order.md

Function: coding sequence for future sessions.

Include:

- Ordered implementation steps.
- What must remain playable after each phase.
- Minimal verification for each phase.

## ProjectManagement/Milestone.md

Function: phase roadmap and milestone acceptance document.

Generate when:

- The project will span multiple sessions or milestones.

Include:

- Milestone ID/name.
- Goal.
- Must-complete items.
- Acceptance criteria.
- Entry/exit condition when useful.

Update rule:

- Update only when the plan changes materially. Do not use it as a live task checklist; use `TaskBoard.md` for that.

## ProjectManagement/TaskBoard.md

Function: live execution tracker.

Include:

- Tasks grouped by milestone.
- Status values such as `Todo`, `Doing`, `Blocked`, `Review`, `Done`.
- Short notes or blockers.

Update rule:

- Update after meaningful work.
- Keep tasks small enough for one focused session.
- Do not mark a task done without verification or a clear explanation.
- Do not mark UI-related tasks as `Done` until real-resolution visual acceptance is complete. If the environment cannot perform visual inspection, leave the task non-Done and record `未完成分辨率视觉验收`.

## ProjectManagement/DevGuidelines.md

Function: AI behavior contract for the project.

Generate using:

- `references/dev-guidelines-template.md`, adapted to the game.

Include:

- Encoding and text rules.
- Deletion limits.
- Rule authority sources.
- Code conventions.
- Data file rules.
- Protected data types.
- Batch modification rules.
- Test requirements.
- AI fairness/visibility constraints.
- UI constraints.
- Real-resolution visual acceptance requirements for UI-related tasks.
- Work session workflow.
- Exception handling.

Update rule:

- Keep broadly stable. Add project-specific risks as discovered.

## ProjectManagement/TestPlan.md

Function: define how correctness will be verified.

Include:

- Test goals.
- Automated test categories.
- Manual test categories.
- Smoke tests.
- Real-resolution UI visual acceptance at default window size, `1280x720`, `1366x768`, `1600x900`, and `1920x1080`.
- A clear statement that headless tests validate logic/loading only and cannot replace UI visual acceptance.
- Regression checkpoints.
- Blocking bug definition.
- Platform/export checks.

Update rule:

- Add tests when new systems or known bug classes appear.

## ProjectManagement/DefinitionOfDone.md

Function: prevent premature completion claims.

Include:

- Single-task completion criteria.
- Rule/system completion criteria.
- UI completion criteria.
- Data completion criteria.
- AI completion criteria.
- Milestone completion criteria.
- A rule that UI-related work cannot be `Done` without real-resolution visual acceptance, or must explicitly remain incomplete with `未完成分辨率视觉验收`.

Update rule:

- Tighten when quality issues recur.

## ProjectManagement/RiskRegister.md

Function: track risks and mitigations across development.

Include:

- Risk ID.
- Risk description.
- Probability.
- Impact.
- Mitigation.
- Owner or status if useful.

Update rule:

- Append or update status. Do not erase historical risks unless explicitly archiving them.

## ProjectManagement/DocumentMap.md

Function: navigation guide for future sessions.

Include:

- Each document and its purpose.
- Which docs to read for each task type.
- Difference between human GDD, AI GDD, split docs, and management docs.

Update rule:

- Update whenever new docs are added, renamed, or split.

## ProjectManagement/WorkSessionProtocol.md

Function: repeatable workflow for each future AI coding session.

Include:

- Startup reading order.
- Implementation discipline.
- Verification expectations.
- Close-out requirements.
- Recommended session size.

Update rule:

- Keep short and operational. It should tell future AI how to start, work, verify, and stop.

## ProjectManagement/ReleaseChecklist.md

Function: release readiness gate.

Include:

- Rule/system checks.
- Data checks.
- UI checks.
- Real-resolution UI visual acceptance checks for default window size, `1280x720`, `1366x768`, `1600x900`, and `1920x1080`.
- AI checks.
- Audio/art checks.
- Platform export checks.
- Version/build record fields.

Update rule:

- Use as a checklist near release. Add project-specific release blockers as they are discovered.

## ProjectManagement/Changelog.md

Function: append-only implementation history.

Generate when:

- Development has started or milestones are being completed.

Include:

- Date headings.
- Completed milestones or tasks.
- Key files/systems changed.
- Tests or commands run.
- Actual real-resolution UI visual acceptance results for UI work, or an explicit `未完成分辨率视觉验收` note when the environment cannot perform the check.
- Important fixes.
- Known verification gaps when relevant.

Update rule:

- Append factual progress after implementation, not speculative plans.
- Keep newest date near the top unless the project prefers chronological order.
- Do not replace `TaskBoard.md`; changelog records history, task board tracks current status.
