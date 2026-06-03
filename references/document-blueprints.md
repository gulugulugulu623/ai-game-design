# Document Blueprints

Use these blueprints when creating pre-development game design and project management docs for an AI-built game.

## Recommended Writing Order

1. `One_Pager_GDD.md`
2. Full human-facing `GDD.md`
3. `forAI_GDD.md`
4. `DataNamingConventions.md`
5. `ProjectManagement/Milestone.md`
6. `ProjectManagement/TaskBoard.md`
7. `ProjectManagement/DevGuidelines.md`
8. Supplemental project management docs
9. `GDD/forAI_Split/*.md`
10. `ProjectManagement/Changelog.md` once implementation begins
11. Validation summary

For complete per-document generation rules, including all split GDD files and project management documents, see `project-document-catalog.md`. For UI/game-screen visual validation gates, see `ui-visual-acceptance.md`.

## One_Pager_GDD.md

Purpose: align quickly on the game before detailed work.

Include:

- Version/date/platform/engine if known.
- Game intro.
- Primary mode or rules version.
- 3-5 design pillars.
- Explanation of how design pillars resolve tradeoffs.
- Core systems and gameplay loop.
- Scoring/progression/outcome summary.
- First-version success criteria.
- Sources or references when research was used.

## Full Human-Facing GDD

Purpose: let a human understand the whole game without reading code. Name it `GDD.md` or use a project-specific name such as `Hanafuda_GDD.md` when that improves clarity.

Include:

- Overview and target experience.
- Rule or gameplay version choices.
- Design pillars.
- Game modes.
- Core loop and moment-to-moment play.
- UI/UX flows and screens.
- Audio and BGM direction.
- Visual/art direction.
- Cards/items/characters/enemies/levels/content lists.
- Scoring, balance, progression, or economy.
- AI opponent or NPC behavior at a design level.
- Tutorial/onboarding.
- Accessibility and localization.
- Scope: must-have and can-delay.
- Acceptance criteria.
- References.

Do not include code details unless the user asks for an implementation-facing GDD.

## forAI_GDD.md

Purpose: give future AI coding sessions enough structure to implement safely.

Include:

- Source design document reference.
- Target engine/version/platform/language.
- Project contract, non-goals, and constraints.
- Recommended directory structure.
- Module responsibilities.
- Data models.
- Stable IDs and enums.
- Static data schemas.
- Runtime state structures.
- State machines.
- Commands, events, signals, or presenter boundaries.
- Rule edge cases.
- Scoring/outcome logic.
- UI implementation notes.
- AI behavior, fairness, and constraints.
- Audio/art asset event keys.
- Localization and accessibility.
- Save/settings/statistics.
- Tutorial and debug tools.
- Testing plan.
- Recommended implementation order.
- Real-resolution visual acceptance requirements for UI-related work.

## DataNamingConventions.md

Purpose: prevent drift in IDs, data files, localization, saves, and tests.

Include:

- General ID principles.
- Directory naming.
- Scene/resource/script naming.
- Code naming.
- Domain-specific ID tables.
- Category/tag enums.
- Rule setting field names.
- Localization key patterns.
- Save field names.
- Test naming.
- Forbidden patterns.

Always separate stable IDs from display text.

## Milestone.md

Purpose: divide the project into development phases with clear exit criteria.

Include:

- One milestone per meaningful phase.
- Goal for each milestone.
- Must-complete items.
- Acceptance criteria.
- Release or handoff condition.

Recommended phases:

1. Documentation/project contract.
2. Engine/project foundation.
3. Static data and validation.
4. Core rules.
5. Scoring/outcome logic.
6. Playable prototype.
7. AI/opponent behavior.
8. Complete UI.
9. Tutorial/onboarding.
10. Audio/art assets.
11. Save/settings/progression.
12. QA/export/release candidate.

## TaskBoard.md

Purpose: track real-time task completion.

Use status values:

- `Todo`
- `Doing`
- `Blocked`
- `Review`
- `Done`

Group tasks by milestone. Each task should be small enough to complete in a focused session.

## Supplemental Management Docs

Create these when the project is expected to continue across many sessions:

- `TestPlan.md`: automatic tests, manual tests, smoke tests, blocking bugs.
- `DefinitionOfDone.md`: completion rules for tasks, UI, data, rules, AI, milestones, including real-resolution UI visual acceptance.
- `RiskRegister.md`: risk ID, probability, impact, mitigation, status.
- `DocumentMap.md`: what each doc is for and what to read for each task type.
- `WorkSessionProtocol.md`: how future AI sessions start, implement, verify, and close.
- `ReleaseChecklist.md`: release readiness checklist.
- `Changelog.md`: append-only record of implementation progress after coding starts.

## Split GDD

Purpose: reduce future context usage by loading only the relevant design slice.

Recommended split files:

- `00_Index.md`
- `01_Project_Contract_Architecture.md`
- `02_Data_Model_Static_Data.md`
- `03_Rules_Turn_State_Machine.md`
- `04_Scoring_Outcome.md`
- `05_UI_UX_Flow.md`
- `06_AI_Behavior.md`
- `07_Audio_Art_Localization.md`
- `08_Save_Tutorial_QA.md`
- `09_Implementation_Order.md`

Adjust names for the game domain. For a combat game, `04_Scoring_Outcome.md` may become `04_Combat_Balance.md`; for a card game, it may become `04_Yaku_Scoring.md`.

Validation requirement: if the user requests no omission, split by exact extraction and verify rejoining the files equals the source AI GDD.

## UI/UX Visual Acceptance

Any UI/UX blueprint, test plan, definition of done, or release checklist must require real-resolution visual acceptance for UI-related work. Include the default window size plus `1280x720`, `1366x768`, `1600x900`, and `1920x1080`.

The UI acceptance rule must state that headless smoke tests, scene loading, button existence, and logic tests cannot replace actual running-game or screenshot inspection. If the environment cannot perform the visual check, the task must report `未完成分辨率视觉验收` and remain non-Done.
