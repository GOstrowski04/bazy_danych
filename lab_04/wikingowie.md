# Wikingowie
## Zadanie 1
```sql
CREATE TABLE postac(id_postaci int primary key auto_increment, nazwa varchar(40), rodzaj enum('wiking', 'ptak','kobieta'), data_ur date, wiek int unsigned);
INSERT INTO postac VALUES(default, 'Bjorn', 'wiking', '1700-06-23', 323);
INSERT INTO postac VALUES(default, 'Drozd', 'ptak', '1975-08-20', 20); 
INSERT INTO postac VALUES(default, 'Tesciowa', 'kobieta', '1960-03-09', 45); 
UPDATE postac SET wiek=88 WHERE nazwa='Tesciowa';
```
## Zadanie 2
```sql
CREATE TABLE walizka(id_walizki int primary key auto_increment, pojemnosc int unsigned, kolor enum('rozowy', 'czerwony', 'teczowy', 'zolty'), id_wlasciciela, foreign key(id_wlasciciela) references postac(id_postaci) ON DELETE CASCADE);
ALTER TABLE walizka ALTER kolor SET DEFAULT 'rozowy';
INSERT INTO walizka values(default, 10, 'czerwony', 1);
INSERT INTO walizka values(default, 20, default, 3);
```
## Zadanie 3
```sql
CREATE TABLE izba(adres_budynku varchar(100), nazwa_izby varchar(100), primary key(adres_budynku, nazwa_izby), metraz int unsigned, wlasciciel, foreign key(wlasciciel) references postac(id_postaci) ON DELETE SET NULL);
ALTER TABLE izba ADD kolor_izby varchar(40) AFTER metraz;
ALTER TABLE izba ALTER kolor_izby SET DEFAULT 'czarny';
INSERT INTO izba values('adres1', 'spizarnia', 100, 1);
```
## Zadanie 4
```sql
CREATE TABBLE przetwory(id_przetworu int primary key auto_increment, rok_produkcji YEAR SET DEFAULT '1654', id_wykonawcy, foreign key(id_wykonawcy) REFERENCES postac(id_postaci) ON DELETE CASCADE, zawartosc varchar(100), dodatek varchar(100) SET DEFAULT 'papryczka chilli', id_konsumenta, foreign key(id_konsumenta) REFERENCES postac(id_postaci));
INSERT INTO przetwory values(default, '1950', 1, 'bigos', default, 3);
```
## Zadanie 5
```sql
INSERT INTO postac values
(default, 'wiking1', 'wiking', '1832-06-15', 180),
(default, 'wiking2', 'wiking', '1832-06-15', 180),
(default, 'wiking3', 'wiking', '1832-06-15', 462),
(default, 'wiking4', 'wiking', '1832-06-15', 300),
(default, 'wiking5', 'wiking', '1832-06-15', 180);
CREATE TABLE statek (nazwa_statku varchar(200) primary key, rodzaj_statku enum('maly','sredni','duzy'), data_wodowania date, max_ladownosc int unsigned);
INSERT INTO statek values ('statek1', 'sredni', '1986-01-27', 200), ('statek2', 'duzy', '1987-05-12', 400);
ALTER TABLE postac ADD funkcja varchar(100);
UPDATE postac SET funkcja='kapitan' WHERE id_postaci=1;
ALTER TABLE postac ADD  statek default null;
ALTER TABLE postac ADD foreign key(statek) REFERENCES statek(nazwa_statku) on delete set null;
UPDATE postac SET statek='statek1' WHERE id_postaci=1;
UPDATE postac SET statek='statek1' WHERE id_postaci=2;
UPDATE postac SET statek='statek1' WHERE id_postaci=4;
UPDATE postac SET statek='statek2' WHERE id_postaci=5;
UPDATE postac SET statek='statek2' WHERE id_postaci=6;
UPDATE postac SET statek='statek2' WHERE id_postaci=7;
UPDATE postac SET statek='statek2' WHERE id_postaci=8;
DELETE FROM izba WHERE nazwa_izby='spizarnia';
DROP TABLE izba;
```
