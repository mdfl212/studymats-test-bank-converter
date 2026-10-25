# StudyMats question-bank schema

The canonical export is a JSON array of question records. The main application's template is [tools/test_bank_template.json](https://github.com/mdfl212/mdfl212.studymats.io/blob/main/tools/test_bank_template.json). Keep this guide synchronized with that file and the Question Authoring Studio importer.

## Fields

| Field | Expected type | Requirement | Notes |
|---|---|---|---|
| `id` | string | Required for a clean conversion | Unique within the draft. The importer can generate or adjust IDs, but report collisions. |
| `subject` | string | Recommended | The importer can assign the selected destination subject. |
| `topic` | string | Optional | A blank topic may be defaulted to `General` by the editor. |
| `question` | string | Required | Non-empty question stem. `stem` is a common source alias only when unambiguous. |
| `questionImage` | string or `null` | Optional | Preserve a URL/path where supplied. A referenced local image may need to travel separately. |
| `options` | array of strings | Required | At least two distinct, non-empty choices. `choices` may be mapped when clearly equivalent. |
| `correctAnswer` | integer | Required | Zero-based index into `options`: first choice is 0, second is 1, etc. |
| `rationale` | object | Required | Must include non-empty `text` and an `images` array. |
| `rationale.text` | string | Required | Do not invent missing explanations. Flag absent content. |
| `rationale.images` | array | Required | Use an empty array when no rationale images are present. |
| `source` | string | Optional | Preserve source/reference information where available. |
| `difficulty` | string or compatible source value | Optional | Preserve the source value; report any normalization. |
| `tags` | array of strings | Optional | Use an empty array if no tags are supplied. |
| additional fields | JSON-compatible values | Conditional | Preserve when compatible and non-conflicting; report any dropped or transformed fields. |

## Accepted wrappers

The importer can recognize a top-level array and common wrapper objects with an array under `questions`, `items`, `data`, or certain `bank` shapes. For the converter's output, prefer the canonical top-level array.

## Answer-key conversion

StudyMats uses a zero-based numeric answer index. For example, an answer key of `B` maps to `1` only when option B is demonstrably the second option in the final `options` array. If the source uses shuffled choices, multiple answers, missing labels, or unclear keys, flag the record rather than guessing.

## Import validation reminders

The current importer checks for a question stem, at least two non-empty distinct choices, a valid answer index, and non-empty rationale text. Duplicate IDs may be made unique during import and possible duplicate stems may be reported. Conversion should catch these issues before handoff whenever possible.

## Example

See [the template](../templates/studymats-question-bank.template.json). Its content is illustrative and not intended as authoritative subject-matter content.
