## Install ImageMagick

```
sudo apt install imagemagick
```

## Enable and Restart Apache

```
sudo a2enmod rewrite

sudo systemctl restart apache2
```
## Omeka Install

Go to root menu, then go to MySQL

create user 'omeka'@'localhost'  
Password: Abc123Def!

```
create database omeka;
```

Give yourself user privleges

```
grant all privileges on omeka.* to 'omeka'@'localhost';
```
Database has been added

Find source for Omeka Download

```
sudo wget https://github.com/omeka/Omeka/releases/download/v3.1.2/omeka-3.1.2.zip
```

Had to install Unzip

```
sudo apt-get install unzip
```
Then renamed omeka-3.1.2 to omeka with ```sudo mv``` 

Configured and set permsissions 
```
sudo nano db.ini
```
Changed ownership location to HTML
```
sudo chown -R www-data:www-data /var/www/html/omeka/files
```
Restart the apache and mysql 

Had to re configure .install file to show error messages. Found out a missing letter in the username I gave MySQL didn't match what I had put into the db.ini file.
Relied heavily on the wordpress installation steps.

Had to install DOM extension as well. Threw an error after I fixed my user name problem. 
```
sudo apt-get install php-xml
```





