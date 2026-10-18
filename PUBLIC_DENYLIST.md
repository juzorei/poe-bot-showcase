# What stays private

[English](PUBLIC_DENYLIST.md) | [Русский](PUBLIC_DENYLIST.ru.md)

These boundaries override the [allowlist](PUBLIC_ALLOWLIST.md), including inside its fourteen approved documents. The public product story may explain capabilities and conceptual flows, not disclose the material below.

## Excluded material

- **Secrets and identity:** passwords, tokens, keys, cookies, credentials, session or account details, infrastructure addresses, and private URLs.
- **Private source and acquisition internals:** source exports, implementation snippets, offsets, signatures, pointer chains, memory layouts, acquisition recipes, private file/line references, local paths, commit hashes, and private history.
- **Raw runtime data:** captures, memory dumps, actual state payloads, maps, coordinates, logs, traces, telemetry, session records, database exports, and fixtures derived from them.
- **Operational steps:** account, proxy, VM, RDP, connection, deployment, launch, remote-control, or live-game procedures; real endpoints and configuration values.
- **Runtime and media:** executables, installers, archives, dependency bundles, configurations, profiles, caches, screenshots, recordings, and dashboard exports.
- **Unsupported claims:** fresh test passes, coverage or CI status, full-clear or campaign success, capacity, profit, resource savings, continuous unattended operation, evasion, or production readiness without appropriate evidence. Historical counts and simulations are not substitutes.

Do not embed, attach, or link private artifacts. Redaction, renaming, transformation, or anonymization does not make raw private material publishable. Possible synthetic examples must use new code and invented data, not cleaned-up captures.

## Keep distinctions intact

Connected code is not live verification; a plan is not its executor; return to town is not proven clearance. Fleet authentication does not certify guest transport. Pooled process samples are not concurrent totals, and fake mode is not a hermetic distributable demo. The [current-stage page](docs/current-stage.md) explains these limits.

Only the [listed documents](PUBLIC_ALLOWLIST.md) are in scope. No bot, server, VM, remote session, or network operation is authorized by documentation approval. New material needs separate review and owner approval.
