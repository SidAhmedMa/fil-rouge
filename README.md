# Fil Rouge — Actuarial Data Science Masterclass

A through-line project: a governed data layer, an actuarial provisioning
engine, AI studies, a domain agent, and an automated dashboard — all
reproducible, documented, and audit-ready.

## Setup
    python -m venv .venv && source .venv/bin/activate
    pip install -e ".[dev]"
    pytest -q

## Docs
    mkdocs serve   # then open http://127.0.0.1:8000
