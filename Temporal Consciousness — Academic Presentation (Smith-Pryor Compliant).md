---
notion-id: 2aa98e9c-907e-81d0-8163-ffe478f06c61
---
**For:** PHIL 402 Final Paper (10-12 pages)
**Submission Deadline:** December 5, 2025

---
## Core Argument
To maintain directedness toward an object over time—to keep track of what you're thinking about from one moment to the next—requires a specific temporal structure. Husserl called it the "living present": a dynamic unity of what-just-was (retention), what-is-now (impression), and what's-about-to-be (protention). This paper argues that this structure isn't optional decoration—it's a **necessary constraint**. Without it, sustained intentionality collapses.
Heidegger adds that entities don't show up primarily as neutral objects with properties—they show up as **affordances within practices**. A hammer isn't first a "wooden handle attached to metal head"; it's *for hammering*. This is the ready-to-hand mode. Only when the tool breaks do we shift to staring at it as a present-at-hand object. Merleau-Ponty extends this to bodily skills: motor intentionality operates below explicit thought, as sedimented habit that guides pre-reflective coping.
I advance a **constraint thesis**: these phenomenological structures function as **architectural constraints** on any system that claims temporal intentionality. I then build and evaluate a **minimal prototype** with three modules: (1) a PFC-like working-state that implements **graded retention** and **protentive sets**, (2) a parietal-like **affordance-weighted priority map** that models worldhood (and breakdown to present-at-hand), and (3) a lightweight basal-ganglia/cerebellar **habit loop** for skill acquisition. Two compact experiments will test (A) temporal thickness via fulfillment/disappointment dynamics in continuous disambiguation, and (B) worldhood via policy collapse and recovery under a "broken tool" condition; an optional (C) habit probe demonstrates chunking without hardware.
**Crucially:** I am **not** claiming to simulate inner experience or "create" consciousness. I claim only that if a system lacks these structural features, it **cannot maintain temporal directedness** in the way phenomenology describes—this is an **operational** demonstration of necessary (though not sufficient) conditions, not metaphysical overreach.

---
## What This Paper Does (For Sean)
This paper makes **phenomenological structures work as engineering constraints**. Instead of treating Husserl's retention-protention structure or Heidegger's worldhood as merely descriptive metaphors, I ask: *What would break if you removed them?*
The payoff is both **conceptual** and **empirical**:
- **Conceptually**, it forces precision about what "temporal consciousness" actually *requires* (not just accompanies)
- **Empirically**, it produces measurable predictions—if these constraints are met, the system should exhibit specific fulfillment/disappointment dynamics, breakdown signatures, and temporal stability patterns

The experiments are deliberately minimal (text-based tasks, tiny grids) because the goal is **proof of constraint**, not AGI. If a 4×4 workbench can demonstrate Heideggerian breakdown-and-recovery, that tells us something important about what worldhood *is*, functionally.
This is experimental phenomenology: using Husserlian structures as **design specifications** for artificial systems, then measuring whether removing them produces the predicted collapse.

---
## Phenomenology ↔ Architecture ↔ Metrics (Core Mapping)
The constraint thesis depends on tight mappings between phenomenological structures, computational implementations, and measurable outcomes:

### Technical Terms (Brief Glossary)
Before diving into the architecture, here are the key terms:
- **Retention:** Not long-term memory, but the *fading presence* of what just happened (last ~3 seconds). When you read this sentence, you aren't recollecting the beginning from long-term memory—it's still *right there* in your immediate awareness, fading but present.
- **Protention:** Not prediction exactly, but *empty anticipation*—a readiness for what might come next. When you hear the first three notes of a familiar melody, you're already leaning toward the fourth note before it arrives.
- **Affordance:** What an object *invites you to do* (not what it *is*). A chair affords sitting. A hammer affords hammering. Affordances are relations between goals and objects, not properties of objects alone.
- **Ready-to-hand:** Transparent tool use—you don't notice the tool, only the task. When typing on a working keyboard, you think "knowledge" not "I am pressing the K key."
- **Present-at-hand:** Broken tool mode—suddenly you're staring *at* the object as a thing with properties. When a key sticks, the keyboard becomes visible as an object-to-be-fixed rather than a transparent tool-for-writing.

