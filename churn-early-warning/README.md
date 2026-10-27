# B2B Churn Early Warning System

A local Python application for exploring customer churn risk, revenue impact,
retention recommendations, customer journeys, and prediction explanations.
It includes a Dash dashboard, a FastAPI API, and scripts for scoring and
monitoring customers.

## Features

- Interactive dashboard with overview, risk, business impact, prescriptions,
  journey analysis, and explainability views
- REST API for predictions, recommendations, explanations, and system metrics
- SQLite database with sample customer and prediction data
- Model scoring and monitoring scripts

## Requirements

- Python 3.11 or newer
- Windows PowerShell, Command Prompt, macOS Terminal, or Linux shell

## Run locally

From the project directory, create and activate a virtual environment, then
install the project dependencies:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

In Command Prompt, activate the environment with:

```bat
.venv\Scripts\activate.bat
```

On macOS or Linux, use:

```bash
source .venv/bin/activate
```

Start the dashboard:

```bash
python run.py
```

Open [http://127.0.0.1:8050](http://127.0.0.1:8050). Stop it with `Ctrl+C`.

## Run the API locally

Open another terminal in the project directory, activate the same virtual
environment, and run:

```bash
python src/api.py
```

The API is available at [http://127.0.0.1:8000](http://127.0.0.1:8000), with
interactive documentation at [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs).

## Run the prediction pipeline

Run the scoring pipeline once to update predictions in the local SQLite
database:

```bash
python src/scheduler.py once
```

To keep the daily scheduler running in a terminal:

```bash
python src/scheduler.py
```

The dashboard and API read from `data/churn_system.db`. Keep the pipeline
running separately if you want it to refresh predictions automatically.

## Project layout

```text
data/                   Sample input data and SQLite database
models/                 Trained churn model
notebooks/              Exploratory analysis and model development
src/app.py              Dash dashboard
src/api.py              FastAPI application
src/scheduler.py        Scoring pipeline and daily scheduler
run.py                  Local dashboard startup script
requirements.txt        Local dependency entry point
requirements_full.txt   Full dashboard, API, and ML dependencies
```
