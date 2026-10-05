# Chapter 2: The Incoming Stack — Pad Films, Oxide Hard Mask & Mask Open

## Overview

A 5 µm silicon trench cannot be etched through photoresist. A 120 nm ArF resist lasts perhaps 0.6 µm of silicon in HBr chemistry. The trench is therefore etched through a **hard mask** of oxide, itself patterned by a separate dielectric etch, over pad films that protect the silicon surface for the rest of the flow. The mask sets the top CD, carries the CD distribution that becomes depth variation, erodes during the trench etch, and must be removed afterwards without harming the pad nitride.

This chapter describes the reference stack, the hard-mask open, the mask budget that decides how long the silicon etch may run, and the incoming variation the trench etch inherits.

**Learning Objectives:**
- Describe the function of each film in the reference stack
- Explain why borosilicate glass is used as the hard mask
- Build the mask budget for DT-R1 and DT-R2
- Estimate the top-CD shift through the mask open and its effect on depth
- Explain how mask faceting couples to the trench profile

---

## 2.1 The Reference Stack

```
Reference stack before litho (illustrative):

  Film                     Thickness   Function
  ──────────────────────────────────────────────────────────────────────
  ArF immersion resist     100 nm      pattern
  SiARC (Si-containing     30 nm       anti-reflection; transfer layer
   anti-reflective coat)
  Organic underlayer (SOC) 200 nm      etch transfer into BSG
  BSG hard mask            900 nm      the trench-etch mask
   (≈ 4 wt% B, PECVD/SACVD)
  Pad SiN (LPCVD)          150 nm      CMP stop and oxidation mask for
                                       STI and later recesses; must
                                       survive the trench etch intact
  Pad oxide (thermal)      5 nm        stress buffer between SiN and Si
  Si substrate             —           p-type ⟨100⟩, 300 mm
```

### 2.1.1 Why Borosilicate Glass

The hard mask must do two contradictory things: resist the silicon etch for 5 µm, then disappear after it without touching the pad nitride or the pad oxide exposed at the trench top.

```
Etch rates in dilute HF-based clean (illustrative, relative to thermal oxide = 1):
  Thermal oxide         1
  TEOS oxide (undensified)  3–5
  BSG (4 wt% B)         20–50 (vapour HF: higher still)
  LPCVD SiN             0.05
```

BSG strips about ten times faster than undoped deposited oxide, so it can be removed in a short clean that leaves the 5 nm pad oxide undercut by only a few nanometres. In the trench etch, BSG etches about as slowly as TEOS in HBr chemistry, because the boron is a minor constituent and the etch of oxide in HBr/O₂ is driven by ion sputtering, not by chemistry.

### 2.1.2 Pad Nitride

The pad SiN is the most valuable film in the stack. It will serve as the CMP stop for the trench fill, the mask for the buried-strap and collar recesses, and later the STI CMP stop. Any loss during the trench etch reduces the margins of three later modules. The trench etch therefore must not reach the pad SiN at the top of the hole: the BSG must survive the entire etch with margin.

---

## 2.2 The Hard-Mask Open

### 2.2.1 Sequence

```
Mask-open steps (CCP dielectric etch chamber, illustrative):

  Step         Chemistry                  Target layer    Time
  ────────────────────────────────────────────────────────────────
  ARC open     CF₄/CHF₃                   SiARC           15 s
  UL open      N₂/H₂ or O₂/COS            organic UL      40 s
  BSG main     C₄F₆/O₂/Ar, 2 kW, 30 mTorr  BSG 900 nm      95 s
  SiN          CH₂F₂/CF₄/O₂/Ar            SiN 150 nm      35 s
  Pad oxide    CF₄/Ar, low power          pad oxide        8 s
  → strip UL in situ (O₂) or ex situ
```

### 2.2.2 CD Transfer

