- Topics
1. Vertical vs Horizontal Scaling
2. Cap Theorem
3. 

      
 ### Vertical vs Horizontal Scaling
   Ref: https://www.youtube.com/watch?v=xpDnVSmNFX0
   
  | Horizontal  | Vertical |
  | ------------- | ------------- |
  | Will Require Load Balancer  | No Load Balancer  |
  | Resilient  | Single point of failure  |
  | Network Calls (RPC) | Inter Process Communication (Fast)
  | Data Inconsistency | Consistency 
  | Scales easily   |  Not scalable easily
   
     
 ### Cap Theorem 
 
 C : Consistency 
 
 A : Availability (A user will definitely get the response irrespective the content latest) 
 
 P : Partition Tolerance (May drop package over network)
 
 Ref: https://www.youtube.com/watch?v=ytPoGSNV8z8
 
 - Traditional db uses consistency over Availability
 - But NOSql db uses Availability over Consistency
 
 1. Consistency/Availability -> RDBMS
 2. Consistency/Partition -> Mongo/Redis/HBase 
 3. Availability/Partition -> CouchDB/Cassandra/Dynamo (Time series analysis, Travel booking websites) 
 
 
 ### ACID/BASE
 
 Ref: 
 
 
 - ACID: Atomicity/Consistency/Isolation/Durability (Used in Traditional dbs like RDBMS)
 
 - BASE:  Basically available soft state eventual consistency (Used in NoSql)
 
     
 ### Partitioning/Sharding
 
 Partitioning
    - 
    
 Sharding
    - Shard/Split 
        Consistency Hashing