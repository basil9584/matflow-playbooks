# Battery Excel cleaning guide (Neware / BioLogic / Arbin / Maccor)

You have 3 exports that don't match. Here's the fix order that actually works:

## 1. Normalize columns first
Map to: cycle_number, charge_capacity_mAh_g, discharge_capacity_mAh_g, voltage_mean_V, current_mA, temperature_C, mass_active_g.
Keep the original file untouched. Work on a copy. See `../templates/battery_cycles_template.csv`.

## 2. The 3 silent killers
- **Mass:** Neware often gives mAh, BioLogic gives mA.h — divide by active mass in g. One wrong mass = whole curve shifts.
- **Cycle definition:** BioLogic .mpt counts every loop as cycle. Group by real charge-discharge pair.
- **Rest steps:** voltage hold / rest rows inflate cycle count. Filter to galvanostatic steps only.

## 3. Quick RUL sanity check (no model needed)
Plot discharge_capacity vs cycle_number. If capacity drops fast in first 10 cycles then flattens, that's SEI-dominated (sqrt-n). If linear then cliff, that's cycling + lithium loss. Don't fit a straight line through both.

## 4. When to use a tool
- cellpy (free): great if you code, handles many formats.
- Matflow demo (https://matflow.celaron.com): upload → auto-normalize → RUL with intervals + mechanism pick by held-out RMSE. Use "use demo dataset" to see expected output before uploading yours.

## 5. Export you can defend
Include: instrument, file name, mass used, voltage window, temperature, excluded cycles + reason, model + interval. If you can't list these, your PI will ask.
