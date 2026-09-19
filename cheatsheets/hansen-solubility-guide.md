# Hansen solubility in plain English

Hansen says "like dissolves like" with 3 numbers: dispersion (dD), polar (dP), hydrogen-bonding (dH).

## How to use the template
`../templates/formulation_runs_template.csv` has fractions that sum to 1.0. Check: fraction_A + B + C = 1.00 every row or your DOE software will silently renormalize and lie.

## Fitted model (what Matflow does)
RidgeCV on RDKit fragment features, ~120 literature solvents, leave-one-out CV MAE reported, split-conformal intervals, applicability-domain flag. Translation: it tells you when you're outside what it knows.

## Screening rule of thumb
Distance Ra² = 4*(dD1-dD2)² + (dP1-dP2)² + (dH1-dH2)². Smaller Ra = more likely miscible. RED = Ra / R0. RED < 1 = good, >1 = risky. Don't optimize to 2 decimals — your raw materials vary more than that.

## D-optimal mixture in one paragraph
You have constraints (A 0.5-0.7, B 0.2-0.4, C 0.1-0.2). Random points waste runs. D-optimal picks points that maximize information for a Scheffé linear/quadratic model via coordinate exchange, then reports D-efficiency. Run the suggested 8, add 2 center repeats, then decide.

Live version: https://matflow.celaron.com
