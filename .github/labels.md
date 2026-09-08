# Issue & PR label convention

This is the convention used by `Vidhyakosh/vidyakosh-datasets` to keep the issue tracker
navigable. Every issue should carry **one `scope:*` label** and **at least one `type:*` label**.
PRs additionally carry a `stage:*` label.

## Scope (which class / board / subject is this about?)

One of:

- `class:1`, `class:2`, …, `class:12` — CBSE / NCERT class
- `board:icse`, `board:isc` — ICSE / ISC (ISC is the Class 11/12 board of ICSE)
- `board:ap`, `board:as`, `board:br`, `board:gj`, `board:hr`, `board:ka`, `board:kl`, `board:mh`,
  `board:mp`, `board:od`, `board:pb`, `board:rj`, `board:tn`, `board:ts`, `board:up`, `board:wb`
  — state boards

## Type (what work is this?)

At least one of:

- `content:chapter` — chapter summary + NCERT solved questions for one (class, subject)
- `content:chapter-list` — only the chapter list (no summaries / questions yet)
- `content:pyq` — PYQ dataset for one (board, class, subject, year, session)
- `content:review` — human-review pass on AI-assisted content (`verification.status` → `verified`)
- `infra:manifest` — changes to `manifest/*.json` shape, schema, or generation
- `infra:release` — release-engineering work (publish script, tag handling, package size budget)
- `docs` — README / ROADMAP / status updates only
- `app:download` — app-side code change required to make the new data downloadable

## Priority

- `p:critical` — blocks a release
- `p:high` — in the current quarter
- `p:medium` — next quarter
- `p:low` — nice-to-have, opportunistic

## Stage (PRs only)

- `stage:authoring` — chapter content / PYQ data being authored
- `stage:validation` — running through the pipeline + on-device smoke
- `stage:published` — already in a release

## Common

- `good first issue` — small enough for a new contributor
- `help wanted` — needs domain knowledge (e.g. Kannada-medium reviewer)
- `duplicate` — close as duplicate (link to the original)
- `wontfix` — explicitly out of scope (close with a one-line reason)
