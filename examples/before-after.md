# Before / after — what "governed" means

## Messy in
- `Neware_45C_cell3.xlsx`: columns `Cap(mAh)`, `Mass?`, merged headers, rest steps counted as cycles 12, 13, 14
- `Biologic_VMP3.mpt`: tech loops, `I/mA` vs `Ewe/V`, 40k rows, no mass column
- Result in Excel: two curves off by 22% because mass was electrode total in one, active in the other

## Clean out (see templates/)
- One table: cycle, Q_charge, Q_discharge, CE, V_mean, T, mass_active_g, source_file, excluded_reason
- Plot: discharge retention with mechanism label + interval, not just a line
- Export: CSV + RO-Crate with instrument, mass, window, exclusions, model version

Add your screenshots here: `before.png` / `after.png` in this folder. Keep file names, hide proprietary chemistry if needed.

Live demo of the same flow: https://matflow.celaron.com → "use demo dataset"
