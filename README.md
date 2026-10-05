# Book #32: DRAM Deep Trench Capacitor Etch — Timed, Passivation-Balanced Silicon Etch for Trench DRAM, eDRAM, and Silicon Trench Capacitors

## Overview

**Book #32** is a technical reference on the **deep-trench (DT) capacitor etch**: the etch that cuts the storage capacitor of a trench DRAM cell downward into the single-crystal silicon substrate, as the first patterned step of the process. Books #29 and #31 followed the stacked capacitor upward through an oxide mold. This book follows the other architecture. The trench cell carried a large share of DRAM production down to the 46 nm generation and remains the basis of **embedded DRAM** on logic and SOI processes and of **silicon trench capacitors** for passive devices.

The reference trench is an ellipse **70 × 110 nm** at the silicon surface and **5.00 µm** deep: an aspect ratio of **71:1** at the top and **83:1** at its average width. It is etched through a 900 nm borosilicate-glass hard mask in HBr/NF₃/O₂. After the etch, the lower trench is widened into a **bottle** by 25 nm per side below an oxide collar, lined with a 2.5 nm-EOT dielectric, filled, and recessed three times. The finished cell holds **20.6 fF**, 61% of it owed to the bottle.

The deep trench is a silicon etch with its own hard problems:

- **No etch stop.** Nothing lies beneath the trench but silicon. Depth is set by time, model, and feed-forward.
- **Width becomes depth.** At fixed time, a trench 1 nm narrower ends **26 nm shallower**. The mask-open CD distribution becomes the capacitance distribution.
- **Fluorine etches sideways.** Unprotected, the wall would lose 70 nm per side. The profile depends on an SiOₓBrᵧ film made from the etch's own products, balanced to within 0.2%.
- **The chamber is a reactant.** Each wafer leaves about 1.7 g of SiBr₄ behind; without a clean and seasoning after every wafer, depth drifts by half its budget within a lot.
- **The bottle spends the wall.** Only 30 nm of silicon margin remains between neighbours at mid-bottle; one deflected trench in a billion merges two storage nodes.
- **The trench is first.** Every residue and every rough patch is inherited by the collar, bottle, dielectric, fill, and recesses.

This book covers the chemistry, transport, hardware, recipes, and control that make the deep trench, and follows every parameter to capacitance, leakage, and failing bits. **The question it answers is how to etch a billion identical 5 µm silicon trenches with no etch stop, and what each nanometre of their shape is worth in femtofarads.**

---

## Intended Audience

This book is written for **semiconductor industry professionals** with working knowledge of plasma processing:

- **Process Engineers**: centring and sustaining HBr/NF₃/O₂ deep-silicon recipes; controlling depth, taper, bow, bottom shape, and grass
- **Equipment Engineers**: specifying ICP deep-silicon chambers, cryogenic chucks, waferless cleans, and fleet matching under heavy by-product load
- **Integration Engineers**: managing the capacitance budget across trench etch, collar, bottle, dielectric, and recesses; setting the silicon wall budget
- **Device Engineers**: understanding how trench depth, bottle, and bottom shape appear in capacitance, leakage, and retention tails
- **Researchers and Modellers**: studying silicon surface kinetics, passivation balance, transport in deep trenches, cryogenic etch, and feature-scale profile models

