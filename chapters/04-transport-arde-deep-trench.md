# Chapter 4: Transport & ARDE in Deep Silicon Trenches

## Overview

The deep trench etches fast at the start and slowly at the end. At 5 µm the bottom of the reference trench etches at 37% of the rate of a wide-open feature, and the last micrometre takes almost as long as the first three. Because there is no etch stop, this slowing is not merely a cost in time. It is the mechanism by which every nanometre of CD error becomes 26 nm of depth error.

This chapter follows ions and neutrals to the bottom of an 83:1 silicon trench, derives the time-to-depth relation used throughout the book, computes the CD-to-depth sensitivity, and asks how deep the trench can go.

**Learning Objectives:**
- Estimate the ion acceptance cone and the ion flux at the bottom of the reference trench
- Explain why charging is weaker in a silicon trench than in an oxide hole
- Apply Clausing and Coburn–Winters transport to Br, F, and O
- Integrate ER = ER₀/(1 + kA) to obtain the time to depth and the CD sensitivity
- Identify the limits on maximum depth

---

## 4.1 Ions

### 4.1.1 Energy and Angle

```
DT-R1 sheath (illustrative): 2 MHz bias, V_pp ≈ 1.2 kV, ⟨E_i⟩ ≈ 450 eV
  Bimodal IED: peaks near 150 and 750 eV
Collisionless angular spread: θ ≈ √(T_i⊥/E_i), T_i⊥ ≈ 0.05 eV
  At 450 eV: √(1.1×10⁻⁴) = 0.0105 rad = 0.60°

Collisions at 30 mTorr (HBr-dominated, 330 K):
  n = 4.0 Pa / (1.38×10⁻²³ × 330) = 8.8×10²⁰ m⁻³
  σ ≈ 4×10⁻¹⁹ m² → λ = 1/(nσ) ≈ 2.8 mm
  Sheath thickness (ICP, n_e ≈ 5×10¹⁷ m⁻³, ≈ 600 V): s ≈ 0.9 mm
  s/λ ≈ 0.32 → collisionless fraction exp(−0.32) ≈ 0.73
```

The high-density ICP sheath is thin, so most ions cross it without collision even at 30 mTorr. The low-energy peak of the bimodal distribution is the main source of angular spread: at 150 eV the collisionless spread is already 1.0°.

### 4.1.2 Acceptance

```
  Point in the etch         h_mask+pad   h (Si)   h_tot    w     arctan(w/h_tot)
                            (nm)         (nm)     (nm)     (nm)  edge to edge
  ───────────────────────────────────────────────────────────────────────────
  Start of main etch          955            0      955     70       4.2°
  1 µm                        895         1000     1895     67       2.0°
  2.5 µm                      755         2500     3255     60       1.06°
  End (5 µm)                  455         5000     5455     50       0.53° at the
                                                                    bottom CD
```

The cone at the end, 0.5°, is comparable to the collisionless spread of the high-energy ions and narrower than that of the low-energy ones. The trench, like the oxide hole of Book #31, relies on grazing specular reflection from the sidewall to bring ions to the bottom. Unlike the oxide hole, the silicon wall is covered by a film only 1–5 nm thick, and the wall itself is crystalline and smooth. Reflection is efficient as long as the wall is straight.

### 4.1.3 Ion Flux at the Bottom

```
Fraction of ions reaching the bottom (Monte Carlo with specular reflection,
illustrative, mixed population):

  Total A (h_tot/w)    20     40     60     83     100    120
  Γ_i,bot / Γ_i,top   0.78   0.69   0.63   0.58   0.55   0.52
```

From the start of the etch to its end, the bottom ion flux falls by little more than a third. As in Book #31, **ions alone do not explain ARDE.** The bottom rate falls to 37%; the ion flux falls only to 58%.

---

## 4.2 Charging

