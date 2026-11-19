# Prompt history

- Asked: Set up the project folders and top-level files for a single-file web app, document the layout, and do not build anything else.
  Changed: Added the numbered folders with README files, documented file placement in `AGENTS.md`, and added minimal top-level specification and HTML placeholders.
  Worked: Yes.

- Asked: Review `spec.md` and give suggestions and recommendations (including real beam section properties); do not write code.
  Changed: No project files changed except this entry. Gave a review in chat covering section-property data, design criteria, missing checks (shear, self-weight, live vs. total deflection), solution method, and more validation cases. Checked the W12x26 validation numbers by hand (M = 50.0 kip-ft, deflection 0.609 in).
  Worked: Yes (review only).

- Asked: Ask 3 specific questions to make the app better.
  Changed: Asked about the steel check method, load classification, and lumber coverage. Answers: Fb = 0.66Fy with fb = M/Sx; Dead/Live load tags (live deflection L/360, total L/240, optional self-weight); DF-L No.2 only, with C_D, C_F, and C_r. No project files changed except this entry; `spec.md` not yet updated.
  Worked: Yes.

- Asked: Update `spec.md` with the review recommendations and the answers to the 3 questions.
  Changed: Rewrote `spec.md`. Added Assumptions (bracing, materials, sign convention, units) and Dead/Live tagged loads with partial-length uniform loads and a self-weight checkbox. Added section data tables for 11 W-shapes and 10 DF-L No. 2 lumber sizes (both to be checked against AISC/NDS), and the numerical calculation method. Checks are now bending (0.66Fy for steel, Fb' = Fb·C_D·C_F·C_r for lumber), shear, and live/total deflection (L/360 and L/240, using 2L for cantilevers). Outputs now include ratio tables and a print view. Validation now has 6 hand-checked cases with a 0.5% tolerance.
  Worked: Yes (spec only, no code).

- Asked: Write the code in `index.html`.
  Changed: Built the full single-file app in `index.html`. It has a DOM-free calculation engine and a UI with live inputs for support, span, W-shape or DF-L No. 2 lumber (C_D, C_r), self-weight, and Dead/Live point and partial uniform loads, with input validation. Output is a check table (bending, shear, live and total deflection, with ratios and pass/fail), an SVG loading sketch, and shear, moment, and deflection diagrams with max values labeled. Also added a print view, dark mode, and a built-in panel that runs the 6 validation cases. Added `01_data/w_shapes_aisc_v16.csv`, `01_data/lumber_dfl_no2.csv`, and `02_validation/validation_cases.md`, plus screenshots in `03_output/`.
  Worked: Yes. All 6 validation cases pass in Node (largest difference 0.2%), and extra checks match closed-form answers (partial uniform load, cantilever uniform load). Headless Chrome screenshots confirmed the layout on desktop and at 500 px wide with no horizontal scroll. Fixed overlapping labels on stacked uniform loads. Section properties still need checking against AISC/NDS.

- Asked: (1) Suggest edits; (2) make the diagrams interactive so any point can be read; (3) add a few more interactive visuals; (4) show a scaled deflected shape on the top plot and a red failure/breaking animation when the beam fails.
  Changed: `index.html`: probe line shared by the sketch and all three diagrams (hover, tap, click to pin, arrow keys, snapping); x-axes aligned across plots. Added a deflected shape on the sketch (auto limit-based scale or ×1/×10/×50/×200, with the limit marked). Added a red crack-and-collapse animation for bending/shear failure (diagonal crack for shear) with a shake, debris, failure label, and Replay button; a deflection-only failure shows a red sagging beam instead. New visuals: draggable loads with end handles, a "Stresses at the probe" panel (section, bending and shear stress distributions vs. allowables), a what-if load multiplier slider showing the multiplier at first failure (`reserveFactor()` in the engine), and a clickable section comparison chart tagging the lightest passing section. Updated `spec.md` (interactive tools, deflected shape, failure display, 2000-step grid). Added screenshots to `03_output/`. Gave the suggested edits in chat.
  Worked: Yes. All 6 validation cases still pass (max diff 0.2%). The reserve factor checks exactly (ratio 1.0000 at the reported multiplier). In headless Chrome: probe values match hand calcs (x = 5 ft: V = 5.00 k, M = 37.50 k-ft, fb = 13.47 ksi), drag moved a point load, the multiplier triggered the break animation, compare-row click switched sections, no console errors, no horizontal scroll at 420 px. Fixed tooltips overlapping max labels and broken pieces falling too far.

- Asked: Commit and share publicly on GitHub.
  Changed: Added `.gitignore` (ignores `.DS_Store`; it has to sit at the repo root for git to use it) and made the first commit on `main` with all project files.
  Worked: Partly. The local commit worked. The push did not happen because this machine has no GitHub login (no `gh` CLI, SSH key, or saved credentials), so the public repo and GitHub Pages setup are waiting on the user.
