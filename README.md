# javaagent-instrumentation for spark

This is an instrumentation lib that aides in getting vital information from spark by
injecting custom byte code
This can help in deriving spark based pipeline leneages or gather DQ statistics evasively.

This lib can be run as agent and will magically gather statistic thereby avoiding 
writing custom code per pipeline

1. To compile the jar:\
`mvn package`

1. To instrument the application add the following JVM option:\
`-javaagent:spark-instrumentation-1.0-SNAPSHOT.jar=classes.cfg`

1. Example of classes.cfg - every classname should be on a separate line\
`org.apache.spark.api.java.JavaRDD`\
`org.apache.spark.SparkContext`\
`org.apache.spark.executor.Executor`\
`org.apache.spark.scheduler.TaskSetManager`\
`org.apache.spark.scheduler.DAGScheduler`\
``

1. Sample output:\
`org.apache.spark.SparkContext.broadcast(java.lang.Object,scala.reflect.ClassTag) : 174
 org.apache.spark.SparkContext.withScope(scala.Function0) : 1360
 org.apache.spark.SparkContext.parallelize(scala.collection.Seq,int,scala.reflect.ClassTag) : 1363
 Transforming: org/apache/spark/api/java/JavaRDD
 org.apache.spark.SparkContext.clean(java.lang.Object,boolean) : 247
 org.apache.spark.api.java.JavaRDD.filter(org.apache.spark.api.java.function.Function) : 52`
 
 
  