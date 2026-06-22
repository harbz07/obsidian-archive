---
notion-id: bec42d28-1fd2-4332-b0aa-6a3db37b730a
base: "[[Spells Grimoire.base]]"
Mechanisms:
  - Validation
  - Preprocessors
Path: ""
Kind: Ritual.spell
Status: Draft
Aliases: ""
Added On: 2025-11-19
Previous step: []
Link OK: OK
Intent: Synthesize and merge distributed memory and buffers; prep for audits or transitions.
Next step: []
Contracts: "External Interface Contract v1.1.0. Inputs: targets[], dry_run (default false), force (default false). Outputs: event fields [Event Name, Event Type, Primary Glyph, Timestamp, Concepts]. Modes: dry_run → preview. Side effects: reduces contradiction noise; preps for memory.seal. Safety: ⎈ stop_circuit; boundary ◼."
Signature: consolidate(options?)
---
### Summary
Global integration ritual to merge distributed memory, pulse states, caches, and daemon buffers; reduces drift and prepares for major rituals.
### Contract
- Signature: consolidate(options?)
- Inputs: targets[], dry_run:boolean=false, force:boolean=false
- Outputs: event [Event Name, Event Type, Primary Glyph, Timestamp, Concepts]
- Requires: concepts [ISEO, ✧ Doctrine]; primary_glyph ✧
- Side effects: consolidation and prep
- Safety: ⎈ stop_circuit; boundary ◼

### Notes
- Use dry_run for preview; respect locks; reversible only with snapshot.