# javaagent-instrumentation for spark

A library, which also to instrument every method in the whitelisted class.\
It will print to stdout method names, which takes more than 50 milliseconds to run.

1. To compile the jar:\
`mvn package`

1. To instrument the application add the following JVM option:\
`-javaagent:java-instrumentation-1.0-SNAPSHOT.jar=classes.cfg`

1. Example of classes.cfg - every classname should be on a separate line\
`org.apache.spark.api.java.JavaRDD`\
`org.apache.spark.api.java.JavaRDD`\
``

1. Sample output:\
`org.apache.spark.SparkContext.broadcast(java.lang.Object,scala.reflect.ClassTag) : 174
 org.apache.spark.SparkContext.withScope(scala.Function0) : 1360
 org.apache.spark.SparkContext.parallelize(scala.collection.Seq,int,scala.reflect.ClassTag) : 1363
 Transforming: org/apache/spark/api/java/JavaRDD
 org.apache.spark.SparkContext.clean(java.lang.Object,boolean) : 247
 org.apache.spark.api.java.JavaRDD.filter(org.apache.spark.api.java.function.Function) : 52`
 
1. How to know which classes to include?\
 I am using debugger to understand which classes needs to be instrumented.
 
  