# Poe Bot — Showcase Coming Later

**Local status package · Private experimental project · Not a runnable showcase**

Poe Bot is a deep private experimental project. This page describes its architectural strengths, current limitations, and the scope of a possible future synthetic showcase. It is not a frozen release, a deployment guide, or evidence of production readiness.

**The source stays private. Nothing is published by this package.** Creating these local documents does not authorize publication, distribution, or disclosure of the source project. Any future publication requires separate explicit approval and a fresh content review.

## Engineering focus

- **Host/guest boundary:** separation between orchestration and environment-specific interaction is an architectural strength. Separation alone does not establish a secure trust boundary.
- **Pure parsing:** isolating interpretation from acquisition makes parsing logic a useful candidate for deterministic, offline examples with invented inputs.
- **Pathfinding and watchdogs:** navigation logic and progress supervision offer opportunities to explain decisions, failure states, and bounded recovery on synthetic scenarios.
- **PoeFleet control-plane:** a coordination and status layer offers a way to discuss lifecycle management and observability without exposing private runtime operations.

These are architectural focus areas, not claims that the complete system is validated, reliable, or ready for external use.

## Where the project stands

The project remains a deep private experiment, not a frozen release. This package is documentation only: it contains no source export, demo implementation, executable, configuration, runtime data, or installation instructions.

The following are **not confirmed** here:

- A current full test-suite pass.
- CI status or coverage.
- Live fleet capacity.
- Map completion or end-to-end success rates.
- Production readiness.

No bot, server, virtual machine, remote session, network call, or live game is part of this package. No source tests are claimed here. The status statements are intentionally conservative and are not a substitute for a fresh full-system validation.

## Why the showcase is coming later

Credential/runtime artifacts must remain outside any export. Fake mode is not fully hermetic and must not be treated as a safe standalone demo. The guest RPC trust boundary needs further review, and incomplete or contradictory metrics do not support headline performance or reliability claims.

A future showcase would use purpose-built synthetic parser, pathfinding, watchdog, and dashboard examples. None of those demos is included or promised as available today. There is no release date commitment.

## Read next

- [Current stage and unresolved evidence](docs/current-stage.md)
- [What a future showcase would show](docs/what-will-be-shown.md)
- [Candidate public-content allowlist](PUBLIC_ALLOWLIST.md)
- [Public-content denylist](PUBLIC_DENYLIST.md)

The allowlist is a review boundary, not publication permission. The denylist takes precedence wherever there is ambiguity.
