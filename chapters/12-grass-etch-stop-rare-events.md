# Chapter 12: Silicon Grass, Etch Stop & Rare Events

## Overview

Most trenches in a wafer look alike. The yield is decided by the few that do not: a trench that stopped at 3 µm, a trench whose bottom grew a needle of silicon, a trench blocked at the top by a particle. With about a billion trenches per die, events at 10⁻⁹ per trench decide whether a die needs repair. This chapter covers the defects that make individual trenches fail — grass, micromasking, etch stop, blocked and shallow trenches — and the statistics needed to measure and control rates far below what any inspection can see directly.

**Learning Objectives:**
- Explain how micromasking forms silicon grass and where it originates
- Describe the conditions for etch stop in a deep silicon trench
- Relate shallow and missing trenches to capacitance failures
- Estimate the defect rates required at a billion trenches per die
- Design monitors that see rates of 10⁻⁹

---

## 12.1 Grass and Micromasking

### 12.1.1 Mechanism

A micromask is any small patch on the etch front that etches more slowly than silicon: a speck of SiOₓBrᵧ redeposited on the bottom, an oxide residue left by the mask open, a fragment of BSG or of chamber coating, a particle of Al₂O₃ or Y₂O₃. Silicon around it etches away; silicon beneath it survives and becomes a pillar. If the micromask lasts, the pillar grows with the etch; if it is undercut, the pillar becomes a needle and may break off.

```
Needle height if the micromask survives from depth z_m to the end:
  h_needle ≈ (H − z_m) × (1 − 1/S_m)    S_m = Si:micromask selectivity

  SiOₓBrᵧ speck (S ≈ 10) formed at 4 µm: ≈ 0.9 µm
  Al₂O₃ particle (S ≈ 200) on the mouth at 0 µm: the trench below it
    never etches (blocked trench)
```

### 12.1.2 Where It Comes From in R1

```
  Origin                                 Controlled by
  ─────────────────────────────────────────────────────────────────────
  Mask-open residue at the trench        breakthrough step (Chapter 2.5)
   mouth
  SiOₓBrᵧ redeposition on the bottom     O₂ ≤ 20 sccm in ME3; NF₃ ≥ 30;
   when the bottom film balance tips     enough bias
  Chamber-coating particles (Y₂O₃)       wall condition; WAC (Chapter 9)
  Boron segregation from the BSG mask    negligible at R1 conditions
```

### 12.1.3 Cryogenic Grass

In DT-R2, grass is the window edge (Chapter 7.4). Its rate rises steeply with O₂ ratio and wafer coldness:

```
Grass sites per cm² of open Si (illustrative, R2):
  O₂/SF₆ 8%, −100 °C:    < 0.1
  O₂/SF₆ 9%, −100 °C:    ≈ 1
  O₂/SF₆ 10%, −100 °C:   ≈ 100 (visibly black)
  O₂/SF₆ 8%, −110 °C:    ≈ 5
```

A factor of a thousand across two points of O₂ ratio: R2 must be run well inside the window.

### 12.1.4 What Grass Costs

A needle at the bottom of a trench is coated by the node dielectric and the electrode like the rest of the wall. Its tip has radius of a few nanometres, so the field across the dielectric there is about twice that on the flat wall (Chapter 10.5.2). A grass needle is therefore a leakage site and an early-breakdown site. A broken-off needle elsewhere is a particle that can block another trench or lodge in the bottle and cause a void in the fill.

---

## 12.2 Etch Stop

### 12.2.1 Conditions

The trench stops etching when the passivation film at the bottom grows faster than ions and fluorine can remove it:

```
Bottom net etch:
  ER_bot = ER₀/(1 + kA) − r_film,bot

The film deposition at the bottom r_film,bot is small in a balanced
recipe (< 10 nm/min equivalent). Etch stop occurs if:
  • O₂ is too high at depth (excess oxidation of the bottom film)
  • bias at depth is too low (ions cannot clear the film)
  • a local neck or bow traps ions in the upper trench (fewer at the bottom)
  • the trench is locally narrow (higher A, lower ER)
```

### 12.2.2 Narrow Trenches

The CD distribution has tails. A trench that opened 15 nm narrower than nominal in the mask has a local aspect ratio about 30% higher:

