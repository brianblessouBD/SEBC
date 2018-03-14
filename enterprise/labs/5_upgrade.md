#Upgrade Cloudera using ClouderaManager

###Step 01: Collect Upgrade information
```
Set root account with password-less sudo permission
Version of CM:  Cloudera Enterprise Data Hub Edition Trial 5.9.3 (support -> about)
Version of jdk: 1.8. (support -> about)
Version fo CDH: CDH 5.9.3, (next to the name of the cluster, home page) 
Cluster installation: Parcels (next to the name of the cluster, home page)
Service enabled: HDFS, Hive, Hue, Oozie, YARN (MR2 Included) and ZooKeeper 	
Operating system Hosts: Distribution 	redhat 7.3                  
```

```
Stop Cloudera Management Service (home page)
Stop cloudera Manager server: sudo service cloudera-scm-server stop
Stop Cloudera Manager Agent: sudo service cloudera-scm-agent stop
```

######Create Backup for /etc/cloudera-scm-server and /etc/cloudera-scm-agent
`[brian@lion ~]$ sudo mkdir -p /backup/5.9.3/etc`
 
`[brian@lion ~]$ sudo cp -R /etc/cloudera-scm-server /backup/5.9.3/etc`

`[brian@lion ~]$ sudo cp -R /etc/cloudera-scm-agent /backup/5.9.3/etc`

`[brian@lion etc]$ sudo cp -R /etc/yum.repos.d /backup/5.9.3/etc/`

`[brian@lion ~]$ ls /backup/5.9.3/etc`
```
cloudera-scm-agent  cloudera-scm-server  yum.repos.d
```

#######Download the cloudera-manager.repo
`[brian@lion ~]$ wget https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo`

`[brian@lion ~]$ rm /etc/yum.repos.d/cloudera-manager.repo`

`[brian@lion ~]$ sudo mv cloudera-manager.repo /etc/yum.repos.d/`

######Upgrade the version of ClouderaManager
`[brian@lion ~]$ sudo yum clean all`
`[brian@lion ~]$ sudo yum upgrade cloudera-manager-server cloudera-manager-daemons cloudera-manager-agent`

######Remove rmp packages
`rpm -qa 'cloudera-manager-*'`

######Start cloudera Manager
`sudo service cloudera-scm-server start`

######Finish the installation with cloudera manager




