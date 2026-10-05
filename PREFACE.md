# Preface: The Capacitor Below the Transistor

## Why This Book Exists

Books #29 and #31 followed the DRAM capacitor upward: a hole in an oxide mold, above the bit line, deepened generation after generation until it reached 91:1. This book follows the other road. In the **trench cell**, the capacitor is etched downward into the silicon substrate itself, as the first patterned step of the whole process, before any transistor exists. The trench cell held a large share of DRAM production for two decades, down to the 46 nm generation, and it remains the basis of **embedded DRAM** on logic processes and of **silicon trench capacitors** for passive and decoupling devices.

The reference trench of this book is an ellipse 70 × 110 nm at the surface and **5.00 µm deep**: an aspect ratio of 71:1 at the top, 83:1 at its average width. After the etch it is widened into a bottle below a collar, lined with a 2.5 nm-EOT dielectric, filled, and recessed three times. It holds **20.6 fF**.

A silicon trench sounds like an easier etch than an oxide hole of the same depth. Silicon etches faster, and it conducts away the charge that twists oxide holes. In practice the deep trench has its own hard problems:

1. **There is no etch stop.** Nothing lies below the trench but more silicon. Depth is set by time, and time is the same for every trench on the wafer.

2. **Width becomes depth.** At fixed time, a trench 1 nm narrower ends 26 nm shallower. The mask-open CD distribution becomes the depth distribution, and the depth distribution becomes the capacitance distribution.

3. **Fluorine etches sideways.** Atomic fluorine attacks silicon without ions. An unprotected wall would lose 70 nm per side during the etch. The profile depends on a passivation film made from the etch's own products, and on a balance between deposition and removal that is off by only 0.2%.

4. **The chamber is a reactant.** Each wafer leaves nearly two grams of silicon bromide behind. The coating on the walls changes the oxygen and fluorine reaching the next wafer. Without a clean and a seasoning after every wafer, depth drifts by half its budget within a lot.

5. **The bottle spends the wall.** After the etch, the lower trench is widened by 25 nm per side to gain 61% more capacitance. Only about 30 nm of silicon margin remains between neighbours. A particle that deflects one trench in a billion merges two storage nodes.

6. **The trench is first.** Every residue, every bit of damage, every rough patch on the wall is driven into the crystal by the thermal steps that follow and is inherited by the collar, the bottle, the dielectric, the fill, and the recesses.

This book treats the deep-trench etch as **a timed, passivation-balanced silicon etch whose output is capacitance**, and follows each of its parameters to the retention tail.

---

## Unique Aspects of Deep-Trench Capacitor Etch

### 1. Silicon Chemistry, Not Fluorocarbon

The reference chemistry is HBr/NF₃/O₂. Bromine drives an ion-assisted, anisotropic etch; fluorine raises the rate and cleans the bottom; oxygen converts etch products into an SiOₓBrᵧ film on the walls. Every profile lever in the book is a lever on that film.

### 2. Two Processes

The book carries two etches through every chapter: **DT-R1**, the HBr/NF₃/O₂ production reference at +60 °C, and **DT-R2**, a cryogenic SF₆/O₂ process at −100 °C that is twice as fast and spares the mask but must hold the wafer to ±1 °C and stay clear of black silicon.

### 3. Depth Control by Model

Without an etch stop, depth is controlled by a model, by feed-forward of the incoming CD, and by feedback from infrared depth measurement. The deep trench is one of the few major etches in the fab that is entirely time-controlled.

### 4. The Bottle and the Wall

The trench etch is judged not only by its own shape but by what the bottle etch can make of it. Taper, twist, roughness, and residual film all pass through the bottle into capacitance and merging.

### 5. A Billion Trenches per Die

At about 10⁹ trenches per die, defects at 10⁻⁹ per trench decide repair. Grass, blocked trenches, narrow-tail trenches, and merged pairs are treated as yield items with their own statistics.

---

## Why This Book Is Organized This Way

Book #32 follows the same four-part structure as Books #19–31:

**Part I: Fundamentals (Chapters 1–4)**
- The trench cell and its capacitance, the hard-mask stack, the silicon etch chemistry and its passivation, and the transport that sets ARDE and the CD-to-depth sensitivity

**Part II: Hardware & Chemistry (Chapters 5–9)**
- ICP deep-silicon platforms and their by-product load, passivation engineering, cryogenic etch, depth-adaptive recipes, and chamber conditioning and matching

**Part III: Phenomena (Chapters 10–14)**
- Profile, twist and merging, grass and rare events, the bottle etch, and SOI eDRAM, downstream recesses, and silicon trench capacitors

**Part IV: Production (Chapters 15–16)**
- Modelling, metrology, APC, yield, retention, and cost

### Reading Paths

**Process Engineers:** Chapters 3, 4, 6, 8, 10, 12  
→ Chemistry, ARDE, profile levers, recipes by depth, profile defects, grass

**Equipment Engineers:** Chapters 5, 7, 9, 15  
→ Platforms, cryogenic chucks, wall conditioning, matching, virtual metrology

**Integration Engineers:** Chapters 1, 2, 11, 13, 14  
→ Capacitance budget, mask stack, wall budget, bottle, recesses, SOI

