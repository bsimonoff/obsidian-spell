# FE Practice Exam Development Protocol

**Purpose**: Build high-quality FE ChemE practice exams with verified, exact answers. Use this protocol every time the user asks for a practice exam.

**Cross-reference**: See [[CLAUDE.md]] → "FE Practice Exam Creation" section for when/why to use this protocol.

---

## Core Principles

### 1. **NO SPOONFED EQUATIONS**
- **NEVER** write out equations in the problem statement
- **ALWAYS** reference the FE Handbook by page number + section
- Example:
  - ❌ WRONG: "Using Q = ṁ(h_out - h_in), what is the heat transfer rate?"
  - ✓ RIGHT: "What is the steady-flow heat transfer rate? *Refer to FE Handbook page 143 (Thermodynamics) for the energy balance equation.*"
- This forces users to consult the handbook and learn WHERE to find formulas

### 2. **EXACT ANSWERS ONLY**
- Every answer must be **mathematically exact** (within rounding to 1-2 significant figures max)
- NO "close enough" approximations like:
  - ❌ 603 W when answer is 600 W (too close but not exact)
  - ❌ 187.5 g when answer is 200 g (off by 6.7%)
  - ✓ Adjust problem parameters so calculation gives exactly the answer option
- **Precision is non-negotiable on the FE exam**

### 3. **WORK BACKWARDS FROM ANSWERS**
If a problem's natural parameters don't give an exact answer:
1. Calculate what the answer should be
2. If it doesn't match an option exactly, adjust ONE parameter
3. Recalculate to verify it now matches exactly
4. **Example**: Want Q = 600 W exactly with h=60, but get 603 W?
   - Change h to 80 W/m²·K → recalculate → verify = exactly 600 W (or adjust answer option to 804 W)

### 3b. **DOUBLE-CHECK CALCULATIONS FOR TRANSCENDENTAL FUNCTIONS**
- Problems involving exponents (fractional powers, exponentials, logs) are high-risk for calculation errors
- **Always verify independently**, especially:
  - T₂/T₁ = (P₂/P₁)^((γ-1)/γ) — verify exponent, verify power calculation
  - e^x calculations — verify x value first
  - ln(x) calculations — verify arguments
- Use PowerShell to compute, then verify result makes physical sense
- **Example error caught:** I calculated (5)^0.2857 = 1.278, but correct is 1.5835 (factor of 1.24x difference). Always recalculate.

### 4. **VERIFY ALL 20 ANSWERS WITH POWERSHELL**
- Before finalizing the exam, run a comprehensive QC check on all answers
- For each question:
  - Calculate the exact numerical result
  - Compare to the stated answer
  - Flag any mismatches
  - Adjust until exact

### 4b. **STRICT NUMERICAL PRECISION QC (NON-NEGOTIABLE)**
- **For every numerical answer:** Calculate result and check error against stated answer option
- **Acceptable error tolerance:**
  - Numerical/calculation problems: **< 1.0%** (e.g., 401 K vs 420 K answer is 4.7% error = **FAIL**)
  - Conceptual problems only: up to 5% if unavoidable
- **CRITICAL: All 20 answers must have at least one matching option within < 1% tolerance**
  - ❌ FAILURE CONDITION: Calculated answer = 20,396 W/m, nearest option = 4,494 W/m (78% error) — this is **NOT ACCEPTABLE**
  - ❌ FAILURE CONDITION: Calculated answer = 5.4 kmol/s, nearest option = 0.144 kmol/s (3700% error) — this is **NEVER ACCEPTABLE**
  - ❌ DO NOT accept "close enough"
  - ❌ DO NOT round to a nearby option
  - ✓ Adjust problem parameters (backward calculation) until exact match
  - ✓ Verify adjustment is physically realistic

### 4c. **ORDER-OF-MAGNITUDE SANITY CHECK (CRITICAL FILTER)**
- **If calculated answer is > 10× OR < 0.1× any answer option: STOP AND FIX**
  - ❌ Example: Calculated 5.4 (all options 0.036–0.144) = **150× error** → REPLACE PROBLEM
  - ❌ Example: Calculated 401 (all options 364–578) = **within range** → FIXABLE
  - ✓ This catches unit errors, formula errors, parameter mismatches instantly
- **Red flag checklist:**
  - Is calculated answer 10× larger than max option? → Likely wrong formula or units
  - Is calculated answer 0.1× smaller than min option? → Likely missing a scale factor
  - Do units match? (e.g., kmol/s vs mol/s, W vs kW, mm vs m)
  - Does the problem use a formula? Verify formula was applied correctly with given parameters

