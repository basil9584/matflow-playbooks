# I built a 500k-line chemistry platform and I don't even like chemistry.

**This repo has almost no code. That's the point.**

It's a free survival kit for people drowning in battery Excel files, EIS spectra, and formulation spreadsheets — plus a live demo of the monster I built to escape that hell.

👉 **Try Matflow live here: https://matflow.celaron.com**

Matflow is a self-hostable R&D platform: drop in any messy lab file, get a governed dataset in minutes, run physics-validated predictions with uncertainty bars, export everything you own. Every number is labelled `MEASURED / COMPUTED / PREDICTED / EXTRACTED / HYPOTHESIS / DEMO` — no fake data presented as real.

Built by a GenAI guy, not a materials guy. 500k lines, ~3,195 backend tests, 5 verticals. I'm freezing the science and keeping the useful parts alive.

---

## Why this repo exists (and why it will rank)

Google "convert BioLogic mpt to capacity csv" or "fit EIS Nyquist to Randles circuit free" — you get papers, dead tools, or $2k software.

This repo gives you the actual templates + checklists + copy-paste LLM prompts I used, for free, no signup. If you want the 1-click version, that's Matflow 👆.

## Who this is for

- Battery test engineers with Neware / BioLogic / Arbin / Maccor exports that don't match
- Formulation nerds doing Hansen + mixture DOE in Excel hell
- Students / indie labs who can't afford Citrine, Schrödinger, or JMP
- Anyone who got burned by "AI chemistry" that hallucinates numbers

If that's not you, star and leave. No hard feelings.

## The 3 free playbooks (start here)

### 1. Battery cycle-life from a dirty cycler Excel
**Pain:** 3 cyclers, 3 formats, missing mass, no RUL, PI wants a plot Friday.
**Free stuff in this repo:**
- `templates/battery_cycles_template.csv` — clean 20-row example that actually imports
- `cheatsheets/battery-excel-cleaning-guide.md` — the 11-point QA checklist (units, mass normalization, cycle reconstruction)
- `prompts/llm-prompts-for-battery-reports.md` — prompt to turn your cleaned CSV into a weekly report draft
**1-click version in Matflow:** upload cycler file → auto-normalize → RUL with conformal intervals → degradation-mechanism analyzer (SEI √n vs cycling n^β vs lithium-inventory loss, picked by held-out RMSE) → reproducible export.
Try it: https://matflow.celaron.com → Data workspace → "use demo dataset"

Keywords for searchers: `battery cycle life prediction excel, neware btsda capacity csv, biologics mpt to csv, battery RUL python, cellpy alternative hosted`

### 2. EIS Nyquist → equivalent-circuit fit without $2k software
**Pain:** You have a Nyquist semicircle and need Rs, Rct, Warburg — now.
**Free stuff:**
- `templates/eis_sample.csv` — Z' / -Z'' sample that won't crash fitters
- `cheatsheets/eis-fitting-guide.md` — Randles vs SEI vs Warburg, when each lies to you
**1-click version:** Matflow extracts Randles/SEI/Warburg params from measured spectrum with plots you can defend.
Try it: https://matflow.celaron.com

Keywords: `fit EIS nyquist online free, randles circuit fitting python, EIS equivalent circuit Rs Rct`

### 3. Formulations: Hansen + D-optimal mixture that fits on one page
**Pain:** 120 solvents, 5 ingredients, constraints, PI says "just DOE it".
**Free stuff:**
- `templates/formulation_runs_template.csv` — ingredient fractions + response template with constraint check
- `cheatsheets/hansen-solubility-guide.md` — fitted Hansen model explained like you're 5 (RidgeCV on RDKit fragments, LOO-CV MAE, applicability flag)
- `prompts/llm-prompts-for-formulations.md`
**1-click version:** fitted Hansen predictor with intervals + D-optimal mixture design (coordinate exchange, Scheffé linear/quadratic, D-efficiency report).
Try it: https://matflow.celaron.com

Keywords: `hansen solubility parameters from smiles, D-optimal mixture design excel, formulation DOE free tool`

---

## Templates in this repo (all free, MIT)

