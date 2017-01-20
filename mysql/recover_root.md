#MySQL

This is a writeup on how to recover the root password on a linux mysql database system. 

To start, you will want to turn off the mysql service. The full path to the mysql service is "/etc/init.d/mysql".

```
word@ubuntu:~$ sudo service mysql stop
```

Next you will want to star mysql in a mode that doesn't require a password for root.

```
word@ubuntu:~$ sudo mysqld_safe --skip-grant-tables &
[1] 2300
word@ubuntu:~$ 2017-01-20T03:28:24.123625Z mysqld_safe Logging to syslog.
2017-01-20T03:28:24.126370Z mysqld_safe Logging to '/var/log/mysql/error.log'.
2017-01-20T03:28:24.153016Z mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
```

Now just let that run in the background, and in a different terminal log in to the mysql server as root (without a password).

```
word@ubuntu:~$ mysql -u root
```

It shouldn't prompt you for the password. Now that you are in, you can go ahead and change the password.

```
mysql> use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> update user set authentication_string=PASSWORD("password") where User='root';
Query OK, 1 row affected, 1 warning (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 1

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)
```
On older versions, the "authentication_string" column might be replaced with "password".

Now you just need to log out of mysql, kill the mysql running in the background, restart the mysql service, then try the new password.

```
word@ubuntu:~$ sudo service mysql restart
[sudo] password for word: 
word@ubuntu:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4
Server version: 5.7.16-0ubuntu0.16.04.1 (Ubuntu)

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
```

And just like that, we reset the password.











