# Asset Watchlist Validation

## Purpose

Define local validation rules and review evidence for the IPC-only asset watchlist.

## Local Commands

Run from the repository root:

```bash
scripts/validation/check-asset-watchlist.sh
```

The command validates the canonical watchlist, valid samples, invalid sample mappings, and non-advisory scope guardrails without network access or deployed services.

## Rule IDs

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

## IPC Baseline Manual Review

Reviewers must confirm `data/watchlists/asset-watchlist.json` satisfies these baseline checks:

- The file exists and is valid JSON.
- `watchlist_id` is `asset-watchlist`.
- `version`, `effective_date`, and `purpose` are present and non-empty.
- `assets` contains exactly one active entry.
- The active entry uses symbol `IPC` and display name `S&P/BMV IPC`.
- The active entry uses asset type `index` and currency `MXN`.
- Market metadata identifies BMV/Mexico context.
- Traceability includes source reference and non-advisory review rationale.
- Notes clarify that IPC observations are index points when needed.

## Sample Expectations

- Valid samples under `data/samples/watchlists/valid/` must pass the same IPC-only structural checks as the canonical watchlist.
- Invalid samples under `data/samples/watchlists/invalid/` must remain parseable JSON but fail at least one `WL-REQ-*` rule.
- Every invalid watchlist sample must be listed in `docs/validation/sample-rule-mapping.md` with at least one violated rule ID.

## Non-Advisory Content Scan

The local validation script rejects watchlist and sample JSON when it finds prohibited terms or fields associated with live prices, target prices, ratings, rankings, trading signals, recommendations, portfolio allocation, or performance forecasts.

Reviewers must also confirm the artifacts do not imply that IPC inclusion is a buy, sell, hold, allocation, ranking, or forecasting decision. IPC inclusion only defines future monitoring scope.

## Traceability Review

Each IPC watchlist entry must include traceability context with:

- A source reference that identifies the public index reference category or documentation basis used for review.
- A review rationale that explains why IPC is in scope without making performance claims.
- Optional reviewer and review date metadata when available.

Traceability must be sufficient for maintainers and future ingestion service owners to understand the source context without fetching live market data.

## Scope Guardrail Checklist

Before approving watchlist changes, reviewers must confirm this feature introduced none of the following:

- Live price fetching.
- Website scraping.
- External API calls.
- Kafka producers or streaming topology.
- FastAPI endpoints or service runtime behavior.
- Database schemas, migrations, or persistence code.
- Dashboard code.
- AI analysis, RAG workflows, or autonomous agents.

Allowed changes are limited to documentation, contracts, sample data, validation guidance, repository-local watchlist artifacts, and local validation scripting.

## Evidence Format

Pull requests must include:

- Command executed.
- Pass/fail result.
- Current watchlist version.
- Active entry count.
- Valid watchlist sample count.
- Invalid watchlist sample count.
- Invalid sample to violated rule ID mapping.
- Confirmation that no runtime ingestion, external API, scraping, database, endpoint, streaming, dashboard, or AI behavior was introduced.

## Failure Handling

- Missing watchlist artifact: create `data/watchlists/asset-watchlist.json` or update the governing spec.
- Invalid JSON: fix the watchlist or sample file.
- IPC constraint failure: update the artifact to match the canonical `IPC` entry requirements.
- Invalid sample without rule mapping: update `docs/validation/sample-rule-mapping.md`.
- Advisory or live-price content: remove prohibited language or data fields.

## Guardrails

- Validation must not fetch live prices, scrape websites, call external APIs, connect to databases, create service endpoints, produce streaming events, run dashboard code, or invoke AI analysis.
- Watchlist artifacts are educational and technical scope controls only; they are not investment advice, trading signals, ratings, rankings, or recommendations.
