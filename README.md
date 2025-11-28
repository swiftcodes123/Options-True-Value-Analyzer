📈 Options True Value Analyzer
A real-time options pricing and mispricing detection tool that compares theoretical values to live market prices.
Show Image
Show Image
Show Image🎯 OverviewThe Options True Value Analyzer is a lightweight analytical tool that identifies potentially mispriced options contracts by computing theoretical prices using the Black–Scholes model and comparing them against live market data from the Schwab API.This project demonstrates practical applications of financial engineering, quantitative modeling, and full-stack development — perfect for roles in quantitative finance, data engineering, and fintech.✨ Features
🔴 Live Option Chain Data — Fetches real-time bid/ask, volume, and implied volatility
📊 Black–Scholes Pricing Engine — Computes theoretical fair values for calls and puts
🧮 Greek Calculations — Delta, Gamma, Theta, Vega, and Rho
🎯 Mispricing Detection — Flags contracts where market price deviates significantly from theoretical value
🌐 Interactive Dashboard — Clean web interface for searching tickers and analyzing results
🛠️ Tech Stack
Backend: Python, Flask
Data Processing: Pandas, NumPy, SciPy
API Integration: Schwab API
Frontend: HTML5, CSS3, Vanilla JavaScript
Deployment: Lightweight Flask server
📦 InstallationPrerequisites
Python 3.8 or higher
pip package manager
Schwab API credentials (optional for demo mode)
Setupbash# Clone the repository
git clone https://github.com/yourusername/options-true-value-analyzer.git
cd options-true-value-analyzer

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Configure API credentials (create .env file)
echo "SCHWAB_API_KEY=your_api_key" > .env
echo "SCHWAB_API_SECRET=your_api_secret" >> .env

# Run the application
python app.pyVisit http://localhost:5000 in your browser.🚀 UsageBasic Workflow
Launch the application

bash   python app.py
Enter a ticker symbol (e.g., AAPL, SPY, TSLA)

View option chain with calculated metrics

Sort by mispricing % to identify potential opportunities
API Endpointsbash# Get option chain for a ticker
GET /api/options?ticker=AAPL

# Get specific contract analysis
GET /api/options/analyze?ticker=AAPL&strike=150&expiry=2025-01-17&type=call📊 Dashboard PreviewMain InterfaceThe dashboard displays a comprehensive option chain with the following columns:ColumnDescriptionStrikeOption strike priceTypeCall or PutExpiryExpiration dateMarket PriceCurrent bid-ask midpointTheoretical PriceBlack–Scholes fair valueMispricing %Deviation from fair valueDelta (Δ)Price sensitivityGamma (Γ)Delta sensitivityTheta (Θ)Time decayVega (ν)Volatility sensitivityRho (ρ)Interest rate sensitivityColor Coding:

🟢 Green: Underpriced (market < theoretical)
🔴 Red: Overpriced (market > theoretical)
🟡 Yellow: Fair value (within threshold)
🧮 MethodologyBlack–Scholes FormulaThe theoretical option price is calculated using:Call Option:
C = S₀N(d₁) - Ke^(-rT)N(d₂)Put Option:
P = Ke^(-rT)N(-d₂) - S₀N(-d₁)Where:
d₁ = [ln(S₀/K) + (r + σ²/2)T] / (σ√T)
d₂ = d₁ - σ√TGreek Calculations
Delta (Δ): ∂V/∂S — Rate of change of option price with respect to underlying price
Gamma (Γ): ∂²V/∂S² — Rate of change of delta
Theta (Θ): ∂V/∂t — Time decay
Vega (ν): ∂V/∂σ — Sensitivity to volatility
Rho (ρ): ∂V/∂r — Sensitivity to interest rates
📁 Project Structureoptions_analyzer/
│
├── app.py                 # Flask application & routes
├── pricing.py             # Black–Scholes engine & Greeks
├── schwab_api.py          # API integration wrapper
├── utils.py               # Helper functions
│
├── templates/
│   ├── index.html         # Main dashboard
│   └── layout.html        # Base template
│
├── static/
│   ├── css/
│   │   └── style.css      # Custom styles
│   ├── js/
│   │   └── main.js        # Dashboard interactivity
│   └── images/
│       └── logo.png
│
├── tests/
│   ├── test_pricing.py
│   └── test_api.py
│
├── requirements.txt       # Python dependencies
├── .env.example          # Environment variables template
├── .gitignore
└── README.md🧪 TestingRun the test suite:bash# Run all tests
pytest

# Run with coverage
pytest --cov=.

# Run specific test file
pytest tests/test_pricing.py🔧 ConfigurationEnvironment VariablesCreate a .env file:bashSCHWAB_API_KEY=your_api_key
SCHWAB_API_SECRET=your_api_secret
RISK_FREE_RATE=0.05
MISPRICING_THRESHOLD=0.05CustomizationModify config.py to adjust:

Risk-free rate
Mispricing detection threshold
API polling frequency
Calculation precision
📈 Example OutputTicker: AAPL (Current Price: $175.43)
Expiry: 2025-03-21

Strike | Type | Market | Theoretical | Mispricing | Delta
-------|------|--------|-------------|------------|-------
170.00 | Call | $8.25  | $7.82       | +5.5%      | 0.62
175.00 | Call | $5.10  | $5.45       | -6.4%      | 0.51
180.00 | Call | $2.95  | $3.21       | -8.1%      | 0.38
