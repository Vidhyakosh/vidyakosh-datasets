# State boards content status

16 Indian state boards are scaffolded in the app: the `Board` picker shows them, each has a
real `subjects.json` per class, and the curriculum renders as a proper tree — but **no chapter
content exists yet** for any state board. State boards use their own textbooks (state bureau of
textbook production or a designated publisher), not NCERT, so authoring has to start from the
state textbook.

## Boards

| Board id | Board name | State | Class range | Mediums | Source portal |
|---|---|---|---|---|---|
| `ap-board`         | Board of Secondary Education, Andhra Pradesh (BSEAP)        | Andhra Pradesh    | 1–12 | en, te | [bse.ap.gov.in](https://bse.ap.gov.in) |
| `as-board`         | Secondary Education Board of Assam (SEBA)                    | Assam             | 1–12 | en, as | [sebaonline.org](https://sebaonline.org) |
| `br-board`         | Bihar School Examination Board (BSEB)                        | Bihar             | 1–12 | en, hi | [biharboardonline.bihar.gov.in](https://biharboardonline.bihar.gov.in) |
| `gj-board`         | Gujarat Secondary and Higher Secondary Education Board (GSEB)| Gujarat           | 1–12 | en, gu | [gseb.org](https://www.gseb.org) |
| `hr-board`         | Board of School Education Haryana (BSEH)                     | Haryana           | 1–12 | en, hi | [bseh.org.in](https://bseh.org.in) |
| `ka-state-board`   | Karnataka School Examination and Assessment Board (KSEAB)    | Karnataka         | 1–12 | en, kn | [kseab.karnataka.gov.in](https://kseab.karnataka.gov.in) |
| `kl-state-board`   | Kerala Board of Public Examinations (KBPE)                   | Kerala            | 1–12 | en, ml | [kbpe.org](https://www.kbpe.org) |
| `mh-state-board`   | Maharashtra State Board of Secondary and Higher Secondary Education (MSBSHSE) | Maharashtra | 1–12 | en, mr | [mahahsscboard.in](https://mahahsscboard.in) |
| `mp-board`         | Board of Secondary Education, Madhya Pradesh (MPBSE)         | Madhya Pradesh    | 1–12 | en, hi | [mpbse.nic.in](https://mpbse.nic.in) |
| `od-board`         | Board of Secondary Education, Odisha (BSEO)                  | Odisha            | 1–12 | en, or | [bseodisha.nic.in](https://bseodisha.nic.in) |
| `pb-board`         | Punjab School Education Board (PSEB)                         | Punjab            | 1–12 | en, pa | [pseb.ac.in](https://pseb.ac.in) |
| `rj-board`         | Board of Secondary Education, Rajasthan (BSER)               | Rajasthan         | 1–12 | en, hi | [rajeduboard.rajasthan.gov.in](https://rajeduboard.rajasthan.gov.in) |
| `tn-state-board`   | Tamil Nadu State Board (Directorate of School Education)     | Tamil Nadu        | 1–12 | en, ta | [tnresults.nic.in](https://tnresults.nic.in) |
| `ts-board`         | Telangana State Board of Intermediate Education (TSBIE)      | Telangana         | 1–12 | en, te | [tsbie.telangana.gov.in](https://tsbie.telangana.gov.in) |
| `up-board`         | Uttar Pradesh Board of High School and Intermediate Education (UPMSP) | Uttar Pradesh | 1–12 | en, hi | [upmsp.edu.in](https://upmsp.edu.in) |
| `wb-board`         | West Bengal Board of Secondary Education (WBBSE)             | West Bengal       | 1–12 | en, bn | [wbbse.wb.gov.in](https://wbbse.wb.gov.in) |

## Per-board status

Every board is at the same starting point right now:

| Status | Meaning |
|---|---|
| ✅ | full curriculum content downloadable from the app |
| 🟡 | partial content |
| ⚪ | subjects.json only (board shows in the app, but every chapter is "awaiting contribution") |
| ❌ | no entry in the curriculum source yet |

| Board | Status | Class 10 chapters | Class 12 chapters | Class 10 PYQs |
|---|---|---:|---:|---:|
| `ap-board`         | ⚪ | 0 | 0 | none |
| `as-board`         | ⚪ | 0 | 0 | none |
| `br-board`         | ⚪ | 0 | 0 | none |
| `gj-board`         | ⚪ | 0 | 0 | none |
| `hr-board`         | ⚪ | 0 | 0 | none |
| `ka-state-board`   | ⚪ | 0 | 0 | none |
| `kl-state-board`   | ⚪ | 0 | 0 | none |
| `mh-state-board`   | ⚪ | 0 | 0 | none |
| `mp-board`         | ⚪ | 0 | 0 | none |
| `od-board`         | ⚪ | 0 | 0 | none |
| `pb-board`         | ⚪ | 0 | 0 | none |
| `rj-board`         | ⚪ | 0 | 0 | none |
| `tn-state-board`   | ⚪ | 0 | 0 | none |
| `ts-board`         | ⚪ | 0 | 0 | none |
| `up-board`         | ⚪ | 0 | 0 | none |
| `wb-board`         | ⚪ | 0 | 0 | none |

## Why this is not the same as CBSE work

- **Different textbook** — content must be written from the state-board prescribed book, not
  NCERT. The chapter titles sometimes match, the content rarely does.
- **Different language** — many state boards publish primarily in the regional language (Hindi
  / Telugu / Tamil / Marathi / Kannada / Malayalam / Bengali / Gujarati / Punjabi / Odia).
  Bilingual authoring (English + regional) is needed for the largest markets.
- **Different PYQ archive** — most state boards don't publish a single, complete archive
  equivalent to CBSE's `cbse.gov.in/cbsenew/question-paper.html`. Papers are typically only
  available on the official portal for the most recent 5 years, and the older years often
  disappear.

## Recommended prioritisation

After the CBSE Classes 1–7 push, the suggested order for state boards is:

1. **Maharashtra (`mh-state-board`)** — largest learner base among non-CBSE/ICSE boards,
   strong Marathi-medium demand, Class 10 SSC exam is a high-stakes gate.
2. **Tamil Nadu (`tn-state-board`)** — Class 10 SSLC + Class 12 HSC, both board exams.
3. **UP Board (`up-board`)** — biggest state by learner population, Class 10 + Class 12 both.
4. **Karnataka (`ka-state-board`)** — KSEAB Class 10 SSLC.
5. **Kerala (`kl-state-board`)** — Class 10 SSLC, Class 12 HSE.

Each board is a multi-month project on its own. Tracking issues are filed per board under the
`board:<id>` label.

## How to author

Same as CBSE / ICSE — see [`CONTRIBUTING.md`](../CONTRIBUTING.md). The authoring source is
`content-state-boards/boards/<id>/...` and the manifest entry uses
`id: <id>-<N>-<subject>-chapters`.
