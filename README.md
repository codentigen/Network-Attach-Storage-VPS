
<h1 align="center">Nettwork Attach Storage VPS LAMP Project</h1>
<h5 align="center">Build with ❤️ by Eos Ageng</h5>
<h5 align="center">NAS(Network Attached Storage) Menggunakan Virtual Private Server dengan konfigurasi LAMP Stack di Ubuntu Server 20.04</h5>

#

## Requirements

 - [VPS Server ](https://awesomeopensource.com/project/elangosundar/awesome-README-templates)
 - [Basic command Linux](https://github.com/matiassingers/awesome-readme)
 - [Sabar dan jangan lupa Berdoa!](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)

#
## Step 1: Update Software Package

<p>Sebelum Instal LAMP stack Kita Update & Upgrade dahulu Server</P>

```bash
NB : Kalau sudah login sebagai root , tidak usah menggunakan sudo
```

```bash
  > sudo apt update
  > sudo apt upgrade
```
#
## Step 2: Install Apacahe Web Server


```bash
  > sudo apt install apache2 apache2-utils -y
```
cek status Apache
```bash
  > sudo systemctl status apache2
  
  ● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2022-04-11 11:31:31 CST; 2s ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 53003 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCCESS)
   Main PID: 53011 (apache2)
      Tasks: 55 (limit: 19072)
     Memory: 6.4M
     CGroup: /system.slice/apache2.service
             ├─53011 /usr/sbin/apache2 -k start
             ├─53012 /usr/sbin/apache2 -k start
             └─53013 /usr/sbin/apache2 -k star
```
Jika Apache Belum aktif bisa ketikan command di bawah ini :
```bash
  > sudo systemctl start apache2
```
Jangan lupa juga cek web server apache dengan Mengetikkan ip dari VPS kalian di website,
jika Sudah Muncul Gambar seperti di bawah ini tandannya Web Server Apache sudah aktif
dan siap digunakan!

<a href="https://ibb.co/jbvGXYF"><img src="https://i.ibb.co/LYz67yf/ubuntu-20-04-lamp-stack.webp" alt="ubuntu-20-04-lamp-stack" border="0"></a>

#
## Step 3: Install MariaDB Database Server

```bash
  > sudo apt install mariadb-server mariadb-client -y
```
cek status MariaDB
```bash
  > sudo systemctl status mariadb

  ● mariadb.service - MariaDB 10.3.22 database server
     Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2022-04-10 14:19:16 UTC; 18s ago
       Docs: man:mysqld(8)
             https://mariadb.com/kb/en/library/systemd/
   Main PID: 9161 (mysqld)
     Status: "Taking your SQL requests now..."
      Tasks: 31 (limit: 9451)
     Memory: 64.7M
     CGroup: /system.slice/mariadb.service
             └─9161 /usr/sbin/mysqld
```
Jika MariaDB belum aktif ketikkan command di bawah ini :

```bash
  > sudo systemctl start mariadb
```
Selanjutnya jalankan skrip keamanan yang disertakan. Ini mengubah beberapa opsi default yang kurang aman untuk hal-hal seperti login root jarak jauh dan pengguna sementara. 
agar akses database bisa lebih Aman

```bash
    > sudo mysql_secure_installation
```
<a href="https://ibb.co/4PH9PGB"><img src="https://i.ibb.co/18kh85H/Install-LAMP-stack-on-Ubuntu-20-04-Maria-DB-Database-server.webp" alt="Install-LAMP-stack-on-Ubuntu-20-04-Maria-DB-Database-server" border="0"></a>

#
## Step 4: Install PHP 7.4

Dalam Kasus ini saya Menggunakan PHP versi 7.4 karena lebih stabil dari versi 7.3 , agar NAS yang kita buat bisa berjalan normal kalian bisa install juga PHP yang sama dengan saya

```bash
    > sudo apt install php7.4 libapache2-mod-php7.4 php7.4-mysql php-common 
      php7.4-cli php7.4-common php7.4-json php7.4-opcache php7.4-readline 
```

Aktifkan PHP Module lalu restart Apache nya

```bash
    > sudo a2enmod php7.4
    > sudo systemctl restart apache2
```
Selanjutnya Aktifkan PHP-FPM beserta Module dan Cofiguration filenya, langkah pertama disable dulu php7.4 lalu install php-fpm
```bash
    > sudo a2dismod php7.4
```
Install php-fpm dan enable module + config
```bash
    > sudo apt install php7.4-fpm
    > sudo a2enmod proxy_fcgi setenvif
    > sudo a2enconf php7.4-fpm
    > sudo systemctl restart apache2
```
