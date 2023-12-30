# Crypocurrency Strategy Backtesting

## Project Overview

This project is a Python-based implementation for retrieving, analyzing, and backtesting cryptocurrency data. The code is organized into several classes, each serving a specific purpose. The main functionalities include fetching cryptocurrency information from the CoinGecko API and historical prices from the Binance API, performing basic data analysis, and implementing a backtesting framework for trading strategies on a cryptocurrency index made from a tag of cryptocurrency.

## Requirements

Make sure you have the following Python packages installed:

- `pycoingecko`
- `python-binance`
- `pandas`
- `matplotlib`
- `numpy`
- `requests`

## Usage

1. **Get Cryptocurrency Data:**
   - `get_crypto_list()`: Retrieves a list of all cryptocurrencies.
   - `get_tag_list()`: Retrieves the list of cryptocurrency categories.
   - `get_crypto_from_tag(tag_id: str)`: Retrieves the list of cryptocurrencies for a given category.
   - `get_historical_prices(params: Dict)`: Retrieves historical prices of a cryptocurrency from Binance.

   ```python
   # Example
   data = GetData()
   crypto_list = data.get_crypto_list()
   tag_list = data.get_tag_list()
   crypto_info = data.get_crypto_from_tag('analytics')
   params = {'symbol': 'BTC', 'start_date': datetime(2022, 1, 1), 'end_date': datetime(2023, 1, 1)}
   historical_prices = data.get_historical_prices(params)
   ```

2. **Data Analysis:**
   - `Analyse` class provides methods for calculating descriptive statistics and displaying graphs.

   ```python
   # Example
   price = historical_prices['close'].astype(float)
   print(Analyse.statistique(price))
   Analyse.graphique(price)
   print(Analyse.financière(price))
   ```

3. **Backtesting:**
   - `Backtester` is an abstract class for backtesting trading strategies. The `Indice` class is herited from it and allows to create an Index or to use one for testing a strategy on it..

   ```python
   # Example
   inputs = {'start_date': datetime(2022, 1, 1), 'end_date': datetime(2023, 1, 1), 'theme': 'dog-themed-coins', 'strategie': 'Ponderation constante', 'parametres': {'ponderation': [0.95, 0.05], 'composition':   ['doge', 'shib'], 'capital': 1000, 'ponderation_method': 'random'}}
   S1 = Indice(inputs)
   results = S1.backtest()
   ```

4. **Trading Strategies:**
   - `Strategie` class provides static methods for implementing trading strategies used in the Indice class.

   ```python
   # Example
   prices, positions, ponderations = Strategie.strategie1(prices, capital, composition, ponderation)
   ```

## Additional Notes

- The code is designed to handle errors and provides informative error messages.
- The project uses Python 3.9.17.
- The project covers most parts of the lectures with the use of class instances, class methods, singleton, factory, abstract methods, static classes and methods, herited classes ...