Charging is the reason twist dominates the oxide capacitor hole (Book #31, Chapter 11). In the silicon trench it is much weaker:

```
  Surface            Conduction path                  Bottom potential
                                                      (illustrative)
  ──────────────────────────────────────────────────────────────────────
  Oxide hole wall    surface leakage through polymer   100–400 V (CW bias)
  Si trench wall     1–5 nm film over p-Si; tunnelling 1–10 V
                     and defect leakage to the
                     grounded substrate
  BSG mask           insulating                         charges as in an
                                                        oxide hole
```

The silicon substrate is connected to the chuck through the backside. Charge deposited on the bottom flows away through the silicon. The mask, however, is an insulator and its sidewalls charge negative. The resulting field deflects low-energy ions in the top 1 µm of the trench, which is one source of upper-wall bow and of the occasional local twist (Chapter 11). A thicker sidewall film, as in an over-passivated recipe, insulates the wall and raises charging.

---

## 4.3 Neutrals

### 4.3.1 Molecular Flow

```
Mean free path at 30 mTorr: ≈ 2 mm ≫ 60 nm → Knudsen number ≈ 3×10⁴
Transport in the trench is free-molecular: molecules travel wall to wall.
```

### 4.3.2 Coburn–Winters

For a reactant with reaction probability s at the bottom, and specular-free (diffuse) wall reflection with wall sticking s_w ≈ 0:

```
Γ_bot / Γ_top ≈ 1 / (1 + (3/4) · s · A)     (long-tube approximation)

Per-species estimates at A = 83 (illustrative reaction probabilities):

  Species   s at bottom   Γ_bot/Γ_top   Comment
  ──────────────────────────────────────────────────────────────
  F         0.05          0.24          etches spontaneously
  Br        0.02          0.44          needs ions
  O         0.10          0.14          consumed on walls too
                                        (s_w ≈ 0.01) → ≈ 0.10
  SiBrₓ     ≈ 0.3 walls   —             product; leaves with
                                        repeated sticking
```

The bottom of the trench is starved of F more than of Br and of O more than of either. This matters in two directions. Less F slows the bottom. Less O thins the film at the bottom, which is why the lower trench stays clean while the upper trench tapers when O₂ is high.

### 4.3.3 The Lumped ARDE Coefficient

Fitting measured depth against time for R1 gives a single effective coefficient:

```
ER(A) = ER₀ / (1 + kA)
  DT-R1: ER₀ = 1600 nm/min, k = 0.020 (w̄ = 60 nm)
  DT-R2: ER₀ = 3000 nm/min, k = 0.012
  Equivalent effective reaction probability: s_eff = (4/3)k
    R1: 0.027;  R2: 0.016
```

---

## 4.4 Time to Depth

### 4.4.1 Integration

```
dh/dt = ER₀ / (1 + k h/w)
→ ER₀ t = h + k h² / (2w)
→ t(h) = [h + k h²/(2w)] / ER₀
```

### 4.4.2 DT-R1

```
  h (µm)   A = h/60   ER/ER₀    t (min)    Δt for the last µm
  ─────────────────────────────────────────────────────────────
  1         16.7       0.75      0.73        0.73
  2         33.3       0.60      1.67        0.94
  3         50.0       0.50      2.81        1.15
  4         66.7       0.43      4.17        1.35
  5         83.3       0.375     5.73        1.56
  6        100.0       0.33      7.50        1.77
  7        116.7       0.30      9.48        1.98
```

The fifth micrometre takes 1.56 minutes; the first takes 0.73. The average rate over 5 µm is 5000/5.73 = 873 nm/min, 55% of ER₀.

### 4.4.3 DT-R2

```
  h = 5 µm: t = [5000 + 0.012 × 25×10⁶ / 120] / 3000 = 7500/3000 = 2.50 min
  ER/ER₀ at the bottom: 1/(1 + 1.0) = 0.50
```

---

## 4.5 CD Becomes Depth

At fixed etch time, a narrower trench etches shallower:

```
From ER₀ t = h + k h²/(2w), differentiating at constant t:
  ∂h/∂w = (k A² / 2) / (1 + k A)

DT-R1 at A = 83.3: (0.020 × 6944 / 2) / 2.667 = 69.4 / 2.667 = 26.0 nm/nm
DT-R2 at A = 83.3: (0.012 × 6944 / 2) / 2.000 = 41.7 / 2.000 = 20.8 nm/nm
```

```
Consequences (R1):
  Top-CD 3σ ±3 nm → depth ±78 nm   (65% of the ±0.12 µm allowance)
  2 nm radial CD signature → 52 nm radial depth signature
  A trench 12 nm narrower at the bottom of the litho distribution
    → 312 nm shallower → 1.8 fF less → 18.8 fF, fails 19.0 fF
```

The sensitivity grows faster than the aspect ratio. A process designed at 6 µm (A = 100) would have ∂h/∂w = (0.02 × 10⁴/2)/3 = 33 nm/nm.

---

## 4.6 How Deep Can It Go?

```
Limits on depth for R1 with the reference stack (illustrative):

  Limit                          Depth        Reason
  ────────────────────────────────────────────────────────────────
  Hard mask (BSG 900)            6.5 µm       Chapter 2
  CD-to-depth sensitivity        ≈ 6.5 µm     ∂h/∂w > 33 nm/nm makes
                                              the ±0.12 µm spec
                                              unreachable with ±3 nm CD
  Throughput                     ≈ 7 µm       > 9.5 min per wafer
  Bottom rate vs. film growth    > 10 µm      at A > 150 the bottom
                                              film balance tips to
                                              etch stop (Chapter 12)
```

The trench is limited by the mask and by variability long before it is limited by the physics of the bottom. This is the reverse of the oxide capacitor hole at 91:1, where the bottom chemistry is the hard wall. It is why the trench cell turned to the bottle for capacitance rather than to depth.

---

## Summary and Key Takeaways

1. **The cone closes to 0.5°.** Ions arrive by grazing reflection from a smooth silicon wall.

2. **Silicon bleeds charge.** Bottom potentials are a few volts; the insulating mask, not the trench, charges.

3. **Ions do not set ARDE.** The bottom ion flux falls to 58%; the rate falls to 37%, because F and O are starved at the bottom.

4. **t = [h + kh²/(2w)]/ER₀.** R1 reaches 5 µm in 5.73 min; R2 in 2.50 min.

5. **26 nm per nm.** At fixed time, CD variation becomes depth variation; this is the dominant term in the depth budget.

6. **Variability limits depth first.** The mask and the CD sensitivity stop R1 near 6.5 µm.

---

## Study Questions

1. Compute the R1 time to 5.5 µm and the ER/ER₀ at that depth.

2. A new ICP source raises ER₀ to 1900 nm/min but k rises to 0.024. Is the 5 µm etch faster or slower? What happens to ∂h/∂w?

3. Using Coburn–Winters, compute Γ_bot/Γ_top for F at A = 50 and A = 120 with s = 0.05.

4. Explain why a thicker sidewall film can raise charging in a silicon trench.

5. Using ∂h/∂w, find the largest top-CD 3σ that allows the ±0.12 µm depth spec if 40% of the depth variance is reserved for other sources.

---

**Next Chapter:** [Chapter 5: Etch Platforms for Deep Silicon Trenches](./05-deep-trench-etch-platforms.md)

---

**Chapter 4 Development Status:** Complete  
**Version:** 1.0
