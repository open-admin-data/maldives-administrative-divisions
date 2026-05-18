# Methodology

## Data Sources

This dataset is compiled from multiple open sources:

- **OCHA COD-AB Maldives** (CC BY-IGO) — 21 atolls + 1,556 islands with administrative P-codes and centroid coordinates from the Common Operational Dataset
- **Maldives Land and Survey Authority IslandList** — Dhivehi (Thaana script) names for islands, atoll assignments, and island categories
- **Protected Areas XLSX** — Dhivehi names for all 21 administrative atolls
- **Wikidata** (CC0) — Supplementary Dhivehi labels and cross-reference

## Processing

1. Atoll and island records from OCHA COD-AB (mdv_admin_boundaries.xlsx) with P-codes and centroids
2. Dhivehi names merged from IslandList CSV (72% coverage) and Wikidata (supplementary)
3. Atoll Dhivehi names from Protected Areas XLSX + Wikidata (100% coverage)
4. Multi-format export: JSON, NDJSON, CSV
5. Hierarchy folder structure with READMEs generated via EJS templates

## Important Notes

- The Maldives has **no postal code system** in common use (Maldives Post operates 5-digit codes but they are not widely adopted)
- Includes all islands (inhabited, uninhabited, resort) from the OCHA dataset — 1,556 total
- Dhivehi names use Thaana script (RTL) — ensure proper Unicode rendering
- Island names in English are romanized Dhivehi; no separate English translations exist

## Accuracy

- Coordinates from OCHA COD-AB centroid computation — 100% coverage at all levels
- Dhivehi (Thaana) names: 100% for atolls, 72% for islands
- P-codes from OCHA standard (e.g., MV001 = Haa Alif, MV001001 = Thuraakunu)
- Build script is idempotent: same input always produces same output