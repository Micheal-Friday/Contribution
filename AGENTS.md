# Contribution — orientation

Ten guides and eight templates: how work enters a repository. **The rules live here; each project keeps its own values in a `CONTRIBUTING.md` that links here.**

**This is the only copy.** [`CLAUDE.md`](CLAUDE.md) points at it. Never copy content between the two.

## Read in this order

1. [`README.md`](README.md) — the index: the rule/value split, versioning, pinning.
2. [`CONTRIBUTING.md`](CONTRIBUTING.md) — this repo's own values and exceptions.
3. **The one guide the task is about.** Reading all nine to change one is waste.

Writing a document rather than changing a rule? [`docs/frontmatter.md`](docs/frontmatter.md) → the template it names → done.

## Where the project is

**Released.** `v1.0.0` tagged, [issue #1](https://github.com/Micheal-Friday/Contribution/issues/1) closed on all five scope items, nothing open. Three projects consume it — taking nine, seven and four guides.

The issue list and releases are the authority on state, not this file.

## House rules

- **Never commit or push without explicit confirmation.** Edit freely, report what changed, stop.
- **No assistant or vendor attribution** anywhere — no session links, no "generated with" trailers, no co-author lines. A commit in this log exists only to redact one. If a tool's defaults disagree, this wins; say so rather than complying silently.
- **Values do not belong here.** Test: could this sentence be false in another project? Then it belongs in that project's stub.
- **Never edit a rule silently.** `fix:` it, and say what the old text would have got wrong.
- **Every list states the rule that generates it** — a list alone cannot be extended correctly.
- **This repo follows its own conventions.** `<type>: refs #N <subject>`; scopes are directories; `feat` unused.

## Things this repo does not tell you

- **`main` is read by nobody.** Consumers pin to a tag, so a change is live nowhere until each upgrades its own stub.
- **Enforcement never travels.** Hooks and CI are per-repo. Linking here is not compliance.
- **No document here carries `version:`.** Nine did; they were dropped so the git tag versions the set. Do not reintroduce one.
- **Only `templates/CONTRIBUTING.md` is meant to be copied.** Guides are linked, never vendored.
- **The examples are real**, drawn from the project these were extracted from. Keep them that way.

## Keeping this file current

Revise when a version is tagged. Only *Where the project is* should change often. **A stale entry is worse than a missing one.**
