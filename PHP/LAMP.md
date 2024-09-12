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

## REFERENCES
[1]. https://www.digitalocean.com/community/tutorials/how-to-install-lamp-stack-on-ubuntu

[2]. https://ubuntu.com/server/docs/get-started-with-lamp-applications
