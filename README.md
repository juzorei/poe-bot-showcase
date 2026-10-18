# Poe Bot

[English](README.md) | [Русский](README.ru.md)

Poe Bot is a private game automation project for Path of Exile 2. It combines host/guest coordination, parsing separated from I/O, pathfinding, progress watchdogs, and PoeFleet for control and status.

The source is private. This repository contains documentation, not a runnable bot or demo.

## Components

- **Host/guest:** separates coordination from interaction with the game environment.
- **Parsing:** interprets acquired data separately from the code that reads it.
- **Pathfinding and watchdogs:** cover route selection, progress checks, and failure handling.
- **PoeFleet:** coordinates instances and shows their lifecycle states.

## Current stage

The implementation is experimental, not a frozen release. Current full-suite results, CI and coverage, live fleet capacity, map completion, and production readiness remain unconfirmed. [Current stage](docs/current-stage.md) covers these gaps, fake-mode isolation, and the guest RPC review still needed.

## Possible demos

Small, separately written examples could show a parser with invented records, pathfinding on a toy grid, a watchdog driven by synthetic events, and a PoeFleet-inspired dashboard. These are possibilities, not included demos or a release schedule. See [demo ideas and boundaries](docs/what-will-be-shown.md).

Publication rules: [allowed materials](PUBLIC_ALLOWLIST.md) · [excluded materials](PUBLIC_DENYLIST.md).
