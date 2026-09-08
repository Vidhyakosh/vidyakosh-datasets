# Vidyakosh datasets

Downloadable content packages for the [Vidyakosh](https://github.com/Vidhyakosh/Vidyakosh) Android app.
The app fetches `manifest/*.json` on demand, shows the packages in **Content library** and on each subject's
PYQ / chapter screen, and downloads them from this repository's GitHub Releases. Every package is
verified (SHA-256 + schema) before it is installed locally; nothing is required online for learning.

This repository is a **read-only publishing target** for packaged, downloadable content. The authoring
sources (chapter JSON, PYQ sources, etc.) live in private companion repositories under the Vidhyakosh
organisation (`content-cbse`, `content-icse`, `content-state-boards`, `content-schema`); the build /
publish pipeline is in [`Vidhyakosh/Vidyakosh`](https://github.com/Vidhyakosh/Vidyakosh) — see
[`tools/pyq/publish-datasets.sh`](https://github.com/Vidhyakosh/Vidyakosh/blob/main/tools/pyq/publish-datasets.sh).

## Folder layout

```
vidyakosh-datasets/
├── README.md                          # this file
├── manifest/                          # catalogued, versioned, SHA-256-verified package lists
│   ├── pyq.json                       # schema vidyakosh-dataset-catalog/1 — PYQ packages
│   └── content.json                   # schema vidyakosh-dataset-catalog/1 — chapter-content packages
├── status/                            # machine + human-readable status of every class/subject/board
│   ├── README.md                      # index page
│   ├── cbse.md                        # CBSE, class 1–12, every subject
│   ├── icse.md                        # ICSE + ISC, every class/subject
│   └── state-boards.md                # 16 state boards, every class/subject
├── ROADMAP.md                         # the long-term content roadmap
├── CONTRIBUTING.md                    # how to contribute chapter content / PYQs
├── ISSUE_TEMPLATE/
│   ├── chapter-content.md             # template: track one (class, subject) chapter-content gap
│   ├── pyq-coverage.md                # template: track PYQ coverage gap for one (board, class, subject)
│   └── board-coverage.md              # template: track a whole new board / curriculum source
└── .github/
    └── labels.md                      # convention for issue / PR labels
```

## Package kinds

| `kind`  | Manifest      | Schema                      | One package =                              | Use case                                |
|---------|---------------|-----------------------------|--------------------------------------------|-----------------------------------------|
| `pyq`   | `pyq.json`    | `vidyakosh-pyq-package/1`   | one (board, class, subject, year, session) | CBSE board papers, year-wise            |
| `chapters` | `content.json` | `vidyakosh-chapters-package/1` | one (board, class, subject)              | summaries + NCERT exercise solutions    |

Each package is a single `.zip` released under a date tag (`pyq-YYYY.MM.DD` or `content-YYYY.MM.DD`).
The zip layout is documented in each `manifest/*.json` package entry's `schema` field.

## Current coverage snapshot

Generated from the `manifest/*.json` catalogues on every release. The `status/` files are
hand-maintained narratives (with a generated table at the top) so contributors know exactly what
exists and what is missing.

### CBSE Classes 1–7 (active scope)

| Class | Math | Science | English | Hindi | Social Science | Sanskrit |
|------:|:----:|:-------:|:-------:|:-----:|:--------------:|:--------:|
| 1     | ✅ 13/13 | n/a     | ✅ 9/9  | ✅ 19/19 | n/a          | —        |
| 2     | ✅ lists only | n/a | ✅ lists only | ✅ lists only | n/a | —        |
| 3     | ✅ lists only | n/a | ✅ lists only | ✅ lists only | n/a | —        |
| 4     | ✅ lists only | n/a | ✅ lists only | ✅ lists only | n/a | —        |
| 5     | ✅ lists only | n/a | ✅ lists only | ✅ lists only | n/a | —        |
| 6     | ✅ 10/10  | ✅ 12/12 | ✅ lists only | ✅ lists only | ✅ lists only | —        |
| 7     | ✅ lists only | ✅ lists only | ✅ lists only | ✅ lists only | ✅ lists only | —        |

✅  = chapter list + summaries + NCERT solved questions packaged & downloadable from the app.
"lists only" = chapter list present, content pending (shows "awaiting contribution" honestly in-app).
"n/a" = subject is not in the NCERT syllabus for that class.

### CBSE Classes 8–12 (backlog)

See [`ROADMAP.md`](./ROADMAP.md) for the backlog of Class 8–12 chapter content and PYQs.

### ICSE / ISC and 16 state boards

`subjects.json` exists for every (board, class) — those boards render in the app. Chapter content
follows the state-specific textbooks, not NCERT, so a different curriculum source is needed before
chapters can be authored. Tracked in [`status/state-boards.md`](./status/state-boards.md).

## How releases are produced

```
local source: content-cbse/, content-icse/, content-state-boards/   (private repos)
        │
        │  vkpyq package --kind chapters --out dist/chapters --version YYYY.MM.DD
        │  vkpyq package --kind pyq      --out dist/pyq      --version YYYY.MM.DD
        ▼
manifest/content.json  +  zips  →  PR to this repo  →  release tag content-YYYY.MM.DD / pyq-YYYY.MM.DD
        │
        ▼
APK:  BundledContentRepository        In-app download:  DownloadsViewModel + DatasetRepository
                                       (SHA-256 verified, schema-checked)
```

Provenance: NCERT chapter content is © NCERT (Government of India); PYQ questions are © CBSE and
are reproduced for non-commercial education. Pipeline code (MIT) and contributed summaries/solutions
(CC-BY-SA-4.0) live in the [Vidyakosh](https://github.com/Vidhyakosh/Vidyakosh) app repository.

## Latest releases

- **chapters**: see [latest content release](../../releases/latest) — `manifest/content.json` lists
  every chapter-content package with its SHA-256.
- **PYQs**: see the latest `pyq-YYYY.MM.DD` release — `manifest/pyq.json` lists every year-subject
  package with its SHA-256.
