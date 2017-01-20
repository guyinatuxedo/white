#Wordpress MySQL Password recovery

This writeup will only be good if your wordpress site uses a MySQL datbase to store it's passwords.

To start, you will need to generate a new password hash. To do this you can just create a file with the plain text password, then generate an md5 hash (since wordpress uses md5 hashing as it's default) using the correct formatters.
```
word@ubuntu:~$ echo 'password' > password
word@ubuntu:~$ tr -d '\r\n' < password | md5sum | tr -d ' -'
5f4dcc3b5aa765d61d8327deb882cf99
```

So we have our new password has "5f4dcc3b5aa765d61d8327deb882cf99". Now to log in to mysql and update it. You will need to replace the 'word' database with whatever database you have wordpress pulling from (if you forgot, you can check in "/var/www/html/wp-config.php"), in addition to the username, and the password hash. After that all of the table names will be the default.

```
word@ubuntu:~$ mysql -u root -p
```

One wall of text later...

```
mysql> use word;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> update wp_users set user_pass="5f4dcc3b5aa765d61d8327deb882cf99" where user_login = 'word';
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0
```

And just like that, the password is updated. When I go to log in, I see that it is indeed changed. Since all it was was just a database entry, we were able to go in and simply update the value. One more thing, here is the command to view all users.

```
mysql> select user_login from wp_users;
```
