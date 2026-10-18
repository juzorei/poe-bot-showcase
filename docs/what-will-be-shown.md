# What this showcase presents

[English](what-will-be-shown.md) | [Русский](what-will-be-shown.ru.md)

This repository explains an existing private Path of Exile 2 automation project. Its present deliverable is bilingual product and engineering documentation, not a collection of hypothetical implementations. The source-based account reflects the **2026-10-18** review, including uncommitted local work, with implementation status kept separate from live verification.

## Available now: the product story

- **[Overview](../README.md):** what Poe Bot does, how mapping, supply, progression, and Fleet fit together, and what this project's development adds to upstream tachikoma-av/poe_bot.
- **[Feature catalog](features.md):** twenty groups covering observation and control, navigation and combat, map lifecycle and encounters, loot and stash, preparation and Atlas, market restocking, campaign and builds, knowledge tooling, Fleet, configuration, frontend, rendering, resource analysis, and the observer bridge.
- **[Architecture](architecture.md):** flows from state to action, through a map cycle and mid-map unloading, from knowledge to plans, from Fleet jobs to sessions, and from execution to observations. It marks the campaign/passive-plan wiring defect that blocks runner initialization and makes dependent gem setup unreachable through the current entrypoint, alongside the missing automatic campaign handoff and unavailable passive-node UI.
- **[Current stage](current-stage.md):** connected implementation, standalone tools, prototypes, unfinished parts, compatibility limits, test scope, and the meaning of telemetry.

The actual Fleet frontend, Qt shell, map renderer, and new observer bridge belong to the private implementation described here. They are not public downloads, screenshots, or a ready-made dashboard demo. No images, runtime, raw records, or operating instructions are included.

## Engineering themes the documents make visible

The state reader illustrates acquisition separated from interpretation and explicit partial failures. Navigation and combat illustrate feedback-driven execution and declarative policy. Mapping and stash trips illustrate lifecycle boundaries, interruptions, and recovery. Fleet illustrates job cancellation, session coordination, and configuration evolution. Planning tools illustrate why computing a plan and executing it are different capabilities. Telemetry illustrates why a return-to-town event or pooled sample cannot stand in for a full-clear or capacity metric.

These are descriptions of implemented work and its limits. They do not require exporting private code or promising measured game outcomes.

## Possible later synthetic examples — unavailable

No standalone synthetic demos are currently available, and there is no release schedule. If separately developed, examples could include:

| Example | Engineering question | Invented input only |
| --- | --- | --- |
| Parser | How are valid fields and partial errors represented separately? | A newly designed record format, not the private runtime schema |
| Routing and watchdog | How does a system distinguish an unreachable target, a stall, and a bounded recovery? | Hand-authored toy grids and virtual-clock events |
| Lifecycle and job queue | How do preparation, interruption, cancellation, and terminal states differ? | Fictional map-cycle and job events |
| Fleet-inspired view | How can an interface show lifecycle state and incomplete observations without overstating success? | Fictional instances and resource samples; controls affect only the model |
| Planning | How can a graph plan be inspected without pretending an executor exists? | A small invented graph with no game integration |

These would be newly written educational examples, not extracted or anonymized parts of the bot. Existing fake mode is not fully hermetic and is not a safe shortcut to a downloadable demo. Any example would need offline isolation, deterministic invented inputs, bounded execution, content review, and separate owner approval. It would demonstrate its own model, not verify the private runtime.

## Publication scope

Only the fourteen Markdown files in the [allowlist](../PUBLIC_ALLOWLIST.md) are included. The [denylist](../PUBLIC_DENYLIST.md) excludes secrets, private source, raw runtime data, and operational steps. Future demo ideas do not authorize additional files or publication of private artifacts.
