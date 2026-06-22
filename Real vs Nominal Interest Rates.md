---
notion-id: ad0665ab-f172-4ea3-9cf4-f083ef97f444
base: "[[Concept Maps by Chapter.base]]"
Chapter: Ch5
Power Dynamic: Unexpected inflation transfers wealth from lenders to borrowers
What's Being Signaled: Real rate = society's compensation for delayed gratification after adjusting for inflation; nominal rate includes inflation expectations
Understanding Level: 🤔 Getting It
Connects To:
  - Intertemporal Coordination
Key Players: Lenders and borrowers competing against inflation erosion
Core Coordination Problem: Coordination against inflation risk—how to preserve purchasing power across time
---
### Anchor
Coordination against inflation: preserve purchasing power across time by separating real and nominal components.
### Key players and incentives
- Lenders want real returns protected from inflation surprises
- Borrowers benefit when unexpected inflation erodes real debt burden

### Signals
- Exact Fisher: 1 + r_nom = (1 + r_real)(1 + π)
- Approximation: r_nom ≈ r_real + π (ok for small rates)

### Links
- Upstream: Inflation expectations, CPI measurement
- Sibling: Time value of money basics
- Downstream: Discount rate selection for NPV, wage and contract indexation

### Example vs counterexample
- Example: r_nom = 7%, π = 3% → r_real ≈ 4%; exact r_real = (1.07/1.03) − 1 ≈ 3.883%
- Counterexample: Plugging nominal r into real cash flows without adjusting → biased NPV

### Common trap → Fix
- Trap: Mixing real cash flows with nominal rates
- Fix: Match like with like. Either convert cash flows to nominal and discount with r_nom, or keep real flows and discount with r_real

### Status

> [!success] ✅
> **Mastery quick set**
> - [ ] Set Understanding to 😵 Confused
> - [ ] Set Understanding to 🤔 Getting It
> - [ ] Set Understanding to 💡 Clear
> - [ ] Set Understanding to ⚡ Could Teach It
> 
> Tip: After checking one, update the Understanding Level property at the top of the page to match.

Understanding Level: 🤔 Getting It | Last Reviewed:  2025-10-10 
### Interactive drills
- [ ] Write the anchor: why do we separate real and nominal?
- [ ] Convert between r_nom, r_real, π (exact and approx)
- [ ] Solve 2 reps: pick correct discount rate for given cash flow description; compute real return from nominal and inflation

> [!note]+ Examples
> - A project’s cash flows are quoted in today’s dollars with no inflation growth. WACC given as nominal 10%, π = 2%. Choose discount rate.
> - Nominal return 12%, inflation 7% → real ≈ 4.67% exact: (1.12/1.07)−1

> [!note]+ Self‑check
> 1) When is the additive Fisher approx acceptable?
> 2) What must match between cash flow definition and discount rate?
> 3) Who wins from an inflation surprise and why?

---