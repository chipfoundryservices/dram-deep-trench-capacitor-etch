# Appendix G: Troubleshooting Guide

Symptom-driven guide for deep-trench etch excursions. For each symptom: likely causes ranked from most to least common, checks to separate them, and corrective actions. Chapter references point to the underlying physics.

---

## G.1 Depth Low, Whole Wafer, One Chamber

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Wall state drift: WAC incomplete        O/Ar up, F/Ar down; WAC endpoint     Restore WAC time; check
   (Ch. 9.1–9.2)                           trace longer                         NF₃ MFC; season
2. Bias delivered power low (generator     V–I probe at chuck; bias voltage     Recalibrate; replace
   or match) (Ch. 5.2)                     readback                             generator
3. O₂ MFC reading low (actual high)        MFC verify; bottom CD smaller        Recalibrate MFC
   (Ch. 6.2)
4. Window coated → source coupling down    Source match position; SiBr          Window clean / PM
   (Ch. 5.3)                               emission down
```

## G.2 Depth Low, Lot-Wide, All Chambers

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Mask-open top CD small (Ch. 2.2, 4.5)   CD-SEM after open                    Feed-forward ME3 time;
                                                                                fix mask open
2. APC feed-forward input missing or       APC log; Δt_ME3 applied              Fix input; re-run
   wrong (Ch. 15.3)                                                             disposition
3. Native oxide thicker (queue time        Queue time; BT trace                 Enforce queue time;
   after strip) (Ch. 2.5)                                                       lengthen BT
```

## G.3 Depth Low at the Wafer Edge

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Edge-ring wear (Ch. 9.5, 11.2)          Ring RF hours; edge tilt monitor     Ring lift / replace
2. Mask-open edge CD small                 Radial CD map                        Radial feed-forward
                                                                                (Ch. 15.3.1)
3. Edge chuck zone warm/cold               Zone temperatures, He by zone        Restore set point
```

## G.4 Bow Up (Collar Zone)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. ME1 SiF₄ low or missing (Ch. 8.2)       MFC readback; recipe version         Restore SiF₄
2. BSG facet larger (mask open, Ch. 2.4)   CD-SEM facet width; BSG remaining    Mask-open tune
3. Chuck temperature high or He leak up    He leak; zone temps                  Chuck service
   (Ch. 3.6, 5.4)
4. Pressure high (throttle valve drift)    Valve position vs history            Valve service
   (Ch. 6.3)
5. First wafer after clean (fluorinated    Wafer slot vs bow                    Seasoning step 3
   wall) (Ch. 9.2)
```

## G.5 Bottom CD Small / Taper Up

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Wall state: O to wafer up (Ch. 9.1)     O/Ar up                              WAC; O₂ APC offset
2. O₂ in ME3 high / bias low (Ch. 8.2)     Recipe; readbacks                    Restore ME3
3. NF₃ low                                 MFC verify                           Recalibrate
4. Chuck cold (Ch. 3.6)                    Zone temps                           Restore set point
```

## G.6 Grass / Black Silicon at the Bottom

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Mask-open residue (Ch. 2.5, 12.1)       TEM of opening before etch; BT       Lengthen BT; fix open
                                           trace                                strip
2. ME3 O₂ high / NF₃ low (Ch. 12.1.2)      Recipe and MFCs                      Restore
3. Chamber particles (Y₂O₃) (Ch. 9.4)      Particle monitor; EDS of needle      Wet clean; inspect
                                           tips                                 coating
4. R2: O₂/SF₆ high or wafer too cold       He pressure, chuck temp; ratio       Return inside window
   (Ch. 7.4.1)                                                                  (≤ 9%, ≥ −105 °C)
```

## G.7 Merged Trenches (Paired Bits Along the Minor Axis)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Particles on mask during etch           Particle adders; cluster map         PM; transfer-path
   (Ch. 11.5)                                                                   clean
2. Bottle over-widened (Ch. 13.4)          Bottle monitor; wet bath temp/       Bottle time/temp
                                           concentration
3. Twist up: film asymmetry, rough mask    X-SEM / delayer twist; LER           Recipe balance;
   (Ch. 11.3)                                                                   mask LER
4. Mask defects (BSG pinholes, litho       Post-open inspection                 Litho / deposition
   bridging)
```

## G.8 Low Capacitance, Normal Depth

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Bottle under-widened (Ch. 13)           Bottle monitor; wet bath age         Restore bottle
2. Sidewall film left → unwidened stripes  TEM of post-clean wall               Post-DT clean (Ch. 2.6)
   (Ch. 13.3)
3. Collar recess too deep (bottle top      Recess depth                         Recess control
   lower) (Ch. 13.1)
4. Taper up → smaller bottle perimeter     X-SEM bottom CD                      See G.5
   (Ch. 10.4)
5. Dielectric EOT high (non-etch)          EOT monitor                          Dielectric module
```

## G.9 High Leakage Tail, Normal Capacitance

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Pointed or microtrenched bottom         TEM bottom shape                     ME3 bias/O₂ (Ch. 10.5)
2. Grass needles (Ch. 12.1.4)              Delayer SEM at bottom                See G.6
3. Sidewall roughness up (Ch. 6.4)         TEM roughness; mask LER              Recipe; smoothing
                                                                                oxidation
4. Collar thin at the bow (Ch. 16.1.2)     X-SEM collar                         See G.4
```

## G.10 BSG Remaining Low

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Bias high (generator) (Ch. 3.5)         V–I probe                            Recalibrate
2. Incoming BSG thin                       BSG thickness per lot                Feed-forward hold
                                                                                (Ch. 15.3)
3. ME3 time extended by APC beyond         APC log                              Cap ME3 extension;
   the mask budget                                                              investigate CD
4. NF₃ high                                MFC verify                           Recalibrate
```

---

**Appendix G Version:** 1.0
