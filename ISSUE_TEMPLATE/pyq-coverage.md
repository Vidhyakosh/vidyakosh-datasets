---
name: PYQ coverage for one (board, class, subject)
about: Track one PYQ dataset gap — one (board, class, subject, year, session) paper set
title: "[PYQ] <board> class-<N> <subject> <year> <session>"
labels: ""
---

## Scope

- Board: <!-- CBSE / ICSE / state board id -->
- Class: <!-- 1..12 -->
- Subject: <!-- mathematics / science / english / hindi / social-science / … -->
- Year: <!-- e.g. 2025 -->
- Session: <!-- Main / Compartment / Second board exam -->
- Paper sets: <!-- 30-1-1, 30-1-2, 30-1-3, 30-2-1, 30-2-2, 30-3-… -->
- Source URL: <!-- https://www.cbse.gov.in/cbsenew/question-paper.html or state board portal -->

## Current state

- [ ] PDF(s) downloaded and OCRed
- [ ] N/N question stems extracted (with exact text)
- [ ] N/M marked questions have marking-scheme answers
- [ ] N/K questions mapped to a chapter (keyword match)
- [ ] Snippet images (math / figures) extracted for non-recoverable questions
- [ ] Dataset file emitted at `content-<board>/boards/<board>/classes/class-XX/<subject>/pyqs/<year>-<session>.json`
- [ ] On-device smoke test (PYQ year screen → question rendering)
- [ ] `content` release published

## Deliverable

- One `pyqs/<year>-<session>.json` per paper set (one file per (year, session))
  with schema `vidyakosh-pyq/1`, containing:
  - `questions[]` with `id`, `paperCode`, `qNumber`, `text` (and/or `snippet`),
    optional `answer.markingScheme`
  - `pyqs[]` per chapter mapping with `chapter` + `confidence`
  - `source` with the official paper URL
- One packaged zip in the next `pyq-YYYY.MM.DD` release:
  `cbse-10-mathematics-2024-main.zip` etc., with the SHA-256 listed in
  `manifest/pyq.json`.

## How to author

```bash
# 1. Build the question-paper catalog (idempotent)
python3 -m vkpyq catalog

# 2. Fetch + OCR + parse + emit for this (class, subject)
VK_CONTENT_DIR=../vidyakosh-content python3 -m vkpyq all \
  --class 10 --subject mathematics --year 2024

# 3. Marking-scheme answers (optional but recommended)
VK_CONTENT_DIR=../vidyakosh-content python3 -m vkpyq answers \
  --class 10 --subject mathematics

# 4. Keyword-based chapter mapping
VK_CONTENT_DIR=../vidyakosh-content python3 -m vkpyq map \
  --class 10 --subject mathematics

# 5. Regenerate the QA report
python3 -m vkpyq report

# 6. Validate, then package
node content-schema/validate.mjs content-cbse
VK_CONTENT_DIR=../vidyakosh-content python3 -m vkpyq package --kind pyq \
  --out vidyakosh-content/dist/pyq --version $(date +%Y.%m.%d)
```

## Acceptance

- [ ] `validate.mjs` passes (PYQ files are validated with a separate rule set)
- [ ] APK smoke test: open the year → question renders, "back" navigation works
- [ ] QA report (`docs/pyq-qa-report.md`) shows 0 unparsed questions for this set
- [ ] Published in a `pyq-YYYY.MM.DD` release
