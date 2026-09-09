---
type: process
status: living
updated: 2026-09-09
tags: [contribution, docs, frontmatter, metadata, process]
aliases: [frontmatter reference, document metadata, what frontmatter do i use]
---

# Frontmatter

> **At a glance**
> **Every document** carries `type`, `status`, and **one date field**. Everything else is per-type or optional.
> **The date field is named for what it means** — `updated:` living · `date:` decided or described · `researched:` evidence gathered.
> **Fastest path** copy the [template](../templates/) for your type; the block is already in it.
> **Rule** **No document carries `version:`.** Only shipped artifacts get SemVer.

---

The lookup that answers *what goes at the top of this file?* The reasoning behind these fields is in [The document lifecycle](document-lifecycle.md) §2; this is the reference you keep open while writing.

---

## 1. Which type am I writing?

| Writing… | `type` | Template | Guide |
|---|---|---|---|
| what the project is trying to be, and why | `strategy` | [document](../templates/document.md) | — |
| what the product does, for whom, in what order | `product` | [document](../templates/document.md) | — |
| how it is built, and how the pieces fit | `architecture` | [document](../templates/document.md) | — |
| how work is done here | `process` | [document](../templates/document.md) | — |
| **one choice, its alternatives, its consequences** | `decision` | [adr](../templates/adr.md) | [decisions](decisions.md) |
| **evidence gathered at a point in time** | `research` | [research](../templates/research.md) | [research](research.md) |
| **a document that leaves the repository** | `report` | [report](../templates/report.md) | [reports](reports.md) |
| a registry of other documents | `index` | [index](../templates/index.md) | [reports §5](reports.md) |

**Nothing fits?** Use the closest type and add a `tag`. A new type is earned by [three tests](document-lifecycle.md), the first being that it needs a **different status ladder** — if the lifecycle is identical, what you have is a topic, and topics are what `tags` are for.

---

## 2. The complete block, by type

Copy one. Every field shown is either required, or commented out and optional.

### Living document — `strategy` · `product` · `architecture`

```yaml
---
type: strategy          # or product, architecture
status: draft           # draft | accepted | superseded
updated: 2026-09-09     # last meaningful revision
tags: [sourcing, positioning]
aliases: [what people actually call this]
# supersedes: positioning-v1.md
# superseded-by: positioning-v3.md
---
```

### `process`

```yaml
---
type: process
status: living          # the only value
updated: 2026-09-09
tags: [contribution, git]
aliases: [commit conventions]
---
```

### `index`

```yaml
---
type: index
status: living          # the only value
updated: 2026-09-09
tags: [index]
aliases: [reports registry]
---
```

### `decision`

```yaml
---
type: decision
status: proposed        # proposed | accepted | rejected | deprecated |
                        # superseded by ADR-NNNN
date: 2026-09-09        # WHEN THE DECISION WAS MADE, not when the file was written
decision-makers: [role or name]
consulted: []           # asked before — delete the key rather than faking one
informed: []            # told after
tags: [storage]
# supersedes: ADR-0009  # on a record that REPLACES an earlier one
---
```

**A superseded decision carries its pointer in `status`, not in a `superseded-by:` field** — see §4.

### `research`

```yaml
---
type: research
status: complete        # the only value — no draft, no revised
researched: 2026-09-09  # WHEN THE EVIDENCE WAS GATHERED, not today
tags: [benchmark, sourcing]
aliases: [vendor benchmark]
# supersedes: benchmark-sourcing-2026-03.md
---
```

### `report`

```yaml
---
type: report
status: complete        # the only value — a draft report has not been sent
date: 2026-09-09        # THE DATE THE REPORT DESCRIBES
report-id: R003
audience: [management, external reviewer]
tags: [benchmark]
# supersedes: R001
---
```

---

## 3. Every field, every type

**●** required · **○** optional · **—** never

