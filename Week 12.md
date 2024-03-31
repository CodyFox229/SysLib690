## Wordpress

Install
```
cd /var/www/html
sudo wget https://wordpress.org/latest.tar.gz
sudo tar -xzvf latest.tar.gz
```
User Setup 

Switch to the root Linux user
Login as the MySQL root user

```
sudo su
mysql -u root

create user 'wordpress'@'localhost' identified by 'XXXXXXXXX';
create database wordpress;
grant all privileges on wordpress.* to 'wordpress'@'localhost';
show databases;
\q
```

Changing the Directory

```
cd /var/www/html/wordpress
sudo cp wp-config-sample.php wp-config.php
sudo nano wp-config.php
```


Username and Password saved locally

Not the biggest fan of wordpress. The GUI seems really clunky. 

Overall, fairly easy install. 
