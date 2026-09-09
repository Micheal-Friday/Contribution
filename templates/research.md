---
type: research
status: complete
researched: <YYYY-MM-DD>
tags: [<area>, benchmark]
aliases: [<what this pass is called>]
---

<!--
  RESEARCH PASS TEMPLATE. Full rules: docs/research.md · fields: docs/frontmatter.md

  `researched:` is when the EVIDENCE WAS GATHERED — not today, not the date
  you finished writing. It is the only field telling a reader in 2028 how
  stale this is.

  `status: complete` on issue. There is no draft and no revised state:
  a pass is READ-ONLY once written. A correction is a NEW pass that names
  what it corrects. Typos and broken links may be fixed — presentation is
  not findings.

  One file per pass. Name it for the AREA, not the trigger:
  benchmark-<area>.md
-->

# <Area> — <benchmark | survey>

**Question:** <the one thing this pass set out to establish>
**Prompted by:** <what triggered it — this is the only place the trigger belongs>

## Findings

<!--
  EVERY MATERIAL CLAIM CARRIES A SOURCE URL, in the same row.
  Label vendor-reported figures as vendor-reported — a vendor's own number
  is evidence of what the vendor claims, which is a different fact.
-->

| Finding | Evidence | Source | Confidence |
|---|---|---|---|
| <what was established> | <the figure or quote> | <URL> | high / medium / **unverified** |

**Conflicts** — record them as conflicts. Never average, never silently pick.

| Claim | Figure A + source | Figure B + source |
|---|---|---|
| | | |

## Coverage

<!--
  MANDATORY. A pass that hides its boundary is worse than no pass, because
  conclusions get built on absence: a reader who cannot see the edge of the
  survey assumes there was none.
-->

| | |
|---|---|
| **Surveyed** | <what was actually examined, by name> |
| **Not reachable** | <looked for, could not be obtained — paywalled, undisclosed, no reply> |
| **Out of scope** | <deliberately excluded, and why — different from unreachable> |

**"Unverified" means *could not be confirmed from a primary source*. It does not mean false.** Never promote an unverified claim by retyping it without its qualifier.

## Where the evidence points

<!--
  FINDINGS ONLY. Research does not decide.
  "The evidence points to X" is a finding. "We should therefore do X" is a
  decision made in a document with no mechanism for deciding anything —
  write the decision record instead: templates/adr.md
-->

- <what the evidence supports, and what it does not reach>
