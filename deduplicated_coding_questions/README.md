# Deduplicated Coding Questions

This folder contains the consolidated coding/programming questions extracted from the PDSA-OPPE repository.

## Processing rules

- Scan every file under OPPE1, OPPE2 and OPPE3.
- A file may contain multiple questions; each question is evaluated separately.
- Include questions that ask students to write, debug, predict, explain, modify, or analyze code/program output, including SQL/Python/R/Java and similar programming tasks.
- Exclude purely conceptual, theory, and mathematics-only questions.
- Deduplicate identical or near-identical questions, including minor wording differences.
- Preserve the exact wording of the representative question from its first occurrence.
- Keep materially different questions separate even when they belong to the same concept/topic, especially when the task, code, input, output, or constraints differ.
- Count every occurrence, including repeated occurrences within the same file.

## Question record

Each deduplicated question will contain, where available:

- `id`
- `concept`
- `statement`
- `boilerplate_code`
- `inputs`
- `outputs`
- `constraints`
- `other_relevant_info`
- `occurrence_count`
- `sources`

The data is being populated progressively as the repository is fully scanned and verified.
