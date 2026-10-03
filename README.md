# Open Food Facts derived data (ODbL)

This repository contains the part of a fitness app's food catalog that was **derived from [Open Food Facts](https://world.openfoodfacts.org)**,
published under the same licence, as the Open Database License (ODbL) requires for derived databases.

- **File:** [`food_items_openfoodfacts.csv`](food_items_openfoodfacts.csv) — one row per product (see `export-info.json` for the row count and the date of the export).
- **Columns:** `barcode`, `name`, `name_en`, `brand`, and per-100 g (or per-100 ml when `serving_unit` is `ml`) `calories` (kcal), `proteins`, `carbs`, `fats` (g), `serving_size`, `serving_unit`, plus the optional `alt_serving_qty` (one serving) and `alt_package_qty` (whole package) in the same unit.

## Source and licence

> Contains information from Open Food Facts, which is made available here under the Open Database License (ODbL). © Open Food Facts contributors.

- Database: Open Food Facts — <https://world.openfoodfacts.org>, licence **ODbL 1.0** — <https://opendatacommons.org/licenses/odbl/1-0/>
- Individual contents of the database: **DbCL 1.0** — <https://opendatacommons.org/licenses/dbcl/1-0/>
- This derived database is made available under **ODbL 1.0** as well: you may share, create works from and adapt it, as long as you attribute Open Food Facts, keep this notice, and offer any database you derive from it under the same licence.

## What was changed from the original

- Only products tagged as sold in Romania (`countries_tags` contains `en:romania`), most-scanned first, plus products that users of the app looked up or scanned later (fetched from the Open Food Facts API at runtime).
- Only products with a valid barcode (8–14 digits), a name, and energy/macronutrients that are in a plausible range and consistent with each other; names in non-Latin alphabets were left out.
- Values were rounded to one decimal; the first listed brand was kept; `kJ` was converted to `kcal` where `kcal` was missing.
- **Not included:** product images (licensed separately by Open Food Facts) and any data that did not come from Open Food Facts (the app's own curated foods are not part of this repository).

## Updates

The file is re-exported from the app's catalog from time to time; `export-info.json` records the date and the number of rows of the current version.

## Issues

For corrections to the product data itself, please contribute to Open Food Facts directly (<https://world.openfoodfacts.org>). For problems with this export, open an issue in this repository.
