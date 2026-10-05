# Appendix C: Standard Procedures

Step-by-step procedures for qualification, monitoring, and recovery of the deep-trench etch. Times and limits are illustrative and must be set from each fab's own data.

---

## C.1 Chamber Qualification After Wet Clean

```
1. Leak check: rate-of-rise < 2 mTorr/min at base pressure
2. RF: delivered bias power at the chuck within ±2% (V–I probe);
   source match within the fleet window
3. Chuck: temperature calibration at +60 °C (±1 °C, 4 zones);
   He leak rate < 1.5 sccm at 15 Torr
4. Seasoning: 25 bare-Si wafers with the full DT-R1 recipe + WAC
5. Monitors:
   • Blanket Si rate (5 sites): ER within ±1.5% of the fleet reference
   • Blanket BSG rate: within ±3%
   • Particles ≥ 45 nm on bare Si: ≤ 10 adders
6. Patterned short-loop DT wafer:
   • IR depth (49 sites): mean within ±40 nm of the chamber baseline,
     radial C–E within ±25 nm
   • X-SEM at centre, mid-radius, 3 mm edge: top CD, bow, bottom CD,
     tilt within specification
7. Release to production with APC offset reset to the last pre-PM value
```

---

## C.2 Daily and Per-Lot Monitoring

```
Per wafer:   OES fingerprint (SiBr, O/Ar, F/Ar); RF readbacks; He leak;
             WAC endpoint trace
Per lot:     IR depth on one wafer (9 sites); EWMA update
Daily:       particle monitor; blanket Si rate on one chamber in rotation
Weekly:      patterned short-loop per chamber: depth, CD, X-SEM profile
Monthly:     t/h calibration of ER₀ and k per chamber (3 times)
```

---

## C.3 Lumped-Model Calibration

```
1. Etch three short-loop wafers to t₁ ≈ 0.3 t_ref, t₂ ≈ 0.7 t_ref, t₃ = t_ref
2. Measure depth by X-SEM (5 trenches per site, 3 sites) and IR (49 sites)
3. Compute y = t/h for each, plot against h
4. Linear fit: intercept a = 1/ER₀; slope b = k/(2 w̄ ER₀)
   → ER₀ = 1/a; k = 2 w̄ b/a
5. Accept if R² > 0.98 and k within ±15% of the fleet value
```

---

## C.4 Edge-Ring Management

```
1. Track ring RF hours per chamber
2. Every 250 RF h: edge tilt monitor (X-SEM or asymmetric OCD at 147 mm)
3. Adjust ring lift to restore tilt to |θ| ≤ 0.08° at 147 mm
4. Replace the ring when lift range is exhausted or at ≈ 1500 RF h
```

---

## C.5 Excursion Response: Depth Out of Control

```
1. Hold the chamber; quarantine lots since the last good measurement
2. Compare IR depth with the virtual-metrology prediction for the
   affected wafers
3. Check (in order): APC inputs (CD, BSG), recipe version, RF readbacks,
   MFC readbacks, chuck temperatures and He leak, WAC trace
4. Run a blanket Si rate monitor and a patterned short-loop wafer
5. If the depth error is explained by APC input: correct and release;
   if by hardware: repair, requalify per C.1
6. Disposition held lots: depth ≥ 4.75 µm per die → release;
   otherwise route to short-loop capacitance test or scrap
```

---

## C.6 Profile Cross-Section Procedure

```
1. Cleave along the minor axis (⟨110⟩) through a row of trenches
2. Coat lightly (≈ 2 nm Pt) to reduce charging
3. SEM at 5 kV, tilt 0°, magnification to fit the full depth
4. Measure CD at 0, 0.2, 0.5, 1, 2, 2.5, 3, 4, 4.8 µm and the bottom
5. Report: top CD, max bow and depth, CD at 2.5 µm, bottom CD, depth,
   tilt (axis angle from bottom-centre to top-centre)
6. Use ≥ 5 trenches per site; report mean and range
```

---

**Appendix C Version:** 1.0
