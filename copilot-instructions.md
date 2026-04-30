# Portfolio Command Center Instructions (Canonical Schema)

The project now uses a canonical 17-field schema for all portfolio files under portfolios/.

## Canonical Top-Level Fields (Required)
- portfolio_id
- portfolio_name
- account_type
- tax_status
- broker
- last_updated
- version
- status
- core_philosophy
- behavioral_commitment
- intentional_overlap
- target_allocation
- current_holdings
- rebalancing_policy
- review_cycle
- notes
- metadata

## Field Roles
- portfolio_id: Stable machine ID. Must be one of:
  - rollover-ira
  - roth-ira
  - traditional-ira
  - income-portfolio
  - my-investments
- portfolio_name: Display name for dashboards and reports.
- account_type: Account wrapper (Rollover IRA, Roth IRA, Traditional IRA, Taxable Brokerage).
- tax_status: tax-deferred, tax-free, or taxable.
- broker: Fidelity.
- last_updated: ISO 8601 timestamp with timezone offset.
- version: 1.0.
- status: active.
- core_philosophy: Long-form strategy narrative.
- behavioral_commitment: Behavioral discipline narrative.
- intentional_overlap: Object with arbitrary string keys and string explanation values.
- target_allocation: Array of objects with ticker, name, target_pct, role.
- current_holdings: Array of objects with ticker and current_pct.
- rebalancing_policy: method, threshold_pct, calendar_review, rebalance_months, next_review.
- review_cycle: frequency, months, next_review.
- notes: Array of strings.
- metadata: created, schema_version, engine_compatible.

## Data Rules
- Keep ticker symbols and percentages unchanged unless explicitly requested.
- current_holdings mirrors target_allocation at creation time.
- Use semi-annual June/December review cycle.
- Use next_review of 2026-06-15 for review_cycle and rebalancing_policy.
- Use broker Fidelity and version 1.0.
- Use ISO 8601 timestamps with offset (example: 2026-04-30T10:10:00-05:00).

## Dashboard/Parser Rules
- Read data from:
  - portfolios/portfolio_rollover_ira.json
  - portfolios/portfolio_roth_ira.json
  - portfolios/portfolio_traditional_ira.json
  - portfolios/portfolio_income.json
  - portfolios/portfolio_my_investments.json
- Replace deprecated mappings:
  - holdings -> current_holdings
  - allocation/final_allocation -> target_allocation
  - weight -> target_pct
  - philosophy -> core_philosophy
  - rebalance_date -> rebalancing_policy.next_review
  - review_date -> review_cycle.next_review
