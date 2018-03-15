##HDFS Lab: Test HDFS Snapshots

`[brian@elephant ~]$ hdfs dfs -put SEBC.zip /precious/`
`[brian@elephant ~]$ sudo su hdfs`
`[hdfs@elephant brian]$ hdfs dfsadmin -allowSnapshot /precious`
```
Allowing snaphot on /precious succeeded
```

`[hdfs@elephant brian]$ hdfs dfs -createSnapshot /precious sebc-hdfs-test`

```
Created snapshot /precious/.snapshot/sebc-hdfs-test
```

`[hdfs@elephant brian]$ hdfs dfs -rm -R /precious`
```
rm: Failed to move to trash: hdfs://elephant.cdh-bootcamp-bb:8020/precious: The directory /precious cannot be deleted since /precious is snapshottable and already has snapshots
```

`[hdfs@elephant brian]$ hdfs dfs -rm /precious/SEBC.zip`
```
18/03/15 05:41:43 INFO fs.TrashPolicyDefault: Moved: 'hdfs://elephant.cdh-bootcamp-bb:8020/precious/SEBC.zip' to trash at: hdfs://elephant.cdh-bootcamp-bb:8020/user/hdfs/.Trash/Current/precious/SEBC.zip
```

`[hdfs@elephant brian]$ hdfs dfs -cp /precious/.snapshot/sebc-hdfs-test/SEBC.zip /precious/`
