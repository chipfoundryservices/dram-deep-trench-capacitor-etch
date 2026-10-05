# Chapter 11: Twist, Tilt, Merging & Placement

## Overview

A trench is a 5 µm lever. An angular error of a tenth of a degree at the top moves the bottom by 9 nm. In the oxide capacitor hole of Book #31, such errors miss a 21 nm landing pad. The deep trench has no landing pad: it ends in silicon. Its placement problem is different. Neighbouring trenches share the silicon between them, and the bottle etch will later consume most of it. Any error that moves one trench toward its neighbour, below the collar, spends the wall that keeps two storage nodes apart.

This chapter distinguishes tilt (collective) from twist (random), estimates each, builds the merging budget, and treats it statistically at a billion trenches per die.

**Learning Objectives:**
- Distinguish tilt and twist and explain why only random errors spend the wall
- Estimate edge tilt from sheath curvature and its depth dependence
- Identify the sources of twist in a silicon trench
- Build a wall budget and estimate the merging probability
- Explain why the merging tail, not the mean, sets the bottle

---

## 11.1 Definitions

```
Tilt:   the trench axis is inclined by θ from the wafer normal, the same
        way for all trenches in a neighbourhood (collective)
Twist:  an individual trench departs from its neighbours' direction,
        randomly, typically in its lower part (random)

Lateral shift at depth z from an angle θ starting at depth z₀:
  Δ(z) = (z − z₀) tan θ
  θ = 0.1° over 5 µm: 8.7 nm;  θ = 0.2°: 17.5 nm
```

**Tilt does not spend the wall.** If both neighbours tilt by the same angle, the wall between them tilts too but keeps its thickness. Tilt matters for what lies above the trench: the collar, the buried strap, and the vertical isolation from the access transistor. Twist spends the wall directly.

---

## 11.2 Tilt

### 11.2.1 Edge Tilt

The sheath follows the wafer, the edge ring, and the step between them. If the ring sits higher or lower than the wafer, the sheath bends in the last few millimetres and ions arrive inclined:

```
Edge tilt versus ring height (illustrative, R1):
  Ring 0.3 mm above wafer: ions tilt outward-in, θ ≈ +0.25° at 1 mm
                            from the edge
  Ring flush:              θ ≈ 0.05°
  Ring worn 0.3 mm low:    θ ≈ −0.20°
Edge ring erosion: ≈ 0.1 mm per 1000 RF hours
```

### 11.2.2 What Tilt Costs

```
At the top of the trench (collar zone, first 1.2 µm):
  θ = 0.2°: Δ(1.2 µm) = 4.2 nm
  The collar and strap see a trench whose upper part is off-axis by
  4 nm relative to the active area; acceptable

At the bottom:
  Δ(5 µm) = 17.5 nm; the specification is ≤ 15 nm
  The bottom moves relative to the N-band and to the trenches of the
  next die row, but not relative to its own neighbours
```

The tilt limit of 15 nm at the bottom comes from the bottle and the buried plate at the edge of the array, where a tilted trench faces a non-tilted structure (an array-edge dummy, the support circuitry well) and the wall is not shared symmetrically.

### 11.2.3 Control

Edge-ring height is tracked with RF hours and compensated by a ring-lift mechanism or by ring replacement; edge tilt is measured on a patterned monitor by X-SEM or by asymmetric OCD and fed into the ring-lift setting.

---

## 11.3 Twist

### 11.3.1 Sources in a Silicon Trench

```
  Source                                  Typical onset          Character
  ───────────────────────────────────────────────────────────────────────────
  Mask asymmetry: facet or LER uneven     from the top           small, ≈ 1–2 nm
   around the opening                                            at the bottom
  Charged-mask deflection of low-E ions   top 1 µm               mostly bow, some
                                                                 twist
  Sidewall film asymmetry: a thicker      mid-depth; grows       the main random
   film on one side shadows ions and                             term; σ ≈ 2 nm
   reflects them across                                          at the bottom
  Particles or residue on one side of     anywhere               heavy tail;
   the bottom                                                    10–30 nm
  Crystallographic preference at low      bottom                 small
   ion flux
```

