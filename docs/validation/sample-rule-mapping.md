# Sample Rule Mapping

## Invalid Samples

| Sample | Violated Rule IDs | Rationale |
|--------|-------------------|-----------|
| `data/samples/asset-events/invalid/asset-event-invalid-01-missing-required.json` | `AE-REQ-001` | Missing required `event_id`. |
| `data/samples/asset-events/invalid/asset-event-invalid-02-bad-source-category.json` | `AE-REQ-006`, `SRC-001` | `source.category` is not one of the accepted policy categories. |
| `data/samples/asset-events/invalid/asset-event-invalid-03-invalid-timestamp.json` | `AE-REQ-004` | `occurred_at` is not an RFC3339 timestamp. |
| `data/samples/watchlists/invalid/asset-watchlist-invalid-missing-required.json` | `WL-REQ-002` | Missing required `effective_date`. |
| `data/samples/watchlists/invalid/asset-watchlist-invalid-wrong-asset-type.json` | `WL-REQ-003`, `WL-REQ-005` | A primary monitoring target is incorrectly typed as an index and the sample lacks the required active equity target count. |
| `data/samples/watchlists/invalid/asset-watchlist-invalid-advisory-content.json` | `WL-REQ-009` | Contains prohibited advisory language. |
