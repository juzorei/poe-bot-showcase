# Current stage

[English](current-stage.md) | [Русский](current-stage.ru.md)

Poe Bot has a substantial private implementation: a connected mapper, state reader, control layer, combat and supply workflows, plus PoeFleet and planning tools. It is active development, not just a proposal for demos. This documentation reflects source reviewed on **2026-10-18**, including committed code and local uncommitted changes; it does not describe a frozen release.

## Implementation status

The [twenty-group catalog](features.md) gives the detailed scope. Its labels describe implementation and wiring, not live verification.

| Status | Present scope |
| --- | --- |
| Connected | External state reader; host/guest control; navigation and declarative combat; mapper lifecycle and encounter handlers; loot, inventory, and stash; MapPrep; Atlas and market supply paths; Fleet management, configuration, frontend, rendering, and collection |
| Standalone tool | Path of Building import and passive graph planning; Atlas passive planning; knowledge ETL and queries; resource presets, CPU governor, and benchmark/infrastructure tools |
| Prototype — blocked | Campaign components and gem-cutter code exist, but the current campaign entrypoint fails before runner execution; dependent gem setup is unreachable through it |
| Unfinished | Passive-node UI execution; Omen, Well of Souls, and socketing; execution beyond Expedition detection; unproven Legion/Harbinger integration |

Connected work can still be WIP. Position and map-progress watchdogs, the newer Atlas interaction path, and the new mapper-connected observer bridge are current examples. The observer bridge is uncommitted local work, not a released standalone dashboard. The actual Fleet frontend and Qt shell exist; neither was rendered or interactively checked for this rewrite.

## Important functional boundaries

- **Mapping:** preparation, fresh-instance activation, entry, exploration, return, and reset are connected, with old-portal prevention. Fake integration tests exercise coordination, not a full live run. Repeated sweeps, boss tracking, unfinished mechanics, and forced exits remain distinct outcomes.
- **Atlas:** a newer selection/insertion path exists, including inventory-delta verification. Repeating the legacy claim that map-device insertion is simply unsupported would miss that development; the current path is still WIP.
- **Campaign — blocked prototype:** components for acts, zones, quests, town, transitions, waypoints, bosses, and a leveling-to-endgame rebuild are implemented. However, a campaign/passive-plan wiring defect replaces the loaded campaign plan with passive-progression data or no plan. Runner initialization then fails because the required campaign structure is missing, before the campaign runs. This is a known entrypoint blocker, not just an unverified live path. Beyond it, quest completion remains partly heuristic; dedicated quest/waypoint readers are missing, NPC dialogue is degraded, and the final mapper handoff code only provides a message. There is no established campaign end-to-end proof or automatic final handoff.
- **Builds and dependent gems:** importing a build and computing passive plans do not apply passive nodes in-game. That UI action is explicitly unavailable/stubbed. Gem-cutter prototype code exists, but dependent gem setup cannot be reached through the current campaign entrypoint because of the startup blocker. Standalone build/passive planning and Atlas passive planning remain distinct from that blocked execution path.
- **Mechanics and crafting:** the catalog identifies connected encounter handlers. Expedition detection is not execution; Legion/Harbinger classes are not proven wired. Omen, Well of Souls, and socketing are stubs.
- **Older modes:** follower, Simulacrum, and legacy quest code exist, but current party and visible-label responses are empty. There is no current compatibility guarantee for those modes. This limitation does not erase the separate ground-item-label reader used by loot pickup.

Loot pickup relies on the game loot filter for primary item policy. Market automation replenishes waystones and optional tablets; it is not a general trade or valuation product.

## Verification evidence and its limits

No fresh tests were executed for this documentation rewrite. Broad companion suites exist for reader/control, pathing, the map cycle, stash, map preparation, market, builds, authentication, jobs, migration, collection, the governor, and benchmarks. Standalone planning tests and fake integration tests are useful evidence of testable boundaries, not a present full-suite pass.

The local compile/lint/host-unittest gate does not include Fleet pytest. Some tests depend on external fixtures. Neither a partial gate nor historical test counts establish current coverage, CI status, or a successful run of every suite. This showcase makes no fresh pass-count claim, live map or campaign success claim, fleet-capacity claim, profit claim, or production-readiness claim.

## Read telemetry according to its meaning

| Observation | What it does and does not establish |
| --- | --- |
| Collector `map_complete` | Records a return to town, not proven full clearance |
| MAP-REPORT | Tracks forced exits, boss state, and unfinished mechanics separately |
| Historical collector CPU/RAM | May be missing; absence must not be interpreted as zero usage |
| Fleet resource snapshot | Uses separate sampling; it is not automatically the same series as collector history |
| Benchmark `TOTAL` | Pools process samples; it is not a simultaneous sum across processes |
| Simulation | Can exercise a model or comparison, not prove real throughput or supported fleet size |

These distinctions are more useful than combining incompatible numbers into one performance claim. No public runtime captures or exports accompany the descriptions.

## Public boundary and future examples

The source remains private and this repository contains documentation only. Existing fake mode is **not fully hermetic**: real configuration, collector, and engine components are still involved. It is not a safe downloadable offline demo. Fleet authentication also does not certify the separate guest RPC boundary; logical host/guest separation is not a security guarantee.

Future synthetic examples would need newly written code, invented inputs, offline isolation, and a separate content review. They are currently unavailable and have no schedule. They would illustrate engineering concepts, not validate the private bot. See [showcase content](what-will-be-shown.md), the [allowlist](../PUBLIC_ALLOWLIST.md), and the [denylist](../PUBLIC_DENYLIST.md).

[Architecture](architecture.md) · [Overview](../README.md)
