# Automated Signal Bot using Telegram and Technical Indicators

## Overview
This project implements an automated Signal bot that retrieves financial data from Yahoo Finance, calculates key technical indicators, and sends  signals via Telegram. The bot continuously monitors predefined assets at different timeframes to detect potential trading opportunities.
multiple symbols and timeframes are supported regarding your cpu and how much ram you got
## Features
- Fetches real-time financial data from Yahoo Finance.
- Calculates key technical indicators:
  - **ADX & ADXR** (Average Directional Index)
  - **MACD** (Moving Average Convergence Divergence)
  - **COG** (Center of Gravity)
- Detects buy/sell signals based on indicator crossovers.
- Sends alerts to a Telegram chat when a signal is detected.
- Runs in a continuous loop with periodic data updates.

```mermaid
graph TD;
    A[Start] -->|Main Loop| B[Loop through SYMBOLS];
    B -->|Loop through TIMEFRAMES| C[Get Data];
    C --> D{Data Available?};
    D -->|Yes| E[Calculate Indicators];
    D -->|No| B;
    E --> F[Check Signals];
    F -->|Signal Detected?| G{Yes};
    G --> H[Send Telegram Message];
    G --> I[Print Message];
    H --> J[Wait 10s];
    I --> J;
    J --> B;
    F -->|No| J;
    B -->|All symbols/timeframes checked| A;

    subgraph Functions
        C -->|Calls| get_data;
        E -->|Calls| calculate_indicators;
        F -->|Calls| check_signals;
        H -->|Uses| bot.send_message;
    end
