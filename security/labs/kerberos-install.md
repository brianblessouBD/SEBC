######Create user brianblessouBD on all nodes
```
Created with Hue
Enable the sample data with the wizard
https://blog.puneethabm.com/configure-hadoop-security-with-cloudera-manager-using-kerberos/
Check if JDC is installed

```

######Install kerberos server on the same server of Cloudera Manager
`sudo yum -y install krb5-server krb5-libs krb5-auth-dialog krb5-workstation`

######Install kerberos client on the others nodes and the node where CM is installed
`sudo yum -y install krb5-workstation krb5-libs krb5-auth-dialog`

######Change Realm name and add parameter to renew keytab for the server installation
Change Realm Name > cdh-bootcamp-bb
Add parameters > max_life = 1d and max_renewable_life = 7d
`sudo nano /var/kerberos/krb5kdc/kdc.conf`

```
[kdcdefaults]
 kdc_ports = 88
 kdc_tcp_ports = 88

[realms]
 CDH-BOOTCAMP.BB = {
  #master_key_type = aes256-cts
  acl_file = /var/kerberos/krb5kdc/kadm5.acl
  dict_file = /usr/share/dict/words
  admin_keytab = /var/kerberos/krb5kdc/kadm5.keytab
  supported_enctypes = aes256-cts:normal aes128-cts:normal des3-hmac-sha1:normal arcfour-hmac:normal ca$
  max_life = 1d
  max_renewable_life = 7d
 }
```

######Config all clients
Add below properties in All Clients:
udp_preference_limit = 1
default_tgs_enctypes = arcfour-hmac
default_tkt_enctypes = arcfour-hmac
`sudo nano /etc/krb5.conf`

```
[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log

[libdefaults]
 default_realm = CDH-BOOTCAMP.BB
 dns_lookup_realm = false
 dns_lookup_kdc = false
 ticket_lifetime = 24h
 renew_lifetime = 7d
 forwardable = true
 udp_preference_limit = 1
 default_tgs_enctypes = arcfour-hmac
 default_tkt_enctypes = arcfour-hmac 

[realms] 
  CDH-BOOTCAMP.BB = {
  kdc = lion.cdh-bootcamp-bb
  admin_server = lion.cdh-bootcamp-bb
 }

[domain_realm]
   .cdh-bootcamp-bb = CDH-BOOTCAMP.BB
   cdh-bootcamp-bb = CDH-BOOTCAMP.BB
```

######Create the database using the kdb5_util utility. (Server)
`/usr/sbin/kdb5_util create -s`
```
Loading random data
Initializing database '/var/kerberos/krb5kdc/principal' for realm 'PUNEETHA.COM',
master key name 'K/M@PUNEETHA.COM'
You will be prompted for the database Master Password.
It is important that you NOT FORGET this password.
Enter KDC database master key: K/M@CDH-BOOTCAMP.BB
Re-enter KDC database master key to verify: K/M@CDH-BOOTCAMP.BB
K/M@CDH-BOOTCAMP.BBK/M@CDH-BOOTCAMP.BBK/M@CDH-BOOTCAMP.BB

K/M@CDH-BOOTCAMP.BB
```

######In Server, add cloudera-scm principal, it will be used by Cloudera Manager later to manage Hadoop principals.
`[brian@lion ~]$ sudo kadmin.local`

```
Authenticating as principal root/admin@CDH.BOOTCAMP.BB with password.
kadmin.local:  addprinc cloudera-scm@CDH.BOOTCAMP.BB
WARNING: no policy specified for cloudera-scm@CDH.BOOTCAMP.BB; defaulting to no policy
Enter password for principal "cloudera-scm@CDH.BOOTCAMP.BB": 
Re-enter password for principal "cloudera-scm@CDH.BOOTCAMP.BB": 
Principal "cloudera-scm@CDH.BOOTCAMP.BB" created.
```

######Add */admin and cloudera-scm to ACL(Access Control List), which gives privilege to add principals for admin and cloudera-scm principal
`sudo nano /var/kerberos/krb5kdc/kadm5.acl`
```
*/admin@CDH.BOOTCAMP.BB *
cloudera-scm@CDH.BOOTCAMP.BB admilc
```

######Adds the password policy to the database.
`[brian@lion ~]$ sudo kadmin.local`

```
Authenticating as principal root/admin@CDH.BOOTCAMP.BB with password.
kadmin.local:  addpol admin
kadmin.local:  addpol users
kadmin.local:  addpol hosts
kadmin.local:  exit
```

######Start Kerberos using the following commands
`[root@lion ~]# sudo service krb5kdc start`
```
Redirecting to /bin/systemctl start krb5kdc.service
```
`[root@lion ~]# sudo service kadmin start`
```
Redirecting to /bin/systemctl start kadmin.service
``` 

######Try kerberos
kinit cloudera-scm

######Finish installation with CM Web UI

######Go to STEP 5 https://www.cloudera.com/documentation/enterprise/latest/topics/cm_sg_s6_user_principals.html

SuperUser group to hdfs

`[root@elephant ~]# kadmin.local`
```
Authenticating as principal cloudera-scm/admin@CDH.BOOTCAMP.BB with password.
kadmin.local:  addprinc hdfs@CDH.BOOTCAMP.BB
WARNING: no policy specified for hdfs@CDH.BOOTCAMP.BB; defaulting to no policy
Enter password for principal "hdfs@CDH.BOOTCAMP.BB": 
Re-enter password for principal "hdfs@CDH.BOOTCAMP.BB": 
Principal "hdfs@CDH.BOOTCAMP.BB" created.
kadmin.local:  exit
```
`[root@elephant ~]# kinit hdfs`
```
Password for hdfs@CDH.BOOTCAMP.BB: 
```
######Step 07
`[root@elephant ~]# kadmin.local`

```
Authenticating as principal hdfs/admin@CDH.BOOTCAMP.BB with password.
kadmin.local:  addprinc brianblessouBD@CDH.BOOTCAMP.BB
WARNING: no policy specified for brianblessouBD@CDH.BOOTCAMP.BB; defaulting to no policy
Enter password for principal "brianblessouBD@CDH.BOOTCAMP.BB": 
Re-enter password for principal "brianblessouBD@CDH.BOOTCAMP.BB": 
Principal "brianblessouBD@CDH.BOOTCAMP.BB" created.
kadmin.local:  exit
```
`[root@elephant ~]# kinit brianblessou@CDH-BOOTCAMP.BB`
```
kinit: Cannot find KDC for realm "CDH-BOOTCAMP.BB" while getting initial credentials
```
`[root@elephant ~]# kinit brianblessouBD`
Password for brianblessouBD@CDH.BOOTCAMP.BB:

######Step 08
Check kerberos security
sudo su brianblessouBD
klist
hdfs dfs -ls => it works
kdestroy
hdfs dfs -ls => doesn't work

######Change Password
sudo passwd brianblessouBD





