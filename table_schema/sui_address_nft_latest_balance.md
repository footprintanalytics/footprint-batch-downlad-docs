> The type of table is `latest table` 
>>This table contains information about each wallet's holdings, such as the balance of each NFT.

| column order | column name                 | data type | description                                   | is_unique_key |
| ------------ | --------------------------- | --------- | --------------------------------------------- | ------------- |
| 1            | amount                      | double    | The number of tokens                          |               |
| 2            | block_number                | integer   | checkpoint                                    |               |
| 3            | block_timestamp             | integer   | Block timestamp where this transaction was in |               |
| 4            | chain                       | varchar   | Blockchain name                               | Y             |
| 5            | collection_contract_address | varchar   | object_type                                   | Y             |
| 6            | nft_token_id                | varchar   | object                                        | Y             |
| 7            | updated_at                  | integer   | The last updated timestamp                    |               |
| 8            | wallet_address              | varchar   | Wallet address                                | Y             |
