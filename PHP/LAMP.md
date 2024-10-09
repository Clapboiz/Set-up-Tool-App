Install `LAMP`

Install web in this path `/var/www/html`.

Config db in `phpmyadmin`.

Config `username, password` to access mysql === `username, password` in file config code. (usually dbconnection.php, config.php)

Some command to check status.

```
tail -f /var/log/apache2/error.log
```

```
systemctl status mysql 
```

```
systemctl status apache2  
```

**If you have error:**

```
[Wed Oct 09 02:03:54.145442 2024] [php7:error] [pid 115047] [client 127.0.0.1:49212] PHP Fatal error:  Uncaught Error: Call to undefined function mysqli_connect() in /var/www/html/DVWA/dvwa/includes/DBMS/MySQL.php:13\nStack trace:\n#0 /var/www/html/DVWA/setup.php(23): include_once()\n#1 {main}\n  thrown in /var/www/html/DVWA/dvwa/includes/DBMS/MySQL.php on line 13, referer: http://127.0.0.1/DVWA/setup.php
```

**Fix:**

```
sudo apt update
sudo apt install php-mysql
```

## REFERENCES
[1]. https://www.digitalocean.com/community/tutorials/how-to-install-lamp-stack-on-ubuntu

[2]. https://ubuntu.com/server/docs/get-started-with-lamp-applications
