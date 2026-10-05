# Appendix E: Scaling & Transport Calculations

Closed-form models used in the book, with the reference values substituted. Each block can be reused with a fab's own numbers.

---

## E.1 Capacitance of an Elliptical Trench

```
Ellipse perimeter (Ramanujan), semi-axes a, b:
  P = π [3(a + b) − √((3a + b)(a + 3b))]

  a, b (nm)      P (nm)    Use
  ──────────────────────────────────────────────
  35, 55         286       top opening
  30.5, 48.5     ≈ 250     as-etched, mid-bottle
  55, 75         411       reference bottle
  53.5, 73.5     401       bottle with 44 nm bottom CD

C_s = (C/A) × [P_bottle × L_bottle + A_bottom]
    = 13.8 fF/µm² × [0.411 × 3.60 + 0.013] µm² = 20.6 fF

Sensitivities:
  ∂C/∂L = (C/A) P = 5.67 fF/µm
  ∂C/∂δ (uniform widening per side) ≈ (C/A) × 2π × L = 0.31 fF/nm
```

---

## E.2 Sense Signal and Retention

```
ΔV_BL = (V_BLH/2) C_s / (C_s + C_BL)
  20.6 fF, 90 fF, 1.2 V → 112 mV (109 mV with C_s = 20 fF)
t_ret = C_s ΔV_allow / I_leak
  20.6 fF × 0.35 V / 0.1 fA = 72 s;   / 50 fA = 144 ms
```

---

## E.3 Ion Angle and Acceptance

```
Collisionless spread: θ ≈ √(T_i⊥ / E_i), T_i⊥ ≈ 0.05 eV
  450 eV → 0.60°;  150 eV → 1.04°;  120 eV (R2) → 1.17°
Sheath collisions: P_nc = exp(−s/λ); λ = 1/(nσ)
  30 mT, 330 K, σ = 4×10⁻¹⁹ m²: λ = 2.8 mm; s = 0.9 mm → 0.73
Acceptance (edge to edge): θ_acc = arctan(w / h_tot)
  w = 50 nm, h_tot = 5455 nm → 0.53°
```

---

## E.4 Neutral Transport

```
Coburn–Winters (long tube, diffuse walls, no wall loss):
  Γ_bot / Γ_top ≈ 1 / (1 + (3/4) s A)

  s \ A       20      50      83      120
  ─────────────────────────────────────────
  0.005      0.93    0.84    0.76    0.69
  0.02       0.77    0.57    0.45    0.36
  0.05       0.57    0.35    0.24    0.18
  0.10       0.40    0.21    0.14    0.10

Lumped ARDE: ER = ER₀ / (1 + kA), k ≈ (3/4) s_eff
```

---

## E.5 Time to Depth

```
ER₀ t = h + k h² / (2w)

Inverse: h = [−1 + √(1 + 2k ER₀ t / w)] / (k / w)

R1 (ER₀ 1600 nm/min, k 0.020, w 60 nm):
  h (µm)    1      2      3      4      5      6      7
  t (min)   0.73   1.67   2.81   4.17   5.73   7.50   9.48

R2 (ER₀ 3000 nm/min, k 0.012, w 60 nm):
  h (µm)    1      2      3      4      5      6      7
  t (min)   0.37   0.80   1.30   1.87   2.50   3.20   3.97
```

---

## E.6 CD Sensitivity

```
∂h/∂w|_t = (k A² / 2) / (1 + k A)

  A        R1 (k 0.020)    R2 (k 0.012)
  ───────────────────────────────────────
  50       12.5            9.4
  83.3     26.0            20.8
  100      33.3            27.3
  117      41.0            34.2
```

---

## E.7 Mask Budget

```
BSG_end = BSG₀ − loss_pre − H / S_eff
  R1: 900 − 100 − 5000/10 = 300 nm
  R2: 800* − 5000/40 = 675 nm   (*after 100 nm pre-etch loss)
Maximum depth with reserve R: H_max = S_eff (BSG₀ − loss_pre − R)
  R1, R = 150: 10 × 650 = 6.5 µm
```

---

## E.8 Tilt and Wall

```
Lateral shift: Δ = H tan θ
  θ (°)     0.05    0.10    0.15    0.20    0.25
  Δ at 5 µm (nm)  4.4     8.7    13.1    17.5    21.8

Wall at mid-bottle: W = p − w_etch − 2δ = 180 − 61 − 50 ≈ 70 nm
σ_wall = √(2 (σ_CD,r² + σ_δ² + σ_tw²))
  = √(2 (0.67² + 0.67² + 1.0²)) = 1.95 nm
```

---

## E.9 Thermal

```
Wafer ΔT over chuck: ΔT = q / h_He
  R1: 1.77 W/cm² / 0.06 W/cm²·K ≈ 30 K
  R2: 0.85 W/cm² / 0.05 W/cm²·K ≈ 17 K
Flamm ratio between T₁ and T₂: (T₁/T₂)^½ exp(−1250 (1/T₁ − 1/T₂))
```

---

## E.10 By-Product Load

```
Si removed per wafer = f_open × A_wafer × H × n_Si
  0.17 × 707 cm² × 5×10⁻⁴ cm × 5.0×10²² = 3.0×10²¹ atoms ≈ 1.7 g as SiBr₄
```

---

**Appendix E Version:** 1.0
