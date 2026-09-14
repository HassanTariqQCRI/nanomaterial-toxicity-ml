# Project Walkthrough

## The evidence

Two spreadsheet versions represented literature-derived metal-oxide nanoparticle experiments. Each row combined particle descriptors, a cell system, dose, exposure, assay, PubMed source, viability and toxicity.

## Tasks A–B: understand data quality

The analysis quantified class balance, material coverage, numeric distributions, skewness, correlations, categorical diversity and missing metadata. Toxic observations represented 15.5% of Version I and 12.8% of Version II. Material coverage was uneven, mass dose was right-skewed and Version I had weaker measurement-method provenance.

## Task C: define leakage-safe targets

The work separated toxicity classification from viability regression. Because toxicity is derived from viability below 50%, the alternate endpoint was always removed. PubMed ID was retained only for study grouping.

## Task D: build fold-contained preparation

The pipelines cleaned categories, converted exposure time, imputed missing values, transformed supported skewed variables, encoded categoricals and scaled where models required it. Every learned preprocessing operation was fitted inside training folds.

## Task E: compare models fairly

Classification compared balanced Logistic Regression, KNN, Random Forest and XGBoost. Regression compared Ridge, Random Forest and XGBoost. F1—not raw accuracy—was emphasized for the imbalanced toxicity endpoint.

## Task F: test unseen-study generalization

Five-fold grouped out-of-fold predictions prevented a PubMed study from appearing in both training and validation data. Threshold analysis made the recall-versus-false-alarm trade-off explicit.

## Task G: translate metrics into research decisions

The smaller curated dataset performed better for classification. The result supports using ML as a screening and prioritization aid while emphasizing the need for richer metadata, external validation, uncertainty estimation and laboratory confirmation.
