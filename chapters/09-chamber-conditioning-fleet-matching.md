# Chapter 9: Chamber Conditioning, By-Product Control & Fleet Matching

## Overview

Every wafer leaves nearly two grams of silicon bromide behind it, partly on the chamber walls (Chapter 5). The walls in turn decide how much oxygen and fluorine reach the wafer, because O and F recombine on them at rates that depend on what covers them. A deep-trench chamber is therefore never in the same state twice unless it is made so. This chapter describes the waferless clean that resets the walls every wafer, the seasoning after a wet clean, the drift between cleans, the particles, and the matching of a dozen chambers to the same depth.

**Learning Objectives:**
- Explain how wall coverage changes the O and F fluxes to the wafer
- Design a waferless auto-clean and estimate its duration
- Describe seasoning after a wet clean and first-wafer effects
- Identify the particle sources and their yield signatures
- Set up a matching method for depth, CD, and profile across a fleet

---

## 9.1 The Wall as a Reactant

### 9.1.1 Recombination

```
Atomic O and F are lost on the walls by recombination with probability γ:

  Wall state                      γ_O       γ_F       Effect at the wafer
  ─────────────────────────────────────────────────────────────────────────
  Clean Y₂O₃ / anodized Al        0.02      0.01      reference
  SiOₓBrᵧ-coated (after 1 wafer)  0.005     0.02      O ↑, F ↓ →
                                                      more taper, slower
  Thick SiOₓBrᵧ (no clean, 25     0.003     0.03      further taper; rate
   wafers)                                            −5%; bottom CD −6 nm
  Fluorinated (after NF₃ clean)   0.03      0.005     O ↓, F ↑ → bow,
                                                      faster (first wafer)
```

The coated wall is a poor sink for O and a better sink for F. As the coating thickens, the wafer receives more O and less F: the trench tapers and slows. Without a clean, the depth drifts by about 60 nm and the bottom CD by 6 nm over a lot. That is half the depth budget.

### 9.1.2 Measuring the Wall

```
Wall-state monitors (illustrative):
  OES ratio O (777 nm) / Ar actinometer: rises as γ_O falls
  OES ratio F (704 nm) / Ar: falls as γ_F rises
  RF: source-match position and coil current drift with window coating
  Pressure-control valve position: changes with deposition in the throttle
```

---

## 9.2 Waferless Auto-Clean

```
WAC after every wafer (illustrative, 60 s):
  Step 1: NF₃/O₂ 300/50 sccm, 2 kW source, no bias, 20 s
          → removes SiOₓBrᵧ from walls and window as SiF₄, Br₂, O
  Step 2: O₂ 400 sccm, 2 kW, 15 s → removes residual C and Br
  Step 3: Season: HBr/O₂/SiF₄ 200/20/20 sccm, 1.5 kW, 25 s
          → deposits a thin, controlled SiOₓBrᵧ film so the next wafer
            starts on a coated, not a fluorinated, wall
```

Step 3 is the essential one. A clean that ends on a fluorinated wall gives a first wafer that bows and over-etches. A clean that ends with a thin seasoning film gives every wafer the same start. The seasoning film must be thin enough that the next WAC removes it fully, so that deposition does not accumulate between wet cleans.

```
Clean-time check (illustrative):
  Film per wafer on walls: ≈ 15 nm SiOₓBrᵧ near the wafer plane
  WAC Step 1 removal rate on the wall: ≈ 1.2 nm/s → 20 s removes 24 nm
  Margin: 60%; seasoning adds ≈ 3 nm, removed next cycle
```

---

## 9.3 Wet Clean and Seasoning

```
Preventive maintenance (illustrative):
  Wet clean every ≈ 400 RF hours (≈ 3000 wafers)
  Replace: liner, edge ring, window (or re-coat)
  Recovery: pump-down, leak check, 25 seasoning wafers (bare Si with
    the DT recipe), 2 monitor wafers for rate and particles,
    1 patterned qualification wafer for depth, CD, profile
  Downtime ≈ 10–12 h
```

The first few seasoning wafers etch differently because the new liner is bare. Depth on the patterned qualification wafer must fall within ±40 nm of the chamber's pre-clean baseline before production resumes.

---