**Device Engineers:** Chapters 1, 12, 16  
→ How depth, bottle, and bottom shape become capacitance, leakage, and failing bits

**Researchers and Modellers:** Chapters 3, 4, 6, 7, 11, 15  
→ Surface kinetics, transport, film balance, cryogenic mechanism, twist, feature-scale models

---

## Key Questions This Book Answers

1. **Why is a 20 fF trench 5 µm deep, and how much of its capacitance comes from the bottle?**
2. **Why does fluorine need a passivation film, and what makes that film?**
3. **How does etch time scale with depth, and why does a 1 nm narrower trench end 26 nm shallower?**
4. **How is depth controlled to ±0.12 µm with no etch stop?**
5. **Which gas sets the taper, which sets the rate, and which separates bow from bottom CD?**
6. **When does cryogenic etch beat HBr/NF₃/O₂?**
7. **Why does a coated chamber wall make the trench taper, and how is it reset every wafer?**
8. **Why does tilt not spend the silicon wall but twist does, and what sets the merging rate?**
9. **How does the bottle etch inherit the trench profile?**
10. **What is the cheapest way to add capacitance: depth, bottle, or dielectric?**

---

## How to Read This Book

**Complete study (2–3 weeks):** Read Part I closely, then work through Parts II and III in order. Finish with Part IV.

**Focused study (3–5 days):** Read Chapters 1, 3, and 4, then follow the reading path for your role.

**Reference mode:** Go straight to the chapter you need. Use the INDEX, GLOSSARY, Appendix E for formulas, and the Appendix G troubleshooting guide.

**Every chapter includes:**
- Learning objectives
- Worked calculations with the reference values substituted
- Tables of levers and responses
- A summary of key takeaways
- Study questions

---

## The Reference Process

```
Reference cell:        45 nm-class trench cell, 8F² = 16,200 nm²,
                       minor-axis trench pitch 180 nm
Reference trench:      ellipse 70 × 110 nm at the Si surface; 5.00 µm
                       deep; bottom 50 × 88 nm; average minor CD 60 nm;
                       A = 71 (top), 83 (average)
Stack:                 900 nm BSG / 150 nm pad SiN / 5 nm pad oxide on
                       p-type ⟨100⟩ 300 mm Si
Downstream:            collar 0.10–1.20 µm; bottle 1.20–4.80 µm, +25 nm
                       per side; As buried plate; EOT 2.50 nm high-k
                       node dielectric; C_s = 20.6 fF
Reference etch DT-R1:  ICP, 2.5 kW source, 2 MHz bias 700–1100 W;
                       HBr/NF₃/O₂ (+SiF₄); 28–30 mTorr; chuck +60 °C;
                       ER₀ = 1600 nm/min, k = 0.020; three main-etch steps,
                       344 s; BSG remaining 300 nm
Reference etch DT-R2:  ICP with cryogenic chuck at −100 °C; SF₆/O₂ (8%);
                       12 mTorr; 250 W bias; ER₀ = 3000 nm/min, k = 0.012;
                       150 s; BSG loss 125 nm
```

We assume you know basic plasma physics and the general behaviour of silicon etching in halogen plasmas. We do **not** assume you know the trench cell, the passivation balance of deep silicon etch, cryogenic surface chemistry, or the downstream bottle and recess modules.

---

## Organization of This Repository

1. **README.md**: overview, scope, file structure, cross-references
2. **PREFACE.md**: this document
3. **INDEX.md**: detailed chapter outline, reading paths, estimated times
4. **chapters/**: Chapters 1–16
5. **appendices/**: Appendices A–G
6. **GLOSSARY.md**: technical terminology

---

## Acknowledgments & Scope

Book #32 is part of the **ChipFoundryServices Technical Series**. It draws on:

- The published plasma etch literature on silicon trench etching in HBr, Cl₂, and fluorine chemistries, sidewall passivation, ARDE, and cryogenic silicon etch
- Classical results on spontaneous fluorine etching of silicon and on free-molecular flow through tubes (Knudsen, Clausing, Coburn–Winters)
- Published descriptions of trench DRAM and eDRAM cells, bottle and collar processes, buried plates, and node dielectrics
- Literature on silicon trench capacitors, deep trench isolation, and through-silicon vias
- Representative industrial practice for deep-trench modules
- The earlier books in this series, especially Books #29 and #31 and the companion volumes *Recess Etch* and *Polysilicon Etch*

It is a **technical reference for professionals**. Background in plasma processing is assumed.

---

## Final Thought

A trench 60 nm wide and 5 µm deep has the proportions of a well 6 cm across and 5 m deep. It is cut into a single crystal, a billion times on each die, with walls between the wells little wider than the wells themselves, and every well must end within 2.4% of the same depth with nothing at the bottom to tell the etch to stop.

Mastering deep-trench capacitor etch means seeing that **the film that keeps the wall straight, the time that sets the depth, and the wall that the bottle will spend are one balance**, and knowing in numbers what each nanometre of it is worth in femtofarads. This book is meant to build that understanding.

---

**Welcome to Book #32: DRAM Deep Trench Capacitor Etch — Timed, Passivation-Balanced Silicon Etch for Trench DRAM, eDRAM, and Silicon Trench Capacitors.**
