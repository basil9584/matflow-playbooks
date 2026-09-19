# Cycler QA checklist — run this before you trust any plot

1. Mass recorded? Active mass in grams, not electrode total. Missing mass = fake mAh/g.
2. Units: mAh vs Ah, mg vs g. Check factor-1000 errors first.
3. Current sign: charge positive? Flip if your cycler does the opposite.
4. Cycle reconstruction: rest steps counted as cycles? Remove them.
5. Formation cycles flagged? Don't fit degradation on cycles 1-3.
6. Temperature column present? 25C vs 45C changes everything.
7. Voltage window consistent? 2.5-4.2V every cycle or it drifted?
8. Duplicate timestamps? Merge, don't average blindly.
9. Missing cycles: gap = 50-75? Note it, don't interpolate for RUL.
10. Coulombic efficiency in [0.9, 1.01]? Outside = bad cycle, exclude from fit.
11. Export encoding: UTF-8, commas, no merged header rows. Save a clean copy.

If 3+ fail, clean first. Matflow rejects unsupported files before charging for exactly this reason.
Live demo: https://matflow.celaron.com