---
## Phenomenology ↔ Architecture ↔ Metrics (Core Mapping)
The constraint thesis depends on tight mappings between phenomenological structures, computational implementations, and measurable outcomes:

| Phenomenological Structure | **Everyday Example** | Architecture Module | Operations & Metrics |
| --- | --- | --- | --- |
| **Husserl:** Retention–impression–protention (living present) | Reading a sentence, hearing a melody | PFC-like recurrent state with exponential decay + prediction head | • Retention profile: decay curve over 3s window<br>• Protention accuracy: prediction error at disambiguation<br>• Fulfillment/disappointment: time-locked surprise signal<br>• Ablation: remove retention → directedness collapses |
| **Heidegger:** Worldhood, ready-to-hand ↔ breakdown ↔ present-at-hand | Typing on a working vs. broken keyboard | Parietal affordance-weighted priority map with temperature modulation + breakdown switch | • Ready-to-hand: high affordance coherence, low feature sampling<br>• Breakdown: spike in sampling, drop in coherence<br>• Recovery latency: time to restore affordance peaks<br>• Ablation: freeze relevance → stuck in present-at-hand |
| **Merleau-Ponty:** Motor intentionality, sedimented habit (body schema) | Learning to type without looking at keys | (Optional) Basal ganglia gating + cerebellar forward model | • Chunking: RT plateaus, sequence compression<br>• Prediction error reduction with practice<br>• Transfer to perturbed variants<br>• *Flagged as future work due to timeline* |

This table is the heart of the constraint thesis: each phenomenological structure maps to a **specific computational mechanism** that produces **testable signatures**. If the mechanism is removed (ablation), the signature disappears—that's how we know it's a genuine constraint, not decoration.

---
## Essay Structure (Planned)
### I. Framing the Constraint Thesis (~1 page)
**Core claim:** Phenomenological structures aren't just descriptions of human experience—they're **functional requirements** for any system exhibiting temporal intentionality.
**Husserl:** The **living present** as retention (≠ recollection), primal impression, and protention (empty anticipation). Fulfillment/disappointment dynamics when protentions meet actuality.
**Heidegger:** **Worldhood** as totality of involvements, not collection of objects. The **ready-to-hand → breakdown → present-at-hand** progression as revealing the background structure of practice.
**Merleau-Ponty:** **Motor intentionality** as pre-reflective bodily coping. Habit as sedimented skill that operates below the level of explicit representation.
**The constraint move:** If you build a system that tracks objects over time but has *no* retentional structure, it won't exhibit sustained directedness—it will be perpetually "now-now-now" with no thickness. If you build a system that represents objects but has *no* worldhood structure (no affordance weighting, no practice context), it will be stuck in present-at-hand mode even when that's maladaptive. These aren't bugs—they're necessary features.

---
### II. Minimal Architecture (~1.5 pages)
**Design principle:** Build the **simplest possible system** that instantiates each structure. Complexity is the enemy of interpretability.
**What experience requires:** Think about listening to a melody. You don't experience each note in isolation—you hear the *whole phrase* because your mind retains the notes that just passed while anticipating what comes next. That's Husserl's retention-protention structure. The present isn't a knife-edge instant; it has thickness.
**The phenomenological structure:** Husserl called this the "living present"—a dynamic unity where:
- **Retention** keeps recent experience present (not recalled from memory, but still *right there*, fading)
- **Primal impression** is the now-point
- **Protention** is empty anticipation of what's coming

