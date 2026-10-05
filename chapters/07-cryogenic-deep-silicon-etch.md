# Chapter 7: Cryogenic Deep Silicon Etch

## Overview

Cryogenic silicon etch was developed for MEMS: SF₆ and O₂ at −100 °C or below, etching silicon at several micrometres per minute with nearly vertical walls and selectivity to oxide in the hundreds. Its appeal for the deep trench is plain from Chapter 4: DT-R2 reaches 5 µm in 2.5 minutes against 5.7 for R1, with weaker ARDE and a fifth of the mask loss. Its costs are less obvious and mostly thermal. This chapter explains the mechanism, the process window, and the defects that make cryogenic etch a niche rather than a replacement.

**Learning Objectives:**
- Explain the SiOₓFᵧ passivation mechanism and its temperature dependence
- Estimate the wafer-temperature uniformity DT-R2 requires
- Predict the effect of O₂/SF₆ ratio and temperature on profile and black silicon
- Compare DT-R2 with DT-R1 on rate, CD sensitivity, mask, defects, and cost

---

## 7.1 Mechanism

### 7.1.1 The Film That Evaporates

```
At −100 °C, with O₂/SF₆ ≈ 8%:
  F etches Si at the bottom, assisted by ions (≈ 120 eV)
  On the walls, O and F co-adsorb with Si to form SiOₓFᵧ, ≈ 1–2 nm,
  stable only while T < ≈ −80 °C
  On warm-up to room temperature the film desorbs; no clean is needed
```

The film does not need etch products from the bottom: it forms from the gas phase on any cold silicon surface. That is the decisive difference from R1. The film is nearly uniform with depth, so the profile is nearly independent of depth, and the trench bottom is not starved of the film's ingredients in the way R1's is.

### 7.1.2 Spontaneous Etch Suppression

```
Flamm rate ratio, 173 K vs 333 K at the same n_F:
  (173/333)^½ × exp(−1250/173) / exp(−1250/333)
  = 0.721 × 7.3×10⁻⁴ / 0.0234 = 0.022
```

The unprotected lateral fluorine rate falls about forty-five-fold. Even where the film is thin, the wall barely etches.

---

## 7.2 The Window

### 7.2.1 Temperature and O₂

```
DT-R2 profile map (illustrative, 5 µm trench, 70 nm top CD):

  O₂/SF₆      −80 °C          −100 °C          −115 °C
  ─────────────────────────────────────────────────────────────
  5%          bow 12 nm,      bow 6 nm,        straight; grass
              undercut        slight undercut  at edges
  8%          bow 5 nm        straight         taper; black Si
                              (reference)      in open areas
  11%         straight;       taper;           black Si; etch
              rough           black Si risk    stop in trench
```

A change of 15 °C moves the profile as much as a change of 3 points in the O₂ ratio. **Temperature is a process gas.**

### 7.2.2 Temperature Uniformity

```
Profile sensitivity at the reference point (illustrative):
  ∂(bottom CD)/∂T ≈ +0.6 nm/°C
  ∂(bow)/∂T       ≈ +0.4 nm/°C

Specification bottom CD ≥ 40 nm with nominal 50 nm, of which the
temperature may use ±3 nm (3σ) → wafer temperature uniformity ±5 °C
including drift; ±1 °C from the chuck design to leave room for
  He leak variation (±1–2 °C)
  backside film variation (±1 °C)
  lot-to-lot chuck drift (±1 °C)
```

### 7.2.3 Heat Removal

```
Heat load: J_i × E = 3.0×10⁻³ × 120 = 0.36 W/cm² → 0.25 kW from ions
  plus ≈ 0.35 kW from the source → ≈ 0.6 kW, 0.85 W/cm²
With He at 10 Torr (h ≈ 0.05 W/cm²·K): ΔT ≈ 17 K wafer above chuck
```

The wafer runs about 17 °C above the chuck. A 10% change in the He conductance moves the wafer by 1.7 °C, which is a third of the temperature budget. The He leak rate becomes a hard interlock.

---

## 7.3 Rate, ARDE, and Sensitivity

```
                          DT-R1           DT-R2
  ─────────────────────────────────────────────────────
  ER₀ (nm/min)            1600            3000
  k (w̄ = 60 nm)           0.020           0.012
  Bottom ER/ER₀ at 5 µm   0.375           0.50
  Time to 5 µm (min)      5.73            2.50
  ∂h/∂w (nm/nm)           26.0            20.8
  BSG loss in main etch   500 nm          125 nm
  Ion energy (eV)         450             120
```

