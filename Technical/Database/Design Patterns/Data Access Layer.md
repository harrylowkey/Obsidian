#Database 

1. DAO
2. Repository

They all stand between Application and Database

## Comparison

- DAO is a lower-level pattern focused on providing direct access to a specific data source, often encapsulating low-level data access operations. It is typically tied to a particular data source, like a database.
- Repository is a higher-level pattern that provides a business-centric interface for data access, abstracting away the specific data storage mechanisms. It can work with multiple data sources and presents a consistent interface to the application.
- `Repository` could be implemented using `DAO`'s, but you wouldn't do the opposite.
- `DAO` would be considered closer to the database, often table-centric.  
- `Repository` would be considered closer to the Domain, dealing only in Aggregate Roots.


`DAO` is an abstraction of **data persistence**.  
`Repository` is an abstraction of **a collection of objects**.

-> DAO's methods like: create/update/delete,... closer to DB terms
-> Repository/s methods like: createPayment/updateCard/deleteMentor,... closer to domain project. And inside the createPayment, it can use the create method of the DAO