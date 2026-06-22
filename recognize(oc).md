---
notion-id: 6d63a8c7-d57d-4d44-a9e7-627701967c28
base: "[[Spells Grimoire.base]]"
Mechanisms:
  - OCR
  - Validation
  - Preprocessors
Path: /spells/ingest_pipeline/recognize_oc
Kind: Ingest.spell
Status: Ready
Aliases: recognize_oc
Added On: 2025-11-19
Previous step: []
Link OK: OK
Intent: Scan handwritten notes, extract text, and layer live commentary/insight.
Next step:
  - "[[Notion/Spells Grimoire/consolidate|consolidate]]"
Contracts: "structured_note required: {id, raw_text, clean_text, commentary[], source{file,capture_timestamp}, context{tag,page_number}}. Global output shape applies."
Signature: recognize(oc, source)
---
### Contract
- Output `structured_note` must always exist with required fields.
- Behavior guarantees:
    - raw_text is never empty; fallback "[[unreadable|unreadable]]" on OCR fail
    - clean_text always exists
    - commentary is an array (can be empty)
    - id unique per call

### Inputs
- required: source:image|pdf_scan
- optional: context_tag, date|timestamp, session_id

### Wiring
- process:
1) OCR handwriting → raw text
2) structure into lines/blocks
3) attach commentary blocks (paraphrase, implicit arguments/jokes/themes, open questions)
4) write structured_note to /buffer/notes

### Notes
- Acts as scanner + tiny co-philosopher.