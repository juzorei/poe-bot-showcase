# What stays private

[English](PUBLIC_DENYLIST.md) | [Русский](PUBLIC_DENYLIST.ru.md)

This list overrides the [allowlist](PUBLIC_ALLOWLIST.md). Its restrictions apply inside approved files too. Everything outside the allowlist is excluded by default; if a material's status is unclear, leave it out until separately reviewed.

## Do not publish

- **Secrets:** passwords, tokens, keys, cookies, session identifiers, connection credentials, or examples copied from material containing them.
- **Private source and internals:** source exports, implementation snippets, offsets, signatures, pointer chains, memory layouts, acquisition details, or other reverse-engineering material.
- **Runtime data:** memory dumps, captured payloads, recorded sessions, real maps, live coordinates, runtime state, traces, logs, telemetry, or fixtures derived from them.
- **Operational details:** endpoints, ports, process names, infrastructure addresses, deployment or account identifiers, and private environment paths.
- **Access and operation instructions:** RDP, VM, proxy, or account setup; connection, deployment, launch, remote-control, or live-game procedures.
- **Runtime files and repository history:** configuration, environment files, caches, databases, persistent profiles, executables, installers, archives, dependency bundles, history, and metadata from the private repository.
- **Captured media:** screenshots, recordings, dashboard exports, or other media from private environments or live sessions.
- **Unsupported claims:** unverified test, CI, coverage, fleet-capacity, map-completion, or production-readiness claims. Claims of continuous unattended operation or evasion capabilities are also out of scope.

Category names can explain these exclusions. Actual values, actionable details, and representative private samples cannot be included, even with parts redacted.

## No indirect export

Do not embed, attach, or link to private artifacts. Renaming, truncating, encoding, redacting, sanitizing, or anonymizing raw runtime material does not make it publishable. Do not insert real configuration into an illustrative example; create synthetic data from scratch and label it as such.

Do not present conflicting metrics as benchmarks, logical host/guest separation as a security guarantee, or existing fake mode as hermetic or safe to distribute. See [Current stage](docs/current-stage.md).

## Approval is limited to the documents

Documentation approval does not permit changing or disclosing private source, running bots or servers, starting VMs or remote sessions, making operational network calls, or interacting with the live game. Future additions require content review and separate owner approval; a proposed synthetic demo is not an exception.
