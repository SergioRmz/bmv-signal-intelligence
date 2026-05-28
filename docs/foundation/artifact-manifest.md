# Foundation Artifact Manifest

## Purpose

Define exact required artifact paths and minimum sections for the initial project foundation.

## Required Artifacts

| Path | Type | Minimum Required Sections |
|------|------|---------------------------|
| `README.md` | Documentation | Purpose, Scope, Non-Goals, Disclaimer, Planned Stack, Methodology |
| `AGENTS.md` | Agent guidance | Repository Scope, Required Reading Order, Contribution Guardrails, Review Expectations |
| `docs/architecture/foundation-architecture.md` | Architecture | Purpose, Conceptual Boundaries, Data Flow, Repository Areas, Deferred Components |
| `docs/policies/allowed-sources.md` | Policy | Purpose, Categories, Decision Criteria, Attribution, Prohibited Sources |
| `contracts/events/asset-event.schema.json` | Contract | JSON Schema metadata, required fields, nested source and asset constraints |
| `data/samples/asset-events/valid/` | Samples | At least 2 valid JSON files |
| `data/samples/asset-events/invalid/` | Samples | At least 3 invalid JSON files |
| `data/watchlists/asset-watchlist.json` | Watchlist data | Version, effective date, purpose, exactly one active IPC entry, traceability |
| `contracts/watchlists/asset-watchlist.schema.json` | Contract | JSON Schema metadata, IPC-only entry constraints, nested market and traceability constraints |
| `data/samples/watchlists/valid/` | Samples | At least 1 valid IPC watchlist JSON file |
| `data/samples/watchlists/invalid/` | Samples | At least 3 invalid IPC watchlist JSON files |
| `docs/validation/event-contract-validation.md` | Validation guide | Purpose, Local Commands, Evidence Format, Failure Handling |
| `docs/validation/asset-watchlist-validation.md` | Validation guide | Purpose, Local Commands, Rule IDs, Evidence Format, Failure Handling, Guardrails |
| `scripts/validation/check-asset-watchlist.sh` | Local validation script | Path checks, JSON parse checks, IPC constraints, sample mappings, non-advisory guardrails |

## Review Rules

- Each artifact must be present before the feature is considered complete.
- Documentation artifacts must include all minimum required sections.
- Invalid samples must map to rule IDs in `docs/validation/sample-rule-mapping.md`.
- Runtime implementation files are not permitted in this foundation feature.
- Watchlist artifacts must not include live prices, ratings, rankings, recommendations, target prices, portfolio guidance, or performance forecasts.
