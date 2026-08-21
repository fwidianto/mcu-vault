# MCU Vault

MCU Vault is a completed personal prototype for organizing Medical Check-Up (MCU) records, structured health metrics, OCR-assisted data entry, trend visualization, and optional AI-generated explanations.

> **Project status:** maintenance-frozen portfolio prototype. This repository is not presented as an actively operated production service and contains no deployment pipeline.

## Scope

The application demonstrates how an unstructured health-document workflow can be turned into a searchable, structured longitudinal record using a small Flask application.

Implemented capabilities include:

- account registration and authentication;
- MCU record CRUD and file attachment;
- structured health metrics such as BMI, blood pressure, glucose, HbA1c, lipids, liver markers, and kidney markers;
- rule-based metric classification and trend visualization;
- side-by-side MCU comparison and CSV export;
- OCR-assisted extraction from PDF/image documents with a human review step before saving;
- optional AI summaries, comparisons, trend narratives, and metric explanations through configurable providers;
- demo-data generation for local exploration.

## Safety boundary

MCU Vault is a software/portfolio prototype, **not a medical device or clinical decision-support system**.

- Classifications and AI output are informational demonstrations only.
- The application must not be used to diagnose, treat, or replace professional medical judgment.
- OCR and AI output can be wrong and should be reviewed against the original source document.
- Do not use real confidential medical records in an unsecured demo environment.

## Architecture

```text
Flask application
├── authentication and record management
├── SQLAlchemy / SQLite data model
├── health-metric analytics
├── OCR extraction + field mapping
├── optional AI health-explanation layer
└── server-rendered HTML/CSS/JavaScript UI
```

Key directories:

- `app/` — application models, routes, services, utilities, and configuration
- `templates/` — server-rendered pages
- `static/` — styles, JavaScript, and local upload directory
- `tests/` — automated application, analytics, OCR, authentication, AI, and seed-data tests
- `scripts/` — local utilities such as demo-data generation
- `migrations/` — project migration utilities

## Local setup

Requirements:

- Python 3.9+
- pip
- Tesseract and Poppler only when exercising OCR against real files

```bash
git clone https://github.com/fwidianto/mcu-vault.git
cd mcu-vault
python -m venv .venv
```

Activate the environment, then install dependencies:

```bash
pip install -r requirements.txt
```

Copy `.env.example` to `.env` and replace the placeholder secret before running outside a disposable local environment.

Start the app:

```bash
python run.py
```

Default local URL:

```text
http://localhost:5000
```

## Optional AI configuration

AI functionality is optional. `.env.example` documents the supported configuration placeholders. The application should continue to function without an AI provider configured.

Never commit real provider keys to this repository.

## Demo data

The repository includes a local seed utility for generating fictional longitudinal records:

```bash
python scripts/seed_data.py
```

Use `--reset` only against a disposable local/demo database.

## Testing

Install pytest if it is not already available:

```bash
pip install pytest
```

Run the complete suite:

```bash
pytest -q
```

GitHub CI compiles the Python source and runs the real pytest suite on pull requests and `main`.

## Data and repository hygiene

The repository intentionally ignores:

- `.env` files;
- SQLite/database files;
- uploaded medical documents;
- logs, caches, virtual environments, and test coverage output.

Only fictional/demo data should be committed. Git history is retained as the development archive; old deployment experiments are intentionally not part of the active working tree.

## Maintenance state

No new product roadmap is active in this repository. Future work should reopen the project only for a concrete reason rather than continuing the former phase-by-phase expansion.

## License

No standalone license file is currently included. The repository should not imply a license grant that is not explicitly present.
