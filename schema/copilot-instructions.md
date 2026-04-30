# Canonical Portfolio Schema Instructions (v1.0)

Use this exact 17-field top-level schema for every portfolio JSON file.

## Required Top-Level Fields (17)
1. portfolio_id: Stable ID string. Allowed IDs in this project:
   - rollover-ira
   - roth-ira
   - traditional-ira
   - income-portfolio
   - my-investments
2. portfolio_name: Human-readable portfolio name.
3. account_type: Account wrapper type (for example: Rollover IRA, Roth IRA, Taxable Brokerage).
4. tax_status: Tax classification (tax-deferred, tax-free, taxable).
5. broker: Always Fidelity.
6. last_updated: ISO 8601 timestamp with timezone offset (example: 2026-04-30T10:10:00-05:00).
7. version: Always 1.0.
8. status: Lifecycle state (active).
9. core_philosophy: Narrative strategy text.
10. behavioral_commitment: Narrative behavioral discipline text.
11. intentional_overlap: Object of explanation entries where each key is a label and each value is a string explanation.
12. target_allocation: Array of objects with required keys:
    - ticker (string)
    - name (string)
    - target_pct (number)
    - role (string)
13. current_holdings: Array of objects with required keys:
    - ticker (string)
    - current_pct (number)
14. rebalancing_policy: Object with required keys:
    - method (string)
    - threshold_pct (number)
    - calendar_review (string)
    - rebalance_months (array of strings)
    - next_review (date string, YYYY-MM-DD)
15. review_cycle: Object with required keys:
    - frequency (string)
    - months (array of strings)
    - next_review (date string, YYYY-MM-DD)
16. notes: Array of strings.
17. metadata: Object with required keys:
    - created (ISO 8601 timestamp with timezone offset)
    - schema_version (string, 1.0)
    - engine_compatible (boolean)

## Project Rules
- Keep broker as Fidelity.
- Keep version as 1.0.
- Use ISO 8601 timestamps with offsets for last_updated and metadata.created.
- current_holdings mirrors target_allocation at creation time.
- Semi-annual review cadence: June and December.
- next_review target date: 2026-06-15 in both rebalancing_policy and review_cycle.
- Do not introduce fields outside the canonical 17-field structure.
