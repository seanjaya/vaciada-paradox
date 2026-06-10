# Vaciada Paradox

> Testing whether the tourism map and the depopulation map are really the same

## Overview
This project examines overtourism and demographic change across the European Union at the NUTS-2 regional level. It tests the popular claim that tourism intensity and population decline track each other geographically — whether the regions filling with tourists are the same ones emptying of locals. The analysis combines cross-country concentration metrics, a cross-EU correlation test, and a regional typology built from K-Means clustering with a rule-based outlier tier, using two harmonized Eurostat datasets.

## Methods
- **Gini coefficient and top-3 concentration ratio (CR-3)** for measuring how lopsided tourism is within each country (Gini restricted to countries with n ≥ 6 NUTS-2 regions for sample reliability)
- **K-Means clustering at k = 4** for the regional typology
- **Rule-based threshold split** on the hyper-tourism cluster to isolate the outlier tier
- **Temporal smoothing** (tourism intensity computed as a 2022–2024 mean to control for post-COVID volatility, particularly the 2023 "revenge tourism" spike)

## Data
- Eurostat's regional tourism table ([tour_occ_nin2](https://ec.europa.eu/eurostat/databrowser/view/tour_occ_nin2))
- Eurostat's regional demographic data ([demo_r_d2jan](https://ec.europa.eu/eurostat/databrowser/view/demo_r_d2jan))

## Reproduction
TBD — instructions will be added as setup solidifies.

## Published article
Coming soon — link will appear here when the piece is published on somewhere-else.org.
