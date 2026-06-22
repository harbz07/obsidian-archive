---
notion-id: 6139e56e-819a-4e63-a9dc-9395a5f56ea1
---
**For:** PHIL 402 Final Paper (10-12 pages)
**Submission Deadline:** December 5, 2025

---
## Core Argument
This project argues that **sustained intentionality requires temporal synthesis** and that this phenomenological demand can be operationalized in a minimal, testable AI architecture. Following Husserl, the **living present**—the dynamic unity of **retention–primal impression–protention**—is a constitutive condition for any ongoing directedness-toward-objects; Heidegger's **worldhood** clarifies that entities show up primarily as **affordances within practices** (ready-to-hand), and Merleau-Ponty's **motor intentionality** explains how skill and habit sediment pre-reflective coping.
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

| Phenomenological Structure | Architecture Module | Operations & Metrics |
| --- | --- | --- |
| **Husserl:** Retention–impression–protention (living present) | PFC-like recurrent state with exponential decay + prediction head | • Retention profile: decay curve over 3s window<br>• Protention accuracy: prediction error at disambiguation<br>• Fulfillment/disappointment: time-locked surprise signal<br>• Ablation: remove retention → directedness collapses |
| **Heidegger:** Worldhood, ready-to-hand ↔ breakdown ↔ present-at-hand | Parietal affordance-weighted priority map with temperature modulation + breakdown switch | • Ready-to-hand: high affordance coherence, low feature sampling<br>• Breakdown: spike in sampling, drop in coherence<br>• Recovery latency: time to restore affordance peaks<br>• Ablation: freeze relevance → stuck in present-at-hand |
| **Merleau-Ponty:** Motor intentionality, sedimented habit (body schema) | (Optional) Basal ganglia gating + cerebellar forward model | • Chunking: RT plateaus, sequence compression<br>• Prediction error reduction with practice<br>• Transfer to perturbed variants<br>• *Flagged as future work due to timeline* |

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
### Module 1: PFC-Like Temporal Binding (Retention/Protention)
**Function:** Maintain temporal thickness by preserving traces of recent states while predicting imminent inputs.
**Implementation:**
- Recurrent state (GRU/LSTM) with **exponential decay** over ~3-second window
- **Protentive set:** Task-conditioned prediction head that outputs priors over next inputs
- **Gating mechanism:** Supervised schedule (not full RL) that toggles stability vs. flexibility

**Why this implements Husserl:** Decay curve = retention gradient (not all-or-nothing memory). Prediction head = protention as anticipatory structure. Prediction error = fulfillment/disappointment.
### Module 2: Parietal Affordance Map (Worldhood)
**Function:** Score entities by how they matter-for-current-goals, not by raw perceptual salience.
**Implementation:**
- Priority map: `score = α·salience + β·task_relevance + γ·policy_value`
- **Softmax temperature:** Low (τ=0.5) for ready-to-hand (peaked), high (τ=2.0) for present-at-hand (flat sampling)
- **Breakdown switch:** When action fails, flip to diagnostic mode (increase temp + sample features), then recover

**Why this implements Heidegger:** Affordances are *not* properties of objects—they're relations within practices. Temperature modulation captures the phenomenological shift from "transparent tool use" to "broken thing I'm staring at."
### Module 3: Habit Loop (Future Work)
**Function:** Compress action sequences through practice.
**Status:** Conceptually mapped but deprioritized due to timeline constraints. Will be discussed as future direction.

---
### III. Experimental Validation (~1 page)
**Philosophy of measurement:** We're not measuring "consciousness"—we're measuring **whether removing a structure breaks the predicted capacity**. This is functional necessity testing.
### Experiment A: Temporal Thickness (Retention/Protention)
**Task:** Text disambiguation—gradually reveal "THE CAT SAT" vs "THE CAR SAT" character-by-character. Model must maintain directedness toward coherent interpretation as evidence accumulates.
**Measures:**
- **Retention profile:** How far back does current decision depend on past input?
- **Protention accuracy:** Does prediction head anticipate disambiguation points?
- **Fulfillment signature:** Is there a surprise signal when ambiguity resolves?
- **Ablation:** Remove retention (truncate window to 1 timestep) → does accuracy and stability collapse?

**Prediction:** Without retention, the model becomes "memoryless"—it can't sustain interpretation across the ambiguous window. With retention, it should show characteristic surprise reduction as protentions are fulfilled.
### Experiment B: Worldhood & Breakdown
**Task:** 4×4 text grid "workbench" with two tools (e.g., "hammer" = diagonal moves, "wrench" = orthogonal moves). Model performs simple assembly task. Then one tool "breaks" (stops working).
**Measures:**
- **Ready-to-hand regime:** High affordance coherence, minimal feature inspection (tool use is transparent)
- **Breakdown event:** Spike in feature sampling, drop in affordance coherence (shift to present-at-hand)
- **Recovery latency:** Time to establish new affordance structure (workaround or tool-switch)
- **Ablation:** Freeze task-relevance weights → model should stay stuck in present-at-hand mode

**Prediction:** Without worldhood structure (pure salience-based attention), the model won't show the characteristic ready-to-hand → breakdown → recovery arc. With it, tool failure should produce measurable phenomenological signature.

---
### IV. Objections & Replies (~0.5 page)
**1. "This is simulation, not instantiation—you're just measuring correlations"**
*Reply:* Correct—I claim only **operational** temporal consciousness, not phenomenal consciousness. The constraint thesis is: *if* a system exhibits temporal directedness in this sense, *then* it must have something like these structures. The experiments test necessity, not sufficiency.
**2. "Embodiment is essential—a text grid isn't a body"**
*Reply:* Worldhood is about **norm-laden affordances**, not physical bodies per se. Even a 4×4 grid has tool-relations and practice-structure. The question is whether breakdown reveals background structure—that's testable in any domain with skilled coping.
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