### 4d. **ANSWER KEY MUST SHOW CALCULATION, NOT ASSUMPTION**
- **NEVER write:** "Answer: C) 0.108 kmol/s (as stated in problem options)"
- **ALWAYS write:** "Calculate: X = [formula] × [values] = [exact result] = **C) 0.097 kmol/s** ✓"
- **If you write the answer key without showing the calculation, it's a red flag**
  - Missing calculation means you didn't verify it
  - This is how Q12 error slipped through (answer was assumed correct, not calculated)

### 4e. **IF CALCULATED ANSWER DOESN'T MATCH ANY OPTION WITHIN TOLERANCE:**
- Option 1: Work backward from answer option to adjust parameters
  - Example: Want answer = 4,494 W/m? Solve for k, or r_o/r_i, or ΔT that gives exactly this result
  - ✓ Shows math: "If answer = 4,494, then k = 2π × 150 / 4,494 × 0.6931 = 3.3 W/m·K"
- Option 2: Replace problem entirely with new geometry/scenario that yields exact answer
  - Example: Q12 had 5.4 kmol/s calculated → replaced with extraction column problem
  - ✓ New problem has exact calculated answer matching an option
- **Do NOT proceed until answer is exact**
- **If replacing: test the new problem independently before finalizing**
- **Additional checks for thermodynamic problems:**
  - ✓ Verify 2nd Law consistency (S_gen ≥ 0 for adiabatic processes)
  - ✓ Check physical realism: For compressors, T_actual ≥ T_isentropic (irreversibilities add heat)
  - ✓ Check physical realism: For turbines, h_actual ≤ h_isentropic (irreversibilities waste work)
  - ✓ Verify energy balances close properly
  - ✓ Verify no impossible state combinations (e.g., lower temp than isentropic in a compressor)

### 5. **REALISTIC PARAMETERS ONLY**
- Use physically/chemically sound values
- ❌ h = 0.001 W/m²·K (unrealistic convection coeff)
- ❌ k = 1000 W/m·K for insulation (unrealistic thermal conductivity)
- ✓ Use reference values: h ∈ [10–100], k ∈ [0.1–50] for typical materials

### 5b. **NO PROPERTY TABLE LOOKUPS REQUIRED**
- **CRITICAL RULE:** Never require students to look up values in steam tables, psychrometric charts, equilibrium tables, or other reference materials
- **Problem:** Different handbook editions have slightly different values → answer mismatches → confusion
- **Instead:** Provide all needed property values **directly in the problem statement**
  - ❌ WRONG: "Steam at 100 kPa enters the turbine. Find outlet entropy." (Requires steam table lookup)
  - ✓ RIGHT: "Steam at 100 kPa with s_f = 1.303, s_fg = 6.055 kJ/kg·K enters the turbine..." (All values given)
- **Exception:** Can reference handbook for *formulas/principles* (e.g., "refer to FE Handbook page 143 for isentropic process relations"), but not for numerical data lookups
- This ensures exact answers regardless of handbook edition used

### 6. **HANDBOOK MAPPING**
Reference the FE Handbook Table of Contents:
- **Page 143**: Thermodynamics
- **Page 181**: Fluid Mechanics
- **Page 209**: Heat Transfer
- **Page 243**: Chemical Engineering
- **Page 86**: Chemistry and Biology
- **Page 130**: Mechanics of Materials
- **Page 117**: Materials Science
- **Page 64**: Probability and Statistics

For each question, insert: `*Refer to FE Handbook page X (Topic) for [equation/principle name].*`

---

## Exam Structure

### Question Distribution (20 questions)
- **Thermodynamics**: 2–3 questions
- **Fluid Mechanics**: 2–3 questions
- **Heat Transfer**: 3 questions
- **Chemical Engineering** (reactions, kinetics, reactors): 3–4 questions
- **Mass Transfer/Separations**: 2 questions
- **Materials Science**: 1–2 questions
- **Chemistry/Biology**: 1 question
- **Probability/Statistics**: 1 question

### Difficulty
- Mix of **calculation-heavy** and **conceptual** questions
- Difficulty: **Medium** (representative of actual FE exam)
- Time target: **90–120 minutes** for 20 questions

