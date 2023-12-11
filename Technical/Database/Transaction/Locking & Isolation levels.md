
## Issues
- Dirty reads
- Non-repeatable reads
- Phantom reads

## Isolation levels
- Read Uncommitted
- Read Committed (Other transactions can access and update same data. But in the level, if re-read same data can cause `Non-repeatable Read`)
	- In the Read Committed isolation level, transactions are allowed to access and update the same data concurrently. However, the key point is that a transaction reading data will only see changes committed by other transactions. It won't read uncommitted changes, preventing what is known as "dirty reads."
	- Breakdowns:
		- **Reads:** Transactions can read data that has been committed by other transactions.
		- **Updates:** Transactions can also update data, and those updates become visible to other transactions only after they are committed.
		- **Dirty Reads:** Dirty reads, where a transaction reads uncommitted changes made by another transaction, ***are not allowed***.
- Repeatable Read(Other transactions access and update same data like `Read Committed`. But it only see the same data through all the transaction from `beginning` until `commit`)
	- In the Repeatable Read isolation level, other transactions can read and update the same data concurrently. The key characteristic of Repeatable Read is that within a single transaction, the values of the data that have been read will remain constant, even if other transactions commit changes to that data.
	- Breakdowns:
		-  **Reads:** Transactions can read data that has been committed by other transactions.
		- **Updates:** Transactions can update data, and those updates become visible to other transactions only after they are committed.
		- **Consistency:** Once a transaction reads a piece of data, it will see the same value for that data throughout the entire transaction, even if other transactions commit changes to that data concurrently.
	- It only lock on selected rows, so that if other connection INSERT data, then we selected again -> it causes phantom reads
- Serializable (Transactions are executed sequentially)


## Isolation levels vs read phenomena

|Read phenomenon  <br>  <br>  <br>  <br><br>Isolation level|Dirty read|Non-repeatable read|Phantom read|
|---|---|---|---|
|Serializable|no|no|no|
|Repeatable read|no|no|yes|
|Read committed|no|yes|yes|
|Read uncommitted|yes|yes|yes|