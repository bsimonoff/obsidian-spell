# FE Transient Conduction Problems (Q9 Alternatives)

**Cross-reference**: See [[CLAUDE.md]] → "FE Practice Exam Creation" section. This document supports the protocol guidance in [[05 Skills/FE Practice Exam Development Protocol.md]].

## Background
Transient conduction problems commonly appear on the FE exam. Two main approaches:
1. **One-term approximation** (most common on FE) — requires Biot number and table lookup, but coefficients CAN be provided directly
2. **Analytical/closed-form solution** — requires direct derivative/calculus understanding, no table lookups

---

## OPTION A: One-Term Approximation (RECOMMENDED FOR FE)

**Q9. [DERIVATIVES REQUIRED]** A plane wall slab (thickness L = 0.1 m, thermal conductivity k = 10 W/m·K, thermal diffusivity α = 1.0 × 10⁻⁶ m²/s) is initially at 20°C. The surface is suddenly exposed to a fluid at 120°C with convection coefficient h = 100 W/m²·K. Using the one-term approximation for transient conduction, find the temperature at the center of the slab after t = 10,000 seconds.

*Refer to FE Handbook page 209 (Heat Transfer) for one-term approximation: (T − Ti)/(T∞ − Ti) = C₁·exp(−ζ₁²·Fo), where Fo = α·t/L² and Bi = h·L/k. Given for this problem: Bi = 1.0, ζ₁ = 0.8603, C₁ = 1.1191.*

A) 52°C  
B) 64°C  
C) 73°C  
D) 85°C

**Answer: C) 73°C**

Calculation:
- Bi = h·L/k = 100 × 0.1 / 10 = 1.0 ✓
- Fo = α·t/L² = 1.0×10⁻⁶ × 10,000 / (0.1)² = 1.0 ✓
- θ = C₁·exp(−ζ₁²·Fo) = 1.1191 × exp(−0.8603² × 1.0)
- θ = 1.1191 × exp(−0.7401) = 1.1191 × 0.4771 = 0.5339
- T = Ti + θ(T∞ − Ti) = 20 + 0.5339(120 − 20) = 20 + 53.39 = **73.39°C** ✓

**Why Option A for FE:** This mirrors the actual FE exam approach. Students learn to:
1. Calculate Bi (non-negotiable step)
2. Look up/use ζ₁ and C₁ (provided to avoid handbook variance)
3. Calculate Fo (dimensionless time)
4. Apply exponential decay relationship (derivative/calculus concept)

---

## OPTION B: Analytical Solution with Explicit Temperature Function

**Q9. [DERIVATIVES REQUIRED - ALTERNATIVE]** A one-dimensional transient temperature distribution in a solid is given by the analytical solution:

T(x,t) = 20 + 80·exp(−t/1000)·sin(πx/0.2)

where x is position (m), t is time (s). At the center of the domain (x = 0.1 m) and at t = 500 s, what is the rate of temperature change dT/dt (in °C/s)?

*Refer to FE Handbook page 209 (Heat Transfer) for transient conduction fundamentals. This problem tests understanding of partial derivatives: ∂T/∂t = (rate of temperature change with time).*

A) −0.049 °C/s  
B) −0.032 °C/s  
C) +0.018 °C/s  
D) +0.042 °C/s

**Answer: A) −0.049 °C/s**

Calculation:
- Given: T(x,t) = 20 + 80·exp(−t/1000)·sin(πx/0.2)
- Take partial derivative with respect to time:
  - ∂T/∂t = 80 × (−1/1000) × exp(−t/1000) × sin(πx/0.2)
  - ∂T/∂t = −0.08 × exp(−t/1000) × sin(πx/0.2)
- At x = 0.1 m, t = 500 s:
  - sin(π × 0.1 / 0.2) = sin(π/2) = 1.0
  - exp(−500/1000) = exp(−0.5) = 0.6065
  - ∂T/∂t = −0.08 × 0.6065 × 1.0 = −0.04852 °C/s ≈ **−0.049 °C/s** ✓
- Negative sign indicates cooling (temperature decreasing over time due to decay)

**Why Option B for variety:** This approach:
1. Doesn't require table lookups at all
2. Tests explicit derivative calculation (calculus-heavy)
3. Requires understanding of sin() and exp() functions
4. More suitable for students comfortable with calculus
5. Teaches the physical meaning of ∂T/∂t (rate of change with time)

---

## When to Use Each Approach

| Approach | When to Use | Advantages | Disadvantages |
|---|---|---|---|
| **Option A (One-term)** | Standard FE exam prep | Mirrors real FE; uses Biot number; common industrial method | Requires table interpretation (mitigated by providing coefficients) |
| **Option B (Analytical)** | Students weak on derivatives | Forces calculus practice; no tables; explicit function manipulation | Less realistic to actual FE exam; requires more algebra |

**Recommendation for job-search exam prep:** Use **Option A**. It's what you'll see on test day.

---

**Last Updated:** July 2026
