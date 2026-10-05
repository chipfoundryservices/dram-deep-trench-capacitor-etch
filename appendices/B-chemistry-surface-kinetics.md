# Appendix B: Chemistry & Surface Kinetics

Reaction pathways, rate expressions, and illustrative coefficients for silicon etching in HBr/NF₃/O₂ and cryogenic SF₆/O₂. Coefficients are fits for the reference conditions; use them to reason about trends, not as universal constants.

---

## B.1 Gas-Phase Dissociation (DT-R1, illustrative)

```
HBr + e → H + Br + e                   Br atom fraction ≈ 10–20%
NF₃ + e → NF₂ + F + e → … F            NF₃ ≈ 90% dissociated at 2.5 kW
O₂  + e → 2O + e                       O ≈ 5–10%
H + F → HF (gas-phase and wall)        H from HBr scavenges part of F
```

The hydrogen released from HBr consumes a fraction of the fluorine as HF, which is one reason NF₃ must be raised slightly when HBr is raised to hold the rate.

---

## B.2 Surface Reactions

```
Ion-assisted etch (bottom):
  Si(s) + 4Br(ads) + ion → SiBr₄(g), and SiBrₓ fragments
  Si(s) + 4F(ads) → SiF₄(g)           (spontaneous and ion-assisted)

Passivation (walls):
  SiBrₓ(g) → SiBrₓ(ads); + O → SiOₓBrᵧ(s)
  SiF₄ + O (+ surface) → SiOₓFᵧ(s)    (minor at +60 °C; major at −100 °C)

Film removal:
  SiOₓBrᵧ + ion → sputtered products  (bottom, upper wall under broad ions)
  SiOₓBrᵧ + F → SiF₄ + BrO/Br + …     (slow chemical etch)
```

---

## B.3 Rate Expressions

```
Spontaneous F etch of Si (Flamm):
  R_F [Å/min] = 2.91×10⁻¹² T^½ n_F exp(−1250/T),  n_F in cm⁻³

  T (K)    T^½      exp(−1250/T)    R_F at n_F = 10¹⁴ (nm/min)
  ───────────────────────────────────────────────────────────
  173      13.2     7.3×10⁻⁴        0.28
  293      17.1     0.0140          7.0
  333      18.25    0.0234          12.4
  353      18.8     0.0290          15.8

Ion-assisted yield (fit to R1, illustrative):
  Y(E) ≈ Y₀ (√E − √E_th),  E_th ≈ 20 eV,  Y₀ ≈ 0.36 → Y(450) ≈ 6.0;
  with F co-adsorption the apparent yield rises to ≈ 7

Bottom balance:
  ER_bot = Y Γ_i,bot / n_Si − r_film,bot
```

---

## B.4 Reaction Probabilities (illustrative)

```
Species     Bottom s    Wall s_w    Comment
───────────────────────────────────────────────────────────
F (+60 °C)   0.05       ≈ 0.005     spontaneous + ion
F (25 °C)    0.005      —           remote-plasma bottle
F (−100 °C)  0.02       ≈ 0         cryogenic
Br           0.02       ≈ 0         needs ions
O            0.10       ≈ 0.01      oxidizes wall film
SiBrₓ        —          0.2–0.4     deposits on walls
```

---

## B.5 Wall Recombination (Chapter 9.1)

```
Wall state                   γ_O      γ_F
──────────────────────────────────────────
Clean Y₂O₃                   0.02     0.01
SiOₓBrᵧ-coated (seasoned)    0.005    0.02
Thick SiOₓBrᵧ                0.003    0.03
Fluorinated (post-clean)     0.03     0.005
```

---

## B.6 Cryogenic Film (DT-R2)

```
SiOₓFᵧ stable below ≈ −80 °C; desorbs on warm-up
Thickness on walls ≈ 1–2 nm; nearly uniform with depth
Black-silicon onset: O₂/SF₆ ≥ 10% at −100 °C, or T ≤ −110 °C at 8%
Profile sensitivity: ∂(bottom CD)/∂T ≈ +0.6 nm/°C; ∂(bow)/∂T ≈ +0.4 nm/°C
```

---

## B.7 Wet Chemistry

```
Dilute NH₄OH (1:20, 40 °C) Si etch:  {100} 12, {110} 15, {111} 0.5 nm/min
Dilute HF (50:1) BSG etch:           ≈ 2–5 nm/s (4 wt% B)
Dilute HF (50:1) thermal oxide:      ≈ 0.1 nm/s
SPM (H₂SO₄:H₂O₂ 4:1, 120 °C):        organics, metals
```

---

**Appendix B Version:** 1.0