```
Minor-axis CD through the stack (reference):
  Resist after litho:     78 nm
  After SiARC/UL open:    75 nm (trim from the UL etch)
  BSG top / bottom:       75 / 71 nm (taper 89.75°)
  SiN bottom:             70 nm
  → top CD in silicon:    70 nm
```

The mask open sets the top CD to within a few nanometres and must reproduce it across the wafer. A 2 nm centre-to-edge CD signature becomes a 52 nm depth signature in the trench (Chapter 4). That is about 40% of the ±0.12 µm depth allowance. The mask-open recipe and the trench recipe are therefore tuned as a pair, and production control feeds the measured post-open CD forward to the trench etch (Chapter 15).

### 2.2.3 Ellipticity

The trench is an ellipse 70 × 110 nm. Litho and the mask open shrink the minor axis faster than the major axis, because the minor axis is closer to the resolution limit and polymer deposition on the sidewall is a larger fraction of it. The ratio drifts from 1.55 at the resist to about 1.57 at the silicon. Ellipticity matters twice later: it sets the capacitor perimeter, and it sets how the bottle grows against the nearest wall along the minor axis.

---

## 2.3 The Mask Budget

### 2.3.1 DT-R1

```
BSG thickness through the module (DT-R1, illustrative):

  Event                                 BSG loss    BSG remaining
  ───────────────────────────────────────────────────────────────
  As deposited                              —          900 nm
  Mask open (top erosion while UL lasts)   40 nm        860 nm
  UL strip / post-open clean               40 nm        820 nm
  Native-oxide breakthrough (10 s)         20 nm        800 nm
  Main etch: 5.0 µm Si at effective
    selectivity 10:1                      500 nm        300 nm
  End of etch                                            300 nm
  Specification                                         ≥ 150 nm
```

The effective selectivity of 10:1 is lower than the open-area selectivity of silicon to BSG (about 20:1 in HBr/NF₃/O₂). Two effects pull it down:

1. **The silicon rate falls with depth** (ARDE), while the mask erodes at the open-area rate. Averaged over the etch, the trench etches at about 55% of the open-feature reference rate (Chapter 4), so the selectivity is roughly halved.
2. **Faceting.** The mask corners erode faster than the flat top, under ions arriving near 45°. Faceting thins the mask locally around the opening.

### 2.3.2 DT-R2

```
Cryogenic SF₆/O₂ at −100 °C: open-area selectivity Si:BSG > 100:1
  Effective (ARDE weaker, k = 0.012): ≈ 40:1
  Main-etch BSG loss for 5 µm: 125 nm → 675 nm left from 800 nm
```

DT-R2 can use a 500 nm BSG mask. A thinner mask reduces the total aspect ratio at the start and lowers the cost of the mask open. Chapter 7 shows why it is nevertheless not universal.

### 2.3.3 Mask as the Depth Limit

```
Maximum depth for a given BSG (R1, 150 nm reserve, 100 nm pre-etch loss):
  BSG 900: (900 − 100 − 150) × 10 = 6.5 µm
  BSG 700: 4.5 µm
  BSG 1100: 8.5 µm, but the extra 200 nm lengthens the mask open by
            ≈ 20 s and raises the starting aspect ratio of the mask
            hole from 13:1 to 16:1, which worsens CD transfer
```

At the reference depth, the BSG is not the limit by a comfortable margin. It becomes the limit if the trench must deepen by 30% to recover capacitance lost elsewhere.

---

## 2.4 Faceting and Its Consequences

```
Facet geometry at end of R1 (illustrative):
  Facet angle ≈ 45° from the horizontal
  Facet depth ≈ 60 nm into the BSG at the trench edge
  The facet widens the top of the mask opening by ≈ 15 nm per side
```

The facet does not change the silicon top CD directly; the silicon below it is protected by the remaining vertical BSG sidewall. It does change the trajectory of ions. Ions that strike the facet are reflected at shallow angles into the trench and strike the upper silicon wall, where they cause **bow** just below the pad nitride (Chapter 10). The faster the facet grows, the larger the bow. Holding the facet to less than half the remaining BSG is a design rule.

