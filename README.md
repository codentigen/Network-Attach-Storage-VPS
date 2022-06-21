
<h1 align="center">Nettwork Attach Storage VPS LAMP Project</h1>
<h5 align="center">Build with ❤️ by Eos Ageng</h5>
<h5 align="center">NAS(Network Attached Storage) Menggunakan Virtual Private Server dengan konfigurasi LAMP Stack di Ubuntu Server 20.04</h5>

#

## Requirements

 - [VPS Server ](https://awesomeopensource.com/project/elangosundar/awesome-README-templates)
 - [Basic command Linux](https://github.com/matiassingers/awesome-readme)
 - [Sabar dan jangan lupa Berdoa!](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)


## Step 1: Update Software Package

Sebelum Instal LAMP stack Kita Update & Upgrade dahulu Server

```bash
  > sudo apt update
  > sudo apt upgrade
```
NB : Kalau sudah login sebagai root , tidak usah menggunakan sudo

## Step 2: Install Apacahe Web Server


```bash
  > sudo apt install apache2 apache2-utils -y
```
cek status Apache
```bash
  > sudo systemctl status apache2
  
  ● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2020-04-11 11:31:31 CST; 2s ago
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

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)


## Step 3: Install MariaDB Database Server

```bash
  > sudo apt install mariadb-server mariadb-client -y
```
cek status MariaDB
```bash
  > sudo systemctl status mariadb

  ● mariadb.service - MariaDB 10.3.22 database server
     Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2020-04-10 14:19:16 UTC; 18s ago
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
Lalu Ketikk
