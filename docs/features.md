# Feature catalog

[English](features.md) | [Русский](features.ru.md)

Twenty areas of the private implementation, based on the source review of **2026-10-18**, including committed code and uncommitted local work. This is a product catalog, not a list of proposed demos.

## How to read the statuses

- **Connected**: implementation is wired into a current execution path. This does not mean it has been verified in a live session.
- **Standalone tool**: a parser, planner, data pipeline, or diagnostic tool exists separately; its output does not imply automated in-game execution.
- **Prototype**: experimental components with material functional gaps; a blocked entrypoint is identified explicitly.
- **Unfinished**: a stub, unavailable action, detection-only capability, or integration not established by the review.

Statuses can differ within one area. Companion tests exist across the system, but none were freshly run for this documentation. [Current stage](current-stage.md) separates implementation evidence from verification.

## 1. External state reader

**Status: Connected.** The external reader supplies player state, entities, terrain, skills, inventory, stash, ground-item labels, UI text, and Atlas observations. A compatible state payload lets consumers use these observations without folding acquisition into every behavior. Partial errors are represented alongside available state rather than implying that every read succeeded.

This is the perception layer for navigation, combat, preparation, and UI-driven interactions. A partial observation is not proof that an entity, item, or UI element is absent.

## 2. Host/guest control and screen transport

**Status: Connected.** Coordination and environment-specific input/screen interaction are separated through host/guest transport. Reconnection behavior, held-input state, and foreground/background adapters are part of the control layer.

This keeps interaction mechanics out of higher-level decisions and makes session interruptions a separate concern from route or combat policy.

## 3. Navigation, exploration, and progress supervision

**Status: Connected; watchdog changes are work in progress.** Navigation combines A*, line-of-sight checks, obstacle clearance, route smoothing, and discovery routes. Movement supports mouse and WASD, doors, transitions, and handling of unreachable destinations.

Position-level and map-level progress watchdogs address different failures: an actor may fail to move, or may move without advancing the map objective.

## 4. Mapper lifecycle

**Status: Connected.** The main lifecycle joins preparation, activation of a fresh instance, entry, exploration, return, and reset. Old-portal prevention is part of keeping one map cycle distinct from the next.

Fake integration tests exercise lifecycle coordination. They are not evidence of a complete live map run, and returning to town is not by itself proof of a full clear. The lifecycle is the framework that connects the following encounter, inventory, and supply functions.

## 5. Declarative combat and builds

**Status: Connected.** Combat uses declarative priorities for skills, flasks, and auras, with buff and distance gates and sticky target selection. Leveling and endgame rotations coordinate with the mover instead of treating movement and attacks as unrelated loops.

The transferable idea is a policy layer that makes action eligibility and ordering explicit while allowing different rotations to share movement coordination.

## 6. Encounter handling and boss search

**Status: Connected for the listed handlers; other mechanics are unfinished.** Essence, Breach, Ritual, Delirium, strongboxes, shrines, and boss hunting participate in the mapper's handling paths. An unfinished-mechanic registry, repeated sweeps, and explicit forced-exit reasons distinguish work still outstanding from a normal return.

Expedition is detected but has no connected executor established here. Legion and Harbinger classes exist, but current wiring was not proven. Their presence must not be advertised as supported encounter execution.

## 7. Loot pickup and item policy

**Status: Connected.** Pickup uses ground labels and restrictions to decide which visible interactions to attempt. The game's loot filter owns the primary item-selection policy.

This is a pickup mechanism, not a price-estimation or market-valuation engine. Its scope should not be confused with the supply purchasing described in group 11.

## 8. Inventory, stash, and mid-map unloading

**Status: Connected.** Inventory handling considers free cells, preserves consumables, relocates items, and verifies transfers into the stash. A mid-map dump-and-return path allows inventory pressure to interrupt exploration without treating unloading as the next map cycle.

Lost-portal handling is part of that return path. Transfer verification and handling a missing return route address separate stages of the interruption.

## 9. Crafting and map preparation

**Status: Connected for MapPrep; named extensions are unfinished.** Identification, currency application, budgeted waystone rolling, and tablets are wired into map preparation. This connects item preparation to the lifecycle rather than leaving it as an isolated utility.

Omen handling, Well of Souls, and socketing remain stubs, not completed crafting features. Budget controls bound the preparation process.

## 10. Atlas selection and activation

**Status: Connected, work in progress.** Atlas selection includes ranking, filtering by mechanics, frontier selection, manual targeting, panning, and text fallback. The newer insertion path checks inventory delta as evidence of item insertion.

An old map-device limitation is not an accurate description of the current implementation: a newer path exists. That path and its UI verification remain WIP; an inventory change does not establish a successful full map cycle.

## 11. Market restocking

**Status: Connected.** Market UI automation replenishes waystones and optionally tablets. It parses listings, normalizes currencies, filters and sorts offers, groups sellers, verifies purchases, and returns control to the surrounding supply workflow.

