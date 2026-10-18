# What a Future Showcase Would Show

**Planned direction only. No runnable demos are included in this package.**

The target is a small set of independently understandable engineering demonstrations, built from invented inputs rather than extracted private runtime material. This is not a promise of availability or a release schedule.

**The source stays private. Nothing is published by this package.** Any future implementation and publication require separate authorization; this document is not permission to export source or operate the private system.

## 1. Synthetic parser demonstration

**Idea:** Interpret a deliberately invented record format and show normalized output, validation failures, and handling of incomplete input.

**What it would illustrate:** The value of pure parsing, explicit contracts, deterministic examples, and separation of interpretation from acquisition.

**Boundary:** No acquisition layer, real memory layout, reverse-engineering details, captured payloads, or samples derived from private dumps. The invented format must not encode the private runtime schema.

## 2. Synthetic pathfinding demonstration

**Idea:** Use a hand-authored toy grid or graph with obstacles, alternative routes, and an unreachable destination.

**What it would illustrate:** Route selection, failure cases, and explainable algorithmic decisions on a small, reproducible problem.

**Boundary:** No real maps, captured navigation data, live coordinates, game integration, or movement execution. A solved toy route is not evidence of map completion in the private project.

## 3. Synthetic watchdog demonstration

**Idea:** Feed an invented event sequence to a small state model, including progress, missing progress, timeout, recovery, and a terminal stop.

**What it would illustrate:** Explicit state transitions, bounded retries, and understandable failure reporting using a virtual clock rather than a live runtime.

**Boundary:** No real process control, remote sessions, runtime control commands, or live supervision. Synthetic outcomes cannot establish operational reliability.

## 4. Synthetic PoeFleet-inspired dashboard demonstration

**Idea:** Present invented worker labels, lifecycle states, alerts, and task outcomes in a self-contained dashboard mockup with clearly marked synthetic data.

**What it would illustrate:** A control-plane perspective on coordination, status visibility, and uncertainty in incomplete observations.

**Boundary:** No operational control connection, real deployment topology, identifying labels, captured screenshots, live metrics, or runtime configuration. Any interactions would affect only the isolated synthetic model. This would not be a live PoeFleet deployment or evidence of fleet capacity.

## Requirements for every future demo

- Create fixtures from scratch; do not sanitize, transform, or anonymize raw private runtime captures into public samples.
- Keep examples independent of the private source tree and runtime configuration.
- Make them genuinely offline and hermetic, with no network access or external runtime integration.
- Use deterministic inputs and bounded execution; label all illustrative data and outcomes as synthetic.
- State exactly what was checked and what remains outside the demonstration's scope.
- Review both content and dependencies against the [allowlist](../PUBLIC_ALLOWLIST.md) and [denylist](../PUBLIC_DENYLIST.md).
- Obtain separate explicit approval before publication. Proposed demo files are not added to the current allowlist by this document.

## What this package does not provide

There is no implementation, installer, dependency bundle, runtime configuration, startup procedure, access instruction, or connection recipe. It contains no source-project certification, operational capacity claim, completion benchmark, or production-readiness claim.

For current blockers and evidence limitations, see [Current Stage](current-stage.md).
