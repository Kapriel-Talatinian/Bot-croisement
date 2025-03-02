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
