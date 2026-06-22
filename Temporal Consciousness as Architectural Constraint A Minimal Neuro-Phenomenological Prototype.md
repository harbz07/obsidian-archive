---
notion-id: 2a798e9c-907e-80c5-b262-cc7671ed8eee
---
## 🚨 CRITICAL PATH ALERT (Added Nov 11, 2025)
> **STATUS:** 23 days to submission (Dec 5). Hardware constraints + 3-experiment scope = high risk of scope creep.

> 

> **DOCUMENT UPDATES (Nov 11):**

> - ✅ Added comprehensive **Pre-Submission Decision Roadmap** (see bottom) with 4-tier dependency structure

> - ✅ **Timeline revised** with 2-day buffer (peer-ready by Nov 26, not Nov 28)

> - ✅ **Hyperparameters specified** in Sec II (concrete values vs ranges)

> - ✅ **Method decisions flagged** in Sec III (task choices, metrics, thresholds)

> - ✅ **Implementation section updated** with library recommendations and coding time estimates

> - ✅ **Objections section expanded** with additional objection options (need to select 3-4)

> 

> **IMMEDIATE BLOCKING DECISIONS (Next 48 hours → Roadmap Tier 1):**

> 1. **Hardware audit:** What machine are you coding on? (Specs determine dataset size, model complexity, iteration speed)

> 2. **Exp C triage:** DROP IT. Two excellent experiments > three rushed ones. Mention habit chunking as "future work" (1 sentence).

> 3. **Exp A choice:** Text disambiguation (fastest to implement, phenomenologically valid)

> 4. **Exp B scope:** 4×4 grid, 2 tools, sudden failure (minimal viable worldhood demo)

> 

> **WHY THIS MATTERS:** If Tier 1 decisions slip past Nov 12, entire implementation timeline cascades into finals week. See roadmap for full dependency cascade.

> 

> **SCROLL TO BOTTOM FOR COMPLETE DECISION ROADMAP 👇**

---
## Opening paragraph
This project argues that **sustained intentionality requires temporal synthesis** and that this phenomenological demand can be operationalized in a minimal, testable AI architecture by semester’s end. Following Husserl, the **living present**—the dynamic unity of **retention–primal impression–protention**—is a constitutive condition for any ongoing directedness-toward-objects; Heidegger’s **worldhood** clarifies that entities show up primarily as **affordances within practices** (ready-to-hand), and Merleau-Ponty’s **motor intentionality** explains how skill and habit sediment pre-reflective coping. I advance a **constraint thesis**: these phenomenological structures function as **architectural constraints** on any system that claims temporal intentionality. I then build and evaluate a **minimal prototype** with three modules: (1) a PFC-like working-state that implements **graded retention** and **protentive sets**, (2) a parietal-like **affordance-weighted priority map** that models worldhood (and breakdown to present-at-hand), and (3) a lightweight basal-ganglia/cerebellar **habit loop** for skill acquisition. Two compact experiments will test (A) temporal thickness via fulfillment/disappointment dynamics in continuous disambiguation, and (B) worldhood via policy collapse and recovery under a “broken tool” condition; an optional (C) habit probe demonstrates chunking without hardware. The payoff is conceptual and empirical: if these constraints are met, the system exhibits **operational temporal consciousness** in precisely the sense phenomenology demands—no metaphysical overreach, just capacities measured.

---
## Essay plan
### I. Framing (~1 page)
- Clarify **constraint thesis** (phenomenological structure → architectural requirement).
- Husserl: **living present** (retention ≠ recollection; protention as empty anticipation; fulfillment/disappointment).
- Heidegger: **worldhood** as totality of involvements; **ready-to-hand → breakdown → present-at-hand**.
- Merleau-Ponty: **motor intentionality** and habit (pre-reflective coping).