```
Narrow trench, top CD 55 nm (w̄ ≈ 45 nm), at the reference time:
  ER₀ t = h + k h²/(2w): 9167 = h + 0.02 h²/90
  → 0.000222 h² + h − 9167 = 0
  → h = [−1 + √(1 + 4 × 0.000222 × 9167)] / (2 × 0.000222)
      = [−1 + √9.14] / 0.000444 = (3.023 − 1)/0.000444 ≈ 4.56 µm
  ΔC ≈ −0.44 µm × 5.67 fF/µm ≈ −2.5 fF, plus less perimeter → ≈ 17.4 fF
```

A trench 15 nm narrow at the top fails the 19 fF floor. The rate of such trenches is set by litho and mask open, and their capacitance failure is decided by the etch's ARDE.

### 12.2.3 True Etch Stop

```
True etch stop (rate → 0 before the end) in R1 (illustrative):
  O₂ in ME3 above 22 sccm: trenches narrower than 50 nm at the top stop
  between 3 and 4 µm
  Bias in ME3 below 800 W: the same at 52 nm
```

These are recipe errors, not rare events. The ME3 step (Chapter 8) keeps O₂ low and bias high to stay far from them.

---

## 12.3 Blocked and Shallow Trenches

```
  Defect                        Cause                         Capacitance
  ────────────────────────────────────────────────────────────────────────
  Missing trench                particle or resist residue    ≈ 0 (no cell)
                                at the mouth
  Shallow (< 3 µm)              micromask early; partial      8–12 fF
                                block; resist scum
  Narrow-tail trench            litho CD tail                 15–19 fF
  Grass at the bottom           micromask late                normal C; high
                                                              leakage
```

---

## 12.4 Rare-Event Arithmetic

### 12.4.1 What Rate Is Acceptable

```
Trenches per die: 1.07×10⁹ (1 Gb, illustrative)
Repair budget for the trench module: ≈ 50 failing cells per die
  (redundant rows and columns shared with all other modules)
Allowed rate per trench: 50 / 1.07×10⁹ ≈ 5×10⁻⁸
Design target (leaving most of the budget to other modules): 5×10⁻⁹
```

### 12.4.2 Why Inspection Cannot See It

```
Bright-field inspection of the trench array after etch:
  Sees: missing and grossly blocked trenches at the mouth
  Rate resolvable: ≈ 1 defect per 10⁶–10⁷ trenches inspected over a
    few cm² → limit ≈ 10⁻⁸ per trench with practical sampling

Shallow, narrow, grass: invisible from above
```

### 12.4.3 Monitors

```
  Monitor                                    Sensitivity
  ──────────────────────────────────────────────────────────────────
  Short-loop capacitor arrays (full         10⁻⁸ per trench per wafer
   DT module, no transistors) with          (one array of 10⁸ trenches)
   capacitance and leakage per block
  Voltage-contrast inspection after the     blocked/shallow trenches;
   poly fill and recess                      10⁻⁹ with large-area scans
  Bit-map at wafer sort                     the real rate, weeks later
```

Rare-event control is a matter of combining these: short-loop arrays for fast feedback on recipe and chamber changes, voltage contrast for weekly excursion detection, and bit-maps for the final verdict.

---

## Summary and Key Takeaways

1. **Micromasks grow grass.** A speck that survives from 4 µm becomes a needle almost a micrometre tall.

2. **Cryogenic grass rises a thousandfold across two points of O₂ ratio.** R2 must run well inside its window.

3. **Narrow trenches fail by ARDE.** A trench 15 nm narrow at the top ends 0.44 µm shallow and below 19 fF.

4. **True etch stop is a recipe error.** Keep O₂ low and bias high at depth.

5. **5×10⁻⁹ per trench.** At a billion trenches per die, the target lies below what inspection can see; short-loop arrays and voltage contrast fill the gap.

---

## Study Questions

1. Compute the needle height for an SiOₓBrᵧ micromask (S = 10) that forms at 2.5 µm.

2. Compute the depth at the reference time for a trench with top CD 60 nm (w̄ ≈ 50 nm).

3. Estimate how many short-loop arrays of 10⁸ trenches are needed to detect a rate of 10⁻⁹ with 90% confidence.

4. Why is grass a leakage risk even when the trench has normal capacitance?

5. An excursion raises missing trenches to 3×10⁻⁸. How many cells per die fail, and does the repair budget absorb them?

---

**Next Chapter:** [Chapter 13: The Bottle Etch — Widening the Lower Trench](./13-bottle-etch-widening.md)

---

**Chapter 12 Development Status:** Complete  
**Version:** 1.0
