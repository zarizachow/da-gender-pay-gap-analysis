# Gender Pay Gap Analysis (MORG 2014)

> **Note:** This project is an assignment submission for the Data Analysis 2 course at Central European University (CEU).

This project analyses the gender pay gap among Elementary and Middle School Teachers using US labor market microdata from the CPS MORG 2014 dataset. It combines descriptive visualisations with OLS regression to estimate:

- **Unconditional pay gap** — the raw average difference in hourly wages by gender
- **Conditional pay gap** — the difference after controlling for education level

---

## Project Overview

The analysis focuses on three core questions:

1. What is the raw wage difference between male and female teachers?
2. How does the gap vary across education levels?
3. How much of the gap persists after conditioning on education?

---

## Repository Structure

```text
da-gender-pay-gap-analysis/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   └── README.md               # Data source and download instructions
├── notebook/
│   └── gender_pay_gap_analysis.ipynb
├── outputs/
│   ├── gender_distribution.png
│   ├── education_by_gender_stacked.png
│   ├── log_wage_density_by_gender.png
│   ├── unconditional_regression_fit.png
│   ├── conditional_gap_by_education_bar.png
│   └── conditional_gap_by_education_scatter.png
└── report/
    └── report.md
```

---

## Data

The raw dataset is **not included** in this repository due to file size.

- **Dataset:** CPS Earnings, MORG 2014 (`morg2014.csv`)
- **Source:** https://osf.io/g8p9j/
- **File path in source:** `raw/morg2014.csv`

To reproduce the analysis, download the file and place it at `data/morg2014.csv` before running the notebook. Full instructions are in `data/README.md`.

---

## Methods

The notebook in `notebook/gender_pay_gap_analysis.ipynb` covers:

- Data loading and cleaning
- Sample filtering to occupation code 2310 (Elementary and Middle School Teachers)
- Gender and education composition summaries
- Log wage distribution comparison by gender
- OLS regression for the unconditional gender wage gap
- OLS regression with education dummies and gender-education interaction terms
- All models use HC3 heteroskedasticity-robust standard errors

---

## Key Findings

- In this teacher sample (N = 3,791), female teachers earn about **13.2% less** than male teachers in the unconditional model.
- After controlling for education, the baseline gap among college graduates remains around **12.5%** and is highly statistically significant (p < 0.01).
- All gender-education interaction terms are statistically insignificant, meaning the gap is broadly consistent across education levels.
- The High School Grad subgroup (N = 31) is a small-sample outlier and should be interpreted with caution.
- Education alone does not explain most of the observed pay difference.

---

## Key Outputs

All figures are saved in `outputs/`:

| File | Description |
|---|---|
| `gender_distribution.png` | Sample composition by gender |
| `education_by_gender_stacked.png` | Education distribution split by gender |
| `log_wage_density_by_gender.png` | Log wage density comparison by gender |
| `unconditional_regression_fit.png` | OLS fit for the unconditional gender gap |
| `conditional_gap_by_education_bar.png` | Conditional gap by education (bar chart) |
| `conditional_gap_by_education_scatter.png` | Conditional gap by education (scatter) |

---

## How to Reproduce

### 1. Clone the repository

```zsh
git clone https://github.com/zarizachow/da-gender-pay-gap-analysis.git
cd da-gender-pay-gap-analysis
```

### 2. Download the data

Follow the instructions in `data/README.md` to download `morg2014.csv` and place it in the `data/` folder.

### 3. Set up the environment

```zsh
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### 4. Run the notebook

Open and run all cells in `notebook/gender_pay_gap_analysis.ipynb`. Plots will be saved to `outputs/` automatically.

---

## Report

A written summary of the analysis, including regression tables and interpretations, is available at `report/report.md`.

---

## Limitations

- Results are observational and not causal.
- Unobserved factors such as experience, seniority, and school type are not controlled for.
- The High School Grad subgroup is too small for reliable estimates.

---

## Future Improvements

- Extend the analysis using Oaxaca-Blinder decomposition
- Add confidence intervals to all plotted gap estimates
- Control for additional covariates such as experience and part-time status

---

## Tools

- Python, pandas, NumPy
- statsmodels (OLS, HC3 robust standard errors)
- matplotlib, seaborn

---

## License

See `LICENSE`.