# Chapter 13: The Bottle Etch — Widening the Lower Trench

## Overview

The trench etch makes a hole; the bottle etch makes it a capacitor. After the collar is formed in the upper 1.2 µm, the lower 3.6 µm is widened by about 25 nm per side, raising the capacitor perimeter from about 260 nm to 411 nm and the capacitance from 12.8 to 20.6 fF (Chapter 1.4). The bottle etch is a second etch through the same hole, but it is isotropic, it works from inside the trench, and its constraint is the silicon wall left to the neighbours. Every feature of the deep-trench profile — taper, bow, twist, roughness, bottom shape — carries through it.

This chapter describes the bottle sequence, compares wet and dry bottle etches, treats the crystallographic shaping of wet bottles and the depth uniformity of dry ones, and sets the bottle against the merging budget of Chapter 11.

**Learning Objectives:**
- Describe the collar-then-bottle sequence and why the collar comes first
- Compare NH₄OH wet, remote-plasma dry, and oxidation-strip bottle methods
- Predict the bottle shape from crystallography and transport
- Compute the bottle uniformity with depth for a dry bottle etch
- Allocate the bottle within the wall budget

---

## 13.1 The Sequence

```
Collar-then-bottle flow (illustrative):

  1. Post-DT clean (Chapter 2.6)
  2. Thin thermal oxide (2 nm) + LPCVD SiN liner (4 nm)
  3. Fill with sacrificial material (resist or a-Si); recess to 1.20 µm
  4. Strip SiN liner above the recess (hot phosphoric or dry isotropic)
  5. Collar: oxidize or deposit oxide (20–25 nm) on the upper wall
  6. Remove sacrificial fill; strip SiN liner below the collar
  7. Bottle etch: widen the exposed lower trench by 25 nm per side
  8. Buried plate: As gas-phase doping or ASG + drive-in
  9. Node dielectric; electrode/poly fill; recesses (Chapter 14)
```

The collar must come first because it protects the upper trench from the bottle etch. The recess depth in step 3 therefore sets the top of the bottle. A recess error of ±50 nm moves the top of the bottle by the same amount and changes the capacitor by about ±0.3 fF (5.67 fF/µm × 0.05 µm).

---

## 13.2 Methods

```
  Method                    Mechanism                  Rate          Shape
  ──────────────────────────────────────────────────────────────────────────
  Dilute NH₄OH wet          anisotropic chemical:      ≈ 12 nm/min   faceted:
  (≈ 1:20, 40 °C)           {100} ≫ {111}              on {100}      octagonal/
                                                                     rectangular
  Remote-plasma (CDE)       F radicals from NF₃/O₂     ≈ 20 nm/min   round;
  NF₃/O₂/(N₂)               downstream, no ions;                     depth-
                            nearly isotropic                         dependent
  Oxidation + HF strip      consumes Si as SiO₂        ≈ 0.44 nm Si  round,
  (repeated)                (0.44 nm Si per nm ox)     per nm ox     conformal,
                                                                     slow
  Vapour-phase HCl or       thermal; selective to      variable      faceted
  Cl₂ at elevated T         oxide/nitride
```

### 13.2.1 Wet NH₄OH

Alkaline etching of silicon is crystallographic: it attacks {100} and {110} planes much faster than {111}. A round trench in ⟨100⟩ silicon, widened in NH₄OH, develops flat facets on the slow planes and becomes polygonal in plan.

```
Reference wet bottle (illustrative):
  Rate on {100}: 12 nm/min; on {110}: 15 nm/min; on {111}: 0.5 nm/min
  Time for 25 nm on the slowest relevant fast plane: ≈ 2.1 min
  Plan shape at mid-bottle: an ellipse squared off along the ⟨110⟩
    directions; corners along ⟨100⟩ advance ≈ 20% further
```

The bottle grows farther in some directions than others. If the farthest-growing direction points at the nearest neighbour, the wall budget suffers. The trench major axis is aligned to ⟨110⟩ for this reason: the minor axis, which faces the nearest neighbour, then points along another ⟨110⟩, and the fast ⟨100⟩ corners point diagonally, toward the larger gaps between staggered neighbours.

Wet bottles are uniform with depth: the reaction is slow compared with diffusion in a 60 nm trench (time constant H²/D ≈ 25 ms, Chapter 2.6). Their risks are wetting (a trapped bubble leaves an unwidened segment) and roughness from crystallographic pitting.

### 13.2.2 Dry Remote-Plasma Bottle

```
CDE bottle (illustrative):
  NF₃/O₂ 200/40 sccm, remote microwave or ICP source, wafer at 25 °C,
  no bias; F reaches the trench as neutrals only
  Open-surface lateral rate: 20 nm/min
```

The F atoms must diffuse down the trench in free-molecular flow, reacting as they go. The widening therefore falls with depth:

```
Coburn–Winters from the bottom of the collar (1.2 µm) to the bottom of the
bottle (4.8 µm), w ≈ 60 nm → A = 3.6/0.06 = 60; s_F at 25 °C ≈ 0.005:
  Γ_bot / Γ_top ≈ 1 / (1 + 0.75 × 0.005 × 60) = 1 / 1.225 = 0.82

Widening for 25 nm at the top of the bottle: ≈ 20.5 nm at the bottom
```

