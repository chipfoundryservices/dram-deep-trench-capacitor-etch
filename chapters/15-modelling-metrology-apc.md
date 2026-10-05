# Chapter 15: Modelling, Metrology & Advanced Process Control

## Overview

The deep trench has no etch stop, so its depth is only as good as the model that sets its time. Its profile cannot be seen from above, so it is only as well known as the few cross-sections and the scatterometry that stand for it. This chapter assembles the control system: the models that predict depth and profile, the metrology that calibrates them, and the feed-forward and feedback loops that hold depth to ±0.12 µm across thirteen chambers.

**Learning Objectives:**
- Choose a model level — lumped, reduced-order, feature-scale — for a given decision
- Compare depth and profile metrology for 5 µm trenches
- Build a feed-forward correction from incoming CD and mask thickness
- Run EWMA feedback on ER₀ with per-chamber offsets
- Use virtual metrology to fill gaps between measurements

---

## 15.1 Models

### 15.1.1 Three Levels

```
  Level            Form                                  Use
  ──────────────────────────────────────────────────────────────────────────
  Lumped           ER₀ t = h + k h²/(2w)                 time setting, APC,
                   two parameters per chamber            CD-to-depth
  Reduced-order    1-D along the trench: ion and         profile response to
                   neutral fluxes by depth; film         recipe changes;
                   balance per depth (Chapter 6.1)       DOE design
  Feature-scale    Monte Carlo particle transport +      bow, twist, notch,
                   level-set surface evolution in 2-D    grass; new recipes;
                   or 3-D                                failure analysis
```

### 15.1.2 Calibrating the Lumped Model

```
Fit ER₀ and k from depth measured at three times on one chamber
(illustrative R1 data, top CD 70, w̄ 60):

  t (min)   h measured (µm)    h model (ER₀ 1600, k 0.020)
  ───────────────────────────────────────────────────────
  1.67        2.00               2.00
  4.17        4.01               4.00
  5.73        4.99               5.00

Rearranged for a linear fit: ER₀ t/h = 1 + (k/2w) h
  → plot t/h against h: intercept 1/ER₀, slope k/(2w ER₀)
```

The linearization makes calibration a straight-line fit. A chamber whose slope rises (k up) while the intercept holds has lost bottom transport — usually a profile change, such as more taper from wall drift — not a source change.

### 15.1.3 Feature-Scale Models

A 3-D feature-scale model of the reference trench tracks about 10⁷ particles per microsecond of etch time across a grid of 1 nm cells. It reproduces the bow from facet reflections and the twist from film asymmetry when given realistic mask roughness. Its role is not production control but explaining failures and screening recipes before costly DOEs. A model calibrated to TEM profiles at three depths predicts the bow within ±1 nm and the bottom CD within ±2 nm across the DOE space of Chapter 6.

---

## 15.2 Metrology

```
  Method                       Measures                Precision        Speed
  ───────────────────────────────────────────────────────────────────────────────
  IR reflectometry /           array average depth      ±20–30 nm       inline,
   IR scatterometry (FTIR)     (effective-medium                          ≈ 1 min/site
                               model of the trench
                               layer)
  OCD (visible/UV              top CD, upper profile;   ±0.5 nm CD      inline
   scatterometry)              little sensitivity
                               below ≈ 1 µm
  CD-SEM (top-down)            top CD at the mouth;     ±0.7 nm         inline
                               BSG facet
  X-SEM                        full profile, depth,     ±3 nm, ±20 nm   offline,
                               bow, bottom              depth           destructive
  TEM                          film, bottom shape,      ±0.5 nm         days
                               roughness
  CD-SAXS (transmission        average profile          ±0.5 nm         slow; lab
   X-ray scattering)           through the full depth                   or pilot
  Electrical (short-loop       capacitance, leakage     ±1%             after module
   arrays)
```

### 15.2.1 IR Depth

Silicon is transparent in the mid-infrared. The trench layer, a mixture of silicon and empty volume, behaves as an effective medium with a refractive index between those of silicon and vacuum. Reflections from its top and bottom interfere, and the fringe spacing gives its thickness — the trench depth:

```
Effective index of the trench layer (illustrative):
  Fill fraction f ≈ 0.35 (array open fraction averaged over depth)
  n_eff² ≈ (1 − f) × n_Si² + f × 1 (simple mixing)
        = 0.65 × 11.7 + 0.35 = 7.96 → n_eff ≈ 2.8
Fringe spacing in wavenumber: Δν = 1/(2 n_eff h)
  h = 5 µm: Δν = 1/(2 × 2.8 × 5×10⁻⁴ cm) ≈ 357 cm⁻¹
```

