
## Relationships loading techniques

Which type of loading to use typically comes down to optimizing the tradeoff between number of SQL executions, complexity of SQL emitted, and amount of data fetched.

**One to Many / Many to Many Collection** - The [`selectinload()`](https://docs.sqlalchemy.org/en/20/orm/queryguide/relationships.html#sqlalchemy.orm.selectinload "sqlalchemy.orm.selectinload") is generally the best loading strategy to use. It emits an additional SELECT that uses as few tables as possible, leaving the original statement unaffected, and is most flexible for any kind of originating query. Its only major limitation is when using a table with composite primary keys on a backend that does not support “tuple IN”, which currently includes SQL Server and very old SQLite versions; all other included backends support it.

**Many to One** - The [`joinedload()`](https://docs.sqlalchemy.org/en/20/orm/queryguide/relationships.html#sqlalchemy.orm.joinedload "sqlalchemy.orm.joinedload") strategy is the most general purpose strategy. In special cases, the [`immediateload()`](https://docs.sqlalchemy.org/en/20/orm/queryguide/relationships.html#sqlalchemy.orm.immediateload "sqlalchemy.orm.immediateload") strategy may also be useful, if there are a very small number of potential related values, as this strategy will fetch the object from the local [`Session`](https://docs.sqlalchemy.org/en/20/orm/session_api.html#sqlalchemy.orm.Session "sqlalchemy.orm.Session") without emitting any SQL if the related object is already present.



The primary difference between `selectinload()` and `joinedload()` is how they handle loading associated entities:

- **`selectinload()`** issues an additional SELECT statement for the associated entities, typically using an IN clause to efficiently load multiple entities at once. This can be beneficial when dealing with large collections.
    
- **`joinedload()`** uses a JOIN operation to fetch the associated entities along with the main entity in a single query. This can be useful in some cases, but it may result in **duplicated data** in the result set, especially when dealing with One-to-Many relationships.

Example:
post has 2 hotspots
```sql
select *  
from post  
         left join hotspot on post.id = hotspot.post_id  
where post_id = 'edea2f5a-0ab8-467d-a578-fdc07016ebaf'

=> will result 2 records
```