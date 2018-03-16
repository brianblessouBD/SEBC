#List the command and output for ls /etc/yum.repos.d

```
[brian@lion ~]$ ls /etc/yum.repos.d
epel.repo  epel-testing.repo  MariaDB.repo  redhat.repo  rh-cloud.repo
```

######List the full command and its output 
```
[brian@lion ~]$ sudo /usr/share/cmf/schema/scm_prepare_database.sh -h 10.3.2.5 mysql scm cmserveruser password
JAVA_HOME=/usr/java/jdk1.8.0_161
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.8.0_161/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
[                          main] DbCommandExecutor              INFO  Successfully connected to database.
All done, your SCM database is configured correctly!
```