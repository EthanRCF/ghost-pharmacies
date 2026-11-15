# data/

Put the raw event files here, exactly as downloaded. **Never edit them.** All cleaning happens in the notebook.

Nothing in this folder is committed except this README (see `.gitignore`).

Expected files (rename the paths at the top of the notebook if yours differ):

| File | Source dataset |
|---|---|
| `google_maps.csv` | Google Maps Places (~500 MB) |
| `Zillow_part1.csv`, `zillow_part2.csv`, `zillow_part3.csv` | Zillow Housing, full file in 3 parts (~7.4 GB total) |
| `census_tracts.csv` | Optional: Census population and income by tract |

On Colab, put the same files in a Google Drive folder instead and set `DRIVE_DATA_DIR` in the setup cell.
