# StudyMats Test Bank Converter

Convert existing question banks into the JSON format accepted by the StudyMats Question Authoring Studio.

This repository defines an **AI-assisted conversion skill and format guide**. It is designed to help an AI transform source material into a clean, reviewable StudyMats question bank without silently inventing answers or losing important source information.

## Start here

- [AI conversion instructions](SKILL.md)
- [Canonical JSON template](templates/studymats-question-bank.template.json)
- [Schema and field reference](docs/schema.md)
- [Supported source formats](docs/supported-formats.md)
- [Recommended workflow](docs/workflow.md)
- [Example source](examples/sample-source.md)
- [Example output](examples/sample-output.json)
- [Validation cases](tests/validation-cases.md)

## Supported first-phase inputs

- JSON
- CSV
- Plain text
- Markdown

Word documents, spreadsheets beyond CSV, PDFs/OCR, diagrams, and image-heavy source banks are future extensions; do not claim these are automatically supported by this repository.

## Important behavior

- Preserve the original meaning, answer key, rationale, references, and relevant metadata.
- Never guess a correct answer or fabricate a rationale. Flag uncertain or missing information for review.
- Report invalid records, duplicate IDs, likely duplicate stems, ambiguous answer keys, missing required fields, and any information that could not be represented.
- Preserve compatible unknown fields when safe, and report fields that are dropped or transformed.
- Output a JSON **array** of question records for direct StudyMats import.
- Conversion is a proposal for human review, not a substitute for subject-matter validation.

## Use with StudyMats

The Question Authoring Studio can import a JSON question bank locally. Select a destination subject, inspect the preview and validation notes, then confirm the import. The browser import workflow does not upload the selected source file to a server.

Canonical template in the main application repository: [tools/test_bank_template.json](https://github.com/mdfl212/mdfl212.studymats.io/blob/main/tools/test_bank_template.json)

## Status

Initial documentation and examples. This repository does not yet contain a standalone conversion web app or automated parser. Do not imply automated tests or runtime integrations exist unless they are added and run.
