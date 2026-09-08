# Vidyakosh datasets — content roadmap

This is the long-term roadmap for what content the Vidyakosh app should ship. Each item is a
milestone that is broken down into per-(class, subject, board) GitHub issues. The goal is for every
"ship" release to push the table in `README.md` forward by a few rows, and for every contributor
to be able to grab one open issue, do the work, open a PR, and get a clean review.

## Done (in the current app releases)

These are already downloadable from the latest release:

- **CBSE Class 10 Mathematics** — 14/14 chapters, 293 NCERT exercise questions solved, summaries,
  formulas. Packaged + bundled.
- **CBSE Class 10 Science** — 13/13 chapters, 391 in-text + exercise questions answered, summaries.
  Packaged + bundled.
- **CBSE Class 6 Mathematics** — 10/10 chapters, summaries + 18 original practice questions
  packaged + bundled.
- **CBSE Class 6 Science** — 12/12 chapters, summaries + original practice questions packaged +
  bundled.
- **CBSE Class 10 English / Social Science** — partial (18/29 + 7/22 chapters with original
  practice questions), in the v0.4.0 feature branch.
- **CBSE Class 1 Math / English / Hindi** — chapter lists only (v0.5.0 feature branch).
- **CBSE Class 10 PYQs** — 9,928 questions, 5 years (2022–2026), main + compartment, across
  Mathematics / Science / Social Science / English. 1,017 with marking-scheme answers.

## Now (Class 1–7 CBSE focus)

The next push is filling the NCERT corpus for Classes 1–7 (CBSE), since these are the classes with
the highest learner volume and the curriculum is the same NCERT book for every learner. The work is
broken into per-(class, subject) issues; each one is a small, reviewable unit of work.

| Milestone | Items | Status |
|---|---:|:---|
| Class 1 (Math / English / Hindi) | 3 subjects | chapter lists done, content issues open |
| Class 2 | 3 subjects (Math / English / Hindi) | chapter lists done, content issues open |
| Class 3 | 3 subjects | chapter lists done, content issues open |
| Class 4 | 3 subjects (Math / English / Hindi) | chapter lists done, content issues open |
| Class 5 | 3 subjects (Math / English / Hindi) | chapter lists done, content issues open |
| Class 6 (English / Hindi / SST) | 3 subjects | Math + Sci done, these 3 are the gaps |
| Class 7 (all 5 main subjects) | 5 subjects | none done yet, all chapter lists needed |

## Next (Class 8–10, 12)

The exam classes. Higher stakes, larger payoff, but each book is bigger.

| Milestone | Items | Status |
|---|---:|:---|
| Class 8 (Math / Science / English / Hindi / SST) | 5 subjects | none done |
| Class 9 (Math / Science / English / Hindi / SST) | 5 subjects | none done |
| Class 10 (English / Hindi / SST completion) | 3 subjects | partial, fill the gaps |
| Class 11 (PCM / PCB / Commerce / Humanities streams) | ~15 subjects | none done |
| Class 12 (PCM / PCB / Commerce / Humanities streams) | ~15 subjects | none done |

## Later

| Milestone | Why | Status |
|---|---|---|
| ICSE Class 10 (English / Math / Science / SST / Hindi / Computer) | 2nd most popular board | subjects.json only |
| ISC Class 11 / 12 (PCM / PCB / Commerce / Humanities) | 2nd most popular board | subjects.json only |
| State board Class 10 (16 boards × ~5 main subjects) | significant regional learner share | subjects.json only |
| PYQ expansion: CBSE Class 12 (5 years × 4 subjects × main + compartment) | exam-class follow-up | not started |
| PYQ expansion: top state boards (Maharashtra, Tamil Nadu, UP, etc.) | regional PYQ need | not started |
| Hindi-medium summaries (Class 6–10) | bilingual learners | not started |

## Honest states

If a (class, subject) has no chapter content yet, the app renders it as "awaiting contribution" —
never a fake empty list. The matching GitHub issue explains what is missing and what file to author.
A subject that is partially done (e.g. Class 10 English 18/29 chapters) renders the missing
chapters as "awaiting contribution" too.

## Honesty contract

Solutions are written with AI assistance from the NCERT text and are labelled **AI-assisted ·
unverified** in the app until a human reviewer signs them off (`verification.status: verified`).
The roadmap does not consider a subject "done" until a domain reviewer has checked the AI-assisted
content and the in-app badge flips from amber to green.