---

## 2.5 Incoming Variation

```
Incoming variation the trench etch inherits (3σ, illustrative):

  Parameter                         Variation        Effect on trench
  ─────────────────────────────────────────────────────────────────────
  Top minor CD after open           ±3 nm            ±78 nm depth
  CD radial signature               2 nm C–E         52 nm depth signature
  BSG thickness                     ±25 nm           ±25 nm of remaining
                                                     mask at the end
  SiN thickness                     ±5 nm            minor
  Native oxide in the opening       0.5–1.5 nm       incubation of 2–6 s;
                                                     ±10 nm depth
  Residue at the bottom of the      0–2 nm C/F/O     micromasking → grass
   opening (mask-open polymer)                       (Chapter 12)
```

The last two rows explain the 10 s breakthrough step before the main etch. HBr/O₂ etches thin native oxide slowly and unevenly; a short, fluorine-rich, higher-bias step clears oxide and residue uniformly so that every trench starts at the same time.

---

## 2.6 Post-Etch Mask Removal

After the trench etch, the remaining 300 nm BSG and the sidewall passivation film are removed together:

```
Post-etch clean (illustrative):
  1. Dilute HF (50:1) or vapour HF: removes BSG at ≈ 2–5 nm/s; removes
     SiOₓBrᵧ/SiOₓFᵧ sidewall film; undercuts the 5 nm pad oxide by ≈ 5–10 nm (budgeted in the collar design)
  2. SPM (H₂SO₄/H₂O₂): organics and metal residue
  3. SC1 dilute: particles; light Si oxidation
  4. Dilute HF last: removes chemical oxide before collar/bottle steps
```

The clean must reach the bottom of a 5 µm trench. Liquid exchange in a 60 nm hole 5 µm deep is by diffusion: the time scale is H²/D ≈ (5×10⁻⁴ cm)²/10⁻⁵ cm²/s = 25 ms, so it is not the limit. Wetting is. A trench that traps a bubble keeps its sidewall film and later forms a void in the poly fill.

---

## Summary and Key Takeaways

1. **The stack.** 900 nm BSG over 150 nm pad SiN and 5 nm pad oxide; the trench is etched through the BSG.

2. **Why BSG.** It resists the silicon etch like TEOS but strips in HF ten times faster, sparing the pad oxide and nitride.

3. **The mask open sets the depth signature.** Each nanometre of CD from the open becomes 26 nm of depth.

4. **The budget.** R1 consumes about 600 nm of BSG and leaves 300 nm; effective selectivity 10:1. R2 leaves 675 nm.

5. **Facets feed the bow.** Ions reflected from the mask facet strike the upper trench wall.

6. **Start every trench at once.** The breakthrough step removes native oxide and mask-open residue that would otherwise delay or micromask.

---

## Study Questions

1. Compute the maximum trench depth for R1 if the effective selectivity falls to 8:1 because of a higher bias power.

2. The mask open leaves a 2 nm centre-high CD signature. Estimate the depth signature in the trench and how much of the ±0.12 µm allowance it uses.

3. Why does the effective selectivity in the trench differ from the open-area selectivity? Estimate it from ER_avg/ER₀ = 0.55 and the open-area selectivity of 20.

4. A fab replaces BSG with undoped TEOS of the same thickness. What changes in the trench etch and what changes in the post-etch clean?

5. Explain how mask faceting produces bow in the upper trench, and suggest two recipe changes that reduce it.

---

**Next Chapter:** [Chapter 3: Silicon Etch Chemistry — HBr, NF₃, O₂ & Sidewall Passivation](./03-silicon-etch-chemistry-passivation.md)

---

**Chapter 2 Development Status:** Complete  
**Version:** 1.0
