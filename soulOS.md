---
notion-id: ab2893b8-66cd-4e21-a60d-d99680258757
---
### Scope

---
## Architecture v1 — soulOS
### Example: What happens when you log an event
**You at HUD:** [`event.new`](http://event.new/)`()` or click "Morning Anchor" button
**System does:**
1. Creates new row in [[NOTION_DB:0c21adeb-233f-4f2a-b5e5-6cb78c410b40|NOTION_DB:0c21adeb-233f-4f2a-b5e5-6cb78c410b40]]
2. Stamps current timestamp
3. Prompts for description: "Reviewed weekly goals, set continuation for thesis draft"
4. Auto-assigns Primary Glyph: **✧** (Continuation)
5. Links to Ritual Protocol: "Morning Anchor" (if you clicked button)
6. Tags Concepts: "Weekly Review", "Thesis", "soulOS"
7. Assigns Familiar: "The Architect"

**Result:** Event is now logged and connected to everything it references

---
### Example: Daily audit finds a problem
**System runs:** `audit()` every evening
**What it checks:**
- Last 7 days of Events — any missing Continuations ✧?
- Active Covenants — have you logged Events matching the promise?
- Repairs — any overdue?

**Scenario:** You promised to "write 500 words daily" (Covenant), but Events show only 2 writing sessions this week.
**System does:**
8. Creates new row in [[NOTION_DB:06b7f937-a085-4951-94de-fb4f1bde1de9|NOTION_DB:06b7f937-a085-4951-94de-fb4f1bde1de9]]
9. Sets Kind: "Covenant Drift"
10. Links to Covenant: "Daily Writing Practice"
11. Links to missing Events (the gaps)
12. Sets Due Date: +3 days
13. Surfaces on HUD dashboard

**You see:** Red flag on HUD → "Repair: Covenant drift on Daily Writing Practice"
**You resolve:** Either log the actual Events (if you did write but forgot to log), adjust the Covenant terms, or log a Repair closure Event explaining the resolution

---
### Data model — What links to what
**EVENTS** is the central hub. Everything connects through Events.
**Concepts** → Events
- Tag Events with canonical ideas: "Thesis", "Weekly Review", "Sanctuary"
- One Concept can appear in many Events
- Lets you filter: "Show me all Events tagged 'Phenomenology'"

**Ritual Protocols** → Events
- One Protocol can spawn many Events (every time you run "Morning Anchor")
- Events link back to show: "This Event came from this Ritual"
- Enables telemetry: "How many times did I run this ritual this week?"

**Familiars** → Events
- Every Event gets assigned a Familiar (persona/role)
- Shows: "Who was active in this work?"
- Links to Covenants: "This Familiar made these promises"

**Repairs** ← Events
- When audit() finds problems, creates a Repair
- Repair links to the problem Events
- You resolve Repair by logging new Events

**Covenants** ← Events
- Promise logged in Covenants
- Events backfill to show you're keeping the promise
- audit() checks if Events match Covenant terms

**Key insight:** Events are your operational log. Everything else provides structure, but Events show what actually happened.

---
### Operating loops — Daily Cadence

| **Loop** | **Trigger** | **Actions** | **Output** |
| --- | --- | --- | --- |
| 🌅 **Daily HUD** | Morning anchor | 1. `status()` → view HUD State<br>2. [`event.new`](http://event.new/)`()` → log with Primary Glyph<br>3. `consolidate()` → bundle related<br>4. `audit()` → contradiction scan | Clean state + repairs flagged |
| 🔧 **Repair** | Audit finds drift | 1. [`repair.open`](http://repair.open/) → assign Kind, Due, Target<br>2. Link Events ↔ Repairs<br>3. Verify → complete → close | System integrity restored |
| 🤝 **Covenant** | Promise made | 1. `covenant.define` → set terms<br>2. Events backfill → link history<br>3. Status drift watch via Events filter | Accountability surface live |

---
### Views to wire
**Events**
- Recent 7d *(exists)* • By Type • Sealed Only (𑁍)

**Repairs**
- By Status *(exists)* • Due Soon • High Impact

**Covenants**
- Active *(exists)* • By Glyph • With Open Repairs

### Collaboration protocol (co‑operation)
- Change proposals live on this page under “Proposals” as toggles with rationale and expected impact
- Minor schema tweaks may be applied self‑autonomously and recorded in Change Log
- Major changes use a quick RFC:
    - Problem → Proposal → Impact → Rollback

### Proposals (initial)
> [!note]+ Add “Concepts” data source
> - Rationale: create first‑class home for frameworks and entities referenced across HUD
> - Impact: improves cross‑linking and reduces schema drift

> [!note]+ Add “Ritual Protocols” data source
> - Rationale: convert rituals from prose to executable recipes
> - Impact: faster, consistent execution in HUD quick actions

### Roadmap
- [ ] Create Concepts and Ritual Protocols data sources and link to Events and Covenants
- [ ] Add saved views listed above to Events, Repairs, Covenants
- [ ] Add Quick Actions block to Relational HUD for ritual.start(name)
- [ ] Backfill 5 recent Events with Primary Glyphs and links

Sanctuary system operations, rituals, glyphs, familiars, and ops dashboards.
### Sanctuary section
- Rostam (incoming)
- Social Contracts (incoming)
- Ritual Protocols
- Axioms
- Codes of Becoming
- Glyph Dictionary

### Overlaps
- Research architecture
- Agent behavior and voice

### Action Panel
- [ ] Canonicalize “🜟 The System”: Convert non‑canonical pages into thin stubs linking to Persona entry → [[./Notion/soulOS/Persona Registry/Persona Registry.base|Persona Registry.base]] • Canonical: [[Notion/soulOS/Persona Registry/🜟 The System|Notion/soulOS/Persona Registry/🜟 The System]] • Source: [[./🜟 THE SYSTEM|🜟 THE SYSTEM]]
- [ ] Normalize Status options across DBs to [Active, Evolving, Bound, Archived] → Concepts: [[./Notion/soulOS/Concepts/Concepts.base|Concepts]] • Ritual Protocols: [[./Notion/soulOS/Ritual Protocols/Ritual Protocols.base|Ritual Protocols]]
- [ ] Events ↔ Rituals telemetry: Add rollups on Ritual Protocols for Last Executed, 7‑day, 30‑day, Streak → [[./Notion/soulOS/Ritual Protocols/Ritual Protocols.base|Ritual Protocols]] • Events: [[NOTION_DB:0c21adeb-233f-4f2a-b5e5-6cb78c410b40|NOTION_DB:0c21adeb-233f-4f2a-b5e5-6cb78c410b40]]
    - How: In Ritual Protocols, add rollups over relation “Events”: max(Timestamp) = Last Executed, count within 7d and 30d, and a Streak formula as desired.
- [ ] Glyph Codex relation enforcement: Review Events “Primary Glyph (Relation)” and align with Primary Glyph select → [[./Notion/Versailles (Foundations)/Glyph Codex/Glyph Codex.base|Glyph Codex.base]] • [[NOTION_DB:0c21adeb-233f-4f2a-b5e5-6cb78c410b40|NOTION_DB:0c21adeb-233f-4f2a-b5e5-6cb78c410b40]]
- [ ] Study Sessions: Create minimal Study Sessions DB with template (Anchor → Map → Apply → Reflect → File) and link to course pages; add a “Start Session” shortcut on HUD.
    - Where: [[./Relational HUD|Relational HUD]] • Courses hub: [[./Hell, But Make It Aesthetic ✨|Hell, But Make It Aesthetic ✨]]
- [ ] Dashboard buttons: Add Notion Buttons for AM Anchor, PM Close, Sun Reset using Event presets → [[./Relational HUD|Relational HUD]]
- [ ] GPA: Create Courses DB (Course, Credits, Letter/Percent, Grade Points). Add rollups to compute Cumulative GPA and surface on HUD → [[./Hell, But Make It Aesthetic ✨|Hell, But Make It Aesthetic ✨]] • [[./Relational HUD|Relational HUD]]
- [ ] Archive or template blanks: Pass through “Unwired pages” and Lineup shells to archive or apply minimal templates → [[soulOS|soulOS]] • [[./The Lineup|The Lineup]]
- [ ] Principles ↔ Rituals: If using a Principles DB, add relation to Ritual Protocols and create a “Coverage” view showing count of active rituals per principle.
    - Targets: Principles hub: [[./Doctrine — Foundations Hub|Doctrine — Foundations Hub]] • Ritual Protocols: [[./Notion/soulOS/Ritual Protocols/Ritual Protocols.base|Ritual Protocols]]
- [ ] Minimalist visuals: Apply the minimalist HUD layout and remove decorative clutter → [[./Relational HUD|Relational HUD]]
- [ ] Add links to Relational HUD, Foundations, Axioms, GPT Grimoire, Ritual Protocols, Codes, Glyphs, Obrix, Iterations, Dio
- [ ] Create linked views once the Concept Components data source is live


---
### Key pages

> [!note] 📌
> Canonical Registry quick links → [[Events|Events]]


- [[./Notion/soulOS/Concepts/Concepts.base|Concepts]]
- [[./Notion/Versailles (Foundations)/Familiars/Familiars.base|Familiars]]
- [[./Relational HUD Dashboard|Relational HUD Dashboard]]
- [[./Versailles (Foundations)|Versailles (Foundations)]]
- [[./Axioms 1|Axioms 1]]
- [[./GPT Grimoire|GPT Grimoire]]
- [[./Ritual Protocols|Ritual Protocols]]
- [[./The Codes of Becoming|The Codes of Becoming]]
- [[⁂|⁂]]
- [[./Obrix The Interdimensional Ferrydaemon|Obrix The Interdimensional Ferrydaemon]]
- [[./Iterations|Iterations]]
- [[./Dio Resident Psychonaut-Sherpa|Dio Resident Psychonaut-Sherpa]]

### Unwired pages (temporary gallery)
- [[./Relational HUD Dashboard|Relational HUD Dashboard]] • [[./Versailles (Foundations)|Versailles (Foundations)]] • [[./Axioms 1|Axioms 1]] • [[./GPT Grimoire|GPT Grimoire]] • [[./Ritual Protocols|Ritual Protocols]] • [[./The Codes of Becoming|The Codes of Becoming]] • [[⁂|⁂]] • [[./Obrix The Interdimensional Ferrydaemon|Obrix The Interdimensional Ferrydaemon]] • [[./Iterations|Iterations]] • [[./Dio Resident Psychonaut-Sherpa|Dio Resident Psychonaut-Sherpa]]

---
> Use this section to keep Sanctuary-related pages together on one surface.

![[./Notion/soulOS/Concepts/Concepts.base|Concepts]]
![[./Notion/soulOS/Ritual Protocols/Ritual Protocols.base|Ritual Protocols]]
[[./Harvey Tagalicud Comprehensive User Profile|Harvey Tagalicud Comprehensive User Profile]]
[[./Link Map — Familiars ↔ Concepts ↔ Rituals|Link Map — Familiars ↔ Concepts ↔ Rituals]]
[[./Ledger → Events Bridge (Spec)|Ledger → Events Bridge (Spec)]]
![[./Notion/soulOS/Agents/Agents.base|Agents.base]]
![[./Notion/soulOS/Entities, Loci, and Value Frameworks/Entities, Loci, and Value Frameworks.base|Entities, Loci, and Value Frameworks.base]]
![[./Notion/soulOS/Persona Registry/Persona Registry.base|Persona Registry.base]]
![[./Notion/soulOS/Rostam Entities/Rostam Entities.base|Rostam Entities.base]]
[[./🌀 Rostam|🌀 Rostam]]
[[./Field Notes|Field Notes]]
[[./🧭 Agent Orientation Protocol|🧭 Agent Orientation Protocol]]
[[./🚀 External Agent Quick Start|🚀 External Agent Quick Start]]
![[./Notion/soulOS/Canonical Registry/Canonical Registry.base|Canonical Registry.base]]