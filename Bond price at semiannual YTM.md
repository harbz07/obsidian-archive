---
notion-id: c64d09ff-e779-4060-9ce0-d2f3cbfc07ca
base: "[[Practice Problem Log.base]]"
Got It Right: false
Difficulty: Medium
Formulas Used: []
Chapters:
  - Ch6
Date Attempted: 2025-10-10
What Tripped Me Up: ""
Coordination Insight: Halve y, double n for pricing; premium vs discount logic.
Source: Practice Exam
---
### Prompt
Price a bond: $1,000 face, 10 years, 5% coupon paid semiannually. Quoted YTM = 6% APR. What’s the price?
### Given
- Face = $1,000
- Coupon rate = 5% → $50/yr → $25 per half‑year
- y_semi = 6%/2 = 3%
- n = 10×2 = 20

### Solution space
Price = Σ 25/(1.03)^t for t=1..20 + 1,000/(1.03)^20 = 
### Self‑check

> [!note] 🎯
> Quick mark
> - [ ] Correct — set Got It Right to true
> - [ ] Incorrect — add one line to "What Tripped Me Up" and keep Got It Right unchecked

- Halved y and doubled n?
- Premium or discount? Coupon 5% < YTM 6% → discount.

### Log
- [ ] Got It Right
- What Tripped Me Up:
- Time Taken (min):