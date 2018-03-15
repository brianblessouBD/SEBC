#Sentry installation
https://www.cloudera.com/documentation/enterprise/latest/topics/sg_sentry_service_install.html

Database Host Name: elephant.cdh-bootcamp-bb
	
Database Type: Mysql
	
Database Name : sentryDB
	
Username: sentryuser
	
Password: password


https://www.cloudera.com/documentation/enterprise/latest/topics/sg_sentry_service_config.html#concept_z5b_42s_p4

######Before Enabling the Sentry Service
`[brian@elephant ~]$ sudo su hdfs`

`[hdfs@elephant brian]$ kinit`

`[hdfs@elephant brian]$ hdfs dfs -chmod -R 771 /user/hive/warehouse`

`[hdfs@elephant brian]$ hdfs dfs -chown -R hive:hive /user/hive/warehouse`


#####Disable impersonation for HiveServer2 
```
    1.Go to the Hive service.
    2.Click the Configuration tab.
    3.Select Scope > HiveServer2.
    4.Select Category > Main.
    5.Uncheck the HiveServer2 Enable Impersonation checkbox.
    6.Click Save Changes to commit the changes.
```

######Block the Hive CLI user from accessing the Hive metastore:
```
    1.In the Cloudera Manager Admin Console, select the Hive service.
    2.On the Hive service page, click the Configuration tab.
    3.In the search field, search for Hive Metastore Access Control and Proxy User Groups Override to locate the hadoop.proxyuser.hive.groups setting.
    4.Click the plus sign three times to add the following groups:
    
        hive
        hue
        sentry
```

######Enable the Sentry service for Hive
```
Enabling the Sentry Service for Hive

    Go to the Hive service.
    Click the Configuration tab.
    Select Scope > Hive (Service-Wide).
    Select Category > Main.
    Locate the Sentry Service property and select Sentry.
    Locate the Enable Stored Notifications in Database property and select it.
    Click Save Changes to commit the changes.
    Restart the Hive service.

Enabling Sentry on Hive service places several HiveServer2 properties on a restricted list properties that cannot be modified at runtime by clients. See HiveServer2 Restricted Properties.
```

######Enable the Sentry Service for Yarn
```
Open the Cloudera Manager Admin Console and go to the YARN service.
Click the Configuration tab.
Select Scope > NodeManager.
Select Category > Security.
Ensure the Allowed System Users property includes the hive user. If not, add hive.
Click Save Changes to commit the changes.
Repeat steps 1-6 for every NodeManager role group for the YARN service that is associated with Hive.
Restart the YARN service.
```

######Enable the Sentry service for hue
```
Enabling the Sentry Service for Hue

Hue uses a Security app to make it easier to interact with Sentry. When you set up Hue to manage Sentry permissions, make sure that users and groups are set up correctly. Every Hue user connecting to Sentry must have an equivalent OS-level user account on all hosts so that Sentry can authenticate Hue users. Each OS-level user should also be part of an OS-level group with the same name as the corresponding user's group in Hue.

For more information on using the Security app, see the related blog post.
Enable the Sentry service as follows:

    Enable the Sentry service for Hive and Impala (as instructed above).
    Go to the Hue service.
    Click the Configuration tab.
    Select Scope > Hue (Service-Wide).
    Select Category > Main.
    Locate the Sentry Service property and select Sentry.
    Click Save Changes to commit the changes.
    Restart Hue.
```
