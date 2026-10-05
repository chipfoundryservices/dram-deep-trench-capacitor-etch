# Index: Book #32 Navigation Guide

## Quick Navigation

**Total Content:** 16 chapters + 7 appendices + glossary  
**Estimated Read Time:** 22–30 hours for the complete book; 5–9 hours for a focused reading path

| Part | Chapters | Theme |
|------|----------|-------|
| I | 1–4 | Fundamentals: the trench cell, the hard-mask stack, silicon etch chemistry and passivation, transport and ARDE |
| II | 5–9 | Hardware & chemistry: ICP platforms, passivation engineering, cryogenic etch, depth-adaptive recipes, chamber conditioning and matching |
| III | 10–14 | Phenomena: profile, twist and merging, grass and rare events, the bottle etch, SOI eDRAM and silicon trench capacitors |
| IV | 15–16 | Production: modelling, metrology, APC, yield, retention, cost |

---

## Part I: Fundamentals (Chapters 1–4)

### Chapter 1: [The Trench Cell — Why Store Charge Below the Silicon](./chapters/01-trench-cell-capacitance.md)
**Estimated Time:** 60 min | **Difficulty:** Foundation | **Reading Level:** All roles  
**Focus:** What must the trench deliver, and why is it 5 µm deep?

**Key Topics:**
- Sense signal (109 mV at 20 fF on 90 fF) and the fixed charge target
- Trench-first: no etch stop, everything inherited downstream
- Reference trench: 70 × 110 nm ellipse, 5.00 µm, A = 71 / 83
- Capacitance 12.8 fF without bottle, 20.6 fF with a 25 nm-per-side bottle
- Specification sheet; depth ±0.12 µm from the capacitance budget

**Critical Equations:** ΔV_BL = (V_BLH/2)C_s/(C_s + C_BL); C/A = ε₀·3.9/EOT; Ramanujan ellipse perimeter  
**Study Questions:** 6

---

### Chapter 2: [The Incoming Stack — Pad Films, Oxide Hard Mask & Mask Open](./chapters/02-hard-mask-stack-mask-open.md)
**Estimated Time:** 45 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration  
**Focus:** What does the trench etch inherit, and how long can its mask last?

**Key Topics:**
- 900 nm BSG / 150 nm pad SiN / 5 nm pad oxide; why BSG
- Mask open and CD transfer; ellipticity
- Mask budget: 300 nm left (R1), 675 nm (R2); maximum depth 6.5 µm
- Facets, incoming variation, breakthrough, post-etch strip

**Critical Equations:** BSG_end = BSG₀ − loss_pre − H/S_eff; H_max = S_eff(BSG₀ − loss_pre − R)  
**Study Questions:** 5

---

### Chapter 3: [Silicon Etch Chemistry — HBr, NF₃, O₂ & Sidewall Passivation](./chapters/03-silicon-etch-chemistry-passivation.md)
**Estimated Time:** 60 min | **Difficulty:** Intermediate | **Reading Level:** Process/Research  
**Focus:** What etches the silicon, and what keeps the wall straight?

**Key Topics:**
- 1.33×10¹⁷ Si cm⁻² s⁻¹; apparent yield ≈ 7 per ion at 450 eV
- Spontaneous F etch: 12 nm/min → 70 nm per side unprotected
- SiOₓBrᵧ film: 3–5 nm at the top, 1–2 nm near the bottom
- Gas roles; selectivity to BSG ≈ 20:1 open area; temperature
- Cryogenic SiOₓFᵧ (DT-R2)

**Critical Equations:** R_F = 2.91×10⁻¹² T^½ n_F exp(−1250/T); dt_f/dt = Γ_dep s_ox − Γ_i,wall Y_f − R_F,film  
**Study Questions:** 5

---

### Chapter 4: [Transport & ARDE in Deep Silicon Trenches](./chapters/04-transport-arde-deep-trench.md)
**Estimated Time:** 75 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** Why does the bottom slow down, and how does CD become depth?

**Key Topics:**
- Ion spread 0.6°; acceptance 0.53° at the end; bottom ion fraction 0.58
- Silicon bleeds charge; the mask does not
- Coburn–Winters for F, Br, O; k = 0.020 (R1), 0.012 (R2)
- t(5 µm) = 5.73 min (R1), 2.50 min (R2); ∂h/∂w = 26 nm/nm
- Depth limited by mask and variability, not bottom physics

**Critical Equations:** ER = ER₀/(1 + kA); ER₀t = h + kh²/(2w); ∂h/∂w = (kA²/2)/(1 + kA)  
**Study Questions:** 5

---

