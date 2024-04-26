> 	This table contains information about each wallet's holdings, such as the balance of each token.
>
| column order | column name    | data type | description                                                                                   | is_unique_key |
| ------------ | -------------- | --------- | --------------------------------------------------------------------------------------------- | ------------- |
| 1            | amount         | double    | The number of tokens                                                                          |               |
| 2            | amount_raw     | varchar   | The raw number of tokens                                                                      |               |
| 3            | block_number   | integer   | checkpoint                                                                                    |               |
| 4            | chain          | varchar   | Blockchain name                                                                               | Y             |
| 5            | token_address  | varchar   | coin_type,eg "0xc060006111016b8a020ad5b33834984a437aaa7d3c74c18e09a95d48aceab08c::coin::COIN" | Y             |
| 6            | token_symbol   | varchar   | The symbol of the token                                                                       |               |
| 7            | updated_at     | integer   | The last updated timestamp                                                                    |               |
| 8            | wallet_address | varchar   | Wallet address                                                                                | Y             |
