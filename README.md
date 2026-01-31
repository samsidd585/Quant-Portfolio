# Quant-Portfolio
I’m Sameer Siddiqui, a rising senior at Indiana University Bloomington, focused on algorithmic trading and market microstrcuture in crypto markets. Here are strategies I have researched using OHLCV and Twitter data:

## Projects (Publishing Soon) 

### 1)Volume Weighted CSMOM strategy (Crypto)
**Goal:** Build on top off the findings of [Huang, Sangiorgi & Urquhart (2024)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4825389) by using coins with higher trading volumes and a CSMOM signal instead off TSMOM to develop a more robust Sharpe after TCOSTS.

**Universe:** Top 100 coins by marketcap with daily trading volume >1million on Binance Global excluding stablecoins. 

**Status:** Code with comments + full writeup publishing by 5th February 

### 2) Crypto Twitter Sentiment analysis
**Goal:** Evaluate whether tweets of liquid coins analysed using standard NLP add predictive power beyond price and volume.

**Universe:** BTC, ETH, XRP, and BNB

**Status:** Code with comments + full writeup publishing by 10th February

## Tools 
Python (pandas, numpy, statsmodel), Jupyter, Github

## In progress
**Event Driven Trading System:**

**Root Directory Breakdown:**

```text
EDS/
├── config/                     <-- Centralized Configuration
│   ├── main.yml                <-- Global settings (API keys, run modes, paths)
│   ├── risk.yml                <-- Portfolio limits (Max drawdown, position sizes)
│   └── universe.yml            <-- Trading universe definitions per strategy
│
├── results/                    <--  Stores logs, CSVs, and run artifacts
│
├── scripts/                    <-- The "Control Panel" (Entry Points)
│   ├── __init__.py
│   ├── kill_switch.py          <-- Emergency stop command
│   ├── liquidate.py            <-- Operator command to sell assets
│   ├── recon.py                <-- Runs the reconciliation tool
│   ├── run_backtest.py         <-- Launches a historical simulation
│   ├── run_live.py             <-- Launches the live trading engine
│   └── run_paper.py            <-- Launches paper trading
│
├── tradesys/                   <-- Main Library Package
│   ├── __init__.py
│   │
│   ├── core/                   <-- Central Nervous System
│   │   ├── __init__.py
│   │   ├── engine.py           <-- Event Loop (The Heart)
│   │   ├── events.py           <-- Event Class Definitions
│   │   └── model.py            <-- Shared Data Objects (Order, Position)
│   │
│   ├── data/                   <-- Data Feeds & Normalization
│   │   ├── __init__.py
│   │   ├── base.py             <-- DataHandler Interface
│   │   ├── backtest.py         <-- Historical CSV Loader
│   │   ├── live_gateway.py     <-- API Stream Handler (Polygon/Alpaca)
│   │   └── reference.py        <-- Static Data Master (Market Hours/Splits)
│   │
│   ├── strategy/               <-- Trading Logic (The Brain)
│   │   ├── __init__.py
│   │   └── base.py           <-- Strategy Interface
│   │
│   ├── portfolio/              <-- Risk & Order Management
│   │   ├── __init__.py
│   │   ├── manager.py          <-- Logic: Handles Signals & Updates State
│   │   ├── risk_rules.py     <-- Logic: Checks Limits (Leverage/Drawdown)
│   │   └── allocator.py       <-- Logic: Position Sizing (HRP/Kelly)
│   │
│   ├── execution/              <-- Broker Interaction
│   │   ├── __init__.py
│   │   ├── base.py             <-- Execution Interface
│   │   ├── backtest_execution.py <-- Simulated Fills
│   │   └── live_execution.py   <-- Real Broker Connection (Alpaca)
│   │
│   └── infra/                      <-- Operational Risk Manager
│       ├── __init__.py
│       ├── alerts.py            <-- Notifications (Telegram)
│       ├── controller.py     <-- System Commands
│       ├── recon.py            <-- Trade Reconciliation
│       └── watchdog.py     <-- Health Monitoring
│
├── .gitignore                    <-- Excludes results/ and config/secrets (if used)
├── README.md               <-- Project Documentation


