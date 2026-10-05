# Chapter 6: Passivation Engineering & Profile Control

## Overview

The profile of a deep trench is the record of a balance between the film that grows on its walls and the ions and fluorine that remove it (Chapter 3). The balance changes with depth, across the wafer, and as the chamber walls age. This chapter turns the balance model into a set of engineering levers: what each gas, power, and temperature does to the taper, the bow, the bottom shape, and the roughness, and how the reference recipe was centred.

**Learning Objectives:**
- Relate sidewall angle to the net film balance at each depth
- Use O₂, SiF₄, NF₃, bias, and temperature to move taper and bow independently
- Explain the origin of sidewall roughness and striations in a silicon trench
- Design a profile DOE and read its response surface

---

## 6.1 From Film Balance to Sidewall Angle

```
Local lateral position of the wall x(z) evolves as:
  dx/dt = R_lat(z) − D(z)

  R_lat  lateral etch of the wall: spontaneous F through a thin or broken
         film, plus grazing ions (positive outward)
  D      net film deposition (positive inward)

The wall angle at depth z relative to vertical:
  tan α(z) ≈ ∫ (dx/dt) dt / (time the wall at z has been exposed)
```

A wall element near the top has been exposed for the whole etch; one near the bottom for a few seconds. **The top of the trench integrates its history.** A small net deposition rate at the top becomes taper; a small net lateral rate becomes bow.

```
Reference R1 (illustrative):
  Top minor CD 70 nm, bottom 50 nm, depth 5000 nm
  Net per-side inward movement averaged over the depth: 10 nm
  Equivalent: D − R_lat ≈ 10 nm over a mean exposure of ≈ 3 min
  → ≈ 3 nm/min of net deposition averaged over the wall
```

The trench closes by 20 nm over its depth because the net balance is only slightly on the deposition side. Three nanometres per minute out of a process removing 1600 nm/min vertically: the profile is set by a 0.2% imbalance.

---

## 6.2 The Levers

### 6.2.1 Response Table

```
Profile response to ±10% changes about the R1 centre (illustrative):

  Lever (+10%)        Top CD   Bow     Bottom CD   Depth    Roughness
                      (nm)     (nm)    (nm)        (nm)
  ──────────────────────────────────────────────────────────────────────
  O₂ flow             0        −1.0    −3.0        −120     +0.1
  NF₃ flow            +0.5     +1.5    +2.0        +150     +0.2
  HBr flow            0        −0.3    −0.5        +40      −0.1
  SiF₄ (5 → 5.5)      0        −0.5    −1.5        −40      0
  Bias power          +0.3     +1.2    +1.5        +110     −0.1
  Source power        +0.2     +0.4    +0.5        +80      0
  Pressure            0        +0.8    −1.0        −60      +0.2
  Chuck temperature   +0.3     +1.0    +0.5        +20      +0.1
   (+6 °C)
```

### 6.2.2 Reading the Table

1. **O₂ is the taper lever.** It closes the bottom three times faster than it straightens the bow. A fab that fights bow with O₂ also narrows the bottom and loses depth.
2. **NF₃ and bias open everything.** Both raise depth; both raise bow. They are the rate levers, used together with O₂ to hold the profile.
3. **SiF₄ thickens the film where products are scarce.** It adds silicon to the gas phase so the film can grow near the top early in the etch, when the trench is shallow and SiBrₓ from the bottom is little. Its main use is in the first minute.
4. **Pressure moves bow.** Higher pressure broadens the ion angle (more collisions), and broad ions strike the upper wall.
5. **Temperature moves bow and lateral etch.** It also moves radially across the chuck zones, making it the main radial-profile knob.

---

## 6.3 Separating Bow from Taper

Bow and taper respond to the same levers in the same direction, but with different ratios:

```
Ratio bow/bottom-CD response:
  O₂:        −1.0 / −3.0 = 0.33
  Bias:      +1.2 / +1.5 = 0.80
  Pressure:  +0.8 / −1.0 = opposite signs
```

Pressure is the only lever that moves the two in opposite directions. Lowering pressure by 10% reduces bow 0.8 nm and opens the bottom 1 nm. Combined with a small O₂ increase to restore the bottom, it straightens the upper trench without closing the lower one. The reference recipe was moved from 35 to 30 mTorr for this reason.

