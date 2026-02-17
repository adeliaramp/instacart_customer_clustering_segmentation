# Segment Action Playbook

This playbook maps each segment to concrete actions and success metrics.

## 1) Champions

Behavior summary:

- high order frequency
- high loyalty
- usually a core revenue base

Actions:

1. early access to high-intent promotions
2. premium basket upsell bundles
3. referral incentives

Primary KPI:

- incremental revenue per user (IRPU)

Guardrail KPI:

- discount burn rate

## 2) Frequent Explorers

Behavior summary:

- frequent shopping
- broader exploration, lower repeat concentration

Actions:

1. personalized “try next” recommendations
2. cross-category bundles
3. low-friction reorder shortcuts for emerging favorites

Primary KPI:

- 30-day reorder rate

Guardrail KPI:

- category concentration decline (avoid over-narrowing exploration too fast)

## 3) Loyal Occasionals

Behavior summary:

- lower frequency than Champions
- strong repeat tendency when active

Actions:

1. timed reminder campaigns near expected reorder windows
2. replenishment nudges for staple categories
3. free-delivery threshold nudges

Primary KPI:

- order frequency uplift

Guardrail KPI:

- opt-out / unsubscribe rate

## 4) At Risk

Behavior summary:

- lower frequency
- weaker loyalty signals

Actions:

1. win-back offers with strict budget caps
2. lightweight “restart basket” templates
3. category-level relevance messaging before deep discounts

Primary KPI:

- reactivation rate (30/60/90-day windows)

Guardrail KPI:

- negative-margin order share

## Targeting policy

1. each user belongs to exactly one segment at scoring time
2. segment is refreshed on a fixed cadence (monthly by default)
3. campaign eligibility layers on top of segment assignment (inventory, region, budget)

## Measurement policy

1. every campaign result is reported by segment and by holdout/control
2. no segment-level rollout without a measurable positive lift vs control
3. segment definitions remain stable unless drift criteria are breached