In an oxide hole, charging drives twist (Book #31, Chapter 11). In a silicon trench, charging is weak (Chapter 4.2), and twist is driven mostly by asymmetric film and reflections. The twist in the reference trench is smaller than the tilt at the edge, but it is random and therefore spends the wall.

### 11.3.2 Growth with Depth

```
Twist amplitude σ_tw at the bottom versus depth (R1, illustrative):

  Depth (µm)    2      3      4      5      6
  σ_tw (nm)     0.6    1.0    1.5    2.0    2.8
```

The growth is faster than linear: once a trench deviates, ions reflected from its nearer wall strike the opposite wall lower down at a steeper angle, amplifying the deviation. Below about 3 µm the effect is small; at 6 µm it becomes significant.

---

## 11.4 The Wall Budget

### 11.4.1 Nominal

```
Wall along the minor axis at mid-bottle (Chapter 1.3.3):
  Pitch 180 nm − bottle minor CD 110 nm = 70 nm
Minimum allowed: 40 nm
Margin: 30 nm
```

### 11.4.2 Random Contributions

```
Per trench, along the minor axis (1σ, illustrative):
  CD at mid-depth (from ±4 nm 3σ):          σ = 1.33 nm → radius 0.67 nm
  Bottle widening per side (±2 nm 3σ):      0.67 nm
  Twist lateral at mid-bottle (≈ 3 µm):     1.0 nm
                                         (2.0 nm at the bottom)

Wall between two neighbours (both contribute, independent):
  σ_wall = √(2 × (0.67² + 0.67² + 1.0²)) = √(2 × 1.90) = 1.95 nm   (mid-bottle)
  At 4.5 µm (twist 1.8 nm): √(2 × (0.45 + 0.45 + 3.24)) = 2.88 nm
```

### 11.4.3 How Many Sigma

```
Margin 30 nm:
  Mid-bottle: 30 / 1.95 = 15σ
  Near the bottom (wall slightly wider because of taper, ≈ 76 nm nominal,
  margin 36 nm): 36 / 2.88 = 12.5σ
```

Fifteen standard deviations should make merging impossible, if the distributions were Gaussian. They are not.

---

## 11.5 The Tail

### 11.5.1 Counting

```
Trenches per die (1 Gb trench DRAM, illustrative): ≈ 1.07×10⁹
Minor-axis neighbour pairs: ≈ 1.07×10⁹
Target merged pairs per die: ≤ 0.1 (repairable, rare)
  → probability per pair ≤ 10⁻¹⁰ → ≈ 6.4σ for a Gaussian
```

### 11.5.2 Heavy Tails

The Gaussian margin of 12–15σ is far beyond 6.4σ. The merging rate is set instead by the non-Gaussian events:

```
  Event                                 Rate per trench     Wall lost
  ─────────────────────────────────────────────────────────────────────
  Particle on the mask edge             10⁻⁹–10⁻⁸           15–40 nm (local
   deflecting the etch                                       twist + bow)
  Mask defect (BSG pinhole, bridge)     10⁻¹⁰–10⁻⁹          trench merged at
                                                            the top or missing
  Grass needle at the bottom            10⁻⁹ (R1),          bottle etch
   (Chapter 12)                         higher in R2         undercuts it: local
                                                            wall loss
  Litho: two openings merged in resist  < 10⁻¹⁰             full merge
```

A particle-induced deflection of 30 nm in one trench, plus a 3σ combination of the Gaussian terms (6 nm), consumes 36 nm, more than the 30 nm margin. At a rate of 10⁻⁹ per trench, that is one merged pair per die. **The merging yield is a particle and defect problem, not a profile problem.** That is why the chamber particle specification (Chapter 9) and the mask-open defect density appear in the trench yield model (Chapter 16).

---

## 11.6 Detection

```
  Method                         What it sees
  ──────────────────────────────────────────────────────────────────
  Planar delayering + SEM at     merged and near-merged trenches at a
   several depths                 chosen depth; slow, sampling
  X-SEM along the minor axis     twist in a few trenches
  Electrical: node-to-node       merged pairs as leakage between
   leakage test structures        adjacent storage nodes
  Bit-map at test                paired-bit failures along the minor axis
```

A pair of failing bits that are minor-axis neighbours is the classic signature of a merged trench.

---

## Summary and Key Takeaways

1. **Tilt is collective; twist is random.** Only random errors spend the wall between neighbours.

2. **Edge tilt follows the ring.** 0.2° gives 17.5 nm at 5 µm; ring wear is tracked and compensated.

3. **Silicon trenches twist by film asymmetry,** not by charging; σ ≈ 2 nm at 5 µm, growing faster than depth.

4. **The Gaussian margin is huge.** 12–15σ in the reference budget.

5. **The tail is particles and mask defects.** One deflected trench per 10⁹ means one merged pair per die.

---

## Study Questions

1. Compute the bottom shift for an edge tilt of 0.15° at 5 µm and at 6 µm.

2. Explain why tilt does not reduce the wall between neighbours. When does it?

3. Recompute σ_wall at mid-bottle if the bottle widening variation doubles to ±4 nm (3σ).

4. The trench deepens to 6 µm and twist rises to σ = 2.8 nm at the bottom. Recompute the margin in σ near the bottom.

5. A fab measures 0.3 merged pairs per die. Which defect sources would you investigate first, and with which methods?

---

**Next Chapter:** [Chapter 12: Silicon Grass, Etch Stop & Rare Events](./12-grass-etch-stop-rare-events.md)

---

**Chapter 11 Development Status:** Complete  
**Version:** 1.0