The material assumes a working knowledge of plasma physics (Books #1–5) and advanced plasma engineering (Books #11–15). Books #29 and #31 (stacked-capacitor etch) provide the comparison; the companion volumes *Polysilicon Etch* and *Recess Etch* cover related silicon etches.

---

## Technical Scope

### Core Concepts Covered

**The Trench Cell:**
- Sense signal, the fixed charge target, and the three capacitance levers
- Trench-first integration and its consequences for the etch
- Elliptical, tapered, bottle-shaped capacitor geometry
- The specification sheet and the capacitance budget

**Chemistry & Transport:**
- HBr/NF₃/O₂ surface chemistry; ion-assisted yield; spontaneous fluorine etching
- SiOₓBrᵧ passivation and its balance with depth
- Ion angle and acceptance, weak charging in silicon, neutral starvation
- ARDE, time to depth, and CD-to-depth sensitivity

**Equipment & Recipes:**
- MERIE to decoupled ICP; 2 MHz bias; SiBr₄ by-product load
- Profile levers and the feasible window
- Cryogenic SF₆/O₂ etch at −100 °C
- Depth-adaptive three-step recipes; gas and bias pulsing; why not Bosch
- Waferless clean, seasoning, particles, and fleet matching

**Process Phenomena:**
- Taper, bow, neck, and bottom shape
- Tilt versus twist; the silicon wall budget and merging tails
- Grass, etch stop, blocked and narrow-tail trenches at 10⁻⁹
- The collar-then-bottle widening etch
- SOI eDRAM, downstream recesses, silicon trench capacitors

**Production Integration:**
- Lumped, reduced-order, and feature-scale models
- IR depth metrology, OCD, X-SEM, TEM, CD-SAXS
- Feed-forward, EWMA feedback, virtual metrology
- Retention tails, bit-map signatures, cost of ownership

### Technology Context

- **Device architectures:** 8F² trench DRAM cells (folded bit line); trench eDRAM on bulk and SOI logic; silicon trench capacitors and related deep-silicon etches (DTI, trench gates, TSVs)
- **Capacitor structure:** elliptical deep trench with oxide collar, bottle, As buried plate, high-k node dielectric, doped poly or TiN/poly storage node, buried strap
- **Process sequence:** pad oxide and nitride → BSG → litho → hard-mask open → **deep-trench etch** → clean → liner and collar → bottle → buried plate → node dielectric → fills and recesses → STI and transistors
- **Manufacturing scale:** 300 mm wafers; ≈ 5.7 min main etch inside a 7.6 min chamber cycle (R1), ≈ 2.5 min for the cryogenic alternative; about 13 chambers for 60,000 wafers per month

---

## Book Organization

### Part I: Fundamentals (4 Chapters)

**Chapter 1: The Trench Cell — Why Store Charge Below the Silicon**
- Charge target and sense signal
- Trench-first integration
- Reference trench and capacitance with and without the bottle
- Specification sheet and depth budget

**Chapter 2: The Incoming Stack — Pad Films, Oxide Hard Mask & Mask Open**
- BSG / pad SiN / pad oxide and why BSG
- Mask open and CD transfer
- Mask budget for R1 and R2
- Facets, incoming variation, post-etch strip

**Chapter 3: Silicon Etch Chemistry — HBr, NF₃, O₂ & Sidewall Passivation**
- Removal flux and ion-assisted yield
- Spontaneous fluorine etching and why passivation is required
- The SiOₓBrᵧ film and its balance
- Selectivity, temperature, and the cryogenic alternative

**Chapter 4: Transport & ARDE in Deep Silicon Trenches**
- Ion energy, angle, acceptance, bottom flux
- Charging in silicon versus oxide
- Neutral transport and the ARDE coefficient
- Time to depth, CD to depth, maximum depth

### Part II: Hardware & Chemistry (5 Chapters)

**Chapter 5: Etch Platforms for Deep Silicon Trenches**
- MERIE, CCP, ICP; the reference chamber
- By-product load and where it goes
- Wafer temperature; cryogenic platform
- Throughput and fleet size

**Chapter 6: Passivation Engineering & Profile Control**
- From film balance to sidewall angle
- Lever response table; separating bow from taper
- Roughness and crystallography
- Centring the recipe

**Chapter 7: Cryogenic Deep Silicon Etch**
- SiOₓFᵧ mechanism and spontaneous-etch suppression
- Temperature as a process gas; uniformity and heat removal
- Rate, ARDE, sensitivity
- Black silicon, stress, condensation; when cryo wins

**Chapter 8: Depth-Adaptive & Multi-Step Recipes**
- What should change with depth
- The ME1/ME2/ME3 reference and step times
- Ramps, gas pulsing, bias pulsing, Bosch
- Depth without an etch stop

**Chapter 9: Chamber Conditioning, By-Product Control & Fleet Matching**
- The wall as a reactant
- Waferless auto-clean and seasoning
- Wet clean, particles
- Fleet matching

### Part III: Process Phenomena (5 Chapters)

**Chapter 10: Profile — Taper, Bow, Necking & the Bottom Shape**
- Reference profile; bow; neck
- Taper and its double cost
- Bottom shapes and field enhancement
- Profile measurement

**Chapter 11: Twist, Tilt, Merging & Placement**
- Tilt versus twist
- Edge tilt and ring wear
- The wall budget
- Heavy tails and detection

**Chapter 12: Silicon Grass, Etch Stop & Rare Events**
- Micromasking and grass; cryogenic grass
- Etch stop and narrow trenches
- Blocked and shallow trenches
- Rare-event arithmetic and monitors

**Chapter 13: The Bottle Etch — Widening the Lower Trench**
- Collar-then-bottle sequence
- Wet, dry, and oxidation-strip bottles
- Inheritance from the trench etch
- The bottle within the wall budget

**Chapter 14: SOI eDRAM, Downstream Recesses & Silicon Trench Capacitors**
- SOI stack, BOX step, notch
- Fills and three recesses
- Silicon trench capacitors
- DTI, trench gates, TSVs

### Part IV: Production Scale (2 Chapters)

**Chapter 15: Modelling, Metrology & Advanced Process Control**
- Three model levels and calibration
- Metrology; IR depth
- Feed-forward and feedback
- Virtual metrology

**Chapter 16: Yield, Retention & Cost of Ownership**
- From etch to retention
- Tail model and bit-map signatures
- Cost of ownership, R1 versus R2
- The economics of capacitance

---

## Key Technical Themes

1. **Depth is time.** With no etch stop, depth is set by ER₀t = h + kh²/(2w) and by the control system around it.
2. **Width becomes depth.** ∂h/∂w = (kA²/2)/(1 + kA) = 26 nm/nm at 83:1; the mask-open CD distribution is the first term in the depth budget.
3. **The profile is a 0.2% balance.** Net film deposition of ≈ 3 nm/min against 1600 nm/min of vertical etch sets a 20 nm taper over 5 µm.
4. **The wall is a reactant.** Chamber coating changes O and F at the wafer; clean and season every wafer.
5. **Silicon bleeds charge.** Charging and twist are weaker than in oxide holes; the insulating mask and BOX are where charge acts.
6. **The bottle spends the wall.** Random errors, not collective tilt, consume the 30 nm margin; the merging rate is set by particles and mask defects.
7. **Depth is the cheapest capacitance.** Up to the limits of the mask and CD sensitivity, about 6–6.5 µm for R1.

---

## Cross-References to Prior Books

**Related Books in the Series:**

- **Books #1–5** (Plasma Physics & Chemistry Fundamentals): sheaths, ion energy and angle, free-molecular transport
- **Books #11–15** (Advanced Plasma Engineering): RF delivery, pulsing, temperature control, endpoint and metrology
- **Book #26** (DRAM Isolation Trench Etch): shallow silicon trenches in the DRAM array
- **Book #29** (DRAM Capacitor Hole Etch) and **Book #31** (DRAM High-Aspect-Ratio Capacitor Etch): the stacked capacitor, for comparison
- **Companion volumes:** *Polysilicon Etch*; *Recess Etch*; *Shallow Trench Isolation Etch*; *Silicon Nitride Etch*; *Thermal Oxide Etch*

Books #29 and #31 asked how deep a hole in oxide can go. This book asks how to make a billion identical holes in silicon when nothing at the bottom says stop.

---

## File Organization

```
dram-deep-trench-capacitor-etch/
├── README.md            ← You are here
├── PREFACE.md
├── INDEX.md
├── GLOSSARY.md
│
├── chapters/
│   ├── 01-trench-cell-capacitance.md
│   ├── 02-hard-mask-stack-mask-open.md
│   ├── 03-silicon-etch-chemistry-passivation.md
│   ├── 04-transport-arde-deep-trench.md
│   ├── 05-deep-trench-etch-platforms.md
│   ├── 06-passivation-engineering-profile.md
│   ├── 07-cryogenic-deep-silicon-etch.md
│   ├── 08-depth-adaptive-multistep-recipes.md
│   ├── 09-chamber-conditioning-fleet-matching.md
│   ├── 10-profile-taper-bow-bottom.md
│   ├── 11-twist-tilt-merging-placement.md
│   ├── 12-grass-etch-stop-rare-events.md
│   ├── 13-bottle-etch-widening.md
│   ├── 14-soi-edram-recesses-silicon-capacitors.md
│   ├── 15-modelling-metrology-apc.md
│   └── 16-yield-retention-cost.md
│
└── appendices/
    ├── A-material-properties.md
    ├── B-chemistry-surface-kinetics.md
    ├── C-standard-procedures.md
    ├── D-process-windows.md
    ├── E-scaling-transport-calculations.md
    ├── F-metrology-modelling-reference.md
    └── G-troubleshooting-guide.md
```

---

## Constraints & Scope

### What This Book Covers
✅ Deep-trench silicon etch for trench DRAM and eDRAM capacitors (primary focus)  
✅ HBr/NF₃/O₂ and cryogenic SF₆/O₂ chemistries, passivation, and transport  
✅ Hard-mask stack, mask budget, and the post-etch strip  
✅ Platforms, recipes, conditioning, and fleet matching  
✅ Profile, placement, merging, grass, and rare-event statistics  
✅ The bottle etch and the downstream modules' dependence on the trench  
✅ Modelling, metrology, APC, yield, and cost  

### What This Book Does NOT Cover
❌ The stacked capacitor (see Books #29 and #31)  
❌ Poly recess etches in detail (see *Recess Etch*)  
❌ Node-dielectric and buried-plate doping chemistry in detail  
❌ MEMS and TSV deep etch beyond comparison  
❌ Vendor-specific recipes or proprietary tool parameters  

### A Note on Numbers
Numbers in this book come from established plasma physics, published literature trends, and representative production practice. Worked examples use **illustrative values** chosen to show the method, and the arithmetic is written out so readers can substitute their own data. A single **reference process** ties the chapters together: a 45 nm-class 8F² trench cell (16,200 nm²) on a 180 nm minor-axis pitch; an elliptical trench 70 × 110 nm at the surface, 5.00 µm deep, 50 × 88 nm at the bottom, average minor CD 60 nm; a 900 nm BSG / 150 nm pad SiN / 5 nm pad oxide stack; a collar to 1.20 µm, a bottle from 1.20 to 4.80 µm widened 25 nm per side, and a 2.50 nm-EOT node dielectric giving 20.6 fF. Two etch processes are carried through the book: **DT-R1**, HBr/NF₃/O₂ in an ICP chamber at +60 °C (ER₀ = 1600 nm/min, k = 0.020), and **DT-R2**, cryogenic SF₆/O₂ at −100 °C (ER₀ = 3000 nm/min, k = 0.012). The closed-form models are collected in Appendix E. Treat recipe values as starting points for a design of experiments, never as qualified process conditions.

---

## Development Status

**Book #32 Foundation:** Complete  
**Part I (Chapters 1–4):** Complete  
**Part II (Chapters 5–9):** Complete  
**Part III (Chapters 10–14):** Complete  
**Part IV (Chapters 15–16):** Complete  
**Back Matter (Appendices A–G, Glossary):** Complete  

---

## Next Steps

1. **Read [PREFACE.md](./PREFACE.md)** for the motivation and reading guidance
2. **Read [INDEX.md](./INDEX.md)** for the detailed chapter outline and reading paths by role
3. **Begin [Chapter 1](./chapters/01-trench-cell-capacitance.md)**: The Trench Cell — Why Store Charge Below the Silicon

---

**Book #32 Version:** 1.0  
**Last Updated:** 2026-10-05  
**Series:** ChipFoundryServices Technical Series
