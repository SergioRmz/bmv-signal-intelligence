# Validation Rule IDs

## Contract Rules

- `AE-REQ-001`: `event_id` is required and must be a non-empty string.
- `AE-REQ-002`: `event_type` is required and must be a non-empty string.
- `AE-REQ-003`: `schema_version` is required and must identify the schema version.
- `AE-REQ-004`: `occurred_at` is required and must be an RFC3339 timestamp.
- `AE-REQ-005`: `source.name` is required and must be a non-empty string.
- `AE-REQ-006`: `source.category` must be one of `allowed`, `conditional`, or `prohibited`.
- `AE-REQ-007`: `asset.symbol` is required and must be a non-empty string.
- `AE-REQ-008`: `asset.market` is required and must be a non-empty string.
- `AE-REQ-009`: `payload` is required and must be an object.

## Policy Rules

- `SRC-001`: Source category must be documented in the allowed sources policy.
- `SRC-002`: Conditional sources must document usage constraints.
- `SRC-003`: Prohibited sources must not appear in valid samples.

## Review Rules

- `REV-001`: PR validation evidence must include commands executed and pass/fail result.
- `REV-002`: Each invalid sample must map to at least one rule ID.

## Watchlist Rules

- `WL-REQ-001`: Watchlist file must exist at `data/watchlists/asset-watchlist.json`.
- `WL-REQ-002`: Watchlist must include `watchlist_id`, `version`, `effective_date`, `purpose`, and `assets`.
- `WL-REQ-003`: Watchlist must contain exactly one active IPC entry.
- `WL-REQ-004`: IPC entry must use symbol `IPC` and display name `S&P/BMV IPC`.
- `WL-REQ-005`: IPC entry `asset_type` must be `index`.
- `WL-REQ-006`: IPC entry `currency` must be `MXN`.
- `WL-REQ-007`: IPC entry must include market metadata sufficient to identify BMV/Mexico context.
- `WL-REQ-008`: IPC entry must include traceability context.
- `WL-REQ-009`: Watchlist and samples must not include live prices, target prices, ratings, trading signals, recommendations, or performance forecasts.
- `WL-REQ-010`: Invalid watchlist samples must map to at least one rule ID in `docs/validation/sample-rule-mapping.md`.
