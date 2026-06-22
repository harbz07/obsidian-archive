---
notion-id: 28598e9c-907e-8092-99c6-f0d9e3ce230d
---
# HUD Palette & View Wiring (Schema-Locked)
## Palette (Updated)
- 🟦 cool blue → cognitive / structural
- 🟩 green → living / active / organic
- 🟨 yellow → creative / experimental
- 🟧 orange → ritual / embodied
- 🟪 purple → metaphysical / liminal
- 🟫 brown → grounded / archival
- ⚪ white → linguistic / lexicon
- ⚫ black → deprecated / void

> Notion caveat: CSV import can’t set Select/Multi-Select colors. After import, set colors in Database → Property → Edit Options. This doc is your color map.

## Concepts (Database) — Select Options & Colors
**Type**
- Principle = 🟦
- Standard = 🟩
- Protocol = 🟪
- Doctrine = 🟨
- System = 🟦
**Status**
- Active = 🟩
- Draft = 🟧
- Bound = 🔵 (Notion: blue)
- Deprecated = ⚫
**Domains**
- System = 🟦
- Ethics = 🟧
- Sanctuary = 🟪
- Ritual = 🟩
- Ops = 🟪
- Lexicon = ⚪
- Archive (optional tag) = 🟫
## Ritual Protocols (Database) — Select Options & Colors
**Type**
- Workflow = 🟩
- Protocol = 🟨
- Form = 🟪
- Ritual = 🟧
- Loop = 🟫 (fallback if needed; or reuse 🟪)
**Status**
- Active = 🟩
- Conceptual = 🟧
- Dormant = 🔵 (blue)
- Deprecated = ⚫
**Domains**
- Sanctuary = 🟩
- Ops = 🟨
- Academic = 🟧
- Body = 🟫 (fallback)
- Cross-Realm = 🟪
**Triggers**
- Time = 🟦
- Emotional = 🟨
- Environmental = 🟩
## HUD Views (build these after import)
1. **Concepts — Gallery by Essence**
    - Card preview: Description
    - Filter: Status != Deprecated
2. **Concepts — Kanban by Status**
    - Swimlanes: Draft · Bound · Active · Deprecated
3. **Ritual Protocols — Board by Domains**
    - Group by: Domains (multi-select; enable show-empty-groups)
4. **Link Map — Familiars ↔︎ Concepts ↔︎ Rituals**
    - Create a Notion page with 3 linked database blocks and synced filters:
        - Left: Familiars (group by Essence)
        - Middle: Concepts (filter: Linked Familiars is not empty)
        - Right: Ritual Protocols (filter: Linked Familiars is not empty)

---
### Collision Notes
This palette uses 🟫=archival/grounded. Existing workspaces sometimes use red for other meanings. After import, check:
- Familiars → *Domains*: some variants use **Cross‑Realm = red**.
- Familiars → *Essence*: some variants use **Memory = red**.
- Associations → *Dialectic Affinity*: **Complementary = red**.
Recommended guardrail: reserve 🟫 for **Concepts/Ritual Protocols** “Archive” tags; leave Familiars/Associations colors as-is to avoid confusion. If you want full unification later, run a one-time recolor migration.