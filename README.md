LANGKAH-LANGKAH PRESTASHOP DARI AWAL SAMPE AKHIR
•	nano /etc/sources.list
deb http://ftp.debian.org/debian bookworm main contrib
deb-src http://ftp.debian.org/debian bookworm main contrib

•	apt update
•	apt upgrade
•	apt install openssh-server
•	nano /etc/ssh/sshd_config
hilangkan tanda #
•	MASUK KE CMD (OPSIONAL MAN TEMAN)
•	ssh (ip Debian) -l root
pilih yes
masukkan password Debian
•	apt install apache2 mariadb-server php php-mysql php-gd php-xml php-json
php-ldap php-zip php-imap php-mbstring php-intl libapache2-mod-php php-curl
•	mariadb -u root -p
masukkan password Debian
CREATE DATABASE prestashopdb;
Create user ‘rezza’@’localhost’identified by ‘12345678’;
GRANT ALL PRIVILEGES ON prestashopdb.*TO 'rezza'@'localhost' IDENTIFIED BY '12345678';
FLUSH PRIVILEGES;
(kalua dicreate user error tetep lanjut NAMA REZZA BISA DIGANTI DENGAN NAMA KALIAN )
•	cd /var/www/
•	mkdir prestashop (UNTUK BUAT DIREKTORY PRESTASHOP)
•	wgethttps://github.com/PrestaShop/PrestaShop/releases/download/8.1.2/prestashop_8.1.2.zip (SETELAH wget SPASI)
•	unzip prestashop_8.1.2.zip -d /var/www/prestashop
•	chown -R www-data:www-data /var/www/prestashop
•	chmod 755 -R /var/www/prestashop
•	a2enmod rewrite
•	cd /etc/apache2/sites-available/
•	cp 000-default.conf prestashop.conf
•	nano prestashop.conf
ServerName ukktkj.org
DocumentRoot /var/www/prestashop
ServerAdmin rezza@ukktkj.org

<Directory /var/www/prestashop>
AllowOverride All
Options +Indexes
Require all granted
</Directory>

ErrorLog ${APACHE_LOG_DIR}/prestashop.error.log
CustomLog ${APACHE_LOG_DIR}/prestashop.access.log combined
   </VirtualHost>
(YANG BAWAH ITU OPSIONAL BOLEH DITAMBAHKAN ATAU TIDAK)
•	a2ensite prestashop.conf
•	a2dissite 000-default.conf
•	systemctl restart apache2

lakukan perintah dibawah apabila tidak bisa login email diprestashop
•	cd /var/www/prestashop/
•	rm -rf install/
•	mv admin……../ admin-ukk/
DAN SELESAI KALAU ADA PROBLEM ATASI SENDIRI 🖕 🖕 🖕 🖕 🖕
