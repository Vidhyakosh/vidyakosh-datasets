# Vidyakosh datasets

Downloadable content packages for the [Vidyakosh](https://github.com/Vidhyakosh/Vidyakosh) Android app.
The app fetches `manifest/pyq.json`, shows the packages in **Content library** and on each subject's PYQ screen,
and downloads them from this repository's GitHub Releases. Everything is verified (SHA-256, schema) before it is
installed locally; nothing is required online for learning.

| Manifest | Contents |
|---|---|
| `manifest/pyq.json` | Previous-year board question packages: one zip per board · class · subject · year · session |

Package zip layout: `package.json` (metadata), `questions.json` (schema `vidyakosh-pyq/1`), `img/*.webp` (exact renderings
of questions whose mathematics or figures are not recoverable as text).

Provenance: the questions are extracted from the official CBSE question-paper archive
(https://www.cbse.gov.in/cbsenew/question-paper.html) by the open-source pipeline in `tools/pyq` of the app repository.
Answers come only from CBSE marking schemes; chapter mapping is keyword-based and labelled with a confidence. The question
papers are © CBSE and are reproduced here for non-commercial education; the pipeline and this manifest are MIT.

Rebuild: `python3 -m vkpyq package --out dist/pyq --version <YYYY.MM.DD>` then `tools/pyq/publish-datasets.sh`.
