apt update
apt upgrade
apt install openssh-server
apt install apache2 mariadb-server unzip php php-mysql php-gd php-xml php-json php-ldap php-zip php-imap php-mbstring php-intl libapache2-mod-php php-curl
php -v => 8.2
cd /var/www/html
nano infophp.php
<?php
phpinfo();
?>
systemctl restart apache2
systemctl status apache2
=>> cek browser =>ip debian/infophp.php

cd /etc/php => ls
cd 8.2
cd apache2 => ls
nano php.ini
ganti display_errors => yes
cd .. => ls
cd cli => ls
nano php.ini
ganti display_errors =>> yes
systemctl restart apache2
=>> cek browser =>ip debian/infophp.php

mysql -u root -p
create database prestashopdb;
create user 'reno'@'localhost'identified by '12345678';
grant all privileges on prestashopdb.* to 'reno'@'localhost'identified by '12345678';
flush privileges;
exit

cd /var/www/html
nano konek-db.php

<?php
$servername ="localhost";
$username ="reno";
$pswd ="12345678";
$database ="prestashopdb";

$koneksi =mysqli_connect($servername, $username, $pswd, $database);

if (!$koneksi){
	die("koneksi database gagal".mysqli_connect_error());
}

echo "koneksi database sukses";
mysqli_close($koneksi);

?>

systemctl restart apache2
=>> cek browser =>ip debian/konek-db.php

cd /var/www/html
apt isntall wget(bila tidak bisa install wget)
wget https://smkn1doko.sch.id/download/prestashop_8.1.2.zip
ls
unzip prestashop_8.1.2.zip
chown -R www-data:www-data /var/www/html
chmod -R 755/777 /var/www/html
a2enmod rewrite
cd /etc/apache2/sites-available/
cp 000-default.conf prestashop.conf
nano prestashop.conf

	ServerName ukktkj.org

        ServerAdmin reno@ukktkj.org
        DocumentRoot /var/www/html

	ErrorLog /var/log/apache2/prestashop.error.log
        CustomLog /var/log/apache2/prestashop.access.log combined

a2ensite prestashop.conf
a2dissite 000-default.conf
systemctl restart apache2

rm -rf install/ 
mv admin---/ admin/

https://tkj.smkn1doko.sch.id