### II. Minimal architecture (1–1.5 pages)
**🚨 HYPERPARAMETER DECISIONS (Tier 2 - by Nov 17):** See Development Implementation section for concrete values.
**PFC module (retention/protention):**
- Recurrent state with **exponential decay** (retentional traces) over a ~~1–5s window~~ **3-second window** (locked per roadmap)
    - *Decision locked: 3s window ≈ 12 timesteps at 250ms granularity*
    - Decay rate λ: **0.3** (gives ~37% retention at 3s)
    - Implementation: GRU hidden state × exp(-λΔt) mask
- **Protentive set** = task-conditioned prediction head producing priors over imminent inputs
    - Architecture: Linear layer on GRU hidden → softmax over next-token vocab
    - Loss function: **Cross-entropy** (not KL divergence - cleaner for discrete tokens)
    - Measures fulfillment (low prediction error) vs disappointment (high prediction error)
- **D1-style "gating"**: ~~RL-controlled gate toggles stabilization vs flexibility~~ **Supervised schedule** (simpler)
    - Gate value: High (0.9) during ambiguous phase, low (0.1) during clear phase
    - Controls recurrent gain: `h[t] = gate * h[t-1] + (1-gate) * new_input`
    - *Defer RL version to "future work" unless time permits*

**Parietal module (worldhood):**
- **Affordance-weighted priority map**: Score each object/feature by bottom-up salience + top-down task relevance + policy value
    - Formula: `score[i] = α·salience[i] + β·relevance[i] + γ·value[i]`
    - **Initial weights:** α=β=γ=0.33 (equal, tune if needed)
    - *Decision needed: Will you do hyperparameter search or stick with defaults?*
- **Attractor dynamics**: Softmax temperature sets competition level (models "attentional gravity")
    - **Ready-to-hand:** τ=0.5 (sharp affordance peaks, fluent tool use)
    - **Present-at-hand:** τ=2.0 (flat distribution, deliberate inspection)
    - Temperature schedule: Normal → Spike at breakdown → Anneal back during recovery
    - *Optional: Add attractor update rule *`*scores += η·∇scores*`* with η=0.1 (skip if converges naturally)*
- **Breakdown switch**: When an action fails, flip to **diagnostic sampling** (present-at-hand) then recover
    - Trigger: Action fails twice in a row
    - Effect: Set τ=2.0, increase feature sampling rate (broader attention)
    - Recovery: Return to τ=0.5 when new policy stabilizes (e.g., 5 consecutive successful actions)
    - *Decision needed: Gradual temperature annealing or step function?*

**Habit loop (RECOMMEND DROPPING - mention as future work):**
- **BG "gate & chunk"**: ~~Simple Q-learning that compacts action sequences~~
    - *If dropped: "Future work could extend this architecture with basal-ganglia loops for habit formation, demonstrating how motor intentionality sediments through repeated practice (Merleau-Ponty's 'body schema'). Preliminary designs include Q-learning over action chunks and cerebellar forward models for error reduction."*
- **Cerebellar forward model**: ~~1-step predictor to reduce error with delayed feedback~~
    - *If kept: Would require additional 2-3 days of implementation + separate evaluation metrics*

### III. Methods & evaluation (1 page)
**🚨 DECISION FLAGS (see Roadmap Tier 2):**
- **Task choice for Exp A:** Text disambiguation vs moving dot vs syllables
- **Retention window:** Concrete value needed (suggest 3s)
- **Statistical power:** How many runs per condition?
- **Baseline specification:** What counts as null model?

**Experiment A — Temporal thickness (REQUIRED):**
- **Task:** Continuous ambiguous stream ~~(e.g., moving-dot or noisy syllable classification; textual "gradually disambiguated" sequences also fine)~~
    - **📌 RECOMMENDATION:** Text disambiguation task (fastest to implement, phenomenologically valid)
    - Example: Gradually revealed phrase with ambiguous prefix ("T..h..i..s.. ..i..s..")
    - Retention window: **3 seconds** (maps to working memory literature, interpretable)
    - Timestep granularity: **250ms** (12 steps per window)
