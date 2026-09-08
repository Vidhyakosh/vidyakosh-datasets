---
name: Whole-board coverage
about: Track the full curriculum content for one board (e.g. a state board)
title: "[board:<id>] Full curriculum coverage"
labels: ""
---

## Scope

- Board: <!-- e.g. mh-state-board (Maharashtra State Board) -->
- Grades: <!-- typically 1..12, sometimes only 1..10 -->
- Curriculum source: <!-- state board portal / NCERT-equivalent textbook publisher -->
- Mediums: <!-- en / hi / regional language -->
- Official portal: <!-- URL -->

## Why this is a different shape

State boards use their own textbooks, not NCERT. A chapter-content JSON file
that says "Maharashtra State Board Class 10 Mathematics Chapter 3" must be
written from the **state** textbook, not from the NCERT one, even when the
chapter titles look identical. Marking-scheme language, examples, and
end-of-chapter exercises all differ.

## Current state

- [ ] `content-state-boards/boards/<id>/board.json` exists with the right
      `code`, `name`, `website`, `classes.from/to`, `mediums`
- [ ] `content-state-boards/boards/<id>/classes/class-NN/subjects.json`
      exists for every class with the correct subject list
- [ ] At least one (class, subject) `chapters.json` is authored from the
      state textbook
- [ ] At least one (class, subject) chapter has summaries + solved
      questions, packaged, downloadable from the APK
- [ ] The `manifest/content.json` release carries at least one `<id>-*-chapters`
      package

## Deliverable

For every (class, subject) pair in scope:

1. A `chapters.json` whose `verification.source` clearly cites the state
   textbook and edition
2. For at least one (class, subject) in scope, full chapter content
   (summaries + solved questions + in-text Q&A)
3. Packaged, SHA-256 verified, downloadable from the APK

## How to author

```bash
# 1. Get the official textbook PDFs (or the publisher's digital textbook)
# 2. For each chapter:
python3 tools/textbook/extract_ncert.py /path/to/state-textbook-ch-N.pdf \
  --chapter N --title "Chapter Title" \
  --out content-state-boards/boards/<id>/classes/class-NN/<subject>/chapters/ch-NN-skel.json
# 3. Clean up the skeleton and save as ch-NN.json
# 4. Merge
python3 tools/textbook/merge_chapters.py content-state-boards/boards/<id>/classes/class-NN/<subject>
# 5. Validate, compile, package, publish (same as CBSE flow)
```

## Acceptance

- [ ] `validate.mjs` passes for `content-state-boards`
- [ ] APK shows the board in the Board picker with real subject/chapter lists
- [ ] At least one subject downloads and renders
- [ ] Release published
- [ ] Documented in `status/<id>.md`