An 18% gradient in widening is too much. Dry bottles compensate by pulsing: a short exposure followed by pump-out, repeated, so the trench refills with fresh reactant each cycle; or by lowering the reaction probability with a lower wafer temperature. Pulsed CDE brings the gradient below 5%.

### 13.2.3 Oxidation and Strip

Thermal oxidation consumes silicon conformally, with no transport limit at these dimensions. Each nanometre of oxide grown consumes 0.44 nm of silicon. Twenty-five nanometres of widening needs about 57 nm of oxide, grown and stripped in two or three cycles. The method is slow and adds thermal budget, but it smooths the wall and rounds the bottom; it is often combined with a wet or dry bottle as a final smoothing step.

---

## 13.3 Inheritance from the Trench Etch

```
  Trench-etch feature            Effect after the bottle
  ──────────────────────────────────────────────────────────────────────────
  Taper                          narrower lower bottle; less perimeter
                                 (Chapter 10.4.2)
  Bow at 0.2–0.5 µm              above the collar; unaffected by the bottle
  Twist (σ 2 nm at the bottom)   carried unchanged; spends wall (Chapter 11)
  Sidewall roughness             wet: amplified at {111} pits; dry: reduced
                                 by 20–40%; oxidation: reduced by ≈ 50%
  Grass needle at the bottom     isotropic etch thins and may free it;
                                 crystallographic etch leaves a {111}-faceted
                                 stub
  Residual sidewall film         masks the bottle locally: unwidened stripes
                                 (the post-DT clean must remove it)
  Pointed bottom                 wet bottle blunts it along {111}; dry bottle
                                 rounds it
```

The last two lines are why the trench etch and the bottle etch are qualified together. A trench etch that leaves a slightly thicker, more oxidized film at depth may pass every trench-etch metrology check and still produce unwidened stripes in the bottle.

---

## 13.4 The Bottle Within the Wall Budget

```
Wall along the minor axis at mid-bottle:
  Pitch 180 − as-etched minor CD 61 − 2 × 25 widening = 69 ≈ 70 nm
Minimum 40 nm → margin 30 nm (Chapter 11.4)

Bottle-specific contributions:
  Widening variation ±2 nm per side (3σ) → in the RSS budget
  Wet facet overshoot along ⟨100⟩ (+20%): along the diagonal neighbours,
    whose distance is ≈ 1.6× the minor-axis pitch: not limiting
  Dry depth gradient (unpulsed): bottle top 25, bottom 20.5 → widen the
    top for the bottom's sake and the top wall shrinks by ≈ 9 nm
```

The bottle is the largest single consumer of the silicon wall: 50 of the 119 nm present at mid-depth. A process that wishes to widen further must first make the trench etch more uniform and less twisted, since each nanometre recovered in the etch's random budget is worth about 0.3 fF in the bottle.

---

## 13.5 Area Enhancement Beyond the Bottle

```
  Technique                         Area gain        Status
  ────────────────────────────────────────────────────────────────────
  Hemispherical-grain Si (HSG)      ×1.6–1.8 on      used at 0.25–0.11 µm;
   on the trench wall               the coated wall  grains too large for
                                                     today's trench
  Mesoporous Si (electrochemical    ×2 and more      research
   or stain etch) in the bottle
  Metal (TiN) electrode instead     no area gain;    used; removes poly
   of doped poly                    ≈ 0.3 nm less    depletion of the
                                    effective EOT    storage node
```

---

## Summary and Key Takeaways

1. **Collar first, then bottle.** The recess that defines the collar sets the top of the bottle.

2. **Three ways to widen.** Wet NH₄OH (crystallographic, uniform with depth), dry remote plasma (round, depth-dependent), oxidation-strip (slow, smooth).

3. **Align the facets away from the neighbours.** Major axis along ⟨110⟩ points the fast ⟨100⟩ corners at the larger gaps.

4. **Dry bottles need pulsing.** An unpulsed CDE bottle widens the bottom 18% less than the top.

5. **The bottle inherits the trench.** Taper, twist, film residue, and bottom shape all pass through it; the two etches are qualified together.

6. **The bottle spends 50 nm of wall.** Each nanometre the trench etch saves in random variation buys about 0.3 fF.

---

## Study Questions

1. A collar recess lands 80 nm deeper than target. Compute the capacitance change.

2. Compute the Coburn–Winters gradient for an unpulsed CDE bottle with s_F = 0.01. What widening at the bottom results if the top widens by 25 nm?

3. How much thermal oxide must be grown and stripped to widen the trench by 15 nm per side?

4. Explain why residual sidewall film from the trench etch produces unwidened stripes in a wet bottle but less so in a dry one.

5. A design moves the trench pitch from 180 to 170 nm along the minor axis. How much bottle widening can be kept at the same 40 nm minimum wall and margin?

---

**Next Chapter:** [Chapter 14: SOI eDRAM, Downstream Recesses & Silicon Trench Capacitors](./14-soi-edram-recesses-silicon-capacitors.md)

---

**Chapter 13 Development Status:** Complete  
**Version:** 1.0
