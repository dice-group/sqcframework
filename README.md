### SQCFramework: The SPARQL Queries Containment Benchmark Generation Framework 
SQCFramework is SPARQL query containment benchmark generation framework which is able to generate customized SPARQL containment benchmarks from real SPARQL query logs. The framework is flexible enough to generate benchmarks of varying sizes and according to the user-defined criteria on the most important SPARQL features to be considered for query containment benchmarking. The generation of benchmarks is achieved by selecting prototypical queries (of a user-defined size and specialized selection criteria) using different clustering algorithms. 
### Generating Benchmarks
Download the source code from [here](https://github.com/AKSW/sqcframework/blob/master/SQCFramwework-src.zip). Unzip the folder which contains 4 -- Agglomerative, commons-math3, FEASIBLE, SQCFramework -- java projects. SQCFramework is the main project from where benchmarks can be generated. Note this project requires the other 3 project to be included in the build path. 
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
### LSQ Datasets
The LSQ datasets can be downloaded from [here](http://hobbitdata.informatik.uni-leipzig.de/lsq-dumps/)
