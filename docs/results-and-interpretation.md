# Results and Interpretation

## Dataset comparison

| Property | Version I | Version II |
|---|---:|---:|
| Rows | 6,842 | 3,246 |
| Toxic observations | 1,059 | 414 |
| Toxic prevalence | 15.5% | 12.8% |
| Relative character | Larger, noisier | Smaller, curated |

Version II's stronger F1 despite fewer rows suggests that curation and metadata consistency can outweigh raw dataset volume. Because the versions overlap, this is a curation comparison—not external validation.

## Classification

| Dataset | Leading model | Mean F1 |
|---|---|---:|
| Version I | XGBoost | 0.470 |
| Version II | Random Forest | 0.590 |

At threshold 0.50, the selected Version I grouped out-of-fold model produced:

- precision: **0.374**
- recall: **0.630**
- F1: **0.469**
- true positives: **667**
- false positives: **1,118**
- false negatives: **392**

A lower threshold can detect more toxic cases but increases false alarms. The scientifically appropriate threshold depends on the relative cost of missed toxicity versus additional laboratory testing.

## Regression

| Dataset | Leading model | MAE |
|---|---|---:|
| Version I | XGBoost | 16.789 |
| Version II | Random Forest | 16.151 |

Errors of roughly 16 viability percentage points are meaningful on a 0–100 scale. Regression therefore provides useful ranking context but is not sufficiently precise for stand-alone decisions.

## Why performance is modest

- Toxic cases are substantially outnumbered.
- Laboratories, assays, particles, cell systems, doses and protocols are heterogeneous.
- Some conditions are underrepresented.
- Version I has sparse measurement-method metadata.
- Cases near 50% viability are intrinsically difficult to classify.
- Study-grouped validation deliberately tests harder unseen-study generalization.
- Available descriptors omit potentially important biological and experimental factors.

## Recommended next work

1. Acquire genuinely external, prospective laboratory data.
2. Increase toxic and underrepresented particle–cell–assay combinations.
3. Improve measurement-method and provenance metadata.
4. Engineer dose–time interactions and physically meaningful size relationships.
5. Use nested grouped tuning, probability calibration and uncertainty estimates.
6. Add interpretable feature-attribution analysis.
7. Compare grouped and ordinary stratified estimates without treating them as equivalent.
