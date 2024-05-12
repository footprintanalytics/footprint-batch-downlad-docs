> The type of table is `silver/gold daily table` 
>> This table can be used to analyze the daily indicators (include price,trade volume in 24 hour,current market capitalization,etc ) of the token.

| column order | column name             | data type | description                                         | is_unique_key |
| ------------ | ----------------------- | --------- | --------------------------------------------------- | ------------- |
| 1            | on_date                 | date      | The date of the recorded data.                      | Y             |
| 2            | token_slug              | varchar   | Unique identifier for the token within Footprint    | Y             |
| 3            | protocol_slug           | varchar   | Unique identifier for the protocol within Footprint |               |
| 4            | token_symbol            | varchar   | The symbol of token, eg: "WBTC"                     |               |
| 5            | token_name              | varchar   | The name of token, eg: "Wrapped BTC"                |               |
| 6            | price                   | double    | The price of the token.                             |               |
| 7            | high                    | double    | The highest price during the day.                   |               |
| 8            | low                     | double    | The lowest price during the day.                    |               |
| 9            | close                   | double    | The closing price of the day.                       |               |
| 10           | circulating_supply      | double    | The amount of the token in circulation.             |               |
| 11           | fully_diluted_valuation | double    | The fully diluted valuation.                        |               |
| 12           | market_cap              | double    | The market capitalization.                          |               |
| 13           | max_supply              | double    | The maximum supply of the token.                    |               |
| 14           | total_supply            | double    | The total supply of the token.                      |               |
| 15           | trading_vol_24h         | double    | The trading volume in the last 24 hours.            |
