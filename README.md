# Triangular Arbitrage Paper Trader

This project implements a triangular arbitrage strategy for cryptocurrencies using real-time exchange rate data. Below is a step-by-step walkthrough of the program's workflow, designed to identify and simulate arbitrage opportunities through paper trading.
This was a final project for an Advanced Python Programming course at Utah State University. I cannot share the code (so my professor can continue giving this assignment out), but reach out to me if you are interested in seeing it.

## Workflow

### 1. **Setup and Initialization**
- **Load Dependencies**: The program imports necessary libraries for HTTP requests, file handling, graph creation, and trading API integration.
- **Configure API**: Connects to Alpaca's Trading API in paper trading mode using provided API keys to simulate trades without real funds.
- **Define Currencies**: Establishes a dictionary mapping cryptocurrency names (e.g., Bitcoin) to their tickers (e.g., BTC) for consistent data handling.
- **Set Up File System**: Creates a local `data` directory to store exchange rate data and trade results.

### 2. **Fetch Exchange Rates**
- **API Call**: Queries the CoinGecko API to retrieve real-time exchange rates for a predefined set of cryptocurrencies, covering all possible trading pairs (e.g., BTC/ETH, ETH/AAVE).
- **Error Handling**: Checks for API errors (e.g., rate limits) and exits gracefully if data cannot be retrieved.
- **Save Rates**: Writes fetched exchange rates to a local text file (`exchange_rates.txt`) for further processing.

### 3. **Build Directed Graph**
- **Graph Creation**: Constructs a directed graph using the NetworkX library, where:
  - Nodes represent cryptocurrencies (e.g., BTC, ETH).
  - Edges represent exchange rates between currency pairs, with weights corresponding to the rates.
- **Data Storage**: Saves exchange rate data to a timestamped CSV file in the `data` directory for record-keeping.

### 4. **Identify Arbitrage Opportunities**
- **Path Exploration**: Iterates through all possible paths in the graph using permutations of nodes to identify potential arbitrage cycles.
- **Profit Calculation**:
  - Computes the profit factor for each path by multiplying exchange rates along the forward path (e.g., BTC → ETH → AAVE) and the reverse path (e.g., AAVE → ETH → BTC).
  - A profit factor greater than 1 indicates a potential arbitrage opportunity.
- **Select Best Path**: Identifies the path with the highest profit factor for trade execution.

### 5. **Execute Simulated Trades**
- **Trade Logic**:
  - For the most profitable path (if profit factor > 1), executes simulated trades via Alpaca's API.
  - Trades are performed in USD, buying $20 worth of each cryptocurrency along the forward path and selling immediately to return to USD.
  - Repeats the process for the reverse path, skipping redundant trades.
- **Position Management**: Ensures all positions are sold after each trade to maintain a cash-based strategy and avoid wash trade errors.
- **Trade Logging**: Records each buy/sell action in a trade history log.

### 6. **Output and Reporting**
- **Console Output**: Displays the highest profit factor, forward and reverse paths, trade history, and final account balance in the terminal.
- **File Output**:
  - Saves trade history and final account balance to a `results.json` file.
  - Stores exchange rate data in timestamped CSV files for reference.
- **No Opportunities**: If no arbitrage opportunities are detected (profit factor ≤ 1), reports this to the console and saves an empty trade history.

## Notes
- The program operates in **paper trading mode** to simulate trades without financial risk.
- All data is sourced from CoinGecko’s public API, ensuring real-time exchange rates.
- Results are saved locally for transparency and further analysis.
- The workflow is designed to be robust, with error handling for API failures and trade execution issues.

## Example Output
![Screenshot](https://github.com/user-attachments/assets/fff99c51-c975-493d-885e-9956779af2f4)
