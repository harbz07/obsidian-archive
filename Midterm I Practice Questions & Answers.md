---
notion-id: 66a5dda5-bf5a-4310-a82a-5e37edeb914a
---
**Full practice set with detailed explanations for BUS 314 Midterm I**
> Use this as a reference guide to check your work and understand the logic behind each solution. Focus on the **why** behind each calculation, not just memorizing formulas.

---
## Corporate Structure & Taxation (Ch 1-2)
### Q1: S Corporation Taxation
**Problem:** An S corporation earns $9.10 per share before taxes. The corporate tax rate is 39%, the personal tax rate on dividends is 15%, and the personal tax rate on non-dividend income is 36%. What is the total amount of taxes paid if the company pays a $5.00 dividend?
**Answer:** A) $3.28
**Explanation:**
- S-corps have **pass-through taxation** — no corporate tax, only personal tax
- Total taxes = $9.10 × 36% = **$3.28**

**Coordination insight:** S-corps avoid double taxation by passing income directly to shareholders

---
### Q2: C Corporation Taxation
**Problem:** A C corporation earns $8.30 per share before taxes. The corporate tax rate is 39%, the personal tax rate on dividends is 15%, and the personal tax rate on non-dividend income is 36%. What is the total amount of taxes paid if the company pays a $6.00 dividend?
**Answer:** C) $4.14
**Explanation:**
- Corporate tax = $8.30 × 39% = $3.24
- Personal tax = $6.00 × 15% = $0.90
- **Total tax = $3.24 + $0.90 = $4.14**

**Coordination insight:** C-corps face **double taxation** — once at corporate level, once at shareholder level. This is a costly signal proving credibility.

---
### Q3: Limited Partnership Operations
**Problem:** Which of the following people cannot manage the operations of a firm in which they are part or full owners?
A) Stockholders in S corporations
B) Stockholders in C corporations
C) Limited partners in a limited partnership
D) General partners in a limited partnership
**Answer:** C) Limited partners in a limited partnership
**Coordination insight:** Limited partnerships separate capital from operations — limited partners provide capital but cannot manage (or they lose liability protection)

---
## Financial Statement Analysis (Ch 2)
### Q4: Quick Ratio Calculation
**Problem:** Using Luther Corporation's balance sheet, calculate the quick ratio for 2006.
**Data:**
- Cash: $65.7M
- Accounts receivable: $54.4M
- Inventories: $46.1M
- Total current liabilities: $143.2M

**Answer:** A) 0.87
**Formula:** Quick Ratio = (Current Assets - Inventory) / Current Liabilities
**Calculation:**
- Quick Ratio = ($171.3 - $46.1) / $143.2 = $125.2 / $143.2 = **0.87**

**Coordination insight:** Quick ratio is a **vulnerability signal** — can the company meet short-term obligations without selling inventory?

---
### Q5: Diluted EPS
**Problem:** Using Luther Corporation's income statement, calculate diluted earnings per share for 2006.
**Data:**
- Net income: $10.6M
- Shares outstanding: 10.0M
- Stock options outstanding: 0.3M
- No convertible bonds

**Answer:** A) $1.03
**Formula:** Diluted EPS = Net Income / (Shares Outstanding + Options + Convertible Shares)
**Calculation:**
- Diluted EPS = $10.6 / (10.0 + 0.3 + 0) = $10.6 / 10.3 = **$1.03**

**Coordination insight:** Diluted EPS shows what happens if all options/convertibles are exercised — a more conservative measure

---
## Time Value of Money (Ch 3-4)
### Q6: Discount Factor
**Problem:** If the interest rate is 9%, the one-year discount factor is equal to:
**Answer:** C) 0.917
**Formula:** Discount Factor = 1 / (1 + r)^n
**Calculation:**
- 1 / (1.09)^1 = **0.917**

**Coordination insight:** Discount factors translate future dollars into present dollars — essential for intertemporal coordination

