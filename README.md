## About the project

This Jupyter notebook sets up a comprehensive modular framework for building and backtesting 
quantitative trading strategies. It's designed to handle all key stages of a data-driven investment workflow.

## 1. Environment and Utilities
The notebook begins by establishing a robust and reproducible environment. It automatically detects if it's running in a Google Colab or local environment and configures the necessary project directory structure (e.g., algotrading, cache, results). It also initializes a flexible, level-based logging system to track the progress and diagnose issues throughout the process. A utility script is included to explore the contents of the stock_universe directory, providing a summary of the number of tickers in each file and identifying any duplicates.

## 2. Strategy Definition
Two core classes, EURStrategyConfig and DynamicConfigurationScanner, work together to define and manage trading strategies. The EURStrategyConfig dataclass stores all key strategy parameters, including factor_weights, portfolio_size, and various risk limits like max_position_size and max_country_exposure. It includes methods to validate that factor weights sum to 1.0 and provides an easy way to add or remove factors while automatically rebalancing the weights. The DynamicConfigurationScanner acts as a factory, offering pre-configured strategies like momentum_focused or balanced_multi_factor to simplify strategy creation.

## 3. Currency Conversion

The EURStandardCurrencyConverter class is a crucial component for handling global markets. It sets EUR as the base currency and provides a comprehensive system for currency conversion. It can automatically detect a stock's currency from its country of origin or its yfinance ticker suffix. The class fetches real-time and historical FX rates from yfinance to accurately convert all financial metrics (e.g., market cap, price, volume) to EUR, ensuring a fair, apples-to-apples comparison of stocks from different countries. To ensure reliability, it includes fallback rates and a caching mechanism to avoid redundant API calls.

## 4. System Functionality and Testing

The notebook includes a comprehensive test suite to ensure the stability and correctness of the strategy and currency components. It tests:

    Strategy Configuration: Verifies that EURStrategyConfig and DynamicConfigurationScanner work as expected, including weight validation, adding/removing factors, and pre-configured strategies.

    Currency Converter: Confirms that currency detection, real-time fetching, and historical conversions are accurate and robust, with demonstrations using sample tickers from the included stock universe files. It also checks caching performance to ensure the system can efficiently handle a large number of tickers.

The output of these tests shows a 100% success rate, indicating that the foundational components of the framework are fully functional and ready to be integrated with further stages, such as a stock data reader, a factor calculator, and a backtesting engine.


Version: 1.0
Status: Ongoing / will update soon
