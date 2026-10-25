# Recommended conversion workflow

1. **Inventory the source.** Identify format, number of apparent records, answer-key conventions, choice ordering, and any attached media.
2. **Map fields.** Match source columns/fields to the StudyMats schema. Document aliases and transformations.
3. **Convert conservatively.** Preserve wording and choice order. Never infer a missing correct answer or rationale.
4. **Validate structure.** Check JSON syntax, field types, required fields, distinct choices, answer index range, IDs, rationale, tags, and image references.
5. **Reconcile counts.** Explain how source records map to clean conversions, conversions with warnings, review-required records, and invalid/skipped records. Avoid counting the same record in multiple top-level categories.
6. **Report losses.** Name each field or media item that was dropped, flattened, transformed, or left unresolved.
7. **Hand off for review.** Provide JSON and a human-readable warning list. Ask the user to review uncertain records and import the file through the StudyMats preview.
8. **Do not claim an end-to-end import test** unless the file was actually imported and checked in the application.

## Suggested conversion report

- Source records detected
- Converted cleanly
- Converted with warnings
- Manual review required
- Invalid/skipped
- Duplicate IDs detected / IDs generated
- Possible duplicate stems
- Missing required fields
- Ambiguous or missing answer keys
- Image/media references requiring attention
- Unknown fields preserved
- Unknown fields transformed or dropped

Define whether review-required records are included in the output or held separately. Keep the counts reconcilable and do not silently omit records.
