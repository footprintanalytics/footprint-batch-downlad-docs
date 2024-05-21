# Footprint Batch Download Tutorial

## Getting Started

- Get domain & psk key from Footprint.
- Understanding the storage structure of data in the cloud. (./docs/sui_file_structure.md)
- Understanding relevant table schema and `table type`. (./table_schema)
- Understanding Python demo script to download data. (./script/download_data_ demo_script.py)

> Different types of table are fetched in different ways, such as `static`, `daily` and `latest` table.
> The type of each table is also labeled on the schema (`./table_schema`)

## How to access the static table

Take the table **`sui_nft_collection_info`** as an example, you can use `download_static_data` method to get the data.

> **“Static data“** refers to token/NFT metadata.

```python
# The path to the file where Footprint is stored on R2 is as follows
| nft_collection_info
| ----file.parquet

def download_static_data(chain, table):
    download(chain, table)

if __name__ == '__main__':
    download_static_data('sui', 'nft_collection_info')
```

## How to access the daily table

Take the table **`sui_nft_transactions`** as an example, If you want to get the data for the day '2024-01-01', you can use the `download_daily_data` method and pass in the parameters to get the corresponding data.

```python
# The path to the file where Footprint is stored on R2 is as follows
| sui_nft_transactions
| --date=2024-01-01
| ----file.parquet
| --date=2024-01-02
| ----file.parquet
.
.
.

def download_daily_data(chain, table, date):
    download(chain, table, f'date={date}')

if __name__ == '__main__':
    download_daily_data('sui', 'sui_nft_transactions', '2024-01-01')
```

## How to access the latest table (TBD)

## How to handle the patch data 

> **“Patch data”** refers to situations where data has not been normally produced due to certain circumstances, or where the addition of a new NFT causes an increase in data.

### Full Overwrite

The tables involved as follows:
- `nft_collection_info`
- `token_info`

Take the table **`nft_collection_info`** as an example, since this type of table size is generally very small and only have a file, once the patch data is generated, we will directly overwrite the entire file under ordinary.
You can use `download_static_patch_data` method to get the data, directly overwrite it.

```python
# The path to the file where Footprint is stored on R2 is as follows
| nft_collection_info
| ----file.parquet

def download_static_patch_data(chain, table):
    download_static_data(chain, table)

if __name__ == '__main__':
    download_static_patch_data('sui', 'nft_collection_info')
```

### Partial Overwrite 

#### Partial Overwrite Ordinary

The tables involved as follows:
- `sui_balance_change_history`
- `sui_object_change_history`
- `sui_token_transfers`
- `sui_transaction_blocks`
- `asset_flow_v2`

Take the table **`sui_token_transfers`** as an example, since this type of table is usually the result of patch data generated by a missing block of time, we will overwrite the corresponding partition.
You can use `download_daily_patch_data` method to get the data, directly overwrite it.

```python
# The path to the file where Footprint is stored on R2 is as follows
| sui_token_transactions
| --date=2024-01-01
| ----file.parquet
| --date=2024-01-02
| ----file.parquet
.
.
.

def download_daily_patch_data(chain, table, date):
    download(chain, table, f'date={date}')

if __name__ == '__main__':
    download_daily_patch_data('sui', 'sui_token_transactions', '2024-01-01')
```

#### Partial Overwrite By Latest Daily Full Data

The tables involved as follows:
- `sui_nft_transactions`
- `sui_nft_transfers`

Take the table **`sui_nft_transactions`** as an example, this type of table has a situation where adding a new NFT leads to an increase in data, and if you use an override partitioning method like bronze table, it may involve a lot of partitioning updates, which is extremely costly to update.

We will generate new folder named `latest` that stored the latest data of original data and patch data, but only from the past 7 days at most. If there are other serious issues over the past 7 days, we will manually upload the data.
You can use `download_daily_latest_full_data` method to get the data, directly overwrite it.
```python
# The path to the file where Footprint is stored on R2 is as follows
| sui_nft_transactions
| --latest
| ----date=2024-01-01
| ------file.parquet
| ----date=2024-01-03
| ------file.parquet

def download_daily_latest_full_data(chain, table):
    download(chain, table, f'/latest')

if __name__ == '__main__':
    download_daily_latest_full_data('sui', 'sui_nft_transactions')
```

## How to access full historical data

### static table
1. use `download_static_data` to download historical data.

### daily table
1. use `download_daily_data` to download historical data.
2. use `download_daily_latest_full_data` to quickly download the latest available full data, if it returns no data, this means there is no patch data or not need patch data.
3. take the latest full data and overwrite the ordinary data with the date involved.  


## Notification

> You'll need to provide a webhook for the Footprint to be able to send you a push message when the data production is complete!

Metadata of notification:

```text
[Footprint Batch Download]
Incident: Data production completed
Impact: sui token_transfers 2024-05-09
Type: Delay
Path: sui/token_transfers/date=2024-05-09
Completed Time: 2024-05-10 11:30 (KST, UTC+9)
```

There are the following types of notification:
- `Ordinary` it means the daily data file has been produced successfully.
- `In Progress` it means the daily data file has been in progress but not have been produced successfully.
- `Delay` it means that the daily data was produced longer than agreed upon.
- `Delta` it means the delta data file has been produced successfully.



