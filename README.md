# Stellar Luminosity Regression

A collection of notebooks to explore and model the relationship between a star's temperature and its luminosity using linear and polynomial regression.

Metaphor: Imagine each star as a musical note and the temperature as the pitch; our goal is to learn the score that maps pitch to loudness (luminosity). The model is the score that allows us to reproduce, predict, and understand the stellar symphony.

## Contents
- `01_part1_linreg_1feature.ipynb`: Linear regression using a single feature (temperature).
- `02_part2_polyreg.ipynb`: Polynomial regression to capture non-linear relationships.

## Metadata
- Author: Juan Pablo Nieto Cortes
- Course: AREP
- Date: 2026-01-25
- Dataset: Pairs of (temperature, luminosity). See notebooks for origin and preprocessing.
- License: MIT (adjust as needed)
- Execution environment: AWS SageMaker (used for development and testing)

## Objective
Explain, experiment with, and compare simple models (linear and polynomial) to predict a star's luminosity from its temperature. Provide reproducible code in notebooks and guides to run locally and on AWS.

---

## Requirements
- Python 3.8+ recommended
- Jupyter (Lab or Notebook)
- Common packages: `numpy`, `pandas`, `matplotlib`, `scikit-learn`, `seaborn`, `notebook`.

Creating a virtual environment is recommended before installing dependencies.

## Installation (local)
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

3. Install dependencies (if a `requirements.txt` exists):

```bash
pip install -r requirements.txt
```

If no `requirements.txt` is present, install packages manually:

```bash
pip install numpy pandas matplotlib scikit-learn seaborn jupyterlab
```

## How to run (local)
- Start Jupyter Lab/Notebook:

```bash
jupyter lab
```

- Open the notebooks:
	- `01_part1_linreg_1feature.ipynb` — step-by-step linear regression walkthrough.
	- `02_part2_polyreg.ipynb` — polynomial regression experiments and visualizations.

- To run the notebooks non-interactively (headless):

```bash
jupyter nbconvert --to notebook --execute 01_part1_linreg_1feature.ipynb --ExecutePreprocessor.timeout=600
jupyter nbconvert --to notebook --execute 02_part2_polyreg.ipynb --ExecutePreprocessor.timeout=600
```

## How to run on AWS (SageMaker)
This project uses AWS SageMaker for development and testing. The workflow is: start the notebook instance (or Studio session with the chosen container), upload the notebooks, run them, then stop the instance to avoid incurring costs.

Steps:
1. Create or start a SageMaker Notebook Instance (or open SageMaker Studio).
2. Choose a suitable image/container or use the default Python image. If you need a custom container, configure it in SageMaker Studio or via an image lifecycle configuration.
3. Upload the notebooks:

```bash
# from the instance terminal or local machine (inside environment)
git clone <repo-url>
cd stellar-luminosity-regression
```

Or use the SageMaker file upload UI to upload `01_part1_linreg_1feature.ipynb` and `02_part2_polyreg.ipynb`.

4. Open and run the notebooks interactively in the SageMaker UI.

5. When finished, stop the Notebook Instance (important to avoid charges):

 - From the AWS Console: go to SageMaker > Notebook instances, select your instance and click `Stop`.
 - Or using AWS CLI:

```bash
aws sagemaker stop-notebook-instance --notebook-instance-name <your-notebook-name>
```

6. To restart later, use `Start` in the Console or:

```bash
aws sagemaker start-notebook-instance --notebook-instance-name <your-notebook-name>
```

Notes:
- Uploading notebooks, running analyses, and then stopping the instance is the recommended flow to minimize costs. Do not `Terminate` the instance unless you want to delete it permanently.
- If you use SageMaker Studio, shut down user apps/sessions when done; Studio resources may be billed differently — stop kernels and user apps from the Studio UI.
- If you want, I can add a `sagemaker-setup.md` file with exact console clicks, IAM minimal policy template, and a lifecycle script to pull a custom Docker image.

### Screenshots / Placeholder for AWS images
Place your screenshots in `docs/images/` and replace the filenames below.

![EC2 - Launch instance](docs/images/aws-ec2-1.png)
*Figure 1 — EC2 instance launch*

![EC2 - Setup environment](docs/images/aws-ec2-2.png)
*Figure 2 — Installing and running Jupyter*

![SageMaker - Notebook](docs/images/aws-sagemaker-1.png)
*Figure 3 — Notebook in SageMaker*

> Security note: Avoid exposing Jupyter directly to the public internet without strong authentication; prefer SSH tunnels or authenticated proxies.

## Technical summary
- Data: pairs (temperature, luminosity). Preprocessing: cleaning and scaling where applicable.
- Models: simple linear regression (baseline) and polynomial regression (configurable degree) to capture curvature.
- Metrics: MSE (mean squared error), R².
- Visualizations: scatter plots with fitted curves and residual analysis.

## Reproducibility
- Set random seeds in the notebooks for reproducible results (`random_state=42`).
- Save outputs (figures, metrics) to a `results/` folder when automating runs.

## Best practices and tips
- Experiment with polynomial degree and validate with `train_test_split` or `cross_val_score`.
- Normalize/standardize features when using high-degree polynomials to improve numerical stability.

## Recommended project layout (optional)
- `notebooks/` — organized notebooks (currently in project root).
- `data/` — datasets (if included).
- `docs/images/` — screenshots for README and docs.

## Contact & contributions
If you want to improve the project, open an issue or a pull request. For questions, contact Juan Pablo Nieto Cortes.

## License
This project is licensed under the MIT License — adjust as you prefer.

---

If you want, I can:
- Add a `requirements.txt` based on the current environment.
- Create the `docs/images/` directory and add placeholder images.
- Add a `sagemaker-setup.md` with detailed SageMaker setup steps.

Tell me which of these you'd like me to add next.