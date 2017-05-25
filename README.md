### SQCFramework: The SPARQL Queries Containment Benchmark Generation Framework 
SQCFramework is SPARQL query containment benchmark generation framework which is able to generate customized SPARQL containment benchmarks from real SPARQL query logs. The framework is flexible enough to generate benchmarks of varying sizes and according to the user-defined criteria on the most important SPARQL features to be considered for query containment benchmarking. The generation of benchmarks is achieved by selecting prototypical queries (of a user-defined size and specialized selection criteria) using different clustering algorithms. 
### Existing Benchmarks
The existing benchmarks that we used in our evaluation is available from [here](https://github.com/AKSW/sqcframework/blob/master/SQCFrameWork-benchmarks.zip) 
### Generating Benchmarks from CLI
Download the folder [SQCFrameWork-cli](https://github.com/AKSW/sqcframework/tree/master/SQCFrameWork-cli) which contains a runable jar sqcframework.jar and a comtomized benchmark generation query file personalized-query.txt. From the folder run the following commands: 
```
### DBSCAN+Kmeans++ Format ### 
 java -jar sqcframwork.jar -m <method> -n <noQueries> -i <maxNoIterations> -t <noTrialRun> -e <endpointUrl> -q <queryPersonalized> -r <radius> -p <minPts> -o <outputFile>
An example format: 
java -jar sqcframework.jar   -m db+km++   -n 15   -i 10   -t 10   -e http://localhost:8890/sparql   -q ../SQCFramework/personalized-query.txt   -r 1   -p 1   -o db+km++-10supqueries-benchmark.ttl


### Kmeans++ Format ### 
 java -jar sqcframwork.jar -m <method> -n <noQueries> -i <maxNoIterations> -t <noTrialRun> -e <endpointUrl> -q <queryPersonalized> -o <outputFile>
An example format: 
java -jar sqcframework.jar   -m km++   -n 15   -i 10   -t 10   -e http://localhost:8890/sparql   -q ../SQCFramework/personalized-query.txt   -o km++-10supqueries-benchmark.ttl


### FEASIBLE Format ### 
 java -jar sqcframwork.jar -m <method> -n <noQueries> -e <endpointUrl> -q <queryPersonalized> -o <outputFile>
An example format: 
java -jar sqcframework.jar   -m feasible   -n 15  -e http://localhost:8890/sparql   -q ../SQCFramework/personalized-query.txt   -o feasible-10supqueries-benchmark.ttl


### Agglomerative Format ### 
 java -jar sqcframwork.jar -m <method> -n <noQueries> -e <endpointUrl> -q <queryPersonalized> -o <outputFile>
An example format: 
java -jar sqcframework.jar   -m agglomerative   -n 15  -e http://localhost:8890/sparql   -q ../SQCFramework/personalized-query.txt   -o agglomerative-10supqueries-benchmark.ttl

Where

noQueries = Number of super-queries in the benchmark
maxNoIterations = Maximum number of iterations for the KMeans++ clustering algorithm. In our evaluation we used maxNoIterations = 10. 
noTrialRun = Number of trial run for the KMeans++ clustering algorithm. In our evaluation we used noTrialRun = 10.
endpointURL = The LSQ endpoint URL containing containment relationships as well
queryPersonalized = The personalized query for costum benchmark generation
radius = Radius for the queries to be considered as outliers. In our evaluation we used radius = 1
minPts = Minimum points or queries in a cluster. In our evaluation we used min. points = 1
outputFile = The output TTL file where the resulting benchmark will be printed

```
### Generating Benchmarks from Source 
Download the source code from [here](https://github.com/AKSW/sqcframework/blob/master/SQCFramwework-src.7z). Unzip the folder which contains 4 -- Agglomerative, commons-math3, FEASIBLE, SQCFramework -- java projects. SQCFramework is the main project from where benchmarks can be generated. Note this project requires the other 3 project to be included in the build path. 
```
//Generate KMeans++ benchmarks from 
package org.aksw.simba.sqcbench.centroid
public class KmeansPlusPlus 

//Generate DBSCAN+KMeans++ benchmarks from 
package org.aksw.simba.sqcbench.hybrid
public class DbscanAndKMeansPluPlus 

//Generate FEASIBLE benchmarks from 
package org.aksw.simba.sqcframework.feasible
public class FEASIBLEClustering 

//You can also generate Agglomerative benchmarks from 
package org.aksw.simba.sqcbench.hierarchical
public class Agglomerative
However, Agglomerative clustering does not allow to generate fix number of clusters
```
Note the SQCFramework requires the LSQ dataset endpoint URL to be provided as input. We have provided the Virtuoso 7.2 endpoints both for SWDF and DBpedia datasets which can be downloaded from [here](http://hobbitdata.informatik.uni-leipzig.de/sqcframework-lsq-endpoints/). The Windows virtuoso endpoint can be started from bin/start.bt while linux can be started from bin/start_virtuoso.sh.  
Generating benchmarks using CLI will be added soon. 
### SPARQL Containment Solvers
We used four -- JSAC, TreeSolver, SPARQL-Algebra, AFMU -- SPARQL query containment solvers in our evaluation. Running these solvers can be found at [here](https://github.com/AKSW/jena-sparql-api/tree/master/benchmarking/sparqlqc-jena3). 
### LSQ Datasets
The LSQ datasets can be downloaded from [here](http://hobbitdata.informatik.uni-leipzig.de/lsq-dumps/)
### Complette Evaluation Results
Our complete evaluation results can be found [here](https://github.com/AKSW/sqcframework/blob/master/SQCFramework-Evaluation-Results.xlsx)
### Authors
  * [Muhammad Saleem](https://sites.google.com/site/saleemsweb/) (AKSW, University of Leipzig) 
  * [Claus Stadler](http://aksw.org/ClausStadler.html) (AKSW, University of Leipzig)
  * [Jens Lehmann](http://jens-lehmann.org/) (University of Bonn)
  * [Axel-Cyrille Ngonga Ngomo](http://aksw.org/AxelNgonga.html) (AKSW, University of Leipzig)
