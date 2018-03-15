#HDFS Lab: Test HDFS throughput

######Create user brianblessouBD
`[brian@lion ~]$ sudo useradd -m brianblessouBD`

`[brian@lion ~]$ sudo su brianblessouBD`

######Create a 10 GB file using teragen

`[brianblessouBD@elephant brian]$ time hadoop jar /opt/cloudera/parcels/CDH-5.9.3-1.cdh5.9.3.p0.4/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -Dmapred.reduce.tasks=4 -Dmapred.map.tasks=4 -Ddfs.block.size=32000000 100000000 teragen10GB`

```
18/03/15 05:15:26 INFO client.RMProxy: Connecting to ResourceManager at horse.cdh-bootcamp-bb/10.3.12.8:8032
18/03/15 05:15:27 INFO terasort.TeraSort: Generating 100000000 using 4
18/03/15 05:15:27 INFO mapreduce.JobSubmitter: number of splits:4
18/03/15 05:15:27 INFO Configuration.deprecation: mapred.reduce.tasks is deprecated. Instead, use mapreduce.job.reduces
18/03/15 05:15:27 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
18/03/15 05:15:27 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
18/03/15 05:15:27 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1521029139363_0003
18/03/15 05:15:27 INFO impl.YarnClientImpl: Submitted application application_1521029139363_0003
18/03/15 05:15:27 INFO mapreduce.Job: The url to track the job: http://horse.cdh-bootcamp-bb:8088/proxy/application_1521029139363_0003/
18/03/15 05:15:27 INFO mapreduce.Job: Running job: job_1521029139363_0003
18/03/15 05:15:32 INFO mapreduce.Job: Job job_1521029139363_0003 running in uber mode : false
18/03/15 05:15:32 INFO mapreduce.Job:  map 0% reduce 0%
18/03/15 05:15:43 INFO mapreduce.Job:  map 6% reduce 0%
18/03/15 05:15:44 INFO mapreduce.Job:  map 13% reduce 0%
18/03/15 05:15:46 INFO mapreduce.Job:  map 17% reduce 0%
18/03/15 05:15:47 INFO mapreduce.Job:  map 22% reduce 0%
18/03/15 05:15:49 INFO mapreduce.Job:  map 26% reduce 0%
18/03/15 05:15:50 INFO mapreduce.Job:  map 30% reduce 0%
18/03/15 05:15:52 INFO mapreduce.Job:  map 35% reduce 0%
18/03/15 05:15:53 INFO mapreduce.Job:  map 38% reduce 0%
18/03/15 05:15:55 INFO mapreduce.Job:  map 40% reduce 0%
18/03/15 05:15:56 INFO mapreduce.Job:  map 42% reduce 0%
18/03/15 05:15:58 INFO mapreduce.Job:  map 43% reduce 0%
18/03/15 05:15:59 INFO mapreduce.Job:  map 44% reduce 0%
18/03/15 05:16:01 INFO mapreduce.Job:  map 45% reduce 0%
18/03/15 05:16:02 INFO mapreduce.Job:  map 47% reduce 0%
18/03/15 05:16:04 INFO mapreduce.Job:  map 48% reduce 0%
18/03/15 05:16:05 INFO mapreduce.Job:  map 50% reduce 0%
18/03/15 05:16:07 INFO mapreduce.Job:  map 51% reduce 0%
18/03/15 05:16:08 INFO mapreduce.Job:  map 53% reduce 0%
18/03/15 05:16:10 INFO mapreduce.Job:  map 54% reduce 0%
18/03/15 05:16:11 INFO mapreduce.Job:  map 56% reduce 0%
18/03/15 05:16:14 INFO mapreduce.Job:  map 59% reduce 0%
18/03/15 05:16:15 INFO mapreduce.Job:  map 62% reduce 0%
18/03/15 05:16:17 INFO mapreduce.Job:  map 66% reduce 0%
18/03/15 05:16:18 INFO mapreduce.Job:  map 70% reduce 0%
18/03/15 05:16:20 INFO mapreduce.Job:  map 73% reduce 0%
18/03/15 05:16:21 INFO mapreduce.Job:  map 76% reduce 0%
18/03/15 05:16:23 INFO mapreduce.Job:  map 78% reduce 0%
18/03/15 05:16:24 INFO mapreduce.Job:  map 80% reduce 0%
18/03/15 05:16:26 INFO mapreduce.Job:  map 81% reduce 0%
18/03/15 05:16:27 INFO mapreduce.Job:  map 83% reduce 0%
18/03/15 05:16:29 INFO mapreduce.Job:  map 84% reduce 0%
18/03/15 05:16:31 INFO mapreduce.Job:  map 86% reduce 0%
18/03/15 05:16:32 INFO mapreduce.Job:  map 87% reduce 0%
18/03/15 05:16:34 INFO mapreduce.Job:  map 89% reduce 0%
18/03/15 05:16:35 INFO mapreduce.Job:  map 90% reduce 0%
18/03/15 05:16:50 INFO mapreduce.Job:  map 91% reduce 0%
18/03/15 05:16:52 INFO mapreduce.Job:  map 95% reduce 0%
18/03/15 05:16:55 INFO mapreduce.Job:  map 96% reduce 0%
18/03/15 05:16:57 INFO mapreduce.Job:  map 100% reduce 0%
18/03/15 05:16:58 INFO mapreduce.Job: Job job_1521029139363_0003 completed successfully
18/03/15 05:16:58 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=493316
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=344
		HDFS: Number of bytes written=10000000000
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters 
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=326079
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=326079
		Total vcore-seconds taken by all map tasks=326079
		Total megabyte-seconds taken by all map tasks=333904896
	Map-Reduce Framework
		Map input records=100000000
		Map output records=100000000
		Input split bytes=344
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=1457
		CPU time spent (ms)=130070
		Physical memory (bytes) snapshot=1002831872
		Virtual memory (bytes) snapshot=6296412160
		Total committed heap usage (bytes)=1700265984
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=214760662691937609
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=10000000000

real	1m33.732s
user	0m5.619s
sys	0m0.367s
```

