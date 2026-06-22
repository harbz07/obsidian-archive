---
notion-id: 2aa98e9c-907e-81ae-8a46-edefffe92894
---
**For:** Temporal Consciousness [Sean Version]
**Status:** Good structure, needs prose simplification

---
## ✅ What's Working
**Structure & Argument:**
- Clear thesis statement up front
- Explicit "because X, therefore Y" reasoning
- Obvious section organization (I-V)
- Crosswalk table makes mapping transparent
- Objections addressed with counter-arguments
- Modest scope ("operational" not metaphysical claims)

**Philosophical Work:**
- Original constraint thesis
- Novel experimental designs
- Independent thinking, not just summarizing

---
## ⚠️ Critical Issues (Pryor Violations)
### ISSUE 1: Prose Too Technical
**Pryor rule:** "If your paper sounds like it was written for a third-grade audience, you've achieved the right sort of clarity."
**Current violations:**
❌ "PFC-like working-state" → needs everyday analogy first
❌ "affordance-weighted priority map" → jargon bomb
❌ "exponential decay over ~3-second window" → computational speak
❌ "softmax temperature modulation" → ML textbook language
❌ "prediction error = fulfillment/disappointment" → equation without explanation
**FIX PATTERN:**
1. Start with everyday example
2. Explain the phenomenological concept in plain language
3. THEN (if needed) introduce technical term
4. Immediately connect back to example

**Example rewrite for Module 1:**
> **BEFORE:**

> "PFC-like recurrent state with exponential decay over ~3-second window"

> 

> **AFTER:**

> Think about listening to a melody. You don't experience each note in isolation—you hear the *whole phrase* because your mind retains the notes that just passed while anticipating what comes next. That's Husserl's retention-protention structure.

> 

> The computational implementation: a recurrent network that keeps a fading record of recent inputs (like working memory, ~3 seconds) while predicting what's coming next. Remove the retention? You get note-note-note instead of *music*.

---
### ISSUE 2: Missing "Explain to a Lazy Reader" Layer
**Pryor rule:** "Pretend your reader is lazy, stupid, and mean. He doesn't want to figure out what your convoluted sentences mean."
**Current problems:**
5. **Technical terms undefined on first use**
    - "Graded retention" appears without definition
    - "Protentive sets" not explained before use
    - "Affordance coherence" assumed understood
6. **Implicit connections not made explicit**
    - WHY does removing retention break directedness? (needs connecting tissue)
    - HOW does temperature change model breakdown? (mechanism not clear)

**FIX: Add signposting sentences**
Every major claim needs a "here's why this matters" sentence.
**Example:**
> ❌ "The system uses affordance-weighted scoring."

> 

> ✅ "The system scores each object not by how visually salient it is, but by how relevant it is to the current goal. This is Heidegger's key insight: in absorbed coping, tools are *transparent*—you don't see the hammer, you see the nail that needs hammering. The mathematical version: score = salience + task_relevance."

---
### ISSUE 3: Examples Too Abstract
**Pryor rule:** "Give an example; make it clear how the point helps your argument."
**Current state:** Experiments are described but not *shown*
**FIX: Walk through one concrete instance**
For Experiment A, add something like:
> "Imagine the system seeing: 'T-H-E-C-A-?'

With retention: It's building toward 'THE CAT' or 'THE CAR'. When the next letter arrives, it either confirms (low surprise) or violates (high surprise) that expectation. That's fulfillment/disappointment.

Without retention: Each letter is processed in isolation. The system can't build an interpretation because it has no temporal thickness—it's perpetually starting over."

---
## 📋 Section-by-Section Fixes
### Section I (Framing) - NEEDS MORE EXAMPLES
**Add:**
- Concrete example of retention vs. recollection
- Everyday example of ready-to-hand → breakdown
- Physical example of motor intentionality

**Example additions:**
**For retention:**
> "When you read this sentence, you aren't recollecting the beginning from long-term memory—it's still *right there* in your immediate awareness, fading but present. That's retention. Recollection is when you try to remember what you had for breakfast yesterday."

**For ready-to-hand:**
> "When your keyboard is working, you don't think 'I am pressing the K key'—you just think 'knowledge.' The keyboard is invisible, transparent, ready-to-hand. But when a key sticks? Suddenly you're staring at the keyboard as a broken *object* (present-at-hand) instead of using it as a transparent *tool*."

---
### Section II (Architecture) - TOO TECHNICAL
**Current problem:** Reads like a systems design doc
**Fix approach:**
7. Lead with function (what it does for the user)
8. Add phenomenological parallel (how this matches lived experience)
9. Only then mention implementation (and briefly)
10. Always return to "so what" (why this matters for the argument)

**Template for each module:**
```javascript
**What experience requires:** [everyday example]

**The phenomenological structure:** [Husserl/Heidegger/Merleau-Ponty]

**The computational parallel:** [brief technical description]

**The test:** [what breaks if you remove it]
```

