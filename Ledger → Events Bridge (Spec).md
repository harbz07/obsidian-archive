---
notion-id: 50586a23-f145-4e68-8f00-614f0b90906e
---
### Ledger → Events Bridge (Spec)
- Purpose: Single source of truth for SanctuaryUI ↔ Events mapping.
- Contract
    - ledger.kind → Events.Event Type
    - ledger.entity → Events.Familiar
    - ledger.tags → Events.Concepts
    - ledger.summary → Events.Description
    - ledger.timestamp → Events.Timestamp
    - ledger.ctx (optional) → Events.Meta
- Ritual enforcement
    - ritual.start(name): 1) log Event → 2) assign Primary Glyph → 3) link to Ritual → 4) HUD ping
    - Default glyph: ✧ for Continuance domain unless protocol overrides
- CI policy hooks
    - Target ≥ 80%, nudge at 70%, weekly reset
    - Guardrails: “Missing Continuation”, “CI Nudge Window” views in Events
- Notes
    - 𑁍 events are non‑decaying; others decay on a 14‑day cycle unless re‑acknowledged
    - Palette: brown = archival

---
> [!note] 📌
> Implementation-ready. If an automation or script posts ledger records, it should apply this mapping and honor the ritual.start contract.