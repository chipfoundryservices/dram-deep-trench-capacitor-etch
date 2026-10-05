# Chapter 5: Etch Platforms for Deep Silicon Trenches

## Overview

The deep trench was first etched in magnetically enhanced reactive-ion etchers (MERIE): a single RF electrode, a rotating magnetic field to raise the density, and pressures near 100–150 mTorr. Those tools set the chemistry of the field. Production of trench DRAM at 70 nm and below, and of eDRAM, moved to **decoupled inductively coupled plasma (ICP)** chambers, in which a coil sets the plasma density and a separate bias on the chuck sets the ion energy. The cryogenic variant uses the same architecture with a chuck that runs 150 °C colder.

This chapter describes what the reference platform must deliver and why: density and uniformity, ion energy control, temperature, the handling of large volumes of silicon bromide by-product, and throughput.

**Learning Objectives:**
- Compare MERIE, CCP, and ICP architectures for deep silicon etch
- Estimate the by-product load and its consequences for the chamber
- Specify source, bias, and chuck for DT-R1 and DT-R2
- Estimate chamber throughput and fleet size

---

## 5.1 Architectures

```
  Architecture   Density (m⁻³)   Pressure      Ion energy      Used for DT
                                               control
  ───────────────────────────────────────────────────────────────────────────
  MERIE          10¹⁶–10¹⁷       80–200 mTorr  coupled to       0.25–0.11 µm
  (single RF +                                 density          trench DRAM
  rotating B)
  Dual-frequency 10¹⁶–10¹⁷       20–80 mTorr   partly decoupled some 90–70 nm
  CCP
  Decoupled ICP  10¹⁷–10¹⁸       10–50 mTorr   independent      70 nm and below;
  (TCP)                                        (bias)           eDRAM (reference)
  ICP, cryogenic 10¹⁷–10¹⁸       5–20 mTorr    independent      DT-R2
  chuck
```

Two properties made ICP win. First, at the same ion energy it delivers several times the ion flux, so the etch is faster at the low energies that preserve the mask. Second, the thin, high-density sheath crosses with few collisions even at 30 mTorr (Chapter 4), so the ions arrive narrow. MERIE could not hold both at once: raising the density with the magnet introduced E × B drifts and charging damage that tilted the trench at the wafer edge.

---

## 5.2 The Reference Chamber

```
DT-R1 chamber (illustrative):
  Source: planar or dome coil, 13.56 MHz, up to 3 kW (2.5 kW used)
  Bias:   2 MHz, up to 2 kW (900 W used), with 13.56 MHz option
  Gap:    ≈ 100 mm coil-to-wafer
  Chuck:  bipolar electrostatic, Al₂O₃ or AlN, 4 thermal zones,
          −20 to +80 °C; backside He 15 Torr
  Walls:  anodized Al or Y₂O₃ coated; liner at 80–120 °C
  Window: Al₂O₃ or Y₂O₃-coated, heated to 80 °C
  Pumping: 3000 L/s turbo; 30 mTorr at 450 sccm
```

### 5.2.1 Why 2 MHz Bias

```
Ion transit time across the sheath vs RF period:
  Sheath ≈ 0.9 mm, ⟨E⟩ ≈ 450 eV, Br⁺ (80 amu):
  v ≈ √(2 × 450 × 1.6×10⁻¹⁹ / (80 × 1.66×10⁻²⁷)) ≈ 3.3×10⁴ m/s
  Transit ≈ 0.9×10⁻³ / (1.6×10⁴ mean over the sheath) ≈ 55 ns

  At 13.56 MHz (74 ns period): ions see an average of the sheath →
    narrow IED near the mean
  At 2 MHz (500 ns period): ions follow the instantaneous sheath →
    broad, bimodal IED; higher maximum energy for the same power
```

The low frequency raises the peak energy reached for a given bias power, which deep trenches need at the end of the etch. It also broadens the distribution. The low-energy peak is the price: its ions are angularly broad and deflected by the charged mask. Some platforms combine 2 MHz and 13.56 MHz bias to shape the distribution; others pulse the bias (Chapter 8).

### 5.2.2 Uniformity

```
Requirement: depth ±0.12 µm (3σ) at 5 µm = ±2.4%
  Of which the rate uniformity may use about ±1.5% (3σ), the rest
  going to CD-driven ARDE and the incoming stack.

Radial levers:
  Coil current split (inner/outer)       ±3% centre-to-edge
  Gas injection (centre/edge ratio)      ±2%, also changes F at the edge
  Chuck zones (Chapter 3.6)              profile more than rate
  Edge ring height                       last 5 mm of the wafer
```

---

## 5.3 By-Products

### 5.3.1 The Load

```
Silicon removed per wafer (reference array, 37% open area in the array,
array ≈ 55% of die area, 600 dies ≈ 85% of the wafer):
  Effective open fraction ≈ 0.37 × 0.55 × 0.85 = 0.17
  Si volume = 0.17 × 707 cm² × 5×10⁻⁴ cm = 0.060 cm³
  Si atoms = 0.060 × 5.0×10²² = 3.0×10²¹ per wafer
  As SiBr₄ (MW 348): 3.0×10²¹/6.02×10²³ × 348 ≈ 1.7 g per wafer
```

