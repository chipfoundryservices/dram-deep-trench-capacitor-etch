# Chapter 8: Depth-Adaptive & Multi-Step Recipes

## Overview

A trench at 1 µm and a trench at 5 µm are different problems. At 1 µm the bottom sees plenty of fluorine and oxygen, the upper walls have been exposed for seconds, and the mask is thick. At 5 µm the bottom is starved, the upper walls have been exposed for minutes, and the mask is thin. A single recipe that suits one depth suits the other badly. Production deep-trench recipes are therefore written as functions of depth, in steps or ramps.

This chapter derives the reference three-step main etch, discusses gas pulsing and time-multiplexed (Bosch-type) etching and why they are not used for the 70 nm trench, and shows how depth is controlled without an etch stop.

**Learning Objectives:**
- Write a recipe whose parameters follow depth rather than time
- Compute step times from the time-to-depth model
- Compare continuous, stepped, gas-pulsed, and time-multiplexed etching
- Estimate scallop size and explain why Bosch etch does not suit nanoscale trenches
- Describe depth control by time, model, and metrology

---

## 8.1 What Should Change with Depth

```
  Depth zone      Problem                        Recipe response
  ─────────────────────────────────────────────────────────────────────────
  0–1.2 µm        little SiBrₓ from the bottom   add SiF₄; lower bias; slightly
  (collar zone)   → thin film on the walls       more O₂ → protect the collar
                  that will be exposed longest   wall from bow
  1.2–3.5 µm      balance                        reference conditions
  3.5–5.0 µm      F and O starved at bottom;     raise bias; raise NF₃; lower
                  rate falls; bottom narrows     O₂ → keep the bottom open
                                                 and the rate up
```

The upper wall is protected early, when it is new, and the lower trench is opened late, when the mask can no longer afford a long etch.

---

## 8.2 The Reference Main Etch

### 8.2.1 Steps

```
DT-R1 main etch, three steps (illustrative):

  Step   Depth (µm)   HBr   NF₃   O₂    SiF₄   Bias    Pressure
                      (sccm)                   (W)     (mTorr)
  ───────────────────────────────────────────────────────────────
  BT     native ox.   100   40    0     0      1200    10
  ME1    0 → 1.2      300   26    20    8      700     30
  ME2    1.2 → 3.5    300   30    18    3      900     30
  ME3    3.5 → 5.0    300   34    15    0      1100    28
  Source 2.5 kW, He 100 sccm, chuck +60 °C throughout
```

### 8.2.2 Step Times

The lumped model ER₀ = 1600 nm/min, k = 0.020 describes the whole stepped etch; the steps are chosen to hold it, not to change it. Step times come from t(h):

```
t(h) = [h + k h²/(2w)] / ER₀, w = 60 nm

  t(1.2 µm) = [1200 + 0.02 × 1.44×10⁶/120] / 1600 = 1440/1600 = 0.900 min = 54 s
  t(3.5 µm) = [3500 + 0.02 × 12.25×10⁶/120] / 1600 = 5542/1600 = 3.464 min = 208 s
  t(5.0 µm) = 9167/1600 = 5.729 min = 344 s

  ME1: 54 s;  ME2: 208 − 54 = 154 s;  ME3: 344 − 208 = 136 s
```

### 8.2.3 What the Steps Buy

```
Single-step at ME2 conditions vs three-step (illustrative, 5 µm):

                    Single step    Three step
  ───────────────────────────────────────────
  Bow (nm)          +6.5           +2.0
  Bottom CD (nm)    43             50
  Depth at 344 s    4.88 µm        5.00 µm
  BSG remaining     310 nm         300 nm
```

The three-step recipe takes the bow out of the collar zone and gains 120 nm of depth in the same time, for 10 nm of extra mask.

---

## 8.3 Continuous Ramps

Steps cause small discontinuities in the wall: a change of film balance leaves a ledge of 0.5–1 nm at each transition depth. A ramp removes it.

```
Ramped form of ME1–ME3 (illustrative):
  O₂(t)   = 20 − 5 × (t/344 s)          sccm
  Bias(t) = 700 + 400 × (t/344 s)^1.3    W
  SiF₄(t) = 8 × max(0, 1 − t/150 s)      sccm
```

Ramps need gas controllers and RF generators that track set points smoothly at 1 s resolution. The benefit is small for the trench itself but matters for the collar, whose oxide must lie flat against the upper wall.

---

## 8.4 Gas Pulsing and Time Multiplexing

### 8.4.1 Bosch-Type Etch