### Question-Format Variety (MIX FROM THE START — do not bolt on at the end)
The real NCEES/Pearson exam is not all 4-option single-answer questions. **Weave alternative formats throughout the exam (~25–30% of questions), not as a separate appended section.** Reference example: [[03 Projects/FE Exam Prep/Sample Exam/NCEES Practice Exam - Transcribed.md]].
- **Matching / drag** ("Drag the correct … to each …") — e.g., unit op → property, agency → function, cycle → diagram
- **Select the TWO / THREE that apply** — multi-answer, common on the real exam
- **Figure-described** — describe a graph/diagram in words (controller response, packed-bed schematic, regression plot) since interactive figures can't be rendered
- **Fill-in-the-blank** (numeric entry) — occasionally, matching NCEES style
- **Breadth topics** the calc distribution omits: **ethics & professional practice, safety/regulatory agencies (OSHA/EPA/NRC/FDA), process control, patents.** At least 1–2 of these per exam.
- Numeric answers in any format still pass the full verification gates below. Conceptual/matching questions are checked against standard definitions.

---

## Quality Checklist

Before finalizing the exam:

- [ ] **Answer Verification**: All 20 answers run through PowerShell QC
- [ ] **Order-of-Magnitude Sanity Check**: Before detailed QC, scan all 20 answers for unit/formula errors
  - [ ] **RED FLAG:** Calculated answer is > 10× max option OR < 0.1× min option = **STOP, REPLACE PROBLEM**
    - [ ] Example: Q12 calculated 5.4 kmol/s but max option 0.144 (factor of 37) → replaced with new problem
    - [ ] Example: Q10 calculated 20,396 W/m but max option 5,618 (factor of 3.6) → replaced with new problem
  - [ ] **PASS:** Calculated answer is within 10× range of answer options (fixable by parameter adjustment)

- [ ] **Numerical Precision QC**: For every numerical answer, verify calculated result matches option to **< 1.0% error** (non-negotiable for calculation problems)
  - [ ] For Q1–20: **SHOW CALCULATION in answer key**, not just "answer is C)"
    - [ ] Format: "Calculate: N = [formula] × [values] = [result] = **option** ✓"
    - [ ] If you can't show the calculation, you didn't verify it
  - [ ] **CRITICAL CHECK:** Verify ALL 20 questions have at least ONE answer option within < 1% tolerance
    - [ ] If ANY question has no matching option within 1%: **FAIL** entire exam — do not finalize
  - [ ] If error > 1%: Adjust problem parameters backward and recalculate until exact match
  - [ ] Example fix: If Q15 calculates to 0.0597 s⁻¹ but answer is 0.046 s⁻¹ (29.8% error), solve for Ea that gives exactly 0.046
- [ ] **Calculation Verification**: Transcendental functions (powers, logs, exponentials) double-checked independently
- [ ] **Physical Reasonableness**: All problem scenarios satisfy thermodynamic/engineering constraints
  - [ ] Compressors: T_actual ≥ T_isentropic
  - [ ] Turbines: h_actual ≤ h_isentropic (or s_actual ≥ s_isentropic)
  - [ ] All adiabatic processes: S_gen ≥ 0
  - [ ] No impossible state combinations
- [ ] **Equation Hiding**: No equation shown in problem; instead reference handbook page
- [ ] **Parameter Realism**: All values are physically/chemically plausible
- [ ] **Coverage**: Questions span multiple topics across ChemE curriculum
- [ ] **Answer Variety**: Options A, B, C, D are roughly evenly distributed across the 20 questions
- [ ] **Handbook Mapped**: Every question references FE Handbook page number
- [ ] **⛔ FINAL GATE — Option Existence Check**: (LAST action before saving) Recompute every answer from the PRINTED problem in a clean pass, confirm the key's stated letter points to an option equal to that value, and confirm the true answer exists among the four options. Paste the verification table into the key. **No exam is saved until this passes for all 20.** (See "FINAL ACTION: Option Existence Check" section.)

---

## Development Workflow

1. **Draft questions** with realistic parameters
2. **Calculate answers** using PowerShell or manual calc
3. **Check for exact matches** to answer options
4. **If not exact**: Adjust problem parameters (backward calculation) until exact
5. **Replace equations with handbook refs** (remove all formula text)
6. **Run full QC check** on all 20 answers
7. **Flag any mismatches** and re-adjust
8. **Finalize** when all answers are exact
9. **FINAL GATE — Option Existence Check (MANDATORY, see below)**

---

## FINAL ACTION: Option Existence Check (MANDATORY — DO NOT SKIP)

**The last thing done before saving ANY exam.** This is a non-negotiable gate. An exam is NOT finished until this passes for all 20 questions.

### The rule
> **For every question, the letter stated in the answer key MUST point to an option whose printed value equals the freshly-recomputed answer within tolerance. Recompute from the PROBLEM AS PRINTED — never from a "fixed" version that only exists in the answer-key prose.**

