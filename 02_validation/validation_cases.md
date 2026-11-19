# Validation cases: hand calculations

E = 29,000 ksi for steel. Self-weight off unless stated. Tolerance: 0.5%.
The app runs these same cases live in its "Validation cases" panel.

## 1. 20 ft simply supported W12x26, w = 1 kip/ft live
- R = wL/2 = 1(20)/2 = 10.0 kips = V_max
- M = wL²/8 = 1(20²)/8 = 50.0 kip-ft
- fb = M/Sx = 50(12)/33.4 = 17.96 ksi ≤ 33 ksi
- Va = 0.6(50)(12.2)(0.230)/1.50 = 56.1 kips
- Δ = 5wL⁴/384EI = 5(1/12)(240⁴)/(384 · 29000 · 204) = 0.609 in ≤ L/360 = 0.667 in

## 2. Same beam, P = 10 kips live at midspan
- M = PL/4 = 10(20)/4 = 50.0 kip-ft
- Δ = PL³/48EI = 10(240³)/(48 · 29000 · 204) = 0.487 in

## 3. Same beam, P = 10 kips live at x = 5 ft (a = 15 ft from the right, b = 5 ft from the left)
- R_left = 10(15)/20 = 7.5 kips, R_right = 2.5 kips
- M_max = 7.5(5) = 37.5 kip-ft at x = 5 ft
- Δ_max = P·a·b(a + 2b)·√(3a(a + 2b)) / (27EIL), with a = 180 in and b = 60 in
  = 10(180)(60)(300)√162000 / (27 · 29000 · 204 · 240) = 0.340 in
- Location: √(a(a + 2b)/3) = √(15 · 25/3) = 11.18 ft from the right end, so x = 8.82 ft

## 4. 10 ft cantilever W8x18, P = 2 kips live at the tip
- M = PL = 20.0 kip-ft; fb = 20(12)/15.2 = 15.8 ksi
- Δ = PL³/3EI = 2(120³)/(3 · 29000 · 61.9) = 0.642 in ≤ 2L/360 = 0.667 in

## 5. 12 ft simply supported 2x10 DF-L No. 2, w = 100 plf live, repetitive, C_D = 1.0
- A = 1.5(9.25) = 13.875 in², S = 21.39 in³, I = 98.93 in⁴, E = 1,600,000 psi
- M = 0.1(12²)/8 = 1.80 kip-ft = 21,600 lb-in; fb = 21,600/21.39 = 1010 psi
- Fb′ = 900(1.0)(1.1)(1.15) = 1139 psi → pass
- V = 600 lb; fv = 1.5(600)/13.875 = 64.9 psi ≤ 180 psi
- Δ = 5(100/12)(144⁴)/(384 · 1.6e6 · 98.93) = 0.295 in ≤ L/360 = 0.400 in

## 6. Case 1 with self-weight (26 plf dead)
- w_total = 1.026 kip/ft; M = 1.026(400)/8 = 51.3 kip-ft
- Δ_total = 0.609(1.026) = 0.625 in ≤ L/240 = 1.00 in
