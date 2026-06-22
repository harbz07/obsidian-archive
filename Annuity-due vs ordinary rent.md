---
notion-id: 928ce35b-c1a2-4d3a-962c-5ab03b046be6
base: "[[Practice Problem Log.base]]"
Got It Right: false
Difficulty: Medium
Formulas Used: []
Chapters:
  - Ch4
Date Attempted: 2025-10-10
What Tripped Me Up: ""
Coordination Insight: Shift annuity-due by ×(1 + r).
Source: Practice Exam
---
### Prompt
Rent is $1,800 paid at the start of each month for 24 months. Monthly rate = 0.5%. What is the present value?
### Given
- C = $1,800 each month
- r_m = 0.5% = 0.005
- n = 24 months
- Timing: annuity‑due (payments at start)

### Solution space
1) Ordinary annuity PV: PV_ord = C × [1 − (1 + r)^−n] / r
2) Annuity‑due shift: PV_due = PV_ord × (1 + r)
3) Compute numerically.
### Self‑check

> [!note] 🎯
> Quick mark
> - [ ] Correct — set Got It Right to true
> - [ ] Incorrect — add one line to "What Tripped Me Up" and keep Got It Right unchecked

- Did you use monthly r and n?
- Did you multiply by (1 + r) for annuity‑due?

### Log
- [ ] Got It Right
- What Tripped Me Up:
- Time Taken (min):