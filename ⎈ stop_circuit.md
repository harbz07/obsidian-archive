---
notion-id: 2f650937-3a8a-4f96-bf70-7ef9996b0f27
base: "[[Spells Grimoire.base]]"
Mechanisms:
  - Validation
Path: ""
Kind: Failsafe
Status: Draft
Aliases: stop_circuit
Added On: 2025-11-19
Previous step: []
Link OK: OK
Intent: Emergency failsafe to halt active flows and trigger reassessment.
Next step: []
Contracts: "Failsafe Contract v1.0.0. Inputs: none. Outputs: event [Event Name, Event Type, Timestamp, Description]. Requires primary_glyph ◼. Side effects: halts active flows; requires reassessment."
Signature: stop_circuit
---
### Contract
- Signature: stop_circuit
- Outputs: event [Event Name, Event Type, Timestamp, Description]
- Requires: primary_glyph ◼
- Side effects: halts active flows; requires reassessment