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

As seen above, nodes can be searched by using the MATCH keyword.

    `MATCH (n:Accelerator { name: "David" })`

Here, Neo4J looks through all of the nodes of type Person and finds the ones whose name's matches to David. Just like with nodes,
MATCH can be used to find relations between nodes:

    `MATCH (Accelerator1:Accelerator { name: "David" })-[:KNOWS]-(Accelerator2:Accelerator)`

> **Update**

Match the node or relation desired, then SET its properties like so:

    `MATCH (a:Accelerator {name: "David"})`
    `SET a.name = "DAVID"`

If you want to update the lable of a relation or node, you must first REMOVE its label before another on is set.

    `MATCH (a:Accelerator {name: "David"})`
    `REMOVE a:Accelerator`
    `SET a:Graduate`

> **Delete**

To delete data, the same steps are followed but now with the keyword DELETE. First, Match and lable the desired connections and then delete them.

    `Match (A1:Accelerator {name: "David"})-[r:KNOWS]->(A2:Accelerator {name: "Hugo"})`
    `DELETE r `

#### If applicable explain its position within the CAP theorem, including the reasoning.

#### Highlight key use cases where this database excels.

- (Neo4J data preview): https://console-preview.neo4j.io/tools/query
- https://www.analyticsvidhya.com/blog/2022/01/a-comprehensive-guide-on-neo4j-graph-database/

It excels at storing data which is highly relational as the relations are stored with the data and not calculated at queary time. It particularly excels in cases like:

- Social networks
- Fraud
- Networks and IT operations
- Knowledge Graphs

#### Discuss the licensing model and its implications for usage.

#### Analyze the advantages and disadvantages of the database.

- Fast look at times when trying to find the connection between different objects. Queries regarding the 20th connection of a node become trivial.

- Great interface which easily visualises the data.

- You can only write single nodes at a time so it becomes a bottle neck for write-intensive data bases where nodes need to be written quickly.

- Since relations are stored and not calculated, this makes them very memory intensive.

#### Demonstrate its functionality, if feasible.

#### Share any other intriguing details about the database.
