# Supported source formats

This is the initial scope for the AI-assisted conversion workflow, not a claim that this repository contains automatic file parsers.

## Supported first phase

### JSON
- Top-level arrays of records.
- Common wrapper objects with a question array such as `questions`, `items`, `data`, or supported `bank` structures.
- Alias mapping when the field meaning is unambiguous.
- Report malformed records and fields that cannot be mapped.

### CSV
- Header-based tables are preferred.
- Typical columns may include question/stem, options or choice columns, correct answer/key, rationale/explanation, topic, subject, tags, source, and difficulty.
- Quoted commas and escaped quotes must be respected by the CSV reader.
- If answer choices are spread across columns, preserve their source order.
- If a key refers to a label not present in the data, mark it for review.

### Plain text
- Convert only when question boundaries, choice labels, answer keys, and rationale boundaries can be identified reliably.
- If formats vary within a file, separate reliably parsed records from review-required sections.

### Markdown
- Headings, numbered questions, bullet choices, and tables can be used when their relationships are clear.
- Do not assume every numbered list is a question bank.
- Preserve relevant headings as subject/topic metadata when appropriate.

## Not in first-phase guarantees

DOCX, XLSX, PDF/OCR, scans, images, embedded diagrams, complex tables, audio, and video are not guaranteed by this specification. If a user supplies one of these, explain what the current environment can actually read and ask for an export to CSV, Markdown, plain text, or JSON when needed.

## Images and external resources

Preserve image URLs and file paths when they are part of the source. A JSON reference does not embed an image. Tell the user if referenced local files need to be copied or packaged separately and verify that the destination can resolve them before claiming they will display.
