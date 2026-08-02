# FE Targeted Drill 01 — Engineering Economics Factors & Reaction Order

> Built per [[05 Skills/FE Practice Exam Development Protocol.md]]. Targeted follow-up to [[03 Projects/FE Exam Prep/FE ChemE Practice Exam 01.md]] — drilling the two areas missed there: **simple vs. compound vs. annuity interest factors** (Q20 miss) and **zero/first/second-order kinetics** (Q16 miss).
> No formulas given — look them up in the FE Handbook. All values provided. Answers + worked calcs at the bottom. Write your letter under each question.

---

## Part A — Engineering Economics (simple vs. compound vs. annuity)

**A1.** $5,000 is invested today at an interest rate of 8% per year, **compounded annually**. The value of the investment after 6 years is most nearly:
*Refer to FE Handbook (Engineering Economics) — single-payment compound-amount factor (F/P).*
- A) $7,930
- B) $7,400
- C) $8,000
- D) $6,340

A

**A2.** A $2,000 loan is issued at 5% per year **simple interest** for 3 years. The total amount owed at the end of 3 years is most nearly:
*Refer to FE Handbook (Engineering Economics) — simple interest.*
- A) $2,150
- B) $2,300
- C) $2,315
- D) $2,600

B

**A3.** $1,000 is deposited at the **end of each year** for 5 years into an account earning 6% per year, compounded annually. The total accumulated value immediately after the last deposit is most nearly:
*Refer to FE Handbook (Engineering Economics) — uniform-series compound-amount factor (F/A).*
- A) $5,000
- B) $5,310
- C) $5,640
- D) $6,340

C

**A4.** A piece of equipment will generate savings of $500 at the **end of each year** for 4 years. Using an interest rate of 10% per year, the present worth of these savings is most nearly:
*Refer to FE Handbook (Engineering Economics) — uniform-series present-worth factor (P/A).*
- A) $2,000
- B) $1,700
- C) $1,450
- D) $1,585

D

---

## Part B — Reaction Order & Kinetics (zero / first / second)

**B1.** A **zero-order** reaction has a rate constant of 0.1 mol/(L·min). Starting from an initial concentration of 2.0 mol/L, the time required for the concentration of the reactant to fall to 0.5 mol/L is most nearly:
*Refer to FE Handbook p. 243 (Chemical Engineering — Reaction Kinetics) — zero-order integrated rate law.*
- A) 15 min
- B) 5 min
- C) 10 min
- D) 20 min

A

**B2.** A **first-order** reaction has a rate constant of 0.2 min⁻¹. Starting from an initial concentration of 1.0 mol/L, the concentration remaining after 5 minutes is most nearly:
*Refer to FE Handbook p. 243 (Chemical Engineering — Reaction Kinetics) — first-order integrated rate law.*
- A) 0.50 mol/L
- B) 0.37 mol/L
- C) 0.25 mol/L
- D) 0.14 mol/L

B

**B3.** A **second-order** reaction has a rate constant of 0.25 L/(mol·min) and an initial reactant concentration of 0.8 mol/L. The half-life of the reaction is most nearly:
*Refer to FE Handbook p. 243 (Chemical Engineering — Reaction Kinetics) — second-order half-life.*
- A) 4 min
- B) 2.5 min
- C) 5 min
- D) 10 min

C

**B4. (Concept)** For which reaction order is the **half-life independent of the initial reactant concentration**?
*Refer to FE Handbook p. 243 (Chemical Engineering — Reaction Kinetics) — half-life relationships.*
- A) Zero order
- B) Second order
- C) Third order
- D) First order

D

---

# Answer Key (with worked calculations)

| Q | Answer | Worked calculation | The trap it targets |
|---|--------|--------------------|---------------------|
| A1 | **A) $7,930** | $F = P(1+i)^n = 5000(1.08)^6 = \$7{,}934$ | *Simple* interest would give $5000(1+0.08\times6)=\$7{,}400$ (option B). "Compounded" ⇒ exponent. |
| A2 | **B) $2,300** | $F = P(1+i\,n) = 2000(1+0.05\times3)=\$2{,}300$ | *Compound* would give $2000(1.05)^3=\$2{,}315$ (option C). "Simple" ⇒ linear. |
| A3 | **C) $5,640** | $F = A\dfrac{(1+i)^n-1}{i}=1000\dfrac{1.06^5-1}{0.06}=\$5{,}637$ | Annuity (F/A), *not* a single lump sum. Don't use F/P here. |
| A4 | **D) $1,585** | $P = A\dfrac{(1+i)^n-1}{i(1+i)^n}=500\dfrac{1.10^4-1}{0.10(1.10)^4}=\$1{,}585$ | Present worth of a *series* (P/A). $500\times4=\$2000$ (option A) ignores the time value of money. |
| B1 | **A) 15 min** | Zero order: $t=\dfrac{C_{A0}-C_A}{k}=\dfrac{2.0-0.5}{0.1}=15$ min | Zero-order decay is *linear* in time, not exponential. |
| B2 | **B) 0.37 mol/L** | First order: $C_A=C_{A0}e^{-kt}=1.0\,e^{-0.2\times5}=0.368$ mol/L | Exponential decay; $e^{-1}=0.368$. |
| B3 | **C) 5 min** | Second order: $t_{1/2}=\dfrac{1}{k\,C_{A0}}=\dfrac{1}{0.25\times0.8}=5$ min | **This is the Q16 trap.** Second-order half-life *depends on $C_{A0}$*. Ignoring it (using $1/k=4$) gives option A. |
| B4 | **D) First order** | $t_{1/2}=\dfrac{\ln 2}{k}$ — no concentration term | Only first-order half-life is concentration-independent. |

---

## Final Gate — Option Existence Check (verification pass)

Recomputed from the printed problem values in a clean PowerShell pass.

| Q | Recomputed | Matched option | % error | Pass |
|---|-----------|----------------|---------|------|
| A1 | $7,934.37 | A) $7,930 | 0.06% | ✓ |
| A2 | $2,300.00 | B) $2,300 | 0% | ✓ |
| A3 | $5,637.09 | C) $5,640 | 0.05% | ✓ |
| A4 | $1,584.93 | D) $1,585 | 0.004% | ✓ |
| B1 | 15 min | A) 15 | 0% | ✓ |
| B2 | 0.3679 mol/L | B) 0.37 | 0.6% | ✓ |
| B3 | 5 min | C) 5 | 0% | ✓ |
| B4 | — (conceptual) | D) First order | — | ✓ |

**Gate result: PASS — every stated answer maps to a matching option within tolerance. Answer letters balanced A/B/C/D = 2/2/2/2.**

---

## Key takeaways to lock in

**Engineering Economics — read the interest wording first:**
- **"Simple interest"** → $F = P(1+in)$ — linear, no compounding.
- **"Compounded"** (single amount) → $F = P(1+i)^n$ — exponent.
- **"Each year / annual payment"** → annuity factor (F/A for future, P/A for present) — never treat a series as a lump sum.

**Reaction kinetics — memorize the three half-lives:**
- Zero order: $t_{1/2} = \dfrac{C_{A0}}{2k}$ — *decreases* as reaction proceeds.
- First order: $t_{1/2} = \dfrac{\ln 2}{k}$ — **constant**, independent of concentration.
- Second order: $t_{1/2} = \dfrac{1}{k\,C_{A0}}$ — *depends on $C_{A0}$* (your Q16 miss); *increases* as concentration drops.