### Why this exists (the failure this catches)
The single most damaging bug pattern: writing a **"BACKWARD FIX: change parameter X"** note inside the answer key **but never editing the actual problem statement or option list.** The printed problem then computes to one value, the key claims another, and often the claimed answer isn't even among the four options. Example failures caught in Session #3 (12 of 20 questions were wrong this way):
- Q7: printed problem → 9,196 W; key claimed C) 19,500 W (unapplied "L₁ change"). No option matched the real answer.
- Q8: printed problem → −0.12 K/s; key claimed B) −0.0225 (unapplied "h change"). Real answer wasn't an option at all.
- Q13: printed problem → 1.047 M; key claimed A) 0.72 (unapplied "Q change").

**A "backward fix" is only real when it edits the printed problem or the printed option. If it lives only in the answer-key text, it does not exist.**

### The procedure (run in a single fresh PowerShell pass)
1. For each question, read the **numbers actually printed in the problem statement** (not the key's prose).
2. Recompute the answer from those printed numbers.
3. Read the **four printed option values** (A/B/C/D) exactly as they appear.
4. Confirm the recomputed answer matches the option whose letter the key states, within tolerance (calculation ≤1%, conceptual ≤5%).
5. Confirm that at least one option exists within tolerance (catches "answer not in options at all").
6. **If ANY question fails: do not save.** Either edit the printed problem parameter or edit the printed option value so the two agree, then re-run this entire pass from scratch.

### Pass criteria (ALL must be true)
- [ ] Every stated answer letter maps to an option value equal to the recomputed answer (within tolerance).
- [ ] No question relies on a parameter/value that appears only in the answer key and not in the printed problem/options.
- [ ] Every question has at least one option within tolerance of the true computed answer.
- [ ] The recompute was done from the printed problem, in a clean calculation pass, at the very end (after all edits).

**Output of this gate:** a verification table (Q | recomputed value | matched option | % error) pasted into the answer key. If you cannot produce that table, the gate has not been run.

---

## Example: Fixing a Mismatched Question

**Problem as drafted:**
- A sphere (D=0.2m) at 100°C, h=60 W/m²·K, ΔT=80K
- Calculated Q = 603 W
- Answer options: A) 480, B) 600, C) 720, D) 960
- **Issue**: 603 ≠ any option exactly

**Fix (backward calculation):**
- Want Q = 804 W (option C, more realistic)
- Current: Q = h × 4πr² × ΔT = 60 × 0.1257 × 80 = 603
- Solve for h: 804 = h × 0.1257 × 80 → h = 80 W/m²·K
- **Result**: Change h from 60 to 80 → now gives exactly 804 W ✓

---

## Anti-Patterns (What NOT to Do)

| Anti-Pattern | Why It Fails | Fix |
|---|---|---|
| Write equation in problem | User doesn't learn to find formula in handbook | Reference handbook page instead |
| Accept "close" answers (603 vs 600) | Precision matters on real exam; encourages sloppy thinking | Adjust parameters until exact |
| Use unrealistic parameters | Fails credibility; user suspects error | Use reference values from industry |
| Skip QC verification | Missed bugs become exam-breaking | Run full PowerShell QC every time |
| **"Backward fix" written in key but never applied to the problem** | Printed problem computes to a different value than the key claims; often the true answer isn't even an option | Every fix MUST edit the printed problem parameter or the printed option value. Run the **Option Existence Check** final gate. |
| **Stated answer letter points to a value the problem doesn't produce** | Student computes the right answer, finds it's not option they were told — loses trust in the whole exam | Recompute from the PRINTED problem at the very end; confirm the answer exists among the four options |
| 4 questions on same topic | Unbalanced coverage | Distribute across multiple areas |
| **Thermodynamically impossible scenarios** | Violates 2nd law, confuses student on fundamental concepts | Verify S_gen ≥ 0; verify compressor T_actual > T_isentropic; verify turbine h_actual < h_isentropic |
| **Trust mental math for transcendental functions** | Easy to miscompute (5^0.2857 ≠ 1.278; correct is 1.5835). Can create wrong answer by factor of 1.2x+ | Always use PowerShell/calculator for powers, logs, exponentials. Verify result is physically plausible. |

---

## Special Topic: Transient Conduction Problems (Heat Transfer)

Transient conduction is a common FE topic. **Two valid approaches:**

