# Australian copper data

Machine-readable Australian copper production and export statistics, quarterly
from March 1990. Companion to
<https://www.miningcapitalfunds.com.au/australian-copper-statistics>.

Compiled from the **Resources and Energy Quarterly** historical data workbook,
published by the Office of the Chief Economist, Australian Government
Department of Industry, Science and Resources, and licensed
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

Nothing here is modelled or forecast. The REQ publishes projections; none of
them appear in these files.

## Files

| File | Rows | What it holds |
|---|---|---|
| `australian-copper-quarterly.csv` | ~5,000 | Production, exports, value, prices and exploration, long format |
| `australian-copper.json` | — | The full series in one object |

### `australian-copper-quarterly.csv`

One fact per row: `quarter,series,category,subcategory,value,unit`

| series | category | subcategory | unit |
|---|---|---|---|
| `mine_production` | `state` / `national` / `residual` | name | kt |
| `mine_production` | `gross weight` | ore and concentrates | kt gross |
| `processed` | `smelter and refinery` | blister / refined | kt |
| `exports_quantity` | `Ores and concentrates` | destination or `Total` | kt gross |
| `exports_quantity` | `Refined` | destination or `Total` | kt |
| `exports_quantity` | `All forms` | `Copper content` | kt |
| `exports_value` | form | — | A$m |
| `price` | `LME cash` / `Australia` | — | US$/t or A$/t |
| `exploration` | `Copper` / all metals | — | A$m |

Quarters are calendar quarters, labelled `YYYY-Qn`. `2026-Q1` is January to
March 2026.

## Three things that will trip you up

**Two different tonnes.** Check the `unit` column before adding anything up.
Rows marked `kt` are contained copper metal. Rows marked `kt gross` are ores and
concentrates weighed as shipped, rock included. Adding a `kt gross` row to a
`kt` row produces a number that means nothing. The `All forms / Copper content`
row is the only export figure directly comparable with mine production.

**Two different currencies.** The `LME cash` price is US dollars a tonne, the
`Australia` price Australian dollars a tonne. Both are reproduced as published
rather than converted, so the distance between them is mostly the exchange rate.

**The Northern Territory is not a row.** The REQ breaks out New South Wales,
Queensland, Western Australia, South Australia and Tasmania, plus an Australian
total. Territory output sits inside the national figure without appearing in any
state. The `residual` category carries the difference. It mattered in the 1990s,
reaching 8.85 kt in a quarter; the last quarter in which it exceeded 0.5 kt was
2008-Q4, and since then it has been rounding. Victoria and the ACT produce no
copper and are correctly absent rather than missing.

## Coverage

Production is copper content of all minerals produced. There is no mine-level
detail: the REQ reports to state level, and no Australian state publishes copper
production mine by mine as open data. Where that detail does exist, for
Queensland coal, it is at <https://github.com/cwzah/qld-coal-data>.

Exploration expenditure begins in 1999-Q3, later than everything else, and is
private expenditure only.

Destinations do not sum to the export total. The REQ names only the major buyers
for each form and withholds some country detail as confidential. The gap is
genuine.

## Updates

Rebuilt after each quarterly REQ edition, roughly March, June, September and
December. File names do not change, so the raw URLs are stable.

## Attribution

Compiled by Clint Zahmel, Mining Capital Funds. Source data © Commonwealth of
Australia, used under CC BY 4.0. Conclusions drawn from this data are not
attributable to the department.
