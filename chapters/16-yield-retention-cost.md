# Chapter 16: Yield, Retention & Cost of Ownership

## Overview

Every chapter of this book ends in a number of failing bits. A trench too shallow holds too little charge; a trench with a rough or pointed bottom leaks it; two trenches merged by a deflected etch short their nodes; a blocked trench is no cell at all. This chapter collects those mechanisms into a yield model, shows how each appears in the retention distribution and the bit-map, and closes with the cost of the module and the economics of making the trench deeper or the bottle wider.

**Learning Objectives:**
- Relate trench-etch parameters to capacitance and leakage distributions
- Build a retention-tail model for the trench cell
- Identify the bit-map signatures of trench-etch failures
- Estimate the cost of ownership of DT-R1 and DT-R2
- Evaluate the economics of deeper trenches versus wider bottles

---

## 16.1 From Etch to Retention

### 16.1.1 Retention Time

```
A cell fails when its stored signal falls below the sense threshold:
  t_ret = (C_s × ΔV_allow) / I_leak

  C_s = 20.6 fF, ΔV_allow ≈ 0.35 V (from 0.6 V to the ≈ 0.25 V
  needed for a 100 mV-class signal at the sense amplifier, illustrative)
  I_leak (typical cell) ≈ 0.1 fA → t_ret ≈ 72 s
  I_leak (tail cell)    ≈ 50 fA  → t_ret ≈ 144 ms
Refresh interval: 64 ms (commodity), 16–32 ms (eDRAM at high temperature)
```

The typical cell holds its charge for a minute; the refresh interval is set by the tail. Two quantities in the formula come from the trench: C_s, through depth and bottle, and I_leak, partly through the dielectric quality on the trench walls.

### 16.1.2 Leakage Paths Touched by the Etch

```
  Path                              Etch link
  ────────────────────────────────────────────────────────────────────────
  Node dielectric (tunnelling,      wall roughness, bottom shape, grass
   trap-assisted)                   (Chapters 6.4, 10.5, 12.1)
  Vertical parasitic transistor     collar zone bow (thinner collar at the
   (node → buried plate along       bow); collar recess depth
   the collar)
  Junction leakage at the buried    crystal damage and contamination from
   strap                            the etch near the top of the trench
                                    driven in by later thermal steps
  Node-to-node                      merged or near-merged trenches
                                    (Chapter 11)
```

---

## 16.2 A Tail Model

```
Capacitance distribution (illustrative, R1 with APC):
  Mean 20.6 fF; σ ≈ 0.38 fF (from the 1.13 fF 3σ budget of Chapter 1.6.1)
  Narrow-tail trenches (Chapter 12.2.2): rate ≈ 10⁻⁷, C ≈ 17–19 fF
  Shallow and blocked trenches: rate ≈ 10⁻⁹–10⁻⁸, C < 12 fF

Leakage distribution: log-normal body (median 0.1 fA, σ_ln ≈ 1.2)
  plus a defect tail from rough/pointed bottoms and grass

Fail if C_s × 0.35 V / I_leak < t_refresh
```

```
Contribution to the retention tail at 64 ms (illustrative, per 10⁹ cells):

  Mechanism                             Failing cells
  ─────────────────────────────────────────────────────
  Body leakage × body capacitance       ≈ 2
  Narrow-tail trenches × body leakage   ≈ 3
  Grass / pointed bottom (high leakage) ≈ 8
  Shallow / blocked trenches            ≈ 5
  Merged pairs                          ≈ 2 (as pairs)
  Strap and junction (non-etch)         ≈ 30
  ─────────────────────────────────────────────────────
  Total                                 ≈ 50 → within the repair budget
```

The trench etch contributes about 40% of the tail through mechanisms of its own. The largest single etch-related term is not capacitance but leakage at defective bottoms, which is why bottom shape and grass control are treated as yield items, not cosmetic ones.

---

## 16.3 Bit-Map Signatures

```
  Signature                                   Likely trench-etch cause
  ──────────────────────────────────────────────────────────────────────────
  Paired bits along the minor axis            merged trenches (particle-
                                              deflected etch)
  Cluster of 10–1000 bits, roughly round      particle on the mask; blocked
                                              or shallow trenches
  Edge-ring of weak bits (outer 5 mm)         edge depth loss (ring wear) or
                                              edge tilt
  Radial gradient in retention                radial depth signature (CD or
                                              rate), uncorrected
  Random single bits, temperature-activated   bottom-shape or grass leakage
  Lot-to-lot shift of the whole distribution  depth drift: APC or chamber
                                              mismatch
```