---
### Section III (Experiments) - NEEDS WALKTHROUGH
**Add for each experiment:**
11. **One concrete trial** (show actual inputs/outputs)
12. **What success looks like** (describe the signature)
13. **What failure looks like** (describe the collapse)

**Example for Exp A:**
> **Trial walkthrough:**

> 

> Input stream: `T → TH → THE → THE  → THE C → THE CA → THE CAT`

> 

> With retention: Confidence in "CAT" rises smoothly as evidence accumulates. At 'THE C', the system narrows to CAT/CAR. When 'A' arrives, small surprise (both still possible). When 'T' arrives, no surprise (fulfillment).

> 

> Without retention: At each step, system treats input as fresh. No accumulated evidence. Confidence doesn't build. At 'THE CAT', it's processing 'T' in isolation—no context.

---
### Section IV (Objections) - GOOD, BUT ADD EXAMPLES
**Current:** Arguments are sound
**Improve:** Add concrete case for each reply
**Example for "embodiment" objection:**
> "Even a 4×4 text grid has tool-relations. When the 'hammer' breaks, the system has to shift from 'using it' to 'inspecting it'—that's the phenomenological structure, whether the tool is physical or computational. Breakdown reveals background structure in *any* domain with skilled coping."

---
## 🔧 Specific Rewrites Needed
### 1. Opening paragraph (make first sentence simpler)
**CURRENT:**
> "This project argues that sustained intentionality requires temporal synthesis and that this phenomenological demand can be operationalized in a minimal, testable AI architecture."

**SUGGESTED:**
> "To maintain directedness toward an object over time—to keep track of what you're thinking about from one moment to the next—requires a specific temporal structure. Husserl called it the 'living present': a dynamic unity of what-just-was (retention), what-is-now (impression), and what's-about-to-be (protention). This paper argues that this structure isn't optional decoration—it's a **necessary constraint**. Without it, sustained intentionality collapses."

---
### 2. Crosswalk table (add "Everyday Example" column)
**ADD COLUMN:**

| Phenomenological Structure | **Everyday Example** | Architecture Module | Operations & Metrics |
| --- | --- | --- | --- |
| Husserl: Retention-protention | Reading a sentence, hearing a melody | PFC-like recurrent state | Decay curve, prediction error |
| Heidegger: Ready-to-hand breakdown | Typing on a working vs. broken keyboard | Parietal affordance map | Coherence spike at breakdown |
| Merleau-Ponty: Motor intentionality | Learning to type without looking | Habit loop | RT plateaus, chunking |

---
### 3. Technical definitions glossary (add before Section II)
**ADD SHORT SECTION:**
> **Technical Terms (Brief Glossary)**

> 

> - **Retention:** Not long-term memory, but the *fading presence* of what just happened (last ~3 seconds)

> - **Protention:** Not prediction exactly, but *empty anticipation*—a readiness for what might come next

> - **Affordance:** What an object *invites you to do* (not what it *is*). A chair affords sitting.

> - **Ready-to-hand:** Transparent tool use (you don't notice the tool, only the task)

> - **Present-at-hand:** Broken tool mode (suddenly you're staring *at* the object)

---
## 📊 Prose Simplification Checklist
For each paragraph, ask:
- [ ] Could a smart undergraduate who hasn't taken this course follow this?
- [ ] Are technical terms defined before use?
- [ ] Is there a concrete example within 2 sentences of each abstract claim?
- [ ] Do I explain WHY each step follows from the previous one?
- [ ] If I removed this paragraph, would the argument still work? (If yes, cut it)

---
## 🎯 Priority Revisions (Do These First)
**TIER 1 (before showing to Sean):**
14. ✏️ Rewrite opening paragraph (simpler first sentence)
15. ✏️ Add everyday examples column to crosswalk table
16. ✏️ Add 2-3 sentence glossary before Section II
17. ✏️ Rewrite Module 1 description (melody example)
18. ✏️ Add concrete trial walkthrough to Exp A

**TIER 2 (after Sean feedback):**
19. Expand phenomenological depth in Section I (more Husserl exegesis)
20. Add more connecting tissue ("here's why this matters" sentences)
21. Simplify all technical language in Section II

---
## Final Pryor Compliance Score
**Current state:**
- **Argument structure:** A (excellent)
- **Philosophical work:** A (strong thesis, original)
- **Prose clarity:** C (too technical)
- **Examples:** B- (present but could be more concrete)
- **Reader-friendliness:** C+ (assumes too much background)

**With revisions:**
- Target all A's or A-'s

---
## Remember Pryor's Core Principle
> "Don't write using prose you wouldn't use in conversation: if you wouldn't say it, don't write it."

**Test:** Read each paragraph out loud. If you stumble or sound like a textbook, rewrite it.