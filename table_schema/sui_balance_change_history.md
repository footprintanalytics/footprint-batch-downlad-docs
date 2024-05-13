> The type of table is `daily table` 

| column order | column name              | data type     | description                            | is_unique_key |
| ------------ | ------------------------ | ------------- | -------------------------------------- | ------------- |
| 1            | transaction_block_digest | varchar       | The digest of the queried transaction. | Y             |
| 2            | checkpoint               | bigint        | The checkpoint number.                 | Y             |
| 3            | time_stamp               | integer       | Transaction's block timestamp.         |               |
| 4            | address                  | varchar       | Owners/wallet address.                 | Y             |
| 5            | coin_type                | varchar       | The type of Coin.                      | Y             |
| 6            | amount                   | decimal(38,0) | Balance changes Amount.                |
