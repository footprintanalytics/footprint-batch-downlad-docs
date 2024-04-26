>
| column order | column name      | data type | description                                                                                  | is_unique_key |
| ------------ | ---------------- | --------- | -------------------------------------------------------------------------------------------- | ------------- |
| 1            | address          | varchar   | The subject address of the recorded data.                                                    | Y             |
| 2            | hash             | varchar   | The digest of the queried transaction.                                                       | Y             |
| 3            | index            | varchar   | /                                                                                            | Y             |
| 4            | internal_index   | varchar   | /                                                                                            | Y             |
| 5            | block_timestamp  | integer   | Timestamp of the block where this transaction was in                                         |               |
| 6            | asset_address    | varchar   | FT / NFT contract address                                                                    |               |
| 7            | nft_token_id     | varchar   | The NFT collection Item Id                                                                   | Y             |
| 8            | flow_type        | varchar   | The direction in which the asset is transferred from the subject address. eg: inflow/outflow | Y             |
| 9            | interact_address | varchar   | The counterpart address of the recorded data.                                                | Y             |
| 10           | asset_name       | varchar   | FT / NFT contract name                                                                       |               |
| 11           | block_number     | bigint    | The checkpoint number.                                                                       |               |
| 12           | amount_raw       | double    | The transaction amount in its raw format.                                                    |               |
| 13           | amount           | double    | Amount_raw multiplied by the decimals.                                                       |
