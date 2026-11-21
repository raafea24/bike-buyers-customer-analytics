# Bike Buyers — Customer Behavior Analytics & Exploratory Data Intelligence

An end-to-end exploratory analytics project that examines how demographic, household, commute, and income characteristics relate to bicycle purchasing behavior. The repository preserves the original notebook, saved visual outputs, and staged datasets while presenting the work as a reproducible, repository-relative analysis.

## Business purpose

The analysis supports customer understanding and market segmentation by answering practical questions such as:

- How do age and income differ between purchasers and non-purchasers?
- Which demographic and commute attributes show useful segmentation patterns?
- How can raw customer data be cleaned, transformed, summarized, and visualized before downstream decision-making?

## Analytical workflow

The recorded notebook implements:

1. **Data quality assessment** — schema inspection, missing-value counts, duplicate detection, and categorical inconsistency checks.
2. **Preprocessing** — high-null column removal, type conversion, categorical standardization, typo correction, duplicate removal, and column-specific imputation (mode, forward fill, mean, and K-nearest-neighbors imputation).
3. **Outlier handling** — IQR-based detection/removal for implausible ages and Z-score inspection of income values, with high-income observations retained for analytical context.
4. **Feature transformation** — label encoding, Min–Max normalization, Z-score standardization, age/income discretization, logarithmic income transformation, and derived-feature construction.
5. **Data reduction and segmentation** — correlation analysis, model-based feature ranking, three-cluster K-Means segmentation, and region/occupation aggregation. This is feature selection and numerosity reduction; the notebook does not implement PCA.
6. **Exploratory analysis** — descriptive statistics, distribution-shape measures, histograms, box plots, count plots, scatter plots, pair plots, correlation heatmaps, grouped bars, and cluster visualizations using Matplotlib and Seaborn.

## Repository structure

```text
.
├── data/
│   ├── raw/          # Original Kaggle-derived snapshot
│   ├── cleaned/      # Intermediate column-cleaning stage
│   └── processed/    # Outlier, text-standardized, and transformed stages
├── notebook/
│   └── bike_buyers_data_pipeline.ipynb
├── .gitignore
├── README.md
└── requirements.txt
```

The retained snapshots document the pipeline's progression: the raw data has 505 rows and 11 columns; the standardized snapshot has 501 rows; and the final transformed snapshot has 493 rows, 14 columns, and no blank cells.

## Documented observations

The included data and saved notebook outputs support the following descriptive observations:

- The standardized snapshot contains 267 purchasers and 234 non-purchasers.
- Purchasers have higher recorded mean age (49.76 versus 46.35) and mean income (51,023.72 versus 47,670.94) than non-purchasers.
- Age and income have a mild positive linear relationship in the transformed snapshot (correlation approximately 0.17).
- Purchase rates in the standardized snapshot are close across gender groups (54.5% for male records and 52.1% for female records), indicating limited descriptive separation on gender alone.
- Single records show a 55.6% purchase rate and married records 50.8% in the standardized snapshot. This data-level check does not support an unqualified claim that married customers purchase more frequently.

These are descriptive findings from the included sample, not causal conclusions or production forecasts.

## Scope and limitations

The notebook retains its original saved outputs, including exploratory feature ranking, K-Means clustering, and a recorded logistic-regression baseline. These components are analytical experiments only: there is no deployed prediction service, production inference pipeline, or independently validated forecasting capability. Some narrative cells contain broader interpretations than the retained snapshots directly establish; the verified observations above should be preferred when presenting results.

The notebook has not been re-executed during publication. Repository-relative paths replace the original private shared-drive paths, so cells should be reviewed and run in order if reproducing the analysis locally.

## Local setup

```bash
python -m venv .venv
python -m pip install -r requirements.txt
jupyter lab notebook/bike_buyers_data_pipeline.ipynb
```

No environment file, credential, API key, or private customer record is required.

## Attribution and data source

- Dataset: [Bike Buyers Dataset on Kaggle](https://www.kaggle.com/datasets/heeraldedhia/bike-buyers), published by Heerald Edhia (2020).
- Original analysis source: [shaafeadawood/bike-buyers-data-science](https://github.com/shaafeadawood/bike-buyers-data-science).
- This repository was imported as a clean publication snapshot without transferring the original Git commit history. Original analytical attribution and the dataset citation are retained here.

The source snapshot did not include a standalone project license file. This publication does not add or imply a new license; reuse remains subject to the dataset's Kaggle terms and any rights applicable to the original project content.
