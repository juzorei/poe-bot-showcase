# Public-Content Allowlist

## Meaning of this list

This is a **candidate content boundary for future review**, not an authorization to publish. All files remain local under the current authorization.

**The source stays private. Nothing is published by this package.** The word "public" in this filename describes a possible future disclosure review, not the package's current visibility or release status.

The [denylist](PUBLIC_DENYLIST.md) overrides this allowlist. A permitted path never makes prohibited content acceptable. Anything not explicitly listed is excluded by default.

## Exact current file set

Only the following text files belong in this status package:

| Relative path | Permitted purpose |
| --- | --- |
| `README.md` | Coming-later introduction, high-level engineering focus, explicit limitations, and local document links. |
| `docs/current-stage.md` | Experimental status, evidence gaps, blockers, and non-operational review gates. |
| `docs/what-will-be-shown.md` | Proposed synthetic demonstration scope and exclusions, with no implementation or launch procedure. |
| `PUBLIC_ALLOWLIST.md` | Exact content boundary and conditions for a separate disclosure review. |
| `PUBLIC_DENYLIST.md` | Prohibited content categories and default-deny rules. |

No other file, hidden metadata, archive, image, executable, configuration, dependency, or source export is authorized as part of this package.

## Permitted content

- Original English prose describing architectural ideas at a high level: the host/guest boundary, pure parsing, pathfinding, watchdogs, and the PoeFleet control-plane.
- Explicit descriptions of the project as deep, private, experimental, and not a frozen release.
- Clear statements that a current full test pass, CI/coverage, live fleet capacity, map completion, and production readiness are not confirmed here.
- Category-level blockers, without identifiers, values, operational details, or raw supporting artifacts.
- Descriptions of possible future demos using purpose-built synthetic inputs, without implying that those demos already exist.
- Relative links between the five documents listed above.

These permissions apply to prose only. They do not authorize copying private implementation details or adding runnable material.

## Separate review before any future publication

1. Confirm that the candidate contains only the approved file set and no embedded or linked private artifacts.
2. Review every document against the denylist, including examples, identifiers, metadata, and claims.
3. Keep unknown or contradictory evidence explicitly unresolved; do not add unsupported badges or headline metrics.
4. Require new scope approval for any future demo, fixture, screenshot, or source file. This list does not pre-approve those artifacts.
5. Obtain explicit publication authorization for a defined destination and reviewed content. Approval to create local materials is not publication approval.
