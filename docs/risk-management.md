# Risk Management

The risk management subsystem monitors all open positions and ensures that trading remains within configured limits.
It works alongside your strategy to prevent excessive exposure and helps to safeguard trading capital.

## Overview

The module keeps track of every position that the bot opens. Before entering a new trade it checks the currently allocated risk and compares it to your configured limits. When the limits would be exceeded, the trade is rejected and a warning is logged.

## Position monitoring

Each active trade is continuously observed. The subsystem records the size and current profit of every position so that the total exposure is known at all times. This information is used to calculate the cumulative risk for all markets.

## Enforcing limits

Risk parameters can be configured in the bot's configuration file. Typical settings include the maximum number of open positions or the allowed percentage of your balance that may be at risk. When the running trades exceed these values, new trades are blocked until exposure falls below the limits.

Example configuration snippet:

```json
"risk_management": {
    "max_open_positions": 5,
    "max_total_risk": 0.2
}
```

With this setup the bot will never hold more than five trades simultaneously and no more than twenty percent of the available balance will be used across all positions.

## Usage

Enable the subsystem by adding the `risk_management` section to your configuration. Once active it operates automatically and requires no further interaction. It is compatible with dry-run and live trading alike.

