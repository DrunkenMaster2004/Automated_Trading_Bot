
# Trading Bot using MetaTrader5

This repository contains a Jupyter notebook that demonstrates how to set up and use the MetaTrader5 API for trading. The notebook includes steps for installation, initialization, logging in, and basic operations using MetaTrader5.

## Table of Contents
- [Installation](#installation)
- [Setup](#setup)
- [Usage](#usage)
- [Features](#features)

## Installation

To use this notebook, you need to have Python installed. The required library can be installed using pip:

```bash
pip install MetaTrader5
```

## Setup

1. **Clone the repository**:

    ```bash
    git clone https://github.com/yourusername/trading-bot.git
    cd trading-bot
    ```

2. **Open the Jupyter notebook**:

    ```bash
    jupyter notebook trading_bot_1.ipynb
    ```

3. **Install the MetaTrader5 package** (if not already installed):

    ```python
    pip install MetaTrader5
    ```

4. **Import the necessary libraries**:

    ```python
    import MetaTrader5 as mt
    from datetime import datetime
    ```

5. **Initialize the MetaTrader5 terminal**:

    ```python
    mt.initialize()
    ```

6. **Set up login credentials and server information**:

    ```python
    login = 51588762
    password = 'your_password'
    server = 'ICMarketsSC-Demo'
    ```

7. **Log in to your MetaTrader5 account**:

    ```python
    mt.login(login, password, server)
    ```

## Usage

Once logged in, you can perform various trading operations using MetaTrader5 API. Examples include:

- **Fetching account information**:
    ```python
    account_info = mt.account_info()
    print(account_info)
    ```

- **Placing a trade**:
    ```python
    symbol = "EURUSD"
    lot = 0.1
    point = mt.symbol_info(symbol).point
    price = mt.symbol_info_tick(symbol).ask
    deviation = 20
    request = {
        "action": mt.TRADE_ACTION_DEAL,
        "symbol": symbol,
        "volume": lot,
        "type": mt.ORDER_TYPE_BUY,
        "price": price,
        "sl": price - 100 * point,
        "tp": price + 100 * point,
        "deviation": deviation,
        "magic": 234000,
        "comment": "Python script open",
        "type_time": mt.ORDER_TIME_GTC,
        "type_filling": mt.ORDER_FILLING_IOC,
    }
    result = mt.order_send(request)
    print(result)
    ```

## Features

- Connect to MetaTrader5 account
- Fetch account information
- Place buy/sell orders
- Fetch market data and historical prices
- Manage trades and positions


