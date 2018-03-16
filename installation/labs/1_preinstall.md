# CM Install Lab

##  System Configuration Checks
ssh-copy-id -i ~/.ssh/id_rsa.pub brian@52.138.194.82
ssh-copy-id -i ~/.ssh/id_rsa.pub brian@52.138.194.134
ssh-copy-id -i ~/.ssh/id_rsa.pub brian@52.138.192.49
ssh-copy-id -i ~/.ssh/id_rsa.pub brian@52.169.13.23
ssh-copy-id -i ~/.ssh/id_rsa.pub brian@52.178.195.11

##1. Add password for my user
`sudo nano /etc/sudoers.d/waagent`
```
brian ALL=(ALL) NOPASSWD:ALL
```

##2. Set hostname on all nodes
`sudo hostnamectl set-hostname <myname>`
 
`sudo nano /etc/sysconfig/network`
```
NETWORKING=yes
HOSTNAME=lion.cdh-bootcamp-bb

```
`sudo nano /etc/hosts`
```
10.3.12.4 lion.cdh-bootcamp-bb lion

10.3.12.5 elephant.cdh-bootcamp-bb elephant

10.3.12.8 horse.cdh-bootcamp-bb horse

10.3.12.7 monkey.cdh-bootcamp-bb monkey

10.3.12.6 tiger.cdh-bootcamp-bb tiger

```
`check with uname -a`

##3.Disable SE Linux
`sudo nano /etc/selinux/config`
```
SELINUX=disabled
```

##4. Disable iptables and firewalls
```
sudo su -
systemctl stop iptables
systemctl stop firewalld
systemctl disable firewalld
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

```

##5. Check vm.swappiness on all your nodes and set to 1
`cat /proc/sys/vm/swappiness`
```
30
```
##### Set to 1
`sudo sysctl -w vm.swappiness=1`

`sudo nano /etc/sysctl.conf`

`vm.swappiness=1`

         
##6. Show the mount attributes of your volume(s)
`[phadmin@monkey ~]$ lsblk `
```  NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
 fd0      2:0    1    4K  0 disk 
 sda      8:0    0   30G  0 disk 
 ├─sda1   8:1    0  500M  0 part /boot 
 └─sda2   8:2    0 29,5G  0 part /
 sdb      8:16   0   56G  0 disk 
 └─sdb1   8:17   0   56G  0 part /mnt/resource
```
    
##7. Disable transparent hugepage support on all nodes

`sudo nano /etc/rc.d/rc.local`
```
echo never > /sys/kernel/mm/transparent_hugepage/defrag
echo never > /sys/kernel/mm/transparent_hugepage/enabled
```
`sudo chmod +x /etc/rc.d/rc.local`
sudo mkdir /boot/grub
`sudo nano /boot/grub/grub.conf`
transparent_hugepage=never
`sudo grub2-mkconfig -o /boot/grub2/grub.cfg`

`sudo reboot`
###### Check if ti's done
`cat /sys/kernel/mm/transparent_hugepage/defrag`
```
always madvise [never]
                
```
           
##8. List your network interface configuration
`[root@monkey phadmin]# ip a`
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 00:0d:3a:b8:88:8b brd ff:ff:ff:ff:ff:ff
    inet 10.3.12.4/24 brd 10.3.12.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::20d:3aff:feb8:888b/64 scope link 
       valid_lft forever preferred_lft forever
```
    
##9. Show that forward and reverse host lookups are correctly resolved
`getent hosts`
```
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
10.3.12.4       lion.cdh-bootcamp-bb lion
10.3.12.5       elephant.cdh-bootcamp-bb elephant
10.3.12.8       horse.cdh-bootcamp-bb horse
10.3.12.7       monkey.cdh-bootcamp-bb monkey
10.3.12.6       tiger.cdh-bootcamp-bb tiger
```       
    
##10. ntpd service 
`sudo yum install ntp`

`sudo service ntpd start`
# Persist to the start
`sudo chkconfig ntpd on`
       
    
##11. nscd service
`sudo yum install nscd`
`sudo service nscd start`
# Persist to the start
`sudo chkconfig nscd on`
###### Check if ti's running
`sudo service nscd status`
       
        
    
##12. Install and configure MariaDB
######Add a MariaDB repo in /etc/yum.repos.d/ via nano
`[root@lion phadmin]# sudo nano /etc/yum.repos.d/MariaDB.repo`
```
[mariadb]
name = MariaDB
baseurl = http://yum.mariadb.org/10.1/centos7-amd64
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1
```
######Install MariaDB
`[root@lion phadmin]# sudo yum install MariaDB-server MariaDB-client`
    
######Stop MariaDB to config it
`[root@lion phadmin]# sudo service mariadb stop`
    
######Modify the /etc/my.cnf file to align with cloudera recommendations  
`[root@lion phadmin]# sudo nano /etc/my.cnf`
```
[mysqld]
transaction-isolation = READ-COMMITTED
# Disabling symbolic-links is recommended to prevent assorted security risks;
# to do so, uncomment this line:
# symbolic-links = 0
key_buffer = 16M
key_buffer_size = 32M
max_allowed_packet = 32M
thread_stack = 256K
thread_cache_size = 64
query_cache_limit = 8M
query_cache_size = 64M
query_cache_type = 1
max_connections = 550
#expire_logs_days = 10
#max_binlog_size = 100M
#log_bin should be on a disk with enough free space. Replace '/var/lib/mysql/mysql_binary_log' with an appropriate path for your system
#and chown the specified folder to the mysql user.
log_bin=/var/lib/mysql/mysql_binary_log
binlog_format = mixed
read_buffer_size = 2M
read_rnd_buffer_size = 16M
sort_buffer_size = 8M
join_buffer_size = 8M
# InnoDB settings
innodb_file_per_table = 1
innodb_flush_log_at_trx_commit  = 2
innodb_log_buffer_size = 64M
innodb_buffer_pool_size = 4G
innodb_thread_concurrency = 8
innodb_flush_method = O_DIRECT
innodb_log_file_size = 512M
[mysqld_safe]
log-error=/var/log/mariadb/mariadb.log
pid-file=/var/run/mariadb/mariadb.pid
```
######Enable mariadb @ boot 
`[root@lion phadmin]# sudo systemctl enable mariadb`
######Check if everything is fine
`[root@lion phadmin]# sudo systemctl list-unit-files | grep mariadb`
```
mariadb.service                               enabled
```



