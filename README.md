# Options-True-Value-Analyzer
Options True Value Analyzer

A real-time mispricing detector that compares theoretical option values to live market prices.

🔍 Overview

The Options True Value Analyzer is a lightweight analytical tool that pulls live option chain data, computes theoretical pricing using the Black–Scholes model, calculates Greeks, and identifies potential mispriced contracts.

It’s built intentionally simple while still demonstrating:

financial modeling

API integration

data transformation

full-stack presentation

real-time analytics

✨ Features

Live Option Chain Fetching
Uses the Schwab API to pull current bid/ask, implied volatility, volume, and greeks if provided.

Black–Scholes Pricing Engine
Calculates:

theoretical fair value

Δ, Γ, Θ, Vega, ρ

implied mispricing %

Mispricing Detector
Flags contracts where |market_price – theoretical_price| exceeds threshold.

Web Dashboard
Simple Flask frontend to:

search a ticker

view its option chain

sort by mispricing

highlight outliers
