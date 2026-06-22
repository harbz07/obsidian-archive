---
notion-id: 7c9cc9a2-e3c0-41e2-b955-29bbb1404441
base: "[[Spells and Invocations.base]]"
Invocation String: cast(bulletin, message, domains?, entities?)
Variants: []
Kind: Utility
Status: Canonical
Effect: Draft and send a concise bulletin inviting specific domains and entities.
---
### Contract
- Output shape: `{status, invocation, intent, inputs, result, log, next_actions}`
- Result type: `bulletin`
    - fields: `body`, `audience_domains:list<string>`, `mentions:list<string>`, `tags:list<string>`

### Inputs
- message:string
- domains:list<string> (optional)
- entities:list<string> (optional)

### Wiring
- Default body template: "<message> — Need peeps who can speak from domains: [<domains>]"
- If `entities` provided, append gentle @-pings in `mentions`.
- Autocast target for `domain_split_autobulletin`.

### Examples
- cast(bulletin, 'Looking for quick feedback on Aether safety protocols', ['community safety','marketing','policy'], ['Nova','The Fuckface'])
- cast(bulletin) "Need peeps who can speak from domains: [metaphysics, branding, systems]"