#Verify user privileges

`[brian@lion ~]$ kinit`
```
Password for brian@CDH.BOOTCAMP.BB:
```
 
`[brian@elephant ~]$ beeline`

!connect jdbc:hive2://localhost:10000/default;principal=hive/fdqn@REALM.COM
localhost: Where is install hiveservers because principal it's hive => elephant.cdh-bootcamp-bb
fdqn@REALM.COM: elephant.cdh-bootcamp-bb@CDH.BOOTCAMP.BB 


```
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.9.3 by Apache Hive
beeline> !connect jdbc:hive2://elephant.cdh-bootcamp-bb:10000/default;principal=hive/elephant.cdh-bootcamp-bb@CDH.BOOTCAMP.BB
scan complete in 2ms
Connecting to jdbc:hive2://elephant.cdh-bootcamp-bb:10000/default;principal=hive/elephant.cdh-bootcamp-bb@CDH
Connected to: Apache Hive (version 1.1.0-cdh5.9.3)
Driver: Hive JDBC (version 1.1.0-cdh5.9.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20180315135959_9829c56e-fdb8-457b-bd43-fade0dbcda51): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20180315135959_9829c56e-fdb8-457b-bd43-fade0dbcda51); Time taken: 0.675 seconds
INFO  : Executing command(queryId=hive_20180315135959_9829c56e-fdb8-457b-bd43-fade0dbcda51): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315135959_9829c56e-fdb8-457b-bd43-fade0dbcda51); Time taken: 0.292 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (2.329 seconds)
```


`[brian@elephant ~]$ hdfs groups brian`
```
brian : brian
```


`[brian@elephant ~]$ beeline`
```
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> CREATE ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20180315140606_75484021-f299-4d2a-aed2-46c7d6f50654): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20180315140606_75484021-f299-4d2a-aed2-46c7d6f50654); Time taken: 0.081 seconds
INFO  : Executing command(queryId=hive_20180315140606_75484021-f299-4d2a-aed2-46c7d6f50654): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315140606_75484021-f299-4d2a-aed2-46c7d6f50654); Time taken: 0.579 seconds
INFO  : OK
No rows affected (0.674 seconds)
```
```
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20180315140606_bed8e991-8c7a-477f-9fc8-9f0ac40982c9): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20180315140606_bed8e991-8c7a-477f-9fc8-9f0ac40982c9); Time taken: 0.119 seconds
INFO  : Executing command(queryId=hive_20180315140606_bed8e991-8c7a-477f-9fc8-9f0ac40982c9): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315140606_bed8e991-8c7a-477f-9fc8-9f0ac40982c9); Time taken: 0.093 seconds
INFO  : OK
```
```
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> GRANT ROLE sentry_admin TO GROUP brian;
INFO  : Compiling command(queryId=hive_20180315142121_63afe074-7557-4fb1-a231-9e1babb762ef): GRANT ROLE sentry_admin TO GROUP brian
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20180315142121_63afe074-7557-4fb1-a231-9e1babb762ef); Time taken: 0.075 seconds
INFO  : Executing command(queryId=hive_20180315142121_63afe074-7557-4fb1-a231-9e1babb762ef): GRANT ROLE sentry_admin TO GROUP brian
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315142121_63afe074-7557-4fb1-a231-9e1babb762ef); Time taken: 0.089 seconds
INFO  : OK
No rows affected (0.177 seconds)
```
```
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20180315142121_c5d598fe-938a-4d75-abaa-b83f8e8a2c7e): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20180315142121_c5d598fe-938a-4d75-abaa-b83f8e8a2c7e); Time taken: 0.072 seconds
INFO  : Executing command(queryId=hive_20180315142121_c5d598fe-938a-4d75-abaa-b83f8e8a2c7e): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315142121_c5d598fe-938a-4d75-abaa-b83f8e8a2c7e); Time taken: 0.313 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.467 seconds)
```

######Create test roles
```
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> CREATE ROLE reads;
INFO  : Compiling command(queryId=hive_20180315143939_d77f46e0-69b4-47dd-9242-1c0f58b99677): CREATE ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20180315143939_d77f46e0-69b4-47dd-9242-1c0f58b99677); Time taken: 0.072 seconds
INFO  : Executing command(queryId=hive_20180315143939_d77f46e0-69b4-47dd-9242-1c0f58b99677): CREATE ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315143939_d77f46e0-69b4-47dd-9242-1c0f58b99677); Time taken: 0.057 seconds
INFO  : OK
```
```
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> CREATE ROLE writes;
INFO  : Compiling command(queryId=hive_20180315144040_e6104bdc-2007-42c5-838c-d0d1aea74249): CREATE ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20180315144040_e6104bdc-2007-42c5-838c-d0d1aea74249); Time taken: 0.086 seconds
INFO  : Executing command(queryId=hive_20180315144040_e6104bdc-2007-42c5-838c-d0d1aea74249): CREATE ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315144040_e6104bdc-2007-42c5-838c-d0d1aea74249); Time taken: 0.032 seconds
INFO  : OK
No rows affected (0.133 seconds)
```
```
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20180315144040_90429f04-1d87-4d95-a2d3-9d4dfea1eff9): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20180315144040_90429f04-1d87-4d95-a2d3-9d4dfea1eff9); Time taken: 0.069 seconds
INFO  : Executing command(queryId=hive_20180315144040_90429f04-1d87-4d95-a2d3-9d4dfea1eff9): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315144040_90429f04-1d87-4d95-a2d3-9d4dfea1eff9); Time taken: 0.038 seconds
INFO  : OK
No rows affected (0.119 seconds)
```
```
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20180315144141_9324bf68-a030-4aff-a1a7-b3904679451b): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20180315144141_9324bf68-a030-4aff-a1a7-b3904679451b); Time taken: 0.06 seconds
INFO  : Executing command(queryId=hive_20180315144141_9324bf68-a030-4aff-a1a7-b3904679451b): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315144141_9324bf68-a030-4aff-a1a7-b3904679451b); Time taken: 0.035 seconds
INFO  : OK
No rows affected (0.109 seconds)
```

