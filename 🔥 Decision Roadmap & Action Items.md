---
notion-id: 2a998e9c-907e-8127-bd52-ea319d61ce4e
---
**Parent Project:** Temporal Consciousness as Architectural Constraint
**Deadline:** Dec 5, 2025 | **Status:** 23 days remaining

---
# ⚠️ CRITICAL PATH BLOCKER
## Hardware Status (DECIDE NOW)
Your main dev machine is broken. This blocks everything.
**Required decisions TODAY:**
- What machine are you using? (specs: RAM, GPU/CPU only, local/cloud)
- Does this kill Exp C? (if yes → drop it, cite as future work)
- Timeline impact: Each day without environment = -1 day buffer

---
# TIER 1: Must Decide By Nov 13
## Exp A: Temporal Thickness Environment
**PICK ONE (recommend #1):**
1. ✅ **Text disambiguation** ← FASTEST
    - Gradually reveal "THE CAT SAT" vs "THE CAR SAT"
    - No rendering overhead, interpretable results
2. Moving dot classification (needs visual pipeline)
3. Noisy syllable stream (needs audio preprocessing)

**Define "collapse":** Accuracy drop >***% OR stability variance >***?

---
## Exp B: Worldhood Toy Specification
**Environment parameters:**
- Grid size: **4×4** (minimal viable)
- Tools: **2 types** (e.g., "hammer"=diagonal, "wrench"=orthogonal)
- Breakdown: **Sudden failure** (easier detection)
- Recovery threshold: Affordance score **>0.8 for 3 steps**

**Deadline:** Nov 13 to start coding Nov 14

---
## Stack Decisions
- [ ] PyTorch version: __
- [ ] Viz library: **matplotlib** (simple) / plotly (interactive) / custom
- [ ] Logging: **wandb** (recommend) / tensorboard / raw CSV
- [ ] Code repo required? Y / N
- [ ] Citation style: __

---
# TIER 2: Must Decide By Nov 17
## PFC Module Hyperparameters
**Retention window:** 1-5s → recommend **3s** (balance)
**Decay function:** `exp(-t/τ)` (standard exponential)
**Gating:** Supervised schedule ← **RECOMMEND** (saves 1-2 days vs RL)
**Protention metric:** KL divergence / cross-entropy / top-k?
**ACTION:** Document starting values for ablation baseline

---
## Parietal Module Parameters
**Affordance weights (α, β, γ):**
- Equal: [0.33, 0.33, 0.33]
- Task-biased: [0.2, 0.5, 0.3] ← which?

**Softmax temperatures:**
- Ready-to-hand: **τ = 0.5** (peaked)
- Present-at-hand: **τ = 2.0** (flat)

**Breakdown detection:** Fixed threshold (faster) / learned classifier?
**Attractor step:** **η = 0.05** (tune if unstable)
**VALIDATION:** 2-3 calibration runs Nov 17-18

---
## Evaluation Design
**Sample size:** 10 runs minimum (30 ideal if compute allows)
**Stats:** Paired t-test / bootstrap CI?
**Baseline:** Feedforward vs retention - H0?
**Figures (max 4):**
4. Retention decay curve (ESSENTIAL)
5. Breakdown time series (ESSENTIAL)
6. Ablation comparison (ESSENTIAL)
7. Architecture schematic (nice-to-have)

---
# TIER 3: Must Decide By Nov 24
## Writing Constraints
**Page limit:** VERIFY with syllabus (typical: 10-12 pages?)
**Current budget:** 4.25pg + refs + figs ≈ 6-7 total
⚠️ **This seems SHORT** - double-check requirements
**Thanksgiving:** Nov 25-27 writing window - does this affect you?

---
## Objections (pick 3-4 strong ones)
**Current:** simulation vs instantiation + embodiment worry
**Add 2 from:**
8. Measure problem: "Correlation ≠ constitution"
9. Chinese Room: "Syntax without semantics"
10. Scale: "Toy ≠ real consciousness"
11. Circularity: "Measuring what you built in"

**Strategy:** Only fight battles you can win decisively

---
# TIER 4: Contingency Plans
## If Exp A Fails
- Plan B: Synthetic data with ground truth
- Plan C: Pure simulation of retention dynamics

## If Exp B Too Noisy
- Plan B: Task-switch instead of tool failure
- Plan C: Simplify to 2×2 grid, 1 tool

## If Hardware Dies
- Plan B: Pure theory with "proposed experiments"
- ⚠️ May not satisfy requirements - CHECK

## Peer Review Risk
Current: Draft Nov 28 → feedback → revise → Dec 5 submit
**PROBLEM:** 3 days is TIGHT
**SUGGEST:** Draft by Nov 26 (lose 2 writing days, gain 5 revision days)

---
# 🎯 THIS WEEK'S ACTIONS
## Tuesday Nov 12
- [ ] Hardware confirmation
- [ ] **Drop Exp C?** (RECOMMEND: yes)
- [ ] Lock Exp A type (TEXT)

## Wednesday Nov 13
- [ ] Exp B spec (4×4, 2 tools, sudden break)
- [ ] Libraries + requirements.txt
- [ ] GitHub repo setup (if required)

## Thursday Nov 14
- [ ] PFC module stub + logging
- [ ] Choose hyperparameters
- [ ] Notebook templates

## Friday Nov 15
- [ ] Calibration runs
- [ ] Debug logging
- [ ] **START Exp A**

**Buffer:** Nov 16-19 for Exp A troubleshooting (CRITICAL)

---
# Key Takeaways
**Make-or-break moments:**
- Nov 15-19: Exp A must work or project collapses
- Nov 25-27: Writing sprint (holiday conflict?)
- Dec 1-3: Feedback window (too short?)

**Recommended cuts:**
- ❌ Exp C (habit) → future work
- ✅ Text tasks (fastest)
- ✅ 4×4 grid max (minimal)
- ✅ Supervised gating (not RL)
- ✅ 10 runs/condition (not 30)

**Questions needing immediate answers:**
12. Hardware specs?
13. Final paper page limit?
14. Code submission required?
15. Thanksgiving impact?