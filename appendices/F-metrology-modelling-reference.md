# Appendix F: Metrology & Modelling Reference

Metrology methods, sampling plans, and model forms for the deep-trench etch. Precision values are representative for the reference trench.

---

## F.1 Metrology Methods

```
Method              Measures                        Precision (3σ)    Throughput    Destructive
─────────────────────────────────────────────────────────────────────────────────────────────────
CD-SEM top-down     top CD after open and etch;     ±0.7 nm           ≈ 30 s/site   no
                    BSG facet width
OCD (UV–vis)        top CD, BSG, upper 1 µm         ±0.5 nm CD        ≈ 10 s/site   no
                    profile
IR (FTIR)           depth (effective medium)        ±20–30 nm         ≈ 60 s/site   no
 reflectometry
CD-SAXS             average full-depth profile,     ±0.5 nm CD;       minutes/site  no
                    bow, taper                      ±15 nm depth
X-SEM               full profile, depth, tilt       ±3 nm, ±20 nm     hours         yes
TEM / STEM-EDS      film composition, bottom        ±0.5 nm           days          yes
                    shape, roughness
Planar delayer +    merging, twist at chosen        ±2 nm position    days          yes
 SEM                depth
Voltage contrast    blocked / shallow trenches      10⁻⁹ rate         hours/wafer   no
 (after fill)
Short-loop arrays   capacitance, leakage, node-     ±1% C             after module  no
                    to-node shorts
```

---

## F.2 Sampling Plan (Illustrative)

```
Per lot:      CD-SEM after open, 2 wafers × 9 sites (feed-forward)
              BSG thickness, 1 wafer × 9 sites (feed-forward)
              IR depth after etch, 1 wafer × 9 sites (feedback)
Per week:     short-loop DT per chamber: IR 49 sites + X-SEM 3 sites
Per month:    TEM on one wafer per recipe; t/h calibration per chamber
Continuous:   OES/RF virtual metrology on every wafer
```

---

## F.3 IR Effective-Medium Depth

```
Fill-fraction profile f(z) from the trench shape:
  f(z) = A_trench(z) / A_cell = π a(z) b(z) / 16,200 nm²
  f(0) = 6,048 / 16,200 = 0.37; f(5 µm) ≈ π × 25 × 44 / 16,200 = 0.21

Layer index (simple mixing): n²(z) = (1 − f) n_Si² + f
Fit: multilayer model with graded n(z); unknowns H, taper
Calibration: X-SEM depth on 3 wafers per recipe; bias < 15 nm
```

---

## F.4 Model Forms

```
Lumped:          ER₀ t = h + k h²/(2w)
Linear form:     t/h = 1/ER₀ + [k/(2w ER₀)] h
Feed-forward:    Δt_ME3 = −(∂h/∂w × ΔCD)/ER_bot
EWMA:            ER₀,est(n+1) = λ ER₀,meas(n) + (1 − λ) ER₀,est(n), λ = 0.3
Reduced-order:   for each depth cell z:
                   dx/dt = R_lat(z) − D(z)
                   Γ_X(z) from Coburn–Winters per species
                   film: dt_f/dt = Γ_dep s_ox − Γ_i,wall Y_f − R_F,film
Feature-scale:   Monte Carlo ions (IEAD from sheath model) and neutrals
                 (cosine re-emission); level-set surface with
                 material-dependent yields; 1 nm grid
Virtual metrology: PLS on ≈ 40 OES/RF/chamber features; ±35 nm (3σ)
```

---

## F.5 Calibration Checklist for Feature-Scale Models

```
1. IEAD from a sheath model matched to measured bias V and I
2. Neutral fluxes from a reactor model or OES actinometry
3. Yields: Si (ion-assisted, Br and F), BSG, film; check against blanket
   rates (Si 1600, BSG 80 nm/min)
4. Film: deposition probability and oxidation; fit to TEM film thickness
   at 0.5, 2.5, 4.5 µm
5. Validate: profile at three etch times (X-SEM); bow ±1 nm,
   bottom CD ±2 nm, depth ±50 nm
6. Re-validate when mask, chemistry, or hardware changes
```

---

## F.6 Statistics for Rare Events

```
Detecting a rate p with N trenches inspected, zero failures observed:
  Upper 90% confidence bound p_U ≈ 2.3 / N
  To show p < 10⁻⁹: N ≈ 2.3×10⁹ trenches (≈ 23 arrays of 10⁸)

With n failures: p_U from the Poisson bound, e.g. n = 1 → 3.9 / N
```

---

**Appendix F Version:** 1.0
