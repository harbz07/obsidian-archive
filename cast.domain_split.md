---
notion-id: 592d5857-5501-4a99-ab48-8757d7ec25e3
base: "[[Spells and Invocations.base]]"
Invocation String: cast(domain_split, source_text?, min_domains=4)
Variants: []
Kind: Cast
Status: Canonical
Effect: Propose multiple concrete domains with rationales and confidence scores.
---
### Contract
- Output shape must be: `{status, invocation, intent, inputs, result, log, next_actions}`
- Result type: `domain_consideration`
    - fields: `consideration_set:list<string>`, `rationale:map<string,string>`, `confidence:map<string,number>`

### Inputs
- source_text:string (default = last user message)
- min_domains:int (default 4)

### Wiring
- Selection algorithm:
    1. Extract key terms and intents from `source_text`.
    2. Map to candidate domains via synonym table + co-occurrence map.
    3. Score by overlap, novelty, actionability; ensure ≥4 with rationales.
    4. Backfill with adjacent domains to diversify if <4 found.
- Autocast hook: emits signal eligible for `domain_split_autobulletin` if next reply is germane.

### Examples
- cast(domain split)
- cast(domain split, 'scale Aether as a safer after-hours space in Honolulu')

### Notes
- Domain taxonomy seed available; expand as needed.
- Logs include binding, mapping, selection steps.