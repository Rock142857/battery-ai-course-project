# AI-Powered Battery Life Prediction and Intelligent Analysis

**Course:** CSI-4130/5130 Artificial Intelligence, Oakland University  
**Project type:** Machine learning evaluation + LLM-assisted analysis  
**Status:** Initial project scaffold; dataset schema and experiments must be verified before reporting results.

## 1. Project Overview

This project explores how machine learning and large language models (LLMs) can support battery-life prediction and explainable battery-data analysis.

The system is planned to:
1. Inspect and preprocess the selected battery dataset.
2. Train and compare suitable machine-learning baselines for a clearly defined battery-life or aging target.
3. Explain predictions using data-grounded feature analysis.
4. Optionally use an LLM API to turn verified model outputs and evidence into a structured engineering-style summary.
5. Evaluate prediction performance, explanation factuality, reproducibility, and limitations.

**Important:** The exact target variable, feature columns, units, and data provenance must be confirmed by inspecting the actual dataset. No performance results are claimed in this initial README.

## 2. Research Questions

- **RQ1:** Which baseline model performs best on the selected battery prediction task?
- **RQ2:** How much do preprocessing and feature selection affect predictive performance?
- **RQ3:** Can an LLM produce useful summaries when it is given only verified model outputs and supporting evidence?
- **RQ4:** How often do generated explanations contain unsupported statements, and how can those errors be measured?

## 3. Planned Method

### Stage A — Dataset audit
- Record the dataset source, license, version, row/column counts, units, missing values, and target definition.
- Check duplicates, outliers, data leakage, and whether multiple rows from the same battery must remain in one split.
- Create a reproducible train/validation/test split.

### Stage B — Machine-learning baselines
Choose models that match the target type after inspecting the dataset:
- Regression, if the target is continuous: DummyRegressor, Linear/Ridge Regression, Random Forest, and Gradient Boosting.
- Classification, if the target is categorical: DummyClassifier, Logistic Regression, Random Forest, and a suitable boosting model.

Use metrics appropriate to the task. For regression, consider MAE, RMSE, and R². For classification, consider accuracy, precision, recall, F1, and ROC-AUC when appropriate. Report test-set results only after the pipeline and split are fixed.

### Stage C — Explainability and LLM analysis
- Provide the LLM with a structured evidence packet containing model predictions, feature values, and verified explanation outputs.
- Compare at least two prompting strategies or two available models if feasible.
- Ask the LLM to separate observed facts from hypotheses, state uncertainty, and avoid claiming a root cause without evidence.
- Evaluate generated reports against a small, manually reviewed checklist or reference answers.

The LLM is an analysis assistant, not a substitute for laboratory validation or engineering judgment.

## 4. Dataset

**Planned dataset:** `BatteryLife_Processed` (the intended dataset mentioned during project planning).

Before experiments, add:
- Original dataset URL and citation
- Dataset version/download date
- License and permitted use
- Target column and unit
- Input feature descriptions and units
- Preprocessing decisions

Do not commit private, confidential, export-controlled, or otherwise restricted company data. Use only data that you are authorized to publish.

## 5. Repository Structure

```text
battery-ai-course-project/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   └── README.md
├── notebooks/
│   └── 01_dataset_audit.ipynb
├── src/
│   ├── dataset_audit.py
│   ├── train_baselines.py
│   └── llm_analysis.py
├── reports/
│   └── final_report.pdf
└── presentation/
    └── video_link.md
```

## 6. Environment Setup

Python 3.10 or newer is recommended.

```bash
python -m venv .venv
```

Activate the environment, then install dependencies:

```bash
# macOS/Linux
source .venv/bin/activate

# Windows PowerShell
.venv\Scripts\Activate.ps1

pip install -r requirements.txt
```

Dataset-specific execution instructions will be added after the dataset schema and file format are confirmed.

## 7. Planned Evaluation

| Component | Planned evaluation |
|---|---|
| Predictive model | MAE/RMSE/R² for regression, or suitable classification metrics |
| Generalization | Fixed held-out test set; group split if samples share a battery identity |
| Baselines | Compare simple baseline against more capable models |
| LLM report quality | Factual consistency, evidence support, completeness, and uncertainty handling |
| Reproducibility | Fixed random seeds, documented dependencies, saved configurations |
| Limitations | Dataset coverage, possible leakage, model bias, LLM hallucinations, and API cost |

All results will be reported only after experiments have been run. Do not fabricate metrics, examples, or conclusions.

## 8. Timeline

- **By October 27, 2026:** Publish the repository and submit its URL on Moodle; include this README and the current project plan.
- **October 28 – November 8:** Audit the dataset, define the target, and establish baseline models.
- **November 9 – November 16:** Compare models and investigate explainability.
- **November 17 – November 22:** Implement and evaluate the LLM analysis component, if feasible.
- **November 23 – November 27:** Complete experiments, error analysis, and report.
- **By November 30, 2026:** Commit the final PDF report, source code, instructions, and final repository state.
- **December 1 or 3, 2026:** Present the project and demonstrate the system.

## 9. Expected Deliverables

- Reproducible dataset-audit and preprocessing code
- Trained baseline models and evaluation results
- A small demonstration workflow for prediction and AI-assisted analysis
- Quantitative evaluation tables and qualitative case studies
- Final academic-style PDF report
- Presentation slides and a link to a recorded presentation
- Citations and acknowledgements for datasets, papers, libraries, models, and APIs

## 10. References and Acknowledgements

This section must be completed with the exact dataset citation, relevant research papers, software libraries, model/API documentation, and any adapted code actually used. Cite the original source rather than copying claims without attribution.

## 11. Current Limitations

This is an initial project plan, not a completed experimental study. The dataset schema, prediction target, model results, LLM provider, and final evaluation protocol remain to be confirmed. Conclusions must be based on reproducible experiments.