Weaker ARDE comes from two effects. Fluorine at −100 °C has a lower reaction probability at the bottom, so it is less depleted down the trench; and the film forms without needing the products of the bottom, so the bottom keeps a balance close to that of the top. The CD sensitivity falls 20%, a direct gain in the depth budget.

---

## 7.4 Defects

### 7.4.1 Black Silicon

Black silicon is a forest of needles formed where micromasks — film islands, particles, residues — protect points of the surface while the surrounding silicon etches. At cryogenic temperature, excess O₂ or excess cooling grows the passivating film on the bottom faster than the low-energy ions can remove it; any spot where it nucleates early becomes a needle. In the array, black silicon appears as grass at the trench bottom; in open areas such as alignment marks, as a black haze.

```
Black-silicon onset (illustrative): O₂/SF₆ ≥ 10% at −100 °C, or
  wafer T ≤ −110 °C at 8%
Mitigation: 20 s high-bias clearing step every 40 s; reduce O₂ near
  the end; keep alignment-mark areas covered
```

### 7.4.2 Mask and Film Stress

```
CTE mismatch: Si 2.6 ppm/K, BSG ≈ 3–4 ppm/K, SiN ≈ 3.3 ppm/K
ΔT room → −100 °C: 125 K
Thermal mismatch strain in BSG: ≈ (3.5 − 2.6) × 10⁻⁶ × 125 ≈ 1.1×10⁻⁴
  × E_BSG (≈ 60 GPa) ≈ 7 MPa — small
```

The steady-state stress is small. The damage comes from the transients: wafers cooled in seconds on the chuck develop radial gradients, and a film already under 300 MPa of deposition stress can crack at defects. Pre-cooling in the load lock and slow ramps eliminate most mask cracks.

### 7.4.3 Condensation

A wafer leaving the chamber at −80 °C into an atmosphere containing a few ppm of water will grow ice and later form water spots or HF from residual fluorine. The warm-up station heats the wafer to above 20 °C under dry N₂ before it reaches the transfer module.

---

## 7.5 When Cryogenic Etch Wins

```
  Criterion                     Favours R1          Favours R2
  ───────────────────────────────────────────────────────────────────────
  Throughput                                        2.3× faster
  Mask budget, deeper trench                        5× less BSG loss
  CD-to-depth sensitivity                           20% lower
  Profile stability with                            film independent of
   chamber aging                                    wall state
  Temperature control           +60 °C, ±2 °C easy  −100 °C, ±1 °C hard
  Defects                       grass manageable    black Si, cracks,
                                                    condensation
  Installed base and know-how   decades of TCP      fewer production
                                trench etch         references
  Integration with bottle,      reference           wall chemistry differs;
   collar                                           post-clean differs
```

Cryogenic etch wins where the trench must be deeper than the R1 mask budget allows, or where throughput dominates cost. For silicon trench capacitors with depths of 10–30 µm and wide features (Chapter 14), cryogenic or Bosch-type etch is the norm. For the 70 nm eDRAM trench, R1 remains the reference.

---

## Summary and Key Takeaways

1. **The film forms from the gas.** SiOₓFᵧ grows on any cold surface and evaporates on warm-up; it does not depend on products from the bottom.

2. **Lateral fluorine etch falls about forty-five-fold.** At −100 °C even a thin film protects the wall.

3. **Temperature is a process gas.** A 15 °C change moves the profile like 3 points of O₂; the wafer must hold ±1 °C from the chuck.

4. **Faster, weaker ARDE, less mask loss.** 2.5 min, k = 0.012, 125 nm of BSG.

5. **Black silicon and thermal transients.** The window is bounded by needles on one side and undercut on the other.

---

## Study Questions

1. Compute the Flamm-rate ratio between −120 °C and +60 °C.

2. The He conductance falls 15%. Estimate the change in wafer temperature and in bottom CD for DT-R2.

3. Using the table in 7.3, compute the depth range at fixed time for a top-CD range of ±3 nm in R1 and R2.

4. Explain why black silicon appears first in open areas and only later at the bottom of the trench.

5. A trench must deepen to 7 µm. Estimate the BSG needed for R1 and for R2 and the etch time of each.

---

**Next Chapter:** [Chapter 8: Depth-Adaptive & Multi-Step Recipes](./08-depth-adaptive-multistep-recipes.md)

---

**Chapter 7 Development Status:** Complete  
**Version:** 1.0
