# Gene Expression Prediction of Lung Disease

Data Science Capstone Project: UTA | Authors: Amukta Chaganty and Clarissa Terrones Bejar

---

## Project Question

Can gene activity in lung tissue predict:

1. Which disease a person has (Control, COPD, or ILD)?
2. How severe the disease is (FEV1 breathing test score)?

---

## Dataset

GSE47460: Lung tissue gene expression from 582 patients

Platform 1 (Training): 429 patients, 15,261 genes

- 91 healthy controls
- 145 COPD patients
- 188 ILD patients

Platform 2 (Testing): 153 patients on different microarray

- Sealed for final validation

Source: [https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE47460](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE47460)

---

## What We Are Doing

### Baseline 1: Disease Classification (Logistic Regression)

Question: Can we identify which disease from gene expression?

Model: Logistic regression on all 15,261 genes Target: Control, COPD, or ILD (3 classes) Validation: 5-fold cross-validation on Platform 1 Status: In progress

### Baseline 2: Disease Severity Prediction (Ridge Regression)

Question: Can we predict how severe the disease is from genes?

Model: Ridge regression on 300 selected genes Target: FEV1 percent predicted (continuous) Validation: 5-fold cross-validation on Platform 1

Results (Preliminary):

- R^2 = 0.293 (explains 29% of variance)
- Mean Absolute Error: 16.5 percentage points
- Gene expression is 2.5x more predictive than clinical factors alone

Fold Performance:

- Fold 1: R^2 = 0.370
- Fold 2: R^2 = 0.275
- Fold 3: R^2 = 0.409
- Fold 4: R^2 = 0.263
- Fold 5: R^2 = 0.077

---

## Key Technical Approach

Strict Data Leakage Prevention:

- Feature selection happens inside cross-validation only
- Never on the full dataset
- Training and test data are kept completely separate

5-Fold Cross-Validation:

- Splits 429 samples into 5 groups
- Tests on 85 samples, trains on 337 samples
- Repeated 5 times, each sample tested exactly once
- Honest estimate of how the model generalizes

---

## Repository Structure

notebooks/

- Baseline_1_and_2.ipynb: Current implementation

proposal/

- Capstone_Proposal.pdf: Formal proposal with references

data/

- GSE47460_Platform1_clean.csv
- GSE47460_Platform2_sealed.csv

README.md: This file

---

## References

Kim, D. K., et al. (2015). Integrative phenotyping framework identifies candidate genes in chronic lung disease. BMC Genomics, 16(1). [https://link.springer.com/article/10.1186/s12864-015-2170-4](https://link.springer.com/article/10.1186/s12864-015-2170-4)

Becker, L., et al. (2021). Bronchial gene expression signature associated with rate of subsequent FEV1 decline. Thorax, 76(3), 275-282. [https://pmc.ncbi.nlm.nih.gov/articles/PMC13021120/](https://pmc.ncbi.nlm.nih.gov/articles/PMC13021120/)

Scientific Reports (2021). Inflated prediction accuracy caused by data leakage in feature selection. [https://www.nature.com/articles/s41598-021-87157-3](https://www.nature.com/articles/s41598-021-87157-3)

Transcriptomics of interstitial lung disease: Systematic review and meta-analysis. European Respiratory Journal, 65(6). [https://publications.ersnet.org/content/erj/65/6/2401070](https://publications.ersnet.org/content/erj/65/6/2401070)

Classification across gene expression microarray studies. [https://pmc.ncbi.nlm.nih.gov/articles/PMC2811711/](https://pmc.ncbi.nlm.nih.gov/articles/PMC2811711/)

---

Status: Capstone 1 In Progress (Fall 2026)