- **Measures:**
    - **Retention profile:** Decay curve of state influence across the last N steps
        - *Decision needed: N = 12 steps (3s) or adjust?*
    - **Protention accuracy:** ~~KL between predicted and realized next-step distributions~~ **Cross-entropy** (more standard)
        - *Decision needed: Threshold for "good" protention?*
    - **Fulfillment/disappointment signature:** Prediction-error time-locking when the ambiguity resolves
        - *Decision needed: How to define "disambiguation moment" operationally?*
    - **Ablation:** Remove retention (truncate window) → show collapse in sustained directedness
        - *Decision needed: What % accuracy drop = "collapse"? (Suggest: >15%)*
- **Statistical design:**
    - Runs per condition: **Minimum 10, ideally 30** (depends on hardware)
    - Tests: Paired t-test (ablation), bootstrap 95% CIs (key metrics)

**Experiment B — Worldhood & breakdown:**
- **Task:** ~~Tiny text-grid "workbench" with two tools; one surreptitiously "breaks"~~
    - **📌 MINIMAL SPEC:** 4×4 text grid, 2 tools (e.g., hammer/saw or write/erase), sudden failure at predetermined step
    - Target: Achieve specific grid pattern using tools
    - Breakdown: Tool 1 fails at step 15 (or after X successful uses)
    - *Decision needed: Gradual degradation or sudden failure?* (Recommend sudden for clear signature)
- **Measures:**
    - **Ready-to-hand regime:** High affordance-peak coherence (score >0.8), low feature sampling rate
        - *Decision needed: Quantitative thresholds for "high coherence"?*
    - **Breakdown event:** Spike in feature sampling + drop in affordance coherence (present-at-hand)
        - *Decision needed: How many samples = "spike"? 2× baseline? 3×?*
    - **Recovery latency:** Time to re-establish coherent affordance peaks once workaround learned
        - *Decision needed: What counts as "recovered"? (Suggest: coherence >0.7 baseline for 5+ steps)*
    - **Ablation:** Freeze top-down relevance → persistent present-at-hand behavior
        - *Decision needed: How to "freeze" – set β=0 in affordance scoring?*
- **Statistical design:**
    - Runs: 10-20 (breakdown point should be deterministic, so variance is in recovery dynamics)
    - Metrics: Mean recovery latency, peak feature sampling at breakdown, coherence time-series

**Experiment C — Habit/skill (OPTIONAL – RECOMMEND DROPPING):**
### IV. Objections & replies (half page)
**🚨 DECISION NEEDED (By Nov 24):** Select 3-4 strongest objections from list below. Don't try to answer everything.
**Current objections (2 drafted):**
- **Simulation vs instantiation:** Claim only **operational** temporal consciousness (capacity-level), tied to measurable fulfillment/disappointment and stability across a temporal window
    - *Reply strategy: Deflate to functional equivalence - not claiming phenomenal consciousness, only architectural constraints*
- **Embodiment worry:** Worldhood modeled as **norm-laden affordances** (not a neutral scene graph); no robotics required
    - *Reply strategy: Affordances are relational properties, not physical properties - software tools have affordance structure*

**Additional objections to consider (pick 1-2):**
- **Measure problem:** "Correlation ≠ constitution" - how do you avoid Chalmers-style hard problem?
    - *Potential reply: We're not claiming constitution, we're testing architectural necessity - if removing retention breaks sustained intentionality, retention is necessary (not sufficient)*
- **Scale objection:** "Toy environment doesn't generalize to real temporal consciousness"
    - *Potential reply: Scaling argument - if principles hold in minimal case, that's evidence they're fundamental (not accidents of complexity)*
- **Chinese Room variant:** "Syntax without semantics" - just symbol manipulation
    - *Potential reply: Same objection applies to human neurons - we're neutral on substrate, focused on architectural constraints*
- **Behaviorist worry:** "You're just measuring outputs, not inner experience"
    - *Potential reply: Phenomenology is about structures of experience, not qualia - we're testing structural constraints, not subjective feel*

