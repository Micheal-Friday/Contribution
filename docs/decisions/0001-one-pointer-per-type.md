---
type: decision
status: accepted
date: 2026-09-09
decision-makers: [maintainer]
tags: [frontmatter, supersession]
---

# 0001 — Put the supersession pointer in one place per type

## Context and Problem Statement

`v1.1.0` added [`docs/frontmatter.md`](../frontmatter.md) to give one answer per field, and it gave a superseded decision's status as the bare value `superseded` — while [`decisions.md`](../decisions.md) §4 and §5 and [`document-lifecycle.md`](../document-lifecycle.md) §2 and §4 all give it as `superseded by ADR-NNNN`. The file added to remove contradictions shipped one.

Underneath the contradiction is a design question that had never been decided: **a superseded record carries the pointer twice**, once inside the status value and again in the `superseded-by:` field. One of the two is redundant, and choosing which to drop is not free — three projects pin to `v1.0.0` and have been reading the guides' form since it was published.

Recorded here because the choice constrains every future record, and because it was taken in a comment thread on [issue #4](https://github.com/Micheal-Friday/Contribution/issues/4), which §1 of the decision guide names as a mistake: a thread is not durable, not linkable from the docs tree, and not indexed.

## Decision Drivers

- **A status value is read by humans and is the primary signal of a record's weight** — `decisions.md` §4. Changing its vocabulary is not the same class of change as adding or removing an inert field.
- **Three projects consume these guides and cannot be consulted before a change lands.** Two of them keep decision records; one keeps nine — issue #1 closing comment.
- **`MAJOR` means following the old text now produces something wrong** — the versioning table in the index. A status vocabulary change makes every superseded record in a consuming project non-conforming, which is a consumer obligation rather than a suggestion.
- **One fact in one field is the machine-readable form.** A pointer embedded in a status string cannot be parsed without knowing the convention.

## Considered Options

1. **Collapse to one field everywhere** — a bare `superseded` status on every type, with `superseded-by:` carrying the pointer alone.
2. **Carry it in both places** — the status names the replacement and `superseded-by:` repeats it.
3. **One place per type** — the pointer lives wherever that type's ladder can carry it: in the `status` for a decision, in `superseded-by:` for every type whose terminal state cannot name a record.
4. **Document both forms** and let each project choose.

## Decision Outcome

**Chosen: option 3.** A decision's ladder already ends in a state that names its replacement — `superseded by ADR-NNNN` — so a `superseded-by:` field on the same record only repeats it. A strategy document ends at a bare `superseded`, and a research pass or report has no superseded state at all, so for those the field is the only place the pointer can go. The rule is therefore one sentence rather than a list: **the pointer lives wherever the type's ladder can carry it, and never in two places at once.**

**Option 1 is the most uniform and the most machine-readable, and was rejected on cost, not on merit.** It changes the status vocabulary three projects have read since `v1.0.0` was published on 2026-08-15 — a MAJOR bump, and an edit to every superseded record they hold.

**Option 2 is what the guides and the reference between them implied, and it is what produced the contradiction**: two statements of one fact, each claiming to be the only part that ever changes. Option 4 was rejected outright — a convention that permits two forms has not decided anything.

### Consequences

- **Good.** No consumer has to do anything. `v1.1.1` shipped as a patch, and every `v1.0.0` link still resolves.
- **Good.** Two guides become true as written rather than contradicting each other. `decisions.md` §5 — *"the status line is the only part of an accepted record that ever changes"* — and the reference's *"the only field ever edited on an append-only document"* now describe different types instead of both claiming the same ground.
- **Good.** Nothing is written twice, so nothing can drift out of agreement with itself.
- **Bad.** The mechanism differs by type, so it must be looked up rather than known. That is what the table in the reference §4 is for.
- **Bad.** A decision's `status` is still not machine-readable — the successor has to be parsed out of the string.
- **Neutral.** `supersedes:` on the new document is unchanged and type-independent, so reverse traversal never varies.

## More Information

**What would show this was wrong:** anyone having to look up which mechanism applies before they can supersede a document. This rule trades uniformity for non-duplication — if the lookup turns out to cost more than the duplication did, the trade was wrong.

**What would trigger a revisit**, as a named condition rather than "if things change": the first time tooling is written that reads `status` programmatically, or the next `MAJOR` bump for an unrelated reason — whichever comes first. A `MAJOR` already being spent is the moment this costs nothing to fix.

- The status **form** — `superseded by ADR-NNNN` rather than a bare `superseded` — was delivered by `fix(docs): refs #4 align the reference with the guides on a superseded status`, released in [`v1.1.1`](https://github.com/Micheal-Friday/Contribution/releases/tag/v1.1.1). The one-place-per-type rule this record settles came after it and is not yet released.
- The alternatives were argued on [issue #4](https://github.com/Micheal-Friday/Contribution/issues/4); this record supersedes that thread as the citable home.
