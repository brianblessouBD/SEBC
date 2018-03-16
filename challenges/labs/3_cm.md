#Challenge 3 - Install CDH 5.13.x

######The command and output for hdfs dfs -ls /user
```
[hdfs@horse brian]$ hdfs dfs -ls /user
Found 8 items
drwxr-xr-x   - admin  admin           0 2018-03-16 11:02 /user/admin
drwxr-xr-x   - anupam anupam          0 2018-03-16 11:04 /user/anupam
drwxr-xr-x   - hilary hilary          0 2018-03-16 11:04 /user/hilary
drwxrwxrwx   - mapred hadoop          0 2018-03-16 10:58 /user/history
drwxrwxr-t   - hive   hive            0 2018-03-16 10:58 /user/hive
drwxrwxr-x   - hue    hue             0 2018-03-16 10:59 /user/hue
drwxrwxr-x   - impala impala          0 2018-03-16 10:59 /user/impala
drwxrwxr-x   - oozie  oozie           0 2018-03-16 10:59 /user/oozie
```




######The command and output from the CM API call
```
[hdfs@horse brian]$ curl -u admin:admin 'http://52.138.194.82:7180/api/v14/hosts'
{
  "items" : [ {
    "hostId" : "0bef34a6-b122-41ca-a570-e0af4fc660aa",
    "ipAddress" : "10.3.2.5",
    "hostname" : "elephant.cdh-bootcamp-bb",
    "rackId" : "/default",
    "hostUrl" : "http://lion.cdh-bootcamp-bb:7180/cmf/hostRedirect/0bef34a6-b122-41ca-a570-e0af4fc660aa",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 29494411264
  }, {
    "hostId" : "39f9ff33-0009-419f-87c9-3d09fff542a4",
    "ipAddress" : "10.3.2.6",
    "hostname" : "horse.cdh-bootcamp-bb",
    "rackId" : "/default",
    "hostUrl" : "http://lion.cdh-bootcamp-bb:7180/cmf/hostRedirect/39f9ff33-0009-419f-87c9-3d09fff542a4",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 29494411264
  }, {
    "hostId" : "fcb1512b-e0e2-43cf-8718-669f7f0912d3",
    "ipAddress" : "10.3.2.4",
    "hostname" : "lion.cdh-bootcamp-bb",
    "rackId" : "/default",
    "hostUrl" : "http://lion.cdh-bootcamp-bb:7180/cmf/hostRedirect/fcb1512b-e0e2-43cf-8718-669f7f0912d3",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 29494411264
  }, {
    "hostId" : "d22241c2-d3b1-4191-b869-3cf63225e601",
    "ipAddress" : "10.3.2.9",
    "hostname" : "monkey.cdh-bootcamp-bb",
    "rackId" : "/default",
    "hostUrl" : "http://lion.cdh-bootcamp-bb:7180/cmf/hostRedirect/d22241c2-d3b1-4191-b869-3cf63225e601",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 29494411264
  }, {
    "hostId" : "75bf1e57-bbf4-45ab-a753-a40239605f55",
    "ipAddress" : "10.3.2.8",
    "hostname" : "tiger.cdh-bootcamp-bb",
    "rackId" : "/default",
    "hostUrl" : "http://lion.cdh-bootcamp-bb:7180/cmf/hostRedirect/75bf1e57-bbf4-45ab-a753-a40239605f55",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 29494411264
  } ]
}
```
```
[hdfs@horse brian]$ curl -u admin:admin 'http://52.138.194.82:7180/api/v8/clusters'
{
  "items" : [ {
    "name" : "cluster",
    "displayName" : "brianblessouBD",
    "version" : "CDH5",
    "fullVersion" : "5.13.2",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ]
  } ]
}
```

######The command and output from the CM API call ../api/v8/clusters/<githubName>/services
```
[hdfs@horse brian]$ curl -u admin:admin 'http://52.138.194.82:7180/api/v8/clusters/brianblessouBD/services'
{
  "items" : [ {
    "name" : "hive",
    "type" : "HIVE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://lion.cdh-bootcamp-bb:7180/cmf/serviceRedirect/hive",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HIVE_HIVEMETASTORES_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "HIVE_HIVESERVER2S_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hive"
  }, {
    "name" : "zookeeper",
    "type" : "ZOOKEEPER",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://lion.cdh-bootcamp-bb:7180/cmf/serviceRedirect/zookeeper",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "ZOOKEEPER_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "ZOOKEEPER_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "ZooKeeper"
  }, {
    "name" : "hue",
    "type" : "HUE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://lion.cdh-bootcamp-bb:7180/cmf/serviceRedirect/hue",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HUE_HUE_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hue"
  }, {
    "name" : "oozie",
    "type" : "OOZIE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://lion.cdh-bootcamp-bb:7180/cmf/serviceRedirect/oozie",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "OOZIE_OOZIE_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Oozie"
  }, {
    "name" : "impala",
    "type" : "IMPALA",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://lion.cdh-bootcamp-bb:7180/cmf/serviceRedirect/impala",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "IMPALA_ASSIGNMENT_LOCALITY",
      "summary" : "DISABLED"
    }, {
      "name" : "IMPALA_CATALOGSERVER_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "IMPALA_IMPALADS_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "IMPALA_STATESTORE_HEALTH",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Impala"
  }, {
    "name" : "yarn",
    "type" : "YARN",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://lion.cdh-bootcamp-bb:7180/cmf/serviceRedirect/yarn",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "YARN_JOBHISTORY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_NODE_MANAGERS_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_RESOURCEMANAGERS_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_USAGE_AGGREGATION_HEALTH",
      "summary" : "DISABLED"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "YARN (MR2 Included)"
  }, {
    "name" : "hdfs",
    "type" : "HDFS",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://lion.cdh-bootcamp-bb:7180/cmf/serviceRedirect/hdfs",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HDFS_BLOCKS_WITH_CORRUPT_REPLICAS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_DATA_NODES_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_FREE_SPACE_REMAINING",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_HA_NAMENODE_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_MISSING_BLOCKS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_UNDER_REPLICATED_BLOCKS",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "HDFS"
  } ]
}
```