######Run the terasort command on this file 

`[brianblessouBD@elephant brian]$ time  hadoop jar /opt/cloudera/parcels/CDH-5.9.3-1.cdh5.9.3.p0.4/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort teragen10GB teraSort10GB`

```
18/03/15 05:21:31 INFO terasort.TeraSort: starting
18/03/15 05:21:32 INFO input.FileInputFormat: Total input paths to process : 4
Spent 184ms computing base-splits.
Spent 5ms computing TeraScheduler splits.
Computing input splits took 189ms
Sampling 10 splits of 316
Making 8 from 100000 sampled records
Computing parititions took 619ms
Spent 810ms computing partitions.
18/03/15 05:21:33 INFO client.RMProxy: Connecting to ResourceManager at horse.cdh-bootcamp-bb/10.3.12.8:8032
18/03/15 05:21:33 INFO mapreduce.JobSubmitter: number of splits:316
18/03/15 05:21:34 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1521029139363_0004
18/03/15 05:21:34 INFO impl.YarnClientImpl: Submitted application application_1521029139363_0004
18/03/15 05:21:34 INFO mapreduce.Job: The url to track the job: http://horse.cdh-bootcamp-bb:8088/proxy/application_1521029139363_0004/
18/03/15 05:21:34 INFO mapreduce.Job: Running job: job_1521029139363_0004
18/03/15 05:21:39 INFO mapreduce.Job: Job job_1521029139363_0004 running in uber mode : false
18/03/15 05:21:39 INFO mapreduce.Job:  map 0% reduce 0%
18/03/15 05:21:46 INFO mapreduce.Job:  map 1% reduce 0%
18/03/15 05:21:48 INFO mapreduce.Job:  map 3% reduce 0%
18/03/15 05:21:49 INFO mapreduce.Job:  map 4% reduce 0%
18/03/15 05:21:53 INFO mapreduce.Job:  map 5% reduce 0%
18/03/15 05:21:54 INFO mapreduce.Job:  map 6% reduce 0%
18/03/15 05:21:58 INFO mapreduce.Job:  map 8% reduce 0%
18/03/15 05:21:59 INFO mapreduce.Job:  map 9% reduce 0%
18/03/15 05:22:01 INFO mapreduce.Job:  map 10% reduce 0%
18/03/15 05:22:02 INFO mapreduce.Job:  map 11% reduce 0%
18/03/15 05:22:07 INFO mapreduce.Job:  map 13% reduce 0%
18/03/15 05:22:08 INFO mapreduce.Job:  map 14% reduce 0%
18/03/15 05:22:09 INFO mapreduce.Job:  map 15% reduce 0%
18/03/15 05:22:15 INFO mapreduce.Job:  map 16% reduce 0%
18/03/15 05:22:16 INFO mapreduce.Job:  map 18% reduce 0%
18/03/15 05:22:17 INFO mapreduce.Job:  map 20% reduce 0%
18/03/15 05:22:22 INFO mapreduce.Job:  map 21% reduce 0%
18/03/15 05:22:24 INFO mapreduce.Job:  map 22% reduce 0%
18/03/15 05:22:25 INFO mapreduce.Job:  map 24% reduce 0%
18/03/15 05:22:30 INFO mapreduce.Job:  map 25% reduce 0%
18/03/15 05:22:31 INFO mapreduce.Job:  map 26% reduce 0%
18/03/15 05:22:34 INFO mapreduce.Job:  map 28% reduce 0%
18/03/15 05:22:36 INFO mapreduce.Job:  map 29% reduce 0%
18/03/15 05:22:37 INFO mapreduce.Job:  map 30% reduce 0%
18/03/15 05:22:40 INFO mapreduce.Job:  map 31% reduce 0%
18/03/15 05:22:42 INFO mapreduce.Job:  map 32% reduce 0%
18/03/15 05:22:43 INFO mapreduce.Job:  map 33% reduce 0%
18/03/15 05:22:44 INFO mapreduce.Job:  map 34% reduce 0%
18/03/15 05:22:45 INFO mapreduce.Job:  map 35% reduce 0%
18/03/15 05:22:50 INFO mapreduce.Job:  map 37% reduce 0%
18/03/15 05:22:51 INFO mapreduce.Job:  map 38% reduce 0%
18/03/15 05:22:52 INFO mapreduce.Job:  map 39% reduce 0%
18/03/15 05:22:54 INFO mapreduce.Job:  map 40% reduce 0%
18/03/15 05:22:57 INFO mapreduce.Job:  map 41% reduce 0%
18/03/15 05:22:58 INFO mapreduce.Job:  map 43% reduce 0%
18/03/15 05:23:03 INFO mapreduce.Job:  map 44% reduce 0%
18/03/15 05:23:05 INFO mapreduce.Job:  map 45% reduce 0%
18/03/15 05:23:06 INFO mapreduce.Job:  map 46% reduce 0%
18/03/15 05:23:07 INFO mapreduce.Job:  map 47% reduce 0%
18/03/15 05:23:08 INFO mapreduce.Job:  map 48% reduce 0%
18/03/15 05:23:12 INFO mapreduce.Job:  map 49% reduce 0%
18/03/15 05:23:13 INFO mapreduce.Job:  map 50% reduce 0%
18/03/15 05:23:14 INFO mapreduce.Job:  map 51% reduce 0%
18/03/15 05:23:15 INFO mapreduce.Job:  map 52% reduce 0%
18/03/15 05:23:19 INFO mapreduce.Job:  map 53% reduce 0%
18/03/15 05:23:20 INFO mapreduce.Job:  map 54% reduce 0%
18/03/15 05:23:21 INFO mapreduce.Job:  map 55% reduce 0%
18/03/15 05:23:22 INFO mapreduce.Job:  map 56% reduce 0%
18/03/15 05:23:24 INFO mapreduce.Job:  map 57% reduce 0%
18/03/15 05:23:26 INFO mapreduce.Job:  map 58% reduce 0%
18/03/15 05:23:27 INFO mapreduce.Job:  map 59% reduce 0%
18/03/15 05:23:30 INFO mapreduce.Job:  map 60% reduce 0%
18/03/15 05:23:32 INFO mapreduce.Job:  map 61% reduce 0%
18/03/15 05:23:34 INFO mapreduce.Job:  map 62% reduce 0%
18/03/15 05:23:35 INFO mapreduce.Job:  map 63% reduce 0%
18/03/15 05:23:37 INFO mapreduce.Job:  map 64% reduce 0%
18/03/15 05:23:39 INFO mapreduce.Job:  map 65% reduce 0%
18/03/15 05:23:40 INFO mapreduce.Job:  map 66% reduce 0%
18/03/15 05:23:42 INFO mapreduce.Job:  map 67% reduce 0%
18/03/15 05:23:44 INFO mapreduce.Job:  map 68% reduce 0%
18/03/15 05:23:47 INFO mapreduce.Job:  map 70% reduce 0%
18/03/15 05:23:48 INFO mapreduce.Job:  map 71% reduce 0%
18/03/15 05:23:49 INFO mapreduce.Job:  map 72% reduce 0%
18/03/15 05:23:54 INFO mapreduce.Job:  map 74% reduce 0%
18/03/15 05:23:55 INFO mapreduce.Job:  map 75% reduce 0%
18/03/15 05:23:56 INFO mapreduce.Job:  map 76% reduce 0%
18/03/15 05:24:00 INFO mapreduce.Job:  map 77% reduce 0%
18/03/15 05:24:01 INFO mapreduce.Job:  map 78% reduce 0%
18/03/15 05:24:02 INFO mapreduce.Job:  map 79% reduce 0%
18/03/15 05:24:03 INFO mapreduce.Job:  map 80% reduce 0%
18/03/15 05:24:07 INFO mapreduce.Job:  map 81% reduce 0%
18/03/15 05:24:09 INFO mapreduce.Job:  map 82% reduce 0%
18/03/15 05:24:10 INFO mapreduce.Job:  map 83% reduce 0%
18/03/15 05:24:11 INFO mapreduce.Job:  map 84% reduce 0%
18/03/15 05:24:16 INFO mapreduce.Job:  map 85% reduce 0%
18/03/15 05:24:18 INFO mapreduce.Job:  map 85% reduce 2%
18/03/15 05:24:19 INFO mapreduce.Job:  map 86% reduce 8%
18/03/15 05:24:20 INFO mapreduce.Job:  map 86% reduce 11%
18/03/15 05:24:21 INFO mapreduce.Job:  map 86% reduce 15%
18/03/15 05:24:22 INFO mapreduce.Job:  map 87% reduce 17%
18/03/15 05:24:23 INFO mapreduce.Job:  map 87% reduce 19%
18/03/15 05:24:24 INFO mapreduce.Job:  map 87% reduce 20%
18/03/15 05:24:25 INFO mapreduce.Job:  map 87% reduce 23%
18/03/15 05:24:26 INFO mapreduce.Job:  map 88% reduce 23%
18/03/15 05:24:27 INFO mapreduce.Job:  map 88% reduce 24%
18/03/15 05:24:28 INFO mapreduce.Job:  map 88% reduce 26%
18/03/15 05:24:29 INFO mapreduce.Job:  map 89% reduce 26%
18/03/15 05:24:30 INFO mapreduce.Job:  map 90% reduce 26%
18/03/15 05:24:34 INFO mapreduce.Job:  map 91% reduce 26%
18/03/15 05:24:35 INFO mapreduce.Job:  map 92% reduce 26%
18/03/15 05:24:37 INFO mapreduce.Job:  map 92% reduce 27%
18/03/15 05:24:39 INFO mapreduce.Job:  map 93% reduce 27%
18/03/15 05:24:41 INFO mapreduce.Job:  map 94% reduce 27%
18/03/15 05:24:44 INFO mapreduce.Job:  map 95% reduce 27%
18/03/15 05:24:46 INFO mapreduce.Job:  map 96% reduce 28%
18/03/15 05:24:49 INFO mapreduce.Job:  map 97% reduce 28%
18/03/15 05:24:53 INFO mapreduce.Job:  map 98% reduce 28%
18/03/15 05:24:55 INFO mapreduce.Job:  map 99% reduce 28%
18/03/15 05:24:56 INFO mapreduce.Job:  map 99% reduce 29%
18/03/15 05:24:59 INFO mapreduce.Job:  map 100% reduce 29%
18/03/15 05:25:02 INFO mapreduce.Job:  map 100% reduce 52%
18/03/15 05:25:03 INFO mapreduce.Job:  map 100% reduce 57%
18/03/15 05:25:05 INFO mapreduce.Job:  map 100% reduce 62%
18/03/15 05:25:06 INFO mapreduce.Job:  map 100% reduce 66%
18/03/15 05:25:08 INFO mapreduce.Job:  map 100% reduce 71%
18/03/15 05:25:09 INFO mapreduce.Job:  map 100% reduce 72%
18/03/15 05:25:11 INFO mapreduce.Job:  map 100% reduce 77%
18/03/15 05:25:12 INFO mapreduce.Job:  map 100% reduce 79%
18/03/15 05:25:13 INFO mapreduce.Job:  map 100% reduce 80%
18/03/15 05:25:14 INFO mapreduce.Job:  map 100% reduce 83%
18/03/15 05:25:15 INFO mapreduce.Job:  map 100% reduce 84%
18/03/15 05:25:17 INFO mapreduce.Job:  map 100% reduce 87%
18/03/15 05:25:20 INFO mapreduce.Job:  map 100% reduce 90%
18/03/15 05:25:21 INFO mapreduce.Job:  map 100% reduce 91%
18/03/15 05:25:27 INFO mapreduce.Job:  map 100% reduce 92%
18/03/15 05:25:30 INFO mapreduce.Job:  map 100% reduce 96%
18/03/15 05:25:36 INFO mapreduce.Job:  map 100% reduce 97%
18/03/15 05:25:39 INFO mapreduce.Job:  map 100% reduce 98%
18/03/15 05:25:42 INFO mapreduce.Job:  map 100% reduce 99%
18/03/15 05:25:45 INFO mapreduce.Job:  map 100% reduce 100%
18/03/15 05:25:48 INFO mapreduce.Job: Job job_1521029139363_0004 completed successfully
18/03/15 05:25:48 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=4447760812
		FILE: Number of bytes written=8830824617
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=10000046136
		HDFS: Number of bytes written=10000000000
		HDFS: Number of read operations=972
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=16
	Job Counters 
		Launched map tasks=316
		Launched reduce tasks=8
		Data-local map tasks=316
		Total time spent by all maps in occupied slots (ms)=1999546
		Total time spent by all reduces in occupied slots (ms)=536924
		Total time spent by all map tasks (ms)=1999546
		Total time spent by all reduce tasks (ms)=536924
		Total vcore-seconds taken by all map tasks=1999546
		Total vcore-seconds taken by all reduce tasks=536924
		Total megabyte-seconds taken by all map tasks=2047535104
		Total megabyte-seconds taken by all reduce tasks=549810176
	Map-Reduce Framework
		Map input records=100000000
		Map output records=100000000
		Map output bytes=10200000000
		Map output materialized bytes=4342614671
		Input split bytes=46136
		Combine input records=0
		Combine output records=0
		Reduce input groups=100000000
		Reduce shuffle bytes=4342614671
		Reduce input records=100000000
		Reduce output records=100000000
		Spilled Records=200000000
		Shuffled Maps =2528
		Failed Shuffles=0
		Merged Map outputs=2528
		GC time elapsed (ms)=92091
		CPU time spent (ms)=1137530
		Physical memory (bytes) snapshot=173348573184
		Virtual memory (bytes) snapshot=511264432128
		Total committed heap usage (bytes)=232231272448
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=10000000000
	File Output Format Counters 
		Bytes Written=10000000000
18/03/15 05:25:48 INFO terasort.TeraSort: done

real	4m17.729s
user	0m7.557s
sys	0m0.473s
```