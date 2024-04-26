> All updates to the Sui ledger happen via a transaction.

|column order	|column name	|data type	|description	|is_unique_key|
|--	|----	|----	|---------	|---|
|1	|digest	|varchar	|Transaction block hash.	|Y|
|2	|timestamp|	integer|	Timestamp of the block where this transaction was in	||
|3	|payment	|array(varchar)	|payment is a vector of gas coin	||
|4	|gas_owner	|varchar|	gas owner is the single owner of all coins used, either the sender, or the sponsor for sponsored transactions.||
|5	|price	|bigint	|price defines how much users will pay for a single unit of execution.	||
|6	|budget	|decimal(38,0)	|budget is the maximum amount a user pays for a transaction.	||
|7	|sender	|varchar	|The address of the user sending this transaction.	||
|8	|transaction	|varchar	|transaction call data	||
|9	|tx_signatures	|array(varchar)|	The combination of the transaction and the arbitration signature on its bytes	||
|10	|len_events	|bigint	|The number of events in the transaction	||
|11	|checkpoint	|bigint	|The number of checkpoints in which the transaction was added. Checkpoints are equivalents for blocks in Sui.	|Y|
|12	|message_version	|varchar	|Transaction message version	||
|13	|status	|varchar	|The status of an object that changed as a result of running the transaction.	||
|14	|gas_computation_cost	|decimal(38,0)	|The cost of computation efforts spent on validating the transaction. It is part of the total gas fee.	||
|15	|gas_storage_cost	|decimal(38,0)	|The cost of storing objects related to the transaction on-chain. It is part of the total gas fee.	||
|16	|gas_storage_rebate	|decimal(38,0)	|The funds that are paid back to the fee payer when objects related to a transaction are deleted from the storage. This parameter diminishes the total gas fee.	||
|17	|gas_non_refundable_storage_fee|	decimal(38,0)	|Non-refundable storage fees = Storage Cost - Storage Rebate	||
|18	|modified_at_versions	|array(varchar)	|The latest version of the object. In the Sui network, each transaction with an object brings about a change in it, the result of which is a new version of this object.||
|19	|shared_objects	|array(varchar)	|Record information read and written by shared users	||
|20	|created	|array(varchar)	|Create transaction object information	||
|21	|mutated	|array(varchar)	|The mutated object is the gas object used to pay for the transaction.	||
|22	|deleted	|array(varchar)	|Record information about deleted objects	||
|23	|gas_object	|varchar	|Record gas fee payer information	||
|24	|events_digest	|varchar	|The object digest is the hash of the object's contents and metadata.	||
|25	|dependencies	|array(varchar)	|An object reference provides an authenticated view of the object at a particular point in the object's history.	||
|26	|object_change|	array(varchar)	|Objects changed as a result of running a transaction	||
|27	|balance_change|	array(varchar)	|Address balance changes due to running transactions	||
