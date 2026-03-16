# Gender Pay Gap Analysis (MORG 2014)

> **Note:** This project is an assignment submission for the Data Analysis course at Central European University (CEU).

This project analyzes the gender pay gap using UK labor market microdata (MORG 2014).  
It combines descriptive visualizations with regression-based analysis to estimate:

- **Unconditional pay gap** (raw average difference in pay)
- **Conditional pay gap** (difference after controlling for key covariates, including education)

---

## Project Overview

The analysis explores how hourly wages differ by gender and how much of that difference remains after adjusting for observable characteristics.

Core questions:
1. What is the raw wage difference between men and women?
2. How does the gap vary by education level?
3. How much of the gap persists after conditioning on controls?

---

## Repository Structure

```text
LICENSE
data/
  morg2014.csv
  README.md
notebooks/
  gender-pay-gap-analysis.ipynb
outputs/
  conditional_gap_by_education_bar.png
  conditional_gap_by_education_scatter.png
  education_by_gender_stacked.png
  gender_distribution.png
  log_wage_density_by_gender.png
  unconditional_regression_fit.png
report/
  report.md
```

---

## Data

- **Source file**: `data/morg2014.csv`
- **Data notes**: see `data/README.md`

> This repository uses a local copy of the dataset. Please check licensing/usage constraints in the data documentation before redistribution.

---

## Methods Summary

The notebook in `notebooks/gender-pay-gap-analysis.ipynb` performs:

- Data loading and basic cleaning
- Gender composition and education composition summaries
- Wage distribution comparison (log wage density by gender)
- Unconditional regression/fit for raw wage difference
- Conditional gap analysis by education level

---

## Key Findings

- In this teacher-only sample ($N=3,791$), women earn about **13.2% less** than men in the unconditional model.
- After controlling for education (with interaction terms), the baseline female gap remains about **12.5% lower** among college graduates.
- The gender-gap interaction terms by education are not statistically significant, suggesting the pay gap is broadly similar across education groups.
- The High School Grad subgroup is a small-sample outlier ($N=31$) and should be interpreted cautiously.
- Overall, the gap narrows only slightly after conditioning on education, indicating education alone does not explain most of the observed difference.

---

## Key Outputs

Generated figures are saved in `outputs/`:

- `gender_distribution.png` — sample composition by gender
- `education_by_gender_stacked.png` — education composition split by gender
- `log_wage_density_by_gender.png` — log wage distribution comparison
- `unconditional_regression_fit.png` — unconditional pay-gap fit
- `conditional_gap_by_education_bar.png` — conditional gap by education (bar view)
- `conditional_gap_by_education_scatter.png` — conditional gap by education (scatter view)

---

## How to Reproduce

### 1) Clone and enter the project

```zsh
git clone https://github.com/zarizachow/da-gender-pay-gap-analysis.git
cd da-gender-pay-gap-analysis
```

### 2) Create and activate a virtual environment (recommended)

```zsh
python3 -m venv .venv
source .venv/bin/activate
```

### 3) Install pinned dependencies

```zsh
pip install -r requirements.txt
```

### 4) Run the notebook

Open and run all cells in:

- `notebooks/gender-pay-gap-analysis.ipynb`

Outputs will be written to `outputs/`.

---

## Report

A written summary is available at:

- `report/report.md`

---

## Limitations

- Results are observational and not causal.
- Estimates depend on selected controls and model specification.
- Unobserved factors (e.g., occupation sorting, firm effects, work history) may still explain part of residual gaps.

---

## Future Improvements

- Add robust/clustered standard errors where appropriate
- Extend decomposition (e.g., Oaxaca–Blinder)
- Add confidence intervals to all plotted gap estimates

---

## License

See `LICENSE`.