**Selection criteria:**
- Pick objections where you have **sharp, non-defensive replies**
- Prioritize objections your **readers will actually raise** (check with advisor/classmates)
- Aim for **diversity** (metaphysical, methodological, phenomenological)

**Recommended set (if unsure):**
1. Simulation vs instantiation
2. Measure problem
3. Scale objection
4. Embodiment worry

### V. Payoff (1/4 page)
- What this clarifies about **time-consciousness** in humans (functionally), and why **architectural constraints** matter more than substrate type for these capacities.

---
## Development Implementation
**🚨 TIER 1 DECISIONS NEEDED (Block all implementation):**
- [ ] Current hardware specs: RAM: ***, GPU: ***, CPU: ___
- [ ] PyTorch version: ___ (check compatibility with hardware)
- [ ] Viz library: matplotlib (recommended - simple) / plotly / custom
- [ ] Logging: CSV files (recommended - no dependencies) / wandb / tensorboard
- [ ] Exp C decision: DROP (recommended) / KEEP

**Stack:** Python + PyTorch. Two notebooks: `temporal_thickness.ipynb`, `worldhood_breakdown.ipynb`
- **Alternative if PyTorch unavailable:** JAX/Flax or pure NumPy (slower but works on any machine)
- **Dependency list:**
    - Core: `torch`, `numpy`, `matplotlib`
    - Optional: `pandas` (data wrangling), `seaborn` (prettier plots), `tqdm` (progress bars)
    - **Total install size: ~500MB with CPU-only PyTorch**

**PFC module implementation:**
- ~~Gated GRU/LSTM with decay mask~~ **RECOMMENDATION:** Simple GRU with post-hoc exponential decay mask
    - Decay function: `state[t] = state[t-1] * exp(-λΔt)` where λ = decay rate parameter
    - **Decision:** λ value? (Suggest: λ=0.3 for 3s window → ~37% retention at t=3s)
- Add scalar "stability gate" ~~trained by RL or supervised schedules~~ **RECOMMENDATION:** Supervised schedule first
    - Schedule: High gate (0.9) during ambiguous phase, low gate (0.1) during clear phase
    - **RL version:** Defer to "future work" unless you have existing RL pipeline
- **Protention head:** Linear layer on top of GRU hidden state → softmax over next-token predictions
    - Loss: Cross-entropy between predicted and actual next token

**Parietal map implementation:**
- Vector of candidates with scores = `α·salience + β·task_relevance + γ·policy_value`
    - **Initial values:** α=0.33, β=0.33, γ=0.33 (equal weighting, tune if needed)
    - Salience: Bottom-up saliency (e.g., novelty, contrast)
    - Task relevance: Top-down goal match (e.g., tool needed for current subgoal)
    - Policy value: Q-value or advantage estimate from policy network
- Softmax with temperature τ:
    - **Ready-to-hand:** τ=0.5 (sharp peaks, fluent selection)
    - **Present-at-hand:** τ=2.0 (flat distribution, exploratory inspection)
    - **Breakdown trigger:** When action fails, set τ=2.0 for K steps, then anneal back
- Small attractor update: `scores ← scores + η·∇scores`
    - **η value:** 0.1 (conservative, prevents instability)
    - **Optional:** Skip attractor dynamics if priority map converges naturally

**Logging design:**
- Save state trajectories: `[timestep, hidden_state, prediction, target, loss]`
- Affordance peaks: `[timestep, candidate_scores, selected_action, temperature]`
- Breakdown events: `[timestep, action_failed, feature_sampling_rate, coherence_score]`
- **File format:** CSV (simplest) or HDF5 (if datasets get large)
- **Plot outputs:** PNG files (300 DPI for paper), saved to `/figures/` directory

