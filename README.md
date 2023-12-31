# Music Influence
Creation of an Ontology and a Knowledge Graph that models the influences between different artists for the Knowledge Engineering exam of A.Y. 2022-2023.

# Authors
* Francesco Alfieri
* Daniele Marini

# Usage 
The ontology is in the file 'Protege_Ontology.ttl', and has to been opened with Protegé.

In order to query the Knowledge Graph we use a free and open source Java framework called Fuseki. 

The first thing to do is to clone the repository to have access to the data:

```shell
git clone https://github.com/KE-Project/music_influence.git
```

## Requirements

For running the query we first have to download fuseki: we can do that from [here](https://dlcdn.apache.org/jena/binaries/apache-jena-fuseki-4.8.0.zip).
After unzipping the file, access the directory:

```shell
cd PATH/apache-jena-fuseki-4.8.0
```

and start the server by running

```shell
java -jar fuseki-server.jar
```

After that the server can be reached on port 3030:  http://localhost:3030/

## Import of the data

After opening fuseki the first thing we have to do is to create a dataset selecting the following steps:
* select **add one**
    * choose a name
    * select the **In-memory – dataset** option
    * select **create dataset**


Now we can select :
* **add data**
* **select files** (we will select the following files)
    * **Protege_Ontology.ttl**
    * All the files inside **ChatGPT data** directory 
    * All the files inside **LinkedJazz data** directory
* **upload all**

# Query the Graph

At this point we can easly query the graph in the query section.
Here an example of query that returns the artists that collaborated with Louie_Bellson:


```shell
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix mi: <http://www.semanticweb.org/KEProject/MusicalInfluences#>

SELECT ?artistName WHERE {  
	mi:Louie_Bellson mi:collaboratedWith ?artist.
    ?artist rdfs:label ?artistName.
}
```


