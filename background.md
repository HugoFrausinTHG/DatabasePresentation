# Background to Neo4J

## At a glance

- Graph-based database implemented in Java and Scala
- Users interact with the DB through the intuitive language Cypher
- Various paid and free implementations
- Used by many leading organisations including:
  - Transport for London (reducing congestion)
  - BNP (reducing fraud)
  - Novartis (exploring connections between new drugs, laboratory data and medical literature)
- Networks of data may be more easily understood and managed through Neo4J and Cypher than in traditional relational DBs
- Visualisation tools available - "whiteboard friendly"

[Neo4j](https://neo4j.com/)

## History

- Created my Emil Eifrem in 2007 during a software movement called "NOSQL"
- A little misleading, but NOSQL = Not Only SQL!
- Version 5 as of 2025
- Apparently the name is related to "Java" in which the program is written

## Compliance

- ACID (similar to the CAP principles) - atomicity, consistency, isolation, durability
- ISO 39075:2024(en) - including many optional recommendations

## A graph-based database

A traditional relational databases like SQL stores data in tables linked by keys to form relationships.

Instead, Neo4J builds graphs using linked lists from the very lowest level (it's not just a wrapper). Network-style collections of data may be better suited to this form of database e.g.

- Transport networks
- Social networks
- Finance networks
- Knowledge (think mind maps)

Underneath the hood, the graphs are built with linked lists. Note that there may be some penalties for specific actions using this data structure as suggested in this post:
[Debate on Graph DBs](https://www.theregister.com/2023/03/08/great_graph_debate_wednesday/)

Such graph-based databases are suggested by the creators to be faster when performing join-like operations where the number of relationships is high. However as a counter-argument, columnar data may be less expensive to read/write as it is contiguous in memory. Columnar memory may also be easier to compress.

There are three types of data in Neo4j:

- Nodes (i.e. vertices)
- Relationships (i.e. edges)
- Properties (held by nodes or relationships as key-value pairs)

### Nodes

- Can have labels (like a class of node)
- Can be constrained (required properties)
- Can be indexed (for performance)
- Can have multiple relationships

### Relationships

- Must connect two named nodes
- Must have a direction

### Searching

- As with other graphs, you could do a breadth-first or depth-first search
- Since we usually want to assess closer nodes (e.g. friends of a person) Neo4j does breadth-first

## A case for Graph databases

The inefficiency/poor scalability of graphs for very large data sets has been raised in the "NOSQL" wars. However, an interesting counterargument was presented here:
[Neo4j webinar](https://neo4j.com/blog/recap-intro-to-graph-databases-webinar-series-1/)

There are two types of scalability:

- Scalability of size
- Scalability of complexity

The presenter explains that, while for a very few extreme situations (think Google-sizes), a database may need size scalability, the vast majority of cases are far too small to be concerned with optimisations of this kind.

Instead, it is much more likely that a project could become more complex (i.e. contain many relationships) which is the specialty of a graph-based DB like Neo4j. Neo4j is superior for actions like "JOINs" over relational databases, and they argue that with the more natural language/structure/visualisation of a graph for humans, it also saves the programmer time and effort which should be valued.