### Approach A: One-Term Approximation (RECOMMENDED)
- **Method**: Use Biot number (Bi = hL/k) and one-term approximation series solution
- **Formula provided**: (T − Ti)/(T∞ − Ti) = C₁·exp(−ζ₁²·Fo)
- **Critical**: Provide ζ₁ and C₁ coefficients DIRECTLY in problem (don't require table lookup)
- **Why**: Mirrors actual FE exam; students learn Biot number concept; tests exponential decay understanding
- **How to implement**:
  1. Choose problem geometry (plane wall, infinite cylinder, sphere)
  2. Calculate Bi = hL/k from given values
  3. Find corresponding ζ₁, C₁ from handbook table
  4. **Provide both ζ₁ and C₁ in problem statement** (not in answer key)
  5. Have student calculate Fo = αt/L², apply formula, get exact numerical answer
- **Reference**: Consult [[05 Skills/FE Transient Conduction Q9 Alternatives.md]] for example

### Approach B: Analytical Closed-Form Solution (ALTERNATIVE)
- **Method**: Provide explicit temperature function T(x,t); ask student to take ∂T/∂t
- **Formula provided**: T(x,t) = ... explicit equation with exponential and trig functions
- **Advantage**: No table lookups; pure calculus; tests derivative understanding
- **Disadvantage**: Less realistic to actual FE exam
- **When to use**: For variety, or when testing calculus skills specifically
- **How to implement**:
  1. Create a realistic temperature function (usually separable: time × spatial part)
  2. Ask for ∂T/∂t or ∂T/∂x (partial derivatives)
  3. Provide exact position and time; student calculates result
  4. Answer must be exact (< 1% error)
- **Reference**: Consult [[05 Skills/FE Transient Conduction Q9 Alternatives.md]] for example

**Rule**: If your exam includes transient conduction, use Approach A (one-term approximation) with coefficients provided. It's higher-fidelity to the actual FE exam.

---

## When Done

- Save the exam to: `03 Projects/FE Exam Prep/[Descriptive Name].md`
- Add a note in `[[CLAUDE.md]]` pointing to the new exam (optional, if user wants inventory)
- User runs the exam and reports which questions they struggled with
- For those questions, I reference this protocol to either fix the problem or create targeted drills

---

## Lessons Learned: Q11-Q20 Full Revision Checklist

**Common errors caught during full exam QC:**
1. **Inconsistent problem setup** (Q11): Problem gave y_actual = 0.65 but y_eq = 0.82 → impossible. Fixed by specifying y_in, y_out directly.
2. **Missing answer keys** (Q12): No answer provided. Calculated from formula and matched to option.
3. **Wrong rate constant** (Q14): k = 0.15 min⁻¹ gave 1.45 M, no option match. Backward-calc: k = 0.50 min⁻¹ gives 0.89 M exactly.
4. **Wrong activation energy** (Q15): Ea = 35 kJ/mol gave k = 0.0597 s⁻¹ (29.8% error from 0.046). Backward-calc: Ea = 26.6 kJ/mol gives exactly 0.046 s⁻¹.
5. **Wrong stoichiometry** (Q20): A → 2B gave equilibrium [A] = 2.0 kmol/m³ (not matching any option). Changed to A ⇌ B (first-order) → [A]_eq = 0.80 kmol/m³.
6. **Wrong answer option** (Q18): Calculated 0.0595 mm but option was 0.024 mm (148% error). Changed option to 0.060 mm.

**Prevention:** When QC reveals no match within 1%, ALWAYS:
- ✓ Recalculate independently (often catches transcription errors)
- ✓ Check problem stoichiometry/setup (often wrong, not calculation)
- ✓ Work backward from answer option to find correct parameters
- ✓ DO NOT force a wrong answer into an option
- ✓ **After every edit, re-run the Option Existence Check final gate — an unapplied "backward fix" is the #1 way a broken answer ships**

---

## Lessons Learned: Session #3 — The Unapplied-Fix Failure

**What happened:** 12 of 20 questions shipped with wrong answer keys. Root cause was uniform: the answer key contained "BACKWARD FIX: change parameter X" prose, but the change was **never applied to the printed problem or option list**. The printed problems computed to different values than the key claimed, and several true answers were not among the four options at all (e.g., printed Q8 → −0.12 K/s, but options ranged −0.0075 to −0.09).

**The fix that prevents recurrence:** the mandatory **FINAL ACTION: Option Existence Check** — recompute every answer from the PRINTED problem in a clean final pass, and confirm the stated answer letter maps to an option holding that value. A fix that lives only in answer-key prose does not exist.

**Last Updated**: July 13, 2026
**Protocol Status**: Finalized with transient conduction guidance, strict < 1% numerical precision QC, no handbook lookups, Q11-20 full revision checklist, **and mandatory Option Existence Check final gate (Session #3 lesson)**
