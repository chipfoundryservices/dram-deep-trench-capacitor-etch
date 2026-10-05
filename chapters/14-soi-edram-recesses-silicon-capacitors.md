# Chapter 14: SOI eDRAM, Downstream Recesses & Silicon Trench Capacitors

## Overview

The deep-trench etch outlived commodity trench DRAM in two places. In **embedded DRAM** on logic processes, often on silicon-on-insulator (SOI) wafers, it gives the densest on-chip memory a logic fab can build. In **silicon trench capacitors** — integrated passive devices and on-die decoupling — the same etch, scaled up in width and depth, delivers capacitance densities of hundreds of nanofarads per square millimetre. Between the etch and either product lie the downstream modules that refill and recess the trench three times. This chapter covers what changes in the etch for SOI, how the recess etches depend on the trench, and how the trench etch is adapted for passive capacitors.

**Learning Objectives:**
- Describe the SOI deep-trench stack and the extra etch steps it requires
- Explain the notch at the buried oxide and how to prevent it
- Describe the poly fill and the three recess etches and their dependence on the trench profile
- Compare the eDRAM trench with silicon trench capacitors in geometry, chemistry, and control

---

## 14.1 SOI eDRAM

### 14.1.1 The Stack

```
SOI eDRAM stack at the trench (illustrative):
  BSG hard mask            700 nm
  Pad SiN                  120 nm
  Pad oxide                5 nm
  SOI silicon              70 nm
  Buried oxide (BOX)       145 nm
  Substrate Si             → trench continues 4.0 µm below the BOX

Trench in the eDRAM cell (illustrative, 22 nm-class logic):
  Opening 60 × 100 nm; depth 4.2 µm below the SOI surface
  Capacitance ≈ 14–18 fF with bottle and high-k
```

The SOI layer removes the need for the collar's parasitic-transistor suppression in the upper trench: the buried oxide already isolates the storage node from the transistor body over 145 nm. The collar in SOI eDRAM is thinner and shorter, which gives more depth to the capacitor.

### 14.1.2 Extra Etch Steps

```
SOI trench etch sequence (illustrative):
  1. Breakthrough (native oxide)                     10 s
  2. SOI silicon (70 nm), HBr/O₂, ME1-like          ≈ 6 s
  3. BOX (145 nm): fluorocarbon step, C₄F₈/O₂/Ar or
     CF₄/CHF₃, higher bias; in the same chamber      ≈ 25 s
  4. Substrate main etch (as DT-R1, ME1–ME3)        ≈ 4.5 min
```

The BOX step is a dielectric etch inside a silicon etch chamber. Its fluorocarbon residue must not reach the silicon main etch, where it would micromask the bottom. A short O₂ flash between steps 3 and 4 removes it.

### 14.1.3 The Notch at the BOX

```
At the BOX/substrate interface:
  During the substrate etch, the insulating BOX sidewall charges
  negatively (like the mask, Chapter 4.2), deflecting low-energy ions
  into the silicon just below it → a lateral notch of 5–15 nm
  In the SOI layer above the BOX, a notch can also form at the
  SOI/BOX interface during step 3 if overetch is long
```

A notch below the BOX widens the storage node exactly where the buried strap and the SOI body are closest; a notch in the SOI layer thins the transistor body. Prevention follows the same logic as bow control: bias pulsing to let the charge relax, a thicker sidewall film early in step 4 (ME1 with SiF₄), and a short BOX overetch.

---

## 14.2 Fill and Recess

### 14.2.1 The Three Recesses

```
Trench DRAM downstream (illustrative):

  After node dielectric:
  Fill 1: As-doped poly (or TiN + poly) fills the trench
    → Recess 1 to 1.20 µm (top of bottle; bottom of the collar)
  Collar formation in the upper trench (if not done before the bottle)
  Fill 2: doped poly
    → Recess 2 to ≈ 120 nm below the Si surface (top of the collar)
  Collar top removed (strap opening)
  Fill 3: undoped or lightly doped poly (buried strap)
    → Recess 3 to ≈ 50 nm below the Si surface
```

Each recess is an etch of polysilicon inside the trench to a depth set by time and endpoint, selective to the collar oxide and the pad nitride. They are covered in the companion volume *Recess Etch*; their dependence on the trench etch is the subject here.

### 14.2.2 What the Recesses Inherit

```
  Trench-etch feature        Effect on fill and recess
  ──────────────────────────────────────────────────────────────────────────
  Neck at the mouth          fill seals at the mouth first → seam or void
                             below; recess opens the void and the recess
                             front runs down the seam (recess too deep)
  Bow in the collar zone     the poly in the bow is shadowed; recess leaves
                             poly "ears" in the bow
  Trench depth variation     unchanged recess depths (measured from the
                             top), but the fill volume changes; no direct
                             effect
  Top CD variation           recess rate depends on width (recess ARDE);
                             ±3 nm CD → ±5–10 nm recess depth
  Rough walls                the poly grain structure follows; recess front
                             roughness ±5 nm
```

