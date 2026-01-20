# Ridge Regression for Salary Adaptation

This project implements a data mining pipeline to predict developer salaries using the Stack Overflow Developer Survey 2025 dataset. It utilizes **Ridge Regression** to establish a transparent baseline for salary benchmarking and anomaly detection.

## Getting Started (Linux)

Follow these steps to set up the environment and run the analysis.

### 1. Environment Setup
Create a new Conda environment and install the required dependencies located in the root directory:

```bash
# Create and activate environment
conda create -n BI2025 python=3.11 -y
conda activate BI2025

# Install dependencies
pip install -r requirements.txt
```

### 2. Data Preparation
Extract the survey data into the `data` folder. Ensure the unzipped directory structure matches the notebook's expectations:

```bash
unzip stack-overflow-developer-survey-2025.zip -d data
```
*Note: The notebook expects the CSV file at `data/stack-overflow-developer-survey-2025/survey_results_public.csv`.*

### 3. Run the Analysis
Launch the Jupyter Notebook:

```bash
jupyter notebook data-analytics-notebook.ipynb
```

---

## Project Details

This experiment strictly adheres to the **CRISP-DM** (Cross-Industry Standard Process for Data Mining) methodology to ensure a structured and business-oriented approach:

1.  **Business Understanding:** Defining goals for salary standardization and budget optimization.
2.  **Data Understanding & Preparation:** Cleaning noisy survey data, handling outliers via log-transformation/percentile capping, and managing high-cardinality features.
3.  **Modeling:** Implementing **Ridge Regression** (L2 Regularization) to handle multicollinearity, compared against a non-linear Histogram-based Gradient Boosting model.
4.  **Evaluation:** Assessing performance ($R^2$, MAE) and identifying potential biases (e.g., geographic).
5.  **Deployment:** Proposing a human-in-the-loop strategy for HR integration.

### Provenance & Reproducibility
A key feature of this project is the integration of a **Semantic Knowledge Graph**. Using the `starvers` engine, every step of the pipeline—from data loading to hyperparameter tuning—is logged using **PROV-O** and **MLSO** ontologies. This ensures that the entire experiment is machine-queryable, transparent, and reproducible.

### Results & Reports
For a detailed analysis of the experiment, modeling decisions, and evaluation, please refer to the reports located in the `Reports/` directory:

* **[Full Report](Reports/BI_Data_Analytics.pdf):** Comprehensive documentation of the entire CRISP-DM lifecycle, including deep dives into feature engineering, hyperparameter tuning, and ethical analysis.
* **[Compact Report](Reports/BI_Data_Analytics_Compact.pdf):** A condensed summary focusing on key findings and deliverables, aligned with course requirements.

### Key Findings
* **Model Performance:** The linear **Ridge Regression** baseline achieved an $R^2$ of ~0.57. A comparative non-linear **Histogram-based Gradient Boosting (HGB)** model improved predictive accuracy to an $R^2$ of ~0.60 on the test set.
* **Benchmarks:** Our models significantly outperformed trivial baselines and achieved results comparable to state-of-the-art solutions found on platforms like Kaggle and GitHub for similar datasets.
* **Limitations:** Error analysis revealed that predictive accuracy degrades in high salary brackets (>$150k). Additionally, geographic biases were identified (e.g., higher error rates for the USA), supporting the recommendation for a "human-in-the-loop" deployment strategy rather than full automation.