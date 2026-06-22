---
notion-id: 9e592793-dd0e-4225-a124-af1434b06297
base: "[[Practice Problem Log.base]]"
Got It Right: false
Difficulty: Hard
Formulas Used: []
Chapters:
  - Ch6
Date Attempted: 2025-10-10
What Tripped Me Up: ""
Coordination Insight: Set up IRR; check reasonableness with coupon vs YTM relation.
Source: Practice Exam
---
### Prompt
An 8% annual‑coupon, 5‑year, $1,000 face bond trades at $1,081.11. What is the annual YTM?
### Given
- Face = $1,000
- Coupon = $80 annually
- Price = $1,081.11
- n = 5 (annual)

### Solution space
Solve y in: 1,081.11 = 80/(1+y)^1 + 80/(1+y)^2 + 80/(1+y)^3 + 80/(1+y)^4 + 1,080/(1+y)^5
- Bracket: since price > par and coupon 8%, expect y < 8%.
- Try y = 7% then refine.

### Self‑check

> [!note] 🎯
> Quick mark
> - [ ] Correct — set Got It Right to true
> - [ ] Incorrect — add one line to "What Tripped Me Up" and keep Got It Right unchecked

- Premium → y < coupon rate.

### Log
- [ ] Got It Right
- What Tripped Me Up:
- Time Taken (min):