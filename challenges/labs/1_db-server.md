######A command and output that shows the hostname of your database server
```
[brian@elephant ~]$ hostname
elephant.cdh-bootcamp-bb
```

######A command and output that reports the database server version
```
[brian@elephant ~]$ mysql -uroot -proot

Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 13
Server version: 10.1.31-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> select version();
+-----------------+
| version()       |
+-----------------+
| 10.1.31-MariaDB |
+-----------------+
1 row in set (0.00 sec)

```

######A command and output that lists all the databases in the server

    scm
    rman
    hive
    oozie
    hue

```
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| hive               |
| hue                |
| information_schema |
| mysql              |
| nav                |
| navms              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
+--------------------+


```