**Total coding time estimate:**
- Exp A (text disambiguation): **2-3 focused days** (includes debugging)
- Exp B (worldhood toy): **3-4 focused days** (environment + breakdown logic + metrics)
- Plotting & analysis: **1 day** (all figures + statistical tests)
- **Buffer for inevitable issues:** **1-2 days**
- **Total: ~7-10 focused days of coding** (Nov 13-24 in revised timeline)

---
## Timeline (concrete dates)
**⚠️ UPDATED TIMELINE (Nov 11 - see Decision Roadmap below for rationale):**
- **Nov 11–12:** 🔴 **BLOCKING:** Hardware audit + Tier 1 decisions (Exp C fate, environment choices, stack locks)
- **Nov 13–14:** Stub notebooks, implement PFC module with retention/protention + logging
- **Nov 15–18:** Run **Experiment A** (text disambiguation); produce decay curves, protention accuracy, ablation; draft Sec II–III(A)
- **Nov 19–22:** Build **worldhood toy** (4×4 grid); implement breakdown switch; run metrics; draft Sec III(B)
- **Nov 23–25:** Write Sec I (framing) & IV (objections); refine all figures
- **Nov 26–27:** Full draft to "peer-ready" state (2-day buffer added vs original timeline)
- **Nov 28–30:** Feedback incorporation from advisor/peer
- **Dec 1–3:** Final polish, proofing, citation formatting
- **Dec 4:** Buffer day for inevitable fires
- **Dec 5:** Submit by deadline

**Original timeline (for reference):**
- ~~Nov 11–14: Finalize architecture; stub both notebooks; implement PFC retention/protention and logging~~
- ~~Nov 15–19: Run Experiment A; produce decay curves, protention accuracy, ablation results; draft section II–III(A)~~
- ~~Nov 20–24: Build worldhood toy; implement breakdown switch; run metrics; draft III(B)~~
- ~~Nov 25–27: Write I (framing) & IV (objections); refine figures~~
- ~~Nov 28–30: Full draft; internal edit pass~~
- ~~Dec 1–3: Advisor/peer feedback; revise~~
- ~~Dec 4: Final proof; submit Dec 5~~

**Key adjustments:**
- Moved "peer-ready" deadline 2 days earlier (Nov 26 vs Nov 28)
- Created explicit buffer day (Dec 4)
- Separated Tier 1 blocking decisions (Nov 11-12) from implementation start (Nov 13)
- Adjusted Exp A/B weeks to 4 days each (more realistic for debug cycles)
- 🎯 **Critical path:** If Tier 1 decisions slip past Nov 12, entire timeline cascades

---
## Preliminary works cited
**Primary phenomenology**
- Husserl, E. *On the Phenomenology of the Consciousness of Internal Time*.
- Husserl, E. *Logical Investigations* (Intentionality).
- Heidegger, M. *Being and Time* ( worldhood; ready-/present-at-hand).
- Merleau-Ponty, M. *Phenomenology of Perception* (motor intentionality, habit).

**Bridging / cognitive**
- Baddeley, A. “Working Memory.” *Science* (classic overview).
- Friston, K. “The free-energy principle: a unified brain theory?” *Nat. Rev. Neurosci.* (predictive processing context).
- O’Keefe, J. & Nadel, L. *The Hippocampus as a Cognitive Map* (map-based memory).
- Eichenbaum, H. “Time cells in the hippocampus.” (for temporal coding, optional).
- Miller, E.K. & Cohen, J.D. “An integrative theory of prefrontal cortex function.” *Annu. Rev. Neurosci.* (top-down control).


---
## 🚨 PRE-SUBMISSION DECISION ROADMAP (Added Nov 11)
> **Critical path analysis:** 23 days to submission with hardware constraints. This roadmap identifies blocking decisions that must be made before implementation can proceed. Each tier represents a dependency cascade - Tier 1 blocks Tier 2, Tier 2 blocks Tier 3, etc.

