---
notion-id: 4ae82203-61b9-495c-93fe-eec92310d7f1
base: "[[Spells and Invocations.base]]"
Invocation String: autocast(domain_split → bulletin)
Variants: []
Kind: Utility
Status: Canonical
Effect: Auto-draft a bulletin from a domain split result when the next reply is germane.
---
### Contract
- Sequence: [cast.domain_split, cast.bulletin]
- Conditional trigger: next_user_reply_is_germane
- Output: `bulletin` object per cast.bulletin
- Global shape preserved `{status, invocation, intent, inputs, result, log, next_actions}`

### Wiring
- Heuristics for "germane":
    - Reply references ≥1 candidate domain or quick affirmative (yes/ok/that one) within 500 chars.
    - Prefer low-friction confirmation; do not block on missing entities.
- Bulletin template: «{user_input}» — Need peeps who can speak from domains: {consideration_set}.
- Safety rails: autotrigger once per domain_split result; off-topic reply → `status:"deferred"` and `next_actions:["clarify domains or message"]`.

### Example Flow
1) cast(domain split, 'Design a safer, non-extractive growth loop for Aether')
2) User: "Let’s look at marketing + safety." → Autocast bulletin with returned set.