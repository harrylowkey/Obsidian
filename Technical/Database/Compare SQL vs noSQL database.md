

## Scalability

SQL databases scale vertically, usually on a single server, and require users to increase physical hardware to increase their storage capacities. In effect, while cloud-storage options are available, SQL databases can be prohibitively expensive for businesses when dealing with vast amounts of [big data](https://www.coursera.org/articles/what-is-big-data-a-laypersons-guide).

NoSQL databases offer horizontal scalability, meaning that more servers simply need to be added to increase their data load. This means that NoSQL databases are better for modern cloud-based infrastructures, which offer distributed resources.


## Support

SQL is a popular standard language that is well supported by many different database systems, while NoSQL has varying levels of support in various database systems.

Regarding support, you’ll generally find that more help is available for SQL databases than NoSQL. This is because SQL is a more established technology and thus has many more users and developers who can help you with your problems. In contrast, NoSQL is still relatively new, with less help available on forums or through the community. Your support options may be limited if you run into difficulties using it.

## Pros and cons of NoSQL

### Pros of SQL:

- SQL is widely understood and supported; most developers know it well.
    

- SQL is extremely useful for simple aggregations over large datasets, such as calculating averages.
    

- SQL is extremely useful for setting up simple ETL jobs, especially if the input and output formats are relational databases.
    

- SQL is well-documented and easy to learn.
    

### Cons of SQL:

- The performance of SQL can be poor on substantial data sets because it requires multiple passes over the data to complete many operations (especially joins). 
    

- Debugging SQL can be complicated because it doesn't provide informative error messages.
    

- The syntax of SQL tends to be verbose compared with programming languages like [Python or R](https://www.coursera.org/articles/python-or-r-for-data-analysis), which makes it harder to write complex transformations as scripts or functions.

## Pros and cons of NoSQL

A significant benefit of NoSQL is that you don't have to define a schema upfront (or ever). This makes it easy to add new columns without dealing with all the issues involved in altering a vast table with lots of data already in it. It also means that if your queries don't require SQL, you can avoid the overhead of parsing and compiling SQL statements, modeling, and storing, providing an enormous performance boost when dealing with large amounts of data.

However, NoSQL is less mature than SQL. Here’s a look at NoSQL's pros and cons.

### Pros and cons of NoSQL

- Flexible schema
- Usable on distributed infrastructure platforms
- Low-cost infrastructure
- High availability and throughput    

### Cons of NoSQL:

- Less mature technology and difficult to manage
- Limited query capabilities
- Data inconsistency and poor performance in some complex scenarios


## When to use: SQL vs. NoSQL 

Deciding when to use NoSQL versus SQL is essential because they differ in structure, capabilities, and ideal use cases.

A relational database like SQL is a great option if you’re looking to build an application structured around a relationship between data tables. SQL also works well when you want to ensure your data is consistent across tables. However, relational databases aren’t always the best choice regarding flexibility or scaling.

A non-relational NoSQL database doesn’t use structured tables but instead uses flexible schemas for unstructured data storage. This gives you more ability to scale your project as needed. However, it also means you have less control over consistency and data relationships.

- **You need high performance, particularly read performance:** The way distributed NoSQL systems like Cassandra and Riak work means you can usually get very high read performance by adding more boxes. Some go so far as to automatically replicate data across nodes to ensure you always have plenty of copies of your data to access.
    

- **You need high availability (HA):** Data replicates across nodes in a NoSQL system, so the failure of a single node does not necessarily result in data loss or downtime for your application. This also means you can easily add or remove nodes from clusters without impacting availability.