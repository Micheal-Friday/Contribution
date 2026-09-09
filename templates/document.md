---
type: <strategy | product | architecture | process | index>
status: <draft | accepted | superseded>   # `living` for process and index
updated: <YYYY-MM-DD>
tags: [<searchable-term>, <searchable-term>]
aliases: [<what people actually call this>]
---

<!--
  GENERIC DOCUMENT TEMPLATE — for living documents.
  Full field rules: docs/frontmatter.md

  NOT for these three — they are append-only and have their own templates:
    a choice + alternatives .......... templates/adr.md
    evidence gathered at a date ...... templates/research.md
    a document that leaves the repo .. templates/report.md

  Name the file lowercase kebab-case: what-it-is.md
  Delete every section you do not fill. An empty heading is a promise broken.
-->

# <Title — the subject, not the document type>

<!--
  ONE paragraph. What this document is for and who needs it.
  A reader must be able to stop here and know whether to continue.
-->

## <The substance>

<!--
  Tables over prose wherever the content is comparable.
  State the RULE that generates any list you write — a list without its
  rule cannot be extended correctly by the next person.
-->

## Open questions

<!--
  What is undecided, and what would settle it. Delete if nothing is open.
  A question here is not a decision — if it has options and drivers,
  it belongs in a decision record.
-->

- <the question, and what would answer it>

## References

<!-- Repo-relative links are fine here; this document stays inside the tree. -->

- [<document>](<path>) — <why a reader would follow it>
