# Current Stage

[English](current-stage.md) | [Русский](current-stage.ru.md)

## Status and scope

Poe Bot is a deep, private experimental project, not a frozen release. Its architectural work is worth explaining, but an externally safe, independently understandable runnable showcase has not yet been prepared.

**The curated documentation has been published publicly with the owner's authorization. The source stays private.** These documents are a status page, not a runnable showcase or a source distribution. No runtime or demo has been published; future additions require separate approval and review.

This status is a conservative editorial snapshot, not a source execution report, security assessment, network validation, or live-system qualification. Architectural strengths must not be read as verified operational outcomes.

## Architectural strengths to explain

| Area | Engineering value | Limit of the claim |
| --- | --- | --- |
| Host/guest boundary | Separates orchestration concerns from environment-specific interaction. | A logical boundary is not proof of authentication, isolation, or safe deployment. |
| Pure parsing | Separates interpretation from acquisition and enables focused reasoning about inputs and outputs. | Suitability for isolated examples does not mean the current runtime is hermetic. |
| Pathfinding and watchdogs | Provides material for discussing route selection, progress checks, and failure handling. | This does not establish live navigation success, map completion, or unattended reliability. |
| PoeFleet control-plane | Provides a coordination and observability perspective across lifecycle states. | This does not establish live fleet capacity or production-grade operation. |

## Evidence not established

| Topic | Current public-facing position | Evidence needed before making a stronger claim |
| --- | --- | --- |
| Current full test pass | Not confirmed; no current full-suite result was obtained for this package. | A reproducible result tied to a defined revision and environment, with scope and exclusions stated. |
| CI and coverage | Not confirmed; no CI or coverage badge is warranted. | Reviewed evidence with a defined measurement scope, provenance, and limitations. |
| Live fleet capacity | Not confirmed; no capacity figure is supplied. | Separately authorized, scoped evaluation. A synthetic dashboard cannot substitute for it. |
| Map completion | Not confirmed; no completion rate or end-to-end success claim is supplied. | A consistent definition of completion and relevant, reproducible evidence. |
| Production readiness | Not established; this package makes no readiness claim. | Broader security, reliability, isolation, and operational evaluation beyond a demo. |

Historical observations, partial checks, and illustrative examples must not be presented as current full-system validation.

## Blockers

1. **Credential and runtime artifacts.** The private workspace must be treated as unsuitable for direct export. No raw repository copy, runtime artifact, or credential-bearing material belongs in the showcase. A future export must be assembled from explicitly reviewed safe material rather than produced by copying and filtering the source tree.
2. **Fake mode is not fully hermetic.** It is not an approved offline demonstration boundary. A safe future demo must be independent of private runtime configuration, external services, environment-specific interaction, and live state. The existing fake mode was not executed or certified here.
3. **Guest RPC trust boundary.** The boundary remains a security review item. Authentication, authorization, accepted inputs, and failure behavior need assessment before any operational exposure. These documents include no connection or deployment details.
4. **Incomplete or contradictory metrics.** Definitions, measurement scope, provenance, and consistency need reconciliation. No uncertain figures are carried into this package, and missing evidence is not treated as success.

## Gate for a future showcase

A future candidate should contain newly authored synthetic examples with no dependency on the private runtime. Its offline behavior, fixture provenance, bounded execution, and content exclusions must be reviewed before any separate publication decision.

Passing checks for a synthetic demo would validate only that demo's stated scope. It would not establish a full source-project test pass, live fleet capacity, map completion, or production readiness.

See [the future showcase scope](what-will-be-shown.md), [allowlist](../PUBLIC_ALLOWLIST.md), and [denylist](../PUBLIC_DENYLIST.md).
