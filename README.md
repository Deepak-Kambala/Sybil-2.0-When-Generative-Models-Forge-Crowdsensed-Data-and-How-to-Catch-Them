# Generative Forgery of Crowdsensed Sensor Streams: A Preliminary Evaluation of Trust Defenses

PerCom 2027 Work-in-Progress experiment artifacts for evaluating crowdsensing defenses against generated sensor streams and a lightweight detector.

## Final deliverables

- `final/sybil2_crowdsensing.ipynb`: executed end-to-end notebook.
- `final/sybil2_percom_wip_results.tex` and `.pdf`: four-page WiP paper draft and rendered manuscript.
- `final/sybil2_project_end_to_end.docx`: detailed explanation from research idea through results and next steps.
- Figures and table fragments used by the LaTeX source are alongside it in `final/`.

## Results and reproducibility artifacts

`outputs_india_aqi/` contains the per-seed main results, three sweep CSVs, summary metadata, exported tables/figures, progress logs, and a `global_scaler_reference/` run retained for the preprocessing audit. The corrected primary run fits channel scaling statistics on the first 60% of the timeline only.

The executed configuration is `MODE="india_aqi"`, `CITY="Delhi"`, `FAST=False`, `SEEDS=[0,1,2]`. The summary records PyTorch enabled and the feature-extraction latency. Results are preliminary: generated attackers are evaluated over one city's recorded traces and one temporal holdout.

## Dataset setup

The hourly Air Quality Data in India file is large and is intentionally not stored in Git. Download the Kaggle dataset **Air Quality Data in India (2015-2020)** by rohanrao, then place these files at:

```text
data/air-quality-data-in-india/station_hour.csv
data/air-quality-data-in-india/stations.csv
data/air-quality-data-in-india/station_day.csv   # optional for this hourly experiment
```

The small `stations.csv` metadata file is included. Dataset files are ignored by Git so local copies remain untracked. Alternatively, set `CFG["INDIA_DIR"]` in the notebook to the directory containing the CSV files.

## Run

Use Python 3.10 or newer with NumPy, pandas, SciPy, scikit-learn, matplotlib, PyTorch (CPU), and Jupyter/nbconvert installed. From the repository root, execute:

```bash
jupyter nbconvert --to notebook --execute --inplace --ExecutePreprocessor.timeout=-1 final/sybil2_crowdsensing.ipynb
```

Do not enable `FAST` for paper results. The notebook exports results under `outputs_india_aqi/`.
