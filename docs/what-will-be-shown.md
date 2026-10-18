# Possible demos

[English](what-will-be-shown.md) | [Русский](what-will-be-shown.ru.md)

These are possible standalone examples, not included implementations. There is no release schedule. Each would use newly written code and invented inputs rather than material extracted from the private bot.

## Four ideas

- **Parser:** an invented record format, normalized output, validation errors, and incomplete input. This could show parsing separately from acquisition. No real memory layouts, acquisition code, captured payloads, or imitation of the private runtime schema.
- **Pathfinding:** a small hand-authored grid or graph with obstacles, alternative routes, and an unreachable destination. No real maps, recorded navigation data, live coordinates, game integration, or movement execution.
- **Watchdog:** invented progress events, stalls, timeouts, recovery attempts, and a terminal stop, driven by a virtual clock. This could show state transitions and bounded retries without controlling real processes or remote sessions.
- **PoeFleet-inspired dashboard:** invented instance labels, lifecycle states, alerts, and task outcomes, including incomplete observations. Any controls would affect only the synthetic model. No live connection, real deployment topology, captured screenshots, runtime configuration, or live metrics.

## Before publication

Examples would need to run offline, with no network access or dependency on the private source tree, configuration, or runtime. Inputs should be deterministic, execution bounded, and synthetic data clearly labeled. Checks should state what they cover and what they leave out.

Fixtures must be created from scratch, not made by sanitizing, transforming, or anonymizing private captures. Content and dependencies need review against the [allowlist](../PUBLIC_ALLOWLIST.md) and [denylist](../PUBLIC_DENYLIST.md), plus separate owner approval. These ideas do not add demo files to the current allowlist.

The [current stage](current-stage.md) explains the unresolved runtime questions and why a synthetic demo would not validate the whole bot.
