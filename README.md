# Maldives Administrative Divisions / ދިވެހިރާއްޖެ

Open dataset of the Maldives' administrative hierarchy — 21 administrative atolls and 1,556 islands. This repository provides structured, bilingual (Dhivehi/Thaana + English) reference data with geographic coordinates at every level. Designed for developers, researchers, government agencies, and AI agents.

Licensed under CC-BY-4.0. Browse the hierarchy through GitHub's folder navigation, download aggregate files in JSON/CSV/NDJSON, or integrate directly via raw URLs.

## Overview

| Item | Details |
|------|---------|
| Atoll | 21 |
| Island | 1,556 |
| Coordinates | ✅ Included (all levels) |
| Formats | JSON, NDJSON, CSV |
| License | CC-BY-4.0 |
| Last Updated | 2026-08-20 |
| Website | [openadmindata.org/mv](https://openadmindata.org/mv/) |
| API | [openadmindata.org/api/mv](https://openadmindata.org/api/mv/) |
| Flag | [PNG](https://onlygames.me/flags-png/mv/) · [SVG](https://onlygames.me/flags-svg/mv/) · [PDF](https://onlygames.me/flags-pdf/mv/) |
| National Anthem | [🎵 Listen & Download Maldives National Anthem MP3](https://onlygames.me/national-anthems/mv/) |

## Browse by Atoll

| # | Atoll | Islands | Link |
|---|----|----|------|
| 1 | އަރިއަތޮޅު އުތުރުބުރި (Alifu Alifu) | 46 | [Browse](divisions/alifu-alifu-mv008/) |
| 2 | އަރިއަތޮޅު ދެކުނުބުރި (Alifu Dhaalu) | 81 | [Browse](divisions/alifu-dhaalu-mv020/) |
| 3 | މާޅޮސްމަޑުލު ދެކުނުބުރި (Baa) | 118 | [Browse](divisions/baa-mv007/) |
| 4 | ނިލަންދެއަތޮޅު ދެކުނުބުރި (Dhaalu) | 69 | [Browse](divisions/dhaalu-mv012/) |
| 5 | ނިލަންދެއަތޮޅު އުތުރުބުރި (Faafu) | 33 | [Browse](divisions/faafu-mv011/) |
| 6 | ހުވަދު އަތޮޅު އުތުރުބުރި (Gaafu Alifu) | 104 | [Browse](divisions/gaafu-alifu-mv016/) |
| 7 | ހުވަދު އަތޮޅު ދެކުނުބުރި (Gaafu Dhaalu) | 170 | [Browse](divisions/gaafu-dhaalu-mv017/) |
| 8 | ފުވައްމުލައް (Gnaviyani) | 1 | [Browse](divisions/gnaviyani-mv018/) |
| 9 | ތިލަދުންމަތީ އުތުރުބުރި (Haa Alifu) | 43 | [Browse](divisions/haa-alifu-mv001/) |
| 10 | ތިލަދުންމަތީ ދެކުނުބުރީ (Haa Dhaalu) | 36 | [Browse](divisions/haa-dhaalu-mv002/) |
| 11 | މާލެއަތޮޅު (Kaafu) | 195 | [Browse](divisions/kaafu-mv009/) |
| 12 | ހައްދުންމަތި (Laamu) | 90 | [Browse](divisions/laamu-mv015/) |
| 13 | ފާދިއްޕޮޅު (Lhaviyani) | 81 | [Browse](divisions/lhaviyani-mv005/) |
| 14 | މާލެ ސިޓީ (Male) | 3 | [Browse](divisions/male-mv021/) |
| 15 | މުލަކަތޮޅު (Meemu) | 67 | [Browse](divisions/meemu-mv013/) |
| 16 | މިލަދުންމަޑުލު ދެކުނުބުރި (Noonu) | 80 | [Browse](divisions/noonu-mv004/) |
| 17 | މާޅޮސްމަޑުލު އުތުރުބުރި (Raa) | 117 | [Browse](divisions/raa-mv006/) |
| 18 | އައްޑުއަތޮޅު (Seenu) | 40 | [Browse](divisions/seenu-mv019/) |
| 19 | މިލަދުންމަޑުލު އުތުރުބުރި (Shaviyani) | 59 | [Browse](divisions/shaviyani-mv003/) |
| 20 | ކޮޅުމަޑުލު (Thaa) | 75 | [Browse](divisions/thaa-mv014/) |
| 21 | ފެލިދުއަތޮޅު (Vaavu) | 48 | [Browse](divisions/vaavu-mv010/) |

## Data Files

| File | Format | Description |
|------|--------|-------------|
| [all-atoll.json](data/all-atoll.json) | JSON | All 21 atoll records |
| [all-island.json](data/all-island.json) | JSON | All 1,556 island records |
| [all-flat.json](data/all-flat.json) | JSON | Levels 1-1 flat array |
| [all-flat.ndjson](data/all-flat.ndjson) | NDJSON | Streaming format |
| [all-flat.csv](data/all-flat.csv) | CSV | Spreadsheet format |
| [hierarchy.json](data/hierarchy.json) | JSON | Nested tree |
| [schema.json](data/schema.json) | JSON Schema | Data schema |

## Quick Start

### Python

```python
import json

with open("data/all-atoll.json", "r", encoding="utf-8") as f:
    data = json.load(f)

for r in data:
    print(f"{r['name']['local']} ({r['name']['en']}) — {r['children_count']['island']} islands")
```

### JavaScript

```javascript
import { readFileSync } from "fs";

const data = JSON.parse(readFileSync("data/all-atoll.json", "utf-8"));
console.log(`Total: ${data.length} atolls`);
```

## Schema

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier |
| `level` | integer | 1=atoll, 2=island |
| `level_name` | object | Level label (local + English) |
| `name.local` | string | Name in local script |
| `name.en` | string | English name |
| `name.slug` | string | URL-safe slug |
| `parent` | object/null | Parent division reference |
| `ancestors` | array | Full ancestor chain |
| `children_count` | object | Count of children per level |
| `zip_codes` | array | Postal codes (where available) |
| `geo.lat` | string | Latitude (WGS84) |
| `geo.lon` | string | Longitude (WGS84) |

Full schema: [data/schema.json](data/schema.json)

## Hierarchy Browse

```
divisions/{atoll-slug}/
```

Islands are listed inline in each atoll's README.

## AI Integration

- [llms.txt](docs/llms.txt) — Quick reference for AI agents
- [llms-full.txt](docs/llms-full.txt) — Summary with per-atoll links
- [Per-atoll data](docs/llms-full/) — Full data by atoll

## Citation

```
Maldives Administrative Divisions Dataset (CC-BY-4.0)
URL: https://github.com/open-admin-data/maldives-administrative-divisions
```

See [CITATION.cff](CITATION.cff) for machine-readable citation.

## License

- **Data**: [CC-BY-4.0](LICENSE)

## Related

- [Open Admin Data](https://openadmindata.org) — Browse, search and explore administrative divisions for every country
- [open-admin-data](https://github.com/open-admin-data) — GitHub organization with all country repos
- [ListBase](https://www.listbase.org) — Structured reference data for every country