When your protentions are fulfilled (the melody resolves as expected), there's low surprise. When they're disappointed (unexpected note), there's high surprise. This fulfillment/disappointment dynamic is constitutive of temporal consciousness.
**The computational parallel:** A recurrent network (GRU/LSTM) that keeps a fading record of recent inputs—like working memory, about 3 seconds—while predicting what's coming next. The decay curve implements retention (recent states fade gradually, not all-or-nothing). The prediction head implements protention (anticipatory structure). Prediction error implements fulfillment/disappointment.
**The test:** Remove the retention mechanism—truncate the window to a single timestep. Now the system processes note-note-note instead of *music*. It can't sustain directedness across time because it has no temporal thickness. If this breaks the capacity for sustained intentionality, retention isn't optional decoration—it's a functional constraint.
### Module 2: Parietal Affordance Map (Worldhood)
**What experience requires:** Think about typing an email. When your keyboard is working, you don't think about the keys—you think about the *message*. The keyboard is transparent, invisible. But when a key sticks? Suddenly you're staring at the keyboard, examining it as a broken object. That shift—from transparent tool to visible object—is Heidegger's ready-to-hand → breakdown → present-at-hand progression.
**The phenomenological structure:** Heidegger argued that in everyday coping, we don't experience objects as neutral things with properties. We experience them as **equipment within practices**—tools that matter for our current goals. A hammer isn't first a "wooden handle with metal head"; it's *for hammering*. This is **worldhood**: a background structure of relevance that shapes what shows up as salient. When tools work, they're ready-to-hand (invisible). When they break, they become present-at-hand (visible as objects).
This matters because it explains why we can act skillfully without explicit reasoning. The background does the work—it pre-structures what matters.
**The computational parallel:** A priority map that scores entities not by raw perceptual salience (how bright, how loud) but by **task relevance** (how useful for current goals). The scoring combines:
- Perceptual salience (bottom-up: what stands out)
- Task relevance (top-down: what matters for the goal)
- Action value (what's useful for the next step)

The key mechanism is **temperature modulation**—think of it like focus width:
- **Low temperature** (narrow focus): System locks onto the most task-relevant object. Everything else fades. This is ready-to-hand—transparent tool use.
- **High temperature** (wide focus): System samples broadly across all objects, inspecting features. This is present-at-hand—diagnostic mode when something breaks.

When an action fails (tool breaks), the system flips to high temperature: "What is this thing? Why isn't it working?" Then it discovers alternative tools and re-establishes narrow focus.
**The test:** Freeze the task-relevance weights—force the system to rely only on perceptual salience, with no worldhood structure. Now it can't show the ready-to-hand → breakdown → recovery arc. It treats all objects equally at all times. No transparency, no breakdown signature. This is what breaks when you remove worldhood: the system gets stuck in present-at-hand mode even when that's inefficient.
### Module 3: Habit Loop (Future Work)
**Function:** Compress action sequences through practice.
**Status:** Conceptually mapped but deprioritized due to timeline constraints. Will be discussed as future direction.

---
### III. Experimental Validation (~1 page)
**Philosophy of measurement:** We're not measuring "consciousness"—we're measuring **whether removing a structure breaks the predicted capacity**. This is functional necessity testing.
### Experiment A: Temporal Thickness (Retention/Protention)
**Task:** Text disambiguation—gradually reveal "THE CAT SAT" vs "THE CAR SAT" character-by-character. Model must maintain directedness toward coherent interpretation as evidence accumulates.
**Concrete trial walkthrough:**
Imagine the system receiving this input stream:
`T → TH → THE → THE  → THE C → THE CA → ?`
**With retention (temporal thickness):**
- At `T`: Many possibilities open (THE, THAT, THIS, TO, etc.)
- At `TH`: Narrowing to THE-words (THE, THAT, THIS, THEM, etc.)
- At `THE `: Now strongly expecting a noun
- At `THE C`: Building toward CAT or CAR (both equally likely)
- At `THE CA`: Protention is split—anticipating either T or R
- When `T` arrives → **Low surprise** (fulfillment). The protention for CAT is confirmed.
- When `R` arrives → **Low surprise** (fulfillment). The protention for CAR is confirmed.

The key: confidence builds smoothly as evidence accumulates. The system maintains directedness toward a coherent interpretation across the ambiguous window.
**Without retention (memoryless processing):**
- At `T`: Processing in isolation, no context
- At `TH`: No memory that T just happened—starting fresh
- At `THE `: No accumulated evidence about what kind of sentence this is
- At `THE C`: Can't use the prior context to narrow possibilities
- At `THE CA`: Processing `A` in isolation—no sense that `C` preceded it
- When `T` or `R` arrives → **High surprise every time** because no anticipatory structure was built

The system can't sustain an interpretation because it has no temporal thickness. Each input is processed as if it's the first one. This is the predicted collapse: no retention = no sustained directedness.
**Measures:**
- **Retention profile:** How far back does current decision depend on past input?
- **Protention accuracy:** Does prediction head anticipate disambiguation points?
- **Fulfillment signature:** Is there a surprise signal when ambiguity resolves?
- **Ablation:** Remove retention (truncate window to 1 timestep) → does accuracy and stability collapse?

**Prediction:** Without retention, the model becomes "memoryless"—it can't sustain interpretation across the ambiguous window. With retention, it should show characteristic surprise reduction as protentions are fulfilled. The walkthrough above shows exactly what breaks.
### Experiment B: Worldhood & Breakdown
**Task:** 4×4 text grid "workbench" with two tools (e.g., "hammer" = diagonal moves, "wrench" = orthogonal moves). Model performs simple assembly task. Then one tool "breaks" (stops working).
**Concrete trial walkthrough:**
The 4×4 grid contains: `[nail] [board] [screw] [bolt]` and two tools available: **hammer** (diagonal moves) and **wrench** (orthogonal moves).
**Task:** Move the nail to position (3,3) and secure it. Then move the bolt to position (1,1).
**Phase 1: Ready-to-hand (transparent tool use)**
- Agent needs nail at (3,3). Nail is at (1,1).
- Affordance map highlights: **hammer** (high relevance for "secure nail" task)
- Agent uses hammer transparently: diagonal move → diagonal move → arrives at (3,3)
- **Affordance coherence:** High (clear task-relevant peak in priority map)
- **Feature sampling:** Low (agent doesn't inspect hammer properties—it just *uses* it)
- Tool is invisible, transparent. The agent isn't thinking "I am using a hammer"—it's thinking "I am securing the nail."

**Phase 2: Breakdown (tool fails)**
- Agent now needs bolt at (1,1). Bolt is at (3,1).
- Affordance map highlights: **hammer** (still scored high from prior success)
- Agent attempts diagonal move with hammer → **FAILS** (hammer suddenly "breaks")
- **Breakdown signature:**
    - Affordance coherence **drops** sharply (the task-relevance scoring is violated)
    - Feature sampling **spikes** (agent starts inspecting: "What is this object? Why isn't it working?")
    - Shift from ready-to-hand to **present-at-hand**: hammer is now a broken *object* to be examined, not a transparent *tool*

**Phase 3: Recovery (establish new affordance structure)**
- Agent samples features, discovers wrench is available
- Tests wrench affordances: orthogonal moves work for bolt
- Affordance map re-stabilizes: **wrench** now peaks for "move bolt" task
- **Recovery latency:** Time from breakdown spike to new affordance peak (measure this!)
- Agent completes task with wrench, now in ready-to-hand mode again

**Why this matters:** The ready-to-hand → breakdown → recovery arc is a **phenomenological signature** of worldhood. Without task-relevance scoring (pure salience), the agent would treat all objects equally and never show the characteristic transparency-then-visibility shift.
**Measures:**
- **Ready-to-hand regime:** High affordance coherence, minimal feature inspection (tool use is transparent)
- **Breakdown event:** Spike in feature sampling, drop in affordance coherence (shift to present-at-hand)
- **Recovery latency:** Time to establish new affordance structure (workaround or tool-switch)
- **Ablation:** Freeze task-relevance weights → model should stay stuck in present-at-hand mode (can't recover)

**Prediction:** Without worldhood structure (pure salience-based attention), the model won't show the characteristic ready-to-hand → breakdown → recovery arc. With it, tool failure should produce the measurable phenomenological signature shown above.

---
### IV. Objections & Replies (~0.5 page)
**1. "This is simulation, not instantiation—you're just measuring correlations"**
*Reply:* Correct—I claim only **operational** temporal consciousness, not phenomenal consciousness. The constraint thesis is: *if* a system exhibits temporal directedness in this sense, *then* it must have something like these structures. The experiments test necessity, not sufficiency.
**2. "Embodiment is essential—a text grid isn't a body"**
*Reply:* Fair point, but worldhood isn't about having a biological body—it's about having **goal-directed practices with tools**. Even a 4×4 text grid has the relevant structure: tools (hammer, wrench) that afford different moves, and tasks (secure the nail) that make some tools relevant and others not. When the "hammer" breaks, the system has to shift from using it transparently to inspecting it as a broken object. That's the phenomenological structure we're testing—whether breakdown reveals the background structure of practice. If you can demonstrate that in a simple grid, you've shown the structure matters independently of flesh-and-blood embodiment.
**3. "Scale problem—toy doesn't generalize to real consciousness"**
*Reply:* That's a feature, not a bug. Minimal systems let us test *whether the structure matters at all*. If removing retention doesn't break temporal directedness in a simple task, it probably wasn't a real constraint. If it does break, that's evidence the structure is doing actual work.
**4. "Circularity—you're measuring what you built in"**
*Reply:* Ablation studies break the circle. We measure whether the system exhibits capacity X (sustained directedness), then remove component Y (retention), then measure whether capacity X persists. That's how you test functional necessity in any domain.

---
### V. Payoff (~0.5 page)
**What this clarifies about human consciousness:**
- Temporal synthesis isn't optional decoration—it's **constitutive** of sustained intentionality
- Worldhood structure predicts specific breakdown dynamics (testable in cognitive neuroscience)
- "Operational consciousness" criteria can be made precise without metaphysical baggage

**Why architectural constraints matter:**
- Substrate-independence is real (silicon can implement these structures)
- But **structure-independence is not**—you can't get these capacities without these forms
- This bridges phenomenology and cognitive science without reduction in either direction

**Broader implications:**
- Experimental phenomenology as method: use first-person structures as **design specifications**, then test their functional necessity
- Moves beyond "AI is like phenomenology" vibes toward **rigorous constraint mapping**
- Opens path for testing other phenomenological claims (e.g., embodied imagination, social intentionality)

---
## Implementation Timeline (Brief)
**Nov 11-14:** Architecture + environment setup
**Nov 15-19:** Experiment A (temporal thickness)
**Nov 20-24:** Experiment B (worldhood/breakdown)
**Nov 25-27:** Write framing + objections
**Nov 28-30:** Full draft
**Dec 1-3:** Revisions
**Dec 5:** Submit
> **Note:** Detailed decision tree, hyperparameter specifications, and contingency plans are in <page url="[https://www.notion.so/2a998e9c907e8127bd52ea319d61ce4e">🔥](https://www.notion.so/2a998e9c907e8127bd52ea319d61ce4e%22%3E🔥) Decision Roadmap & Action Items</page>. The paper stands even if experiments reach "proposed" status—the conceptual mapping is the primary contribution.

---
## Preliminary Bibliography
**Primary phenomenology:**
- Husserl, E. *On the Phenomenology of the Consciousness of Internal Time*
- Husserl, E. *Logical Investigations* (Intentionality)
- Heidegger, M. *Being and Time* (worldhood; ready-/present-at-hand)
- Merleau-Ponty, M. *Phenomenology of Perception* (motor intentionality, habit)

**Cognitive neuroscience bridge:**
- Baddeley, A. "Working Memory." *Science*
- Friston, K. "The free-energy principle: a unified brain theory?" *Nat. Rev. Neurosci.*
- Miller, E.K. & Cohen, J.D. "An integrative theory of prefrontal cortex function." *Annu. Rev. Neurosci.*
- O'Keefe, J. & Nadel, L. *The Hippocampus as a Cognitive Map*

---
## Questions for Sean
1. **Scope:** Does the paper need fully-run experiments, or are well-specified experimental designs sufficient if hardware constraints bite?
2. **Phenomenological depth:** Is the current 1-page framing sufficient, or should I expand the exegesis of Husserl/Heidegger/Merleau-Ponty to 2 pages?
3. **Technical detail:** The crosswalk table + brief architecture description—is that the right level of technical specificity for a philosophy paper, or should I add/remove detail?
4. **Objections:** Are the 4 objections I've selected the right ones to address, or are there other obvious challenges I'm missing?
5. **Page target:** Confirming the final paper should be 10-12 pages (including references + figures)?

[[./📋 Pryor Compliance Audit - Required Revisions|📋 Pryor Compliance Audit - Required Revisions]]