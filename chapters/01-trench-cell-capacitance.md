# Chapter 1: The Trench Cell — Why Store Charge Below the Silicon

## Overview

A DRAM cell stores a bit as charge on a capacitor of about 20 fF. There are two ways to fit that capacitor into a cell a few hundred nanometres on a side. The **stacked** capacitor builds it upward, above the transistor and the bit line, in a dielectric mold (Books #29 and #31). The **trench** capacitor builds it downward, into the silicon substrate, before any transistor exists. For two decades the two architectures competed. The stacked cell won commodity DRAM; the trench cell survived longest in trench DRAM down to the 46 nm generation and in **embedded DRAM (eDRAM)** on logic processes, where it is still the densest on-chip memory a logic fab can build.

The defining step of the trench cell is the **deep trench (DT) etch**: a hole, elliptical in plan, 70 nm wide and 5 µm deep, etched into single-crystal silicon through an oxide hard mask, at the very start of the process flow. It is a silicon etch, not a dielectric etch. Its chemistry is HBr, NF₃, and O₂, not fluorocarbons. Its problems are passivation balance, mask erosion, the absence of any etch-stop layer, and what happens to the hole afterwards, when it is widened into a bottle, doped, lined, filled, and recessed three times.

This chapter sets out why the trench is so deep, defines the reference cell and trench that the rest of the book follows, and derives the specification sheet the etch must meet.

**Learning Objectives:**
- Compute the sense signal and the capacitance a trench cell must deliver
- Explain why a trench capacitor is formed first and why that constrains the etch
- Compute the capacitance of an elliptical, tapered, bottle-shaped trench
- Relate depth, CD, and bottle widening to capacitance
- State the reference trench and its specification sheet

---

## 1.1 The Charge Target

### 1.1.1 Sense Signal

When the word line opens, the cell shares its charge with the bit line:

```
ΔV_BL = (V_BLH/2) · C_s / (C_s + C_BL)

Reference trench DRAM array (illustrative):
  V_BLH = 1.2 V → V_BLH/2 = 0.6 V
  C_BL  ≈ 90 fF (folded bit line, 512 cells)
  C_s   = 20 fF: ΔV_BL = 0.6 × 20/110 = 109 mV

eDRAM macro (short bit line, 128 cells):
  V_BLH = 1.0 V, C_BL ≈ 35 fF
  C_s   = 20 fF: ΔV_BL = 0.5 × 20/55 = 182 mV
```

The sense amplifier needs about 80–100 mV after offset, noise, and the charge lost to leakage over the refresh interval. A cell below about 17 fF fails at the tail of the retention distribution in the commodity array. eDRAM can tolerate somewhat less capacitance because its bit line is short, but it pays for that with a hotter, leakier logic environment and shorter refresh.

### 1.1.2 Why the Target Does Not Shrink

The charge target is set by the sense amplifier, the bit-line capacitance, and the leakage. None of these scales with the cell area. Each generation must therefore deliver the same 17–25 fF in a smaller footprint. The trench cell has three levers:

1. **Thinner dielectric.** Limited by leakage and reliability; the node dielectric stopped near 2.5 nm EOT once high-k replaced oxide–nitride.
2. **Deeper trench.** Limited by the etch: rate falls with depth, the mask erodes, the profile degrades.
3. **Wider lower trench.** The **bottle**: the trench is widened below the collar after the etch. Limited by the silicon wall between neighbouring trenches.

The trench etch carries the second lever outright and creates the template for the third.

---

## 1.2 The Trench Cell

### 1.2.1 Structure

```
Cross-section of the reference trench cell (not to scale):

        BL contact     WL (gate)
            │             │
   ─────────┴──────┬──────┴───────────── Si surface (0 µm)
   STI │ S/D  │ ch │ S/D │ buried strap ─┐
       │      │    │     │               │
                                     ┌───┴───┐  ← top of DT
                                     │ collar│  0.10–1.20 µm: thick oxide collar
                                     │ oxide │    (suppresses the parasitic
                                     │ poly  │     vertical transistor)
                                     ├───────┤
                                    ╱  node   ╲ 1.20–4.80 µm: bottle,
                                   │ dielectric│ widened 20 nm per side,
                                   │  + poly   │ As-doped buried plate outside
                                   │  storage  │
                                    ╲  node   ╱
                                     ╲_______╱   ← 5.00 µm: bottom
         ═══════════ N-band (buried plate common to all trenches) ═══════════
```

The **storage node** is the doped polysilicon (or metal) fill inside the trench. The **counter-electrode** is the silicon around it, heavily doped with arsenic to form the **buried plate**; all buried plates connect through an n-type **N-band** to a common bias. The **node dielectric** separates the two. The **collar**, a thick oxide on the upper trench wall, keeps the storage node from turning on the vertical parasitic transistor formed by the node, the p-well, and the buried plate. The **buried strap** connects the top of the storage node to the source of the access transistor.

### 1.2.2 Trench-First

The trench is the first patterned feature in the flow. It is etched before STI, before the wells, before the gate. That has four consequences for the etch:

1. **The substrate is pristine.** The etch sees only the pad oxide, pad nitride, and hard mask, with no topography beneath them.
2. **No etch stop exists.** Nothing lies below the trench but more silicon. Depth is set by time alone, and depth variation goes straight into capacitance.
3. **Every later thermal step sees the trench.** Damage, contamination, and residue left by the etch are driven into the crystal by the buried-plate drive-in and the collar oxidation.
4. **Every later module must refill and recess what the etch made.** The profile, the bottom shape, and the roughness are inherited by the bottle etch, the dielectric, the poly fill, and three recess etches (Chapter 14).

---

## 1.3 The Reference Cell and Trench

### 1.3.1 Cell Geometry

```
Reference array (illustrative, 45 nm-class trench cell):
  F = 45 nm; 8F² folded-bit-line cell
  Cell area: 8 × 45² = 16,200 nm²
  Trench pitch along the minor axis: 180 nm (4F)
  Trench pitch along the major axis: 270 nm (6F, staggered)
```

### 1.3.2 The Trench

```
Opening at the silicon surface (ellipse):
  Minor axis w_top = 70 nm, major axis L_top = 110 nm
  Area = π × 35 × 55 = 6,048 nm² (37% of the cell)
  Perimeter (Ramanujan): π[3(a+b) − √((3a+b)(a+3b))]
    = π[270 − √(160 × 200)] = π[270 − 178.9] = 286 nm

Depth below the silicon surface: H = 5.00 µm
Bottom (before the bottle): minor 50 nm, major 88 nm
Average minor CD over the depth: w̄ = 60 nm
Sidewall angle along the minor axis: arctan(5000/10) → 89.89°

Aspect ratio:
  At the top minor CD:      5000/70 = 71:1
  At the average minor CD:  5000/60 = 83:1   (used for transport and ARDE)
  Including the remaining hard mask and pad nitride at the end of the etch
  (300 nm BSG + 150 nm SiN + 5 nm pad oxide = 455 nm):
                            5455/60 = 91:1
```

### 1.3.3 Silicon Walls

```
Wall between neighbours along the minor axis:
  At the top:         180 − 70 = 110 nm
  At mid-depth (CD 60): 120 nm
  In the bottle (minor CD widened to ≈ 100 nm at mid-depth): 80 nm
  Minimum allowed (dielectric field, buried-plate depletion,
  node-to-node short margin): 40 nm
```

Bottle widening is limited by this wall. A trench that etches 10 nm wide at mid-depth leaves 10 nm less wall; a trench that bows by 10 nm per side leaves 20 nm less. The etch profile becomes a merging budget once the bottle is added (Chapter 11).

---

## 1.4 Capacitance

### 1.4.1 Areal Capacitance

```
C/A = ε₀ · 3.9 / EOT
  EOT = 2.5 nm (Al₂O₃-based node dielectric, illustrative)
  C/A = 8.854×10⁻¹² × 3.9 / 2.5×10⁻⁹ = 1.381×10⁻² F/m² = 13.8 fF/µm²
```

### 1.4.2 Capacitor Area

Only the trench below the collar stores charge. The collar occupies 0.10–1.20 µm. The bottle occupies 1.20–4.80 µm. The last 0.20 µm curves into the bottom.

```
Without a bottle (tapered ellipse, average perimeter below the collar ≈ 255 nm):
  Wall:   0.255 µm × 3.60 µm = 0.918 µm²
  Bottom: ≈ 0.010 µm² (rounded, 50 × 88 nm)
  Total ≈ 0.93 µm² → C_s = 0.93 × 13.8 = 12.8 fF

With the reference bottle (+20 nm per side: minor 110, major 150 at mid-bottle):
  Perimeter at a = 55, b = 75:
    π[3 × 130 − √(240 × 280)] = π[390 − 259.2] = 411 nm
  Wall:   0.411 µm × 3.60 µm = 1.480 µm²
  Bottom: ≈ 0.013 µm²
  Total ≈ 1.49 µm² → C_s = 1.49 × 13.8 = 20.6 fF
```

The bottle adds 61% to the capacitance. Without it the 45 nm-class trench cell does not work.

### 1.4.3 Sensitivities

```
Depth:   ∂C/∂H = 0.411 µm × 13.8 fF/µm² = 5.67 fF/µm = 0.57 fF per 100 nm
Bottle:  ∂C/∂(per-side widening) ≈ π × 2 (both axes) × 3.60 µm × 13.8 fF/µm²
         per µm → ≈ 0.31 fF per nm of widening per side
Top CD:  a 1 nm narrower trench (minor CD) etches ≈ 26 nm shallower at fixed
         time (Chapter 4) → ≈ 0.15 fF from depth, plus ≈ 0.08 fF from the
         smaller perimeter
```

The most important line is the last one. **A nanometre of CD matters little through the perimeter; it matters through the 26 nm of depth it costs.** Depth is controlled by time, and time is the same for every trench on the wafer, so CD variation becomes depth variation becomes capacitance variation.

---

## 1.5 The Etch Sequence

```
Reference deep-trench module (illustrative):

  Step                               Tool                    Time
  ──────────────────────────────────────────────────────────────────────
  1. Litho: ArF immersion resist     scanner
     over SiARC / organic underlayer
  2. Hard-mask open:                 CCP dielectric etch     ≈ 3 min
     ARC → BSG (900 nm) → SiN
     (150 nm) → pad oxide (5 nm)
  3. Resist / underlayer strip       ash + wet               ≈ 2 min
  4. Native-oxide breakthrough       Si etch chamber          10 s
  5. Deep-trench Si etch (DT-R1)     Si etch chamber        ≈ 5.8 min
  6. Post-etch clean (dilute HF,     single-wafer wet         ≈ 3 min
     SPM) removing SiOₓBrᵧ/SiOₓFᵧ
     sidewall film
  7. Depth / CD metrology            IR, CD-SEM, OCD
  → collar, bottle, buried plate, node dielectric, fill, recesses
```

Two etch processes are carried through the book:

- **DT-R1**: HBr/NF₃/O₂ in an inductively coupled silicon etch chamber, chuck at +60 °C, about 1.6 µm/min open-feature reference rate, main etch ≈ 5.7 min. The production reference.
- **DT-R2**: SF₆/O₂ at −100 °C (cryogenic), about 3.0 µm/min, main etch ≈ 2.5 min. Faster and more selective to the hard mask, with harder temperature control and new defects (Chapter 7).

---

## 1.6 The Specification Sheet

```
Deep-trench etch specification (reference, illustrative):

  Parameter                         Target          Limit
  ─────────────────────────────────────────────────────────────────
  Depth below Si surface            5.00 µm         ±0.12 µm (3σ wafer),
                                                    ≥ 4.75 µm every die
  Minor CD at Si surface            70 nm           ±3 nm (3σ)
  Minor CD at 2.5 µm                60 nm           ±4 nm
  Bottom minor CD                   50 nm           ≥ 40 nm
  Bow (max minor CD − top CD)       ≤ 0 nm          ≤ +5 nm
  Sidewall angle (minor)            89.9°           89.6–90.0°
  Bottom shape                      rounded         no microtrench, no
                                                    pointed tip
  Twist / tilt at the bottom        —               ≤ 15 nm shift
  Remaining BSG at end              ≥ 250 nm        ≥ 150 nm
  Pad SiN loss                      0 nm            ≤ 10 nm
  Sidewall roughness (RMS)          ≤ 1.5 nm        ≤ 2.5 nm
  Silicon grass / black Si          none            0 sites per die
  Capacitance after full module     20.6 fF         ≥ 19.0 fF
```

### 1.6.1 Why ±0.12 µm

```
Capacitance budget: 20.6 fF nominal, 19.0 fF floor → 1.6 fF margin
Allocation (RSS):
  Depth:           ±0.12 µm × 5.67 fF/µm = 0.68 fF
  Bottle widening: ±2 nm per side × 0.31 = 0.62 fF
  EOT:             ±3% × 20.6 = 0.62 fF
  CD (perimeter):  ±3 nm minor × 0.08 = 0.24 fF
  RSS = √(0.68² + 0.62² + 0.62² + 0.24²) = 1.13 fF  (3σ)
  Margin left for the mean offset: 1.6 − 1.13 = 0.47 fF ≈ 80 nm of depth
```

The etch owns about a third of the variance. Because a CD error of 3 nm costs 78 nm of depth, the top-CD uniformity from the hard-mask open is part of the depth budget too.

---

## 1.7 Trench Versus Stack

```
                         Trench (this book)       Stacked (Books #29, #31)
  ──────────────────────────────────────────────────────────────────────────
  Where                  in the Si substrate      above the bit line
  When                   first patterned step     after the bit line
  Material etched        single-crystal Si        oxide/nitride mold
  Chemistry              HBr/NF₃/O₂, SF₆/O₂       fluorocarbon, HF-based
  Etch stop              none (timed)             SiN stop over W pad
  Aspect ratio           71:1 top, 83:1 average   57–91:1
  Widening               bottle after etch        none (bow is a defect)
  Logic compatibility    high (before the gate)   low (needs thermal budget
                                                  after transistors)
  Where it lives today   eDRAM on SOI and bulk    all commodity DRAM
                         logic; silicon
                         capacitors; legacy DRAM
```

The trench lost commodity DRAM largely because scaling the cell below about 40 nm made the bottle wall and the vertical parasitic device hard to control. It kept eDRAM because it is formed before the logic transistors and leaves the planar surface intact for them. Chapter 13 covers the SOI eDRAM variant, and Chapter 14 the silicon trench capacitors that use the same etch for passive devices.

---

## Summary and Key Takeaways

1. **The charge target is fixed.** About 20 fF gives 109 mV on a 90 fF bit line.

2. **Three levers.** Dielectric thickness, depth, and bottle widening; the etch owns depth and the template for the bottle.

3. **The reference trench.** 70 × 110 nm ellipse, 5.00 µm deep, 71:1 at the top CD, 83:1 at the average CD; 20.6 fF with a 20 nm-per-side bottle.

4. **No etch stop.** Depth is set by time; each nanometre of CD becomes 26 nm of depth and 0.15 fF.

5. **The bottle is 61% of the capacitance.** And it spends the silicon wall that the etch profile must preserve.

6. **Trench-first.** Whatever the etch leaves in the crystal, every later thermal step drives in.

---

## Study Questions

1. Compute ΔV_BL for C_s = 17 fF on the reference commodity array and on the eDRAM macro.

2. Compute the capacitance of the reference trench with no bottle if the depth is raised to 7.0 µm. Is this a practical alternative to the bottle? (Use Chapter 4's ARDE to estimate the etch time.)

3. The node dielectric is changed to EOT 2.0 nm. By how much can the depth be reduced at constant capacitance?

4. A lot arrives with top minor CD 67 nm. Estimate the depth and capacitance change at the reference etch time.

5. The bottle widening is raised to 25 nm per side. Compute the capacitance and the remaining silicon wall at mid-depth along the minor axis.

6. Explain why the trench etch has no etch-stop layer and list three ways the process controls depth without one.

---

**Next Chapter:** [Chapter 2: The Incoming Stack — Pad Films, Oxide Hard Mask & Mask Open](./02-hard-mask-stack-mask-open.md)

---

**Chapter 1 Development Status:** Complete  
**Version:** 1.0
