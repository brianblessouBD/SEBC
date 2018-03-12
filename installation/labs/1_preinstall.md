# CM Install Lab

##  System Configuration Checks

    1. Check vm.swappiness on all your nodes 
    
        * Connect to one node
            <code>ssh phadmin@lion<\code>
        * Check the swappiness
            <code>[root@lion phadmin]# cat /proc/sys/vm/swappiness
                30
            </code>
        * Set swappiness to 1 if it's not
            <code>[phadmin@horse ~]$ sudo sysctl -w vm.swappiness=1<\code>
        * Set swappiness to 1 if it's not 
            <code>[phadmin@horse ~]$ vim /etc/sysctl.conf<\code>
            ``` # sysctl settings are defined through files in
            # /usr/lib/sysctl.d/, /run/sysctl.d/, and /etc/sysctl.d/.
            #
            # Vendors settings live in /usr/lib/sysctl.d/.
            # To override a whole file, create a new file with the same in
            # /etc/sysctl.d/ and put new settings there. To override
            # only specific settings, add a file with a lexically later
            # name in /etc/sysctl.d/ and put new settings there.
            #
            # For more information, see sysctl.conf(5) and sysctl.d(5).
            vm.swappiness = 1
            ```
         *  Do the same thing on every node
         
    2. Show the mount attributes of your volume(s)
        * <code>[phadmin@monkey ~]$ lsblk <\code>
           ```  NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
             fd0      2:0    1    4K  0 disk 
             sda      8:0    0   30G  0 disk 
             ├─sda1   8:1    0  500M  0 part /boot 
             └─sda2   8:2    0 29,5G  0 part /
             sdb      8:16   0   56G  0 disk 
             └─sdb1   8:17   0   56G  0 part /mnt/resource
           ```
    3. If you have ext-based volumes, list the reserve space setting
    
    4. Disable transparent hugepage support
        * check the file /sys/kernel/mm/transparent_hugepage/defrag
        <code>cat /sys/kernel/mm/transparent_hugepage/defrag<\code>
            ```
            [always] madvise never
            ```
        * If you have "[always] madvise never" you need to do :
           <code>echo never > /sys/kernel/mm/transparent_hugepage/defrag<\code>
        
        * check if it's done
            <code>cat /sys/kernel/mm/transparent_hugepage/defrag<\code>
                ```
                always madvise [never]
                
                ```
           
    5. List your network interface configuration
        * <code>[root@monkey phadmin]# ip a <\code>
            ```
            1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN qlen 1
                link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
                inet 127.0.0.1/8 scope host lo
                   valid_lft forever preferred_lft forever
                inet6 ::1/128 scope host 
                   valid_lft forever preferred_lft forever
            2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
                link/ether 00:0d:3a:b9:95:da brd ff:ff:ff:ff:ff:ff
                inet 10.3.9.5/24 brd 10.3.9.255 scope global eth0
                   valid_lft forever preferred_lft forever
                inet6 fe80::20d:3aff:feb9:95da/64 scope link 
                   valid_lft forever preferred_lft forever
            ```
    
    6. Show that forward and reverse host lookups are correctly resolved
       
       * List hosts
         <code>[root@monkey phadmin]# getent hosts<\code>
         ```
         127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
         127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
         13.79.240.255   lion
         40.69.93.114    elephant
         52.169.87.66    tiger
         52.138.203.99   elephant
         52.169.126.48   monkey
         ```
    
    6.
         * nscd => caching service
          
         * <code>[root@monkey phadmin]# sudo yum install nscd<\code>
          
         * <code>[root@monkey phadmin]# sudo service nscd start<\code>
          
         * <code>[root@monkey phadmin]# sudo chkconfig nscd on<\code>
          
         * <code>[root@monkey phadmin]# sudo service nscd status<\code>
    
    7. Show the ntpd service is running
        * Install ntp
        <code>[root@monkey phadmin]# yum install ntp<\code>
        ```Note: Forwarding request to 'systemctl is-enabled ntpd.service'.
        disabled
        ```
        * Enable to each boot the starting of ntpd
        <code>[root@monkey phadmin]# sudo chkconfig ntpd on<\code>
        ```Note: Forwarding request to 'systemctl enable ntpd.service'.
        Created symlink from /etc/systemd/system/multi-user.target.wants/ntpd.service to /usr/lib/systemd/system/ntpd.service.
        ```
        * Start service ntpd
        <code>[root@monkey phadmin]# sudo service ntpd start<\code>
        ```
        Redirecting to /bin/systemctl start ntpd.service
        ```
        * Check with ntpstat
        <code>[root@monkey phadmin]# ntpstat<\code>
        ```
        synchronised to NTP server (89.234.64.77) at stratum 3 
           time correct to within 975 ms
           polling server every 64 s
        ```
        * check list of server in ntp.conf file
        <code>[root@monkey phadmin]# sudo nano /etc/ntp.conf<\code>
        
    
    8. Install and configure MariaDB
        * Add a MariaDB repo in /etc/yum.repos.d/ via nano
            <code>[root@lion phadmin]# sudo nano /etc/yum.repos.d/MariaDB.repo<\code>
          ```
          [mariadb]
          name = MariaDB
          baseurl = http://yum.mariadb.org/10.1/centos7-amd64
          gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
          gpgcheck=1
          ```
        * Install MariaDB
            <code>[root@lion phadmin]# sudo yum install MariaDB-server MariaDB-client<\code>
        
        * Stop MariaDB to config it
            <code>[root@lion phadmin]# sudo service mariadb stop<\code>
        
        * Modify the /etc/my.cnf file to align with cloudera recommendations  
            <code>[root@lion phadmin]# sudo nano /etc/my.cnf<\code>
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
        * enable mariadb @ boot 
            <code>[root@lion phadmin]# sudo systemctl enable mariadb<\code>
        * Check if everything is fine
            <code>[root@lion phadmin]# sudo systemctl list-unit-files | grep mariadb<\code>
            ```
            mariadb.service                               enabled
            ```
        * start MariaDB to finish config
            <code>[root@lion phadmin]# sudo service mariadb start<\code>
        * Check status
            <code>[root@lion phadmin]# sudo service mariadb status<\code>
        * Set root password
            <code>[root@lion phadmin]# sudo /usr/bin/mysql_secure_installation<\code>
        * Create script repository
            <code>[root@lion phadmin]# mkdir script<\code>
        * Add line to create DB
            <code>[root@lion phadmin]# sudo nano /home/phadmin/script/create_db.sql<\code>
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
        * Check DB
            <code>[root@lion phadmin]# mysql -uroot -proot<\code>
            ```
            > show databases;
            ```
    9. Install JDBC
        * Go to /tmp
            <code>[root@lion phadmin]# cd /tmp/<\code>
        * Get mysql connectorr tar.gz from internet
            <code>[root@lion phadmin]# wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.40.tar.gz<\code>
        * Untar the tar.gz mysql connector
            <code>[root@lion phadmin]# tar zxvf mysql-connector-java-5.1.40.tar.gz<\code>
        * Create the directory /usr/share/java
            <code>[root@lion phadmin]# mkdir /usr/share/java<\code>
        * Copy the jar to /usr/share/java
            <code>[root@lion phadmin]# sudo cp mysql-connector-java-5.1.40/mysql-connector-java-5.1.40-bin.jar /usr/share/java/mysql-connector-java.jar<\code>
    
    10. Set up Oracje JDK 1.8
        * Download and put the jdk-8u161-linux-x64.tar.gz in your $HOME
        * Untar the tar.gz Jdk
            <code>[root@lion phadmin]# sudo tar zxvf jdk-8u161-linux-x64.tar.gz<\code>
        * Copy the folde jdk1.8.0_161 to /usr/java
            <code>[root@lion phadmin]# sudo cp jdk1.8.0_161/ -R /usr/java<\code>
        * Move this folder into /opt
            <code>[root@lion phadmin]# mv jdk1.8.0_161/ /opt<\code>
        * Configuration for Java
            <code>[root@lion phadmin]# sudo alternatives --install /usr/bin/java java  /usr/java/jdk1.8.0_152/bin/java 1000<\code>
        * Add JAVA_HOME and JRE_HOME in environment variables
            <code>[root@lion phadmin]# sudo nano /etc/environment<\code>
        * Set the PATH in the $HOME/.bash_profile
            <code>[root@lion phadmin]# sudo nano .bash_profile<\code>
    
    11. Check Python installation on all nodes
        * <code>[root@lion phadmin]# whereis python<\code>
        
    12. Disable ip tables
    * <code>[root@tiger ~]# systemctl stop firewalld<\code>
    * <code>[root@tiger ~]# systemctl disable firewalld<\code>
    * <code>[root@tiger ~]# iptables -F<\code>
    * <code>[root@tiger ~]# iptables -X<\code>
    * <code>[root@tiger ~]# iptables -t nat -F<\code>
    * <code>[root@tiger ~]# iptables -t nat -X<\code>
    * <code>[root@tiger ~]# iptables -t mangle -F<\code>
    * <code>[root@tiger ~]# iptables -t mangle -X<\code>
    * <code>[root@tiger ~]# iptables -P INPUT ACCEPT<\code>
    * <code>[root@tiger ~]# iptables -P FORWARD ACCEPT<\code>
    * <code>[root@tiger ~]# iptables -P OUTPUT ACCEPT<\code>
    
    


  
  

    









     

        
