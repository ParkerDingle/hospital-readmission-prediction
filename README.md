# Predicting 30-Day Hospital Readmission for Diabetic Patients

**Question:** Before a diabetic patient leaves the hospital, can we tell who is likely to be readmitted within 30 days, and can a model flag them better than a simple rule?

Readmissions within 30 days are costly for hospitals and often signal that a patient needed more support after discharge. This project explores what is linked to early readmission, builds models to rank patients by risk, and checks whether those models work equally well across patient groups.

## Data

[Diabetes 130-US Hospitals for Years 1999–2008](https://archive.ics.uci.edu/dataset/296) from the UCI Machine Learning Repository.

- 101,766 hospital stays at 130 US hospitals, from 71,518 different patients
- 50 columns: demographics, diagnoses, lab tests, medications, prior visits, and whether the patient was readmitted (`<30` days, `>30` days, or `NO`)
- Files are in `data/`: `diabetic_data.csv` (the stays) and `IDS_mapping.csv` (what the ID codes mean)

Citation: Clore, J., Cios, K., DeShazo, J., & Strack, B. (2014). *Diabetes 130-US Hospitals for Years 1999-2008* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5230J (CC BY 4.0)

## Notebooks

| Notebook | What it covers |
|---|---|
| `01_first_look.ipynb` | Size of the data, missing values, readmission split, 30-day readmission rate by age |

## Early findings (week 1)

- 11.2% of stays ended in a readmission within 30 days, 34.9% after 30 days, and 53.9% were not readmitted.
- Patients aged 20–30 had the highest 30-day readmission rate (14.2%). That group is small (1,657 stays), so this needs a statistical test before drawing conclusions.
- `weight` is missing for 96.9% of stays, and HbA1c was not measured in 83% of them.

## Roadmap

- [x] First look at the data
- [ ] Cleaning: translate ID codes, remove patients who died or went to hospice, handle repeat patients, group diagnosis codes
- [ ] Exploration and statistical tests
- [ ] Tableau dashboard
- [ ] Models: simple baseline, logistic regression, gradient boosting
- [ ] Evaluation, choosing a cutoff, and SHAP explanations
- [ ] Fairness check across race, gender, and age
- [ ] Final write-up and model card

## Tools

Python (pandas, matplotlib), Jupyter notebooks in PyCharm, Tableau.

## How to run

```
pip install pandas matplotlib jupyter
jupyter notebook 01_first_look.ipynb
```

Run the notebook from the project folder so it can find `data/diabetic_data.csv`.