######Grant INSERT privilege for default.sample07 to 'writes':
```
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20180315144343_ba98e641-61c2-488e-bfe4-d0165c5ed2d4): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20180315144343_ba98e641-61c2-488e-bfe4-d0165c5ed2d4); Time taken: 0.063 seconds
INFO  : Executing command(queryId=hive_20180315144343_ba98e641-61c2-488e-bfe4-d0165c5ed2d4): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315144343_ba98e641-61c2-488e-bfe4-d0165c5ed2d4); Time taken: 0.11 seconds
INFO  : OK
No rows affected (0.188 seconds)
```
```
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> GRANT INSERT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20180315144343_6c648e0f-d09b-42c4-8115-6f8f121da186): GRANT INSERT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20180315144343_6c648e0f-d09b-42c4-8115-6f8f121da186); Time taken: 0.061 seconds
INFO  : Executing command(queryId=hive_20180315144343_6c648e0f-d09b-42c4-8115-6f8f121da186): GRANT INSERT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315144343_6c648e0f-d09b-42c4-8115-6f8f121da186); Time taken: 0.07 seconds
INFO  : OK
No rows affected (0.148 seconds)
```
```
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20180315144343_5ca5d235-fc21-4704-ac1d-b371b16a283d): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20180315144343_5ca5d235-fc21-4704-ac1d-b371b16a283d); Time taken: 0.059 seconds
INFO  : Executing command(queryId=hive_20180315144343_5ca5d235-fc21-4704-ac1d-b371b16a283d): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315144343_5ca5d235-fc21-4704-ac1d-b371b16a283d); Time taken: 0.033 seconds
INFO  : OK
No rows affected (0.105 seconds)
```

######kinit as george, then login to beeline
`[brian@elephant ~]$ sudo su ferdinand`

`[ferdinand@elephant brian]$ klist`

```
Ticket cache: FILE:/tmp/krb5cc_1200
Default principal: ferdinand@CDH.BOOTCAMP.BB

Valid starting       Expires              Service principal
2018-03-15 14:34:23  2018-03-16 14:34:23  krbtgt/CDH.BOOTCAMP.BB@CDH.BOOTCAMP.BB
	renew until 2018-03-22 14:34:23
```

`[ferdinand@elephant brian]$ beeline`

```
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.9.3 by Apache Hive
beeline> !connect jdbc:hive2://elephant.cdh-bootcamp-bb:10000/default;principal=hive/elephant.cdh-bootcamp-bb@CDH.BOOTCAMP.BB
scan complete in 2ms
Connecting to jdbc:hive2://elephant.cdh-bootcamp-bb:10000/default;principal=hive/elephant.cdh-bootcamp-bb@CDH.BOOTCAMP.BB
Connected to: Apache Hive (version 1.1.0-cdh5.9.3)
Driver: Hive JDBC (version 1.1.0-cdh5.9.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> show tables;
INFO  : Compiling command(queryId=hive_20180315144444_aa5801f8-d797-45de-b4f3-3a113c50f2e3): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20180315144444_aa5801f8-d797-45de-b4f3-3a113c50f2e3); Time taken: 0.075 seconds
INFO  : Executing command(queryId=hive_20180315144444_aa5801f8-d797-45de-b4f3-3a113c50f2e3): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315144444_aa5801f8-d797-45de-b4f3-3a113c50f2e3); Time taken: 0.283 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.467 seconds)
```

`[brian@elephant ~]$ sudo su george`
`[george@elephant brian]$ klist`

```
klist: No credentials cache found (filename: /tmp/krb5cc_1100)
```
`[george@elephant brian]$ kinit`
```
Password for george@CDH.BOOTCAMP.BB:
```

`[george@elephant brian]$ beeline`

```
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.9.3 by Apache Hive
beeline> !connect jdbc:hive2://elephant.cdh-bootcamp-bb:10000/default;principal=hive/elephant.cdh-bootcamp-bb@CDH.BOOTCAMP.BB
scan complete in 2ms
Connecting to jdbc:hive2://elephant.cdh-bootcamp-bb:10000/default;principal=hive/elephant.cdh-bootcamp-bb@CDH.BOOTCAMP.BB
Connected to: Apache Hive (version 1.1.0-cdh5.9.3)
Driver: Hive JDBC (version 1.1.0-cdh5.9.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://elephant.cdh-bootcamp-bb:1000> show tables;
INFO  : Compiling command(queryId=hive_20180315144646_82d0566f-2cfc-4dbe-86d7-c6e474acc180): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20180315144646_82d0566f-2cfc-4dbe-86d7-c6e474acc180); Time taken: 0.071 seconds
INFO  : Executing command(queryId=hive_20180315144646_82d0566f-2cfc-4dbe-86d7-c6e474acc180): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20180315144646_82d0566f-2cfc-4dbe-86d7-c6e474acc180); Time taken: 0.245 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.413 seconds)
```



