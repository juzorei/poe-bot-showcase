# Poe Bot

[English](README.md) | [Русский](README.ru.md)

Poe Bot is a Path of Exile 2 automation project that combines game-state observation, navigation, combat, map preparation, inventory management, and multi-instance control. Its central workflow is a mapper: prepare a map, activate a fresh instance, enter, explore and handle encounters, then return and prepare for the next cycle. Around that workflow are a campaign prototype, build-planning tools, market restocking, and PoeFleet, an application for managing runners and observing their work.

The interesting engineering problem is not simply choosing the next action. It is keeping perception, decisions, input, recovery, and operator controls consistent when observations are incomplete, movement stalls, an inventory fills up, or a session changes state.

## Inside the product

**Observation and control.** An external reader supplies player, entity, terrain, skill, inventory, stash, ground-label, UI-text, and Atlas state through a compatible state payload with partial-error reporting. Host/guest transport carries input and screen interactions, with reconnect handling, held-input state, and foreground/background adapters. Parsing and acquisition are separate concerns.

**Navigation and combat.** A* routing is combined with line-of-sight checks, clearance, smoothing, discovery routes, doors, and transitions. Mouse and WASD movement share progress supervision. Declarative combat priorities cover skills, flasks, auras, buffs, distance gates, and sticky targets, with leveling and endgame rotations coordinated with movement. Position and map-progress watchdogs remain active development areas.

**The map loop.** The mapper connects preparation, fresh-instance activation, entry, exploration, and return/reset, including protection against reusing old portals. Encounter handling includes Essence, Breach, Ritual, Delirium, strongboxes, shrines, and boss hunting, with repeated sweeps and unfinished-mechanic tracking. Loot pickup follows labels and restrictions; the game loot filter remains the primary item policy, not a market-valuation engine. Inventory handling preserves consumables, verifies stash transfers, and supports a mid-map dump and return, including lost-portal handling.

**Preparation and supply.** Map preparation includes identification, currency use, budgeted waystone rolling, and tablets. Atlas selection combines ranking, filters, mechanics preferences, frontier discovery, manual targeting, and UI fallbacks. Market UI automation restocks waystones and optional tablets, normalizes listing currencies, groups sellers, and verifies purchases. It is a supply workflow for mapping, not a general trading bot.

**Progression and planning.** Campaign prototype components cover acts, zones, town visits, transitions, waypoints, bosses, and a leveling-to-endgame build rebuild, but a campaign/passive-plan wiring defect blocks the current entrypoint before runner execution, also making dependent gem setup unreachable. Quest interpretation is partly heuristic, and the final mapper handoff code only provides a message, not an automatic transition. Separate tools parse Path of Building data, plan passive graphs, and turn knowledge data into campaign and build plans. Gem-cutting code exists as a prototype; passive-node UI execution is unavailable.

**PoeFleet and observability.** Fleet combines slot lifecycles, runner controls, authenticated APIs, FIFO jobs, cancellation, configuration migration, validation, and masked settings. Its existing frontend includes an account wizard, instance and map-bot views, resources, proxies, mapper/market/Atlas settings, statistics, jobs, appearance controls, and a Qt shell. Rendering, event collection, resource presets, CPU governance, and A/B benchmark tooling support investigation. A new mapper-connected observer bridge adds player, entity, route, goal, and behavior snapshots; it is not a bundled standalone dashboard.

## What this showcase represents

The source is private; this repository publishes its product and engineering documentation, not a runtime, screenshots, or a downloadable demo. The descriptions reflect source reviewed on **2026-10-18**, including committed and uncommitted local work, rather than a frozen release. Connected implementation is not the same as live verification. No fresh tests were executed for this rewrite, and no capacity, profit, or end-to-end success claims are made.

Poe Bot is based on upstream **tachikoma-av/poe_bot**. This project's development extends that foundation with an external reader and declarative build engine, a PoE2 campaign runner, PoeFleet, and market UI automation. It does not claim that all inherited movement or combat work was written from scratch.

## Read further

- [Feature catalog](docs/features.md): twenty areas and their implementation status.
- [Architecture](docs/architecture.md): observation, execution, recovery, and management flows.
- [Current stage](docs/current-stage.md): connected work, prototypes, gaps, and verification limits.
- [Showcase content](docs/what-will-be-shown.md): what is documented now and possible future synthetic examples, currently unavailable and without a schedule.
- [Publication allowlist](PUBLIC_ALLOWLIST.md) and [private-material boundaries](PUBLIC_DENYLIST.md).
