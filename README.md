Write the answers to these questions in the README.md doc of your GitHub repo:

Q:    How did changing values on the SparkSession property parameters affect the throughput and latency of the data?

A:Spark session property parameters will impact the scheduling and processing time for job.
Value for the following parameters impact the throughput which one can see with the value of processedRowsPerSecond.

spark.sql.shuffle.partitions
spark.streaming.kafka.maxRatePerPartition
spark.default.parallelism

Q:    What were the 2-3 most efficient SparkSession property key/value pairs? Through testing multiple variations on values, how can you tell these were the most optimal?

A:    I see following three paratmeters are important 
    *spark.conf.set("spark.sql.shuffle.partitions", 100)
    *spark.conf.set("spark.streaming.kafka.maxRatePerPartition", 10)
    *spark.conf.set("spark.default.parallelism",500)
    
 For above setting I find  processedRowsPerSecond varies with numInputRows and the different parameters. Clearly these  three parameters are key settings for optimization.
    
   Please find the information from my process.
   ********************************************************************************************
    2020-07-13 00:30:35 INFO  WriteToDataSourceV2Exec:54 - Data source writer org.apache.spark.sql.execution.streaming.sources.MicroBatchWriter@613aede5 committed.
2020-07-13 00:30:35 INFO  SparkContext:54 - Starting job: start at NativeMethodAccessorImpl.java:0
2020-07-13 00:30:35 INFO  DAGScheduler:54 - Job 1 finished: start at NativeMethodAccessorImpl.java:0, took 0.000064 s
2020-07-13 00:30:35 INFO  MicroBatchExecution:54 - Streaming query made progress: {
  "id" : "1ce3c8b7-fb37-49f4-a42c-92fa0719d9ac",
  "runId" : "18681840-d6d7-4980-8044-883072de47fa",
  "name" : null,
  "timestamp" : "2020-07-13T00:30:18.365Z",
  "batchId" : 0,
  "numInputRows" : 7440,
  "processedRowsPerSecond" : 440.78440665916224,
  "durationMs" : {
    "addBatch" : 12713,
    "getBatch" : 265,
    "getOffset" : 3308,
    "queryPlanning" : 531,
    "triggerExecution" : 16878,
    "walCommit" : 43
  },
  "eventTime" : {
    "avg" : "2018-12-30T02:37:25.185Z",
    "max" : "2018-12-31T23:57:00.000Z",
    "min" : "2018-12-28T07:16:00.000Z",
    "watermark" : "1970-01-01T00:00:00.000Z"
  },
  "stateOperators" : [ {
    "numRowsTotal" : 10798,
    "numRowsUpdated" : 10798,
    "memoryUsedBytes" : 3130027
  } ],