## Part II: Hardware & Chemistry (Chapters 5–9)

### Chapter 5: [Etch Platforms for Deep Silicon Trenches](./chapters/05-deep-trench-etch-platforms.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment  
**Key Topics:** MERIE → ICP; 2 MHz bias and bimodal IED; 1.7 g SiBr₄ per wafer; wafer 30 K above chuck; 7.6 min cycle; 13 chambers for 60k wafers/month (7 with R2)  
**Study Questions:** 5

### Chapter 6: [Passivation Engineering & Profile Control](./chapters/06-passivation-engineering-profile.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Process  
**Key Topics:** 0.2% imbalance sets the taper; lever response table; pressure separates bow from bottom CD; roughness sources; crystallography; DOE and the narrow feasible lens  
**Study Questions:** 5

### Chapter 7: [Cryogenic Deep Silicon Etch](./chapters/07-cryogenic-deep-silicon-etch.md)
**Estimated Time:** 50 min | **Difficulty:** Advanced | **Reading Level:** Process/Equipment/Research  
**Key Topics:** SiOₓFᵧ film from the gas; lateral F etch ÷45; temperature as a process gas; ±1 °C; black silicon; thermal transients; R1 versus R2  
**Study Questions:** 5

### Chapter 8: [Depth-Adaptive & Multi-Step Recipes](./chapters/08-depth-adaptive-multistep-recipes.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Process  
**Key Topics:** ME1/ME2/ME3 = 54/154/136 s; ramps; Bosch scallops and why not; gas and bias pulsing; depth by model, feed-forward, and feedback  
**Study Questions:** 5

### Chapter 9: [Chamber Conditioning, By-Product Control & Fleet Matching](./chapters/09-chamber-conditioning-fleet-matching.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Key Topics:** Wall recombination γ_O, γ_F; 60 nm drift per lot without cleans; WAC with seasoning; wet clean and recovery; particles become missing trenches; matching by time offsets  
**Study Questions:** 5

---

## Part III: Phenomena (Chapters 10–14)

### Chapter 10: [Profile — Taper, Bow, Necking & the Bottom Shape](./chapters/10-profile-taper-bow-bottom.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration  
**Key Topics:** Three-zone profile; bow sources in the collar zone; neck and fill voids; taper costs depth and perimeter; bottom shapes and field enhancement 1 + t/r  
**Study Questions:** 5

### Chapter 11: [Twist, Tilt, Merging & Placement](./chapters/11-twist-tilt-merging-placement.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Process/Integration  
**Key Topics:** Tilt is collective, twist random; edge tilt 0.2° → 17.5 nm; wall 70 nm, σ_wall 1.95 nm, 15σ margin; heavy tails from particles and mask defects; paired-bit signature  
**Study Questions:** 5

### Chapter 12: [Silicon Grass, Etch Stop & Rare Events](./chapters/12-grass-etch-stop-rare-events.md)
**Estimated Time:** 50 min | **Difficulty:** Advanced | **Reading Level:** Process/Device  
**Key Topics:** Micromasking and needle height; cryogenic grass ×1000 over two points of O₂; narrow trench ends 0.44 µm shallow; target 5×10⁻⁹ per trench; short-loop arrays and voltage contrast  
**Study Questions:** 5

### Chapter 13: [The Bottle Etch — Widening the Lower Trench](./chapters/13-bottle-etch-widening.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Integration/Process  
**Key Topics:** Collar-then-bottle; NH₄OH crystallographic bottle; pulsed remote-plasma bottle (18% gradient unpulsed); oxidation-strip; inheritance from the trench; the bottle spends 50 nm of wall  
**Study Questions:** 5

### Chapter 14: [SOI eDRAM, Downstream Recesses & Silicon Trench Capacitors](./chapters/14-soi-edram-recesses-silicon-capacitors.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Integration  
**Key Topics:** BOX step and notch; shorter collar on SOI; three recesses inherit the mouth; silicon trench capacitors at 69 nF/mm²; DTI, trench gates, TSVs  
**Study Questions:** 5

---

## Part IV: Production (Chapters 15–16)

### Chapter 15: [Modelling, Metrology & Advanced Process Control](./chapters/15-modelling-metrology-apc.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Process/Equipment/Research  
**Key Topics:** Lumped, reduced-order, feature-scale models; t/h linearization; IR effective-medium depth; feed-forward −2.6 s/nm; EWMA; SiBr virtual metrology; ±0.08 µm with full APC  
**Study Questions:** 5

