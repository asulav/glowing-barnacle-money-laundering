# Graph Theory & Neo4j
Using Graph Databases and Graph Theory

## Start Neo4j
```
docker run \
    --name testneo4j \
    -p7474:7474 -p7687:7687 \
    -d \
    -v $HOME/neo4j/data:/data \
    -v $HOME/neo4j/logs:/logs \
    -v $HOME/neo4j/import:/var/lib/neo4j/import \
    -v $HOME/neo4j/plugins:/plugins \
    --env NEO4J_AUTH=neo4j/test \
    neo4j:latest
```
#### Create Nodes:
```
CREATE (n: node:optionalLabel {data:"dataA", optionalData: "optionalDataB"}) return n
```
#### Create Edge:
```
MATCH (a:node {data:"a"}), (b:node {data: "b"})
CREATE (a)-[r1:next]->(b)
RETURN a
```
#### Delete Nodes and Relationships
```
MATCH p=()-[r:next]->() delete p
```
#### Delete Only Relationships
```
MATCH (n { name: 'a'})-[r:next]->()
DELETE r
```
