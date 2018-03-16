# Challenge 4 - HDFS Testing

######As user hilary, use teragen to generate a 65,536,000-record dataset 
```
[brian@horse ~]$ sudo su hilary
[hilary@horse brian]$ time hadoop jar /opt/cloudera/parcels/CDH-5.13.2-1.cdh5.13.2.p0.3/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -Dmapreduce.map.memory.mb=768 -Dmapreduce.reduce.memory.mb=768 -Dmapred.reduce.tasks=16 -Dmapred.map.tasks=16 -Ddfs.blocksize=64000000 65536 /user/hilary/tgen
18/03/16 11:07:13 INFO client.RMProxy: Connecting to ResourceManager at horse.cdh-bootcamp-bb/10.3.2.6:8032
18/03/16 11:07:13 INFO terasort.TeraGen: Generating 65536 using 16
18/03/16 11:07:14 INFO mapreduce.JobSubmitter: number of splits:16
18/03/16 11:07:14 INFO Configuration.deprecation: mapred.reduce.tasks is deprecated. Instead, use mapreduce.job.reduces
18/03/16 11:07:14 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
18/03/16 11:07:14 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1521197879731_0001
18/03/16 11:07:14 INFO impl.YarnClientImpl: Submitted application application_1521197879731_0001
18/03/16 11:07:14 INFO mapreduce.Job: The url to track the job: http://horse.cdh-bootcamp-bb:8088/proxy/application_1521197879731_0001/
18/03/16 11:07:14 INFO mapreduce.Job: Running job: job_1521197879731_0001
18/03/16 11:07:21 INFO mapreduce.Job: Job job_1521197879731_0001 running in uber mode : false
18/03/16 11:07:21 INFO mapreduce.Job:  map 0% reduce 0%
18/03/16 11:07:27 INFO mapreduce.Job:  map 25% reduce 0%
18/03/16 11:07:30 INFO mapreduce.Job:  map 38% reduce 0%
18/03/16 11:07:31 INFO mapreduce.Job:  map 50% reduce 0%
18/03/16 11:07:32 INFO mapreduce.Job:  map 75% reduce 0%
18/03/16 11:07:33 INFO mapreduce.Job:  map 94% reduce 0%
18/03/16 11:07:34 INFO mapreduce.Job:  map 100% reduce 0%
18/03/16 11:07:34 INFO mapreduce.Job: Job job_1521197879731_0001 completed successfully
18/03/16 11:07:34 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=2362230
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=1326
		HDFS: Number of bytes written=6553600
		HDFS: Number of read operations=64
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=32
	Job Counters 
		Launched map tasks=16
		Other local map tasks=16
		Total time spent by all maps in occupied slots (ms)=84788
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=84788
		Total vcore-milliseconds taken by all map tasks=84788
		Total megabyte-milliseconds taken by all map tasks=86822912
	Map-Reduce Framework
		Map input records=65536
		Map output records=65536
		Input split bytes=1326
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=1014
		CPU time spent (ms)=10630
		Physical memory (bytes) snapshot=3771912192
		Virtual memory (bytes) snapshot=21721825280
		Total committed heap usage (bytes)=7690256384
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=140678493208567
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=6553600

real	0m22.840s
user	0m6.239s
sys	0m0.363s
```

######The command and output of hdfs dfs -ls /user/hilary/tgen
```
[hilary@horse brian]$ hdfs dfs -ls /user/hilary/tgen
Found 17 items
-rw-r--r--   3 hilary hilary          0 2018-03-16 11:07 /user/hilary/tgen/_SUCCESS
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00000
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00001
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00002
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00003
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00004
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00005
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00006
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00007
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00008
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00009
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00010
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00011
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00012
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00013
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00014
-rw-r--r--   3 hilary hilary     409600 2018-03-16 11:07 /user/hilary/tgen/part-m-00015
```

######The command and output of hadoop fsck -blocks /user/hilary
```
[hilary@horse brian]$ hadoop fsck -blocks /user/hilary
DEPRECATED: Use of this script to execute hdfs command is deprecated.
Instead use the hdfs command for it.

Connecting to namenode via http://elephant.cdh-bootcamp-bb:50070/fsck?ugi=hilary&blocks=1&path=%2Fuser%2Fhilary
FSCK started by hilary (auth:SIMPLE) from /10.3.2.6 for path /user/hilary at Fri Mar 16 11:08:01 UTC 2018
.................Status: HEALTHY
 Total size:	6553600 B
 Total dirs:	3
 Total files:	17
 Total symlinks:		0
 Total blocks (validated):	16 (avg. block size 409600 B)
 Minimally replicated blocks:	16 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		4
 Number of racks:		1
FSCK ended at Fri Mar 16 11:08:01 UTC 2018 in 5 milliseconds


The filesystem under path '/user/hilary' is HEALTHY
```
