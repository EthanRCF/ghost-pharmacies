# Ghost Pharmacies

**When Bay Area pharmacies closed, people in cheaper homes lost their nearest pharmacy more often, even though more pharmacies closed in expensive areas.**

Project for the 8th Annual Datathon for Social Good (Advanced Track). We join Google Maps Places pharmacies to Zillow homes by distance to measure who lost walkable access, then train a closure-risk model and compare it with a chain-only baseline.

## Repository layout

```
data/        raw event files (not committed, never edited)
notebooks/   ghost_pharmacies.ipynb: the single notebook, raw data to results
outputs/     tables, figures and maps the notebook creates
```

## Run it in Google Colab (team default)

1. In Google Drive, create `MyDrive/ghost-pharmacies/data/` and put the raw files there (see `data/README.md`). Share the folder with the team.
2. In Colab: *File → Open notebook → GitHub*, paste this repository's URL, open `notebooks/ghost_pharmacies.ipynb`.
3. Run the Step 0 cells. They install folium, mount Drive, set the seed and check that every raw file and column is present.
4. To save your work back here: *File → Save a copy in GitHub*.

## Run it locally

Python 3.11 or newer.

```bash
python -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
# put the raw files in data/
jupyter lab notebooks/ghost_pharmacies.ipynb
```

## Reproduce every result

All randomness uses `SEED = 42`. From a clean checkout with the raw files in `data/`:

```bash
jupyter nbconvert --to notebook --execute --inplace notebooks/ghost_pharmacies.ipynb
```

The notebook must finish without errors from top to bottom. The held-out test IDs are written to `outputs/test_ids.csv` in Step 6 and only scored once, in Step 8.

## Data

| Dataset | Used for |
|---|---|
| Google Maps Places | Pharmacy list, open/closed label, nearby groceries, clinics, bus stops |
| Zillow Housing | Home locations, local rent level, walk score |
| Census (optional) | Population and income by tract |
