# Stellar Luminosity Regression

A compact, reproducible project that explores and models the relationship between a star’s **surface temperature** and its **luminosity** using **linear** and **polynomial regression**.

**Metaphor**: Imagine each star as a musical note and the temperature as the pitch; our goal is to learn the *score* that maps pitch to loudness (luminosity). The regression model is that score—allowing us to reproduce, predict, and understand the stellar symphony.

---

## Contents

* `01_part1_linreg_1feature.ipynb` — Linear regression using a single feature (temperature).
* `02_part2_polyreg.ipynb` — Polynomial regression to capture non‑linear relationships.

---

## Project Metadata

* **Author**: Juan Pablo Nieto Cortes
* **Course**: AREP
* **Date**: 2026‑01‑25
* **Dataset**: Pairs of *(temperature, luminosity)* (see notebooks for origin and preprocessing).
* **License**: MIT
* **Intended execution environment**: AWS SageMaker (see note below).

---

## Objective

To explain, experiment with, and compare simple regression models—linear and polynomial—for predicting a star’s luminosity from its temperature. The project emphasizes clarity, reproducibility, and interpretability rather than model complexity.

---

## Requirements

* Python **3.8+** (recommended)
* Jupyter (Notebook or Lab)
* Common scientific packages:

  * `numpy`
  * `pandas`
  * `matplotlib`
  * `scikit-learn`
  * `seaborn`
  * `notebook` / `jupyterlab`

> Creating a virtual environment is strongly recommended.

---

## Installation (Local)

1. Clone the repository:

```bash
git clone <repo-url>
cd stellar-luminosity-regression
```

2. Create and activate a virtual environment:

```bash
python -m venv venv
source venv/bin/activate
```

3. Install dependencies:

If a `requirements.txt` file is present:

```bash
pip install -r requirements.txt
```

Otherwise, install manually:

```bash
pip install numpy pandas matplotlib scikit-learn seaborn jupyterlab
```

---

## How to Run (Local)

1. Start Jupyter:

```bash
jupyter lab
```

2. Open and run the notebooks:

* `01_part1_linreg_1feature.ipynb` — step‑by‑step linear regression walkthrough.
* `02_part2_polyreg.ipynb` — polynomial regression experiments and visualizations.

3. Optional: run notebooks non‑interactively (headless execution):

```bash
jupyter nbconvert --to notebook --execute 01_part1_linreg_1feature.ipynb --ExecutePreprocessor.timeout=600
jupyter nbconvert --to notebook --execute 02_part2_polyreg.ipynb --ExecutePreprocessor.timeout=600
```

---

## AWS SageMaker – Execution Note

This project was **designed to be compatible with AWS SageMaker** and was initially intended to be executed there. Multiple attempts were made to upload and run the notebooks using standard SageMaker workflows (Notebook Instances and SageMaker Studio).

However, due to **environment and file‑upload limitations**, the notebooks could not be executed successfully within SageMaker during the available development window.

As a result:

* All analyses and results included in this repository were **executed and validated locally**.
* No changes to the code are required for SageMaker compatibility; the notebooks can be run in SageMaker once the environment or upload issues are resolved.

This limitation does **not** affect the correctness or reproducibility of the results.

---

## Running on AWS SageMaker

Typical workflow (once environment issues are resolved):

1. Create or start a SageMaker Notebook Instance or open SageMaker Studio.
2. Use a standard Python image/container.
3. Upload or clone the repository:

```bash
git clone <repo-url>
cd stellar-luminosity-regression
```

4. Open and run the notebooks from the SageMaker UI.
5. Stop the instance after use to avoid unnecessary charges.

---

## Technical Summary

* **Data**: pairs *(temperature, luminosity)* with basic cleaning and optional scaling.
* **Models**:

  * Linear regression (baseline).
  * Polynomial regression (configurable degree).
* **Metrics**:

  * Mean Squared Error (MSE).
  * Coefficient of determination (R²).
* **Visualizations**:

  * Scatter plots with fitted curves.
  * Residual analysis.

---

## Reproducibility

* Fixed random seeds where applicable (`random_state = 42`).
* Notebook outputs are deterministic given the same environment and inputs.

---

## Best Practices & Notes

* Polynomial degree should be selected carefully to avoid overfitting.
* Feature normalization improves numerical stability for higher‑degree polynomials.
* Simpler models are preferred for interpretability in this educational context.

---

## Recommended Project Structure (Optional)

```
stellar-luminosity-regression/
├── notebooks/
├── data/
├── results/
└── docs/
```

---

## Contributions & Contact

Contributions are welcome via issues or pull requests.
For questions or academic review, contact **Juan Pablo Nieto Cortes**.

---

## License

This project is licensed under the **MIT License**.
