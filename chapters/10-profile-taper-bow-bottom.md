# Chapter 10: Profile — Taper, Bow, Necking & the Bottom Shape

## Overview

The reference trench narrows from 70 nm at the top to 50 nm at the bottom, almost linearly, with a rounded floor. Every departure from that shape costs something specific. Bow spends the silicon wall that the bottle needs. A neck under the pad nitride shadows the trench and later traps a void in the fill. Excess taper closes the bottom and loses depth and capacitance. A pointed or microtrenched bottom concentrates the electric field across the node dielectric. This chapter takes each feature in turn: its cause, its measurement, its downstream cost, and its control.

**Learning Objectives:**
- Describe the reference profile and its tolerances
- Explain the origin of upper bow and its link to the mask facet and charging
- Explain necking at the pad-nitride interface
- Relate taper to depth loss and capacitance
- Describe the bottom shapes produced by different ion and film balances

---

## 10.1 The Reference Profile

```
Minor-axis CD versus depth (DT-R1 reference, illustrative):

  Depth (µm)    0     0.2    0.5    1.0    2.0    2.5    3.0    4.0    4.8    5.0
  CD (nm)       70    71     71     69     65     63     61     57     53     rounded
                      (bow +1 at 0.2–0.5 µm)

  Average CD over depth: ≈ 60 nm
  Sidewall angle (0.5–4.8 µm): ≈ 89.9°
```

The profile has three zones: a short bow just below the pad films, a long near-linear taper, and a rounded bottom of radius about 25 nm along the minor axis.

---

## 10.2 Bow

### 10.2.1 Where It Comes From

```
  Source                              Depth of maximum bow
  ───────────────────────────────────────────────────────────────
  Ions reflected from the mask facet  0.1–0.5 µm below the Si surface
   (Chapter 2.4)
  Low-energy ions deflected by the    0.1–0.8 µm
   negatively charged BSG wall
   (Chapter 4.2)
  Broad (collisional) ions            0–1 µm, spread
  Thin film early in the etch,        0–0.3 µm
   before products accumulate
   (Chapter 6.2)
```

All four act on the upper micrometre of the trench, which is the collar zone. The bow does not grow below 1 µm, because the film there is thick enough and the ions arriving at the wall are already the narrow population.

### 10.2.2 What Bow Costs

```
Bow of b nm per side at depth z_b:
  • Silicon wall along the minor axis: 110 − 2b nm at z_b
  • Collar oxide deposited into a bowed trench is thicker at the bow;
    the collar recess (Chapter 14) leaves a cusp
  • The buried strap forms against the upper wall; bow moves the strap
    contact outward and changes its resistance
```

The collar zone has no bottle, so bow does not threaten merging directly. Its cost is in the collar and strap. The specification allows ≤ 5 nm of bow (CD at the bow ≤ 75 nm); the reference recipe gives about 1–2 nm.

### 10.2.3 Control

```
  Lever                                        Bow change
  ──────────────────────────────────────────────────────────────
  ME1 with SiF₄ and lower bias (Chapter 8)     −4.5 nm
  Pressure 35 → 30 mTorr                       −0.8 nm (×1.7 for 5 mTorr)
  Bias pulsing, 70% duty, 2 kHz                −1.5 nm
  BSG facet reduced (harder mask open)         −1.0 nm
  Chuck −10 °C                                 −1.7 nm
```

---

## 10.3 Necking

A neck is a local narrowing at the top of the trench, usually where the silicon meets the pad oxide. Its causes are redeposition of SiOₓBrᵧ on the pad SiN and BSG sidewall early in the etch, and the slight undercut of pad oxide during the mask open.

```
Reference neck (illustrative): ≈ 2 nm per side at 0–30 nm below the Si surface
Effect: the trench mouth is narrower than the trench at 0.2 µm by ≈ 4 nm
```

The neck matters most for the fill. A poly or TiN fill deposited into a trench whose mouth is narrower than its interior closes at the mouth first and leaves a seam or void below (Chapter 14). After the bottle widens the lower trench, the ratio of mouth to interior becomes much larger, which is why the collar and fill sequence was designed around it.

---

## 10.4 Taper

### 10.4.1 Taper and Depth

Taper narrows the trench as it deepens, and a narrower trench etches more slowly:

