##Latest available version
`[brian@lion ~]$ curl -u admin:admin 'http://52.138.182.88:7180/api/version'`
    ```
    v19
    ```

##Version upgraded
`[brian@lion ~]$ curl -u admin:admin 'http://52.138.182.88:7180/api/v19/cm/version'`
    
```
{
    "version" : "5.14.1",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20180207-1728",
    "gitHash" : "f253d8e2b9cf5cb61a2f1ba1bf71de6fb603add0",
    "snapshot" : false
}
```

##List all CM users
`[brian@lion ~]$ curl -u admin:admin 'http://52.138.182.88:7180/api/v10/users'`
```
{
  "items" : [ {
    "name" : "admin",
    "roles" : [ "ROLE_ADMIN" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  } ]
}
```

##Report the database server type in use by CM
`[brian@lion ~]$ curl -u admin:admin 'http://52.138.182.88:7180/api/v19/cm/scmDbInfo'`
```
{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}
```
