# Executive Summary (Recruiter + Hiring Manager)

## Project in one line

Built and validated a production-ready customer segmentation framework for Instacart-style user behavior data, choosing a deterministic approach after testing and rejecting weaker unsupervised alternatives.

## Business question

Can we segment users in a way that is both statistically defensible and operationally usable for lifecycle campaigns?

## Final recommendation

Ship a 4-segment rule-based framework:

1. Champions
2. Frequent Explorers
3. Loyal Occasionals
4. At Risk

Why this instead of pure clustering:

- baseline clustering silhouette: `0.105`
- all-features clustering silhouette: `-0.008`
- best clustering result (behavioral features): `0.191` at `k=2`

Conclusion: clustering is useful for exploratory structure checks, but not strong enough for final assignment logic.

## Scale and rigor

- users analyzed: `182,223`
- engineered features: `149`
- full pipeline: data readiness -> feature engineering -> preprocessing -> clustering diagnostics -> final segmentation
- statistical validation includes ANOVA + effect sizes + stability checks

## Segment distribution (current run)

- Champions: `61,317` (`33.65%`)
- Frequent Explorers: `30,055` (`16.49%`)
- Loyal Occasionals: `29,851` (`16.38%`)
- At Risk: `61,000` (`33.48%`)

## Why this portfolio is relevant for FAANG DA roles

1. Shows decision quality, not just model-building.
2. Demonstrates willingness to reject weak methods with evidence.
3. Connects analytics outputs to operational actions and experiment plans.
4. Includes monitoring/recalibration design for production reliability.

## What to review first

1. `docs/01_decision_memo.md`
2. `docs/02_segment_action_playbook.md`
3. `docs/03_experiment_plan.md`
4. `docs/04_monitoring_and_retraining_plan.md`
5. `docs/00_canonical_case_story.md`

## Suggested interview narrative (30 seconds)

I started with an unsupervised-first approach, tested multiple clustering paths, and found that separability was too weak for reliable personas. Instead of overclaiming, I switched to a deterministic segmentation design, validated it statistically, mapped each segment to concrete actions, and defined an A/B + monitoring plan so this can actually run in production.
