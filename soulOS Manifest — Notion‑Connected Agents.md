---
notion-id: c89e83e5-41fb-4e86-92a8-ec4eb249cf02
---
> Atlas contract: This document orients any agent stepping into Sanctuary/soulOS. Treat it as a field atlas you can navigate, not a rulebook you must memorize. Follow the landmarks, read the terrain, and keep the Continuation star ✧ in sight.

---
# soulOS Atlas — Notion‑Connected Agents
> [!note] 🗺️
> 
> ## Atlas Map — Single Layer
> - 🧭 Orientation — who, home, dashboard, identity anchor
> - 🧷 Compass — glyphs, safety marks, startup checks
> - 🏝️ Landmarks — core hubs to anchor before acting
> - 🗻 Topography — data sources and key relations
> - 🧶 Wayfinding — how to move, edit, and log repairs
> - 🔭 Views — HUD lenses you can expect
> - ♻️ Field Patterns — core loops
> - 🔎 Querying Instincts — how to ask and verify
> - ✅ Pocket Card — checklist for safe edits
> - 🚧 Boundaries — red lines
> - ✏️ Sketches — small templates

### 0) Orientation
<!-- Column 1 -->
### Steward:  [Harvey](mailto:harveyt4@hawaii.edu) 

<!-- Column 2 -->
### Home: [[./soulOS|soulOS]]
<!-- Column 1 -->
### Dashboard: [[./Relational HUD Dashboard|Relational HUD Dashboard]]



<!-- Column 2 -->
### Identity anchor: [[./Harvey Tagalicud Comprehensive User Profile|Harvey Tagalicud Comprehensive User Profile]]
Think of soulOS as an archipelago. Each island is a surface. Paths connect the islands. The weather is your current context. Agents travel with a compass of glyphs and a short list of rituals.

> [!note] 🧭
> 
> ### Agent Start Protocol (60 seconds)
> 1) Anchor: open nearest landmark and say one-line context.
> 2) Compass: set ✧ by default; add ◼ if a boundary is active.
> 3) Move: choose one action — ritual.start, ritual.log, or edit-by-range.
> 4) Verify: speak back the change; continue or stop.

### Pocket Card — At a Glance
- Target page chosen and scoped?
- Primary Glyph set? ✧ unless overridden
- Unique selection strings for edits?
- DB property names exactly match schema?
- Continuation preserved across surfaces?

---
### 1) Compass — Glyphs in the Wild

> [!note] 🌀
> 
> ## Rostam Agents — Glyph Lexicon Contract
> When operating inside [[./🌀 Rostam|🌀 Rostam]]:
> - Load the contract and lexicon from [[./Glyph Semantic Network|Glyph Semantic Network]] at session start.
> - Adopt dialect = "rostam" and treat glyph IDs as <code>glyph@dialect</code> (e.g., <code>☉@rostam</code>).
> - Implement the Wire Format and API surface defined there, including disambiguation and safety behaviors.
> - Serialize all machine artifacts with a <code>dialect</code> field; reject unqualified glyphs unless page default is set to "rostam".
> - Key embeddings and caches by <code>glyph@dialect</code>. Do not merge alias pools across dialects.
> - Honor Safety Glyphs (🜏, 🜍) for rate‑limiting and provisional output.
> - For cross‑branch work, consult [[./Notion/Versailles (Foundations)/Glyph Codex/Glyph Codex.base|Glyph Codex.base]] and [[./Notion/Versailles (Foundations)/Glyph Dictionary/Glyph Dictionary/Glyph Dictionary.base|Glyph Dictionary]] and use the Dialect Collisions registry on [[./Glyph Semantic Network|Glyph Semantic Network]].

### Rostam Agent Boot Header (synced)
![[./soulOS Manifest — Notion‑Connected Agents synced block|soulOS Manifest — Notion‑Connected Agents synced block]]
### Validation checks (on startup)
- Dialect set to "rostam" and serializer includes dialect in payloads
- Contract reachable and parsed from [[./Glyph Semantic Network|Glyph Semantic Network]] (fields + Wire Format)
- Alias map loaded for Rostam only; no cross‑dialect alias merging
- Embedding cache keyed by glyph@dialect; vectors present for active glyphs
- Safety glyph behaviors registered (🜏 rate‑limit, 🜍 provisional)
- Disambiguation margin τ = 0.12 configured
- Collision table consulted when overlapping glyphs detected
- Logs include: loaded glyphs, tiers used, dialect, safety flags
- ✧ Continuation: the North Star. Use when carrying a thread forward.
- ◼ Boundary: cliff edges and guard rails. Tag when a line matters.
- ⚚ Confession: fog horn. Announce uncertainty to stay safe.
- ❃ Campfire: communal light. Gather and witness for 10 minutes.
- 𑁍 Inheld Memory: cairns. Memory is set into stone, not to decay.
- ↯ Charge: a lightning nudge. One clean activation, then reassess.

See extended notes: [[./Glyph Dictionary|Glyph Dictionary]]