Nearly two grams of silicon bromide leave each wafer. Most is pumped away; a fraction deposits on the walls, the liner, the window, and the pump. At 25 wafers per lot and 20 lots between wet cleans, the chamber processes about a kilogram of SiBr₄. This is the defining equipment problem of the deep-trench etch.

### 5.3.2 Where It Goes

```
  Location            Effect                              Mitigation
  ─────────────────────────────────────────────────────────────────────────
  Window / coil side  absorbs RF, shifts plasma density;  heated window;
                      flakes as particles                 in-situ clean
  Chamber walls       changes O and F recombination →     waferless auto-
                      rate and profile drift              clean (WAC) every
                                                          wafer (Chapter 9)
  Turbo and foreline  deposits; rotor imbalance           heated foreline;
                                                          purge
  Exhaust             HBr, Br₂, SiF₄                      abatement
```

---

## 5.4 Temperature

```
Heat load on the wafer (DT-R1):
  Ion power: J_i × ⟨E⟩ = 3.0×10⁻³ A/cm² × 450 V = 1.35 W/cm² → 0.95 kW
  Recombination and radiation from the source: ≈ 0.3 kW
  Etch reaction enthalpy: small
  Total ≈ 1.25 kW into the wafer

Wafer–chuck ΔT with 15 Torr He (h ≈ 0.06 W/cm²·K):
  1.25 kW / 707 cm² = 1.77 W/cm² → ΔT ≈ 1.77 / 0.06 ≈ 30 K
```

In practice the wafer runs 20–40 °C above the chuck. The stated chuck temperature (+60 °C for R1) is a control set point, not the wafer temperature. Because lateral fluorine etching rises with temperature (Chapter 3), any change in He leak rate, chuck surface wear, or wafer backside film shifts the profile. The He leak rate is monitored on every wafer.

---

## 5.5 The Cryogenic Platform (DT-R2)

```
DT-R2 chamber differences (illustrative):
  Chuck: −100 °C, LN₂ or closed-cycle; ±1 °C across the wafer required
  Heat load: lower ion energy (120 eV) but same flux → ≈ 0.6 kW
  Load lock: wafer pre-cooled; warm-up station after etch to prevent
             condensation on transfer
  Seals and bellows rated for −120 °C; long-term He backside stability
```

Chapter 7 covers the process consequences.

---

## 5.6 Throughput and Fleet

```
DT-R1 chamber cycle (illustrative):
  Transfer and pump:          25 s
  Breakthrough:               10 s
  Main etch (5 µm):          344 s
  Post-etch passivation strip
   (in-situ, O₂/NF₃ low bias): 15 s
  Waferless auto-clean:       60 s
  ──────────────────────────────
  Total:                     ≈ 454 s ≈ 7.6 min → 7.9 wafers/h per chamber

Fab of 60,000 wafer starts per month (one DT step per wafer):
  60,000 / (30 × 24) = 83 wafers/h
  At 85% availability: 83 / (7.9 × 0.85) ≈ 12.4 → 13 chambers
  (four 3-chamber platforms plus one spare chamber)

DT-R2 cycle: 25 + 10 + 150 + 40 (warm-up handled outside the chamber)
  + 30 (lighter clean) ≈ 255 s → 14 wafers/h → 7 chambers
```

The cryogenic process halves the fleet. The capital per chamber and the cost of the cryogenic plant reduce but do not remove the advantage (Chapter 16).

---

## Summary and Key Takeaways

1. **ICP won.** Decoupled density and energy, a thin collisionless sheath, and fast etch at low ion energy.

2. **2 MHz bias.** It reaches the peak energies the bottom needs, at the cost of a bimodal distribution whose low-energy ions are broad.

3. **Two grams per wafer.** Silicon bromide by-products dominate chamber hardware, cleaning, and drift.

4. **The wafer is hotter than the chuck.** 1.25 kW on the wafer; He leak and chuck wear move the profile.

5. **Thirteen chambers.** For 60,000 wafers per month with R1; about seven with R2.

---

## Study Questions

1. Compute the Si removed and the SiBr₄ produced per wafer if the trench is deepened to 6 µm.

2. Estimate the ion transit time across the sheath for Br⁺ and for HBr⁺ at 150 eV. At which bias frequency does the IED become bimodal for each?

3. The He backside pressure falls from 15 to 12 Torr because of chuck wear. Estimate the wafer temperature change and the profile consequence.

4. A fab doubles the waferless clean to 120 s. How many chambers are needed for 60,000 wafers per month?

5. List three ways SiBrₓ deposition on the window affects the process and how each is detected.

---

**Next Chapter:** [Chapter 6: Passivation Engineering & Profile Control](./06-passivation-engineering-profile.md)

---

**Chapter 5 Development Status:** Complete  
**Version:** 1.0
