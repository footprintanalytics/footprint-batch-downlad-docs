> The type of table is `daily table` 
>> This table contains the NFT token transfers event information of ERC1155, ERC721 included in the nft_contract_info table and some ERC20 NFTs. Mainly includes the flow direction of the token, and covers mint, burn and transfer transactions.

| column order | column name                 | data type | description                                                            | is_unique_key |
| ------------ | --------------------------- | --------- | ---------------------------------------------------------------------- | ------------- |
| 1            | block_timestamp             | integer   | Block timestamp where this transaction was in                          | Y             |
| 2            | block_number                | bigint    | checkpoint                                                             | Y             |
| 3            | transaction_hash            | varchar   | transaction_block_digest                                               | Y             |
| 4            | log_index                   | varchar   | The digest of object change => sui_object_change_history.digest        | Y             |
| 5            | collection_contract_address | varchar   | object_type                                                            | Y             |
| 6            | from_address                | varchar   | The sender of transaction                                              |               |
| 7            | to_address                  | varchar   | The owner of each object change records                                |               |
| 8            | nft_token_id                | varchar   | object                                                                 | Y             |
| 9            | amount_raw                  | double    | The number of tokens transferred                                       |               |
| 10           | internal_index              | varchar   | The unique item index for multiple NFT transactions in a single event. | Y             |
| 11           | chain                       | varchar   | Blockchain name                                                        | Y             |