| Field | strategy | product | architecture | process | index | decision | research | report |
|---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| `type` | ● | ● | ● | ● | ● | ● | ● | ● |
| `status` | ● | ● | ● | ● | ● | ● | ● | ● |
| `updated` | ● | ● | ● | ● | ● | — | — | — |
| `date` | — | — | — | — | — | ● | — | ● |
| `researched` | — | — | — | — | — | — | ● | — |
| `tags` | ○ | ○ | ○ | ○ | ○ | ○ | ○ | ○ |
| `aliases` | ○ | ○ | ○ | ○ | ○ | ○ | ○ | ○ |
| `supersedes` | ○ | ○ | ○ | — | — | ○ | ○ | ○ |
| `superseded-by` | ○ | ○ | ○ | — | — | **—** | ○ | ○ |
| `decision-makers` | — | — | — | — | — | ● | — | — |
| `consulted` | — | — | — | — | — | ○ | — | — |
| `informed` | — | — | — | — | — | ○ | — | — |
| `audience` | — | — | — | — | — | — | — | ● |
| `report-id` | — | — | — | — | — | — | — | ● |
| **`version`** | — | — | — | — | — | — | — | — |

**Four rows worth reading twice.**

- **`updated` is — on the append-only three.** `decision`, `research` and `report` are frozen at merge. A field promising *last updated* on a document that is never updated invites exactly the edit the rules forbid.
- **`version` is — everywhere.** Only shipped artifacts get SemVer; documents get status and supersession.
- **`process` and `index` cannot be superseded**, because neither ladder has a `superseded` state. They are living documents, edited until deleted.
- **`superseded-by` is — on `decision`**, because a decision's status already names its replacement. **The pointer lives in exactly one place per type**, and which place depends on whether that type's ladder has a state that can carry it — see §4.

---

## 4. Status — the full ladder per type

Never invent a status value. The vocabulary is fixed by type, because **the end state is most of what `type` communicates**.

| `type` | Ladder | Ends by |
|---|---|---|
| `strategy` `product` `architecture` | `draft` → `accepted` → `superseded` | being superseded |
| `process` `index` | `living` | never — edited until deleted |
| `decision` | `proposed` → `accepted` \| `rejected` → `deprecated` \| `superseded by ADR-NNNN` | being superseded; never edited, never deleted |
| `research` `report` | `complete` | never — append-only. A correction is a new document |

| Value | Means | What may be built on it |
|---|---|---|
| `draft` | being written, not agreed | Nothing |
| `proposed` | written and argued, **not decided** | **Nothing.** Work that assumes it is speculative work |
| `accepted` | decided. Binding on later work | Everything. This is the constraint others live inside |
| `rejected` | considered and declined. **The record stays, permanently** | Nothing — but the next person to propose it gets the reasons for free |
| `deprecated` | no longer applies, and nothing replaced it | Nothing |
| `superseded` | replaced. On a **decision** the value carries the pointer itself — `superseded by ADR-NNNN`. On a living document it is bare, and `superseded-by:` carries the pointer | Follow the pointer |
| `living` | current by definition; the git log is its history | Everything |
| `complete` | issued. Describes a state at a date | It is evidence, not a commitment |

> **`proposed` is not a soft `accepted`.** The moment it starts meaning *probably yes*, the folder stops being a record of decisions and becomes a folder of drafts. See [decisions §4](decisions.md).

### Where the supersession pointer lives

**One place per type — whichever the type's ladder can carry.** Writing it twice means two fields that can disagree, and nothing checks that they agree.

| Type | The old document points forward via | Because |
|---|---|---|
| `decision` | its **`status`** — `superseded by ADR-NNNN` | the ladder's terminal state names the replacement, so a field would only repeat it |
| `strategy` `product` `architecture` | **`superseded-by:`** | the status is a bare `superseded` with nowhere to put a name |
| `research` `report` | **`superseded-by:`** | the ladder stops at `complete` and has no superseded state at all |
| `process` `index` | — | living documents; they are edited until deleted, never superseded |

**The reverse link is always `supersedes:` on the new document**, whatever the type. So both directions traverse in every case, with the pointer written once in each.

---

## 5. The date field is named for what the date means

**This is the rule that removes the guesswork.** One field name was answering three different questions, so the names now differ.

