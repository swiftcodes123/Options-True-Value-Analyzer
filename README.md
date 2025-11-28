# Options True Value Analyzer

A real-time options pricing and mispricing detection tool built with Python and Flask.

## Overview

This tool fetches live option chain data from the Schwab API, computes theoretical option values using the Black-Scholes model, calculates Greeks, and identifies contracts where market prices deviate from theoretical fair value. The system provides a web-based dashboard for analyzing potential trading inefficiencies.

## Features

- Live option chain data ingestion via Schwab API
- Black-Scholes pricing engine for calls and puts
- Greek calculations: Delta, Gamma, Theta, Vega, Rho
- Mispricing detection based on percentage deviation thresholds
- Web dashboard with sorting and filtering capabilities

## Technical Stack

Python, Flask, Pandas, NumPy, SciPy, Schwab API, HTML/CSS/JavaScript

## Installation
```bash
pip install -r requirements.txt
python app.py
```

Access the dashboard at http://localhost:5000

## Architecture
```
options_analyzer/
├── app.py              # Flask routes and server
├── pricing.py          # Black-Scholes engine and Greeks
├── schwab_api.py       # API integration
├── templates/
│   └── index.html
└── static/
    └── style.css
```

## Methodology

Uses the Black-Scholes formula to compute theoretical option prices:
```
C = S₀N(d₁) - Ke^(-rT)N(d₂)
P = Ke^(-rT)N(-d₂) - S₀N(-d₁)
```

Mispricing is flagged when the absolute difference between market price and theoretical price exceeds a configurable threshold.

## Use Case

This tool demonstrates quantitative modeling, financial engineering, API-driven data processing, and full-stack development skills relevant to fintech and quantitative finance roles.