The fit uses a full model with taper (a graded fill fraction). Its accuracy depends on knowing the profile: a change in taper changes n_eff with depth and biases the depth. IR depth is therefore calibrated against X-SEM for each recipe and rechecked when the profile changes.

---

## 15.3 Feed-Forward

```
Inputs per lot (measured after the mask open):
  ΔCD = CD_measured − 70 nm (top minor, CD-SEM or OCD)
  ΔBSG = BSG_measured − 820 nm (after strip)

ME3 time adjustment (Chapter 8.5):
  Δt_ME3 = −(∂h/∂w × ΔCD) / ER_bottom
  ER_bottom (5 µm, R1) = 600 nm/min = 10 nm/s, ∂h/∂w = 26 nm/nm
  → Δt_ME3 = −2.6 s × ΔCD [nm]

Mask check:
  Predicted BSG at end = BSG_measured − 20 − 500 × (1 + Δt/344)
  Hold the lot if < 200 nm
```

### 15.3.1 Radial Feed-Forward

A centre-to-edge CD signature cannot be corrected by time. It is corrected by the radial knobs of the etch (coil split, chuck zones; Chapter 5.2.2), using a per-lot radial CD profile from the mask open:

```
Radial CD signature +2 nm at the edge → +52 nm depth at the edge
Compensation: reduce the edge rate by ≈ 1% (≈ 50 nm at 5 µm), e.g. by an
  outer coil current change of ≈ −0.8% (illustrative sensitivity)
```

---

## 15.4 Feedback

```
EWMA on ER₀ per chamber (illustrative):
  ER₀,est(n+1) = λ × ER₀,meas(n) + (1 − λ) × ER₀,est(n),  λ = 0.3
  ER₀,meas from IR depth on one wafer per lot, corrected for that lot's CD
  Main-etch time for the next lot: t = [h_target + k h_target²/(2w)] / ER₀,est

Per-chamber state:
  ER₀ offset (from matching, Chapter 9.5)
  k (updated slowly, from the t/h fit monthly)
  Edge-ring RF hours (tilt and edge depth)
  Window RF hours (source coupling)
```

```
Performance (illustrative, R1 fleet):
  Depth 3σ lot-to-lot without APC:            ±0.21 µm
  With EWMA only:                             ±0.15 µm
  With feed-forward CD + EWMA:                ±0.10 µm
  With radial feed-forward + consumable       ±0.08 µm
   offsets
```

The ±0.12 µm specification needs feed-forward. Feedback alone cannot remove the CD-driven depth variation, because it arrives lot by lot from the mask open.

---

## 15.5 Virtual Metrology

Only one wafer per lot is measured for depth. The other 24 are predicted from chamber data:

```
Virtual-metrology inputs (illustrative):
  OES: SiBr (≈ 425 nm) intensity during ME2–ME3 → Si removal rate
  OES: O (777 nm)/Ar, F (704 nm)/Ar → wall state
  RF: bias voltage and current, source match positions
  He leak rate, chuck temperatures
  Wafer position in the lot; time since WAC; RF hours

Model: partial least squares on ≈ 40 features
  Predicted depth error: ±35 nm (1σ ≈ 12 nm) against IR measurement
```

The SiBr emission is the most valuable single signal: it is proportional to the silicon removal rate over the whole wafer, which for a fixed pattern is proportional to the trench etch rate. A wafer whose SiBr integral is 2% low has etched about 2% less silicon and is flagged for measurement.

---

## Summary and Key Takeaways

1. **Three model levels.** Lumped for time, reduced-order for recipe response, feature-scale for failures and new recipes.

2. **Linearize to calibrate.** t/h against h gives ER₀ and k from a straight line.

3. **IR measures depth through the silicon.** It needs a profile-aware effective-medium model calibrated to X-SEM.

4. **Feed-forward CD is mandatory.** −2.6 s per nanometre of CD in ME3; feedback alone leaves ±0.15 µm.

5. **SiBr emission is the virtual depth gauge.** It integrates the silicon removed on every wafer.

---

## Study Questions

1. Using the t/h linearization, compute ER₀ and k from the points (2.0 min, 2.30 µm) and (6.0 min, 5.10 µm) with w = 60 nm.

2. A lot arrives with ΔCD = −1.5 nm and ΔBSG = −40 nm. Compute the ME3 adjustment and the predicted remaining BSG.

3. The taper increases so that the bottom CD falls from 50 to 44 nm. How does IR depth respond, and what should be done before trusting it?

4. Why can EWMA feedback not remove the depth variation caused by the mask-open CD?

5. Propose three virtual-metrology features that would detect edge-ring wear.

---

**Next Chapter:** [Chapter 16: Yield, Retention & Cost of Ownership](./16-yield-retention-cost.md)

---

**Chapter 15 Development Status:** Complete  
**Version:** 1.0