---
### Q7: Present Value for Retirement
**Problem:** Sara wants to have $600,000 in her savings account when she retires. How much must she put in the account now, if the account pays 8% fixed interest, to ensure she has $600,000 in 20 years?
**Answer:** A) $128,729
**Calculator:**
- N = 20
- I/Y = 8
- PMT = 0
- FV = 600,000
- **Compute PV = -$128,728.92**

**Coordination insight:** Present value shows the **opportunity cost** of waiting — how much less you need to invest today if you can wait

---
### Q8: Stream of Cash Flows PV
**Problem:** What is the PV of cash flows: $5000 (year 1), $6000 (year 2), $7000 (year 3), $8000 (year 4) at 10% interest?
**Answer:** B) $20,227
**Calculation:**
- PV = $5000/(1.1)^1 + $6000/(1.1)^2 + $7000/(1.1)^3 + $8000/(1.1)^4
- PV = $4,545.45 + $4,958.68 + $5,259.20 + $5,464.11 = **$20,227.44**

---
### Q9: NPV Calculation
**Problem:** A business promises to pay $1500 (year 1), $3000 (year 2), and $3000 (year 3) for an investment of $6000 today. What is the PV if interest rate is 6%?
**Answer:** A) $603.94
**Calculator (CF method):**
- CF0 = -$6000
- CF1 = $1500, F1 = 1
- CF2 = $3000, F2 = 2
- Interest = 6%
- **Compute NPV = $603.94**

**Coordination insight:** Positive NPV means the project creates value — benefits exceed opportunity costs

---
## Perpetuities & Annuities (Ch 4)
### Q10: Delayed Perpetuity
**Problem:** A perpetuity will pay $900 per year, starting five years after purchase. What is the PV on purchase date if interest rate is 11%?
**Answer:** C) $5,390
**Two-step calculation:**
1. Calculate perpetuity value at t=4: C/r = $900/0.11 = $8,181.82
2. Discount back to t=0: $8,181.82 / (1.11)^4 = **$5,389.62**

**Coordination insight:** Perpetuities turn wealth into permanent power — infinitely repeating cash flows

---
### Q11: Annuity Future Value
**Problem:** Grandparents deposit $1200 every birthday from age 1-18. Account pays 6% annually. How much immediately after 18th birthday deposit?
**Answer:** A) $37,086.78
**Calculator:**
- N = 18
- I/Y = 6
- PV = 0
- PMT = -$1200
- **Compute FV = $37,086.78**

**Coordination insight:** Compounding is how the patient accumulate wealth — time preference coordination

---
### Q12: Loan Payment Calculation
**Problem:** You purchase a $33,000 car with 0.75% monthly rate (9% APR) for 60 months. What are monthly payments?
**Answer:** B) $685
**Calculator:**
- N = 60
- I/Y = 0.75
- PV = 33,000
- FV = 0
- **Compute PMT = -$685.03**

---
### Q13: Growing Annuity (Retirement Savings)
**Problem:** You're 30 years old, planning retirement at 65. Salary is $42,000 next year, growing at 5% annually. You'll deposit 8% of salary each year starting at age 31. Interest rate is 9%. What is the PV (at age 30) of retirement savings?
**Answer:** A) $61,303
**Calculation:**
- First deposit = 0.08 × $42,000 = $3,360
- Growing annuity formula with g = 5%, r = 9%, N = 35
- PV = $3,360 × [1/(0.09-0.05)] × [1 - ((1+0.05)/(1+0.09))^35] = **$61,303**

---
## Interest Rates & Compounding (Ch 5)
### Q14: Effective Annual Rate (EAR)
**Problem:** What is the EAR for an 11% APR compounded quarterly?
**Answer:** C) 11.46%
**Formula:** EAR = (1 + APR/m)^m - 1
**Calculation:**
- EAR = (1 + 0.11/4)^4 - 1 = (1.0275)^4 - 1 = **0.1146 or 11.46%**

**Coordination insight:** EAR standardizes rates across different compounding frequencies for fair comparison

