# Contributing

This repository holds the shared conventions, and **follows them**. A conventions repository whose own log breaks its rules is hard to argue with anyone about.

Read the guides for the rules — start at [`README.md`](README.md). This file records only what is specific to **this** repository.

**Pinned to:** n/a — this *is* the source. Adopting projects pin to a tag.

---

## This project's values

### Commit scopes

A scope names the smallest part that ships, is reviewed, and is retired as one unit. Here that is a **directory**, not an individual guide: the guides cross-reference heavily, and a change to one is routinely reviewed alongside its neighbour — which fails the "reviewable on its own" test at file granularity.

| Family | Values |
|---|---|
| A guide directory | `git`, `github`, `docs` |
| The adoption surface | `templates` |

Omit the scope when a change spans the repository — a rule change that touches a guide, a template and the index has no honest narrower scope.

### Commit types in use

| Type | Means here |
|---|---|
| `docs` | the normal case. These documents *are* the artifact, so writing and editing them is `docs:` |
| `fix` | a rule that was **wrong**, not merely improvable — a correction someone following the old text would have got bitten by |
| `chore` | deletions, moves, index sweeps |

`feat` is deliberately unused. A new guide is still a document, and calling it `feat:` would imply a version bump that nothing here consumes.

### Branch types in use

`docs/` · `fix/` · `chore/`, plus `adr/<NNNN>` now that a record series exists. **No `adr/` branch has carried a record yet** — ADR-0001 landed on a `fix/` branch alongside the corrections it settles, because the point of that branch was the corrections. A branch implementing one record on its own takes the `adr/` form.

### Labels

**None in use.** GitHub's defaults are present and unpruned; they will be curated the first time the issue list is long enough that filtering it is a real task. Adding a label before anyone needs to filter is how a taxonomy fills with values nobody applies.

### Where work is recorded

| Question it answers | Where |
|---|---|
| who is doing what, and when is it finished | GitHub issues |
| what was decided, and what it cost | [`docs/decisions/`](docs/decisions/), indexed in its own `README.md`. Opened 2026-09-09 with ADR-0001 — the first convention change that had alternatives worth recording |
| what we want, and in what order | nowhere. There is no backlog; the issue list is short enough to be one |

---

## This project's exceptions

**None.**

There was one, and it is recorded here rather than deleted because a reader who saw the old frontmatter needs to know it went deliberately.

The guides each carried a `version:`, which [document-lifecycle](docs/document-lifecycle.md) says documents should not — justified on the grounds that they are consumed by other repositories, which makes them closer to a shipped artifact than to an internal document.

It was retired in `docs: refs #1 version the set, not the files`. Nine files carried a version, four saying `1.0` and five saying `2.0`; nothing consumed either. **A tag names a commit, so one version covers the whole set** — which is what an adopting project pins to anyway.

---

## What this project cannot honestly enforce

| Convention | Reality here |
|---|---|
| **Author ≠ reviewer** | Aspirational at one maintainer. The substitute is a self-review pass plus a cooling-off period, and the change request says which it got |
| **Hold cross-cutting changes three business days** | Same. It applies once there is a second reviewer; until then it is a cooling-off convention, not a gate |
| **"Yes, if" review norm** | Adoptable now — it is a way of writing feedback, not a headcount requirement |

**Revisit this table whenever the team size changes.** Each row is a rule waiting for a precondition, not a rule that was rejected.

---

## Prior art that is not the model

Conventions here start on **2026-07-29**; this repository's first commit is **2026-08-11**. So unusually, every commit here was written under the conventions — which is not the same as complying with them. **Four subjects exceed the 72-character limit** in [commit messages](git/commit-messages.md) §4. That is recorded rather than quietly fixed, because the history is not being rewritten and a false compliance claim in this section would be worse than the defect it hides.

Most projects adopting these will have far more prior art that does not comply, which is why the stub has this section.

The guides' worked examples come from the project these were extracted from, and its history predates the rules. Where an example is held up as *bad*, that is why.

---

## Changing a rule

1. **A rule change is a change to every project that follows it.** Say in the change request which projects it affects and whether any need to pin before it lands.
2. **Never edit a rule silently.** If the old text was wrong, `fix:` it and say what someone following it would have got wrong — that sentence is the whole value of the commit.
3. **Values do not belong here.** If a change adds a specific scope, label or path, it belongs in a project's own `CONTRIBUTING.md`. The test: could this sentence be false in another project? Then it is a value, not a rule.
4. **Keep the examples real.** Placeholders make a document portable and useless. An example drawn from a real history, labelled as such, is evidence the rule survived contact with something.
