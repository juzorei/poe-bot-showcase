# Current stage

[English](current-stage.md) | [Русский](current-stage.ru.md)

Poe Bot has an experimental private implementation, not a frozen release. Only the documentation is public; no runtime or demo has been published.

## What is implemented

The project separates coordination from environment-specific interaction through host/guest components. Parsing is separate from I/O. Pathfinding handles route selection, watchdogs check progress, and PoeFleet provides coordination and status across instance lifecycle states.

The host/guest split is logical separation, not proof of authentication, isolation, or a secure RPC boundary. Separating parsing from I/O does not make the whole runtime hermetic.

## What is not confirmed

There is no current confirmation here of:

- A successful full test-suite run.
- CI status or test coverage.
- Live fleet capacity.
- Map completion or end-to-end success rates.
- Production readiness.

A current test result would need a defined revision, environment, and scope. Partial checks and historical observations cannot stand in for that result. Live capacity and map completion would need their own evaluation; synthetic examples cannot establish either.

## What remains before a public demo

- **Fake mode is not fully hermetic.** It is not a standalone offline demo. A new example would need to work without private configuration, external services, interaction with the game environment, or live state.
- **Guest RPC needs a trust-boundary review.** Authentication, authorization, accepted inputs, and failure behavior need assessment before operational exposure.
- **Metrics are incomplete or contradictory.** Definitions, measurement scope, and data provenance need to be reconciled before using them for performance or reliability claims.
- **Credential and runtime artifacts rule out direct export.** Copying and filtering the private workspace is not an acceptable way to prepare public material. Examples would need newly written code and invented data, not cleaned-up private captures.

The [possible demos](what-will-be-shown.md) would need checks for offline isolation, data provenance, and bounded execution, followed by content review and separate owner approval. Those checks would cover the examples, not certify the bot as a whole.

Publication rules are in the [allowlist](../PUBLIC_ALLOWLIST.md) and [denylist](../PUBLIC_DENYLIST.md).
