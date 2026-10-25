# StudyMats Test Bank Converter

Convert existing question banks into the JSON format accepted by the StudyMats Question Authoring Studio—using an AI-assisted, review-first workflow.

**This repository is a conversion skill and format guide, not a standalone converter app or automatic file parser.** It helps an AI transform source material without silently inventing answers or losing source information.

## Start here

- **[Open the documentation website](https://mdfl212.github.io/studymats-test-bank-converter/)**
- [Step-by-step conversion tutorial](docs/tutorial.html)
- [AI conversion instructions](SKILL.md)
- [Canonical JSON template](templates/studymats-question-bank.template.json)
- [Schema and field reference](docs/schema.md)
- [Supported source formats](docs/supported-formats.md)
- [Recommended conversion workflow](docs/workflow.md)
- [Sample source](examples/sample-source.md) · [Sample output](examples/sample-output.json)
- [Manual validation cases](tests/validation-cases.md)

## Quick start

1. Prepare a source bank in **JSON, CSV, plain text, or Markdown** with clear question boundaries, choice order, answer keys, and rationales.
2. Give an AI assistant the instructions in the **SKILL.md** file and the source material in a format that assistant can actually read.
3. Ask for a valid UTF-8 JSON array, plus a conversion report covering warnings, skipped records, duplicates, ambiguous keys, and fields or media that were transformed or lost.
4. Validate the JSON and compare answer keys and rationales against the original source.
5. Import the file into the StudyMats Question Authoring Studio, inspect the preview and validation notes, and confirm only after review.

## Supported first-phase inputs

- JSON
- CSV
- Plain text
- Markdown

DOCX, XLSX, PDF/OCR, scans, diagrams, complex tables, and image-heavy source banks are **not guaranteed** by the first-phase specification. Export to CSV, Markdown, plain text, or JSON when needed. Preserve local image files separately; a JSON path does not embed an image.

## Conversion principles

- Preserve the original meaning, wording, answer key, rationale, references, choice order, and relevant metadata.
- Never guess a correct answer or fabricate a rationale. Flag missing or uncertain information for review.
- Report invalid records, duplicate IDs, likely duplicate stems, ambiguous answer keys, missing required fields, and information that could not be represented.
- Preserve compatible unknown fields when safe; report fields that are dropped or transformed.
- Treat conversion as a proposal for human review, not a substitute for subject-matter validation.

## Use with StudyMats

The Question Authoring Studio can import a JSON question bank locally. Select a destination subject, inspect the preview and validation notes, then confirm the import. The browser import workflow does not upload the selected source file to a server; the privacy handling of any AI tool used during conversion depends on that service.

Canonical template in the main application repository: [tools/test_bank_template.json](https://github.com/mdfl212/mdfl212.studymats.io/blob/main/tools/test_bank_template.json).

## Downloads

- [Download the complete repository ZIP](https://github.com/mdfl212/studymats-test-bank-converter/archive/refs/heads/main.zip) (GitHub branch archive; not an installer)
- [Download the AI conversion skill](https://raw.githubusercontent.com/mdfl212/studymats-test-bank-converter/main/SKILL.md)
- [Download the JSON template](https://raw.githubusercontent.com/mdfl212/studymats-test-bank-converter/main/templates/studymats-question-bank.template.json)

## Status and limitations

This repository contains instructions, examples, documentation, and manual validation cases. It does not currently contain a standalone conversion web app, automatic file parsers, or an automated end-to-end import test. Do not claim automated tests or runtime integrations exist unless they are added and actually run.

## License

[MIT License](LICENSE).
