# Contributing to Vidyakosh datasets

Thanks for helping to build India's open, offline NCERT learning library. This document explains
how to author and ship a new chapter-content or PYQ package.

## Where the work happens

| Layer | Repository | Audience | What lives here |
|---|---|---|---|
| App (Kotlin) | [`Vidhyakosh/Vidyakosh`](https://github.com/Vidhyakosh/Vidyakosh) | App developers | renderer, repository, downloads, navigation |
| Schema (the JSON contract) | `Vidhyakosh/content-schema` (private) | Content authors + pipeline | `schema/*.json`, `validate.mjs` |
| Authoring source | `Vidhyakosh/content-cbse` / `content-icse` / `content-state-boards` (private) | Content authors | per-(board, class, subject) JSON files |
| Datasets (this repo) | `Vidhyakosh/vidyakosh-datasets` | APK end users (indirect) | packaged zips, manifests, releases |

For most people "contributing content" means opening a PR against the private authoring source
repo, and the pipeline will then re-package and publish here.

## Authoring chapter content (CBSE NCERT)

The minimum viable chapter content file is one per-chapter JSON fragment:

```
content-cbse/boards/cbse/classes/class-06/science/chapters/ch-03.json
```

with the shape defined in [`content-schema`](https://github.com/Vidhyakosh/content-schema) —
see the README in that repo for the exact JSON contract. At a high level each chapter fragment
carries:

- `n` — chapter number (matches `chapters.json`)
- `summary` — `points`, `takeaways`, `remember`, optional `formulas` for math/science
- `questions` — NCERT in-text + exercise questions with `stem`, `hints`, `solution` (steps),
  optional `answer`, optional `snippet` image ref
- `topic` — the sub-section the question belongs to (e.g. `"3.4 Acids and Bases"`)

The honest contract:

- Every NCERT exercise question for the chapter must be solved (no skipping).
- Every in-text question must have a model answer (`solution.steps`).
- Summaries should be 4–8 `points` + 2–3 `takeaways` + 2–3 `remember` items.
- `verification.status` stays `"ai-assisted-unverified"` until a reviewer checks it.

Use `python3 tools/textbook/extract_ncert.py <pdf>` to produce a *skeleton* from the NCERT PDF,
then fill in the clean stems, symbols, and solutions.

## Verifying locally

```bash
# Validate every chapter JSON against the schema
node content-schema/validate.mjs content-cbse

# Merge per-chapter fragments into the subject's chapters.json
python3 tools/textbook/merge_chapters.py content-cbse/boards/cbse/classes/class-06/science

# Rebuild the APK-bundled index (re-runs schema validation, then compiles)
cd tools && VK_CONTENT_DIR=../vidyakosh-content node compile-content.mjs

# Package chapter-content zips + the content manifest
VK_CONTENT_DIR=../vidyakosh-content python3 -m vkpyq package --kind chapters \
  --out vidyakosh-content/dist/chapters --version $(date +%Y.%m.%d)

# (Optional) Re-package the PYQ side too
VK_CONTENT_DIR=../vidyakosh-content python3 -m vkpyq package --kind pyq \
  --out vidyakosh-content/dist/pyq --version $(date +%Y.%m.%d)
```

## Publishing a release

When a meaningful batch of content is ready, the maintainer runs:

```bash
tools/pyq/publish-datasets.sh YYYY.MM.DD pyq
tools/pyq/publish-datasets.sh YYYY.MM.DD chapters
```

This pushes the new manifest to this repo and creates the `pyq-YYYY.MM.DD` / `content-YYYY.MM.DD`
release with all the `.zip` assets attached.

## Labelling conventions

See [`.github/labels.md`](.github/labels.md) for the issue / PR label taxonomy. Every content
issue should carry exactly one **scope** label (`class:1`, `class:6`, `board:icse`, …) and at least
one **type** label (`content:chapter`, `content:pyq`, …).