The recess depths are measured from the top of the trench, so trench depth does not enter them. Top CD and the neck do. A trench etch that reduces the neck by 2 nm can remove a void class that otherwise appears as recess-depth outliers at the strap.

---

## 14.3 Silicon Trench Capacitors

### 14.3.1 Geometry

```
Silicon trench capacitor (integrated passive device, illustrative):
  Trenches 1.5 µm wide, 3.0 µm pitch, 30 µm deep (A = 20:1)
  Square array; trench density ≈ 1.1×10⁵ per mm²
  Wall area per trench: 4 × 1.5 µm × 30 µm = 180 µm² (square trench)
  Dielectric: ONO or high-k, EOT 10 nm (high-voltage rating)
  C/A on the walls = ε₀ × 3.9 / 10 nm = 3.45 fF/µm²
  Wall area per mm² = 1.1×10⁵ × 180 µm² = 2.0×10⁷ µm² → 69 nF/mm²
    (plus top and bottom ≈ 4 nF/mm²)
  Multi-layer MIMIM stacks in the trench: 2–3× more
```

### 14.3.2 How the Etch Differs

```
                          eDRAM DT (R1)          Si trench capacitor
  ──────────────────────────────────────────────────────────────────────
  Width                   60–70 nm               0.5–3 µm
  Depth                   4–5 µm                 15–80 µm
  Aspect ratio            70–85                  10–40
  Chemistry               HBr/NF₃/O₂             Bosch SF₆/C₄F₈, or
                                                 cryogenic SF₆/O₂
  Rate                    0.9 µm/min average     5–20 µm/min
  Mask                    BSG 900 nm             resist or oxide, µm-thick
  Scallops                not acceptable         20–200 nm; smoothed by
                                                 oxidation
  Depth control           time + APC; ±2.4%      time; ±3–5%
  Open area               17% of wafer           30–50% of the device
                                                 area
```

At micrometre widths, the scallops of the Bosch process are a small fraction of the trench, and its rate and selectivity are unmatched. The problems shift: loading at 40% open area (the rate falls with exposed silicon), the trench-to-trench wall stiffness during wet processing, and wafer bow from the large volume of dielectric in the trenches.

---

## 14.4 Other Uses of the Same Etch

```
  Application                         Width       Depth       Note
  ──────────────────────────────────────────────────────────────────────
  Deep trench isolation (DTI) for     0.2–1 µm    3–10 µm     image sensors,
   image sensors and BCD/power                                high-voltage
                                                              isolation
  Trench MOSFET gates (power)         0.3–1 µm    1–3 µm      rounded bottom
                                                              critical
  Through-silicon vias (TSV)          2–10 µm     20–100 µm   Bosch
  Superjunction trenches              2–5 µm      30–50 µm    epitaxial refill
```

The DTI trench for image sensors is the closest relative of the DRAM trench: narrow, deep, and filled with oxide or polysilicon, with sidewall damage controlling dark current as sidewall roughness controls dielectric leakage here.

---

## Summary and Key Takeaways

1. **SOI adds a BOX step and a notch risk.** The insulating BOX charges like the mask and notches the silicon below it.

2. **SOI shortens the collar.** The BOX isolates the storage node from the transistor body.

3. **The recesses inherit the mouth.** Neck and bow, not depth, decide fill voids and recess outliers.

4. **Passive trench capacitors scale up the etch.** Micrometre-wide trenches tens of micrometres deep, etched by Bosch or cryogenic processes, give tens to hundreds of nF/mm².

5. **One etch, many products.** DTI, trench gates, TSVs, and superjunctions share the physics at different scales.

---

## Study Questions

1. Compute the time for the BOX step at 350 nm/min with 20% overetch.

2. Explain why the BOX sidewall charges and what bias change would reduce the notch.

3. A trench etch leaves a 3 nm neck per side. Sketch the poly fill and predict the recess-depth signature.

4. Recompute the capacitance density of the silicon trench capacitor for 1.0 µm trenches at 2.0 µm pitch, 30 µm deep.

5. Why is the Bosch process acceptable for silicon trench capacitors but not for the eDRAM trench?

---

**Next Chapter:** [Chapter 15: Modelling, Metrology & Advanced Process Control](./15-modelling-metrology-apc.md)

---

**Chapter 14 Development Status:** Complete  
**Version:** 1.0
