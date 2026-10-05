# Chapter 3: Silicon Etch Chemistry — HBr, NF₃, O₂ & Sidewall Passivation

## Overview

A capacitor hole in oxide is etched by ions; fluorocarbon chemistry supplies the reactant and the polymer that protects the walls (Books #29, #31). A trench in silicon is different. Atomic fluorine etches silicon spontaneously, without ions, at room temperature. Bromine and chlorine do not, or barely. The deep-trench chemistry exploits this contrast: bromine provides an ion-driven, anisotropic etch; a little fluorine raises the rate and keeps the bottom clean; oxygen turns etch products into an oxide-like film on the walls that stops the fluorine from etching sideways.

This chapter sets out the surface chemistry of DT-R1, the passivation film that makes it anisotropic, the selectivity to the hard mask, and the knobs that move the balance.

**Learning Objectives:**
- Compute the silicon removal flux and estimate the ion yield in DT-R1
- Estimate spontaneous lateral etching by fluorine and why passivation is required
- Explain how SiOₓBrᵧ forms and where it deposits
- Predict the effect of O₂, NF₃, HBr, and temperature on rate, taper, and selectivity
- Distinguish the chemistry of DT-R1 from cryogenic DT-R2

---

## 3.1 What the Etch Removes

```
Silicon atom density: n_Si = 5.0×10²² cm⁻³
DT-R1 open-feature reference rate: ER₀ = 1600 nm/min = 26.7 nm/s
Removal flux: 26.7×10⁻⁷ cm/s × 5.0×10²² = 1.33×10¹⁷ Si cm⁻² s⁻¹

Ion flux (ICP, illustrative): J_i ≈ 3.0 mA/cm² → 1.9×10¹⁶ ions cm⁻² s⁻¹
Apparent yield: 1.33×10¹⁷ / 1.9×10¹⁶ ≈ 7 Si per ion at ⟨E_i⟩ ≈ 450 eV
```

A yield of 7 is far above physical sputtering of silicon at 450 eV (about 0.6 atoms per ion). The ion is a catalyst: it drives the reaction of a surface saturated with Br and F to volatile products. Each ion impact removes several silicon atoms as SiBr₄, SiBr₂, SiF₄, and mixed SiBrₓFᵧ.

### 3.1.1 Products and Volatility

```
  Product   Boiling point   Comment
  ───────────────────────────────────────────────────────────
  SiF₄      −86 °C          very volatile; leaves spontaneously
  SiCl₄     58 °C           volatile
  SiBr₄     153 °C          volatile at low pressure; readily
                            redeposits and oxidizes
  SiBrₓOᵧ   (involatile)    the passivation film
```

The low volatility of SiBr₄ and of its partly brominated fragments is what makes HBr chemistry good for passivation: a fraction of what leaves the bottom sticks to the walls on the way up.

---

## 3.2 Why Fluorine Alone Fails

### 3.2.1 Spontaneous Etching

Atomic fluorine etches silicon without ion assistance. A widely used rate expression (Flamm) is:

```
R_F = 2.91×10⁻¹² · T^½ · n_F · exp(−1250/T)   [Å/min; n_F in cm⁻³]

At chuck 60 °C (T ≈ 333 K), n_F = 1×10¹⁴ cm⁻³:
  T^½ = 18.25; exp(−1250/333) = exp(−3.754) = 0.0234
  R_F = 2.91×10⁻¹² × 18.25 × 10¹⁴ × 0.0234 = 124 Å/min ≈ 12 nm/min
```

Twelve nanometres a minute is slow compared with the 1600 nm/min vertical rate. But the etch lasts 5.7 minutes:

```
Lateral etch of an unprotected sidewall at the top of the trench:
  12 nm/min × 5.7 min ≈ 70 nm per side
→ a 70 nm trench would end 210 nm wide at the top
```

Even a tenth of that would ruin the 110 nm wall. **The sidewall must be passivated from the first second.**

### 3.2.2 Why Not Pure HBr

Pure HBr (with an inert diluent) etches silicon anisotropically and selectively, but slowly, and it leaves the bottom prone to **micromasking**: small particles of redeposited SiBrₓOᵧ or of mask material protect points on the bottom and grow into silicon grass (Chapter 12). A small fraction of NF₃ or SF₆ raises the rate and keeps the bottom free of film.

---

## 3.3 The DT-R1 Chemistry

```
DT-R1 main etch, ME2 conditions (illustrative; the full three-step recipe is in Chapter 8):
  HBr 300 sccm, NF₃ 30 sccm, O₂ 18 sccm, He 100 sccm (+ SiF₄ 0–10 sccm)
  Pressure 30 mTorr; ICP source 2.5 kW at 13.56 MHz
  Bias 900 W at 2 MHz → ⟨E_i⟩ ≈ 450 eV, peaks near 150 and 750 eV
  Chuck +60 °C; backside He 15 Torr
  O₂/(HBr+NF₃) ≈ 5.5%
```

### 3.3.1 What Each Gas Does

```
  Gas    Role                                     Too little         Too much
  ────────────────────────────────────────────────────────────────────────────
  HBr    Br for ion-driven etch; SiBrₓ products   slow, isotropic    rate falls,
         for passivation; H scavenges F                              grass
  NF₃    F for rate and bottom cleaning;          grass, slow        lateral etch,
         etches the sidewall film                                    bow, mask loss
  O₂     oxidizes SiBrₓ to SiOₓBrᵧ on walls        bow, undercut      taper, etch
                                                                     stop, grass
  SiF₄   additional Si source for the film        —                  heavy taper,
         where the trench is too deep for                            closing
         SiBrₓ to reach the top
  He     dilution; thermal transfer               —                  —
```

---

## 3.4 The Passivation Film

### 3.4.1 Formation

Silicon bromides leave the bottom, travel up the trench, and strike the walls. Some stick. Oxygen atoms arriving from the plasma oxidize them. The result is a film of SiOₓBrᵧ (with some F) that grows on the walls and on the mask. On the bottom, where ions arrive at full energy, the same film is sputtered and etched as fast as it forms.

```
Film on the sidewall (illustrative, R1, from TEM/EDS):
  Upper trench (0–1 µm):    3–5 nm, O-rich, Br ≈ 5 at%
  Mid trench (1–3 µm):      2–3 nm
  Lower trench (3–5 µm):    1–2 nm, Br-rich, less O
  Bottom:                   < 0.5 nm (steady state)
```

### 3.4.2 A Balance Model

```
Net film growth on a wall element:
  dt_f/dt = Γ_dep · s_ox − Γ_i,wall · Y_f(E, θ) − R_F,film

  Γ_dep    flux of Si-bearing product (falls with distance from the bottom)
  s_ox     fraction that oxidizes and sticks (rises with O₂)
  Γ_i,wall grazing ion flux on the wall (rises with angular spread)
  R_F,film fluorine etch of the film (rises with NF₃)
```

Three profile regimes follow:

1. **Film wins everywhere.** The wall grows inward; the trench tapers and, at the extreme, closes. Excess O₂ or SiF₄.
2. **Balance.** A thin film holds a vertical wall; the bottom stays clean.
3. **Film loses near the top.** The upper wall, struck by ions reflected from the mask facet and by the broad ion population, loses its film and etches laterally: **bow**. Excess NF₃ or bias.

### 3.4.3 Why the Film Thins with Depth

The Si-bearing flux comes from the bottom. Higher in the trench, the wall sees all the products of the deeper etch; low in the trench it sees fewer, because they have not yet had to pass it. At the same time, the O flux falls with depth by neutral transport (Chapter 4). The film is therefore thickest near the top and thinnest near the bottom, which is also where the trench most needs it least: the lateral fluorine flux is smallest deep in the trench. Chapter 8 uses this to design a depth-adaptive recipe.

---

## 3.5 Selectivity to the Hard Mask

```
Open-area BSG etch in R1 (illustrative): ≈ 80 nm/min
  Ion-driven: BSG is etched by physical sputtering assisted by F
  Si:BSG open area ≈ 1600/80 = 20:1

Knobs:
  Bias 900 → 1200 W:  Si +12%, BSG +35%   → selectivity 17.5:1
  NF₃ 30 → 45 sccm:   Si +15%, BSG +25%   → selectivity 18.5:1
  O₂ 18 → 24 sccm:    Si −8%,  BSG −5%    → selectivity 19.4:1, more taper
  HBr 300 → 400:      Si +5%,  BSG −5%    → selectivity 22:1
```

HBr is the selectivity lever: Br does not etch oxide, while it does etch silicon. Bias is the main enemy of selectivity, and bias is what ARDE demands. Chapter 8 resolves the conflict by raising the bias only when the trench is deep enough to need it.

---

## 3.6 Temperature

```
Effect of chuck temperature on R1 (illustrative):

  Chuck     Si rate   Lateral etch (unprotected)   Film
  ────────────────────────────────────────────────────────────────
  20 °C     −6%       7 nm/min                     thicker; taper
  60 °C     ref.      12 nm/min                    reference
  80 °C     +4%       15 nm/min                    thinner; bow
```

The spontaneous fluorine rate doubles between 20 °C and 80 °C (from the Arrhenius factor), while the film's sticking falls. The chuck temperature profile across the wafer therefore acts as a radial profile knob. A ±2 °C centre-to-edge difference produces a measurable difference in top bow.

---

## 3.7 The Cryogenic Alternative (DT-R2)

```
DT-R2 main etch (illustrative):
  SF₆ 200 sccm, O₂ 16 sccm (O₂/SF₆ = 8%), 12 mTorr
  ICP 2.5 kW; bias 250 W → ⟨E_i⟩ ≈ 120 eV
  Chuck −100 °C; backside He 10 Torr
  ER₀ ≈ 3000 nm/min
```

At −100 °C, spontaneous fluorine etching of silicon slows sharply: the Arrhenius factor at 173 K is exp(−7.23) = 7×10⁻⁴, about thirty times smaller than at 333 K. More important, an SiOₓFᵧ film forms on the walls and is stable only while the wafer is cold; it evaporates on warm-up, leaving clean walls. The film is thin, uniform with depth, and needs no Si-bearing product from the bottom. ARDE is weaker (k = 0.012 against 0.020), selectivity to oxide exceeds 100:1, and the low ion energy spares the mask.

The costs (Chapter 7):

```
  • Temperature uniformity of ±1 °C across a wafer at −100 °C, under 2.5 kW
  • Black silicon if O₂ is slightly high or the wafer slightly cold
  • Mask cracking or delamination on thermal cycling
  • Condensation and particle risk in the transfer path
```

---

## Summary and Key Takeaways

1. **Ions catalyze.** DT-R1 removes about 7 Si atoms per ion at 450 eV; sputtering alone would remove 0.6.

2. **Fluorine etches sideways.** Unprotected, the upper wall would lose 70 nm per side in one etch; the passivation film is mandatory.

3. **The film is made from the etch.** SiBrₓ products from the bottom oxidize on the walls to SiOₓBrᵧ, 3–5 nm at the top and 1–2 nm near the bottom.

4. **Balance sets the profile.** Too much O₂ tapers and closes; too much NF₃ or bias bows.

5. **HBr buys selectivity; bias spends it.** Open-area Si:BSG is about 20:1.

6. **Cryogenic etch changes the film.** SiOₓFᵧ forms independently of depth and disappears on warm-up; ARDE and mask loss fall, at the cost of temperature control and black silicon.

---

## Study Questions

1. Compute R_F at n_F = 2×10¹⁴ cm⁻³ and 80 °C. How much lateral etch would an unprotected upper wall see in the reference etch time?

2. The ion flux is raised to 3.6 mA/cm² at the same energy, and the rate rises 10%. What is the new apparent yield? What does the sub-linear response suggest about what limits the rate?

3. Why is the passivation film thickest near the top of the trench? Which gas would you raise to thicken it near the bottom, and what would it cost?

4. Estimate the open-area Si:BSG selectivity after a change of O₂ from 18 to 24 sccm and HBr from 300 to 400 sccm, using the table in 3.5 and assuming the effects multiply.

5. List three reasons DT-R2 shows weaker ARDE than DT-R1.

---

**Next Chapter:** [Chapter 4: Transport & ARDE in Deep Silicon Trenches](./04-transport-arde-deep-trench.md)

---

**Chapter 3 Development Status:** Complete  
**Version:** 1.0
