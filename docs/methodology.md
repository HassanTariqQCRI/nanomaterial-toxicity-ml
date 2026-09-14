# Methodology

## 1. Scientific framing

The project treats each record as an experimental observation linking a metal-oxide nanoparticle, biological system, exposure and measured response. Two supervised problems are considered:

1. **Classification:** predict toxic versus nontoxic response.
2. **Regression:** predict continuous cell viability percentage.

Toxicity is defined from the 50% viability boundary. Consequently, viability is forbidden as a classification predictor and toxicity is forbidden as a regression predictor.

## 2. Exploratory analysis

The audit covers dataset size, toxic-class prevalence, source-study counts, representation by material and biological system, numeric distributions, skewness, correlations, categorical cardinality and measurement-method missingness. EDA informs transformations rather than standing alone as description.

## 3. Data preparation

- Strip and normalize categorical values.
- Convert exposure duration to numeric hours.
- Median-impute numerical predictors inside each training fold.
- Use explicit or most-frequent categorical imputation inside each fold.
- Apply `log1p` only to non-negative, materially right-skewed variables.
- Standardize inputs for scale-sensitive linear and distance-based models.
- One-hot encode categorical predictors with unknown-category handling.
- Group infrequent categories where supported.

Signed electronic and surface-charge variables are not blindly log-transformed.

## 4. Validation design

`Pubmed ID` defines study groups. Five-fold grouped validation keeps every source study wholly within either training or validation data for a fold. This is stricter and more scientifically realistic than ordinary row-level stratification for literature-derived data.

All predictions used for detailed assessment are out-of-fold. Preprocessing is fitted only on each training fold.

## 5. Classification assessment

Accuracy is retained for context but is not the headline metric because the toxic class is rare. The principal measures are:

- **Precision:** proportion of toxicity alerts that are correct.
- **Recall:** proportion of toxic observations detected.
- **F1:** harmonic balance of precision and recall.
- **PR-AUC:** performance across thresholds under class imbalance.
- **ROC-AUC and balanced accuracy:** complementary discrimination measures.

Threshold curves show the cost-sensitive trade-off between missed toxic cases and false alarms.

## 6. Regression assessment

- **MAE:** average absolute error in viability percentage points.
- **RMSE:** emphasizes large errors.
- **R²:** variance-explained context.

Fold-level ranges and standard deviations reveal sensitivity to held-out studies.

## 7. Interpretation boundary

The workflow supports hypothesis generation and prioritization for laboratory validation. It does not establish biological causality, certify safety, or replace prospective experiments.
