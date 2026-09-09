---
type: report
status: complete
date: <YYYY-MM-DD>
report-id: R<NNN>
audience: [<who this is written for>]
tags: [<area>]
---

<!--
  REPORT TEMPLATE. Full rules: docs/reports.md · fields: docs/frontmatter.md

  A report LEAVES THE REPOSITORY. Its reader has nothing but this file —
  no tree, no clone, maybe no access. Every rule below comes from that.

  NO REPO-RELATIVE LINKS IN THE BODY. Not ../docs/x.md, not anchors.
  Cite as plain text instead:  positioning.md §3   ADR-0010   R003
  External URLs are fine and encouraged — they resolve everywhere.

  File name:  R<NNN>-<subject-slug>-<YYYY-MM-DD>.md
  The date is the date the report DESCRIBES, not when the file was touched.
  R<NNN> is sequential and never reused, including for withdrawn reports.

  Never edited after it is issued. A correction is a new report that names
  what it corrects.
-->

# <Subject> — <what kind of report>

<!--
  HEADER BLOCK — mandatory, and not duplication of the frontmatter above.
  The recipient reads rendered text and may never see the YAML.
  It must identify this document with nothing else present.
-->

| | |
|---|---|
| **Report** | R<NNN> |
| **Date** | <YYYY-MM-DD> |
| **Subject** | <one line> |
| **Scope** | <the branch, pull request, or research pass this covers> |
| **Reading time** | ~<N> minutes |

## Decisions needed

<!--
  ONLY if this report asks something of the reader — then it goes HERE,
  near the top. A decision buried on page nine does not get made.
  Delete this section if the report asks for nothing.
-->

1. <the decision, stated so it can be answered yes or no>

## Summary

<!--
  Three to six sentences. Written so that reading ONLY this is a defensible
  use of the reader's time.
-->

## Findings

<!--
  The substance. Tables over prose.
  Every figure carries its source IN THE SAME SENTENCE — the reader cannot
  follow a link to check it.
  Expand every abbreviation on first use, every time.
-->

## The weakest link

<!--
  MANDATORY. Name the thinnest part of your own argument.
  A report presenting only strengths reads as advocacy and gets discounted
  whole. This is the difference between a report that can be CHECKED and
  one that can only be believed.

  "There are some uncertainties" is not a weakest link. Name a specific
  claim, what would falsify it, and what it costs if it is wrong.
-->

**The claim:** <the specific load-bearing claim>
**Falsified by:** <what evidence would break it>
**Cost if wrong:** <what has to be redone>

## Coverage and confidence

<!--
  Research and benchmark reports only. What was surveyed, what was not
  reachable, how much weight each finding will bear. Delete otherwise.
-->

## Sources

<!--
  Plain text. Document names and sections; external URLs in full.
  Never cite a commit hash from an unmerged branch — cite the pull request.
-->

- <document name> §<N>
- <https://example.com/...>
