# Monitoring and Retraining Plan

This plan keeps segmentation reliable after deployment.

## Monitoring cadence

1. weekly KPI checks
2. monthly distribution and feature-drift checks
3. quarterly threshold review

## What to monitor

Segment distribution drift:

- compare current segment mix vs baseline (`data/segments/segment_summary_percentile.csv`)
- alert if any segment share shifts by more than 5 percentage points month-over-month

Feature drift:

- track percentile movement for core drivers (`freq_score`, `loyalty_score`, `avg_basket_size`, `unique_products`)
- alert on sustained shifts using PSI or KS thresholds

Performance drift:

- KPI by segment (IRPU, reorder rate, reactivation rate)
- alert when segment-targeted campaigns lose lift vs control for 2 consecutive cycles

Stability diagnostics:

- use split stability references from `data/segments/split_stability_summary.csv`
- monitor relative-gap trend over time, not one-off spikes only

## Retraining / recalibration triggers

Trigger threshold recalibration when one of these occurs:

1. segment distribution alert for 2 straight months
2. feature drift threshold breached for 2 straight months
3. campaign lift deterioration across at least 2 segments

## Recalibration protocol

1. refresh the latest feature snapshot
2. rerun `07_rule_based_segmentation.ipynb`
3. compare old vs new segment assignments and KPI lift
4. approve only if:
- business interpretability stays clear
- holdout performance does not regress
- guardrails remain healthy

## Ownership

1. Data Analyst owns monthly scoring QA and drift reporting.
2. Marketing Ops owns campaign execution and guardrail enforcement.
3. Product/Analytics Manager approves threshold updates and rollout decisions.
