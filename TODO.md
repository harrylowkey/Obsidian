
## Need to check

- [ ] Socket not work when loading module in thread

## Refactor fastapi-queue-task

- [ ] Remove check pytest
- [ ] Override fsatapi-queue-task while running test

## Refactor fastapi-orm-helper

- [ ] Add @Entity decorator
- [ ] Add @Uniques decorator 
- [ ] Join relationships
- [ ] Check async.gather queries

## Add Base migration

- [ ] Generate migration 

## Refactor transaction

Note:
Engine manages pool of connection (lowest level of SQLAlchemy using) (alembic is using it for DDL)
Engine.execute() behind the scene uses `connection.execute()` (connection from pool of connection)
Session.execute() behind the scene use `connection.execute()`

Resources:
	https://docs.sqlalchemy.org/en/20/orm/session_transaction.html#managing-transactions
- Currently when session instanced, it auto-begin create transaction: https://docs.sqlalchemy.org/en/20/orm/session_basics.html#auto-begin

- nested transaction: save point, begin_nested()
- two-phase commit (2 DBs)