The Bosch process alternates a passivation step (C₄F₈, depositing a fluorocarbon film) with an etch step (SF₆, removing the film at the bottom and etching silicon isotropically). It dominates MEMS and through-silicon vias.

```
Scallop depth per cycle:
  Etch step removes Δz per cycle; the isotropic component undercuts the
  film by s ≈ (lateral/vertical ratio) × Δz

  MEMS TSV (5 µm wide): Δz ≈ 500 nm, s ≈ 100–200 nm  — acceptable
  Reference trench (70 nm wide): even Δz ≈ 20 nm, s ≈ 4–8 nm per side
    → 8–16 nm of scalloping on a 70 nm trench; 200+ cycles to 5 µm
```

At the trench scale, the scallops are a large fraction of the CD, each cycle's gas exchange takes longer than its useful etch, and the fluorocarbon film is hard to clear from the bottom of an 80:1 trench. Bosch etch is used for silicon trench capacitors with widths of 0.5–3 µm (Chapter 14), not for the DRAM trench.

### 8.4.2 Rapid Gas Pulsing

```
Fast-switching variant (illustrative): O₂ modulated 10 ↔ 25 sccm at 0.5 Hz
  over HBr/NF₃ base
  Film grows during high-O₂ phases; bottom clears during low-O₂ phases
  Scallop amplitude: < 0.5 nm (below roughness)
```

Gas pulsing gives a second control axis: the duty cycle sets the average balance while the amplitude sets how well the bottom is cleared. It reduces grass without opening the bow, at the cost of controller wear and of matching between chambers (Chapter 9).

### 8.4.3 Bias Pulsing

Pulsing the bias at 1–5 kHz with 50–80% duty lets the film grow in the off phase and lets negative charge on the mask relax. It reduces upper-wall bow by 1–2 nm and the local twist at the wafer edge (Chapter 11), at a rate cost of 10–15%.

---

## 8.5 Depth Without an Etch Stop

There is no layer at 5 µm. The process stops when the time ends. Depth control therefore rests on three things:

```
1. A model:  h(t, CD) from ER₀ t = h + k h²/(2w)
2. Feed-forward: measured post-open CD and BSG thickness per lot
   adjust the ME3 time:
     Δt_ME3 ≈ −(∂h/∂w × ΔCD) / ER_bottom
     ER_bottom at 5 µm = 1600 × 0.375 = 600 nm/min = 10 nm/s
     ΔCD = −2 nm → Δh = −52 nm → Δt = +5.2 s
3. Feedback: measured depth on a sample wafer per lot (IR or X-SEM)
   corrects ER₀ by EWMA (Chapter 15)
```

```
In-situ endpoint options (illustrative):
  Optical emission (SiBr, SiF): tracks the etch rate, not depth;
    useful for detecting the end of the breakthrough and for chamber
    health, not to stop the main etch
  Laser interferometry on a test pad: measures a wide feature, whose
    depth differs from the trench by ARDE
  IR interferometry through the wafer on an array target: research
    and some production use; resolution ≈ ±30 nm
```

The trench etch is one of the few major etches in the fab that is controlled entirely by time and model. Its depth precision depends on how well the model and the feed-forward represent the wafer.

---

## Summary and Key Takeaways

1. **Write the recipe against depth.** Protect the collar zone early; open the bottom late.

2. **Three steps, 344 s.** ME1 54 s, ME2 154 s, ME3 136 s; bow falls from 6.5 to 2 nm and depth rises 120 nm.

3. **Ramps remove ledges.** They matter most for the collar.

4. **Bosch is too coarse.** Scallops of several nanometres per side ruin a 70 nm trench; Bosch belongs to wide trench capacitors and TSVs.

5. **Time is the endpoint.** Feed-forward of CD and feedback of depth replace the missing etch stop.

---

## Study Questions

1. Compute the ME3 time for a 5.2 µm target and for a lot whose top CD is 72 nm.

2. A ledge of 1 nm at each step transition is unacceptable for the collar. Which transition matters, and how would you ramp across it?

3. Estimate the number of Bosch cycles and the total gas-exchange time for a 5 µm trench with Δz = 20 nm and a 1.5 s exchange per step.

4. Why can optical emission not be used to stop the main etch at depth?

5. A lot shows BSG 30 nm thinner than nominal. Should the ME3 time change? What should change?

---

**Next Chapter:** [Chapter 9: Chamber Conditioning, By-Product Control & Fleet Matching](./09-chamber-conditioning-fleet-matching.md)

---

**Chapter 8 Development Status:** Complete  
**Version:** 1.0