| File | What it is | Use it for |
|---|---|---|
| `templates/battery_cycles_template.csv` | 20-row clean cycle example | Test any importer before your real file |
| `templates/eis_sample.csv` | Clean Z'/Z'' spectrum | Test any EIS fitter |
| `templates/formulation_runs_template.csv` | Mixture runs + constraints | Test any DOE tool |
| `templates/cycler_qa_checklist.md` | 11-point import QA | Stop silent unit errors |
| `cheatsheets/battery-excel-cleaning-guide.md` | Step-by-step cleaning | Neware/BioLogic/Arbin mess |
| `cheatsheets/eis-fitting-guide.md` | Circuit picker + pitfalls | Defendable fits |
| `cheatsheets/hansen-solubility-guide.md` | Hansen in plain English | Solvent screening |
| `prompts/llm-prompts-for-battery-reports.md` | Copy-paste prompts | Weekly report drafts |
| `prompts/llm-prompts-for-formulations.md` | Copy-paste prompts | Run-sheet + next batch |
| `examples/before-after.md` | Messy in → clean out | See what "governed" means |

No pip install. No Docker. Just download and open in Excel/Sheets/Python.

## Matflow vs the usual suspects (honest version)

| Tool | Good at | Pain |
|---|---|---|
| cellpy (free, MIT) | Reads many cycler formats, great lib | You code everything, no hosted review/export |
| BioLogic EC-Lab / Neware BTSDA | Native analysis for their box | Single-vendor, cross-brand batch = pain |
| JMP / Citrine / MaterialsZone | Real stats, real platform | Price, procurement, overkill for 1 lab |
| **Matflow (this → https://matflow.celaron.com)** | Cross-vendor ingest + review + uncertainty + export you own, self-hostable | Beta. Student-built. No enterprise support. DEMO data always labelled DEMO. |

If native software already does your job well, stay there. If you're stitching 3 exports in Excel every Friday, try the demo dataset.

## Evidence classes (why I won't hallucinate your thesis)

Every number in Matflow carries one:
`MEASURED` = from your instrument file, `COMPUTED` = deterministic calc, `PREDICTED` = model + interval, `EXTRACTED` = LLM/doc parse needing review, `HYPOTHESIS` = guess, `DEMO` = synthetic sample.

Synthetic is always labelled DEMO. Audit log is hash-chained. RO-Crate + OPTIMADE export so you can leave anytime.

## Pricing (to pay the server, not to yacht)

Matflow live pricing: Starter $99 / Pro $349 / Enterprise from $999/mo, credit packs $8–$110 for real compute. Free tier: 5 datasets, 2 campaigns, 10 copilot msgs/mo, watermarked dossiers. Academic `.edu/.ac` auto-approved for free taste.

This GitHub repo stays free forever. Templates are MIT. Take them even if you never click Matflow.

## FAQ (from real DMs)

**Is this another AI wrapper that fakes science?** No. If the engine isn't installed it says DEMO and charges $0. Real QM/MD/docking/FEP runs are metered and debited from credits. No fake as real.
**Do I need to install anything?** For templates: no. For Matflow: browser only, or self-host with Docker.
**Can I self-host?** Yes. Docker Compose + Caddy + Postgres. Your files, your box.
**I have a weird file. Will it work?** Maybe not. Upload the sample first, check `templates/cycler_qa_checklist.md`. Unsupported = rejected before charge, with reason.
**Are you really not a materials guy?** Correct. I'm GenAI/LLMs. That's why I built boring ingest + review + export instead of pretending to be a professor.

## Get 3 months free Pro (labs only)

I'm giving 5 indie/academic labs free Pro for 3 months if you:
1. Try the demo dataset at https://matflow.celaron.com
2. Run 1 real file (your own, you own rights)
3. Post your before/after + what broke (issue in this repo or email)

No sales call. Async only. During exams I reply slow — jobs queue, data stays.

Open an issue titled `LAB-TRY: <your lab>` with: instrument/file type, rows, what you want out. I'll enable you.

---

Built for fun with free LLM credits and a Contabo box. Star ⭐ if a template saved you 30 minutes — that's the whole GTM budget.
