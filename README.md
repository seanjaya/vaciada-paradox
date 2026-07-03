# The Vaciada Paradox

**Everyone assumes the tourism map and the depopulation map of Europe are the same map. They are not — and the word for the problem belongs to the wrong country.**

A data analysis of overtourism and depopulation across 277 European NUTS-2 regions. The headline finding: only **four** regions sit at the genuine overlap of intense tourism and population decline — three Greek island groups (South Aegean, Ionian Islands, Crete) and the Croatian Adriatic. None is in Spain, the country whose term *la España vaciada* ("the emptied Spain") gave the phenomenon its name.

## The finding

Across the continent, tourism intensity and population change are essentially uncorrelated (r = 0.05). The intuitive single "map" — crowded coasts, emptying interiors as two ends of one force — does not hold at the European scale. Where the two *do* coincide, they coincide in a small, hyper-specialised set of Mediterranean island and coastal economies. Spain's tourism (coastal, insular, highly concentrated) and its depopulation (interior, village-scale) happen in different places — and the true *vaciada* heartland is sub-regional, largely invisible at the NUTS-2 resolution this analysis uses.

## Data

All data is pulled live from [Eurostat](https://ec.europa.eu/eurostat) via the `eurostat` Python package — no data files are stored in this repo. Two source tables:

| Table | Description |
|-------|-------------|
| `tour_occ_nin2` | Nights spent at tourist accommodation establishments, by NUTS-2 region |
| `demo_r_d2jan` | Population on 1 January, by NUTS-2 region |

Tourism intensity is a 2022–2024 mean (to smooth post-pandemic volatility); population change is computed 2018–2024 over the boundary-stable region set (277 of 288 regions; 11 dropped for boundary or data-lag reasons, documented in the notebook).

> **Note on reproducibility:** Eurostat occasionally revises figures or restructures tables. Data was extracted in June 2026. Re-running the notebook fetches current data, which may differ slightly from the values reported in the article. To reproduce the exact published numbers, use the committed `analysis_df.csv` snapshot (if present).

## Method

1. Pull and clean both Eurostat tables to a common NUTS-2 region set.
2. Compute tourism intensity (nights per capita) and 2018–2024 population change.
3. K-means clustering (k = 4) on the two standardised features, followed by a deterministic Stage-2 rule that splits the hyper-tourism cluster by population sign — isolating the regions that are both heavily touristed and declining.
4. Robustness checks: 50-seed re-run confirming the four-region outlier tier is completely seed-invariant.

## Running it

```bash
pip install -r requirements.txt
jupyter notebook vaciada_paradox.ipynb
```

Then run all cells top to bottom. The notebook fetches its own data from Eurostat, so an internet connection is required on first run.

## Files

- `vaciada_paradox.ipynb` — the full analysis notebook
- `vaciada_paradox_article.html` — the public-facing article (self-contained, figures embedded)
- `fig1_scatter.png`, `fig2_clusters.png` — the two figures
- `requirements.txt` — Python dependencies
- `analysis_df.csv` — processed 277-region dataset (optional snapshot for exact reproducibility)

## Author

Part of the data-driven essay series at [somewhere-else.org](https://somewhere-else.org).