| Field | Answers | On | Set it to |
|---|---|---|---|
| `updated:` | *how stale is this?* | living types | the last **meaningful** revision — not a typo fix |
| `date:` | *when was this true?* | `decision` | the day the decision was **made**, even if written up later |
| `date:` | *when was this true?* | `report` | the date the report **describes**, not when the file was touched |
| `researched:` | *how stale is the evidence?* | `research` | the day the **evidence was gathered** |

**ISO-8601 always — `2026-09-09`.** It is unambiguous in every locale; `09/09/26` is not. **Resolve relative dates before writing them down** — "last Tuesday" is unresolvable the moment the reader is not you, and "recently" was already false when it was committed.

---

## 6. Field reference

| Field | Format | Rule |
|---|---|---|
| `type` | one bare word from §1 | Fixed vocabulary. It sets the status ladder and the date field, so it is the field everything else follows from |
| `status` | one value from §4 | Never invented, never blended. It is the reader's signal for how much weight to put on the document |
| `updated` | `YYYY-MM-DD` | The last *meaningful* revision. Bumping it for a typo is noise; leaving it stale after a rewrite is a lie |
| `date` | `YYYY-MM-DD` | See §5. Not the file's modified time, and not today by default |
| `researched` | `YYYY-MM-DD` | The only field telling a reader in 2028 how stale the findings are |
| `tags` | list, lowercase kebab | Terms a searcher would type. **A tag used once is noise** — if it will not reach a second document, it is a sentence in the body instead |
| `aliases` | list, plain words | Other names the document is **actually called**, for search and wiki-links. Not invented synonyms: if nobody says it out loud, it is not an alias |
| `supersedes` | ID or file name | Set on the **new** document. Names what it replaces |
| `superseded-by` | ID or file name | Set on the **old** one, **only where its status cannot carry the pointer** — so never on a `decision`. On `research` and `report` it is the whole link, and **the only field ever edited on an append-only document** |
| `decision-makers` | list of roles or names | Who actually decided. A record with none was not a decision, it was a suggestion |
| `consulted` | list | Asked **before**. An empty list is honest — delete the key rather than listing someone who was not asked |
| `informed` | list | Told **after** |
| `audience` | list | Who the report is written for. Drives how much gets expanded, since the reader is outside the repository |
| `report-id` | `R<NNN>` | Three digits, zero-padded, sequential, **never reused** — including for withdrawn reports |

### Fields that do not exist here

| Not this | Use instead |
|---|---|
| `version:` | Nothing, on a document. The git tag versions the set; SemVer belongs to the shipped artifact |
| `author:` | `git log`, which cannot drift. Use `decision-makers:` where *who decided* is the point |
| `created:` | Nothing. The first commit is the creation date, and no reader has needed it |
| `last-modified:` | `updated:`, set deliberately. An auto-stamped field bumps on whitespace and stops meaning anything |
| `title:` | The H1. Two titles disagree eventually, and then neither is trusted |

---

## 7. Before you commit

- [ ] `type` is from the fixed list, and it is the type whose **status ladder** actually fits.
- [ ] `status` is a value that ladder allows.
- [ ] The date field is the **right one for the type**, and holds the date it claims — not today by default.
- [ ] No `updated:` on a `decision`, `research` or `report`.
- [ ] No `version:` anywhere.
- [ ] Every `tag` will reach at least one other document.
- [ ] Every `alias` is a name somebody actually says.
- [ ] The record number or `report-id:` is **the next one**, and no earlier one was reused.
- [ ] Superseding? The new document has `supersedes:`, and the old one points forward **once** — in its `status` if it is a `decision`, in `superseded-by:` otherwise. Both directions, or the link is broken. Never both on the same document.
- [ ] Report? It also needs a **header block in the body** ([reports §3](reports.md)) — the file leaves the repository, and its reader may never see this YAML.

---

## References

- [The document lifecycle](document-lifecycle.md) — naming, the type table, the versioning boundary, supersession
- [Architecture decisions](decisions.md) — the status ladder these fields serve, and the numbering rule
- [Research](research.md) — `researched:`, and why a pass is read-only once written
- [Writing reports](reports.md) — `audience:`, `report-id:`, and the header block frontmatter does not replace
- [Templates](../templates/) — every block in §2, ready to copy