######start MariaDB to finish config
`[root@lion phadmin]# sudo service mariadb start`

sudo /usr/bin/mysql_secure_installation
#######Check status
`[root@lion phadmin]# sudo service mariadb status`
######Create script repository
 `[root@lion phadmin]# mkdir script`
######Script to create DB
`[root@lion phadmin]# sudo nano script/create_db.sql`
```
CREATE DATABASE cmserver DEFAULT CHARACTER SET utf8;
CREATE DATABASE rman DEFAULT CHARACTER SET utf8;
CREATE DATABASE metastore DEFAULT CHARACTER SET utf8;
CREATE DATABASE amon DEFAULT CHARACTER SET utf8;
CREATE DATABASE sentry DEFAULT CHARACTER SET utf8;
CREATE DATABASE nav DEFAULT CHARACTER SET utf8;
CREATE DATABASE navms DEFAULT CHARACTER SET utf8;
CREATE DATABASE hue DEFAULT CHARACTER SET utf8;
CREATE DATABASE oozie DEFAULT CHARACTER SET utf8;

GRANT ALL on cmserver.* TO 'cmserveruser'@'%' IDENTIFIED BY 'password';
GRANT ALL on rman.* TO 'rmanuser'@'%' IDENTIFIED BY 'password';
GRANT ALL on metastore.* TO 'hiveuser'@'%' IDENTIFIED BY 'password';
GRANT ALL on amon.* TO 'amonuser'@'%' IDENTIFIED BY 'password';
GRANT ALL on sentry.* TO 'sentryuser'@'%' IDENTIFIED BY 'password';
GRANT ALL on nav.* TO 'navuser'@'%' IDENTIFIED BY 'password';
GRANT ALL on navms.* TO 'navmsuser'@'%' IDENTIFIED BY 'password';
GRANT ALL on hue.* TO 'hueuser'@'%' IDENTIFIED BY 'password';
GRANT ALL on oozie.* TO 'oozieuser'@'%' IDENTIFIED BY 'password';
```

mysql -uroot -proot < script/create_db.sql
######Check if databases exist
`[root@lion phadmin]# mysql -uroot -proot`
```
> show databases;
```

##9. Install JDBC driver
`wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.40.tar.gz`

`tar zxvf mysql-connector-java-5.1.40.tar.gz`

`mkdir -p /usr/share/java`

`sudo cp mysql-connector-java-5.1.40/mysql-connector-java-5.1.40-bin.jar /usr/share/java/mysql-connector-java.jar`

##10. Set up Oracje JDK 1.8
######Download and put the jdk-8u161-linux-x64.tar.gz in your $HOME
`wget http://download.oracle.com/otn-pub/java/jdk/8u161-b12/2f38c3b165be4555a1fa6e98c45e0808/jdk-8u161-linux-x64.tar.gz --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie"`

`tar xvzf jdk-8u161-linux-x64.tar.gz`

`sudo mkdir /usr/java`

`sudo cp -R jdk1.8.0_161 /usr/java`

`sudo alternatives --install /usr/bin/java java  /usr/java/jdk1.8.0_161/bin/java 1000`

`sudo alternatives --install /usr/bin/javac javac  /usr/java/jdk1.8.0_161/bin/javac 1000`
###### Set JAVA_HOME and JRE_HOME
###### For all user except root
`sudo nano /etc/environment`
```
export JAVA_HOME=/usr/java/jdk1.8.0_161
export JRE_HOME=/usr/java/jdk1.8.0_161/jre
```
`sudo nano ~/.bash_profile`
```
PATH=$PATH:$HOME/.local/bin:$HOME/bin:$JAVA_HOME/bin:$JRE_HOME
export PATH
```
##### For root
`sudo su -`

`sudo nano ~/.bash_profile`
```
export JAVA_HOME=/usr/java/jdk1.8.0_161
export JRE_HOME=/usr/java/jdk1.8.0_161/jre
PATH=$PATH:$HOME/.local/bin:$HOME/bin:$JAVA_HOME/bin:$JRE_HOME
export PATH
```

##11. Check Python installation on all nodes
`[root@lion phadmin]# whereis python`

## Set up CM
###### Get content of this page
`https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo`
```
[cloudera-manager]
# Packages for Cloudera Manager, Version 5.9, on RedHat or CentOS 7 x86_64           	  
name=Cloudera Manager
baseurl=https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/5.9/
gpgkey =https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/RPM-GPG-KEY-cloudera    
gpgcheck = 1
```

######Maybe Start NTP service
sudo service ntpd start
######Copy that content into this directory
`sudo nano /etc/yum.repos.d/cloudera-manager.repo`
######Install CM daemons on all nodes inclusind lion
`sudo yum install cloudera-manager-daemons cloudera-manager-server`
######Prepare the database for CM
`sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql cmserver cmserveruser password`
######Start CM
`sudo service cloudera-scm-server start`
```
You can access to the log into /var/log/cloudera-scm-server
```
    
    


  
  

    









     

        
