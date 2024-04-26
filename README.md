# Footprint Batch Download Tutorial

## Getting Started

- Get domain & psk key from Footprint
- Learn about Python demo script to  download data


## How to access the daily data

Take the table **`sui_nft_transactions`** as an example, If you want to get the data for the day "2024-01-01", you can use the `download_daily_data` method and pass in the parameters to get the corresponding data.

```python
# The path to the file where Footprint is stored on R2 is as follows
| sui_nft_transactions
| --block_date=2024-01-01
| ----file.parquet
| ----file.parquet
| --block_date=2024-01-02
| ----file.parquet
| ----file.parquet


def download_daily_data(chain, table, date):
    download(chain, table, f"block_date={date}")

if __name__ == '__main__':
    download_daily_data('sui', 'sui_nft_transactions', '2024-01-01')
```


## How to access the static data

Take the table **`sui_nft_collection_info`** as an example**,** you can use `download_static_data` method to get the data.

> **“Static data“** refers to token/NFT metadata.

```python
# The path to the file where FP is stored on R2 is as follows
| nft_collection_info
| ----file.parquet
| ----file.parquet


def download_static_data(chain, table):
    download(chain, table)

if __name__ == '__main__':
		download_static_data('sui', 'nft_collection_info')
```

## How to update latest balance data



## How to access the patch data

Take the table **`sui_nft_transactions`** as an example, get patch data for a specific version  or block date by using the `download_patch_data` method

> **“Patch data”** refers to situations where data has not been normally produced due to certain circumstances, or where the addition of a new FT causes an increase in data. The missing data will be regenerated to the specified version folder. At the same time, patch data generation will also be under different version folders to prevent data conflicts

```python
# The path to the file where FP is stored on R2 is as follows
| sui_nft_transactions
| --patch_data
| ----version=1
| ------block_date=2024-01-01
| --------file.parquet
| --------file.parquet
| ------block_date=2024-01-03
| --------file.parquet
| --------file.parquet


def download_patch_data(chain, table, version):
    download(chain, table, f"/patch_data/version={version}")

if __name__ == '__main__':
		download_patch_data('sui', 'sui_nft_transactions', 1)
# download_patch_data('sui', 'sui_nft_transactions', 1, '2024-01-01')
```


## How to merge table with patch data

Take the table `**sui_token_tranfers**` as an example,  please prepare the following items:

1. Prepare a table to store patch data, here we use `sui_token_tranfers_patch_table`.
2. Download the patch data via `download_patch_data` method and save it in `sui_token_tranfers_patch_table`.
3. Merge the data through the design of the primary key in the table.

Here is a Trino sql example of updating historical table patch data, where the database is merged based on the table primary key information provided.

> Please contact Footprint to get table primary key informations

```SQL
MERGE INTO sui_token_tranfers AS a
USING sui_token_tranfers_patch_table AS b
ON  a.chain = b.chain
AND a.block_number = b.block_number
AND a.log_index = b.log_index
AND a.transaction_hash = b.transaction_hash
WHEN MATCHED THEN
  UPDATE SET
    chain = b.chain,
    block_number = b.block_number,
    log_index = b.log_index,
    transaction_hash = b.transaction_hash,
    block_hash = b.block_hash,
    block_timestamp = b.block_timestamp,
    from_address = b.from_address,
    to_address = b.to_address,
    token_address = b.token_address,
    token_symbol = b.token_symbol,
    amount_raw = b.amount_raw,
    value = b.value,
    total_gas_fee = b.total_gas_fee,
    status = b.status
```

## How to access full historical data

1. use `download_daily_data` to download historical data.
2. use `download_all_patch_data` to quickly download the latest available patch data, if it returns no data, this means there is no historical patch data.
3. Merge `all patch data` ****to `daily_data` by primary keys. (Skip if none is available)

---

## Notification

> You'll need to provide a webhook for the FP to be able to send you a push message when the data production is complete!

Metadata of notification:

```json
{
	"message": "sui balance_change_history 2024-04-02 has been produced",
	"chain": "sui",
	"table_name": "sui_nft_transactions",
	"update_path": "sui/sui_nft_transactions/block_date=2024-01-01",
	"type": "ordinary"
}
```

There are the following types of notification:
- `ordinary` it means the daily data file has been produced successfully.
- `delay` it means that the daily data was produced longer than agreed upon.
- `delta` it means the delta data file has been produced successfully.