### TIER 1: MUST DECIDE BY NOV 13 (2 days) ⚠️
*These block ALL downstream work*
### 1.1 Hardware Constraints & Stack Finalization
- [ ] **Current dev machine specs?** (RAM, GPU, CPU - determines dataset size limits)
- [ ] **Exp C final decision:** Keep or drop? (Recommendation: **DROP** - mention as future work. Focus quality over quantity)
- [ ] **Library versions locked:**
    - PyTorch version: ___
    - Visualization: matplotlib / plotly / custom
    - Logging: wandb / tensorboard / raw CSV
- [ ] **Compute budget:** How many training runs can you realistically execute? (affects statistical power)

### 1.2 Experiment A: Pick ONE Ambiguous Stream Type
**Decision required:** You listed three options. Choose now:
- [ ] **Option 1:** Text disambiguation (e.g., gradually revealed word/phrase) - **RECOMMENDED: Fastest to implement, still phenomenologically valid**
- [ ] **Option 2:** Moving dot classification - requires rendering pipeline
- [ ] **Option 3:** Noisy syllable sequence - requires audio preprocessing

**Supporting specifications:**
- [ ] **"Sustained directedness" operational threshold:** What % accuracy drop = "collapse"? (Suggest: >15% drop from baseline)
- [ ] **Concrete retention window:** Pick from range. **Recommendation: 3 seconds** (interpretable, maps to working memory literature)
- [ ] **Timestep granularity:** 100ms? 250ms? 500ms? (affects sequence length)

### 1.3 Experiment B: Workbench Environment Spec
**Minimal viable environment:**
- [ ] **Grid dimensions:** Recommend **4×4 text grid** (keeps state space tractable)
- [ ] **Tool inventory:** **2 tools only** (hammer/saw, write/erase, etc.)
- [ ] **Breakdown mechanism:** Gradual degradation vs sudden failure?
    - **Recommendation:** Sudden failure at predetermined step (easier to detect breakdown signature)
- [ ] **Recovery criterion:** Quantitative threshold for "affordance coherence restored"
    - Suggest: Affordance peak returns to >0.7 of pre-breakdown baseline for 5+ consecutive steps

---
### TIER 2: MUST DECIDE BY NOV 17 (6 days)
*These determine experimental interpretability*
### 2.1 PFC Module Implementation Choices
- [ ] **Decay function type:**
    - Pure exponential: `state[t] = state[t-1] * exp(-λΔt)`
    - Leaky integrate-and-fire: `state[t] = αstate[t-1] + (1-α)input[t]`
    - **Recommendation:** Exponential (cleaner retention profile visualization)
- [ ] **Retention storage:** Full window vs compressed summary?
    - **Recommendation:** Store full window for 3s, then FIFO drop oldest
- [ ] **Gating mechanism choice:**
    - RL-based (adds training loop complexity)
    - Supervised schedule (e.g., high stability during ambiguous phase, low during clear)
    - **Recommendation:** Supervised schedule first - simpler, still demonstrates principle
- [ ] **Protention accuracy metric:**
    - KL divergence (continuous)
    - Classification accuracy (discrete)
    - Cross-entropy (middle ground)
    - **Recommendation:** Cross-entropy (standard, interpretable)

### 2.2 Parietal Module Hyperparameter Ranges
- [ ] **Initial affordance weights (α, β, γ):**
    - Start equal (0.33, 0.33, 0.33)?
    - Task-biased (0.2, 0.5, 0.3)?
    - **Recommendation:** Equal start, then brief grid search if time permits
- [ ] **Temperature calibration:**
    - "Ready-to-hand": τ = ??? (lower = sharper peaks)
    - "Present-at-hand": τ = ??? (higher = flatter distribution)
    - **Recommendation:** Ready τ=0.5, Present τ=2.0 (start here, tune if needed)
- [ ] **Breakdown detection method:**
    - Threshold on prediction error
    - Learned detector (adds complexity)
    - **Recommendation:** Simple threshold - if action fails twice, trigger diagnostic mode
- [ ] **Attractor step size (η):** Suggest **η=0.1** (conservative, stable)

