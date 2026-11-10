# PRCE-003: Mall Customers Data Analysis (PySpark)

## Project overview

This project uses PySpark to explore customer Spending Scores and segment customers using their annual income and Spending Score. The analysis is implemented in a Jupyter notebook and includes CSV outputs and a written report.

## Project objectives

- Load and clean the customer data with PySpark.
- Describe the distribution of Spending Scores using summary statistics.
- Compare average Spending Scores across gender and age groups.
- Measure the Pearson correlation between annual income and Spending Score.
- Apply KMeans clustering to annual income and Spending Score.

## Dataset

The supplied CSV contains 200 customer records and five original columns:

| Column | Description |
|---|---|
| `CustomerID` | Customer identifier |
| `Genre` | Customer gender as recorded in the source data |
| `Age` | Customer age |
| `Annual Income (k$)` | Annual income, in thousands of dollars |
| `Spending Score (1-100)` | Spending Score on a 1–100 scale |

The notebook renames the columns to `snake_case` (for example, `Annual Income (k$)` becomes `annual_income_k`) and casts the numeric fields to integers.

The project files do not identify the dataset's source or license. Verify source attribution and redistribution permissions before redistributing the dataset.

## Repository structure

```text
.
├── README.md
├── data/
│   └── Mall_Customers.csv
├── notebook/
│   └── PRCE-003_Mall_Customers_Analysis.ipynb
├── outputs/
│   ├── cleaned_mall_customers.csv
│   ├── kmeans_cluster_summary.csv
│   ├── kmeans_segments.csv
│   ├── ss_by_age_group.csv
│   └── ss_by_genre.csv
└── reports/
    └── PRCE-003_Mall_Customers_Analysis_Report.docx
```

## Technology stack and setup

The notebook metadata identifies Python 3.11 and the `mall_pyspark` Jupyter kernel. The project setup uses Conda, OpenJDK 17, PySpark 3.5, pandas, matplotlib, seaborn, Jupyter, and ipykernel.

In Windows Anaconda Prompt or a Conda-enabled terminal, create and configure the environment:

```powershell
conda create -n mall_pyspark python=3.11 -y
conda activate mall_pyspark
conda install -c conda-forge openjdk=17 pyspark=3.5 pandas matplotlib seaborn jupyter ipykernel -y
python -m ipykernel install --user --name mall_pyspark --display-name "Python (mall_pyspark)"
```

## How to run

The notebook reads `data/Mall_Customers.csv` and writes the generated CSV files under `outputs/`. Start Jupyter from the project root so these relative paths resolve correctly:

```powershell
jupyter notebook
```

Open [`notebook/PRCE-003_Mall_Customers_Analysis.ipynb`](notebook/PRCE-003_Mall_Customers_Analysis.ipynb), select the **Python (mall_pyspark)** kernel, and run the cells in order.

## Analysis and results

The following figures are reflected in the provided dataset and summary CSVs:

- Overall Spending Score mean: **50.20**; median: **50**.
- Average Spending Score by gender: **Female 51.53**, **Male 48.51**.
- The **25–34** age group has the highest average Spending Score: **63.17**.
- Pearson correlation between annual income and Spending Score: approximately **+0.0099**. This describes a near-zero linear relationship in this dataset; it does not establish cause and effect.
- KMeans uses **k = 5**. Cluster IDs are numeric labels and are not given semantic names in the project files.

## Outputs

- [`outputs/cleaned_mall_customers.csv`](outputs/cleaned_mall_customers.csv) — cleaned customer records with renamed columns.
- [`outputs/ss_by_genre.csv`](outputs/ss_by_genre.csv) — customer counts and Spending Score summary statistics by gender.
- [`outputs/ss_by_age_group.csv`](outputs/ss_by_age_group.csv) — customer counts and average score and income by age group.
- [`outputs/kmeans_segments.csv`](outputs/kmeans_segments.csv) — annual income, Spending Score, and assigned KMeans cluster ID for each customer.
- [`outputs/kmeans_cluster_summary.csv`](outputs/kmeans_cluster_summary.csv) — customer counts and average income, Spending Score, and age for each cluster.
- [`notebook/PRCE-003_Mall_Customers_Analysis.ipynb`](notebook/PRCE-003_Mall_Customers_Analysis.ipynb) — PySpark analysis and visualizations.
- [`reports/PRCE-003_Mall_Customers_Analysis_Report.docx`](reports/PRCE-003_Mall_Customers_Analysis_Report.docx) — written analysis report.

## Limitations

- The analysis covers only 200 customers. Findings describe this dataset and should not be generalized to a broader customer population without additional evidence.
- The near-zero correlation indicates little linear relationship between annual income and Spending Score in this dataset; it does not rule out other patterns.
- KMeans uses annual income (`annual_income_k`) and Spending Score (`spending_score`) as implemented in the notebook. The notebook applies `VectorAssembler` directly and does **not** scale or standardize these features before clustering.

## Reproducibility and attribution

This README documents the files and saved results currently present in the repository; it does not claim that the notebook has been executed or independently tested as part of this documentation update. The notebook uses relative paths, so run it from the project root as described above.

No source or license attribution for the dataset was found in the project files. Confirm the dataset's provenance, attribution requirements, and redistribution permissions before sharing it publicly.
