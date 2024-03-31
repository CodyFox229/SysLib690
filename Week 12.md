## Wordpress

Install
```
cd /var/www/html
sudo wget https://wordpress.org/latest.tar.gz
sudo tar -xzvf latest.tar.gz
```
User Setup 
```
create user 'wordpress'@'localhost' identified by 'XXXXXXXXX';
create database wordpress;
grant all privileges on wordpress.* to 'wordpress'@'localhost';
show databases;
\q
```
Username and Password saved locally

Not the biggest fan of wordpress. The GUI seems really clunky. 

Overall, fairly easy install. 
