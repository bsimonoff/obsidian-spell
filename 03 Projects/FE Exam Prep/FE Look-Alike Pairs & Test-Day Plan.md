# FE — Look-Alike Pairs & Test-Day Plan

> **Cross-reference:** See [[CLAUDE.md]] → "FE Practice Exam Creation." Built from graded misses on [[03 Projects/FE Exam Prep/FE ChemE Practice Exam 01.md]] and [[03 Projects/FE Exam Prep/FE ChemE Practice Exam 02.md]].
> **Your one nameable weakness:** you grab the *adjacent* formula/definition under a look-alike prompt. Your calculation execution is flawless — so this list is where your points actually leak. Read it the morning of the exam.

---

## The Look-Alike Pairs (memorize the *discriminator*, not just the formulas)

| # | Pair | The two forms | The tell / how to pick |
|---|------|---------------|------------------------|
| 1 | **Simple vs. compound interest** | Simple: $F=P(1+in)$ · Compound: $F=P(1+i)^n$ | Word **"compounded"** ⇒ exponent. "Simple" ⇒ linear. |
| 2 | **Refrigerator vs. heat-pump COP** | Fridge: $\text{COP}_R=\dfrac{T_L}{T_H-T_L}$ · Heat pump: $\text{COP}_{HP}=\dfrac{T_H}{T_H-T_L}$ | What are you *paid to move*? Cold space kept cold ⇒ $T_L$ on top. Heat delivered to hot side ⇒ $T_H$ on top. Note $\text{COP}_{HP}=\text{COP}_R+1$. |
| 3 | **Eutectic vs. recrystallization** | Eutectic = liquid → two solids at lowest melting point · Recrystallization = new strain-free grains in a cold-worked metal | Definition says **"liquid / melting"** ⇒ eutectic (phase diagram). Says **"grains / cold-worked"** ⇒ recrystallization (solid-state). |
| 4 | **Half-life by reaction order** | Zero: $t_{1/2}=\dfrac{C_{A0}}{2k}$ · First: $t_{1/2}=\dfrac{\ln 2}{k}$ (constant) · Second: $t_{1/2}=\dfrac{1}{kC_{A0}}$ | **Look at units of $k$.** If $k$ carries "mol⁻¹" (e.g., L/mol·min), a concentration *must* appear ⇒ 2nd order. Only 1st-order half-life is concentration-independent. |
| 5 | **CSTR vs. PFR (1st order)** | CSTR: $\dfrac{C_0}{C_f}=1+k\tau$ · PFR: $\dfrac{C_0}{C_f}=e^{k\tau}$ | CSTR = perfectly mixed, reacts at low outlet conc ⇒ algebraic $(1+k\tau)$, needs *more* volume. PFR = conc falls along tube ⇒ integrate ⇒ $e^{k\tau}$. |
| 6 | **Manometer: liquid-over-liquid vs. gas-over-liquid** | General: $\Delta P=(\rho_{gauge}-\rho_{line})gh$ | Only drop $\rho_{line}$ when the line fluid is a **gas** (ρ≈0). Liquid over liquid (water/mercury) ⇒ you **must** subtract it. |

### High-yield extras to eyeball (common FE traps, same family)
- **Laminar vs. turbulent:** pipe flow transitions near **Re ≈ 2,100**. Laminar friction factor $f=64/Re$; turbulent needs Moody/Colebrook.
- **LMTD vs. arithmetic mean ΔT:** always use **log-mean** unless told the ΔTs are close.
- **Gauge vs. absolute pressure:** check which the problem wants (ideal-gas law uses absolute).
- **Mass fraction vs. mole fraction:** convert via molecular weights before using in mole-based equations.

---

## 3-Day Plan (consolidation, NOT new material)

**Day 1 (today) — one full-length timed mock.**
- Take an **official NCEES FE Chemical practice exam** if you can get it (best calibration; mine run easier). Simulate real conditions: ~5 hr 20 min, only the searchable NCEES Reference Handbook PDF, NCEES-approved calculator.
- Goal here is **stamina + handbook-navigation speed**, not score. Note which handbook sections you fumbled to find.

**Day 2 — targeted repair + logistics.**
- Review *only* the questions you missed on the mock + this look-alike sheet. Don't start new topics.
- Drill **handbook search speed**: practice finding 10 random equations fast. On exam day, knowing *where* it lives is half the clock.
- **Logistics check:** confirm Pearson VUE appointment time + location, travel time, valid government ID (name must match registration), calculator is on the NCEES-approved list, know the check-in rules (no personal items).

**Day 3 (day before) — taper. This is deliberate.**
- **Light** review of this sheet + your formula intuition. No heavy problem sets.
- Prep your bag, lay out ID + calculator, confirm travel. **Sleep is worth more than one more practice problem** — you flagged that health/wellbeing is a hard line; honor it here. A rested brain catches look-alike traps; a fried one walks into them.

---

## Test-Day Execution Rules (your anti-slip checklist)

1. **Say the answer as value + letter before committing** — "5 minutes, that's C." Kills the misinput error (you lost a "point" to this on the drill).
2. **Unit-check every calc answer.** If the units don't resolve to what's asked, you grabbed the wrong formula (this catches the 2nd-order half-life trap automatically).
3. **On the identify step, pause half a second:** which of the look-alike pair is this? That half-second is where your points are.
4. **Flag and move on.** ~1.7 min/question average. If stuck >2 min, flag it, guess, return later. Never let one problem eat five.
5. **No blanks** — there's no wrong-answer penalty. Every flagged question gets a guess before you leave the section.
6. **Trust your calc engine.** It's been flawless across every practice set. Your errors come from *setup*, not arithmetic — so spend your scrutiny there.

---

*You're scoring 85–90% on full practice sets against a ~50–56% cut score. Barring a stamina collapse, you pass. Consolidate, rest, execute.*
