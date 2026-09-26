# MastiPredict — AI-Based Early Forecasting of Bovine Mastitis-Related Risk

MastiPredict is a research-oriented software platform for animal-wise early forecasting of bovine mastitis-related risk using multimodal IoT data, edge processing, machine learning, and an interactive dashboard.

## Research Direction

> Does reliability-aware multimodal fusion of wearable, milk, and environmental signals improve animal-wise longitudinal forecasting of future mastitis-related risk compared with single-modality approaches?

The initial research configurations are milk-only, milk + wearable, milk + environment, all modalities, and reliability-aware multimodal fusion.

## Architecture

```text
Wearable / Milking / Environment Nodes
              |
         Wi-Fi / MQTT
              v
      Raspberry Pi Edge Gateway
              |
   SQLite -> Validation -> Baseline
              |
       Feature Engineering
              |
       ML Forecasting
              |
       7-day / 14-day Risk
              |
          Dashboard
              |
   Farmer / Veterinarian
```

## Software Stack

- Python, Pandas, NumPy, SciPy
- Scikit-learn, XGBoost, Joblib
- Paho MQTT, SQLAlchemy, SQLite
- Flask / Streamlit / Plotly
- ESP32 firmware under `firmware/`

## Installation

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd MastiPredict-AI-Mastitis-Forecasting
py -m venv .venv
.venv\\Scripts\\activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Data and ML Pipeline

```text
Raw telemetry -> cleaning/synchronization -> individual-animal baseline
-> trends/rolling statistics/cross-sensor features -> ML
-> 7-day and 14-day future-risk estimates
```

Evaluation will include precision, recall/sensitivity, specificity, F1, ROC-AUC, PR-AUC, and calibration. The 7-day and 14-day horizons are research targets and are not pre-validated clinical claims.

## Data Safety

Do not commit private farm information, veterinary records containing personal information, credentials, API keys, production databases, or non-shareable datasets.

## Repository Structure

```text
src/mastipredict/   # Python application modules
firmware/            # ESP32 software
data/                # sample/local data structure
experiments/         # ablation and forecasting experiments
docs/                # architecture, API, database, research
tests/               # automated tests
```

## License

This initial repository uses the MIT License as a software-license template. Confirm institutional ownership, research/IP rules, and third-party licensing before public or commercial release.

## Disclaimer

MastiPredict is an engineering/research decision-support prototype, not an automated veterinary diagnostic system. Model risk is not a clinical diagnosis.
