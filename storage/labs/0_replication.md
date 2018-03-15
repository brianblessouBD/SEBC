#HDFS Lab: Replicate to another cluster on all nodes

######create a 500 MB file
`hadoop jar /opt/cloudera/parcels/CDH-5.9.3-1.cdh5.9.3.p0.4/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen 5000000 /user/brianblessouBD/teragen500MB`

```
18/03/15 04:56:08 INFO client.RMProxy: Connecting to ResourceManager at horse.cdh-bootcamp-bb/10.3.12.8:8032
18/03/15 04:56:08 INFO terasort.TeraSort: Generating 5000000 using 2
18/03/15 04:56:08 INFO mapreduce.JobSubmitter: number of splits:2
18/03/15 04:56:09 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1521029139363_0002
18/03/15 04:56:09 INFO impl.YarnClientImpl: Submitted application application_1521029139363_0002
18/03/15 04:56:09 INFO mapreduce.Job: The url to track the job: http://horse.cdh-bootcamp-bb:8088/proxy/application_1521029139363_0002/
18/03/15 04:56:09 INFO mapreduce.Job: Running job: job_1521029139363_0002
18/03/15 04:56:15 INFO mapreduce.Job: Job job_1521029139363_0002 running in uber mode : false
18/03/15 04:56:15 INFO mapreduce.Job:  map 0% reduce 0%
18/03/15 04:56:24 INFO mapreduce.Job:  map 50% reduce 0%
18/03/15 04:56:25 INFO mapreduce.Job:  map 100% reduce 0%
18/03/15 04:56:25 INFO mapreduce.Job: Job job_1521029139363_0002 completed successfully
18/03/15 04:56:25 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=246656
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=167
		HDFS: Number of bytes written=500000000
		HDFS: Number of read operations=8
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=4
	Job Counters 
		Launched map tasks=2
		Other local map tasks=2
		Total time spent by all maps in occupied slots (ms)=14185
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=14185
		Total vcore-seconds taken by all map tasks=14185
		Total megabyte-seconds taken by all map tasks=14525440
	Map-Reduce Framework
		Map input records=5000000
		Map output records=5000000
		Input split bytes=167
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=225
		CPU time spent (ms)=10790
		Physical memory (bytes) snapshot=738426880
		Virtual memory (bytes) snapshot=3162750976
		Total committed heap usage (bytes)=1140326400
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=10735710707299981
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=500000000
```

######Copy your partner's file to your target directory 
`Doesn't work because no link between VM`

######Browse the results

