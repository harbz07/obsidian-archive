---
notion-id: 03b39e73-f14a-49a0-b281-4a6de0986663
base: "[[Spells Grimoire.base]]"
Mechanisms:
  - Consolidation
  - Validation
  - Preprocessors
Path: /spells/ingest_pipeline/consolidate
Kind: Transform.spell
Status: Ready
Aliases: /consolidate; LEGACY
Added On: 2025-11-19
Previous step: []
Link OK: Missing
Intent: Compile extracted notes from buffers into a cleaned, single document for reading/editing/archiving.
Next step:
  - "[[Notion/Spells Grimoire/linguify|linguify]]"
Contracts: "word_document required: {doc_path, included_notes, date_range{start,end}, contexts[]}. Always produce a .docx and truthful metadata."
Signature: /consolidate(source?, target?)
---
> [!note] 📦
> **Legacy notice**: `/consolidate` is maintained as a legacy/manual consolidation path. The preferred shaping pipeline is `/extract` → `/shape` → `/consecrate`. Use `/shape` for new work; keep `/consolidate` for backward compatibility and edge cases requiring its specific preprocessing.
> - Successor: `/shape` (Architect.spell)
> - Output parity: both produce .docx + truthful metadata; `/shape` enforces stricter commentary delineation and metadata integrity.

### Contract
- Always produce Word Document + metadata stub, even if buffer empty.
- Required fields present and truthful; duplicate IDs not inserted twice.

### Inputs
- source_buffer default: /buffer/notes
- optional: doc_title, include_commentary (default true), ordering_rule: by_date|by_context|by_source|manual

### Wiring
- process:
1) fetch structured notes
2) clean text (fix OCR errors, normalize spacing, dedupe)
3) assemble (group by context or date; interleave text + commentary; add headings)
4) export .docx with metadata; optionally mark buffer consolidated
- Default ordering: chronological by capture_timestamp; include commentary unless turned off.

### Document Layout
- 
    # Consolidated Notes
- 
    ## <context_tag or "untagged">
- 
    ### Note <id>

<clean_text>
- 
    ### Commentary
- 
    - <commentary items>