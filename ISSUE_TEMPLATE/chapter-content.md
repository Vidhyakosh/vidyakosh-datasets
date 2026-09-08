---
name: Chapter content for one (class, subject)
about: Track summaries + NCERT solved questions for one (class, subject) pair
title: "[class-N] <subject> chapters: summaries + NCERT exercise solutions"
labels: ""
---

## Scope

- Board: <!-- CBSE / ICSE / ISC / state board id (e.g. mh-state-board) -->
- Class: <!-- 1..12 -->
- Subject: <!-- mathematics / science / english / hindi / social-science / … -->
- Textbook: <!-- e.g. NCERT Ganita Prakash 6 (new NCF 2023) -->
- Edition: <!-- 2023–24 / 2024–25 / … -->

## Current state

- [ ] chapter list exists in `chapters.json`
- [ ] N/M chapters have summaries
- [ ] N/M chapters have NCERT exercise questions solved
- [ ] N/M chapters have in-text questions answered
- [ ] on-device smoke test done in the APK
- [ ] `verification.status` flipped to `verified` by a reviewer

## Deliverable

For every chapter in the subject:

1. `summary.points` (4–8), `summary.takeaways` (2–3), `summary.remember` (2–3),
   `summary.formulas` (if applicable).
2. Every NCERT exercise question in the printed book, solved:
   - `id` like `ncert-<class>-<subject>-<chN>-ex<sec>-q<n>`
   - `stem` (clean, with proper LaTeX-style markup)
   - `solution.approach`, `solution.steps[]`, optional `hints[]`
3. Every NCERT in-text question with a `solution.steps[]` model answer.
4. All questions tagged with their sub-section `topic`.
5. `verification.status: "ai-assisted-unverified"` until a reviewer checks.

## How to author

```bash
# 1. Skeleton from the NCERT PDF
python3 tools/textbook/extract_ncert.py /path/to/chapter-N.pdf \
  --chapter N --title "Chapter Title" --out content-cbse/.../chapters/ch-NN-skel.json

# 2. Clean up the skeleton by hand (or with assistant help), then save as ch-NN.json

# 3. Merge into the subject's chapters.json
python3 tools/textbook/merge_chapters.py content-cbse/boards/cbse/classes/class-XX/<subject>

# 4. Validate
node content-schema/validate.mjs content-cbse

# 5. Rebuild the APK-bundled index
cd tools && VK_CONTENT_DIR=../vidyakosh-content node compile-content.mjs

# 6. Run the APK on a device / emulator and confirm the new chapters render
```

## Acceptance

- [ ] `validate.mjs` passes for the subject
- [ ] APK smoke test on the relevant screens (`Subject detail`, `Chapter detail`,
      `Chapter summary`)
- [ ] No "awaiting contribution" badges on this subject
- [ ] `verification.status` reviewed by a human and either kept
      `ai-assisted-unverified` (with a note) or flipped to `verified`
- [ ] `content` release is published (`tools/pyq/publish-datasets.sh YYYY.MM.DD chapters`)

## Out of scope

- Adding the chapter list itself (use the `chapter-list` template for that)
- Cross-subject/board mapping or naming work
- App-side renderer changes
