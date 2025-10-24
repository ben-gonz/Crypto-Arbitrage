# Triangular Arbitrage Paper Trader 🤑

This project implements a triangular arbitrage strategy for cryptocurrencies using real-time exchange rate data. Below is a step-by-step walkthrough of the program's workflow, designed to identify and simulate arbitrage opportunities through paper trading.
This was a final project for an Advanced Python Programming course at Utah State University. I cannot share the code (so my professor can continue giving this assignment out), but reach out to me if you are interested in seeing it.

## Workflow

### 1. **Initialization**
- Imports libraries for API requests, graph processing, and trading.
- Connects to a trading API in paper trading mode for simulated trades.
- Defines a set of cryptocurrencies and their tickers.
- Sets up a local directory for data storage.

### 2. **Fetch Exchange Rates**
- Retrieves real-time exchange rates for cryptocurrency pairs from a public API.
- Saves rates to a local file for processing.
- Handles API errors and exits if data is unavailable.

### 3. **Build Graph**
- Creates a directed graph with cryptocurrencies as nodes and exchange rates as weighted edges.
- Stores rate data in a timestamped CSV file.

### 4. **Find Arbitrage Opportunities**
- Explores all possible paths in the graph to identify arbitrage cycles.
- Calculates profit factors by multiplying rates along forward and reverse paths.
- Selects the path with the highest profit factor (>1) for trading.

### 5. **Simulate Trades**
- Executes simulated trades for the best path using the trading API.
- Buys and sells fixed amounts in USD along forward and reverse paths.
- Logs each trade and ensures positions are closed after each step.

### 6. **Output Results**
- Displays the best path, profit factor, trade history, and final balance in the terminal.
- Saves trade history and balance to a JSON file.
- Reports if no arbitrage opportunities are found.

## Example Output
![Screenshot](https://github.com/user-attachments/assets/fff99c51-c975-493d-885e-9956779af2f4)
