# US Local Service Cost Benchmarks

City-level home service planning estimates, local price research and household affordability context from **[Cost in USA](https://costinusa.com/)**. This repository brings the published figures into reusable CSV and JSON files, with a homeowner handbook that explains how to compare the work behind a quote.

**[Read the handbook](docs/README.md)** · **[Browse city cost guides](https://costinusa.com/cost-guides/)** · **[Explore the affordability index](https://costinusa.com/affordability-index/)**

Maintained by Cost in USA, operated by Open Skill LLC. Figures are in USD and retain their original scope and billing unit. They are planning ranges, not binding contractor quotes or measured citywide averages.

## Current coverage

Cities covered | Published city/service guides | Service categories | States and DC covered
--- | --- | --- | ---
112 | 112 | 1 | 38

**Latest included guide publication:** 2026-11-09. Coverage reflects the currently published, indexable guides; it is a publication sample, not a census of providers or a nationally representative price survey.

### Browse by service

- [House Cleaning cost planning](docs/services/house-cleaning.md) — 112 published city guides.

## A few city examples

City and service guide | Service scope | Planning range (USD) | Billing unit
--- | --- | --- | ---
[Phoenix, AZ — House Cleaning](https://costinusa.com/house-cleaning/phoenix-az/) | 1-bed, 1-bath standard visit | $120–$175 | per visit
[Los Angeles, CA — House Cleaning](https://costinusa.com/house-cleaning/los-angeles-ca/) | 1-bed, 1-bath standard visit | $125–$190 | per visit
[Dallas, TX — House Cleaning](https://costinusa.com/house-cleaning/dallas-tx/) | 1-bed, 1-bath standard visit | $110–$180 | per visit
[Chicago, IL — House Cleaning](https://costinusa.com/house-cleaning/chicago-il/) | 1-bed, 1-bath standard visit | $110–$180 | per visit
[San Diego, CA — House Cleaning](https://costinusa.com/house-cleaning/san-diego-ca/) | 1-bed, 1-bath standard visit | $125–$195 | per visit
[Seattle, WA — House Cleaning](https://costinusa.com/house-cleaning/seattle-wa/) | 1-bed, 1-bath standard visit | $130–$210 | per visit
[Miami, FL — House Cleaning](https://costinusa.com/house-cleaning/miami-fl/) | 1-bed, 1-bath standard visit | $110–$175 | per visit
[Denver, CO — House Cleaning](https://costinusa.com/house-cleaning/denver-co/) | 1-bed, 1-bath standard visit | $120–$200 | per visit


These rows are selected examples, not a cheapest-to-most-expensive ranking. Open the linked guide to check home size, condition, frequency, included work and local price references before comparing budgets. [All state chapters](docs/README.md#state-chapters) provide the wider directory.

## Files and downloads

Resource | Contents | Start here
--- | --- | ---
Homeowner handbook | Practical guidance on scope, units, written quotes and recurring costs | [Read](docs/homeowner-maintenance-handbook.md)
City service prices (CSV) | One row per city, service and price scope, with low/high values, unit, date and guide URL | [Download](data/city-service-prices.csv)
City service prices (JSON) | The same city/service snapshots, plus available Census context | [Download](data/city-service-prices.json)
Affordability index (CSV) | Comparable service cost midpoints and separate income/rent shares | [Download](data/affordability-index.csv)
Data dictionary | Field definitions, units and missing-data notes | [Read](data/data-dictionary.md)
State chapters | City guide links and planning ranges grouped by service | [Browse](docs/README.md#state-chapters)
Research methods | Snapshot selection, calculations and limitations | [Read](docs/methodology.md)

## How the figures are researched

1. **Start with a defined service scope.** A one-bedroom standard clean, a localized roof repair and a full roof replacement are separate purchases. We do not combine them into a single service average.
2. **Research published prices and local context.** The source city guides carry provider references, research notes and distinctions between published examples and estimated planning ranges. A single provider example does not establish the price for an entire city.
3. **Review before publication.** Reports go through automated content and consistency checks and the site’s editorial publication rules. This repository exports the current indexable publication snapshots rather than drafts or private project requests.
4. **Keep provenance attached.** Each price row includes its billing unit, publication date and original city guide URL so readers can inspect the assumptions and sources.

[Editorial and review guidelines](https://costinusa.com/review-policy/) · [About the research](https://costinusa.com/about/) · [Affiliate disclosure](https://costinusa.com/disclosure/)

## Reading the affordability index

For a comparable service scope, the cost midpoint is `(low + high) / 2`. The index reports two separate ratios:

- **Income share:** one service purchase ÷ median annual household income × 100.
- **Rent share:** one service purchase ÷ median monthly gross rent × 100.

A $200 visit represents 0.25% of an $80,000 annual household income, or 10% of a $2,000 monthly rent. These are different denominators; neither ratio represents a household’s actual annual service spending. Recurring visits require a separate frequency assumption.

Available U.S. Census ACS survey periods, margins of error and annotations accompany the JSON context. Records with missing or incompatible denominators are excluded from the relevant rankings. Close differences can fall within survey uncertainty. Project prices may include materials as well as labor.

## Using the data

The CSV files open in spreadsheets. For a quick JSON lookup with Python, no extra packages are required:

```python
import json
from pathlib import Path

records = json.loads(Path("data/city-service-prices.json").read_text(encoding="utf-8"))
for record in records[:5]:
    print(record["city"], record["state"], record["service"], record["guide_url"])
```

Filter by `service` and price scope before comparing values. Preserve `unit`, `currency`, `basis` and `published_at` when redistributing CSV rows. Missing Census values mean unavailable; they do not mean zero.

## Updates and corrections

Exports follow publication changes on Cost in USA. The data version below identifies this snapshot; Git history records changes. There is no fixed refresh schedule or live contractor availability feed.

For a correction, use this repository’s **Issues** tab or email [coco@costinusa.com](mailto:coco@costinusa.com). Include the city, service, row or guide URL, relevant scope/unit, source URL and the date you checked it. Please keep private household details and contact information out of public issues. Provider or contributor affiliation should be disclosed with a submission.

## Citation and reuse

Attribute **Cost in USA**, link to the original city guide, include its publication date and indicate any changes you make. Keep the distinction between a published provider example and a derived planning estimate. For an index comparison, also identify the service scope, Census survey period and snapshot version.

Original documentation and derived planning estimates use [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Third-party quotations and source material retain their own terms. Place names originate from [GeoNames](https://www.geonames.org/) under CC BY 4.0; Census references identify their [source datasets](https://www.census.gov/data/developers.html). See [DATA-LICENSE.md](DATA-LICENSE.md) for details.

## Handbook publishing

GitHub Pages renders the handbook from the default branch’s `docs/` directory. For GitBook site sync, keep **Project directory** at the repository root; `gitbook-docs.yaml` maps the handbook to `docs/`. The first sync direction is **GitHub → GitBook**. Once linked, preserve the space’s stable key when changing site settings. Existing GitBook mappings are retained by the exporter.

[GitBook setup documentation](https://gitbook.com/docs/docs-as-code/git-sync/enabling-github-sync) · [Snapshot notes](docs/updates.md)

Data version 695889a36f68
