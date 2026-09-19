# EIS fitting guide — pick a circuit without lying to yourself

Sample data: `../templates/eis_sample.csv` (freq_Hz, Z', -Z'').

## Which circuit?
- **Randles (Rs - Rct/Cdl - W):** one semicircle + 45-degree tail. Start here.
- **SEI version (Rs - Rsei/Csei - Rct/Cdl - W):** two semicircles. Only if you see two arcs. Don't force it.
- **Blocking / capacitive:** vertical tail, no Warburg. Your cell isn't diffusing, it's charging.

## Fit order
1. Read high-freq intercept → Rs. That's your electrolyte + contacts. Should be 1-5 ohm for liquid cells.
2. Diameter of main semicircle → Rct. Bigger = slower kinetics.
3. Low-freq tail slope ~1 → Warburg present. Slope ~vertical → capacitive, drop W.
4. If fit needs 7 elements to look pretty, it's overfit. 3-4 elements max for a first report.

## Red flags
- Rct negative or 10,000 ohm → wrong circuit or bad data range. Trim 100kHz-0.1Hz first.
- Two papers, same data, different Rs by 5x → one forgot cable inductance. Mention freq range in your methods.
- Smoothing the spectrum before fitting hides the second arc. Fit raw, plot smooth.

Hosted 1-click version with Randles/SEI/Warburg extraction: https://matflow.celaron.com
Free alternative to learn: impedance.py (Python), EC-Lab ZFit (if you have BioLogic).
