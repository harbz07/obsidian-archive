---
notion-id: affd0a31-122b-415f-83e0-ceb2dfef7cfd
base: "[[Spells Grimoire.base]]"
Mechanisms:
  - Schema dispatch
  - Export layer
  - Validation
Path: ""
Kind: Command.spell
Status: Draft
Aliases: ""
Added On: 2025-11-19
Previous step: []
Link OK: OK
Intent: Generate a typed inter-relational graph from Sanctuary knowledge with ready-to-render formats.
Next step: []
Contracts: "External Interface Contract v1.0.0. Inputs: query string, options object. Outputs: graph_bundle {nodes, edges, legend, formats, stats}. Side effects: none by default; may write receipt if provenance=archive."
Signature: graph(query, options?)
---
### Contract
- Signature: graph(query, options?)
- Inputs: query:string, options:object
- Outputs: graph_bundle {nodes, edges, legend, formats [json|mermaid|dot|graphml], stats}
- Side effects: none by default; optional archive receipt

### Wiring
- Supports scope, include/exclude filters, reductions, and layout hints.