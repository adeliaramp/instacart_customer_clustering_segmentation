# Contributing

Thanks for contributing.

## Local setup

1. Create and activate a Python 3.9 virtual environment.
2. Install dependencies:
   `pip install -r requirements.txt`
3. Register kernel (optional):
   `python -m ipykernel install --user --name instacart-segmentation`

## Notebook execution order

1. `01_data_readiness_assessment.ipynb`
2. `02_user_feature_engineering.ipynb`
3. `03_feature_preprocessing_and_reduction.ipynb`
4. `04_clustering_baseline_validation.ipynb`
5. `05_clustering_ablation_all_features.ipynb`
6. `06_clustering_ablation_behavioral_features.ipynb`
7. `07_rule_based_segmentation.ipynb`

## Contribution guidelines

- Keep notebooks deterministic (set random seed where relevant).
- Add markdown cells for business and statistical interpretation, not only plots.
- Avoid committing large raw data files.
- Keep output artifacts in `visualizations/` or `data/` subfolders with clear names.