## 9.4 Particles

```
  Source                      Particle               Yield signature
  ─────────────────────────────────────────────────────────────────────────
  Window/coil-side flakes     SiOₓBrᵧ, 0.1–1 µm      blocked trenches:
                                                     shallow or missing
                                                     DT → low-C bits,
                                                     clusters
  Edge-ring erosion           Si, SiC, quartz        edge-die blocked DT
  Chuck surface wear          Al₂O₃/AlN              backside; He leak;
                                                     temperature drift
  Condensed SiBr₄ in          liquid/solid droplets  random blocked DT
   transfer chamber (cold
   spots)
  Grass fragments from        Si needles             bridging in the bottle;
   neighbouring open areas                           poly-fill voids
```

A particle that lands on the mask during the etch blocks one or several trenches. Because the trench is etched first, a blocked trench is invisible until electrical test, when it appears as a cell with low capacitance or as a cluster of failing bits. Particle adders on a bare-silicon monitor are held below about 10 per wafer at ≥ 45 nm.

---

## 9.5 Fleet Matching

### 9.5.1 What Must Match

```
Chamber-to-chamber matching targets (3σ across the fleet, illustrative):
  Depth at fixed time (array):        ±40 nm
  Top minor CD:                       ±1 nm
  Bottom CD:                          ±2 nm
  Bow:                                ±1.5 nm
  BSG remaining:                      ±20 nm
  Radial depth signature (C–E):       ±25 nm
```

### 9.5.2 Hardware Sources of Mismatch

```
  Source                                   Typical effect on depth
  ──────────────────────────────────────────────────────────────────
  Coil and match differences               ±1.5% density → ±40 nm
  Bias generator calibration (±2%)         ±25 nm
  Chuck temperature calibration (±2 °C)    ±15 nm, bow ±0.7 nm
  Gas MFC calibration (O₂ ±2%)             ±25 nm, bottom CD ±0.6 nm
  Edge-ring wear                           edge depth −50 nm at end of life
  Window coating at PM                     ±20 nm
```

### 9.5.3 Matching Method

```
1. Hardware: calibrate RF (delivered power at the chuck with a V–I probe),
   MFCs, chuck temperature against a reference set
2. Chamber fingerprint: OES spectra and RF parameters on a standard
   wafer; fingerprint distance from the fleet golden reference
3. Etch: blanket Si rate and BSG rate on monitors (±1.5%)
4. Patterned: depth and CD on a short-loop DT wafer per chamber weekly
5. Tuning: per-chamber ME3 time offset and O₂ offset in the APC system
   (Chapter 15), not separate recipes
```

The per-chamber time offset absorbs most depth mismatch, but it cannot absorb profile mismatch. A chamber that bows more must be corrected in hardware or by the O₂ offset, because a longer or shorter etch does not change the bow.

---

## Summary and Key Takeaways

1. **The wall is a reactant.** SiOₓBrᵧ coating raises O and lowers F at the wafer; without cleans, depth drifts 60 nm per lot.

2. **Clean and season every wafer.** NF₃/O₂ removal followed by a thin, controlled seasoning film gives every wafer the same start.

3. **Wet clean every ≈ 3000 wafers.** Recovery needs 25 seasoning wafers and a patterned qualification.

4. **Particles become missing trenches.** They are invisible until electrical test.

5. **Match with time offsets; fix profiles in hardware.** Time corrects depth, not bow.

---

## Study Questions

1. A WAC step 1 is shortened to 15 s to gain throughput. Will the walls accumulate film? Estimate the residue after 25 wafers.

2. After a PM the first wafer bows by 3 nm more than the baseline. Which wall state explains it, and how would you change the seasoning?

3. Using the hardware mismatch table, estimate the RSS depth mismatch and compare it with the ±40 nm target.

4. Why must a chamber that bows more be corrected by gas flow or hardware rather than by time?

5. Describe the electrical signature of a 0.3 µm particle that lands on the mask in the first second of the main etch.

---

**Next Chapter:** [Chapter 10: Profile — Taper, Bow, Necking & the Bottom Shape](./10-profile-taper-bow-bottom.md)

---

**Chapter 9 Development Status:** Complete  
**Version:** 1.0
