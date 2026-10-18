# Public-Content Denylist

## Default-deny rule

**The curated documentation has been published publicly with the owner's authorization. The source stays private.** The package is documentation only, not a runnable showcase. No runtime or demo has been published; future additions require separate approval and review.

Everything outside the exact file set in the [allowlist](PUBLIC_ALLOWLIST.md) is excluded. The restrictions below also apply inside allowlisted files. If classification is uncertain, omit the material and require separate review rather than assuming it is safe.

## Prohibited content

| Category | Excluded material |
| --- | --- |
| Secrets and credentials | Secret values, passwords, tokens, keys, cookies, session identifiers, connection credentials, or examples copied from credential-bearing artifacts. |
| Private source and internals | Source exports, copied implementation snippets, offsets, signatures, pointer chains, memory layouts, acquisition details, or other reverse-engineering material. |
| Raw memory and session data | Memory dumps, captured payloads, recorded sessions, real maps, live coordinates, runtime state, traces, logs, telemetry exports, or fixtures derived from them. |
| Identifying and operational details | Exact endpoints, ports, process names, infrastructure addresses, deployment identifiers, account identifiers, or private environment paths. |
| Access and operation instructions | RDP, VM, proxy, or account instructions; connection recipes; deployment, launch, remote-control, or live-game operation procedures. |
| Runtime artifacts and dependencies | Runtime configuration, environment files, caches, local databases, persistent profiles, executables, installers, archives, dependency bundles, or repository history and metadata. |
| Captured media | Screenshots, recordings, dashboard exports, or other media captured from private environments or live sessions. |
| Unsupported claims | Claims of a current full test pass, CI/coverage, live fleet capacity, map completion, or production readiness without appropriate evidence. Claims of continuous unattended operation or evasion capabilities are out of scope. |

Category names may be discussed to explain exclusions. Actual sensitive values, actionable details, and representative private samples must not be included, even in redacted examples.

## No indirect disclosure

- Do not link to private artifacts, embed them in documents, or package them as attachments.
- Do not treat renaming, truncation, encoding, redaction, or anonymization as sufficient grounds to export private runtime material.
- Do not substitute real configuration into illustrative examples.
- Do not disguise uncertain or conflicting metrics as benchmarks. Synthetic examples must remain explicitly synthetic.
- Do not imply that a logical host/guest separation establishes a secure guest RPC boundary.
- Do not label the existing fake mode hermetic or safe to distribute without an independent, scoped review.

## Boundaries of this task

Authorization to publish the curated documentation does not authorize modifying the source project, running the bot or servers, starting virtual machines or remote sessions, making network calls other than those needed for the authorized documentation publication, interacting with a live game, or publishing unreviewed additions.

A future synthetic demo is a separate task. Approval of this public documentation package does not relax these restrictions or authorize publication of the original project.