### 2.3 Statistical Design
- [ ] **Runs per condition:** Minimum 10, ideally 30 (depends on compute budget from 1.1)
- [ ] **Statistical tests:**
    - Paired t-tests for ablations
    - Bootstrap 95% CIs for key metrics
    - **Skip Bayesian estimation unless you have prior experience** (time sink)
- [ ] **Baseline specification:**
    - Null model: Feedforward network (no retention)
    - Control model: Fixed retention (no decay)
- [ ] **Figure priority (max 3-4 for space):**
    1. **REQUIRED:** Retention decay curve with/without retention module
    2. **REQUIRED:** Breakdown signature time-series (affordance coherence + feature sampling)
    3. **REQUIRED:** Ablation comparison bar chart (accuracy, stability metrics)
    4. Optional: Architecture schematic diagram

---
### TIER 3: MUST DECIDE BY NOV 24 (13 days)
*These shape paper narrative*
### 3.1 Writing Constraints - VERIFY WITH SYLLABUS
- [ ] **Page limit:** Course requirement = ___? (Usually 10-12pp for finals)
- [ ] **Current allocation check:**
    - Sec I: 1pg | Sec II: 1.5pg | Sec III: 1pg | Sec IV: 0.5pg | Sec V: 0.25pg
    - = 4.25pg prose + refs (1-2pg) + figures (1pg) ≈ **6-7 pages total**
    - **Is this your target or do you need more content?**
- [ ] **Citation format:** APA / Chicago / Other? (affects formatting time)
- [ ] **Code submission expectation:** GitHub repo required or optional?

### 3.2 Objection Selection (Need 3-4 Total)
**You have 2, need 1-2 more:**
- [x] Simulation vs instantiation
- [x] Embodiment worry
- [ ] **Add: Measure problem** - "Correlation ≠ constitution" (Chalmers-style hard problem)
- [ ] **Add: Scale objection** - "Toy environment doesn't generalize"
- [ ] **Add: Chinese Room variant** - "Syntax without semantics" (skip if too obvious)

**Select strongest 3-4 objections where you have sharp replies.** Don't try to answer everything.
### 3.3 Figure Production Plan
- [ ] **Which 3 plots are LOCKED IN?** (See 2.3 recommendations)
- [ ] **Figure space budget:** Max 1 page (2-3 figures with captions)
- [ ] **Architecture diagram?**
    - **If yes:** Hand-drawn + digitized OR programmatic (mermaid/graphviz)?
    - **Recommendation:** Simple box diagram showing PFC ↔ Parietal ↔ Habit loop (15min in Excalidraw)

---
### TIER 4: MUST DECIDE BY NOV 30 (19 days)
*Contingency planning*
### 4.1 Failure Modes & Backup Plans
- [ ] **If Exp A doesn't converge:**
    - Fallback: Synthetic data with known temporal structure
    - Fallback: Pre-trained embeddings instead of end-to-end training
- [ ] **If Exp B tool-breaking is too noisy:**
    - Pivot: Demonstrate worldhood via task-switch (ready-to-hand → present-at-hand) instead
- [ ] **If hardware completely fails:**
    - Nuclear option: Pure theoretical paper with "proposed experiments" section
    - **Only viable if you have strong philosophical contribution independent of empirical work**

### 4.2 Review & Feedback Timeline
- [ ] **Draft readers identified:**
    - Professor: *** (response time = ***?)
    - Peer: *** (response time = ***?)
    - Classmate: *** (response time = ***?)
- [ ] **Feedback scope:**
    - Clarity & flow (all readers)
    - Technical rigor (peer with ML background)
    - Phenomenology accuracy (professor or philosophy student)
- [ ] **"Peer-ready" draft deadline:**
    - Current plan: Nov 28 (gives 3 days for feedback before Dec 1 final)
    - **⚠️ WARNING:** 3-day turnaround during finals week is optimistic
    - **Recommendation:** Move to Nov 26 (gives 5 days buffer)