This is restocking for the mapper, not a generic trade bot or valuation service. Parsing offers, choosing purchases, and checking the result form a supply workflow around map preparation.

## 12. Campaign runner

**Status: Prototype, blocked at the current entrypoint.** PoE2 campaign components are implemented for acts, zones, quests, town visits, transitions, waypoints, bosses, and rebuilding a leveling setup for endgame. Their existence does not make the current campaign entrypoint usable.

A campaign/passive-plan wiring defect replaces the loaded campaign plan with passive-progression data or no plan before runner initialization. The runner therefore does not receive the campaign structure it requires and fails during initialization, before campaign execution. Dependent gem setup cannot be reached through this entrypoint either. This is a known startup blocker, not merely missing live verification.

Beyond that blocker, quest completion remains partly heuristic; dedicated quest and waypoint readers are missing, and NPC dialogue handling is degraded. The final mapper handoff code only provides a message, not automatic startup of mapping; it is not reached through the blocked entrypoint. No campaign end-to-end proof is established.

## 13. Build import, passive planning, and gems

**Status: Standalone tools, a prototype blocked through the campaign entrypoint, and unfinished UI execution.** Path of Building XML/codec handling produces a BuildSpec, and graph-based passive planning has standalone tests. Atlas passive planning is also a separate tool; these tools are distinct from campaign startup.

Gem-cutter prototype code is implemented, but dependent gem setup cannot be reached through the current campaign entrypoint because the campaign/passive-plan wiring defect blocks runner initialization. It is not a working connected gem-setup workflow through that entrypoint. Selecting passive nodes through the UI is separately unavailable/stubbed. A valid imported build or planned graph therefore must not be presented as a fully applied in-game build.

## 14. Knowledge pipeline

**Status: Standalone tool.** An ETL pipeline transforms Lua/data sources into SQLite. A query API exposes that knowledge for campaign and build plans.

This is data preparation and planning infrastructure, not a live hosted service. Keeping data ingestion, queries, and plan construction distinct makes the domain knowledge reusable without claiming that every plan has an executor.

## 15. PoeFleet lifecycle and jobs

**Status: Connected.** PoeFleet manages slot lifecycles and runner controls through an authenticated API. FIFO jobs have cancellation and terminal states, and RealBackend connects management operations to runtime sessions.

The engineering scope includes coordinating requested work with session lifecycle and reporting how jobs end. Job cancellation and terminal outcomes are explicit parts of that management model.

## 16. Authentication and configuration

**Status: Connected.** Session/token authentication and login throttling accompany configuration version migration, validation, atomic writes, and masking. UI preferences and hot-read mapper settings provide separate paths for presentation choices and changing runtime policy.

These mechanisms cover access, persisted settings, and runtime policy without making the UI preferences and mapper configuration the same concern. The separate guest-transport boundary is discussed in [Current stage](current-stage.md).

## 17. Fleet frontend and desktop shell

**Status: Connected implementation; not rendered for this showcase.** The actual Fleet frontend includes an account wizard, instances and map bots, resources, proxies, mapper/market/Atlas settings, statistics, jobs, and appearance controls, with a Qt desktop shell.

This is an existing interface, not merely an idea for a future synthetic dashboard. Its presence is documented without publishing account/proxy recipes, screenshots, or claims about a fresh UI test.

## 18. Map rendering and event collection

**Status: Connected.** Rendering covers terrain, entities, movement trails, and explored areas. The collector records transitions, deaths, degraded states, and history, with export capabilities in the private implementation.

The collector's `map_complete` event means a return to town, not a proven full clear. MAP-REPORT tracks forced exits, boss status, and unfinished mechanics separately. Historical collector CPU/RAM fields may be absent; Fleet snapshots use separate resource sampling. These distinctions matter when interpreting a timeline or aggregate.

## 19. Resource management and benchmarks

**Status: Standalone tools.** Resource presets support verification and application; a governor manages CPU plans, and A/B benchmark tools compare distributions. Infrastructure tooling supports this operational engineering work without being part of the public package.

Simulation is not measured live throughput. A benchmark `TOTAL` that pools process samples is not a simultaneous total across processes. Neither establishes fleet capacity, resource savings, or production performance without a suitable measurement design.

## 20. Observer telemetry bridge

**Status: Connected, new uncommitted work.** An observer bridge is hooked into the mapper and provides snapshots of player state, entities, path, goal, and behavior. It adds a structured observation boundary for understanding current decisions and movement.

It is not a standalone dashboard bundled with this repository, and no runtime telemetry is published. Its presence in the reviewed local WIP is documented without presenting it as a released interface.

## Compatibility outside this catalog

Follower, Simulacrum, and legacy quest code also exist. Current party and visible-label responses are empty, so that code carries no current compatibility guarantee. Code existence alone is not enough to add another supported workflow.

Read the [architecture flows](architecture.md), [current stage](current-stage.md), and [showcase scope](what-will-be-shown.md). [Back to overview](../README.md).
