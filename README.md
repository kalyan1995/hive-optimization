# hive-optimization


https://community.hortonworks.com/articles/22419/hive-on-tez-performance-tuning-determining-reducer.html

set hive.vectorized.execution.enabled=true;
set hive.vectorized.execution.reduce.enabled=true;

Vectorization improves the performance by fetching 1,024 rows in a single operation instead of fetching single row each time. It improves the performance for operations like filter, join, aggregation, etc.

$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$

set hive.cbo.enable=true;
set hive.compute.query.using.stats=true;
set hive.stats.fetch.column.stats=true;
set hive.stats.fetch.partition.stats=true;

Hive optimizes each query's logical and physical execution plan before submitting for final execution. However, this is not based on the cost of the query during the initial version of Hive.

$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$

hive.exec.parallel=false
hive.exec.parallel.thread.number=8

Hive runs query plans in stages. 
Some stages depend on other stages and cannot be started until the previous stages have completed. 

However some other stages can run concurrently with others. Heving stages run in parallel can save the overall job running time. 
To enable parallel execution of stages, do

Parallel execution will increase the cluster utilization.
If the utilization of a cluster is already high, parallel execution will not help much in terms of overall performance.



$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$


set hive.tez.auto.reducer.parallelism = true;
hive.tez.auto.reducer.parallelism=true;
 
hive.tez.min.partition.factor=0.25;
 
hive.tez.max.partition.factor=2.0;
 
hive.exec.reducers.bytes.per.reducer=1073741824; // 1gb







$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$









$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$
