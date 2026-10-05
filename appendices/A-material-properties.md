# Appendix A: Material Properties

Properties of the substrate, pad, mask, liner, dielectric, and chamber materials used in this book, with physical constants. Values are representative; film properties depend on deposition conditions and should be measured for each process.

---

## A.1 Silicon

```
Property                                   Value
──────────────────────────────────────────────────────────────────
Atomic density                             5.00×10²² cm⁻³
Density                                    2.33 g/cm³
Lattice constant                           0.543 nm
Refractive index (mid-IR, 5 µm)            3.42 (n² ≈ 11.7)
Thermal conductivity (300 K)               ≈ 150 W/m·K
CTE (300 K)                                2.6 ppm/K
Young's modulus ⟨110⟩                      169 GPa
Physical sputter yield, Ar⁺ / Br⁺ at 450 eV ≈ 0.6 / ≈ 0.7 atoms/ion
Wet NH₄OH rate ratio {100} : {110} : {111}  ≈ 24 : 30 : 1 (dilute, 40 °C)
Oxidation: Si consumed per nm of SiO₂      0.44 nm
```

---

## A.2 Pad Films and Hard Mask

```
Material              Thickness   Density   Stress      Etch in R1     Dilute HF
                      (ref.)      (g/cm³)   (MPa)       (nm/min,       (rel. thermal
                                                        open area)     oxide)
──────────────────────────────────────────────────────────────────────────────────
Pad oxide (thermal)   5 nm        2.27      −300        ≈ 60           1
Pad SiN (LPCVD)       150 nm      3.0       +1000       ≈ 25           0.05
BSG (≈ 4 wt% B)       900 nm      2.2       −100 to     ≈ 80           20–50
                                            +50
TEOS (alternative)    —           2.2       −150        ≈ 75           3–5
SiARC                 30 nm       1.4–1.6   —           removed in mask open
Organic underlayer    200 nm      1.1–1.2   —           removed in mask open
```

---

## A.3 Trench Liners and Dielectrics

```
Material                   Role                       k        Typical
                                                               thickness
────────────────────────────────────────────────────────────────────────
Thermal SiO₂               liner, collar (partial)    3.9      2–25 nm
LPCVD SiN                  liner, sacrificial         7.5      4 nm
Collar oxide (CVD or       collar                     3.9      20–25 nm
 oxidized)
NO (nitride–oxide)         legacy node dielectric     ≈ 6.5    EOT 3.5–4 nm
Al₂O₃ (ALD)                node dielectric            ≈ 9      ≈ 6 nm phys.
HfO₂ / HfSiO (ALD)         node dielectric            15–22    ≈ 4–6 nm phys.
Reference stack            node dielectric            —        EOT 2.50 nm
```

---

## A.4 Fill and Electrode

```
Material                 Role                        Resistivity
──────────────────────────────────────────────────────────────────────
As-doped poly-Si         storage node (fills 1–2)    ≈ 1–3 mΩ·cm
Undoped/lightly doped    buried strap (fill 3)       outdiffusion-doped
 poly
TiN (ALD/CVD)            metal storage-node liner    ≈ 150–250 µΩ·cm
Buried plate (As in Si)  counter-electrode           10¹⁹–10²⁰ cm⁻³ As
```

---

## A.5 Chamber Materials

```
Material             Where               Behaviour in HBr/NF₃/O₂
──────────────────────────────────────────────────────────────────────
Anodized Al          walls (legacy)      fluorinates; AlF₃ particles
Y₂O₃ (coated)        walls, liner,       low erosion; YOF formation;
                     window              particles if coating cracks
Al₂O₃ ceramic        window, chuck       moderate erosion
AlN                  chuck               high thermal conductivity
Si / SiC             edge ring           erodes; ring height drives
                                         edge tilt
Quartz               edge parts          erodes in F; O source
```

---

## A.6 By-Products

```
Species    MW      Boiling point   Note
─────────────────────────────────────────────────────────
SiF₄       104     −86 °C          volatile
SiCl₄      170     58 °C           volatile
SiBr₄      348     153 °C          condenses on cold spots
Br₂        160     59 °C           exhaust; abatement
HBr        81      −67 °C          corrosive with moisture
```

---

## A.7 Constants

```
ε₀ = 8.854×10⁻¹² F/m           k_B = 1.381×10⁻²³ J/K
e  = 1.602×10⁻¹⁹ C             amu = 1.661×10⁻²⁷ kg
N_A = 6.022×10²³ mol⁻¹          1 Torr = 133.3 Pa
C/A at EOT 2.5 nm = 13.8 fF/µm²
```

---

**Appendix A Version:** 1.0
