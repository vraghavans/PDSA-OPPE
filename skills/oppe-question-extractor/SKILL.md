# OPPE Question Extractor Skill

## Purpose

Extract, preserve, classify, and deduplicate programming/coding questions from the PDSA OPPE repository (`PDSA OPPE1`, `PDSA OPPE2`, `PDSA OPPE3`) and similar exam repositories.

The highest-priority requirement is **source fidelity**. The original visual assets must never be redrawn, approximated, or replaced by AI-generated graphs, diagrams, screenshots, tables, or charts.

## Core rule: preserve source visuals exactly

When a source contains a graph, diagram, screenshot, table image, flowchart, chart, or other visual that forms part of a question:

1. Preserve the original source asset whenever technically possible.
2. If the source is a PDF, retain the original page/image asset extracted from that PDF.
3. If the source is a Markdown/HTML file with an image URL, preserve the original URL and download/copy the original asset when possible.
4. Do **not** redraw or recreate the visual.
5. Do **not** substitute an AI-generated image.
6. Do **not** infer missing graph edges, labels, values, coordinates, colours, or layout from OCR alone.
7. OCR may be used to make the visual searchable and to recover text, but the original visual remains authoritative.
8. If extraction cannot preserve the visual reliably, place the question in `deduplicated_coding_questions/image_questions_backlog.md` with its exact source path and all available image URLs/assets rather than guessing.

## Recommended document extraction backends

Prefer an open-source local parser such as **MinerU** or **Docling** for PDFs and image-heavy documents.

MinerU supports PDF/image/DOCX inputs, OCR, image extraction, tables, Markdown/JSON output, scanned PDFs, and layout visualization. Use it as an extraction aid, not as an image recreation engine.

Docling supports advanced PDF layout understanding, reading order, tables, code, formulas, image classification, and Markdown/JSON export. It is also suitable as a fallback or cross-check.

When available, run both on difficult documents and compare extracted text/layout. Never use a generated reconstruction when the original source asset is available.

## Repository scan

Scan every file recursively under:

- `PDSA OPPE1/`
- `PDSA OPPE2/`
- `PDSA OPPE3/`

A file may contain multiple questions. Do not assume one file equals one question.

## What counts as a coding question

Include questions that ask students to:

- write or implement code
- complete a function/program
- debug or modify code
- predict program output
- analyze code/program behavior
- implement an algorithm/data structure
- write SQL or database code
- write Python/R/Java or other executable code
- solve a programming task using a supplied program skeleton

Exclude purely conceptual/theory/math questions unless the question explicitly requires code/program analysis.

## Exact wording and deduplication

- Preserve the exact wording of the representative question from its **first occurrence**.
- Do not rewrite, standardize, improve grammar, or paraphrase the source statement.
- Minor wording differences count as the same question when the underlying task is materially the same.
- Same topic/concept does **not** mean same question.
- Keep separate questions when code, input, output, constraints, required behavior, or task are materially different.
- Count every appearance, including repeated appearances within one file.
- Record all source references for every occurrence.

## Question record format

Each deduplicated question should contain:

1. Question ID (`Q001`, `Q002`, ...).
2. Exact representative statement from the first occurrence.
3. Student/boilerplate context from the source.
4. Input specification.
5. Output specification.
6. Constraints/relevant information.
7. Occurrence count.
8. Every source path/reference.
9. Original visual assets/URLs when applicable.
10. Full reference implementation.
11. Student implementation context.

## YOUR CODE HERE rule

If the original source contains `YOUR CODE HERE` markers:

- Preserve the full runnable source program.
- Preserve every existing `YOUR CODE HERE` marker exactly where it occurs.
- Do not replace unrelated code with invented markers.
- Include a separate **Full Reference Code** section containing the complete solution.

If the source is a complete implementation question without `YOUR CODE HERE`:

- Do not invent a marker.
- Preserve the original function/program signature and surrounding context.
- State that the student is expected to implement the requested function/program.
- Include the full reference implementation separately.

## Image/PDF workflow

For PDFs:

1. Acquire the original PDF.
2. Parse its text layer if present.
3. Detect pages containing images/screenshots/graphs/diagrams.
4. Extract/render the original visual at sufficient resolution.
5. OCR the page/image only to obtain searchable text.
6. Associate extracted text with the original page/image.
7. Extract each coding question.
8. Preserve the original page/image in the resulting question record.
9. If fidelity cannot be guaranteed, put it in the image backlog.

For image-only questions:

1. Preserve the original image URL/asset.
2. OCR only when the workflow explicitly permits processing that image.
3. Never replace the source image with a reconstruction.
4. If OCR is deferred, record the question in `image_questions_backlog.md`.

## Image backlog

Use:

`deduplicated_coding_questions/image_questions_backlog.md`

For deferred image questions, record:

- source directory
- exact source file path
- question/file identifier
- all image URLs present in the source
- image asset names/paths where available
- reason for deferral

Do not invent question text for deferred image questions.

## Output location

Write deduplicated questions under:

`deduplicated_coding_questions/`

Do not modify existing question IDs merely to make wording look cleaner. When updating an existing question, preserve its ID unless the evidence proves it is a different question.

## Quality checks before commit

Before committing:

- Verify every source file was examined.
- Verify multiple questions within one source file were not missed.
- Verify duplicates were counted rather than silently discarded.
- Verify first-occurrence wording is unchanged.
- Verify source references are complete.
- Verify all original visuals are preserved or deferred to the image backlog.
- Verify no graph/diagram was AI-redrawn.
- Verify reference code is complete.
- Verify `YOUR CODE HERE` markers are preserved exactly when present.
- Verify no purely conceptual question was included.

## Preferred processing strategy for this repository

For ordinary text/code files, use direct source extraction.

For PDFs and image-heavy documents, use MinerU first where available, with Docling as a fallback/cross-check. Keep the original PDF/page/image alongside the extracted Markdown/text so visual fidelity can always be verified.

The extractor is allowed to improve **machine readability** of text, but it is never allowed to improve or alter the **visual source**.
