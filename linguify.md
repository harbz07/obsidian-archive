---
notion-id: 01162673-c4df-4eeb-b994-9ebb88d31538
base: "[[Spells Grimoire.base]]"
Mechanisms:
  - Dataset export
  - Glyph awareness
  - Validation
  - Preprocessors
  - Schema dispatch
  - Export layer
Path: /spells/ingest_pipeline/linguify
Kind: Export.spell
Status: Ready
Aliases: /linguify
Added On: 2025-11-19
Previous step:
  - "[[Notion/Spells Grimoire/consolidate|consolidate]]"
Link OK: OK
Intent: Convert a consolidated .docx into a structured dataset for LLM fine-tuning or RAG.
Next step: []
Contracts: "Dataset export guarantees: outputs dataset.jsonl + metadata.json; examples adhere to selected schema (philosophy|humor|hybrid); attach glyphs_detected and glyph_structures."
Signature: /linguify(source:/docs/<name>.docx, mode?)
---
### Contract
- Modes: philosophy | humor | both(hybrid)
- Each example includes required fields per schema; attach glyph metadata; deterministic for same inputs.
- Exports: dataset.jsonl + metadata.json; logs errors and skipped units without aborting batch.

### Inputs
- source_doc: /docs/<name>.docx
- optional: mode, granularity, schema

### Wiring
- Validation layer ensures stable unit structure; soft errors logged.
- Preprocessors: remove OCR artifacts, normalize whitespace.
- Mode dispatch → schema implementations
- Glyph Awareness Module:
    - detect glyphs in text/commentary
    - adjust tone/weights; add glyph_tags; include glyphs_detected
- Export layer writes JSONL and metadata; maintains ordering.

### Notes
- Failsafe: Glyph Immunity Mode if too many glyph errors in batch.