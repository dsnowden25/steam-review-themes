# Why Do Gamers Game? Themes in Steam Reviews, 2014–2026

CS6140 Machine Learning mini project — Daymian Snowden, Khoury College, Northeastern University.

This project asks which features make a PC game well or poorly received, using English Steam reviews written from 2014 to 2026. It finds the themes players write about, measures how each theme relates to positive or negative recommendations, and tracks how those relationships change over time. All results are associational, not causal.

## Research questions

- **RQ1:** Which measurable game features can be extracted from public Steam data?
- **RQ2:** What themes do players express in reviews, and how do they relate to game features?
- **RQ3:** Which themes are associated with positive vs. negative reviews, and how has that changed from 2014 to 2026?

## Pipeline

| Step | File | What it does |
|---|---|---|
| 1 | `collect.py` | Pulls review text and game metadata from Steam and SteamSpy into `data/raw/` |
| 2 | `clean.py` | Filters, samples by release year and popularity tier, builds features, writes `data/processed/` |
| 3 | `analyze.py` | Theme model (GMM/EM, k-means baseline), L2 logistic regression, Beta–Bernoulli rankings, figures |

## Data sources

- Steam reviews: `store.steampowered.com/appreviews/{appid}` (public, no key)
- Game metadata: Steam store `appdetails`
- User tags and owner estimates: SteamSpy

Raw and processed data are not committed. Run `collect.py` to rebuild them.

## Setup (Windows, PowerShell)

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

## Run

```powershell
python collect.py
python clean.py
python analyze.py
```

## Layout

```
collect.py
clean.py
analyze.py
requirements.txt
data/
  raw/          # API pulls (gitignored)
  processed/    # model-ready tables (gitignored)
figures/
mini project proposal.pdf
```
