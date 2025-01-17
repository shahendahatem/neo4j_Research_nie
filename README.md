


## Requirements
- Docker installed on your system.
- Internet access to fetch the sample graph data.

## Setup
To set up the Neo4j environment with the necessary plugins and import the sample data, follow the steps below:

1. Open a terminal or command prompt.

2. Execute the following Docker command to run the Neo4j instance with the required plugins:
   ```
   docker run --name testneo4j -p 7474:7474 -p 7687:7687 -d --env NEO4JLABS_PLUGINS='["apoc", "n10s"]' --env NEO4J_AUTH=none neo4j:5.7
   ```

## Data Import
The next step is to import the sample graph data into the Neo4j database. We'll use the `n10s` plugin to fetch the data from the specified URL and load it into the database.

1. Open a web browser and navigate to the Neo4j browser at http://localhost:7474.

vse });
      ```

## Data Deletion
Before running any analysis queries, you might want to delete any existing data to start with a clean slate. To delete all nodes and relationships in the database, execute the following query in the Neo4j browser:

```cypher
MATCH (n)
OPTIONAL MATCH (n)-[r]-()
DELETE n, r;
```

## Explore Data
Now that the data is imported, you can explore it using Cypher queries. For example, to get all nodes and relationships in the database, execute the following query:

```cypher
MATCH (s)-[p]->(o)
RETURN s, p, o
LIMIT 200;
```

Feel free to modify and execute other Cypher queries to analyze the data based on your research requirements.

## Note
Remember to stop and remove the Docker container when you are done with your research:

```
docker stop testneo4j
docker rm testneo4j
```


/etc/neo4j/neo4j.conf
dbms.memory.transaction.total.max=0

sudo -u root neo4j start

sudo -u root neo4j stop

CALL n10s.rdf.import.fetch(
  'file:///home/nu1/Desktop/1t%20Hard%20drive/shahenda/graph4code-master/scripts/stackoverflow_triples_3.nq',
  'N-Quads',
  {
    singleTx: false
  }
);





## Switching Databases
When switching between databases, follow these steps:

1. Stop the current Neo4j instance:
   ```bash
   sudo -u root neo4j stop
   ```

2. Edit the Neo4j configuration file using the command:
   ```bash
   kate /etc/neo4j/neo4j.conf
   ```

3. Search for the line that reads `initial.dbms.default_database=DocString`. Change the database name to the desired one.

4. Save and close the configuration file.

5. Start the Neo4j instance again:
   ```bash
   sudo -u root neo4j start
   ```

6. Access the Neo4j browser at http://localhost:7474/browser/ to work with the new database.

## Import Data from a Local File
To import data from a local file into the Neo4j database, you can use the `n10s` plugin. Here's how:

1. Open a web browser and navigate to the Neo4j browser at http://localhost:7474.


2. In the Neo4j browser, execute the following Cypher query to import the data from your local file:

   a. Initialize the `n10s` plugin configuration and create a constraint to ensure unique URIs for resources:
      ```cypher
      CALL n10s.graphconfig.init();
      CREATE CONSTRAINT n10s_unique_uri FOR (r:Resource) REQUIRE r.uri IS UNIQUE;
      ```

   b. Import the sample data 
   ```cypher
   CALL n10s.rdf.import.fetch(
     'file:///home/nu1/Desktop/1t%20Hard%20drive/shahenda/graph4code-master/scripts/stackoverflow_triples_3.nq',
     'N-Quads',
     {
       singleTx: false
     }
   );
      

Remember to modify the file path in the above query to point to the correct location of your local file.

## References
- Neo4j: https://neo4j.com/
- Graph4Code: https://github.com/wala/graph4code

