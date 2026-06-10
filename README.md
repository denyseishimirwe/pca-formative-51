# PCA from Scratch — African Development Indicators

**Course:** Advanced Linear Algebra — Formative 1 (Principal Component Analysis)
**Peer Pair 51:** Denyse & Divine

Principal Component Analysis implemented **from scratch in NumPy** (no `scikit-learn`, no
`pandas`) on socio-economic indicators for African countries.

## Dataset

UN *Country Profile* indicators, filtered to the **56 African countries**.

- **Source columns:** 50 (we select 12 thematic numeric features + the categorical `Region`)
- **Missing values:** present in the raw file as `...`, `-99`, `~0.0` — handled by mean imputation
- **Non-numeric column:** `Region` (EasternAfrica, MiddleAfrica, NorthernAfrica, SouthernAfrica,
  WesternAfrica) — label-encoded

The 12 features describe:

- **Economic activity** — GDP per capita, GDP growth, agriculture / industry / services share of
  GVA, unemployment, internet usage
- **Population pressure** — population density, population growth, urbanisation, fertility rate,
  infant mortality

## What the notebook does

1. **Load & clean** — download data, filter to Africa, parse missing values, impute, encode `Region`
2. **Standardize** — z-score each feature (mean 0, std 1)
3. **Covariance matrix** — relationships between features
4. **Eigendecomposition** — `np.linalg.eigh` (symmetric solver)
5. **Sort** — eigenvalues/eigenvectors in descending order
6. **Explained variance** — dynamic component selection (90% threshold → 8 components) + scree plot
7. **Project** — reduce 12 features → 8 components
8. **Visualize** — before/after PCA scatter, coloured by region

**Task 3** benchmarks the optimization (symmetric `eigh` and `svd` vs. the general `eig`).

## Tooling note (re: "numpy only")

All PCA mathematics uses **NumPy only**. The Python standard library (`csv`, `urllib`) is used purely
to read the CSV file, and `matplotlib` purely for the required plots. No `sklearn`, no `pandas`.

## How to run

Open `PCA_Formative_1_51.ipynb` in Google Colab or Jupyter and run all cells
(**Runtime → Run all**). The notebook downloads its data automatically, so no manual upload is needed.

## Dataset file

`african_country_profile.csv` — the dataset used, filtered to the 56 African countries
(`Country`, `Region`, and the 12 features). The original missing values (`...`, `-99`) are
preserved, so the file still reflects the raw data before imputation. The notebook downloads the
full source from GitHub automatically, so this CSV is included as a supporting copy of the data.

## Files

- `PCA_Formative_1_51.ipynb` — the completed notebook
- `PCA_Formative_1_51.pdf` — PDF export of the notebook
- `african_country_profile.csv` — the dataset (56 African countries, 14 columns, with missing values)
- `Contribution_Sheet_Pair51.pdf` — member contributions
- `PCA_Formative_1_Pair51_Combined.pdf` — notebook + contribution sheet merged into one PDFdataset
- 
