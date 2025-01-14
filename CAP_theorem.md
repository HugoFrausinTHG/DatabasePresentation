# Does Neo4j comply with any CAP-model?

In the CAP theorem (consistency, availability, partition-tolerance) a distributed database can only have two of the three properties when a partition occurs:

1. CA - to ensure consistency and availability, a DB could is not partition-tolerant
2. CP - by locking users out when there's a partition, the DB can ensure consistency
3. AP - by allowing users to see different versions (inconsistent), a DB can maintain availability in the face of partition.

Which does Neo4j implement?

Answer: None really.

Explanation:
Neo4j alone is not a technology that is built for distributed systems (multiple machines).
For that you use servers like these:
[Distributed Database systems](https://thechief.io/c/editorial/top-25-distributed-databases/)

However, if you were to do this, there are two broad strategies:

1. Break the database into closely connected subsections between machines (called sharding/fragmentation)
2. Replicate the database onto many machines and decide how they communicate (e.g. master-slave relationship)

Neo4j is not considered partition-tolerant on its own. This is because the graph model must all be present for a heaily interconnected system so the database cannot be split into chunks easily and it has no built-in support for multiple machines.

## An example of sharding/fragmentation for Neo4j

In the reference below, an idea for how to fragment a large Neo4j database is discussed. It can be harder to split a graph into sections as there is no guarantee that a user will not connect any two nodes with a relationship.

However, if it is clear that certain nodes rarely talk to each other, then they can be grouped into shards (e.g. by a specific property/label such as location). Then, individual machines can take on the work of a subsection of requests by location. It is very dependent on the data.

[Neo4j sharding](https://www.fromdev.com/2013/10/neo4j-cache-sharding-scale-out.html)

Note: some NoSQL databases have been classified by their CAP position here:
[CAP of some NoSQL databases](https://www.ibm.com/think/topics/cap-theorem#:~:text=the%20next%20step-,What%20is%20the%20CAP%20theorem%3F,'P'%20in%20CAP)
