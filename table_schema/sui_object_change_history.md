| column order | column name              | data type | description                                                                  | is_unique_key |
| ------------ | ------------------------ | --------- | ---------------------------------------------------------------------------- | ------------- |
| 1            | transaction_block_digest | varchar   | The digest of the queried transaction.                                       | Y             |
| 2            | checkpoint               | bigint    | The checkpoint number.                                                       | Y             |
| 3            | time_stamp               | integer   | Transaction's block timestamp.                                               |               |
| 4            | sender                   | varchar   | Sender Address.                                                              |               |
| 5            | owner_type               | varchar   | Type of the object owner (AddressOwner, ObjectOwner, Shared).                |               |
| 6            | owner_address            | varchar   | The address of the owner who owned the object.                               |               |
| 7            | shared_object_version    | varchar   | The latest version of the share object                                       |               |
| 8            | object_type              | varchar   | The type of the queried object.                                              |               |
| 9            | object_id                | varchar   | The ID of the queried object.                                                | Y             |
| 10           | version                  | varchar   | The version of the queried object.                                           |               |
| 11           | digest                   | varchar   | The digest of the object.                                                    |               |
| 12           | type                     | varchar   | The type of object changed this time(eg: 'mutated', 'created' ,'published'). |               |
