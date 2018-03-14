##Check the current state
`curl -u admin:admin 'http://52.138.182.88:7180/api/v10/clusters/brianblessouBD/services/hive'`

```
{
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
}
```

`curl -X POST -u admin:admin 'http://52.138.182.88:7180/api/v1/clusters/brianblessouBD/services/hive/commands/stop'
`
```
{
  "id" : 162,
  "name" : "Stop",
  "startTime" : "2018-03-14T09:50:02.366Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
```

`curl -X POST -u admin:admin 'http://52.138.182.88:7180/api/v1/clusters/brianblessouBD/services/hive/commands/start'`
```
{
  "id" : 166,
  "name" : "Start",
  "startTime" : "2018-03-14T09:51:28.636Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```