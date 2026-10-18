# Architecture and execution flows

[English](architecture.md) | [Русский](architecture.ru.md)

Poe Bot combines a decision-and-execution runtime, planning tools, and the PoeFleet management application. The architecture below describes the private implementation reviewed on **2026-10-18**, including local uncommitted work. It is a conceptual view of existing connections, not a deployment guide or a frozen release specification. Status details are in the [feature catalog](features.md).

## System boundaries

| Area | Responsibility | Important distinction |
| --- | --- | --- |
| Observation | External reads, parsing, compatible state, partial errors | Missing data is not automatically a negative observation |
| Decisions | Mapper lifecycle, campaign components, combat policy, exploration, encounter and supply choices | Selecting an action is separate from executing it; the campaign entrypoint is blocked |
| Interaction | Host/guest input and screen transport, adapters, held state, reconnects | Logical separation is not a security guarantee |
| Planning | Build import, passive graphs, knowledge ETL and queries | A plan can exist without a connected UI executor |
| Management | Fleet sessions, slots, jobs, configuration, frontend | Operator job state is distinct from in-game progress |
| Observation of execution | Renderer, collector, observer bridge, resource sampling | Different streams have different meanings and completeness |

## 1. From observation to an action

**External reader → parsing and compatible state → behavior decision → movement/combat/UI action → host/guest interaction → next observation.**

The reader covers the player, entities, terrain, skills, inventory, stash, ground labels, UI text, and Atlas. It can expose available state alongside partial errors. Acquisition and interpretation are separate, so a consumer does not need to implement its own data-reading mechanism.

A navigation decision can use terrain and an objective to construct an A* route, check line of sight and clearance, and smooth the result. Exploration supplies discovery goals; doors, transitions, and unreachable targets change how a route is executed. Combat evaluates declarative priorities and eligibility gates while coordinating with movement. Input adapters then carry out the chosen interaction, accounting for held state and reconnects.

The next observation provides feedback rather than treating a sent input as proof of success. Transfer, insertion, and purchase checks use this distinction in their respective workflows. Position and map-progress watchdogs supervise different scales of progress and remain WIP.

## 2. The mapper cycle and its interruptions

**Prepare → select and activate a fresh instance → enter → explore and handle encounters → return → reset.**

Preparation joins inventory/stash work and MapPrep: preserve consumables, make space, identify and roll waystones within a budget, and handle tablets. When supplies need replenishment, the market workflow parses offers, normalizes currencies, filters and groups them, verifies purchases, and returns to preparation.

Atlas selection contributes ranking, mechanics filters, frontier or manual targets, panning, and text fallback. The newer insertion path checks an inventory delta. Fresh-instance handling and old-portal prevention keep activation separate from accidental reuse of the previous cycle.

During exploration, navigation, combat, loot pickup, and encounter handlers share the map objective. The unfinished-mechanic registry and repeated sweeps preserve the distinction between visiting an area and finishing its work. Boss status and forced-exit reasons are tracked separately.

**Inventory pressure → mid-map stash trip → transfer verification → return through the map portal, or lost-portal handling.** This is an interruption of the current cycle, not necessarily a completed map or the start of a new one.

Fake integration tests cover lifecycle coordination, not a full live run. The collector's `map_complete` records return to town; MAP-REPORT separately describes forced exits, boss state, and unfinished mechanics. A return event must not collapse those outcomes into “fully cleared.”

## 3. Knowledge, build plans, and campaign execution

**Lua/data → ETL → SQLite → query API → campaign and build plans.** This is an offline tooling boundary, not a hosted knowledge service.

**Path of Building XML/codec → BuildSpec → graph-based passive plan.** Build import and passive planning have standalone tests; Atlas passive planning is also separate. Planning data is not evidence that passive nodes can be selected in the game: that UI executor is unavailable/stubbed. Gem-cutter prototype code exists, but dependent gem setup is unreachable through the current campaign entrypoint.

**Current campaign entrypoint → campaign/passive-plan wiring defect → runner initialization failure, before campaign execution.** The loaded campaign plan is replaced with passive-progression data or no plan, so the runner does not receive the campaign structure it requires. This blocks the path before campaign behavior and dependent gem setup can run; it is not a working connected prototype awaiting only live verification.

Campaign components for acts, zones, quests, town actions, transitions, waypoints, bosses, and a leveling-to-endgame rebuild are implemented despite that startup blocker. Their decision logic partly depends on quest heuristics because dedicated quest and waypoint readers are missing; NPC dialogue is degraded.

**End-of-campaign code: mapper handoff message only.** This code is not reached through the blocked entrypoint. Even apart from the startup defect, there is no automatic final transition into the mapper, and no demonstrated campaign end-to-end run. Neither startup nor the final handoff is shown as a completed continuous campaign-to-mapping flow.

## 4. Fleet management and configuration

**Fleet frontend / Qt shell → authenticated API → FIFO job lifecycle → RealBackend session wiring → runner and slot lifecycle.** Cancellation and terminal job states belong to the management layer, alongside runner controls. They describe the requested operation, not whether every game objective was completed.

The existing interface exposes instance and map-bot views, an account wizard, resource and proxy views, mapper/market/Atlas settings, statistics, jobs, and appearance controls. It was not rendered for this documentation; the architecture does not depend on publishing interface captures or account setup steps.

Session/token authentication and login throttling support API access. Configuration has version migration, validation, atomic writes, and masking. UI preferences are distinct from mapper settings that can be reread during execution. These are implemented management controls, not a certification of the separate guest transport trust boundary.

## 5. Observability and resource analysis

Three related views serve different questions:

- **Map renderer:** terrain, entities, the movement trail, and explored space explain the spatial state.
- **Event collector and history:** transitions, deaths, degraded states, and private export capabilities explain what happened over time. Completion-event semantics remain narrower than a full-clear claim.
- **Observer bridge:** new uncommitted work hooks mapper snapshots of player, entities, path, goal, and behavior into a structured observation stream. It is not a standalone bundled dashboard.

Resource analysis is another path: presets can be verified and applied, a governor manages CPU plans, and A/B tooling compares distributions. Historical collector CPU/RAM may be missing, while Fleet snapshots sample resources separately. Pooled process samples labeled `TOTAL` are not a concurrent aggregate. Simulation and diagnostic output do not establish real fleet throughput.

## Engineering value and provenance

The transferable work is in coordinating feedback loops, explicit lifecycles, declarative policy, planning/execution boundaries, job cancellation, configuration evolution, and interpretable telemetry. These are useful engineering subjects even without distributing the game-facing implementation.

The project is based on **tachikoma-av/poe_bot**. This project's development extends upstream with the external reader and declarative build engine, the PoE2 campaign runner, Fleet, and market UI work. Inherited movement and combat foundations are not claimed as exclusively original work.

[Current stage](current-stage.md) · [Showcase content](what-will-be-shown.md) · [Overview](../README.md)
