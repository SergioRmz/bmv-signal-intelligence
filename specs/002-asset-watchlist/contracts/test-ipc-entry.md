# Contract Test Scenario: Canonical IPC Entry

## Purpose

Verify that the canonical watchlist artifact satisfies the IPC-only contract before any future ingestion feature consumes it.

## Scenario

1. Open `data/watchlists/asset-watchlist.json`.
2. Confirm the top-level fields `watchlist_id`, `version`, `effective_date`, `purpose`, and `assets` exist.
3. Confirm `assets` contains exactly one entry.
4. Confirm the entry has `active: true`.
5. Confirm the entry uses symbol `IPC` and display name `S&P/BMV IPC`.
6. Confirm the entry uses asset type `index` and currency `MXN`.
7. Confirm market metadata identifies BMV and Mexico context.
8. Confirm traceability includes `source_reference` and `review_rationale`.
9. Confirm no live prices, target prices, ratings, trading signals, recommendations, portfolio guidance, or performance forecasts appear.

## Expected Result

The canonical watchlist passes local validation with:

```bash
scripts/validation/check-asset-watchlist.sh
```
