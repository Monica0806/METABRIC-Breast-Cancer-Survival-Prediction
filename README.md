
# Breast Cancer Survival Prediction Using METABRIC

An independent computational research study comparing Cox proportional hazards regression and Random Survival Forest models for overall survival prediction in breast cancer.

**Researcher:** Monica Chaganti  
**Research area:** Applied Machine Learning, Survival Analysis, Clinical Data Science

## Research Objective

This study investigates whether a Random Survival Forest can improve overall survival prediction compared with penalized Cox proportional hazards regression using clinical characteristics from the METABRIC breast cancer cohort.

The study evaluates model discrimination, five-year prediction accuracy, calibration, and uncertainty in performance differences.

## Dataset

The study uses clinical and overall survival information from the Molecular Taxonomy of Breast Cancer International Consortium (METABRIC) cohort.

Seven clinical predictors were used:

- Age at diagnosis
- Tumor size
- Number of positive lymph nodes
- Tumor grade
- Estrogen receptor status
- Progesterone receptor status
- HER2 status

The final modeling cohort contained 1,980 patients, divided into 1,583 training patients and 397 held-out test patients.

The original dataset is not redistributed in this repository. Dataset access information and preprocessing instructions will be provided after verification of the source and applicable data-use terms.

## Methods

Two survival prediction models were developed:

1. Penalized Cox proportional hazards regression
2. Random Survival Forest

Both models were trained using the same clinical predictors and evaluated on the same held-out test cohort.

Model performance was assessed using:

- Harrell's concordance index
- Five-year IPCW Brier score
- Five-year grouped calibration
- Paired bootstrap confidence intervals using 2,000 resamples

## Results

| Model | Test C-index | Five-year IPCW Brier score |
|---|---:|---:|
| Cox proportional hazards | 0.6548 | 0.1570 |
| Random Survival Forest | 0.6912 | 0.1451 |

The Random Survival Forest achieved higher test-set discrimination and lower five-year prediction error.

The observed C-index difference (RSF minus Cox) was 0.0364, with a 95% paired bootstrap confidence interval of [0.0089, 0.0655].

The observed five-year Brier score difference (Cox minus RSF) was 0.0119, with a 95% paired bootstrap confidence interval of [0.0023, 0.0219].

The bootstrap confidence intervals account for resampling uncertainty in the held-out test cohort while keeping the fitted models fixed.

## Five-Year Calibration

![Five-year calibration comparison](results/final_model_calibration_5yr.png)

Both models showed differences between predicted and observed survival probabilities in some patient groups.

## Research Manuscript

The independent research manuscript is available in the `manuscript/` directory.

The manuscript describes the study design, survival modeling methods, experimental results, calibration analysis, statistical uncertainty, limitations, and future research directions.

**Status:** Independent research manuscript; not peer-reviewed.

## Reproducibility

The `notebooks/` directory contains the Python notebooks used for data preparation, model development, evaluation, and comparison.

The analysis uses Python, pandas, NumPy, scikit-learn, lifelines, scikit-survival, and Matplotlib.

The original dataset must be obtained from its authorized source before reproducing the analysis.

## Limitations

This study uses a retrospective cohort and a single held-out train-test split.

The models have not been externally validated in an independent clinical population.

The findings should not be interpreted as evidence of clinical readiness or used to guide individual patient care.

## Author

Monica Chaganti

Independent Researcher | Data Science and Applied Machine Learning