### Chapter 16: [Yield, Retention & Cost of Ownership](./chapters/16-yield-retention-cost.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Integration/Device/Management  
**Key Topics:** Retention 72 s typical, tail at 500× leakage; etch owns ≈ 40% of the tail; bit-map signatures; ≈ $27 per wafer (R1), ≈ $24 (R2); depth is the cheapest capacitance  
**Study Questions:** 5

---

## Appendices

| Appendix | Content |
|----------|---------|
| [A](./appendices/A-material-properties.md) | Silicon, pad, mask, liner, dielectric, fill, chamber, by-product properties; constants |
| [B](./appendices/B-chemistry-surface-kinetics.md) | Dissociation, surface reactions, Flamm rate, yields, reaction probabilities, wall recombination, cryogenic film, wet chemistry |
| [C](./appendices/C-standard-procedures.md) | Chamber qualification, monitoring, model calibration, edge ring, depth excursion, cross-section |
| [D](./appendices/D-process-windows.md) | Mask open, DT-R1, DT-R2, WAC, bottle recipes and windows; sensitivities |
| [E](./appendices/E-scaling-transport-calculations.md) | All closed-form models with reference values |
| [F](./appendices/F-metrology-modelling-reference.md) | Metrology methods, sampling, IR model, model forms, rare-event statistics |
| [G](./appendices/G-troubleshooting-guide.md) | Symptom-driven troubleshooting |
| [Glossary](./GLOSSARY.md) | Terminology |

---

## Reading Paths by Role

### Process Engineer (≈ 9 hours)
Chapters 1, 3, 4, 6, 8, 10, 12 → Appendices D, G

### Equipment Engineer (≈ 7 hours)
Chapters 3, 5, 7, 9, 15 → Appendices A, C

### Integration Engineer (≈ 8 hours)
Chapters 1, 2, 10, 11, 13, 14, 16 → Appendix E

### Device Engineer (≈ 5 hours)
Chapters 1, 12, 16

### Researcher and Modeller (≈ 10 hours)
Chapters 3, 4, 6, 7, 11, 15 → Appendices B, E, F

---

## Cross-Reference Map to Other Books

| Book | Title | Used in |
|------|-------|---------|
| #1–5 | Plasma Physics & Chemistry Fundamentals | Ch. 3, 4, 5 |
| #11–15 | Advanced Plasma Engineering | Ch. 5–9, 15 |
| #26 | DRAM Isolation Trench Etch | Ch. 1, 14 |
| #29 | DRAM Capacitor Hole Etch | Ch. 1, 4 (stacked-cell comparison) |
| #31 | DRAM High-Aspect-Ratio Capacitor Etch | Ch. 1, 4, 7, 11 (transport, cryogenic, twist) |
| Companion | Polysilicon Etch | Ch. 3, 14 |
| Companion | Recess Etch | Ch. 14 |
| Companion | Shallow Trench Isolation Etch | Ch. 1, 14 |
| Companion | Silicon Nitride Etch; Thermal Oxide Etch | Ch. 2, 13 |
| Companion | 3D NAND High-Aspect-Ratio Oxide/Nitride Stack Etch | Ch. 7 |

---

## Study Questions Summary

**Total Study Questions:** 81 (5–6 per chapter × 16 chapters)  
**Nature:** Mostly calculation-based  
**Topics:** Sense signal and capacitance, mask budget, Flamm rate, ARDE and time to depth, CD-to-depth sensitivity, by-product load, heat balance, profile levers, cryogenic windows, step times, wall recombination, tilt and wall budget, needle height, bottle transport, BOX notch, model calibration, APC, retention, cost

Examples:
- Compute the capacitance of a 7 µm trench without a bottle
- Find the lateral etch of an unprotected wall at 80 °C
- Derive ∂h/∂w from the time-to-depth relation
- Find the O₂/pressure combination that cuts bow without closing the bottom
- Compute ME3 time for a lot with a small top CD
- Estimate σ_wall when bottle variation doubles
- Compute the CDE bottle gradient for a different F reaction probability
- Fit ER₀ and k from two depth measurements
- Compare deepening the trench with widening the bottle for 2 fF

---

## How to Use This Index

1. **First time?** Read PREFACE.md, then this INDEX, then Chapter 1.
2. **Focused reading?** Pick your role from the reading paths above.
3. **Reference mode?** Jump to the chapter. Use Appendix G for symptoms and Appendix E for formulas.
4. **Deep dive?** Read Chapters 1–16 in order and work the study questions.

---

**Index Version:** 1.0  
**Last Updated:** 2026-10-05  
**Next:** Begin [Chapter 1: The Trench Cell — Why Store Charge Below the Silicon](./chapters/01-trench-cell-capacitance.md)
