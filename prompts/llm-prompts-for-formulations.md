# Copy-paste LLM prompts for formulations

## Run-sheet from constraints
```
Ingredients: A [range], B [range], C [range], sum=1.0. Constraints: [e.g. C<=0.2].
Propose 8 D-optimal-like runs + 2 center repeats for a Scheffé quadratic. Table: run, A, B, C, temp, mixing. No explanation fluff.
```

## Next batch picker
```
Past runs:
[paste run,A,B,C,response]
Propose next 3 runs to reduce uncertainty where response changes fastest. Give reason per run in 1 line.
```

## Hansen screen
```
Target polymer dD/dP/dH: [values], R0: [value].
Candidates: [SMILES or names + dD/dP/dH].
Rank by Ra and RED, flag outside applicability domain. Table only.
```

Automated version with D-efficiency report: https://matflow.celaron.com