---
## 🎯 IMMEDIATE ACTION ITEMS (Next 48 Hours)
**BLOCKING DECISIONS (do these first):**
5. **Exp C fate:** Recommend **DROPPING IT**. Mention as "future work: habit chunking via basal-ganglia loops demonstrates motor intentionality sedimentation" (1 sentence in Section V). Two excellent experiments > three rushed ones.
6. **Hardware audit:** What machine are you coding on RIGHT NOW? Specs determine everything downstream.
7. **Exp A choice:** Go with **text disambiguation** (fastest, lowest overhead, phenomenologically valid).
8. **Exp B scope:** Lock in **4×4 grid, 2 tools, sudden failure** (minimal viable worldhood demo).

**UNBLOCKING TIER 2:**
9. Set retention window to **3 seconds** (maps to working memory, interpretable).
10. Use **supervised gating schedule** (defer RL complexity).
11. Temperature values: **τ=0.5 (ready), τ=2.0 (present)**.

**Timeline reality check:**
- **Nov 15-19 (Exp A week):** If you're still debugging architecture here, you're behind.
- **Nov 25-27:** U.S. Thanksgiving - are you affected? If yes, push writing earlier.
- **Dec 1-3 feedback:** Assumes instant turnaround from busy people in finals week - unrealistic?

**Recommendation:** Shift all deadlines 2 days earlier to create buffer.

---
## 📊 REVISED TIMELINE (Adjusted for Buffer)
- **Nov 11–12:** Hardware audit, Tier 1 decisions locked, stub both notebooks
- **Nov 13–14:** Implement PFC retention/protention with logging, basic tests
- **Nov 15–18:** Run Experiment A (text disambiguation), produce plots, draft Sec II–III(A)
- **Nov 19–22:** Build worldhood toy, implement breakdown switch, run metrics, draft Sec III(B)
- **Nov 23–25:** Write Sec I (framing) & IV (objections), produce all figures
- **Nov 26–27:** Full draft complete ("peer-ready" state)
- **Nov 28–30:** Feedback incorporation, revisions
- **Dec 1–3:** Final polish, proof, formatting
- **Dec 4:** Buffer day (inevitable last-minute issues)
- **Dec 5:** Submit by deadline

---
## 💡 DESIGN RECOMMENDATIONS (From Analysis)
**Minimal Viable Exp A (Text Disambiguation):**
```python
# Example: Gradually reveal phrase
Sequence: "T..h..i..s.. ..i..s.. ..a.. ..t..e..s..t"
Ambiguity window: First 8 chars
Retention needed: Track char history to predict next
Disambiguation point: When "This" becomes clear
```
**Minimal Viable Exp B (Workbench):**
```javascript
Grid: 4×4 text cells
Tools: [hammer: combines cells, saw: splits cells]
Task: Achieve target pattern
Breakdown: Hammer breaks at step 15
Ready-to-hand: High affordance on hammer (used fluently)
Breakdown: Affordance spike on saw + increased cell inspection
Recovery: New policy stabilizes on saw workaround
```
**Why these are sufficient:**
- Text disambiguation captures retention/protention/fulfillment-disappointment
- Workbench captures worldhood/ready-to-hand/breakdown/present-at-hand
- Both are **implementable in 2-3 focused days each**
- Both produce **clear, interpretable signatures**
- Both map directly to **phenomenological concepts**

---
*This roadmap added by architectural analysis Nov 11, 2025. Treat as living document - update as decisions lock in.*
[[./🔥 Decision Roadmap & Action Items|🔥 Decision Roadmap & Action Items]]
[[./Temporal Consciousness — Academic Presentation (Smith-Pryor Compliant)|Temporal Consciousness — Academic Presentation (Smith-Pryor Compliant)]]
[[./Temporal Consciousness — Academic Presentation (Pre-Adjustment)|Temporal Consciousness — Academic Presentation (Pre-Adjustment)]]