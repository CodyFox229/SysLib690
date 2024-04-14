## Installing Koha ILS

## Create a Firewall in Gcloud
Click on the hamburger ☰ icon at the top left.
Click on VPN Network
Click on Firewall
At the top of the page, choose Create a firewall rule (do not choose Create a firewall policy)
Add name: koha
Add description: open port 8080
Next to Targets, click on All instances in the network
In the Source IPv4 ranges, add 0.0.0.0/0
Click on Specified protocols and ports
Click on TCP
Add 8080 in the Ports box
Click on Create

## Server setup 
Run:
```
sudo apt upgrade
sudo apt autoremove -y && sudo apt clean
sudo apt install gnupg2
sudo reboot now
```

## Add Koha Repository
```
sudo su

echo 'deb http://debian.koha-community.org/koha stable main' | sudo tee /etc/apt/sources.list.d/koha.list

wget -q -O- https://debian.koha-community.org/koha/gpg.asc | sudo apt-key add -
```

## Install Koha
```
apt update
apt show koha-common
apt install koha-common
```

## Configure Koha
```
nano /etc/koha/koha-sites.conf
```
Change `INTRAPORT="80"` to `INTRAPORT="8080"`

Install and setup mysql-server:
```
sudo apt install default-mysql-server
mysqladmin -u root password bibliolib1
a2enmod rewrite
a2enmod cgi 
```
Restart Apache2:
```
systemctl restart apache2
```
Create a database for Koha:
```
koha-create --create-db bibliolib
nano /etc/apache2/ports.conf 
Listen 8080
apachectl configtest
systemctl restart apache2

a2dissite 000-default
a2enmod deflate
a2ensite bibliolib
systemctl reload apache2
systemctl restart apache2
```
## Koha Web Installer
```
nano /etc/koha/sites/bibliolib/koha-conf.xml

http://34.16.174.216:8080
```
Click on More in the top drop down box
Click on Administration
Click on Global System Preferences
Click on OPAC in the left hand side bar
Scroll down to the OPACBaseURL line.
Enter the IP address of your server: http://34.16.174.216
Click on Save all OPAC Preferences
