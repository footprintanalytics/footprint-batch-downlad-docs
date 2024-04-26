>
| column order | column name      | data type     | description                                                                                   | is_unique_key |
| ------------ | ---------------- | ------------- | --------------------------------------------------------------------------------------------- | ------------- |
| 1            | transaction_hash | varchar       | transaction_block_digest                                                                      | Y             |
| 2            | block_number     | bigint        | checkpoint                                                                                    | Y             |
| 3            | block_hash       | varchar       | digest of the checkpoint                                                                      |               |
| 4            | block_timestamp  | integer       | Transaction's block timestamp.                                                                |               |
| 5            | log_index        | integer       | There are multiple transfers in a transaction, and the index is intended to be a unique key.  | Y             |
| 6            | from_address     | varchar       | token sender acount                                                                           |               |
| 7            | to_address       | varchar       | token recipient acount                                                                        |               |
| 8            | token_address    | varchar       | coin_type,eg "0xc060006111016b8a020ad5b33834984a437aaa7d3c74c18e09a95d48aceab08c::coin::COIN" |               |
| 9            | token_symbol     | varchar       | eg USDT(can be null)                                                                          |               |
| 10           | amount_raw       | decimal(38,0) | transfers value                                                                               |               |
| 11           | value            | varchar       | transfers value, some value will exceed max int, use string type.                             |               |
| 12           | total_gas_fee    | bigint        | transaction total gas fee, same value as suiscan, doesn't split into each token transfers     |               |
| 13           | status           | varchar       | The status of the transaction_block_digest, the same in the sui_transaction_blocks            |
