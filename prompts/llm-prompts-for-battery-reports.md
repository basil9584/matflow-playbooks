# Copy-paste LLM prompts for battery reports

Paste your cleaned CSV summary (NOT raw 10k rows). Models choke on huge tables. Give aggregates + the plot.

## Weekly report draft
```
I have battery cycling data: [N] cycles, [chemistry], [voltage window], [temperature].
Initial discharge [X] mAh/g, latest [Y] mAh/g, retention [Z]%.
Excluded cycles: [list + reason].
Write a 5-bullet weekly update: what happened, degradation rate per 100 cycles, likely mechanism (SEI vs cycling), next 2 checks. Flag uncertainty. No hype.
```

## Mechanism check
```
Capacity vs cycle: [paste 10-15 points cycle,capacity].
Does this look like sqrt(n) SEI-dominated or linear-then-cliff? Give held-out reasoning, not just fit R². List 2 confounders (temperature, mass error).
```

## PI-ready methods paragraph
```
Instrument: [Neware/BioLogic], file: [name], mass active [g], current [mA], voltage window, temperature.
Write a 4-sentence methods paragraph I can paste into a report, with exclusions.
```

Want it automatic with intervals + export? https://matflow.celaron.com