```
For a linear taper from w_top to w_bot over H, ARDE uses the local width.
Effect of reducing the bottom CD from 50 to 44 nm at constant top CD:
  w̄ from 60 to 57 nm → depth at fixed time −(∂h/∂w × 3) ≈ −78 nm
  Plus the narrower bottom loses rate in the last µm: ≈ −30 nm
  Total ≈ −110 nm → −0.6 fF
```

### 10.4.2 Taper and the Bottle

The bottle etch widens the lower trench by a fixed amount per side. A trench that is narrower at the bottom stays narrower after the bottle, and its perimeter — the capacitance — is smaller:

```
Bottle perimeter at mid-bottle vs bottom CD (illustrative):
  Reference (bottom CD 50): as-etched 61 × 97 nm at mid-bottle
    → 110 × 150 nm after 25 nm per side → perimeter 411 nm
  Bottom CD 44 (mid-bottle as-etched ≈ 58 × 94 nm)
    → 107 × 147 nm → perimeter ≈ 401 nm → −2.4% → −0.5 fF
```

Taper therefore costs capacitance twice: through depth and through perimeter.

---

## 10.5 The Bottom

### 10.5.1 Bottom Shapes

```
  Shape           Cause                                Risk
  ────────────────────────────────────────────────────────────────────────
  Rounded         balanced ions and film (reference)   none
  (r ≈ w/2)
  Flat with       ions reflected off the lower walls   field concentration at
  microtrenches   concentrate at the bottom corners;   the corners; dielectric
                  film thin at the corners             breakdown; poly voids
  Pointed (V)     excess film; ions reach only the     lost area; field at the
                  centre; low bias at depth            tip; local thinning of
                                                       the node dielectric
  Faceted         chemistry-dominated at low ion flux  mild; follows {111}
  {111}
```

### 10.5.2 Field Concentration

```
Field enhancement at a convex tip of radius r with dielectric thickness t:
  E_tip / E_flat ≈ (r + t)/r = 1 + t/r   (spherical tip)

  r = 25 nm (rounded reference), t ≈ 4 nm physical:  1.16
  r = 5 nm (pointed), t ≈ 4 nm:                     1.8
  r = 2 nm (microtrench corner, concave/convex mix): ≈ 2–3
```

Leakage through a high-k dielectric rises steeply with field; a factor of 1.8 in local field can raise local leakage by orders of magnitude. The bottom of the trench is a small area, but its shape decides the retention tail of trenches with defective bottoms. ME3 is tuned to keep the bottom rounded: higher bias and less O₂ round it; too much bias makes microtrenches.

---

## 10.6 Measuring the Profile

```
  Method                       Resolution   Throughput        Sees
  ─────────────────────────────────────────────────────────────────────────
  X-SEM (cleave)               2–3 nm       destructive,      a few trenches
                                            hours
  TEM (FIB lamella)            0.5 nm       destructive, day  film, bottom shape
  OCD / IR scatterometry       ±1 nm CD,    inline, minutes   array average
   on array                    ±20 nm depth
  CD-SAXS                      ±0.5 nm      slow; lab or      average profile
                                            some fabs         incl. bow
```

Chapter 15 describes how these combine with models for control.

---

## Summary and Key Takeaways

1. **Three zones.** A small bow below the pad films, a long linear taper, a rounded bottom.

2. **Bow lives in the collar zone.** It comes from facet reflections, mask charging, and early thin film; it costs collar and strap margin.

3. **The neck shapes the fill.** A mouth narrower than the interior seals first and leaves a void.

4. **Taper costs capacitance twice.** Through ARDE depth and through bottle perimeter.

5. **The bottom sets the leakage tail.** Pointed and microtrenched bottoms concentrate the field 1.8–3 times.

---

## Study Questions

1. A trench shows 6 nm of bow per side at 0.3 µm. Compute the silicon wall at that depth and propose two recipe changes to recover the specification.

2. Estimate the depth and capacitance cost of reducing the bottom CD from 50 to 40 nm.

3. Explain why microtrenches form at the bottom corners when the bias rises.

4. Compute the field enhancement at a bottom tip of radius 8 nm under a 4 nm dielectric.

5. Which profile features can OCD measure reliably on the array, and which require TEM?

---

**Next Chapter:** [Chapter 11: Twist, Tilt, Merging & Placement](./11-twist-tilt-merging-placement.md)

---

**Chapter 10 Development Status:** Complete  
**Version:** 1.0