---

## 16.4 Cost of Ownership

```
DT-R1 module cost per wafer (illustrative):

  Item                                        $/wafer
  ─────────────────────────────────────────────────
  Mask-open etch (CCP, ≈ 3 min)               4
  Strip and clean                             2
  DT etch chamber depreciation
   (≈ $3.5 M per chamber, 5 yr, 7.9 wph,
    85% availability)                         12
  Consumables (rings, liners, windows)        3
  Gases and abatement (HBr, NF₃)              2
  Post-etch clean (BSG strip)                 2
  Metrology (IR, CD-SEM, sampled X-SEM)       2
  ─────────────────────────────────────────────────
  Total                                       ≈ 27

Depreciation check: $3.5 M / (5 × 8760 h × 0.85 × 7.9 wph) = $11.9/wafer
```

```
DT-R2 (cryogenic) comparison:
  Chamber + cryogenic plant ≈ $4.5 M; 14 wph
  Depreciation: $4.5 M / (5 × 8760 × 0.85 × 14) = $8.6/wafer
  Thinner BSG (500 nm): mask open −$1
  Consumables (less erosion at 120 eV): −$1
  Cryogen and warm-up station: +$1.5
  Total ≈ $24 → about 10% cheaper per wafer
```

DT-R2 is cheaper per wafer by about $3 but asks for a less mature process and tighter thermal control. The decision turns on yield: a grass excursion that costs 1% of die yield on a $5,000 wafer costs $50, more than ten years of the cost difference per wafer.

---

## 16.5 The Economics of Capacitance

```
Options to add 2 fF to the reference cell (illustrative):

  Option                         What it costs
  ──────────────────────────────────────────────────────────────────────────
  Deeper trench: +0.35 µm        etch time +0.60 min (R1) → +8% fleet;
   (5.67 fF/µm)                  ∂h/∂w 26 → 29 nm/nm; BSG −40 nm;
                                 twist +15%
  Wider bottle: +6.5 nm/side     wall 70 → 57 nm: margin 30 → 17 nm;
   (0.31 fF/nm)                  merging tail rises sharply
  Thinner EOT: −0.23 nm          dielectric leakage ×3–10; tail grows
  Metal electrode (TiN)          removes poly depletion (≈ 0.3 nm EOT);
                                 integration cost; no etch change
```

```
Deeper trench, cost per wafer:
  Fleet +8% → depreciation +$0.95; time-related consumables +$0.25
  ≈ +$1.2 per wafer
```

Deepening the trench is the safest and cheapest lever as long as the mask and the CD sensitivity allow it, up to about 6 µm with R1 (Chapter 4.6). Beyond that, R2's mask budget and weaker ARDE make it the path to depth. The bottle cannot grow much further without new control of twist and particles; the dielectric cannot thin without leakage. The trench cell's capacitance, like the stacked cell's, is ultimately bought with etch.

---

## Summary and Key Takeaways

1. **The tail sets refresh.** A typical cell holds charge for a minute; the 64 ms refresh is set by cells with 500 times the median leakage.

2. **The etch owns about 40% of the tail.** Leakage at defective bottoms is its largest term, ahead of shallow trenches.

3. **Bit-maps read the etch.** Paired bits mean merging; round clusters mean particles; edge rings mean ring wear.

4. **About $27 per wafer.** Chamber depreciation dominates; R2 is about 10% cheaper if its defects are controlled.

5. **Depth is the cheapest capacitance.** About $1.2 per wafer for 2 fF, up to the limits of mask and CD sensitivity.

---

## Study Questions

1. Compute t_ret for a cell of 18.0 fF with 30 fA leakage. Does it pass a 64 ms refresh?

2. The grass rate doubles. Using the tail table, how many extra failing cells per 10⁹ result, and does the die stay within a 50-cell repair budget?

3. Recompute the DT-R1 depreciation per wafer if availability falls to 80% and the chamber price rises to $4 M.

4. A design needs 22.6 fF. Compare the cost and risk of deepening to 5.35 µm versus widening the bottle by 6.5 nm per side.

5. Which bit-map signature would you expect from a 0.25° edge tilt combined with a worn edge ring, and how would you confirm it?

---

**Book #32 Complete.** Continue to the [Appendices](../appendices/A-material-properties.md) for reference data.

---

**Chapter 16 Development Status:** Complete  
**Version:** 1.0
