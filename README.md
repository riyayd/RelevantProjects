# ML Model Bias Audit Tool

A Jupyter notebook that trains a machine learning classifier and audits it for **fairness, bias, and transparency** — producing a structured HTML governance report. No external API or paid service required.

## What it does

1. Trains and compares two classifiers (Random Forest + Logistic Regression) on customer churn data
2. Measures three standard AI governance fairness metrics across demographic groups:
   - **Demographic parity** — equal prediction rates across groups
   - **Equal opportunity** — equal recall (catching actual churners) across groups
   - **Predictive parity** — equal precision across groups
3. Computes a bias risk rating (Low / Medium / High) with automated logic
4. Generates a full **HTML governance report** with charts, tables, and actionable recommendations

## Why this matters

Regulators across the EU (EU AI Act, GDPR Article 22) require financial institutions to audit automated decision-making systems for bias before deployment. This tool demonstrates that workflow end-to-end.

## Tech stack

- Python · Jupyter Notebook
- scikit-learn (Random Forest, Logistic Regression, metrics)
- pandas · NumPy
- Matplotlib · Seaborn
- Jinja2 (HTML report generation)

## How to run

```bash
# 1. Install dependencies (one-time)
pip install jupyter scikit-learn pandas matplotlib seaborn jinja2

# 2. Launch Jupyter
jupyter notebook ML_Bias_Audit_Tool.ipynb

# 3. Run all cells top to bottom (Kernel → Restart & Run All)
```

No API key or internet connection needed after installation.

## Output files

| File | Description |
|------|-------------|
| `model_performance.png` | Confusion matrix, model comparison, feature importance |
| `fairness_audit.png` | Bias analysis across gender, age group, and region |
| `governance_report.html` | Full governance report — open in any browser |

## Key findings (example run)

- Random Forest outperforms Logistic Regression on AUC and F1
- Gender and Age introduce measurable demographic parity gaps
- Recommendations include feature removal, re-weighting, and monthly monitoring

## Related projects

- [`CustomerChurn.ipynb`](../CustomerChurn.ipynb) — baseline churn prediction
- [`NetflixStockForcasting.ipynb`](../NetflixStockForcasting.ipynb) — ARIMA forecasting
- [`Risk_Management_101.ipynb`](../Risk_Management_101.ipynb) — financial risk analysis

---

*MSc Computational & Applied Mathematics, FAU Erlangen-Nürnberg*
