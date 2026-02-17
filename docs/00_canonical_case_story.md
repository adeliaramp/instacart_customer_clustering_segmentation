# Canonical Case Story (What To Review First)

If you are reviewing this portfolio as a hiring manager, this is the fastest path:

1. Read `docs/01_decision_memo.md` first.
2. Skim `README.md` for project scope and outputs.
3. Open `01_data_readiness_assessment.ipynb` to verify data suitability and risk checks.
4. Open `02_user_feature_engineering.ipynb` for feature design and QA.
5. Open `03_feature_preprocessing_and_reduction.ipynb` for preprocessing and PCA tradeoffs.
6. Open `07_rule_based_segmentation.ipynb` for final production segmentation logic.

Appendix notebooks (diagnostic evidence):

1. `04_clustering_baseline_validation.ipynb`
2. `05_clustering_ablation_all_features.ipynb`
3. `06_clustering_ablation_behavioral_features.ipynb`

Why this structure:

- The core storyline shows decision quality from data checks to deployable segmentation.
- The appendix proves rigor: I tested unsupervised alternatives, reported weak results honestly, and chose a simpler production approach.
