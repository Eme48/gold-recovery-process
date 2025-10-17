# Gold Recovery Process — Predictive Modeling

End‑to‑end data science project to **model and optimize gold recovery** in an industrial flotation pipeline.
Focus on predicting *rougher* and *final* recovery using process sensor data, handling time‑series leakage,
and evaluating with **sMAPE** as in typical metallurgical quality tasks.

## 🔍 Problem
Given historical process variables (feed composition, air flow, reagent dosage, cell conditions),
predict:
- `rougher.output.recovery`
- `final.output.recovery`

and provide insights that help stabilize and improve the production process.

## 📁 Repository Structure
```
gold-recovery-process/
├─ notebooks/
│  └─ gold_recovery_project_integrado_v5.ipynb
├─ src/
│  └─ __init__.py
├─ data/
│  ├─ raw/        # put original datasets here (excluded from git)
│  └─ processed/  # derived/cleaned datasets (excluded from git)
├─ reports/       # figures, exported tables
├─ .github/workflows/
│  └─ lint.yml    # optional CI (flake8)
├─ requirements.txt
├─ .gitignore
├─ LICENSE
└─ README.md
```

## 🧪 Methodology (high level)
1. **EDA**: feature distributions, missingness, train/test split respecting time.
2. **Preprocessing**: alignment of targets and features, scaling, imputation.
3. **Modeling**: baselines → regularized regression / tree‑based models.
4. **Validation**: cross‑validation and **sMAPE** for rougher & final recovery;
   report macro score = mean(sMAPE_rougher, sMAPE_final).
5. **Interpretability**: feature importance / permutation importance.
6. **Reporting**: figures in `reports/`.

## ▶️ How to Run
```bash
# create environment
python -m venv .venv && source .venv/bin/activate  # (Windows: .venv\Scripts\activate)
pip install -r requirements.txt

# start notebooks
jupyter notebook notebooks/gold_recovery_project_integrado_v5.ipynb
```

> **Data**: place source CSVs under `data/raw/` (not versioned). Update paths in the notebook if needed.

## 📊 Metrics
- **sMAPE** for `rougher.output.recovery` and `final.output.recovery`
- Macro score = average of both sMAPEs

## 🧭 Next Steps
- Parameter tuning with cross‑validation
- Drift monitoring for sensor signals
- Export a lightweight inference pipeline (joblib / ONNX)
- Optional: Streamlit report for operations team

---

**Author:** Emerson Ríos · 2025  
**License:** MIT