---
### Q15: Comparing Investment Returns
**Problem:** Which investment offers the lowest effective rate?
- A: 6.9030% Annual
- B: 6.6992% Daily
- C: 6.7787% Quarterly
- D: 6.7643% Monthly

**Answer:** A) Investment A
**Calculation:** Convert all to EAR
- EAR(A) = 6.9030% (already annual)
- EAR(B) = (1 + 0.066992/365)^365 - 1 = 6.9280%
- EAR(C) = (1 + 0.067787/4)^4 - 1 = 6.9530%
- EAR(D) = (1 + 0.067643/12)^12 - 1 = 6.9781%

**Lowest:** Investment A at 6.9030%

---
### Q16: Mortgage Payment
**Problem:** You borrow $290,000 for 20 years (240 months) at 12% APR. What is the monthly payment?
**Answer:** C) $3,193
**Calculator:**
- N = 240
- I/Y = 1 (12%/12)
- PV = 290,000
- FV = 0
- **Compute PMT = -$3,193.15**

---
## Complex TVM Applications
### Q17: Multi-Stage Investment NPV
**Problem:** Salvatore invests $10,000 now and $10,000 at end of year 1, receiving $5,000 at end of each of years 1-5. Interest rate is 3%. What is the net value?
**Answer:** D) $3,189.80
**Two-step calculation:**
3. PV of investments = $10,000 + $10,000/(1.03) = $19,708.74
4. Use CF function:
    - CF0 = -$19,708.74
    - CF1 = $5,000, F1 = 5
    - Interest = 3%
    - **NPV = $3,189.80**

---
### Q18: Loan Balance (Amortization)
**Problem:** A $111,000 truck is financed over 4 years at 8.10% APR with monthly payments. After 3 years, what is the remaining balance?
**Answer:** C) $31,195
**Two-step calculation:**
5. Find monthly payment:
    - N = 48, I/Y = 8.1/12, PV = 111,000, FV = 0
    - **PMT = -$2,715.05**
6. Find PV of remaining 12 payments:
    - N = 12, I/Y = 0.675, PMT = -2,715.05, FV = 0
    - **Compute PV = $31,195**

---
### Q19: Real Interest Rate
**Problem:** In 2007, nominal interest rate was 4.5% and inflation was 2.8%. What was the real interest rate?
**Answer:** D) 1.65%
**Formula:** (1 + nominal) / (1 + inflation) - 1
**Calculation:**
- Real rate = 1.045 / 1.028 - 1 = 1.0165 - 1 = **1.65%**

**Coordination insight:** Real rates coordinate across time by removing inflation noise

---
### Q20: Opportunity Cost of Capital
**Problem:** A friend asks for $5,100 today, promising $5,610 in one year. Your best alternative investment with similar risk pays $5,508 in one year for the same $5,100. What is the opportunity cost of capital?
**Answer:** B) 8%
**Calculation:**
- Return from alternative = ($5,508 - $5,100) / $5,100 = $408 / $5,100 = **0.08 or 8%**

**Coordination insight:** Opportunity cost is the return you sacrifice by choosing one investment over the next best alternative

---
## Study Tips
**Pattern Recognition:**
- **S-corp vs C-corp:** Pass-through vs. double taxation
- **Quick ratio:** Liquidity without inventory
- **Discount factor:** Convert future → present
- **Perpetuity:** C/r (starts immediately) or C/r discounted (starts later)
- **Growing annuity:** Use special formula when g ≠ r
- **EAR:** Standardizes comparison across compounding frequencies
- **Real rate:** Removes inflation effect

**Calculator Shortcuts:**
- Always clear before new problem (2nd → CLR TVM)
- For monthly: divide APR by 12, multiply years by 12
- PMT and PV have opposite signs (one is inflow, one is outflow)
- Use CF worksheet for irregular cash flows

**Common Traps:**
- Forgetting to subtract inventory in quick ratio
- Using wrong compounding frequency
- Perpetuity starting later requires two-step calculation
- Real rate requires division, not subtraction
- Loan balance needs recalculation with remaining periods