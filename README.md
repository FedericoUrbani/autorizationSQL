MySQL Shell 8.0.28

Copyright (c) 2016, 2022, Oracle and/or its affiliates.
Oracle is a registered trademark of Oracle Corporation and/or its affiliates.
Other names may be trademarks of their respective owners.

Type '\help' or '\?' for help; '\quit' to exit.
 MySQL  JS > \sql
Switching to SQL mode... Commands end with ;
 MySQL  SQL > \connect root@localhost
Creating a session to 'root@localhost'
Fetching schema names for autocompletion... Press ^C to stop.
Your MySQL connection id is 54 (X protocol)
Server version: 8.0.28 MySQL Community Server - GPL
No default schema selected; type \use <schema> to set one.
 MySQL  localhost:33060+ ssl  SQL > CREATE USER 'developer'@'localhost' IDENTIFIED BY 'developer1';
Query OK, 0 rows affected (0.0366 sec)
 MySQL  localhost:33060+ ssl  SQL > CREATE USER 'viewer'@'localhost' IDENTIFIED BY 'developer1';
Query OK, 0 rows affected (0.0149 sec)
 MySQL  localhost:33060+ ssl  SQL > CREATE USER 'writer'@'localhost' IDENTIFIED BY 'developer1';
Query OK, 0 rows affected (0.0121 sec)
 MySQL  localhost:33060+ ssl  SQL > SELECT User from mysql.user;
+------------------+
| User             |
+------------------+
| developer        |
| hbstudent        |
| mysql.infoschema |
| mysql.session    |
| mysql.sys        |
| root             |
| springstudent    |
| viewer           |
| writer           |
+------------------+
9 rows in set (0.0004 sec)
 MySQL  localhost:33060+ ssl  SQL > CREATE ROLE 'app-developer', 'app_read', 'app_write';
Query OK, 0 rows affected (0.0116 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT ALL ON *.* TO 'app-developer';
Query OK, 0 rows affected (0.0159 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT SELECT ON *.* TO 'app_read';
Query OK, 0 rows affected (0.0129 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT INSERT, UPDATE, DELETE ON *.* TO 'app_write';
Query OK, 0 rows affected (0.0098 sec)
 MySQL  localhost:33060+ ssl  SQL > CREATE DATABASE IF NOT EXISTS newdb;
Query OK, 1 row affected (0.0139 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT ALL PRIVILEGES ON newdb . * TO 'developer'@'localhost';
Query OK, 0 rows affected (0.0124 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT SELECT ON newdb . * TO 'developer'@'localhost';
Query OK, 0 rows affected (0.0109 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT ALL PRIVILEGES ON newdb . * TO 'developer'@'localhost';
Query OK, 0 rows affected (0.0117 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT SELECT ON newdb . * TO 'viewer'@'localhost';
Query OK, 0 rows affected (0.0111 sec)
 MySQL  localhost:33060+ ssl  SQL > GRANT INSERT,UPDATE,DELETE ON newdb . * TO 'writer'@'localhost';
Query OK, 0 rows affected (0.0114 sec)

