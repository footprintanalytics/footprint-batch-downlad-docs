> The type of table is `daily table` 
>> This table contains the information of the NFT sales transactions traded only on marketplaces.

| column order | column name                      | data type | description                                                              | is_unique_key |
| ------------ | -------------------------------- | --------- | ------------------------------------------------------------------------ | ------------- |
| 1            | chain                            | varchar   | Blockchain name                                                          | Y             |
| 2            | collection_contract_address      | varchar   | object_type                                                              | Y             |
| 3            | block_number                     | bigint    | checkpoint                                                               | Y             |
| 4            | transaction_hash                 | varchar   | transaction_block_digest                                                 | Y             |
| 5            | log_index                        | varchar   | The index position in the events of transaction. => sui_events.event_seq | Y             |
| 6            | internal_index                   | varchar   | The unique item index for multiple NFT transactions in a single event.   | Y             |
| 7            | block_timestamp                  | integer   | Block timestamp where this transaction was in                            | Y             |
| 8            | buyer_address                    | varchar   | Wallet address of the buyer                                              |               |
| 9            | seller_address                   | varchar   | Wallet address of the seller                                             |               |
| 10           | marketplace_contract_address     | varchar   | Marketplace contract address                                             | Y             |
| 11           | amount_currency_contract_address | varchar   | Token address of amount_currency                                         |               |
| 12           | nft_token_id                     | varchar   | object                                                                   | Y             |
| 13           | number_of_nft_token_id           | double    | The number of nfts transacted in the transaction                         |               |
| 14           | amount                           | double    | The number of tokens transferred                                         |               |
| 15           | trade_type                       | varchar   | Trade type (single/bundle/batch)                                         |               |
| 16           | amount_currency                  | varchar   | Aamount currency                                                         |               |
| 17           | marketplace_slug                 | varchar   | Unique identifier for the marketplace within Footprint                   |               |
| 18           | value_currency                   | varchar   | Value currency                                                           |               |
| 19           | royalty_amount                   | double    | Royalty amount                                                           |               |
| 20           | platform_fees_amount             | double    | Platform fees amount                                                     |               |
| 21           | royalty_rate                     | double    | Royalty rate                                                             |               |
| 22           | platform_fee_rate                | double    | Platform fee rate                                                        |               |
| 23           | value                            | double    | Amount of tokens transferred(in USD)                                     |               |
| 24           | royalty_value                    | double    | Royalty value (in USD)                                                   |               |
| 25           | platform_fees_value              | double    | Platform fees value (in USD)                                             |               |
| 26           | collection_slug                  | varchar   | Unique identifier for the collection within Footprint                    |