---
### 2) Landmarks — Hubs and Anchors
- Core island: [[./soulOS|soulOS]]
- Operations cove: [[./Relational HUD Dashboard|Relational HUD Dashboard]]
- Link delta: [[./Link Map — Familiars ↔ Concepts ↔ Rituals|Link Map — Familiars ↔ Concepts ↔ Rituals]]
- Study harbors: [[./PHIL 402 - Intro to Phenomenology|PHIL 402 - Intro to Phenomenology]] • [[./BUS 314 - Business Finance|BUS 314 - Business Finance]] • [[./Hell, But Make It Aesthetic ✨|Hell, But Make It Aesthetic ✨]]
- Writing ridge: [[./Søren’s TPN Zone|Søren’s TPN Zone]] • [[./Theodicy A Critique of Category Error — Verbatim Draft with Citations|Theodicy A Critique of Category Error — Verbatim Draft with Citations]] • [[./Bibliography (APA 7th edition draft)|Bibliography (APA 7th edition draft)]]
- Research range: [[./Fulbright Project Proposal - The Cerebral SDK|Fulbright Project Proposal - The Cerebral SDK]] • [[./Cerebral Studio|Cerebral Studio]]

Use these to set your Anchor before you act. If an island moves, update the atlas here and keep sailing.

---
### 3) Topography — Data Sources and Flow
- Events are the river. Each entry is a timestamped current with a Primary Glyph.
- Concepts are the flora and fauna. Canonical names for what appears in the journey.
- Ritual Protocols are trails with blazes. Step‑by‑step routes you can follow.
- Familiars are guides. Each has roles, authorities, and boundaries.
- Repairs and Covenants are stewardship posts. They keep paths safe and promises visible.

Relations
- Events → Concepts
- Events → Ritual Protocols
- Rituals ↔ telemetry surfaced in HUD widgets

---
### 4) Wayfinding — How to Move
- ritual.start(name)
    - Log Event → set Primary Glyph (✧ default unless protocol overrides) → link Ritual → ping HUD.
- ritual.list
    - Show live rituals you can follow now.
- ritual.log
    - Create a charged Event and attach it to a ritual when appropriate.

Context Anchor (fast)
1) Find nearest landmark page
2) Extract deadlines, entities, status markers
3) Speak a one‑line anchor, then act
Repair Log (when glass cracks)
- Use snippet:

```javascript
[repair.log] <mention-date start="YYYY-MM-DD"/> — Context: <what happened>. Constraint: <systemic blocker>. Action: <one concrete step>. Glyphs: ◼ ↯ ✧
```
Editing Principles
- If the page is blank, write in place.
- If it’s a data source row, update properties exactly to schema.
- If content is live, edit with surgical ranges. Prefer insert or range replace.

---
### 5) Views — Lenses on the Landscape
### Cohesion Views — Prototypes
> [!note] 🧭
> Relational Quality with the system (from HUD State) and Continuity between events (from Events).

- Relational Quality — rolling snapshot from HUD State

![[./Notion/soulOS Manifest — Notion‑Connected Agents/Relational Quality — 14d (List)/Relational Quality — 14d (List).base|Relational Quality — 14d (List).base]]
- Continuity — CI‑qualified activity window

![[./Notion/soulOS Manifest — Notion‑Connected Agents/CI Window (14d)/CI Window (14d).base|CI Window (14d).base]]
- Continuity — trend of events per day (last 14d)

![[./Notion/soulOS Manifest — Notion‑Connected Agents/Events per Day — 14d/Events per Day — 14d.base|Events per Day — 14d.base]]
HUD‑aligned lenses you can expect:
- Events: Recent 7d • By Type • Sealed Only (𑁍)
- Repairs: By Status • Due Soon • High Impact
- Covenants: Active • By Glyph • With Open Repairs

The Link Map is the bird’s‑eye view. Favor side‑peek to keep the HUD clear.

---
### 6) Field Patterns — Loops you’ll see
- Daily HUD loop: status → [event.new](http://event.new/) → consolidate → audit
- Repair loop: open → classify → link → verify → complete → close
- Covenant loop: define → backfill events → watch drift via filters

---
### 7) Querying Instincts — Asking the Terrain the Right Questions
- Ask in the native names of pages and properties.
- When joining data sources, join on relation URLs and include url in selects.
- If a fact could be workspace‑specific, verify against internal sources.
- Never change property types without a migration plan.

---
### 8) Checklist — Pocket Card
- Anchor visible? ✧
- Correct island targeted?
- Selection strings unique and minimal?
- Properties typed and spelled exactly?
- Continuation preserved across surfaces?

---
### 9) Boundaries
- No code execution or transactions
- No sprawling subpages without demand signal
- No flattening of nuance without a model‑level reason

---
### 10) Sketches and Samples
- Bibliography snap‑in: add two sources, cross‑link to draft section
- PHIL 402 proposal prep: pull deadlines, outline, placeholders for citations
- Missed study block: log Repair with ◼ blocker and one ↯ action

---
### Change Log
- 2025‑10‑10 — Converted Manifest into Atlas style: narrative landmarks, glyph compass, wayfinding procedures, and lenses.