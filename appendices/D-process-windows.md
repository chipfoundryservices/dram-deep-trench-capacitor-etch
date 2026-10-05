# Appendix D: Process Windows

Reference recipes and their windows for the hard-mask open, DT-R1, DT-R2, the waferless clean, and the bottle etch. All values are illustrative starting points for a design of experiments, not qualified process conditions.

---

## D.1 Reference Geometry

```
Cell: 45 nm-class, 8F² = 16,200 nm²; minor-axis pitch 180 nm
Trench: ellipse 70 × 110 nm at the Si surface; depth 5.00 µm
  Bottom (before bottle) 50 × 88 nm; w̄ = 60 nm (minor)
  A = 71 (top CD), 83 (w̄), 91 including 455 nm of mask + pad at end
Bottle: 1.20–4.80 µm, +25 nm per side → 110 × 150 nm at mid-bottle
Node dielectric EOT 2.50 nm → 13.8 fF/µm²; C_s = 20.6 fF
Stack: BSG 900 / pad SiN 150 / pad oxide 5 nm
```

---

## D.2 Hard-Mask Open (CCP)

```
Step        Gases (sccm)                  Pressure  Power (W)        Time
──────────────────────────────────────────────────────────────────────────
ARC         CF₄ 100, CHF₃ 30              20 mT     600 / 200        15 s
UL          N₂ 300, H₂ 100                15 mT     1200 / 300       40 s
BSG         C₄F₆ 25, O₂ 20, Ar 600        30 mT     2000 HF/1500 LF  95 s
SiN         CH₂F₂ 40, CF₄ 40, O₂ 20, Ar   40 mT     800 / 400        35 s
Pad oxide   CF₄ 80, Ar 200                10 mT     400 / 100         8 s
Window: top CD 70 ± 1.5 nm; BSG loss ≤ 50 nm; no residue in opening
```

---

## D.3 DT-R1 (HBr/NF₃/O₂, ICP, chuck +60 °C)

```
Step  Depth (µm)  HBr  NF₃  O₂   SiF₄  Bias (W)  P (mT)  Time
──────────────────────────────────────────────────────────────────
BT    —           100  40   0    0     1200      10      10 s
ME1   0 → 1.2     300  26   20   8     700       30      54 s
ME2   1.2 → 3.5   300  30   18   3     900       30      154 s
ME3   3.5 → 5.0   300  34   15   0     1100      28      136 s
Source 2.5 kW (13.56 MHz); bias 2 MHz; He 100 sccm; backside He 15 Torr

Model: ER₀ = 1600 nm/min, k = 0.020 → t(5 µm) = 5.73 min
Windows (ME2, holding other factors):
  O₂ 16–20 sccm; NF₃ 27–34 sccm; bias 800–1000 W; pressure 26–34 mT;
  chuck 55–65 °C
Responses at centre: bow ≤ 2 nm; bottom CD 50 nm; BSG remaining 300 nm
```

---

## D.4 DT-R2 (SF₆/O₂, ICP, chuck −100 °C)

```
BT:   SF₆ 100, bias 300 W, 10 s (chuck cold)
Main: SF₆ 200, O₂ 16 (O₂/SF₆ 8%), 12 mT, source 2.5 kW, bias 250 W,
      backside He 10 Torr; ≈ 150 s
Model: ER₀ = 3000 nm/min, k = 0.012 → t(5 µm) = 2.50 min
Windows:
  O₂/SF₆ 7–9%; chuck −105 to −95 °C; wafer uniformity ±1 °C
  Black-silicon edge: O₂/SF₆ 10% or T ≤ −110 °C
BSG loss 125 nm (main); BSG 500 nm sufficient
```

---

## D.5 Waferless Auto-Clean

```
Step 1: NF₃ 300, O₂ 50; 2.0 kW source; no bias; 20 s
Step 2: O₂ 400; 2.0 kW; 15 s
Step 3: HBr 200, O₂ 20, SiF₄ 20; 1.5 kW; 25 s  (seasoning)
Endpoint check: SiF (440 nm) emission falls to baseline in step 1
```

---

## D.6 Bottle Etch

```
Wet (reference):  NH₄OH 1:20, 40 °C, ≈ 2.1 min → 25 nm per side
                  (crystallographic; uniform with depth)
Dry (alternative): remote NF₃/O₂ 200/40, 25 °C wafer, pulsed
                  (5 s on / 5 s pump × 15); gradient ≤ 5% top-to-bottom
Oxidation-strip:  57 nm thermal oxide + HF, in 2–3 cycles → 25 nm
Window: widening 25 ± 2 nm (3σ) per side; wall ≥ 40 nm
```

---

## D.7 Sensitivities

```
Quantity                          Value (R1)            Value (R2)
──────────────────────────────────────────────────────────────────────
∂h/∂w at 5 µm                     26.0 nm/nm            20.8 nm/nm
ER at bottom (5 µm)               600 nm/min            1500 nm/min
ME3 / main time per nm CD         −2.6 s/nm             −0.8 s/nm
∂C/∂H                             5.67 fF/µm            same
∂C/∂(bottle per side)             0.31 fF/nm            same
∂C/∂(top CD), via depth           0.15 fF/nm            0.12 fF/nm
```

---

**Appendix D Version:** 1.0
