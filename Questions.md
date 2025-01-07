#### Provide background information on the database system.

- (summary video): https://www.youtube.com/watch?v=urO5FyP9PoI&t=92s

- (quick notes): https://www.geeksforgeeks.org/neo4j-introduction/

It is a NoSQL system, where data is directly stored natively as a graph. This means that each data is stored with direct reference to

other data nodes in the data base. This speeds up look at time in the data base as relations between data are stored with the data

and they do not have to be calculated or looked up -- thus making these data bases more scalable.

#### Outline the design principles and architecture of the system.

- (quick notes): https://www.geeksforgeeks.org/neo4j-introduction/
- (official website): https://neo4j.com/product/

Neo4J is a graph data base, storing data as Nodes, Edges, and Properties.

- **Node**: Represnts a data item, containing lables which represents different attributes of this data point.
- **Edge**: Connection between nodes, illustrates how the data is connected.
- **Properties**: These hold additional information about the Edges between nodes. Directionality, kind of connection, etc.

Neo4J provides a userfriendly interface with simplistic yet powerful syntax. Since the data and its connections are stored together intermediary tables do not have to be referenced. Thus, reducing the amount of boiler plate used when making queries.

> **Create**

Data and relations between data can be created using the _keyword_ "CREATE", following the form bellow:

    `CREATE (hugo:Accelerator {name: "Hugo", nationality: "British"})`

Here, the line after Create specifies a node with a node variable "hugo" with the lable "Accelerator" (type of node). The properties of the node are then defined as key value pairs in {}. Relations between nodes can then be defined in a similar way:

    `MATCH (hugo:Accelerator { name: "Hugo" }), (david:Accelerator { name: "David" })`

    `CREATE (hugo)-[:KNOWS {since:2024}]-(david)`

Similar to nodes, relations can have lables which themselves can have further properties defining that relation.

Unlike nodes, before a relation can be stablish, it needs to first find the nodes being linked. This is done by the keyword MATCH which looks for the nodes that match the search function.

> **Read**

> **Update**

> **Delete**

#### If applicable explain its position within the CAP theorem, including the reasoning.

#### Highlight key use cases where this database excels.

- (Neo4J data preview): https://console-preview.neo4j.io/tools/query

#### Discuss the licensing model and its implications for usage.

#### Analyze the advantages and disadvantages of the database.

#### Demonstrate its functionality, if feasible.

#### Share any other intriguing details about the database.
