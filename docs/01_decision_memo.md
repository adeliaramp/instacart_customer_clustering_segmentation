# Decision Memo: Customer Segmentation Strategy

## Context

We need a segmentation framework that is:

- statistically defensible,
- explainable to non-technical partners,
- operationally usable for campaign targeting.

Dataset coverage:

- users: 182,223
- engineered features: 149

## Decision

Use a deterministic 4-segment, score-based framework as the production approach.

Segments:

1. Champions
2. Frequent Explorers
3. Loyal Occasionals
4. At Risk

## Why this decision

Unsupervised clustering was tested hard but did not produce strong enough separation for clean personas:

- baseline clustering: silhouette `0.105` (`data/clusters/clustering_metrics.csv`)
- all-features ablation (149 features): silhouette `-0.008` (`data/clusters/ablation_all_features/clustering_metrics_all_features.csv`)
- behavioral-feature ablation (14 features): best silhouette `0.191` with `k=2` (`data/clusters/ablation_non_aisle_features/clustering_metrics_non_aisle.csv`)

Interpretation:

- clustering has exploratory value,
- but segmentation assignment should not rely on a weak/moderate latent structure.

## Evidence that the final segmentation is meaningful

From ANOVA and effect-size checks (`data/segments/anova_results.csv`):

- large separation: `cv_days_between_orders`, `unique_products`
- medium separation: `unique_aisles`
- small separation: `reorder_consistency`, `avg_basket_size`
- negligible practical separation: `mean_order_hour` (statistically significant due to large sample size)

Current segment distribution (`data/segments/segment_summary_percentile.csv`):

- Champions: 61,317 (33.65%)
- Frequent Explorers: 30,055 (16.49%)
- Loyal Occasionals: 29,851 (16.38%)
- At Risk: 61,000 (33.48%)

## Risks and caveats

- `mean_days_between_orders` is mathematically tied to assignment inputs; treat that metric as a definition sanity check, not independent validation.
- Some split-stability gaps are non-trivial on `unique_products`; this is acceptable for now but should be monitored in production.
- This is not yet out-of-time validated.

## Expected business use

Primary use case:

- targeted lifecycle campaigns with clear audience logic and full user coverage.

Expected near-term value:

- faster campaign design cycles,
- fewer arbitrary audience definitions,
- more consistent KPI tracking by segment.

## Next actions

1. Run A/B tests on segment-specific actions before broad rollout.
2. Monitor segment drift and KPI drift monthly.
3. Recalibrate thresholds quarterly or when drift alerts trigger.
