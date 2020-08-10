System design Topics:


1. **Horizontal Vs Vertical Scaling**

```
    Horizontal                  Vertical
    More network overhead       Less network overhead
    scalable easily             Not Easily scalable
    Better resource optimizan   resource optimization
    More Resilient              Less Resilient
                                Single point of faiulue
    Load balancer Required      No Required Load balancer
    Network calls (RPC)         InterProcess Communicatio    (IPC)
    Data InConsistency          data Consistency

Ref: https://www.youtube.com/watch?v=xpDnVSmNFX0
```


2.  **CAP Theorem**

```
C: Consistency
A: Availability
P: Partition Tolerance

References:

https://www.youtube.com/watch?v=PyLMoN8kHwI
https://towardsdatascience.com/cap-theorem-and-distributed-database-management-systems-5c2be977950e
https://medium.com/@bikas.katwal10/mongodb-vs-cassandra-vs-rdbms-where-do-they-stand-in-the-cap-theorem-1bae779a7a15
https://www.ibm.com/cloud/learn/cap-theorem


CAP Theorem says that a database can't have all three at once. It can have atmost 2.

CA: RDBMS
CP: Mongo, Redis, HBase
AP: CouchDB, Cassandra, DynamoDB

But in real world, Partition Tolerance is highly recommended. so Ideally, It's either

CP:
AP:
```


3. **ACID Properties  of database**


```
A: Atomicity: Either perform the transaction as a whole or do nothing 
    Eg: Transferring amount from account A to account B

C: Consistency: Data should be consistent after whole transaction
    Eg: Account A: 100, Account B: 300,: Total = 400
    A transfers 50rs to B. Still total amount is: 400

I: Isolation: All transactions should be in Isolation of other transactions happening in the system.
D: Durability: The database should be durable enough to hold all its latest updates even if the system fails or restarts


References:
https://www.youtube.com/watch?v=nZK5a-jHvMU
https://www.youtube.com/watch?v=Z57b-1HLSU8

```


4. **Partitioning/Sharding Data**

```
Partitioning: Splitting a table based on the row on a single machine.
    Eg: Splitting a user table using ids or their first name or locations etc.


Sharding: Sharding is Splitting the table(s) same way as Partitioning but across all the servers.

How to Partition:
There are multiple ways to Partition the data. Some of them are:
    - Consistent Hashing
    - User's location
    -

Pros:
    - Time to search on a data reduces.
    - Data is limited to some extent.
    - Read/Write Performance goes up

Cons:
    - Joins are costly.
    - Tough to further scale/split
    - Consistency is difficulty to achieve
    - Transactions Properties (ACID) are not valid on sharding


What if any node/shard fail ??
    We can use master slave architecture.

References:
    - https://www.youtube.com/watch?v=iHNovZUZM3A
    - https://www.youtube.com/watch?v=5faMjKuB9bc&t=312s
    - https://stackoverflow.com/questions/18302773/what-are-horizontal-and-vertical-partitions-in-database-and-what-is-the-differen
    - https://medium.com/@jeeyoungk/how-sharding-works-b4dec46b3f6
    - https://www.youtube.com/watch?v=K12oQCzjPxE
```

5. **Consistent Hashing**

6. **Optimistic vs Pessemistic Locking**

7. **Strong vs Eventual Consistency**
```
Strong Consistency: All reads should always get the latest data writen in the database
Eg: Any payment gateway, stock exchange

DB: Relational Database
This provides more Consistency but somewhere less Availability. 

Eventual Consistency: Some reads may get outdated data but at some point, User will get latest data.

Eg: User likes on a particular post/blog/video. 
DB: NoSQL Database


This provides higher Availability.
```

8. **Relational DB vs NoSQL DB**


References:
    - https://www.youtube.com/watch?v=ZS_kXvOeQ5Y
    - https://www.youtube.com/watch?v=ruz-vK8IesE
    - https://www.youtube.com/watch?v=xQnIN9bW0og

```

Relational DB:

This is entirely based on relations of entities. Each entity has relation with some other entities.

Relational DB follows the schema for each table defined at initial step. Therefor, It is mandatory
for each record to follow schema otherwise it raises an Invalid schema exception.

Also, It strictly allows `Referential Integrity`. Meaning that
It allows following types of relations.

    1. One to One
    2. One to Many
    3. Many to Many

Based on above relation, each relation has to follow the protocols/rules. Otherwise it raises
`referential Integrity` error. 

Pros:
    1. Easy to understand
    2. Very few chances of invalid data (Since it already adds up a layer of data validation)
    3. Supports ACID transaction Properties
    4. By using normalization, One can reduce the data redundancy
    5. Good for write intensive applications.
    6. Introducing Indexing is easy business
    7. Horizontal Scaling is Impossible. But vertical Scaling is possible.
    8. Data is distributed across multiple tables.
    9. Limitations for lots of read/write queries per second.
    10. Forces Consistency on the data 

Cons:

    1. Slow in data writing
    2. Not good for flexible data ( data without schema)
    3. 


NoSQL DB:

Database without schema is NoSQL DB. 

                    Document
            ___________|_____________________
            |          |                    |
        Collection1   Collection 2.... Collection n

Pros:
    - Both Horizontal/Vertical Scaling is possible.
    - Good for read intensive applications. ( Since no need of any joins )
    - Data is typically merged/nested in a few collections
    - Great Performance for massive read/write.

Cons
    - No schema. So data schema is tough to predict.
    - Queries are less flexible.

should prefer only when application require less update on data. Or application is read intensive.

Types of NoSQL DB:
    1. Key Value { Redis }
    2. Wide Column { Cassandra }
        - A table can have a higher number of columns

    3. Document based { MongoDB }
        - JSON based or xml based data can be stored

    4. GraphBased {}

Refer: https://www.youtube.com/watch?v=p4C0n3afZdkp

When to use what ?

SQL                                     NoSQL
- When your access patterns         - When your access pattern is defined
aren't defined                      - When your primary key is Known.
                                    - When your model data fits (Graph)
- WHen you want to perform          - When you need high performance and low Latency
flexible queries                    - 

- When you want to perform 
relational queries

- When you want to enforce field 
constraints

- When you want to use a well 
documented access language. (SQL)

```

9. **Caching**

    ```
    Types of caching:
        1. File based
        2. Memory based
        3. DB Based


    Redis is preferred more for caching. 
    
    ```

