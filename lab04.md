login as: infs_ostrowskig
infs_ostrowskig@uwm-a008-36.uwm.edu.pl's password:
Access denied
infs_ostrowskig@uwm-a008-36.uwm.edu.pl's password:
Access denied
infs_ostrowskig@uwm-a008-36.uwm.edu.pl's password:
Linux bad2 4.10.17-1-pve #1 SMP PVE 4.10.17-16 (Tue, 11 Jul 2017 09:55:44 +0200)                                                     x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Mon Oct 30 11:26:43 2023 from 213.184.8.152
infs_ostrowskig@bad2:~$ mysql -u infs_ostrowskig -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1500
Server version: 8.0.22 MySQL Community Server - GPL

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use infs_ostrowskig
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+---------------------------+
| Tables_in_infs_ostrowskig |
+---------------------------+
| postac                    |
+---------------------------+
1 row in set (0.00 sec)

mysql> INSERT INTO postac (nazwa, rodzaj, data_ur, wiek) VALUES (('Bjorn', 'Droz
d', 'Tesciowa'), ('wiking','ptak','kobieta'),^C
mysql> ;
ERROR:
No query specified

mysql> show create table postac;
+--------+----------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    -----------+
| Table  | Create Table                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
+--------+----------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    -----------+
| postac | CREATE TABLE `postac` (
  `id_postaci` int NOT NULL AUTO_INCREMENT,
  `nazwa` varchar(40) NOT NULL,
  `rodzaj` enum('wiking','ptak','kobieta') DEFAULT NULL,
  `data_ur` date DEFAULT NULL,
  `wiek` int unsigned DEFAULT NULL,
  PRIMARY KEY (`id_postaci`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+--------+----------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    -----------+
1 row in set (0.01 sec)

mysql> describe postac;
+------------+---------------------------------+------+-----+---------+---------                                                    -------+
| Field      | Type                            | Null | Key | Default | Extra                                                              |
+------------+---------------------------------+------+-----+---------+---------                                                    -------+
| id_postaci | int                             | NO   | PRI | NULL    | auto_inc                                                    rement |
| nazwa      | varchar(40)                     | NO   |     | NULL    |                                                                    |
| rodzaj     | enum('wiking','ptak','kobieta') | YES  |     | NULL    |                                                                    |
| data_ur    | date                            | YES  |     | NULL    |                                                                    |
| wiek       | int unsigned                    | YES  |     | NULL    |                                                                    |
+------------+---------------------------------+------+-----+---------+---------                                                    -------+
5 rows in set (0.01 sec)

mysql> show create table postac;
+--------+----------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    -----------+
| Table  | Create Table                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
+--------+----------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    -----------+
| postac | CREATE TABLE `postac` (
  `id_postaci` int NOT NULL AUTO_INCREMENT,
  `nazwa` varchar(40) NOT NULL,
  `rodzaj` enum('wiking','ptak','kobieta') DEFAULT NULL,
  `data_ur` date DEFAULT NULL,
  `wiek` int unsigned DEFAULT NULL,
  PRIMARY KEY (`id_postaci`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+--------+----------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    --------------------------------------------------------------------------------                                                    -----------+
1 row in set (0.00 sec)

mysql>
mysql>
mysql> ;
ERROR:
No query specified

mysql> insert into postac values(default, "Bjorn", "wiking", "1700-10-23",323);I                                                    NSERT INTO postac (nazwa, rodzaj, data_ur, wiek) VALUES (('Bjorn', 'Droz
Query OK, 1 row affected (0.00 sec)

    '> ;
    '>
    '> ');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that                                                     corresponds to your MySQL server version for the right syntax to use near '' at                                                     line 4
mysql> desc posta
    -> ;
ERROR 1146 (42S02): Table 'infs_ostrowskig.posta' doesn't exist
mysql> desc postac
    -> ;
+------------+---------------------------------+------+-----+---------+---------                                                    -------+
| Field      | Type                            | Null | Key | Default | Extra                                                              |
+------------+---------------------------------+------+-----+---------+---------                                                    -------+
| id_postaci | int                             | NO   | PRI | NULL    | auto_inc                                                    rement |
| nazwa      | varchar(40)                     | NO   |     | NULL    |                                                                    |
| rodzaj     | enum('wiking','ptak','kobieta') | YES  |     | NULL    |                                                                    |
| data_ur    | date                            | YES  |     | NULL    |                                                                    |
| wiek       | int unsigned                    | YES  |     | NULL    |                                                                    |
+------------+---------------------------------+------+-----+---------+---------                                                    -------+
5 rows in set (0.00 sec)

mysql> select * from postac;
+------------+-------+--------+------------+------+
| id_postaci | nazwa | rodzaj | data_ur    | wiek |
+------------+-------+--------+------------+------+
|          1 | Bjorn | wiking | 1700-10-23 |  323 |
+------------+-------+--------+------------+------+
1 row i
mysql> insert into postac(nazwa, rodzaj, wiek, data_ur) values("Dawid", "wiking"                                                    ,30, "1993_04-01");
Query OK, 1 row affected (0.00 sec)

mysql> select * from postac;
+------------+-------+--------+------------+------+
| id_postaci | nazwa | rodzaj | data_ur    | wiek |
+------------+-------+--------+------------+------+
|          1 | Bjorn | wiking | 1700-10-23 |  323 |
|          2 | Dawid | wiking | 1993-04-01 |   30 |
+------------+-------+--------+------------+------+
2 rows in set (0.00 sec)

mysql> delete from postac where id_postaci=2;
Query OK, 1 row affected (0.02 sec)

mysql> select * from postac;
+------------+-------+--------+------------+------+
| id_postaci | nazwa | rodzaj | data_ur    | wiek |
+------------+-------+--------+------------+------+
|          1 | Bjorn | wiking | 1700-10-23 |  323 |
+------------+-------+--------+------------+------+
1 row in set (0.00 sec)

mysql> insert into postac values(default, "Drozd", "ptak", "1900-05-21", 123);
Query OK, 1 row affected (0.00 sec)

mysql> insert into postac values(default, "Tesciowa", "kobieta", "1935-03-06", 8                                                    8);
Query OK, 1 row affected (0.01 sec)

mysql> show * from postac
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that                                                     corresponds to your MySQL server version for the right syntax to use near '* fro                                                    m postac' at line 1
mysql> select * from postac;
+------------+----------+---------+------------+------+
| id_postaci | nazwa    | rodzaj  | data_ur    | wiek |
+------------+----------+---------+------------+------+
|          1 | Bjorn    | wiking  | 1700-10-23 |  323 |
|          3 | Drozd    | ptak    | 1900-05-21 |  123 |
|          4 | Tesciowa | kobieta | 1935-03-06 |   88 |
+------------+----------+---------+------------+------+
3 rows in set (0.00 sec)

mysql> update postac set id_postaci=2 where id_postaci=3;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> update postac set id_postaci=3 where id_postaci=4;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from postac;
+------------+----------+---------+------------+------+
| id_postaci | nazwa    | rodzaj  | data_ur    | wiek |
+------------+----------+---------+------------+------+
|          1 | Bjorn    | wiking  | 1700-10-23 |  323 |
|          2 | Drozd    | ptak    | 1900-05-21 |  123 |
|          3 | Tesciowa | kobieta | 1935-03-06 |   88 |
+------------+----------+---------+------------+------+
3 rows in set (0.00 sec)

mysql> update postac set wiek=88 where id_postaci=2;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> create table (
    -> id_walizki int primary key auto_increment,
    -> pojemnosc int unsigned,
    -> kolor enum("rozowy", "czerwony", "teczowy", "zolty"),
    -> id_wlasciciela int,
    -> foreign key(id_wlasciciela) references postac(id_postaci) on delete casca                                                    de);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your                                 MySQL server version for the right syntax to use near '(
id_walizki int primary key auto_increment,
pojemnosc int unsigned,
kolor enum(' at line 1
mysql> create table (id_walizki int primary key auto_increment,
    -> pojemnosc int unsigned,
    -> kolor enum('rozowy', 'czerwony', 'teczowy', 'zolty'),
    -> id_wlasciciela int;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your                                 MySQL server version for the right syntax to use near '(id_walizki int primary key auto_increment,
pojemnosc int unsigned,
kolor enum('' at line 1
mysql> create table walizka (id_walizki int primary key auto_increment, pojemnosc int unsigned, kolo
r enum('rozowy', 'czerwony', 'teczowy', 'zolty'), id_wlasciciela int,
    -> foreign key(id_wlasciciela) references postac(id_postaci) on delete cascade);
Query OK, 0 rows affected (0.18 sec)

mysql> selcet * from walizka
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your                                 MySQL server version for the right syntax to use near 'selcet * from walizka' at line 1
mysql> selcet * from walizka;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your                                 MySQL server version for the right syntax to use near 'selcet * from walizka' at line 1
mysql> select * from walizka;
Empty set (0.01 sec)
       show create table postac;
+--------+------------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ------------------------------------------------+
| Table  | Create Table                                                                                                                                                                                                                                                                                                                                                                                                                                     |
+--------+------------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ------------------------------------------------+
| postac | CREATE TABLE `postac` (
  `id_postaci` int NOT NULL AUTO_INCREMENT,
  `nazwa` varchar(40) NOT NULL,
  `rodzaj` enum('wiking','ptak','kobieta') DEFAULT NULL,
  `data_ur` date DEFAULT NULL,
  `wiek` int unsigned DEFAULT NULL,
  PRIMARY KEY (`id_postaci`)
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+--------+------------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ------------------------------------------------+
1 row in set (0.00 sec)

mysql> show create table walizka;
+---------+-----------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ---------------------------------------------------------------------------------+
| Table   | Create Table                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
+---------+-----------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ---------------------------------------------------------------------------------+
| walizka | CREATE TABLE `walizka` (
  `id_walizki` int NOT NULL AUTO_INCREMENT,
  `pojemnosc` int unsigned DEFAULT NULL,
  `kolor` enum('rozowy','czerwony','teczowy','zolty') DEFAULT NULL,
  `id_wlasciciela` int DEFAULT NULL,
  PRIMARY KEY (`id_walizki`),
  KEY `id_wlasciciela` (`id_wlasciciela`),
  CONSTRAINT `walizka_ibfk_1` FOREIGN KEY (`id_wlasciciela`) REFERENCES `postac` (`id_postaci`) ON D                                ELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+---------+-----------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ----------------------------------------------------------------------------------------------------                                ---------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> alter table walizka alter kolor set default "rozowy";
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> insert into walizka values(default, 10, 'czerwony', 1);
Query OK, 1 row affected (0.01 sec)

mysql> insert into walizka values(default, 20, default, 3);
Query OK, 1 row affected (0.01 sec)

mysql> select * from walizka;
+------------+-----------+----------+----------------+
| id_walizki | pojemnosc | kolor    | id_wlasciciela |
+------------+-----------+----------+----------------+
|          1 |        10 | czerwony |              1 |
|          2 |        20 | rozowy   |              3 |
+------------+-----------+----------+----------------+
2 rows in set (0.00 sec)

mysql> create table 'izba' (
    -> adres_budynku ...,
    -> nazwa_izby ...,
    -> );
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''izba' (
adres_budynku ...,
nazwa_izby ...,
)' at line 1
mysql> create table 'izba' (
    -> adres_budynku varchar(100),
    -> nazwa_budynku varchar(100),
    -> primary key(adres_budynku, nazwa_izby),
    -> metraz int unsigned,
    -> wlasciciel int,
    -> foreign key(wlasciciel) references postac(id_postaci) on delete set null);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''izba' (
adres_budynku varchar(100),
nazwa_budynku varchar(100),
primary key(adr' at line 1
mysql> create table izba ( adres_budynku varchar(100), nazwa_budynku varchar(100), primary key(adres_budynku, nazwa_izby), metraz int unsigned, wlasciciel int, foreign key(wlasciciel) references postac(id_postaci) on delete set null);
ERROR 1072 (42000): Key column 'nazwa_izby' doesn't exist in table
mysql> create table izba ( adres_budynku varchar(100), nazwa_izby varchar(100), primary key(adres_budynku, nazwa_izby), metraz int unsigned, wlasciciel int, foreign key(wlasciciel) references postac(id_postaci) on delete set null);
Query OK, 0 rows affected (0.07 sec)

mysql> describe izba;
+---------------+--------------+------+-----+---------+-------+
| Field         | Type         | Null | Key | Default | Extra |
+---------------+--------------+------+-----+---------+-------+
| adres_budynku | varchar(100) | NO   | PRI | NULL    |       |
| nazwa_izby    | varchar(100) | NO   | PRI | NULL    |       |
| metraz        | int unsigned | YES  |     | NULL    |       |
| wlasciciel    | int          | YES  | MUL | NULL    |       |
+---------------+--------------+------+-----+---------+-------+
4 rows in set (0.01 sec)

mysql> alter table izba add [COLUMN] kolor_izby varchar(20) AFTER metraz;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '[COLUMN] kolor_izby varchar(20) AFTER metraz' at line 1
mysql> alter table izba add kolor_izby varchar(30) AFTER metraz;
Query OK, 0 rows affected (0.10 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table izba alter kolor_izby set default "czarny";
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> create table przetwory (
    -> id_przetwory int primary key auto_increment,
    -> rok_produkcji year,
    -> id_wykonawcy int,
    -> foreign key(id_wykonawcy) references postac(id_postaci) on delete cascade,
    -> zawartosc varchar(200),
    -> dodatek varchar(200) default 'papryczka chilli',
    -> id_konsumenta int,
    -> foreign key(id_konsumenta) references postac(id_postaci) on delete cascade);
Query OK, 0 rows affected (0.07 sec)

mysql> desc przetwory;
+---------------+--------------+------+-----+------------------+----------------+
| Field         | Type         | Null | Key | Default          | Extra          |
+---------------+--------------+------+-----+------------------+----------------+
| id_przetwory  | int          | NO   | PRI | NULL             | auto_increment |
| rok_produkcji | year         | YES  |     | NULL             |                |
| id_wykonawcy  | int          | YES  | MUL | NULL             |                |
| zawartosc     | varchar(200) | YES  |     | NULL             |                |
| dodatek       | varchar(200) | YES  |     | papryczka chilli |                |
| id_konsumenta | int          | YES  | MUL | NULL             |                |
+---------------+--------------+------+-----+------------------+----------------+
6 rows in set (0.00 sec)

mysql> insert into postac() values(default, '1950', 1, 'bigos', default, 3);
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> insert into postac() values(default, 1950, 1, 'bigos', default, 3);
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> insert into postac values(default, 1950, 1, 'bigos', default, 3);
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> insert into postac values(1, 1950, 1, 'bigos', default, 3);
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> insert into przetwory values(1, 1950, 1, 'bigos', default, 3);
Query OK, 1 row affected (0.00 sec)

mysql> select * from przetwory;
+--------------+---------------+--------------+-----------+------------------+---------------+
| id_przetwory | rok_produkcji | id_wykonawcy | zawartosc | dodatek          | id_konsumenta |
+--------------+---------------+--------------+-----------+------------------+---------------+
|            1 |          1950 |            1 | bigos     | papryczka chilli |             3 |
+--------------+---------------+--------------+-----------+------------------+---------------+
1 row in set (0.00 sec)

mysql> row in set (0.00 sec)
    ->
    -> mysql>
    -> row in set (0.00 sec)
    ->
    -> mysql>
    ->
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'row in set (0.00 sec)

mysql>
row in set (0.00 sec)

mysql>' at line 1
mysql> desc postac;
+------------+---------------------------------+------+-----+---------+----------------+
| Field      | Type                            | Null | Key | Default | Extra          |
+------------+---------------------------------+------+-----+---------+----------------+
| id_postaci | int                             | NO   | PRI | NULL    | auto_increment |
| nazwa      | varchar(40)                     | NO   |     | NULL    |                |
| rodzaj     | enum('wiking','ptak','kobieta') | YES  |     | NULL    |                |
| data_ur    | date                            | YES  |     | NULL    |                |
| wiek       | int unsigned                    | YES  |     | NULL    |                |
+------------+---------------------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> insert into postac values(default,'wiking1 'wiking', 1800, 232
    '> ;
    '> );
    '> ')l
    -> ');
    '> );
    '> ;
    '> 23
    '> ;
    '> \c
    '> '\c'
    '> /c
    '> ^C
mysql> ;
ERROR:
No query specified

mysql> insert into postac values(default, 'wiking1', 'wiking', 1800, 232);
ERROR 1292 (22007): Incorrect date value: '1800' for column 'data_ur' at row 1
mysql> insert into postac values(default, 'wiking1', 'wiking', '1800-07-17', 232);
Query OK, 1 row affected (0.00 sec)

mysql> select * from postac;
+------------+----------+---------+------------+------+
| id_postaci | nazwa    | rodzaj  | data_ur    | wiek |
+------------+----------+---------+------------+------+
|          1 | Bjorn    | wiking  | 1700-10-23 |  323 |
|          2 | Drozd    | ptak    | 1900-05-21 |   88 |
|          3 | Tesciowa | kobieta | 1935-03-06 |   88 |
|          5 | wiking1  | wiking  | 1800-07-17 |  232 |
+------------+----------+---------+------------+------+
4 rows in set (0.00 sec)

mysql> alter table postac alter set id_postaci=4 where id_postaci=5
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'set id_postaci=4 where id_postaci=5' at line 1
mysql> alter table postac alter set id_postaci=4 where id_postaci=5;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'set id_postaci=4 where id_postaci=5' at line 1
mysql> update postac set id_postaci=4 where id_postaci=5;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from postac;
+------------+----------+---------+------------+------+
| id_postaci | nazwa    | rodzaj  | data_ur    | wiek |
+------------+----------+---------+------------+------+
|          1 | Bjorn    | wiking  | 1700-10-23 |  323 |
|          2 | Drozd    | ptak    | 1900-05-21 |   88 |
|          3 | Tesciowa | kobieta | 1935-03-06 |   88 |
|          4 | wiking1  | wiking  | 1800-07-17 |  232 |
+------------+----------+---------+------------+------+
4 rows in set (0.00 sec)

mysql> alter table postac auto_increment = 5;
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> insert into postac values(default, 'wiking2', 'wiking', '1800-07-17', 232);
Query OK, 1 row affected (0.00 sec)

mysql> insert into postac values(default, 'wiking3', 'wiking', '1800-07-17', 232);
Query OK, 1 row affected (0.01 sec)

mysql> insert into postac values(default, 'wiking4', 'wiking', '1800-07-17', 232);
Query OK, 1 row affected (0.00 sec)

mysql> insert into postac values(default, 'wiking5', 'wiking', '1800-07-17', 232);
Query OK, 1 row affected (0.00 sec)

mysql> select * from postac;
+------------+----------+---------+------------+------+
| id_postaci | nazwa    | rodzaj  | data_ur    | wiek |
+------------+----------+---------+------------+------+
|          1 | Bjorn    | wiking  | 1700-10-23 |  323 |
|          2 | Drozd    | ptak    | 1900-05-21 |   88 |
|          3 | Tesciowa | kobieta | 1935-03-06 |   88 |
|          4 | wiking1  | wiking  | 1800-07-17 |  232 |
|          5 | wiking2  | wiking  | 1800-07-17 |  232 |
|          6 | wiking3  | wiking  | 1800-07-17 |  232 |
|          7 | wiking4  | wiking  | 1800-07-17 |  232 |
|          8 | wiking5  | wiking  | 1800-07-17 |  232 |
+------------+----------+---------+------------+------+
8 rows in set (0.00 sec)

mysql> create table statek (
    -> nazwa_statku varchar(200) primary key,
    -> rodzaj_statku enum('maly','sredni','duzy'),
    -> data_wodowania date,
    -> max_ladownosc int unsigned);
Query OK, 0 rows affected (0.05 sec)

mysql> insert into statek values('statek1', 'sredni', '1986-01-27', 200);
Query OK, 1 row affected (0.00 sec)

mysql> insert into statek values('statek2', 'duzy', '1987-05-12', 400);
Query OK, 1 row affected (0.00 sec)

mysql> alter table postac add [column] funkcja varchar(100);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '[column] funkcja varchar(100)' at line 1
mysql> alter table postac add funkcja varchar(100);
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select * from postac;
+------------+----------+---------+------------+------+---------+
| id_postaci | nazwa    | rodzaj  | data_ur    | wiek | funkcja |
+------------+----------+---------+------------+------+---------+
|          1 | Bjorn    | wiking  | 1700-10-23 |  323 | NULL    |
|          2 | Drozd    | ptak    | 1900-05-21 |   88 | NULL    |
|          3 | Tesciowa | kobieta | 1935-03-06 |   88 | NULL    |
|          4 | wiking1  | wiking  | 1800-07-17 |  232 | NULL    |
|          5 | wiking2  | wiking  | 1800-07-17 |  232 | NULL    |
|          6 | wiking3  | wiking  | 1800-07-17 |  232 | NULL    |
|          7 | wiking4  | wiking  | 1800-07-17 |  232 | NULL    |
|          8 | wiking5  | wiking  | 1800-07-17 |  232 | NULL    |
+------------+----------+---------+------------+------+---------+
8 rows in set (0.00 sec)

mysql> alter table postac alter set funkcja='kapitan' where id_postaci=1;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'set funkcja='kapitan' where id_postaci=1' at line 1
mysql> update postac set funkcja='kapitan' where id_postaci=1;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> insert into izba values('adres1', 'spizarnia', 200, 1);
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> desc izba;
+---------------+--------------+------+-----+---------+-------+
| Field         | Type         | Null | Key | Default | Extra |
+---------------+--------------+------+-----+---------+-------+
| adres_budynku | varchar(100) | NO   | PRI | NULL    |       |
| nazwa_izby    | varchar(100) | NO   | PRI | NULL    |       |
| metraz        | int unsigned | YES  |     | NULL    |       |
| kolor_izby    | varchar(30)  | YES  |     | czarny  |       |
| wlasciciel    | int          | YES  | MUL | NULL    |       |
+---------------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> insert into izba values('adres1', 'spizarnia', 200, default, 1);
Query OK, 1 row affected (0.00 sec)

mysql> alter table postac add statek int;
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc postac;
+------------+---------------------------------+------+-----+---------+----------------+
| Field      | Type                            | Null | Key | Default | Extra          |
+------------+---------------------------------+------+-----+---------+----------------+
| id_postaci | int                             | NO   | PRI | NULL    | auto_increment |
| nazwa      | varchar(40)                     | NO   |     | NULL    |                |
| rodzaj     | enum('wiking','ptak','kobieta') | YES  |     | NULL    |                |
| data_ur    | date                            | YES  |     | NULL    |                |
| wiek       | int unsigned                    | YES  |     | NULL    |                |
| funkcja    | varchar(100)                    | YES  |     | NULL    |                |
| statek     | int                             | YES  |     | NULL    |                |
+------------+---------------------------------+------+-----+---------+----------------+
7 rows in set (0.00 sec)

mysql> update postac set statek=2 where id_postaci=1;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> update postac set statek=2 where id_postaci=2;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> update postac set statek=2 where id_postaci=4;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> update postac set statek=1 where id_postaci=5;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> update postac set statek=1 where id_postaci=6;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> update postac set statek=1 where id_postaci=7;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> update postac set statek=1 where id_postaci=8;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from postac;
+------------+----------+---------+------------+------+---------+--------+
| id_postaci | nazwa    | rodzaj  | data_ur    | wiek | funkcja | statek |
+------------+----------+---------+------------+------+---------+--------+
|          1 | Bjorn    | wiking  | 1700-10-23 |  323 | kapitan |      2 |
|          2 | Drozd    | ptak    | 1900-05-21 |   88 | NULL    |      2 |
|          3 | Tesciowa | kobieta | 1935-03-06 |   88 | NULL    |   NULL |
|          4 | wiking1  | wiking  | 1800-07-17 |  232 | NULL    |      2 |
|          5 | wiking2  | wiking  | 1800-07-17 |  232 | NULL    |      1 |
|          6 | wiking3  | wiking  | 1800-07-17 |  232 | NULL    |      1 |
|          7 | wiking4  | wiking  | 1800-07-17 |  232 | NULL    |      1 |
|          8 | wiking5  | wiking  | 1800-07-17 |  232 | NULL    |      1 |
+------------+----------+---------+------------+------+---------+--------+
8 rows in set (0.00 sec)

mysql> show tables;
+---------------------------+
| Tables_in_infs_ostrowskig |
+---------------------------+
| izba                      |
| postac                    |
| przetwory                 |
| statek                    |
| walizka                   |
+---------------------------+
5 rows in set (0.00 sec)

mysql>
