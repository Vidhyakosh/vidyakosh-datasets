# ICSE + ISC content status

ICSE (Class 10) and ISC (Class 11–12) use their own council-prescribed textbooks — not NCERT — so
chapter content cannot be copied from CBSE. Authoring source files exist at
`content-icse/boards/icse/...` and `content-icse/boards/isc/...` (private authoring repo); this
status file mirrors the board's class/subject list.

## ICSE (Class 1–10)

| Class | Status | Notes |
|---|---|---|
| 1–5 | ❌ | subjects.json shipped, no chapter lists yet |
| 6    | ❌ | subjects.json shipped, no chapter lists yet |
| 7    | ❌ | subjects.json shipped, no chapter lists yet |
| 8    | ❌ | subjects.json shipped, no chapter lists yet |
| 9    | ❌ | subjects.json shipped, no chapter lists yet |
| 10   | ❌ | subjects.json shipped, no chapter lists yet. **Next priority after CBSE Classes 1–7.** |

The ICSE Class 10 syllabus covers (typically): English, Hindi, Sanskrit, French, German, Spanish,
Mathematics, Physics, Chemistry, Biology, History & Civics, Geography, Computer Applications,
Commercial Studies, Economic Applications, Environmental Science, Art, etc.

The official syllabus PDFs are the canonical source — see
[isc.int](https://www.isc.in/Common-Pattern-of-Syllabus) (formerly cisce.org).

### Class 10 PYQs

Not started. The ICSE board does not publish a single official PYQ archive equivalent to CBSE's;
papers are scattered across school websites. This is a multi-month effort.

## ISC (Class 11–12)

| Class | Status | Notes |
|---|---|---|
| 11 | ❌ | subjects.json shipped, no chapter lists yet |
| 12 | ❌ | subjects.json shipped, no chapter lists yet. High-priority (board exam class). |

The ISC Class 12 syllabus covers (typically): English, Hindi, Sanskrit, French, German, Spanish,
Mathematics, Physics, Chemistry, Biology, Accounts, Commerce, Economics, Business Studies,
Computer Science, History, Geography, Sociology, Political Science, Psychology, Art, etc.

### Class 12 PYQs

Not started.

## Authoring sources

The ICSE / ISC council prescribes a single textbook per (class, subject) from a short list of
publishers (Morning Star, APC, Oswaal, Cordova, etc.). The chapter content JSON must cite the
specific edition in `verification.source` and the `textbook` field.

## How to author

See [`CONTRIBUTING.md`](../CONTRIBUTING.md) — the flow is the same as CBSE except the source
textbook is the ICSE / ISC one and the manifest entry uses `id: icse-10-<subject>-chapters` or
`id: isc-12-<subject>-chapters`.
