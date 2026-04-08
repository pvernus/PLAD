# PLAD ADM-2 Panel

Match political leaders' birthplaces and ethnicities (PLAD v7.0) to ADM-2 subnational units (GADM 4.10) to produce a balanced panel and cross-section of leader affiliation indicators, 2000–2022.

## Data Sources

| Dataset | Version | Description |
|---------|---------|-------------|
| [PLAD](https://www.brettcarter.org/plad) | v7.0 (April 2024) | Birthplaces and ethnicities of effective leaders in 177 countries, 1989–2023 |
| [GADM](https://gadm.org) | 4.10 (cleaned) | ADM-2 subnational boundaries (`gadm_410_adm2_clean.gpkg`) |
| [GeoEPR](https://icr.ethz.ch/data/epr/geoepr/) | 2023 | Settlement patterns of politically relevant ethnic groups |

## Output Datasets

| File | Description |
|------|-------------|
| `output/plad_adm2_panel.rds` | Balanced ADM-2 × year panel, 2000–2022 |
| `output/plad_adm2_crosssection.rds` | Balanced ADM-2 cross-section, 2000–2022 summary |

## Scripts

### `script/plad_panel.qmd` — Panel dataset (time-varying)

| Variable | Definition |
|----------|------------|
| `birthplace_match` | 1 if ADM-2 unit contains the current leader's birthplace in year t |
| `ethnicity_match` | 1 if ADM-2 unit falls within the GeoEPR settlement of the current leader's ethnicity in year t |

### `script/plad_crosssection.qmd` — Cross-section dataset (time-invariant)

| Variable | Definition |
|----------|------------|
| `ever_birthplace` | 1 if ADM-2 unit was ever a leader's birthplace, 2000–2022 |
| `always_birthplace` | 1 if ADM-2 unit was a leader's birthplace in every year, 2000–2022 |
| `pct_birthplace` | Share of years 2000–2022 in which ADM-2 unit was a leader's birthplace |

## How to Run

```bash
quarto render script/plad_panel.qmd
quarto render script/plad_crosssection.qmd  # requires panel output
```

## Environment

| Software | Version |
|----------|---------|
| R | 4.5.2 |
| sf | 1.1.0 |
| terra | 1.8.93 |
| tidyverse | 2.0.0 |

## License

MIT
