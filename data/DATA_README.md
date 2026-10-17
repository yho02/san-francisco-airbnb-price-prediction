# Data provenance

All files are read locally from this folder; the notebook makes no network calls.

## Listings (Inside Airbnb, San Francisco, detailed `listings` files)
Official source: https://insideairbnb.com/get-the-data/ (Inside Airbnb archives older releases; access is by request).

The files below were obtained from a classmate's public mirror of the Inside Airbnb data
(`github.com/jamparque/airbnb-data`, `raw.githubusercontent.com/jamparque/airbnb-data/main/<file>`), downloaded 2026-10-13.
They were cross-checked against the user's own copies of Inside Airbnb's *summary* `listings.csv` files for the same four
snapshots (since deleted by the user): identical row counts, listing ids, prices, coordinates, room types, minimum nights
and availability for all four.

| File | Snapshot | Scrape date | Rows | SHA-256 |
|---|---|---|---|---|
| listings_dec24.csv | Dec 2024 | 2024-12-04 | 7,863 | 079eca9f73dabc02d5c4e0f85696ed750ac17561ee051c005bc8a0accc34737c |
| listings_mar25.csv | Mar 2025 | 2025-03-01/02 | 7,831 | de39238f894165b34b411de9e42447124ffc274df758f99c229c2370d02f953b |
| listings_jun25.csv | Jun 2025 | 2025-06-17 | 7,804 | aaeda1c510fe80542ffef0d4133380b180e6fac9cc7ece620174b51c2ce7eceb |
| listings_sep25.csv | Sep 2025 | 2025-09-01 | 7,780 | 7b824150f8a9cd5b0027ff8a480f9d10a75bc297e44c321238fff3f7b49eaee1 |

## Location data (from the same classmate repo)
| File | Content | SHA-256 |
|---|---|---|
| BART_Stations_2025.kmz | BART station coordinates | 8cc2bcc3509bf72529436f6794e89d6c73feec1d0abaa56d1fde27ce8a84bd69 |
| Muni_Stops_20251114.csv | SFMTA Muni stop coordinates (export dated 2025-11-14) | 24f155198d2a305a658e8258b6905093c132c0e0f3b27040e89be35ae07e7ca4 |
| sf_attractions.csv | Hand-compiled list of 60 attractions (class report says coordinates from Wikipedia). Encoded as Mac Roman, not UTF-8; read with `encoding="mac_roman"` | c3e15d99b540a65701596a4d2d41c9a38ac6ed38250ee161421c1af9e75aa688 |

## Files in this folder that are NOT used
`dec_25.csv`, `march_26.csv`, `june_26.csv`, `sep_26.csv` (detailed Inside Airbnb listings, Dec 2025 and 2026).
- `dec_25.csv`: the `price` column is empty on all 7,535 rows (also empty in the summary version), so it cannot be used for price modelling.
- 2026 files: the release adds `price_quote_*` columns and `price` equals `price_quote_price_per_night`, the average per-night cost of a quoted stay
  (future check-in date, usually the listing's minimum stay, weekly/monthly discounts applied). For the same listings the median change from Sep 2025
  to Mar 2026 is +26% with only 0.2% of prices unchanged (vs 26-31% unchanged between consecutive 2025 snapshots), so 2026 prices are not comparable
  with 2024-25 and are excluded. Whether the definition change explains the whole jump is likely but not proven.
