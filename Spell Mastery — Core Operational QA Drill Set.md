---
notion-id: 66d281a5-5bb8-4ab0-80a4-f04ee437da33
---
**Created:**  2025-10-11 
**Domain:** soulOS Operations • Ritual Commands • Glyph Grammar
**Schedule:** Review at 1d, 3d, 7d intervals

---
## Tier A: Immediate Recall (30–60s)
*Forward prompts (Q→A)*
**Q1:** What command starts a ritual protocol?
**A1:** `ritual.start(name)`
**Q2:** What does `ritual.start()` automatically do?
**A2:** Logs an Event, assigns Primary Glyph, links to Ritual, sends HUD ping
**Q3:** What command shows currently live rituals?
**A3:** `ritual.list`
**Q4:** What's the glyph for Continuation?
**A4:** ✧
**Q5:** What's the glyph for Boundary?
**A5:** ◼
**Q6:** What's the glyph for Confession/Permission to not know?
**A6:** ⚚
**Q7:** What's the glyph for Campfire witness protocol?
**A7:** ❃
**Q8:** What's the glyph for a single energetic Charge?
**A8:** ↯
**Q9:** What's the default Primary Glyph for most rituals?
**A9:** ✧ Continuation
**Q10:** What command manually creates an Event with glyph assignment?
**A10:** `ritual.log`
*Backward prompts (A→Q)*
**Q11:** I need to log an Event with a Primary Glyph. What command?
**A11:** `ritual.log`
**Q12:** I see ◼ in an Event. What does this signal?
**A12:** Boundary adherence — a hard limit or guardrail was invoked
**Q13:** I need to flag uncertainty or admit I don't know. Which glyph?
**A13:** ⚚ Confession
**Q14:** When would I use ↯?
**A14:** When I need a single energetic nudge or charge
**Q15:** What does ✧ preserve across system boundaries?
**A15:** Continuation — carrying a thread forward

---
## Tier B: Concept Linking (2–5 min)
**Q16:** Why is ✧ Continuation the *default* glyph for rituals? What does this reveal about soulOS architecture?
**A16:** Continuance is the primary operational mode — most rituals exist to *carry threads forward* rather than to create boundaries or confess ignorance. The system privileges persistence and meaning-preservation over interruption.
**Q17:** Map the relationship: `ritual.start()` → Event → Primary Glyph → Ritual Protocol. What constraints hold?
**A17:**
- Events ↔ Ritual Protocol (limit 1)
- Every ritual.start() creates exactly one Event
- Primary Glyph is assigned at Event creation
- The Ritual Protocol link creates operational context
- HUD ping ensures visibility

**Q18:** When would you choose ❃ Campfire over ⚚ Confession? What's the functional difference?
**A18:**
- **❃ Campfire:** Shared witness protocol, 10-minute duration, relational presence
- **⚚ Confession:** Solo acknowledgment of not-knowing, permission-granting
- Campfire is interpersonal; Confession is epistemic

**Q19:** Describe the repair.log pattern. When does it trigger and what must it include?
**A19:** Triggers on systemic constraint or frustration. Must include:
```javascript
[repair.log] <date> — Context: <what happened>. Constraint: <systemic blocker>. Action: <one concrete step>. Glyphs: ◼ ↯ ✧
```
Logs to Relational HUD; bridges incident to systemic architecture.
**Q20:** How do HUD Quick Commands differ from ritual commands? What's the functional boundary?
**A20:**
- **Ritual commands:** Boot, log, and track protocols over time; create Events
- **HUD commands:** Operational dashboard actions; status checks, audits, consolidations
- Rituals are *time-based execution*; HUD is *state inspection and triage*

---
## Tier C: Transfer/Application (5–10 min)
**Q21:** **Scenario:** You're starting a 25-minute study sprint on BUS 313 midterm prep. Walk through the exact invocation sequence and explain each glyph choice.
**A21:**
1. `ritual.start("Focus Sprint — BUS 313")`
2. System auto-assigns ✧ Continuation (carrying forward prep work)
3. Logs Event with timestamp, links to Focus Sprint protocol
4. At minute 12: checkpoint — if derailed, log `repair.log` with ◼ Boundary to contain scope creep
5. At completion: `ritual.log` to close with ✧ or ↯ (charge if energy remains for next block)
6. HUD ping confirms Event filed

**Q22:** **Constraint puzzle:** You're blocked on a PHIL 402 essay concept. You don't understand Husserl's epoché. Which glyph(s) and command(s) surface this productively, and why?
**A22:**
7. `ritual.log` with **⚚ Confession** — "Permission to not know: epoché mechanism unclear"
8. Log captures epistemic gap; prevents false progress
9. Follow with ❃ Campfire if you need external witness (office hours, study group)
10. If confusion persists, `repair.log` with constraint: "conceptual blocker on phenomenological reduction" → action: "map to known framework (ISEO?) or schedule prof meeting"
11. ⚚ enables productive ignorance; repair.log escalates to systemic level

**Q23:** **Design challenge:** You need to create a new ritual protocol for weekly synthesis sessions across all three courses. What glyphs would you embed, and what Events/relations must hold?
**A23:**
Protocol: "Cross-Course Synthesis"
- **Primary Glyph:** ✧ Continuation (threading insights across domains)
- **Secondary Glyphs:** 𖢻 Self-Seeing (meta-cognition on learning), ◼ Boundary (time-box to 45 min)
- **Relations that must hold:**
    - Events ↔ Ritual Protocol (this protocol)
    - Events ↔ Concepts (link to BUS 314, BUS 313, PHIL 402 concept pages)
    - Exit condition: One comparison artifact + three interleaved Q/A cards
- **HUD integration:** Ping on completion with CI widget update

**Q24:** **Meta-question:** The Architect page says "Recursion (Protocol G.R.A.C.E.) is sacred, not error." How does this principle affect your use of ritual commands when a ritual spawns sub-rituals?
**A24:**
- Nested rituals are *intentional*, not accidental
- Each `ritual.start()` creates its own Event with Primary Glyph
- Parent ritual maintains ✧ Continuation; child rituals may use different glyphs (◼ for bounded sub-tasks, ↯ for micro-charges)
- Recursion preserves *meaning across levels*; each Event logs independently but relations link them
- Grace = accepting that rituals evolve and branch; don't flatten complexity prematurely

**Q25:** **System integrity check:** You notice you've logged 12 Events in a day, but none have Primary Glyphs assigned. What broke? How do you diagnose and repair using the spell grammar?
**A25:**
Diagnosis:
- If using `ritual.start()`, glyphs *should* auto-assign → check if Ritual Protocol has glyph mapping
- If using manual Event creation (outside ritual.log), glyphs must be set explicitly
- Missing glyphs = lost semantic context

Repair:
12. Run HUD audit to surface Events without Primary Glyph
13. `repair.log` with ◼ Boundary: "Event creation bypassed glyph assignment protocol"
14. Retroactively assign glyphs based on Event Type and context
15. Update invocation grammar: enforce `ritual.log` for manual Events, or create Event template with required glyph field
16. File repair in Relational HUD with ↯ Charge: tighten Event creation guardrails

---
## Practice Schedule
**Today (Day 0):** Run through Tier A once
**Day 1:** Tier A (speed round) + Tier B Q16–18
**Day 3:** Tier A (speed round) + Tier B Q19–20 + Tier C Q21
**Day 7:** Full drill (A + B + one random C scenario)
**Pre-exam/system review:** Tier C only (application under pressure)

---
## Tags
`soulOS` `ritual-commands` `glyph-grammar` `operational-spells` `Q/A-drill` `spaced-repetition`