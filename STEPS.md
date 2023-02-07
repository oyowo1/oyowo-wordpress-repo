STEPS FOLLOWED:

1. CREATE A MYSQL DATABASE WITH AMAZON RDSsudo apt-get update
2. CREATE AN EC2 INSTANCE
3. CONFIGURE YOUR AMAZON RDS DATABASE
4. CONFIGURE WORDPRESS ON EC2
5. EXPLORE YOUR NEW WEBSITE AND CLEAN UP

the following commands were used for updates and installations

sudo apt-get install apache2
sudo systemctl start apache2
sudo systemctl enable apache2
sudo apt-get install php libapache2-mod-php
sudo vi /etc/apache2/mods-enabled/dir.conf


Change the DirectoryIndex line to list index.php first
<IfModule mod_dir.c>
     DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>

sudo service apache2 restart
wget https://wordpress.org/latest.tar.gz
tar xzvf latest.tar.gz
sudo cp -r wordpress/* /var/www/html/
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
sudo mysql -u root -p
CREATE DATABASE wordpress;
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpressuser'@'localhost' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
EXIT;

sudo apt-get install php-mysql

sudo service apache2 restart

wget https://wordpress.org/latest.tar.gz
tar xzvf latest.tar.gz

sudo cp -r wordpress/* /var/www/html/

sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/

sudo mysql -u root -p
CREATE DATABASE wordpress;
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpressuser'@'localhost' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
EXIT;

Note: Replace wordpressuser with a unique database username, and replace password with a secure password.
