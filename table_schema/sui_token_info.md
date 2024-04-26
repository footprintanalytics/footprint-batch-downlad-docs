> This table contains the basic information of the token, which can be used to identify the token using the token_address.

| column order | column name    | data type      | description                                                                                                             | is_unique_key |
| ------------ | -------------- | -------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------- |
| 1            | chain          | varchar        | Blockchain name                                                                                                         | Y             |
| 2            | token_slug     | varchar        | Unique identifier for the token within Footprint                                                                        |               |
| 3            | token_address  | varchar        | object_type, eg: "0x94e7a8e71830d2b34b3edaa195dc24c45d142584f06fa257b73af753d766e690::celer_wbtc_coin::CELER_WBTC_COIN" | Y             |
| 4            | token_symbol   | varchar        | The symbol of token, eg: "WBTC"                                                                                         |               |
| 5            | decimals       | bigint         | The number of decimals                                                                                                  |               |
| 6            | token_name     | varchar        | The name of token, eg: "Wrapped BTC"                                                                                    |               |
| 7            | protocol_slug  | varchar        | Unique identifier for the protocol within Footprint                                                                     |               |
| 8            | logo           | varchar        | Token logo                                                                                                              |               |
| 9            | created_at     | double         | timestamp this record created                                                                                           |               |
| 10           | updated_at     | double         | timestamp this record last updated                                                                                      |               |
| 11           | token_type     | array(varchar) | labels for a token (all null in Sui)                                                                                    |               |
| 12           | crypto_stack   | varchar        | one kind of category methodology about token, use for aggregate, means tech stack (can be null)                         |               |
| 13           | sector         | varchar        | one kind of category methodology about token, use for aggregate (can be null)                                           |               |
| 14           | industry       | varchar        | one kind of category methodology about token, use for aggregate (can be null)                                           |               |
| 15           | token_taxonomy | varchar        | one kind of category methodology about token, use for aggregate (can be null)                                           |