---

## 6.4 Sidewall Roughness

### 6.4.1 Sources

```
  Source                              Signature                Scale
  ──────────────────────────────────────────────────────────────────────────
  Mask line-edge roughness            vertical striations      LER 2–3 nm →
   transferred                        running the full depth   0.6–1.5 nm
  Film islands (non-uniform           pits and bumps           1–3 nm
   nucleation)
  Bosch-like cycling if gas pulsing   horizontal scallops      0.5–5 nm
   is used (Chapter 8)
  Crystallographic etching            facets on {111} near     at the bottom
                                      the bottom
```

### 6.4.2 Why It Matters

Roughness on the trench wall becomes roughness on the node dielectric. A 1 nm bump on a 2.5 nm EOT dielectric concentrates the field; the leakage of the whole trench is set by its roughest points. Striations also spoil specular ion reflection, so a rough trench etches more slowly at depth and bows more (Chapter 10). After the etch, a light oxidation and HF strip can smooth the wall by about a third, and the bottle etch (Chapter 13) changes the roughness again.

---

## 6.5 Crystallography

The wafer is ⟨100⟩, and the trench major axis is aligned to ⟨110⟩. Silicon etched by ions is nearly isotropic in crystal terms, but the spontaneous component is not: fluorine and especially wet chemistry etch {111} planes more slowly. In the ion-dominated main etch the trench walls are nearly round. At the bottom, where ion flux falls and the film is thin, the round bottom can develop faint facets. In the bottle etch, which is largely chemical, crystallography dominates (Chapter 13).

---

## 6.6 Centring the Recipe

### 6.6.1 A Profile DOE

```
Central composite design, 4 factors (O₂, NF₃, bias, pressure), 25 runs
Responses: top CD, bow, CD at 2.5 µm, bottom CD, depth, mask remaining,
           roughness (TEM), grass count (SEM)
Fitted to quadratic models (R² 0.85–0.97 for geometric responses)
```

### 6.6.2 Constraints

```
Feasible region (R1, illustrative):
  Bow ≤ +5 nm               → bias ≤ 1000 W at 30 mTorr
  Bottom CD ≥ 40 nm         → O₂ ≤ 21 sccm
  Grass = 0                 → NF₃ ≥ 25 sccm, O₂ ≤ 20 sccm
  Mask ≥ 150 nm             → bias ≤ 1100 W
  Depth 5.0 µm in ≤ 6 min   → NF₃ ≥ 27 sccm at 900 W
```

The feasible window is a narrow lens: O₂ 16–20 sccm and NF₃ 27–34 sccm at 900 W. The centre (18/30) sits about 10% from the nearest edge in each direction. Chamber drift of 5% uses half of that, which is why the recipe needs the conditioning and matching of Chapter 9.

---

## Summary and Key Takeaways

1. **A 0.2% imbalance sets the profile.** Net deposition of ≈ 3 nm/min closes the trench by 20 nm over 5 µm.

2. **The top integrates history.** Upper walls see the whole etch; small rates become large taper or bow.

3. **O₂ for taper, NF₃ and bias for rate, pressure for bow.** Pressure is the only lever that moves bow and bottom CD in opposite directions.

4. **Roughness becomes leakage.** Mask LER and film islands print on the wall and later on the node dielectric.

5. **The window is narrow.** About ±10% on O₂ and NF₃; chamber drift uses half of it.

---

## Study Questions

1. A trench is 70 nm at the top and 56 nm at the bottom. Estimate the net average deposition rate on the walls.

2. Using the response table, find a combination of O₂ and pressure changes that reduces bow by 1.5 nm while keeping the bottom CD constant.

3. Why is SiF₄ most useful at the start of the etch?

4. Mask LER improves from 3 nm to 2 nm. Estimate the change in sidewall roughness and discuss the effect on dielectric leakage.

5. The chamber wall ages and the O recombination probability falls, raising the O flux to the wafer by 8%. Predict the profile change and the compensating NF₃ adjustment.

---

**Next Chapter:** [Chapter 7: Cryogenic Deep Silicon Etch](./07-cryogenic-deep-silicon-etch.md)

---

**Chapter 6 Development Status:** Complete  
**Version:** 1.0
